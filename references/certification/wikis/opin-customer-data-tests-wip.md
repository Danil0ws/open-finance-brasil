# [OPIN] Customer Data Tests WIP

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/[OPIN]-Customer-Data-Tests-WIP](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/[OPIN]-Customer-Data-Tests-WIP)
**Slug:** `[OPIN]-Customer-Data-Tests-WIP`

---

# Overview

The customer data Phase 2 Version 2 Test plan is a series of tests plans which have been built with the objective to test if the Open Insurance Implementation of each institution is in line with the latest version of the [Open Insurance Brazil Customer Data API](https://br-openinsurance.github.io/areadesenvolvedor/#fase-2-apis-do-open-insurance-brasil), and also the expected functional requirements.

The tests are divided into two different classes:

**- Structural Tests** - Tests that will validate the JSON structure for the  20X response for each data endpoint. Since no security layer will be tested, the payload shouldn’t be protected via MTLS. We will have one test module per API inside the same test plan.

**- Functional Tests** - Tests that will validate the functional behaviour of the API, with one specific test plan for each API.

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. 
In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/openinsurancebrazil/conformance-suite/-/issues) so we can have it evaluated by the Conformance Suite Engineering team.


# Release Dates

- 15/09/22 - Functional and Structural tests have been deployed on an Alpha Version, as follows:
    - Consents API based on version 1.0.0
    - Resources API based on version 1.0.0
    - Customers API based on version 1.1.0
    - Patrimonial API based on version 1.1.0


# Data Sample Requirements

All tests require the institutions to set at least one Personal or Business account with the product that is being tested. The tested user CPF or CPF/CNPJ pair will have to be provided on the test configuration so the APIs can be accessed and the response payloads validated on the test scope.

When more data than the one defined above is required, the test summary will define what must be set for the execution to achieve success. The following test plans contain modules that require data samples to be set: 

1. Resources API Test 1.1.0 - 3 up to 25 listable resources will need to be set for the user to pass on the pagination tests that require a second page to be accessed.


# Test Plan Execution
To execute the tests the user will have to follow a three-step process:

