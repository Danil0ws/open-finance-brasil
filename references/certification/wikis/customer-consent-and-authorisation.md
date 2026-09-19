# Customer Consent and Authorisation

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Consent-and-Authorisation](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Consent-and-Authorisation)
**Slug:** `Customer-Consent-and-Authorisation`

---

[Portuguese version available](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Consent-and-Authorisation-%28PT%29)

We are going to go through the steps to obtain access to customer data using the Brazil Open Banking Standards for Redirect using both Encrypted Request Objects and Pushed Authorisation Requests. Both modes that are supported for Brazil Open Banking.

### Step 0. Simplify our development efforts

Creating a strongly typed API client can be a simple as running a single cli command. An example of generating a consentsAPI client using the [Consents OpenAPI definition](https://github.com/OpenBanking-Brasil/areadesenvolvedor/blob/master/documentation/source/swagger/swagger_consents.yaml) is below.

```
openapi-generator generate -i swagger.yaml -g typescript-axios --additional-properties=npmName=@raidiam/api_consents_open_banking_brasil --additional-properties=supportsES6=true  -o ./tmp
```

### Step 1. Create a Consent Resource

Using a newly created typescript API

```
  using creating a new consent resource is as simple as
// Obtain Tokens for a client credentials grant with scope of consents
const tokens = await fapiClient.grant({ scope: 'consents', grant_type: 'client_credentials' });

// Craft Post Request
var oneYearFromNow ​= new Date();
oneYearFromNow.setFullYear(oneYearFromNow.getFullYear() + 1);


var now = new Date();


const createPost = await consentsApi.consentsPostConsents(`${tokens.token_type} ${tokens.access_token}`,
                {
                    data: {
                        permissions: [CreateConsentDataPermissionsEnum.AccountsRead, CreateConsentDataPermissionsEnum.AccountsBalancesRead],
                        expirationDateTime: oneYearFromNow.toISOString(), transactionFromDateTime: now.toISOString(), transactionToDateTime: oneYearFromNow.toISOString(),
                        loggedUser: {
                            document: {
                                identification: '12345123451',
                                rel: 'CPF'
                           } 
                        },
                        businessEntity: {
                            document: {
                                identification: '11111111111111',
                                rel: 'CNPJ'
                            }
                        }
                    }
                }).catch(err => {
                    console.log(err);
                });

```

Done, a new consent request is created

```
{
   "data":{
      "consentId":"mock-ccfe895c-b4cf-4685-b744-2c8fb997c795",
      "creationDateTime":"2021-06-08T16:30:39.399Z",
      "status":"AWAITING_AUTHORISATION",
      "statusUpdateDateTime":"2021-06-08T16:30:39.199Z",,
      "permissions":[
         "ACCOUNTS_READ",
         "ACCOUNTS_BALANCES_READ"
      ],
      "expirationDateTime":"2022-06-08T16:30:39.199Z",
      "transactionFromDateTime":"2021-06-08T16:30:39.199Z",
      "transactionToDateTime":"2022-06-08T16:30:39.199Z",
   },
   "links":{
      "self":"https://matls-api.mockbank.poc.raidiam.io/consents/mock-ccfe895c-b4cf-4685-b744-2c8fb997c795"
   },
   "meta":{
      "totalRecords":1,
      "totalPages":1,
      "requestDateTime":"2021-06-08T16:30:39.399Z"
   }
}
```

### Step 2. Creating a Request Object

#### 2.1 Create a PKCE Code Challenge for the request

```
  const state = crypto.randomBytes(32).toString('hex');
        const nonce = crypto.randomBytes(32).toString('hex');
        const code_verifier = generators.codeVerifier();



        const code_challenge = generators.codeChallenge(code_verifier);
```

#### 2.2 Optional: Create a claims object containing desired Brazil OIDF Standard Claims or the authentication level that you wish a Bank to Perform with the end user

The Brazil security profile defines two new OIDC claims that Third Parties can request be provided by their Bank. CPF and CNPJ. The details of these claims are on the Brasil FAPI Security Profile.

```
 const claims = {
            id_token: {
                auth_time: {
                    essential: true,
                },
                cpf: {
                    essential: true,
                },
                given_name: {
                    essential: true,
                },
                acr: {
                    values: ['urn:brasil:openbanking:loa2'],
                    essential: true
                }
            },
            user_info: {
                auth_time: {
                    essential: true,
                },
                cpf: {
                    essential: true,
                },
                given_name: {
                    essential: true,
                },
                acr: {
                    values: ['urn:brasil:openbanking:loa2'],
                    essential: true
                }
            }
        };
```

#### 2.3 Package up a request object and sign it (using the oidc-client)

The library that is free for all use takes care of all of the heavy lifting for developers so much so that creating a sign JWT that meets the requirement for a FAPI Request Object is as simple as

```
const requestObject = await fapiClient.requestObject({
            `openid consent:${consentId}`,
            response_type: 'code id_token',
            redirect_uri: 'https://tpp.localhost/cb',
            code_challenge,
            code_challenge_method: 'S256',
            response_mode: 'form_post',
            state,
            nonce,
            claims,
            max_age: 300
        
});

```

#### 2.4 To PAR or Not to PAR

The pros (many) and cons (not many) of using Pushed Authorisation Requests are a topic for another article however for developers there is no over head for using PAR with this library and there are significant privacy benefits that can be gained when communicating requests for information. More information on PAR can be found in the recent introduction video that [Raidiam's CTO gave to the Brazil Ecosystem on behalf of the OpenID Foundation](https://www.youtube.com/watch?v=v8ks7C-f9Yg).

**2.4.1 Create Authorization Url Using PAR**

```
reference = await fapiClient.pushedAuthorizationRequest({
            request: requestObject
          
});
authUrl = await fapiClient.authorizationUrl({ request_uri: reference.request_uri });
```

**2.4.2 Create Authorization Url not using PAR **

```
authUrl = await fapiClient.authorizationUrl({ request: requestObject });
```

![image](uploads/071633b65db318d8dfeee19080c3b3f8/image.png)

### 3.0 Send User off for Authorisation

```
const { authUrl, code_verifier, state, nonce } = await generateRequest(createPost.data.data.consentId, USE_PAR);

//save state
//save nonce
//save code_verifier

return res.redirect(authUrl);
```

### 4.0 User Authenticates and Authorises

The validation steps and information that needs to be presented to the customer

![image](uploads/6fd71e5a2acaeae5040446a6a8f82602/image.png)

### 5.0 Validate Redirect and obtain access tokens

```
const state = retrieveState();
res.cookie('bank.state', null, { path });


const nonce = retrieveNonce();
res.cookie('bank.nonce', null, { path });


const code_verifier = retrieveCodeVerifer();
res.cookie('bank.code_verifier', null, { path });


tokens = await fapiClient.callback('https://tpp.localhost/cb',
               callbackParams,
               { code_verifier, state, nonce, response_type: 'code id_token' },
           );
```

This project leverages an [Open Source, FAPI Certified, OIDC Client](https://github.com/panva/node-openid-client) that comes with extensive documentation and examples. If you wish to use the [Open Source OIDC Client](https://github.com/panva/node-oidc-provider/blob/main/docs/README.md), please do consider sponsoring the project as additional support is available.

That's it! End to End with only a couple of hundred lines of NodeJS and the use of free open source libraries a TPP can discovery, register, setup consent, obtain customer Authorization for access and then access resources.

---

*Conteúdo baixado em 16/09/2026, 15:37:21*
