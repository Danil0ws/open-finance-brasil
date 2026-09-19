# Setting up Consent

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Setting-up-Consent](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Setting-up-Consent)
**Slug:** `Setting-up-Consent`

---


#### Defining endpoint function

```
function getEndpoint(authServer, apiFamilyType, apiEndpointRegex) {
    let consentEndpoint;
    authServer.ApiResources.find((resource) => {
      if (resource.ApiFamilyType === apiFamilyType) {
        //'payments-consents'
        resource.ApiDiscoveryEndpoints.find((endpoint) => {
          if (endpoint.ApiEndpoint.match(apiEndpointRegex)) {
            //'open-banking\/payments\/v1\/consents$'
            consentEndpoint = endpoint.ApiEndpoint;
            return endpoint;
          }
        });
        return resource;
      }
    });
    return consentEndpoint;
  }
```

#### Pushing authorization request to bank

This pushes an authorization request to the banks pushed authorisation request and returns the authorisation redirect uri
```

  async function generateRequest(
    fapiClient,
    authServer,
    organisation,
    payment
  ) {
    consentLog('Beginning the generation of a consent record and authorisation process');

```

Find the consent endpoint for this authorisation server

```
   
    consentLog('Find the consent endpoint for the payments consent from the selected authorisation server from the directory');
    const consentEndpoint = getEndpoint(
      authServer,
      'payments-consents',
      'open-banking/payments/v1/consents$'
    );
    consentLog('Consent endpoint found %O', consentEndpoint);
```

#### Creating the consent
Create the consent

```
    consentLog('Creating the consent record');
    createdConsent = await fapiClient.requestResource(
      consentEndpoint,
      ccToken,
      {
        method: 'POST',
        body: jwt,
        headers: {
          'content-type': 'application/jwt',
          'x-idempotency-key': nanoid(),
        },
      }
    );
    //Errors processing a JWT are sent as a
    if (createdConsent.statusCode != 201) {
      console.log(JSON.parse(createdConsent.body.toString()));
    }
```

#### Validating consent response JWT and retrieving keyset

Validate the Consent Response JWT to confirm it was signed correctly by the bank

Retrieve the keyset for the bank sending the consent response from the diretory of participants

```    
    const JWKS = await jose.createRemoteJWKSet(
      new URL(
        `https://keystore.sandbox.directory.openbankingbrasil.org.br/${organisation.OrganisationId}/application.jwks`
      )
    );

    //Validate the jwt
    const { payload } = await jose.jwtVerify(
      createdConsent.body.toString(),
      JWKS,
      {
        issuer: organisation.organisation_id,
        audience: config.data.organisation_id,
        clockTolerance: 2,
      }
    );
```
Update the payment consent

```   
    createdConsent = payload;
    consentLog('Consent response payload validated and extracted successfully');
    consentLog(createdConsent);
```

Setting parameters for the authorisation flow including nonce and pkce

```
    const state = crypto.randomBytes(32).toString('hex');
    const nonce = crypto.randomBytes(32).toString('hex');
    const code_verifier = generators.codeVerifier();

```
Store the code_verifier in your framework's session mechanism, if it is a cookie based solution

It should be httpOnly (not readable by javascript) and encrypted.

```
    const code_challenge = generators.codeChallenge(code_verifier);

```
Request that the bank provide the users authentication time in the id_token, if the bank does not support this then the it should just ignore this attribute and carry on processing the request

```
    const claims = {
      id_token: {
        auth_time: {
          essential: true,
        },
      },
      user_info: {
        auth_time: {
          essential: true,
        },
      },
    };
```

#### Add the created consent records id to the dynamic consent scope 

Add the created consent records id to the dynamic consent scope
```
    const scope = `openid consent:${payload.data.consentId} payments`;
    consentLog('Create the FAPI request object');
    const requestObject = await fapiClient.requestObject({
      scope,
      response_type: 'code id_token',
      redirect_uri: 'https://tpp.localhost/cb',
      code_challenge,
      code_challenge_method: 'S256',
      response_mode: 'form_post',
      state,
      nonce,
      claims,
      max_age: 900,
    });

    consentLog(requestObject);