1. Access the [Open Insurance Conformance Suite](https://web.conformance.directory.opinbrasil.com.br)
2. Select a Test Plan
3. Fill out the configuration fields 
4. Execute Test modules

Each step detail should be executed as follows:

# Access the Conformance Suite

The Customer Data tests are available on the [Open Insurance Brasil Conformance Suite](https://web.conformance.directory.opinbrasil.com.br). In order to access the conformance suite, the user must have an active account at the [Open Insurance Brasil Sandbox Directory](https://web.sandbox.directory.opinbrasil.com.br/).

Upon entry the user should be presented with an initial page with 6 different buttons:

![image](uploads/0ff4ceea581a8f13c6fba3ed48b839c2/image.png)

In order to run any tests, the user should click on the button **"Create new test plan"**. The user can also check others test logs and plans published on the other options.

# Select a Test Plan

When creating a new test plan, the user will have fill some information regarding the execution:

![image](uploads/05d95301ec7097dc8104de8ab22f3403/image.png)

The full list of Test Plans is available under the menu "Test Plans". From there the user can select any of the Customer Data Test Plans that are presented on the dropdown list. Both the Structural and Functional test plans will be available on this list:

![image](uploads/6202813f380118b990207e97a9313f8e/image.png)

After selecting a test plan, the user will also be prompted to select three other options:

1. **Client Autenthication Type** - How will the client authenticate on the server to obtain a token. FAPI only supports private_key_jwt and tls_client_auth out of the allowed [OAuth 2.0 Authentication Methods](https://darutk.medium.com/oauth-2-0-client-authentication-4b5f929305d4)

2. **Request Object Method** - If [PAR](https://datatracker.ietf.org/doc/rfc9126/) will or not be used

3. **FAPI Response Mode** - Open Banking Brazil does not permit JARM so tests will have to be executed always with "plain response"

# Fill out the configuration fields

Depending on the kind of test being executed (Functional or Structural) the user will be promptd to provide additional information to enable test execution. The information required are details about both the client that will be used by the Conformance Suite, as well as the details about the Server that will be certified on the Conformance Tests. 

## Structural test configuration file

The use will have to provide the following information to run the structural tests:

![image](uploads/a770767f4eb11cc3e6e362002aa42d7c/image.png)

### Test Information:

Those fields are used to define general information used by the conformance suite when saving and executing the test.

**alias:** This field will be used to create the redirect_uri that will be used when doing the authorization code flow on the test scope. This is a standard field, and _won't be used in the structural tests_.

**description:** Freeform text field used to identify this test later.

**publish:** Select whether the results of this test will be made public or will remain private - If made public it will be possible for other users to find your test plans [when searching for public test logs](https://web.conformance.directory.openbankingbrasil.org.br/logs.html?public=true).

### Resource:

**resourceUrl:** Provide any example URL, which will be used to access the endpoint via Regex. Important to notice that the resource URL provided is this field should be the one that hosts the payloads that will be validated ion the structural test, so it shouldn't be protected via MTLS. Example: https://www.bank.dummypayload.com/open-insurance/consents/v1/

**Mock Policy ID:** Provide the mocked policy ID that will be used to access the endpoints, when necessary. The value will also be used as the consent ID on the consents structural tests. The user _should only provide the value for the Mock Policy ID_, and **not** the URI with the Mock Policy ID. Example of URI that will use this field: https://www.bank.dummypayload.com/open-insurance/insurance-patrimonial/v1/{policyID}/policy-info


## Functional test configuration file

The functional tests requires additional information to informed on the configuration files. The three sections that should be provided are:

* Test Information
* Server
   * Client
   * Resource
   * Directory

The description for each field is provided below:

### Test Information:

Those fields are used to define general information used by the conformance suite when saving and executing the test.

**alias:** This field will be used to create the redirect_uri that will be used when doing the authorization code flow on the test scope. The redirect URI will have the following format "https://web.conformance.directory.openbankingbrasil.org.br/test/a/alias/callback" where alias is the value set on the alias field. Make sure this redirect_uri is added on the software_statement used on the DCR.

**description:** Freeform text field used to identify this test later.

**publish:** Select whether the results of this test will be made public or will remain private - If made public it will be possible for other users to find your test plans [when searching for public test logs](https://web.conformance.directory.openbankingbrasil.org.br/logs.html?public=true).

### Server Details 

Those fields are related to the server configuration and it's URIs, including both the Authorisation Server URIs and the Resource Servers URIs.

**discoveryUrl:** Provide the [Authorisation Server Meta Data URI](https://tools.ietf.org/id/draft-ietf-oauth-discovery-08.html), also known as the well-known address.

#### Client Details:

Those details are related to the Software Statement that must be created on the Open Insurance Brasil Sandbox environment and will be used by the Conformance Suite to connect with the server that is going to be tested. Before generating the certificates and doing the DCR to generate the required client_id, make sure that the correct redirect_uri and DADOS Role has been added into the Software

**jwks**: Provide the Signing Keys used by the client in a JWKS format. Here we suggest using the Directory Sandbox PKI to generate those keys. To create a Signing Key (BRSEAL) with the Directory Sandbox PKI refer to the [Open Insurance Brazil Directory Guide](https://br-openinsurance.github.io/areadesenvolvedor/files/OpenInsurance_Gerando_o_Certificado_BRSEAL.pdf)

The keys generated by following the instructions on the directory will be provided on a format that is not JSON, however, tests will require keys as JWKS. There are multiple ways for this to be done. Given that this key will be made public during the test execution it's possible to use an online conversor to obtain the JWKS, as follows:

1. Convert the .key file obtained from the directory to RSA with OpenSSL `openssl rsa -in server.key -out server_new.key`
2. Convert the RSA encoded key to JWK with https://8gwifi.org/jwkconvertfunctions.jsp 
3. Before adding the Private Key into the CS, make sure the object "alg": "PS256" is added on the jwks, that the "kid" is updated with the correct directory kid and that "use" is set to "sig"

**mtls.cert**: Provide the contents of the Public Transport Certificate (BRCAC) Generated on the Sandbox Participant Directory in PEM format. Here you can open the .pem file with a regular Text Editor and paste it's contents on the field. To create a BRCAC on the Sandbox Directory refer to the [Open Insurance Brazil Directory Guide](https://br-openinsurance.github.io/areadesenvolvedor/files/OpenInsurance_Gerando_o_Certificado_BRCAC.pdf)

**mtls.key**:Provide the contents of the Public Key in .PEM format. Similar step to the mtls.cert, however here you should provide the details of the Key that was generated together with the .csr

**mtls.ca**: Provide the Participant Directory Certificate Chain, used to sign all keys issued by the Sandbox PKI. File is provided below, paste it's contents on the field.

```
-----BEGIN CERTIFICATE-----
MIIF+TCCBOGgAwIBAgIUREOZADRSvAehVYQQw8xHQ60nZ78wDQYJKoZIhvcNAQEL
BQAwdDELMAkGA1UEBhMCQlIxHjAcBgNVBAoTFU9wZW4gSW5zdXJhbmNlIEJyYXNp
bDEXMBUGA1UECxMOT3BlbiBJbnN1cmFuY2UxLDAqBgNVBAMTI09wZW4gSW5zdXJh
bmNlIFJvb3QgUFJPRFVDVElPTiAtIEcxMB4XDTIxMTIwMTIyNTIwMFoXDTI2MTIw
MTIyNTIwMFowejELMAkGA1UEBhMCQlIxHjAcBgNVBAoTFU9wZW4gSW5zdXJhbmNl
IEJyYXNpbDEXMBUGA1UECxMOT3BlbiBJbnN1cmFuY2UxMjAwBgNVBAMTKU9wZW4g
SW5zdXJhbmNlIFBST0RVQ1RJT04gSXNzdWluZyBDQSAtIEcxMIIBIjANBgkqhkiG
9w0BAQEFAAOCAQ8AMIIBCgKCAQEA6TIU0IP+uAkcZELubrJX+XmBwbaRIciK0h7j
6GAapcesiLK38yMYoaMDGrIFcBGVZel4obGt/zNgbPgf1DPgy5DiissfpXWiwSM5
NmfQMzEkytng0VpZqRAadHo1do1s9pxe1GPrPPreS3F4yQgDw6muQxqOhSXFVSzF
B/PMTBbxOc3UBWy0gTwzTTeRxtl/mxJ/pqeShHshx6aORyJ7jO9w10LR6VxsqaUO
mZAx9uTYgqksqeude4Zey0+UJ596VwimqEPv5XlvSnZdxnZcL/CoD2utIejWFryz
K9cf8Dj45QdmA5Zx7vUa0OFAePnOyp6vUtVxfvabuDhbwLqEqQIDAQABo4ICezCC
AncwDgYDVR0PAQH/BAQDAgEGMBIGA1UdEwEB/wQIMAYBAf8CAQAwHQYDVR0OBBYE
FPhBgaejhY3OmEaSm8czJEVVH7VnMB8GA1UdIwQYMBaAFMJpDULSOPWXMhRNUL00
FUsCVtlbMD0GCCsGAQUFBwEBBDEwLzAtBggrBgEFBQcwAYYhaHR0cDovL29jc3Au
cGtpLm9waW5icmFzaWwuY29tLmJyMDwGA1UdHwQ1MDMwMaAvoC2GK2h0dHA6Ly9j
cmwucGtpLm9waW5icmFzaWwuY29tLmJyL2lzc3Vlci5jcmwwggGSBgNVHSAEggGJ
MIIBhTCCAYEGCisGAQQBg7ovZAEwggFxMIIBNgYIKwYBBQUHAgIwggEoDIIBJFRo
aXMgQ2VydGlmaWNhdGUgaXMgc29sZWx5IGZvciB1c2Ugd2l0aCBSYWlkaWFtIFNl
cnZpY2VzIExpbWl0ZWQgYW5kIG90aGVyIHBhcnRpY2lwYXRpbmcgb3JnYW5pc2F0
aW9ucyB1c2luZyBSYWlkaWFtIFNlcnZpY2VzIExpbWl0ZWRzIFRydXN0IEZyYW1l
d29yayBTZXJ2aWNlcy4gSXRzIHJlY2VpcHQsIHBvc3Nlc3Npb24gb3IgdXNlIGNv
bnN0aXR1dGVzIGFjY2VwdGFuY2Ugb2YgdGhlIFJhaWRpYW0gU2VydmljZXMgTHRk
IENlcnRpY2ljYXRlIFBvbGljeSBhbmQgcmVsYXRlZCBkb2N1bWVudHMgdGhlcmVp
bi4wNQYIKwYBBQUHAgEWKWh0dHA6Ly9jcHMucGtpLm9waW5icmFzaWwuY29tLmJy
L3BvbGljaWVzMA0GCSqGSIb3DQEBCwUAA4IBAQAw9/XF3wYwCE321WVJBZZ8xHYE
ze4umx9lTklw90x2gmOhjmxnU5V0eL0LaV+XcZjsRF7Hs8Du/vB7WiOELuAlw2Yq
I+8/2xcdARfbgEQirhPTrogTUPFcoW9SJ1OS3IGRErsFEvhAaiq1Vh+l9VNWTJdp
82vraRxR48DiWDPSq+H/qWtW+TrnbLloLu+lhIIGScmaRpPyQfPzGdRL8tmiRdW+
zlpP9P6dM/Y1RS0LM1xfoSaLL2dxSWmr3w7qq0YgALv3HN7qTX+lUDf9IKU+Bq1U
wGvtyBGSrL6/WYEAlpLHwZNbTbMcIYUSjerAZ6Pk/AJ825fE2vy3hwtJOQDW
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
MIIDuDCCAqCgAwIBAgIUTJ8WRDgDO7xeSD9ZCWX390zO970wDQYJKoZIhvcNAQEL
BQAwdDELMAkGA1UEBhMCQlIxHjAcBgNVBAoTFU9wZW4gSW5zdXJhbmNlIEJyYXNp
bDEXMBUGA1UECxMOT3BlbiBJbnN1cmFuY2UxLDAqBgNVBAMTI09wZW4gSW5zdXJh
bmNlIFJvb3QgUFJPRFVDVElPTiAtIEcxMB4XDTIxMTIwMTIyNTIwMFoXDTI2MTEz
MDIyNTIwMFowdDELMAkGA1UEBhMCQlIxHjAcBgNVBAoTFU9wZW4gSW5zdXJhbmNl
IEJyYXNpbDEXMBUGA1UECxMOT3BlbiBJbnN1cmFuY2UxLDAqBgNVBAMTI09wZW4g
SW5zdXJhbmNlIFJvb3QgUFJPRFVDVElPTiAtIEcxMIIBIjANBgkqhkiG9w0BAQEF
AAOCAQ8AMIIBCgKCAQEA2DpSVXawMOMvJgoLnNDjnVHSImyZXEwPNbvaEPW9oHUL
8ZdcRGgwcqchlSnjle1xEDFSVC+ZX+y/mPuU5KgG/AYdfCa4wlpCgh4v+Cx9QoJS
s1UsMVBvDjE9uUHh2UJb+aQAelOmaugJGhHnclW8Z29H5jV6gZpjkRPPhOfcOBXl
K/4uy8JKnjEHofnN00c8qkF4FyHHfrqx6ULKrjJ+rhSLxCYwwklQorVuoASOblxy
j28aCsuHUCwGUfSDG/mRpvEbZrDb9mjDml6A5IF+5kjaYu+FA44oK7MaKjuVLy4U
mQ3jQJmLYfRZiiWHtFibuHkBKZthI9lP5d1xYyIN5QIDAQABo0IwQDAOBgNVHQ8B
Af8EBAMCAQYwDwYDVR0TAQH/BAUwAwEB/zAdBgNVHQ4EFgQUwmkNQtI49ZcyFE1Q
vTQVSwJW2VswDQYJKoZIhvcNAQELBQADggEBAHYj6cKCDqDF+hfaRS4XysyQcl2v
mGtgE3a+g/stcFJzR508eVz6ycglYHAsNgAWszD+eLRZmBvo6cp4bpNPwEZkOpUd
CHtCQeZEk3v5sP6I1xvMUSynwkMb0GfUK7Dj0XRlT+2Xr9XUJmJFDCVkYpQnWCcC
Pdt5S8aBqEubFGMJjybVSO7Q0+7Ud4JoxdsMgr0J0mKwIhEv3o16YK2AInmfNSu2
6FDpyQkPQnLyV1o1mNZSyZ4fao8ANxb75K9RrqRma5DQsM+mpw0z9MRd9usrKe3c
X8XHUuNNi44GGS+bQWipEvaQo99znfRpETB6LNNHEwAqafuAEzbCSj3h5eo=
-----END CERTIFICATE-----
```

Those files are also hosted on the OPIN Directory PKI: [Root CA](http://crl.pki.opinbrasil.com.br/root-ca.pem) and [Issuing CA](http://crl.pki.opinbrasil.com.br/issuer-ca.pem)


**client_id:** On this field you must provide a client_id that was generated when doing a [DCR](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2-ptbr.md) against the server to be tested using the credentials above. 


Make sure that the Software Statement used has been registered with the DADOS role.

#### Resouce

**consentUrl:** Provide the URI used to access the Customer Data Consent API Resource.

**brazilCpf:** Provide the CPF of the testing user created for the scope of those tests. This CPF will be used when creating a ConsentID on every single test plan executed by the Conformance Suite.

**brazilCnpj:** If the institution wishes to test a User of type Business, also provide the CNPJ that will be used to create the Consent. This field is not mandatory.

**Business or Personal Products:** Select whether the Conformance Suite will use Customer Personal Permissions or Business Personal Permission when obtaining data from the server. If the field brazilCnpj is provided, do select Business Personal Permission to be used.

#### Directory

**Directory ClientID:** Client ID for this Client on the Open Insurance Directory. This is used to obtain an access token, which is used to retrieve the software statement.

Once everything is configured, click on "Create Test Plan":

![image](uploads/811428a60528d0e1796426922a5b534f/image.png)

# Execute Test modules

Once test plans are created, you will be redirected to the test plan page. To start executing the tests, select the test module to be executed, and click on the "Run test" button:

![image](uploads/7ef53db59074b434c8d00cdeb48edd47/image.png)

Please read the description of the test in the light blue box near the top of the log page – this may contain specific instructions; for example, one test requires that the user rejects the authentication process. If applicable, the test will ask you to approve (or deny or ignore) the request on the relevant authentication device.

When the test is complete, press “Continue Plan” to start the next test, or “Return to Plan” to view your progress.

If you require support, please open an issue in this GitLab by visiting this [link](https://gitlab.com/openinsurancebrazil/conformance-suite/-/issues)

If it relates to a test failure, please include a link to the relevant log-detail.html, or if using a local install the downloaded log file. Once you have successfully completed testing, please follow the Certification instructions to complete the certification process.

# Test Plan List

26 Unique Test Modules have been already released for the Certification of Version 2 of the Phase 2 APIs. Those tests are separated into six different test plans, one for each functional API plus one for the structural tests. The specification for each module is described in the test summary:

* Functional tests for Consents API - version 1.0.0
   * opin-preflight-check-test
   * opin-consent-api-test
   * opin-consent-api-status-test
   * opin-consent-api-test-negative
   * opin-consent-api-test-permission-groups
   * opin-consent-api-test-client-limits
   * opin-consent-api-status-declined-test
   * opin-consent-api-expired-consent-test
   * opin-consents-api-delete-test
   * opin-consent-inavlid-user-test
* Functional tests for Resources API - version 1.0.0
   * opin-resources-api-test
   * opin-resources-api-test-404-customer-data
   * opin-resources-api-pagination-test
* Functional tests for Customer Personal API - version 1.1.0
   * opin-customer-personal-data-api-test
   * opin-customer-personal-api-wrong-permissions-test
* Functional tests for Customer Business API - version 1.1.0
   * opin-customer-business-data-api-test
   * opin-customer-business-api-wrong-permissions-test
* Functional tests for Patrimonial API - version 1.1.0
   * opin-patrimonial-api-test
   * opin-patrimonial-api-wrong-permissions-test
   * opin-patrimonial-resources-api-test
   * opin-patrimonial-residencial-api-branch-test
* Structural tests
   * opin-consents-api-structural-test
   * opin-resources-api-structural-test
   * opin-customer-personal-api-structural-test
   * opin-customer-business-api-structural-test
   * opin-patrimonial-api-structural-test 

---

*Conteúdo baixado em 16/09/2026, 15:38:47*
