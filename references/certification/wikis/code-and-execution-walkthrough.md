# Code and Execution Walkthrough

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Code-and-Execution-Walkthrough](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Code-and-Execution-Walkthrough)
**Slug:** `Code-and-Execution-Walkthrough`

---

# Registration of an App on the 'App Store'

[Portuguese version available](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-an-Application-and-Retrieving-a-Software-Statement-%28PT%29)

We're going to make the assumption that a TPP has already been through the necessary onboarding processes of both themselves as an organisation and as an individual and have successfully registered on the Directory.

### Creating a new App or Software Record

![image](uploads/a6b63dce51e402510485d6defd4db7ed/image.png)

Navigate to Software Statements - Click '+ New Software Statement' and fill out the form with the Softwares Metadata

### Upload or Generate Certificates

![image](uploads/1f7f8045a9fe028e3e5dce2559e617ac/image.png)

This step should also be pretty self explanatory. Either use the in-built production grade PKI and Certificate Authority to create certificates or bring your own.

### Generating your own BRCAC certificate through the directory

After creating a valid software statement, you can go and create the BRCAC certificate.

Select the software statement that you want to create the certificate on:

![image](uploads/41cd1efc1b021a70036d9b6a680dadbb/image.png)

In this example, we'll be using Example TPP as our software statement

After, scroll down to Certificate and press on New Certificate:

![image](uploads/21ff01d7ec31c15a58e00a89a3ca10f4/image.png)