```

#### Authorisation request URL using PAR

If there is a pushed authorisation request end point then use it as it is a more secure way to talk to the bank

Decide how to communicate the request to the bank, by reference (PAR) or by Value

```
let reference;
    let authUrl;

    if (fapiClient.issuer.pushed_authorization_request_endpoint) {
      consentLog('The bank supports PAR so we will use this mechanism as it is more secure');
      try {
        consentLog('Create a PAR resource');
        reference = await fapiClient.pushedAuthorizationRequest({
          request: requestObject,
        });
      } catch (e) {
        console.log(e);
      }

      consentLog('Create a authorisation request url using PAR');
      authUrl = await fapiClient.authorizationUrl({
        request_uri: reference.request_uri,
        prompt: 'consent',
      });
      consentLog(authUrl);
      return { authUrl, code_verifier, state, nonce, createdConsent };
    } else {
      consentLog('Create a authorisation request url passing the request object by value');
      authUrl = await fapiClient.authorizationUrl({
        request: requestObject,
        prompt: 'consent',
      });
      consentLog(authUrl);
      return { authUrl, code_verifier, state, nonce, createdConsent };
    }
  }
```

## Setting up express routes

```
//Express setup routes
  app.use(cookieParser());
  app.use(express.static(path.join(__dirname, 'public')));

  app.use('/banks', async (req, res) => {
    consentLog('Providing a list of banks to the customer for them to choose from the UI');
    res.json(availableBanks);
  });

  app.get('/', async (req, res) => {
    //Clear stale cookies on page load
    res.clearCookie('state');
    res.clearCookie('nonce');
    res.clearCookie('code_verifier');

    res.sendFile(path.join(__dirname, './views', 'payment.html'));
  });

  app.get('/payment', async (req, res) => {
    //Clear stale cookies on page load
    setupLog('Starting a new journey, clearing old cookies');
    res.clearCookie('payment');
    res.clearCookie('state');
    res.clearCookie('nonce');
    res.clearCookie('code_verifier');

    res.sendFile(path.join(__dirname, './views', 'payment.html'));
  });

```

#### Payment route

```
app.post('/payment', async (req, res) => {
    consentLog('Starting a new payment consent');
    let date = new Date();
    const offset = date.getTimezoneOffset();
    date = new Date(date.getTime() - offset * 60 * 1000);

    const data = {
      debtorAccount: {
        number: req.body.debtorAccount_number,
        accountType: req.body.debtorAccount_accountType,
        ispb: req.body.debtorAccount_ispb,
        issuer: req.body.debtorAccount_issuer,
      },
      loggedUser: {
        document: {
          identification: req.body.loggedUser_document_identification,
          rel: req.body.loggedUser_document_rel,
        },
      },
      creditor: {
        name: req.body.creditor_name,
        cpfCnpj: req.body.creditor_cpfCnpj,
        personType: req.body.creditor_personType,
      },
      payment: {
        date: date.toISOString().split('T')[0],
        amount: req.body.payment_amount,
        currency: 'BRL',
        details: {
          proxy: '12345678901',
          localInstrument: req.body.payment_details_localInstrument,
          creditorAccount: {
            number: req.body.payment_details_creditAccount_number,
            accountType: req.body.payment_details_creditAccount_accountType,
            ispb: req.body.payment_details_creditAccount_ispb,
            issuer: req.body.payment_details_creditAccount_issuer,
          },
        },
        type: 'PIX',
      },
    };
```

![image](uploads/2c85678efc57c1f6e0db51b134e70fb1/image.png)

#### Consent payload storing

Storing consent payload in a cookie for convenience, server side mechanisms would be more secure and consent payload only just fits in a cookie size
```
    res.cookie('consent', JSON.stringify(data), {
      sameSite: 'none',
      secure: true,
    });

    //Clear stale cookies on page load
    res.clearCookie('state');
    res.clearCookie('nonce');
    res.clearCookie('code_verifier');

    consentLog('Sending customer to select the bank they want to make the payment from');
    res.render('idp', {});
  });

  app.get('/idp', async (req, res) => {
    //Clear stale cookies on page load
    res.clearCookie('state');
    res.clearCookie('nonce');
    res.clearCookie('code_verifier');

    res.render('idp', {});
  });

  let client;
  let issuer;

  app.use(express.urlencoded());
  
```
#### Finishing consent

This is used for response mode form_post, query and form_post are the most common
```
  app.post('/cb', async (req, res) => {
    consentLog('Received redirect from the bank');
    const callbackParams = client.callbackParams(req);

```
Obtaining access token

```
    consentLog('Trying to obtain an access token using the authorization code');
    const tokenSet = await client.callback(
      'https://tpp.localhost/cb',
      callbackParams,
      {
        code_verifier: req.cookies.code_verifier,
        state: req.cookies.state,
        nonce: req.cookies.nonce,
        response_type: 'code',
      },
      {
        clientAssertionPayload: {
          aud: issuer.mtls_endpoint_aliases.token_endpoint,
        },
      }
    );
    consentLog('Access token obtained. %O', tokenSet);
```

Consent process finished



---

*Conteúdo baixado em 16/09/2026, 15:38:36*