Inside the New Certificate Window, select BRCAC. It'll prompt you to go to spec's segurança [GitHub](https://github.com/OpenBanking-Brasil/specs-seguranca/tree/main/certificate-generation-instructions) that contains instructions on how to generate the certificate.

You should be able to generate your .csr file by following the tutorial. For the Example TPP, these were our settings:

```
"Size": null,
    "RegistrationId": null,
    "OrganisationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
    "City": "London",
    "Postcode": "EC2M 3TY",
    "AddressLine2": "Vila Hamburguesa",
    "RegisteredName": "Raidiam Services Ltd",
    "AddressLine1": "199 Bishopsgate",
    "LegalEntityName": "Raidiam Services Ltd",
    "OrganisationName": "Open Banking Brasil",
    "Country": "UK",
    "RegistrationNumber": "43142666000197",
    "CreatedOn": "2020-12-11T13:34:10.449Z",
    "Tag": null,
    "ParentOrganisationReference": "43142666000197",
    "CompanyRegister": "Cadastro Nacional Da Pessoa Juridica",
    "CountryOfRegistration": "UK"
```

And for the BRCAC.cnf file:

```
[req]
default_bits = 2048
default_md = sha256
encrypt_key = yes
prompt = no
string_mask = utf8only
distinguished_name = client_distinguished_name
req_extensions = req_cert_extensions

[ client_distinguished_name ]

#One of "Private Organization", "Government Entity", "Business Entity", "Non-Commercial Entity"
businessCategory = Private Organization

#Country of registration of the company
jurisdictionCountryName = UK 

#CNPJ/registration number
serialNumber = 43142666000197 

#Fixed value
countryName = BR

#Organisation Name from directory
organizationName = Open Banking Brasil

#Anything, (not validated right now, must be present)
stateOrProvinceName = RS 

#City of registration address
localityName = London 

#Organisation Id from directory
organizationalUnitName = 74e929d9-33b6-4d85-8ba7-c146c867a817 

#Software Statement Id
UID = 7218e1af-195f-42b5-a44b-8c7828470f5a

#Can be Anything (not validated right now, must be present)
commonName = tpp.localhost

[ req_cert_extensions ] 
basicConstraints = CA:FALSE
subjectAltName = @alt_name
keyUsage = critical,digitalSignature,keyEncipherment
extendedKeyUsage = clientAuth

[ alt_name ]
#DNS names may be present in this certificate type, but are not validated
DNS = tpp.localhost 
```

When you finish, you should run the openSSL script to generate the .csr file and upload it to the directory:

```
openssl req -new -utf8 -newkey rsa:2048 -nodes -out brcac.csr -keyout brcac.key -config ./brcac.cnf && cat brcac.csr
```

![image](uploads/9145b9b45627b7687c4695f7f4c9c0c6/image.png)

You'll then successfully generate a BRCAC certificate

### Interacting with the App Store

When a Software Statement is registered, an OAuth client is provisioned for this Software Record that enables participants to interact with the API. The next steps will show how, with less than 50 lines of NodeJs, you can interact with OpenID FAPI Protected Resources using the client credentials grant by leveraging the [node-openid-client](https://github.com/panva/node-openid-client) which is an OpenID Certified Relying Party. 

## Work out how to talk to the OpenID Server

Leveraging [OpenID Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html), simply create an Issuer class and then create a client associated with the issuer. Most of the code below is either logging, comments or setting the correct HTTP options to ensure that client certificate authentication is used when making HTTP calls.

#### Setup some initial variables for logging and views
```
'use strict';
var dcrLog = require('debug')('tpp:dcr')
  , paymentLog = require('debug')('tpp:payment'), setupLog = require('debug')('tpp:setup'), consentLog = require('debug')('tpp:consent'), commsLog = require('debug')('tpp:communications');
const config = require('./config');

```
#### Setup Key Material
```
(async () => {
  const {
    Issuer,
    custom,
    generators /*, TokenSet */,
  } = require('openid-client');
  const fs = require('fs');
  const crypto = require('crypto');
  const express = require('express');
  const cookieParser = require('cookie-parser');
  const app = express();
  const path = require('path');
  const https = require('https');
  const { default: axios } = require('axios');
  const certsPath = path.join(__dirname, './certs/');
  const jose = require('jose');
  const { nanoid } = require('nanoid');
  
  //A lot of oauth 2 bodies are form url encoded
  app.use(express.urlencoded({ extended: true }));

  //We need to confirm our private key into a jwks for local signing
  const key = crypto.createPrivateKey(
    fs.readFileSync(certsPath + 'signing.key')
  );
  const privateJwk = await jose.exportJWK(key);
  privateJwk.kid = config.data.signing_kid;
  setupLog('Create private jwk key %O', privateJwk);
  const keyset = {
    keys: [privateJwk],
  };

```
#### Setup MTLS Certificate
We need to setup an mtls certificate httpsAgent

NOTE: Do NOT leave rejectUnauthorized as 'false' as this disables certificate chain verification

```
  const httpsAgent = new https.Agent({
    ca: fs.readFileSync(certsPath + 'ca.pem'),
    key: fs.readFileSync(certsPath + 'transport.key'),
    cert: fs.readFileSync(certsPath + 'transport.pem'),
    rejectUnauthorized: false,
  });

  // set HBS to be in charge of rendering the HTML
  app.set('views', __dirname + '/views');
  app.set('view engine', 'hbs');

```
Set some logging options so that we log evrey request and response in an easy to use pattern

```
  custom.setHttpOptionsDefaults({
    hooks: {
      beforeRequest: [
        (options) => {
          commsLog(
            '--> %s %s',
            options.method.toUpperCase(),
            options.url.href
          );
          commsLog('--> HEADERS %o', options.headers);
          if (options.body) {
            commsLog('--> BODY %s', options.body);
          }
          if (options.form) {
            commsLog('--> FORM %s', options.form);
          }
        },
      ],
      afterResponse: [
        (response) => {
          commsLog(
            '<-- %i FROM %s %s',
            response.statusCode,
            response.request.options.method.toUpperCase(),
            response.request.options.url.href
          );
          commsLog('<-- HEADERS %o', response.headers);
          if (response.body) {
            commsLog('<-- BODY %s', response.body);
          }
          return response;
        },
      ],
    },
    timeout: 20000,
    https: {
      certificateAuthority: fs.readFileSync(certsPath + 'ca.pem'),
      certificate: fs.readFileSync(certsPath + 'transport.pem'),
      key: fs.readFileSync(certsPath + 'transport.key'),
      rejectUnauthorized: false,
    },
  });
```

#### Retrieving information from the Directory

Retrieve the information from the open banking brazil directory of participants on launch

```
  const instance = axios.create({ httpsAgent });
  setupLog('Retrieving Banks from Directory of Participants');
  const axiosResponse = await instance.get(
    'https://data.sandbox.directory.openbankingbrasil.org.br/participants'
  );


  const availableBanks = axiosResponse.data;
  setupLog(availableBanks);

```

These are set as global variables, they should be stored in a memory cache and retrieved based on the users session / state

```

  let selectedAuthServer;
  let selectedOrganisation;
  let createdConsent;


```

![image](uploads/21ff1b4c83700cb34b68ea76f8068393/image.png)

#### Setting up configuration for the Bank's FAPI Client

This configures a FAPI Client for the Bank that you have selected from the UI

```
  async function setupClient(bank) {
    setupLog('Begin Client Setup for Target Bank');
    selectedOrganisation = availableBanks.find((server) => {
      if (
        server.AuthorisationServers &&
        server.AuthorisationServers.some((as) => {
          if (as.CustomerFriendlyName == bank) {
            selectedAuthServer = as;
            setupLog('Target bank found in authorisation servers list');
            setupLog(selectedAuthServer);
            return true;
          }
        })
      ) {
        return server;
      }
    });

```

### Dynamic Client Registration (DCR)

#### Starting a new FAPI Client to talk to the directory

Check if client already registered for this target bank
```
    dcrLog('Client not registered');
    dcrLog('Beginning DCR Process');
    dcrLog('Discover how to talk to the Directory of Participants');
    const directoryIssuer = await Issuer.discover(
      'https://auth.sandbox.directory.openbankingbrasil.org.br/'
    );

    dcrLog(
      'Discovered directory issuer %s %O',
      directoryIssuer.issuer,
      directoryIssuer.metadata
    );
    const DirectoryFAPIClient = directoryIssuer.FAPI1Client;
    const directoryFapiClient = new DirectoryFAPIClient(config.data.client);
    dcrLog('Create FAPI Client to talk to the directory %O', directoryFapiClient);

```
Set the mutual tls client and certificate to talk to the client.

```
    directoryFapiClient[custom.http_options] = function (url, options) {
      const result = {};

      result.cert = fs.readFileSync(certsPath + 'transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
      result.key = fs.readFileSync(certsPath + 'transport.key');
      result.ca = fs.readFileSync(
        certsPath + 'ca.pem'
      ); // <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
      return result;
    };
```

#### Grabbing necessary information

Grab an access token with directory:software scope

```

    dcrLog('Obtaining Directory Access Token');
    const directoryTokenSet = await directoryFapiClient.grant({
      grant_type: 'client_credentials',
      scope: 'directory:software',
    });

```
Obtain the client ssa

```
    
    dcrLog('Obtaining SSA');
    const ssa = await directoryFapiClient.requestResource(
      `https://matls-api.sandbox.directory.openbankingbrasil.org.br/organisations/${config.data.organisation_id}/softwarestatements/${config.data.software_statement_id}/assertion`,
      directoryTokenSet
    );

```
Retrieve the keyset of the directory to validate the SSA, technically this is not required as the Bank is the party that have to validate it but it's good to show

```

    dcrLog('Obtaining Directory JWKS to validate the SSA');
    const JWKS = await jose.createRemoteJWKSet(
      new URL(
        'https://keystore.sandbox.directory.openbankingbrasil.org.br/openbanking.jwks'
      )
    );
```

#### Validating the JWT

Validating SSA and extracting contents

```
    const { payload } = await jose.jwtVerify(
      ssa.body.toString('utf-8'),
      JWKS,
      {

```
The expected issuer for production is available on the security specifications
```
        issuer: 'Open Banking Open Banking Brasil sandbox SSA issuer',
        clockTolerance: 2,
      }
    );
    dcrLog(payload);
```

#### Finding OpenID server configuration for the target bank

Discovering how to talk to target bank
```
    const localIssuer = await Issuer.discover(
      selectedAuthServer.OpenIDDiscoveryDocument
    );

    dcrLog(
      'Discovered Target Bank Issuer Configuration %s %O',
      localIssuer.issuer,
      localIssuer.metadata
    );

```

#### Selecting authentication method

Select how to to authenticate to the bank from Banks advertised mechanisms, private_key_jwt is preferred

```
    const { FAPI1Client } = localIssuer;
    //base on the options that the bank supports we're going to turn some defaults on
    localIssuer.metadata.token_endpoint_auth_methods_supported.includes(
      'private_key_jwt'
    )
      ? (config.data.client.token_endpoint_auth_method = 'private_key_jwt')
      : (config.data.client.token_endpoint_auth_method = 'tls_client_auth');

```

#### Pushed Authorisation Requests (PAR) based authentication selected


Mechanism selected based on what bank supports
```
    //This line will require the bank to enforce par without it the client should be free to choose PAR or standard
    localIssuer.metadata.request_uri_parameter_supported ? config.data.client.require_pushed_authorization_requests = true : config.data.client.require_pushed_authorization_requests = false;
```

Use pushed authorisation requests if the bank supports it. Will use PAR?
```
    //Set the redirects as they're required as a subset of whats registered
    config.data.client.redirect_uris = payload.software_redirect_uris;
    dcrLog('Set redirect_uris from software statement %O', payload.software_redirect_uris);

    //Add the software statement to your request for registration
    config.data.client.software_statement = ssa.body.toString('utf-8');
    dcrLog('Set softwarestatement from directory into registration metadata %O', config.data.client.software_statement);

    //Set jwks uri from the directory as this is required outside of the SSA if the client is going to be privatekeyjwt
    config.data.client.jwks_uri = payload.software_jwks_uri;
    dcrLog('Set jwks_uri from directory into registration metadata %O', payload.software_jwks_uri);
```

### Finishing DCR and creating a new client

Register Client at Bank
```
let fapiClient;
    try {
      //try and register a new client and set the private keys
      //For the new instance
      FAPI1Client[custom.http_options] = function (url,options) {
        // see https://github.com/sindresorhus/got/tree/v11.8.0#advanced-https-api
        const result = {};

        result.cert = fs.readFileSync(certsPath + 'transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
        result.key = fs.readFileSync(certsPath + 'transport.key');
        result.ca = fs.readFileSync(
          certsPath + 'ca.pem'
        ); // <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
        return result;
      };

      fapiClient = await FAPI1Client.register(config.data.client, {
        jwks: keyset,
      });
      dcrLog('New client created successfully');
      dcrLog(fapiClient);
      dcrLog('TODO: Save client For Later Use');
    } catch (err) {
      console.log(err);
      dcrLog('Error registering client at bank');
      dcrLog(err);
      throw(err);
    }

```
For the new instance set the HTTPS options as well
```

    fapiClient[custom.http_options] = function (url,options) {
      // see https://github.com/sindresorhus/got/tree/v11.8.0#advanced-https-api
      const result = {};

      result.cert = fs.readFileSync(certsPath + 'transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
      result.key = fs.readFileSync(certsPath + 'transport.key');
      result.ca = fs.readFileSync(
        certsPath + 'ca.pem'
      ); // <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
      return result;
    };

    setupLog('Client Setup for Target Bank Complete');
    return { fapiClient, localIssuer };
  }

```

#### Full code snippet so far

```
'use strict';
var dcrLog = require('debug')('tpp:dcr')
  , paymentLog = require('debug')('tpp:payment'), setupLog = require('debug')('tpp:setup'), consentLog = require('debug')('tpp:consent'), commsLog = require('debug')('tpp:communications');
const config = require('./config');


(async () => {
  const {
    Issuer,
    custom,
    generators /*, TokenSet */,
  } = require('openid-client');
  const fs = require('fs');
  const crypto = require('crypto');
  const express = require('express');
  const cookieParser = require('cookie-parser');
  const app = express();
  const path = require('path');
  const https = require('https');
  const { default: axios } = require('axios');
  const certsPath = path.join(__dirname, './certs/');
  const jose = require('jose');
  const { nanoid } = require('nanoid');
  
  //A lot of oauth 2 bodies are form url encoded
  app.use(express.urlencoded({ extended: true }));

  //We need to confirm our private key into a jwks for local signing
  const key = crypto.createPrivateKey(
    fs.readFileSync(certsPath + 'signing.key')
  );
  const privateJwk = await jose.exportJWK(key);
  privateJwk.kid = config.data.signing_kid;
  setupLog('Create private jwk key %O', privateJwk);
  const keyset = {
    keys: [privateJwk],
  };

  //We need to setup an mtls certificate httpsAgent
  //NOTE: Do NOT leave rejectUnauthorized as 'false' as this disables certificate chain verification
  const httpsAgent = new https.Agent({
    ca: fs.readFileSync(certsPath + 'ca.pem'),
    key: fs.readFileSync(certsPath + 'transport.key'),
    cert: fs.readFileSync(certsPath + 'transport.pem'),
    rejectUnauthorized: false,
  });

  // set HBS to be in charge of rendering the HTML
  app.set('views', __dirname + '/views');
  app.set('view engine', 'hbs');

  //Set some logging options so that we log evrey request and response in an easy to use pattern
  custom.setHttpOptionsDefaults({
    hooks: {
      beforeRequest: [
        (options) => {
          commsLog(
            '--> %s %s',
            options.method.toUpperCase(),
            options.url.href
          );
          commsLog('--> HEADERS %o', options.headers);
          if (options.body) {
            commsLog('--> BODY %s', options.body);
          }
          if (options.form) {
            commsLog('--> FORM %s', options.form);
          }
        },
      ],
      afterResponse: [
        (response) => {
          commsLog(
            '<-- %i FROM %s %s',
            response.statusCode,
            response.request.options.method.toUpperCase(),
            response.request.options.url.href
          );
          commsLog('<-- HEADERS %o', response.headers);
          if (response.body) {
            commsLog('<-- BODY %s', response.body);
          }
          return response;
        },
      ],
    },
    timeout: 20000,
    https: {
      certificateAuthority: fs.readFileSync(certsPath + 'ca.pem'),
      certificate: fs.readFileSync(certsPath + 'transport.pem'),
      key: fs.readFileSync(certsPath + 'transport.key'),
      rejectUnauthorized: false,
    },
  });

  //Retrieve the information from the open banking brazil directory of participants on launch
  const instance = axios.create({ httpsAgent });
  setupLog('Retrieving Banks from Directory of Participants');
  const axiosResponse = await instance.get(
    'https://data.sandbox.directory.openbankingbrasil.org.br/participants'
  );


  const availableBanks = axiosResponse.data;
  setupLog(availableBanks);

  //These are set as global variables, they should be stored in a memory cache and retrieved based on the users session / state
  let selectedAuthServer;
  let selectedOrganisation;
  let createdConsent;

  //This configures a FAPI Client for the Bank that you have selected from the UI
  async function setupClient(bank) {
    setupLog('Begin Client Setup for Target Bank');
    selectedOrganisation = availableBanks.find((server) => {
      if (
        server.AuthorisationServers &&
        server.AuthorisationServers.some((as) => {
          if (as.CustomerFriendlyName == bank) {
            selectedAuthServer = as;
            setupLog('Target bank found in authorisation servers list');
            setupLog(selectedAuthServer);
            return true;
          }
        })
      ) {
        return server;
      }
    });

    //Check if the client is registered, if it is not, register it.
    dcrLog('Check if client already registered for this target bank');
    dcrLog('Client not registered');
    dcrLog('Beginning DCR Process');
    dcrLog('Discover how to talk to the Directory of Participants');
    //Create a new FAPI Client to talk to the directory.
    const directoryIssuer = await Issuer.discover(
      'https://auth.sandbox.directory.openbankingbrasil.org.br/'
    );

    dcrLog(
      'Discovered directory issuer %s %O',
      directoryIssuer.issuer,
      directoryIssuer.metadata
    );
    const DirectoryFAPIClient = directoryIssuer.FAPI1Client;
    const directoryFapiClient = new DirectoryFAPIClient(config.data.client);
    dcrLog('Create FAPI Client to talk to the directory %O', directoryFapiClient);

    //Set the mutual tls client and certificate to talk to the client.
    directoryFapiClient[custom.http_options] = function (url, options) {
      const result = {};

      result.cert = fs.readFileSync(certsPath + 'transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
      result.key = fs.readFileSync(certsPath + 'transport.key');
      result.ca = fs.readFileSync(
        certsPath + 'ca.pem'
      ); // <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
      return result;
    };

    //Grab an access token with directory:software scope
    dcrLog('Obtaining Directory Access Token');
    const directoryTokenSet = await directoryFapiClient.grant({
      grant_type: 'client_credentials',
      scope: 'directory:software',
    });

    //Obtain the client ssa
    dcrLog('Obtaining SSA');
    const ssa = await directoryFapiClient.requestResource(
      `https://matls-api.sandbox.directory.openbankingbrasil.org.br/organisations/${config.data.organisation_id}/softwarestatements/${config.data.software_statement_id}/assertion`,
      directoryTokenSet
    );

    //Retrieve the keyset of the directory to validate the SSA, technically this is not required as the Bank is the party that have to validate it but it's good to show
    dcrLog('Obtaining Directory JWKS to validate the SSA');
    const JWKS = await jose.createRemoteJWKSet(
      new URL(
        'https://keystore.sandbox.directory.openbankingbrasil.org.br/openbanking.jwks'
      )
    );

    //Validate the jwt
    dcrLog('Validating SSA and extracting contents');
    const { payload } = await jose.jwtVerify(
      ssa.body.toString('utf-8'),
      JWKS,
      {
        //The expected issuer for production is available on the security specifications
        issuer: 'Open Banking Open Banking Brasil sandbox SSA issuer',
        clockTolerance: 2,
      }
    );
    dcrLog(payload);

    //Find the openid server configuration for the target bank
    dcrLog('Discovering how to talk to target bank');
    const localIssuer = await Issuer.discover(
      selectedAuthServer.OpenIDDiscoveryDocument
    );

    dcrLog(
      'Discovered Target Bank Issuer Configuration %s %O',
      localIssuer.issuer,
      localIssuer.metadata
    );

    dcrLog('Select how to to authenticate to the bank from Banks advertised mechanisms, private_key_jwt is preferred');
    const { FAPI1Client } = localIssuer;
    //base on the options that the bank supports we're going to turn some defaults on
    localIssuer.metadata.token_endpoint_auth_methods_supported.includes(
      'private_key_jwt'
    )
      ? (config.data.client.token_endpoint_auth_method = 'private_key_jwt')
      : (config.data.client.token_endpoint_auth_method = 'tls_client_auth');
    dcrLog('Mechanism selected based on what bank supports %O', config.data.client.token_endpoint_auth_method);
    //This line will require the bank to enforce par without it the client should be free to choose PAR or standard
    localIssuer.metadata.request_uri_parameter_supported ? config.data.client.require_pushed_authorization_requests = true : config.data.client.require_pushed_authorization_requests = false;
    dcrLog('Use pushed authorisation requests if the bank supports it. Will use PAR? %O', config.data.client.require_pushed_authorization_requests);

    //Set the redirects as they're required as a subset of whats registered
    config.data.client.redirect_uris = payload.software_redirect_uris;
    dcrLog('Set redirect_uris from software statement %O', payload.software_redirect_uris);

    //Add the software statement to your request for registration
    config.data.client.software_statement = ssa.body.toString('utf-8');
    dcrLog('Set softwarestatement from directory into registration metadata %O', config.data.client.software_statement);

    //Set jwks uri from the directory as this is required outside of the SSA if the client is going to be privatekeyjwt
    config.data.client.jwks_uri = payload.software_jwks_uri;
    dcrLog('Set jwks_uri from directory into registration metadata %O', payload.software_jwks_uri);


    let fapiClient;
    try {
      dcrLog('Register Client at Bank');
      //try and register a new client and set the private keys
      //For the new instance
      FAPI1Client[custom.http_options] = function (url,options) {
        // see https://github.com/sindresorhus/got/tree/v11.8.0#advanced-https-api
        const result = {};

        result.cert = fs.readFileSync(certsPath + 'transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
        result.key = fs.readFileSync(certsPath + 'transport.key');
        result.ca = fs.readFileSync(
          certsPath + 'ca.pem'
        ); // <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
        return result;
      };

      fapiClient = await FAPI1Client.register(config.data.client, {
        jwks: keyset,
      });
      dcrLog('New client created successfully');
      dcrLog(fapiClient);
      dcrLog('TODO: Save client For Later Use');
    } catch (err) {
      console.log(err);
      dcrLog('Error registering client at bank');
      dcrLog(err);
      throw(err);
    }
    //For the new instance set the HTTPS options as well
    fapiClient[custom.http_options] = function (url,options) {
      // see https://github.com/sindresorhus/got/tree/v11.8.0#advanced-https-api
      const result = {};

      result.cert = fs.readFileSync(certsPath + 'transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
      result.key = fs.readFileSync(certsPath + 'transport.key');
      result.ca = fs.readFileSync(
        certsPath + 'ca.pem'
      ); // <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
      return result;
    };

    setupLog('Client Setup for Target Bank Complete');
    return { fapiClient, localIssuer };
  }
```

# Finding Providers of Resources of Interest to our Customers

[Portuguese version available](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-and-Onboarding-with-Banks-%28PT%29)

One of the features of the Directory is the ability for Participating Banks to advertise their Authorisation Servers and to list and advertise what APIs, Versions and Locations of those Resources that these authorisation servers will issue access tokens for. This enables Banks to manage API version lifecycles in a consistent centralised way, deprecate old versions or start advertising support for newer APIs as and when those resources become available. This allows TPPs to Dynamically manage the connections they have to banks based on the propositions that can be enabled as a result of data becoming available.

![Screen_Shot_2022-02-09_at_08.44.52](uploads/0c4a200a8a878b8b56a06c737b2540cc/Screen_Shot_2022-02-09_at_08.44.52.png)

![Screen_Shot_2022-02-09_at_08.45.29](uploads/0525f2a13cae0db2589620a04993c2e5/Screen_Shot_2022-02-09_at_08.45.29.png)

![Screen_Shot_2022-02-09_at_08.46.42](uploads/1893c6c3d3a820bb85d44d7cafe31f68/Screen_Shot_2022-02-09_at_08.46.42.png)

In this example, the Raidiam Mock Bank is advertising that it supports the 'financings' api and the locations at which this API can be found. In most situations you would expect on a single endpoint for a resource location however, some UK Banks, use separate physical hosts for their failover / alternate site locations instead of relying on DNS failover.

```
{
        "PayloadSigningCertLocationUri": "https://mockbank.com/payload.pem",
        "ParentAuthorisationServerId": null,
        "OpenIDDiscoveryDocument": "https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration",
        "CustomerFriendlyName": "Mock Bank",
        "CustomerFriendlyDescription": null,
        "TermsOfServiceUri": "https://mockbank.com/tos",
        "ApiResources": [
            {
                "ApiFamilyType": "financings",
                "ApiVersion": 1,
                "ApiResourceId": "b67768ec-a0aa-4445-ae96-e00f28145146",
                "ApiDiscoveryEndpoints": [
                    {
                        "ApiDiscoveryId": "13aad598-12c6-4f75-92f4-dc754756b222",
                        "ApiEndpoint": "https://api.personal.bank.com/v1/personal-accounts"
                    }
                ]
            }
        ],
        "AutoRegistrationSupported": true,
        "CustomerFriendlyLogoUri": "https://mockbank.com/logo.png",
        "DeveloperPortalUri": "https://mockbank.com/dev",
        "AuthorisationServerId": "c8f0bf49-4744-4933-8960-7add6e590841"
    
},

```


#### Crafting a Dynamic Client Registration Request

There are many different FAPI compliant configurations that an OpenID Provider can choose to adopt and deciding what is best for each provider will depend on a number of different factors which are out of scope for this article.

Because of wide range of options that Banks can choose to adopt, TPPs must be able to process and select from the advertise capabilities the combination from whats on offer that they would like to use. The following is a rough example method for how a TPP could use a Software Statement and a Banks OpenID Metadata to determine if it can use OAuth 2 Pushed Authorisation Requests (PAR) or if it needs to use Signed and Encrypted Request Objects.


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

Find payment endpoint for the selected bank from the directory of participants

```
    const paymentEndpoint = getEndpoint(
      selectedAuthServer,
      'payments-pix',
      'open-banking/payments/v1/pix/payments$'
    );
```
Payment endpoint found
```
    let date = new Date();
    const offset = date.getTimezoneOffset();
    date = new Date(date.getTime() - offset * 60 * 1000);

```
Create payment object

```
    const payment = {
      creditorAccount: createdConsent.data.payment.details.creditorAccount,
      localInstrument: createdConsent.data.payment.details.localInstrument,
      proxy: createdConsent.data.payment.details.proxy,
      remittanceInformation: 'Making a payment',
      cnpjInitiator: '59285411000113',
      payment: {
        amount: createdConsent.data.payment.amount,
        currency: createdConsent.data.payment.currency,
      },
    };

```

Signing payment

```
const jwt = await new jose.SignJWT({ data: payment })
      .setProtectedHeader({ alg: 'PS256', typ: 'JWT', kid: privateJwk.kid })
      .setIssuedAt()
      .setIssuer(config.data.organisation_id)
      .setJti(nanoid())
      .setAudience(paymentEndpoint)
      .setExpirationTime('5m')
      .sign(key);
```
Create payment resource using the signed payment JWT 
```
et paymentResponse = await client.requestResource(
      `${paymentEndpoint}`,
      tokenSet,
      {
        body: jwt,
        method: 'POST',
        headers: {
          'content-type': 'application/jwt',
          'x-idempotency-key': nanoid(),
        },
      }
    );
    paymentLog('Payment resource created successfully %O', paymentResponse.body.toString());
    paymentLog('Validate payment response as it is a JWT');
    paymentLog('Retrieve the keyset for the bank (this has already been done and could be cached)');
    //Retrieve the keyset of the sending bank
    const JWKS = await jose.createRemoteJWKSet(
      new URL(
        `https://keystore.sandbox.directory.openbankingbrasil.org.br/${selectedOrganisation.OrganisationId}/application.jwks`
      )
    );
```

Validate the jwt came from the correct bank and was meant to be sent to me

```
let { payload } = await jose.jwtVerify(
      paymentResponse.body.toString(),
      JWKS,
      {
        issuer: selectedOrganisation.OrganisationId,
        audience: config.data.organisation_id,
        clockTolerance: 2,
      }
    );
    paymentLog('Payment response extracted and validated');

```

Check for payment's state

```
let x = 0;
    while (!['ACSP', 'ACCC', 'RJCT'].includes(payload.data.status)) {
      paymentLog(
        'Payment still not in a valid end state. Status: %O. Will check again to see if it has gone through.', payload.data.status
      );
      paymentLog(payload);
      paymentLog(
        'Use the self link on the payment to retrieve the latest record status. %O', payload.links.self
      );
      paymentResponse = await client.requestResource(
        payload.links.self,
        tokenSet,
        {
          headers: { accept: 'application/jwt', 'x-idempotency-key': nanoid() },
        }
      );
      
      paymentLog(
        'Validate and extract the payment response from the bank'
      );
      ({ payload } = await jose.jwtVerify(
        paymentResponse.body.toString(),
        JWKS,
        {
          issuer: selectedOrganisation.OrganisationId,
          audience: config.data.organisation_id,
          clockTolerance: 2,
        }
      ));
      x = x + 1;
      if (x > 5) {
        paymentLog(
          'Payment has not reached final state after 5 iterations, failing'
        );
        payload = { msg: 'Unable To Complete Payment', payload: payload };
        payload.stringify = JSON.stringify(payload);
        return res.render('cb', { claims: tokenSet.claims(), payload });
      }
    }

    paymentLog('Payment has reached a final state of',payload.data.status);
    paymentLog(payload);
    payload.stringify = JSON.stringify(payload);
    paymentLog('Payment execution complete');
    return res.render('cb', { claims: tokenSet.claims(), payload });
  });
```

Defining make payment view:

```
app.post('/makepayment', async (req, res) => {
    if (req.body.bank) {
      //Setup the client
      consentLog('Customer has select bank issuer to use %O', req.body.bank);
      const { fapiClient, localIssuer } = await setupClient(req.body.bank);
      consentLog('Client created, ready to talk to the chosen bank');
      client = fapiClient;
      issuer = localIssuer;
    }
    else {
      throw Error('No bank was selected');
    }
```

---

*Conteúdo baixado em 16/09/2026, 15:37:14*
