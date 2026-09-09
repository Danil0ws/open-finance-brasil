# [EN] Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3

## Foreword

Este documento também está disponível em [Português](file:///C:/wiki/spaces/DraftOF/pages/76251182)

The Open Finance Brasil Initial Structure is responsible for creating standards and specifications necessary to meet the requirements and obligations of the Brasil Open Finance Legislation as originally outlined by the [Brasil Central Bank](https://www.bcb.gov.br/content/config/Documents/BCB_Open_Banking_Communique-April-2019.pdf). There is a possibility that some of the elements of this document may be the subject to patent rights. OFBIS shall not be held responsible for identifying any or all such patent rights.

Open Finance Brasil Financial-grade API Security Profile 1.0 consists of the following parts:

-   Open Finance Brasil Financial-grade API Security Profile 1.0
    
-   [Open Banking Brasil Dynamic Client Registration Profile 1.0](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76709980/EN+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3)
    

These parts are intended to be used with [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [OIDC](https://openid.net/specs/openid-connect-core-1_0.html), [FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) and [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html)

## Introduction

The Open Finance Brasil Financial-grade API is a highly secured OAuth profile that aims to provide specific implementation guidelines for security and interoperability which can be applied to APIs in the Brasil Open Finance area that require a higher level of privacy than provided by standard [Financial-grade API Security Profile 1.0 - Part 2: Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html). Among other enhancements, this specification addresses privacy considerations identified in [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) that are relevent in the Open Finance Brasil specifications but have not, so far, been required by other jurisdictions.

Although it is possible to code an OpenID Provider and Relying Party from first principles using this specification, the main audience for this specification is parties who already have a certified implementation of [Financial-grade API Security Profile 1.0 - Part 2: Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and want to achieve certification for the Brasil Open Finance programme.

## Notational Conventions

The key words "shall", "shall not", "should", "should not", "may", and "can" in this document are to be interpreted as described in [ISO Directive Part 2](https://www.iso.org/sites/directives/current/part2/index.xhtml).

These key words are not to be used as lexicon terms such that any occurrence of them shall be interpreted as key words and are not to be interpreted with their natural language meanings.

## 1\. Scope

This document specifies the method of

-   applications to obtain the OAuth tokens in an appropriately secure manner for higher risk access to data in a manner that meets the requirements of [Open Finance Brasil](https://www.in.gov.br/en/web/dou/-/resolucao-conjunta-n-1-de-4-de-maio-de-2020-255165055);
    
-   applications to use OpenID Connect to identify the customer; and
    
-   applications to use OpenID Connect to assert identity of the customer;
    

This document is applicable to all participants engaging in Open Finance in Brasil.

## 2\. Normative references

The following referenced documents are indispensable for the application of this document. For dated references, only the edition cited applied. For undated references, the latest edition of the referenced document (including any amendments) applies.

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

[RFC6749](https://tools.ietf.org/html/rfc6749) - The OAuth 2.0 Authorization Framework

[RFC6750](https://tools.ietf.org/html/rfc6750) - The OAuth 2.0 Authorization Framework: Bearer Token Usage

[RFC7636](https://tools.ietf.org/html/rfc7636) - Proof Key for Code Exchange by OAuth Public Clients

[RFC6819](https://tools.ietf.org/html/rfc6819) - OAuth 2.0 Threat Model and Security Considerations

[RFC7515](https://tools.ietf.org/html/rfc7515) - JSON Web Signature (JWS)

[RFC7519](https://tools.ietf.org/html/rfc7519) - JSON Web Token (JWT)

[RFC7591](https://tools.ietf.org/html/rfc7591) - OAuth 2.0 Dynamic Client Registration Protocol

[RFC7592](https://tools.ietf.org/html/rfc7592) - OAuth 2.0 Dynamic Client Registration Management Protocol

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[OIDC](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0 incorporating errata set 1

[FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[OIDD](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0 incorporating errata set 1

[OIDR](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0 incorporating errata set 1

[RFC8705](https://tools.ietf.org/html/rfc8705) - OAuth 2.0 Mutual TLS Client Authentication and Certificate Bound Access Tokens

[JARM](https://bitbucket.org/openid/fapi/src/master/Financial_API_JWT_Secured_Authorization_Response_Mode.md) - Financial-grade API: JWT Secured Authorization Response Mode for OAuth 2.0 (JARM)

[PAR](https://tools.ietf.org/html/draft-ietf-oauth-par) - OAuth 2.0 Pushed Authorization Requests

[JAR](https://tools.ietf.org/html/draft-ietf-oauth-jwsreq) - OAuth 2.0 JWT Secured Authorization Request

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[FAPI-2-Baseline](https://bitbucket.org/openid/fapi/src/master/FAPI_2_0_Baseline_Profile.md) - Financial-grade API Security Profile 2.0 - Part 1: Baseline

[FAPI-2-Advanced](https://bitbucket.org/openid/fapi/src/master/FAPI_2_0_Advanced_Profile.md) - Financial-grade API Security Profile 2.0 - Part 2: Advanced

[LIWP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md) - OIDF FAPI WG Lodging Intent Working Paper

[OFB-FAPI-DCR](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID3.html) - Open Banking Brasil Financial-grade API Dynamic Client Registration Profile 1.0

[RFC4648](https://tools.ietf.org/html/rfc4648) - The Base16, Base32, and Base64 Data Encodings

## 3\. Terms and definitions

For the purpose of this document, the terms defined in [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [OpenID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html) and ISO29100 apply.

## 4\. Symbols and Abbreviated terms

-   **API** \- Application Programming Interface
    
-   **CSRF** \- Cross Site Request Forgery
    
-   **DCR** \- Dynamic Client Registration
    
-   **FAPI** \- Financial-grade API
    
-   **HTTP** \- Hyper Text Transfer Protocol
    
-   **MFA** \- Multi-Factor Autentication
    
-   **OFBIS** \- Open Finance Brasil Initial Structure
    
-   **OIDF** \- OpenID Foundation
    
-   **REST** \- Representational State Transfer
    
-   **TLS** \- Transport Layer Security
    

## 5\. Brasil Open Finance Security Profile

### 5.1. Introduction

The Brasil Open Finance Security profile specifies additional security and identity requirements for high risk API resources protected by the OAuth 2.0 Authorization Framework that consists of [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html), [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and other specifications.

This profile describes security and features provisions for a server and client that are necessary for the Brasil Open Finance Programme by defining the measures to mitigate or address:

-   attacks that address privacy considerations identified in clause 9.1 of \[FAPI1 Advanced\]
    
-   the requirement to support fine-grained access to resources for data minimisation purposes
    
-   the requirement to convey the Authentication Context Request that was performed by an OpenID Provider to a Client to enable a appropriate client management of customer conduct risk.
    

### 5.2. Open Finance Brasil security provisions

#### 5.2.1. Introduction

Open Finance Brasil has a requirement to address privacy considerations that were identified but not addressed in the [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) final specification without imposing additional requirements on Authorisation Servers being proposed in [FAPI-2-Baseline](https://bitbucket.org/openid/fapi/src/master/FAPI_2_0_Baseline_Profile.md).

This profile outlines the client management requirements needed to support the broader Open Finance Brasil ecosystem.

As a profile of the OAuth 2.0 Authorization Framework, this document mandates the following for the Brasil Open Finance Security profile.

#### 5.2.2. Authorization server

The Authorization Server shall support the provisions specified in clause 5.2.2 of [Financial-grade API Security Profile 1.0 - Part 2: Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html)

In addition, the Authorization Server

1.  shall perform client authentication using private\_key\_jwt;
    
2.  shall require requests of the type "pushed authorization requests" PAR;
    
3.  shall distribute discovery metadata (such as the authorization endpoint) via the metadata document as specified in [OIDD](https://openid.net/specs/openid-connect-discovery-1_0.html) and \[RFC8414\] (".well-known");
    
4.  shall support the claims parameter as defined in clause 5.5 [OpenID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html);
    
5.  shall support the acr "urn:brasil:openbanking:loa2" as defined in section 5.2.2.3;
    
6.  should support the acr "urn:brasil:openbanking:loa3" as defined in section 5.2.2.3;
    
7.  shall implement the userinfo endpoint as defined in clause 5.3 [OpenID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html);
    
8.  shall support parameterized OAuth 2.0 resource scope consent as defined in clause 6.3.1 [OIDF FAPI WG Lodging Intent Pattern](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
9.  may support [Financial-grade API: Client Initiated Backchannel Authentication Profile](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md);
    
10.  (withdrawn temporarily);
     
11.  shall support refresh tokens;
     
12.  shall issue access tokens with an expiry no greater than 900 seconds and no less than 300 seconds;
     
13.  shall always include an acr claim in the id\_token;
     
14.  shall support the response\_type value code id\_token;
     
15.  shall not allow refresh token rotation;
     
16.  shall ensure that, in case of sharing the Authorization Server for other services, in addition to Open Finance, it does not disclose and/or allow the use of non-certified methods in the Open Finance environment;
     
17.  shall ensure that the settings disclosed to other participants through OpenID Discovery (indicated by the Well-Known file registered in the Directory) are restricted to the operating modes to which the institution has certified;
     
     1.  shall keep in your settings the methods for which there are still active clients;
         
     2.  shall update the records that use non-certified methods, through bilateral treatment between the institutions involved;
         
18.  shall refuse requests, for the Open Finance environment, that are outside the modes of operation to which the institution has certified its Authorization Server;
     
19.  the minimum expiration time of request\_uri must be 60 seconds;
     
20.  shall deny all requests without header x-fapi-interaction-id on protected resources endpoints;
     
21.  must require the use of Proof Key for Code Exchange (PKCE);
     
22.  must require the use of subject\_type “_public_”;
     
23.  must require the use of response\_mode “fragment”;
     
24.  _shall issue refresh\_tokens (JWT or opaque) without an expiration period in scenarios where it is necessary._
     

##### 5.2.2.1. ID Token as detached signature

The Authorization Server shall support the provisions specified in clause 5.2.2.1 of [Financial-grade API Security Profile 1.0 - Part 2: Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html)

1.  **Shall encrypt the id\_token in callback and token endpoint;**
    
2.  For the encryption of the id\_token, a key available in the JWKS informed in the jwks\_uri parameter, with the attribute “use”:”enc”, during the client registration must be used, indicated through the kid header of the JWT document;
    
3.  The use of other headers to indicate the key used, such as x5u, x5c, jku or jkw is prohibited as defined in clause 2 [OIDC](https://openid.net/specs/openid-connect-core-1_0.html).
    

##### **5.2.2.2. "sub" Claim clarifications**

This profile uses the official definition found at: [Analise requisitos de criptografia ID\_TOKEN](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251250/Analise+requisitos+de+criptografia+ID+TOKEN). This means that the sub is an identifier that is never transferred or changed to the end user within the Account Servicing Payment Service Provider (ASPSP).

##### 5.2.2.3. Requesting the "urn:brasil:openbanking:loa2" or "urn:brasil:openbanking:loa3" Authentication Context Request

This profile defines "urn:brasil:openbanking:loa2" and "urn:brasil:openbanking:loa3" as new Authentication Context Request (ACR) classes.

-   LoA2: Authentication performed using single factor;
    
-   LoA3: Authentication performed using multi factor (MFA)
    

The following rules are applicable to the authentication mechanism of Open Finance Brazil API's:

-   In accordance to Art. 17 of [Joint Resolution nº 01 - Open Banking Brasil](https://www.in.gov.br/en/web/dou/-/resolucao-conjunta-n-1-de-4-de-maio-de-2020-255165055), institutions must adopt procedures and controls for client authentication compatible with those applicable in their electronic service channels.
    
-   In accordance with the regulation, it is suggested that:
    
    -   For Read-Only APIs (Phase 2): the Authorization Servers should adopt, at least, an authentication method compatible with LoA2; and
        
    -   For Read-Write API's (subsequent phases): the Authorization Servers should adopt an authentication method compatible with LoA3 or higher.
        

In all cases, the adoption of a more rigorous authentication mechanism (LoA3 or higher) is at the discretion of the Bank (ASPSP), according to its risk assessment and in a manner compatible with the mechanisms usually employed.

Authentication factors clarification

The authentication methods are:

-   Something you know, such as password or phrase
    
-   Something you have, such as token, smartcard or device
    
-   Something you are, meaning an authentication that makes use of physical characteristics, such as biometric validation.
    

To performe a MFA authentication is necessary that the end user presents at least two different methods as listed above. A unique method used more than once - ie. presenting passwords - is not accepted as MFA.

**5.2.2.4 Mandatory scopes on the well-known endpoint**

The authorization server must declare the scopes below in its well-known endpoint, regardless of whether the institution provides the products related to the scopes listed below:

-   invoice-financings
    
-   financings
    
-   loans
    
-   unarranged-accounts-overdraft
    
-   bank-fixed-incomes
    
-   credit-fixed-incomes
    
-   variable-incomes
    
-   treasure-titles
    
-   funds
    
-   exchanges
    

The scopes not listed above must be declared if the institution provides products related to them  
(i.e.: accounts, payments)

#### 5.2.3. Confidential client

A confidential client shall support the provisions specified in clause 5.2.3 of [Financial-grade API Security Profile 1.0 - Part 2: Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html),

In addition, the confidential client

1.  shall support Pushed Authorisation Requests [PAR](https://tools.ietf.org/html/draft-ietf-oauth-par);
    
2.  shall support parameterized OAuth 2.0 resource scope consent as defined in clause 6.3.1 [OIDF FAPI WG Lodging Intent Pattern](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
3.  shall support refresh tokens;
    
4.  shall not populate the acr claim with required values;
    
5.  shall require the acr claim as an essential claim;
    
6.  shall not allow refresh tokens rotation feature;
    
7.  shall send header x-fapi-interaction-id on FAPI endpoints;
    

## 6\. Security considerations

Participants shall support all security considerations specified in clause 8 [Financial-grade API Security Profile 1.0 - Part 1: Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and the [Brazilian Central Bank Open Banking Security Manual](data/references/Instrução_Normativa_BCB_134.md). The Brazilian ICP issues RSA x509 certificates only therefor section removes for simplicity support for EC algorithms and requires that only IANA recommended encryption algorithms be used.

### 6.1. Message Content Signing Considerations (JWS)

JWS standad defined in [RFC7515](https://tools.ietf.org/html/rfc7515) shall be adopted to ensure integrity and non-repudiation of information processed in sensitive API's (message sign requirement is indicated at API's documentation/swagger), which includes:

-   Header (JSON Object Signing and Encryption - JOSE Header), which defines the algorithm used and includes information about the public key or certificate that can be used to validate the signature;
    
-   Payload (JWS Payload): content itself as detailed in the API specification;
    
-   Digital signature (JWS Signature): digital signature, performed according to header parameters.
    

1.  Each of elements above must be encoded using the Base64url pattern RFC4648 and the elements must be concatenated with "." (JWS Compact Serialization method as defined in [RFC7515](https://tools.ietf.org/html/rfc7515)).
    
2.  The payload of signed messages (request JWT and response JWT) shall include the following claims as defined at [RFC7519](https://openbanking-brasil.github.io/specs-seguranca/JWT):
    

-   aud (in the JWT request): the Resource Provider (eg the institution holding the account) must validate if the value of the aud field matches the endpoint being triggered;
    
-   aud (in JWT response): the API client (eg initiating institution) shall validate if the value of the aud field matches its own organisationId listed in the directory;
    
-   iss (in the JWT request and in the JWT response): the receiver of the message shall validate if the value of the iss field matches the organisationId of the sender;
    
-   jti (in the JWT request and in the JWT response): the value of the jti field shall be filled with the UUID defined by the institution according to \[RFC4122\] version 4;
    
-   iat (in the JWT request and in the JWT response): the iat field shall be filled with the message generation time and according to the standard established in RFC7519 to the NumericDate format.
    
-   cty (in the JWT request and in the JWT response): the cty field shall be filled in the normal case in which nested signing or encryption operations are not employed, the use of this Header Parameter is not recommended. In the case that nested signing or encryption is employed, this Header Parameter must be present; in this case, the value must be "JWT", to indicate that a Nested JWT is carried in this JWT. While media type names are not case sensitive, it is recommended that "JWT" always be spelled using uppercase characters for compatibility with legacy implementations.
    

1.  The HTTP content-type of requests and responses with JWS messages shall be defined as: "application/jwt".
    
2.  The JOSE header must contain the following attributes:
    

-   alg - shall be filled with the value PS256";
    
-   kid - shall be filled with the key identifier value used for the signature;
    
-   In case of error in signature validation by Resource Provider the API provider shall return HTTP error message with status code 400 and the ResponseError content shall include, in the code property, the content BAD\_SIGNATURE.
    
-   Errors in validating the signed messages received by the client application (eg payment initiator) must be logged and the Resource Provider (eg account holding institution) must be notified.
    

1.  The receiver shall validate the consistency of the JWS message's digital signature exclusively based on the information obtained from the directory, that is, based on the keys published in the institution's JWKS in the directory.
    
2.  Signatures must be performed using the digital signature certificate specified in the [Open Finance Brazil Certificates Standard](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76710230/EN+Padr+o+de+Certificados+Open+Finance+Brasil+1.0);
    
3.  the iat claim must be numeric in Unix Time format GMT+0 with a tolerance of +/- 60 seconds;
    
4.  the jti claim must be unique for a clientId within a time frame of 86,400 seconds (24h), and cannot be reused within this period. In case of reuse, the HTTP error code 403 shall be return. Any other case must follow RFC 6749 instructions in item 5.2.
    

### 6.1.1. Signing algorithm considerations

For JWS, both clients and Authorization Servers

shall use PS256 algorithm;

#### 6.1.2. Encryption algorithm considerations

For JWE, both clients and Authorization Servers

shall use RSA-OAEP with A256GCM

#### 6.1.3. Secure Use of Transport Layer Security considerations

For TLS, Authorization Server endpoints and Resource Server endpoints used directly by the Client

1.  shall support TLS\_ECDHE\_RSA\_WITH\_AES\_128\_GCM\_SHA256
    
2.  shall support TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384
    
3.  The "TLS Session Resumption" e "TLS Renegotiation" features shall be disabled
    

## 7\. Data Sharing Considerations

### 7.1. Authorisation Mechanism

#### 7.1.1. Introduction

Existing mechanisms for appropriately managing access to resources defined in [RFC6749](https://tools.ietf.org/html/rfc6749) are insufficient to meet the requirements for a modern data sharing ecosystem. Leveraging static scope strings does not provide consumers control of sufficient granularity to share with third parties. Open Finance Brasil have elected to implement a [Consent API](https://openbanking-brasil.github.io/areadesenvolvedor/swagger/swagger_consents_apis.yaml) as a OAuth 2.0 protected resource that can be used to manage fine grain access to resources. The reference to the Consent Resource will be conveyed as part of an OAuth 2.0 dynamic resource scope.

#### 7.1.2. Dynamic Consent Scope Definition

This profile defines OAuth 2.0 dynamic scope "consent" as follows:

-   string 'consent' or ‘recurring-consent’ and
    
-   delimiter of a colon ":"; and
    
-   Consent API REST Resource Id as returned by a successful creation of Open Finance Consent Resource;
    

In addition:

-   the Consent Resource Id must include url safe characters only;
    
-   the Consent Resource Id must be namespaced;
    
-   the Consent Resource Id must have the properties of a nonce Nonce;
    

#### 7.1.3. Dynamic Consent Scope Example

consent:urn:bancoex:C1DD33123

### 7.2. Authorisation Life Cycle

#### 7.2.1. Introduction

The Consent Resource has a life cycle that is managed seperately and distinctly from the OAuth 2.0 Authorisation Framework. The state transitions and expected behaviours and error conditions expected of REST Resources protected with this profile are defined in the functional API specifications published by Open Finance Brasil.

#### 7.2.2. Authorization server

In addition to the requirements outlined in Open Finance Brasil security provisions the Authorization Server

1.  shall only issue refresh\_tokens when linked to an active and valid consent;
    
    1.  Must not issue refresh\_token when consent status is "CONSUMED" (for phase 3);
        
    2.  Must issue an access\_token through the grant\_type client credentials when consent status is "CONSUMED"(for phase 3).
        
2.  shall only share access to resources when presented access\_token linked to an active consent and with the status "AUTHORISED“. For tokens generated with the scope: payments or recurring-payments, the status of the consent will not be validated.
    
    1.  In the scenario of receiving an invalid token, status code 401 should be returned.
        
3.  shall revoke refresh tokens and, access tokens where aplicable, when the linked Consent Resource is deleted;
    
4.  shall ensure access tokens are issued with sufficient scope necessary for access to data specified in the Permission element of a linked Consent Resource object;
    
5.  shall not reject an authorisation request requesting scopes broader than those necessary to access data specified in the Permissions element of a linked Consent Resource object;
    
6.  may reduce requested scope to a level sufficient to enable access to data resources specified in the Permissions element of a linked Consent Resource object;
    
7.  shall retain a complete audit history of the consent resource in accordance with current Central Bank brazilian regulation;
    
8.  shall return authentication failure and return code \_accessdenied in the error parameter (as specified in section 4.1.2.1 of [RFC6749](https://tools.ietf.org/html/rfc6749)) if the CPF of the authenticated user is not the same as indicated in the loggedUser element of the Consent Resource Object;
    
9.  shall return authentication failure and return code \_accessdenied in the error parameter (as specified in section 4.1.2.1 of [RFC6749](https://tools.ietf.org/html/rfc6749)) if the businessEntity element has not been populated in the related Consent Resource Object and the user has selected or authenticated by using a credential related to a business account;
    
10.  an autenticated or selected business account's CNPJ must match the value present in the businessEntity element of the Consent Resource Object. In case of divergence authorization server shall return authentication failure and return code _access\_denied_ in the error parameter (as specified in section 4.1.2.1 of [RFC6749](https://tools.ietf.org/html/rfc6749));
     
11.  shall ensure _refresh\_token_ expiration time is at least equal to the linked consent resource expiration time.
     

#### Confidential Client

In addition to the requirements outlined in Open Finance Brasil security provisions the Confidential Client

1.  shall revoke where possible and cease usage of refresh and access tokens that are bound to a Consent Resource that has been deleted;
    
2.  shall delete Consent Resource that are expired;
    

## 8\. Acknowledgements

With thanks to all who have set the foundations for secure and safe data sharing through the formation of the OpenID Foundation FAPI Working Group, the Open Finance Brasil GT Security and to the pioneers who will stand on their shoulders.

The following people contributed to this document:

-   Alexandre Siqueira (Mercado Pago)
    
-   Joseph Heenan (Authlete)
    
-   Marcos Rodrigues (Itaú)
    
-   Mário Ginglass (BNDES)
    
-   Nic Marcondes (Quanto)
    
-   Ralph Bragg (Raidiam)
    

## Appendix A. Notices

Copyright (c) 2023 Open Finance Brasil Initial Structure.

The Open Finance Brasil Initial Structure (OFBIS) grants to any Contributor, developer, implementer, or other interested party a non-exclusive, royalty-free, worldwide copyright license to reproduce, prepare derivative works from, distribute, perform and display, this Implementers Draft or Final Specification solely for the purposes of (i) developing specifications, and (ii) implementing Implementers Drafts and Final Specifications based on such documents, provided that attribution be made to the OFBIS as the source of the material, but that such attribution does not indicate an endorsement by the OFBIS.

The technology described in this specification was made available from contributions from various sources, including members of the OpenID Foundation, the Open Finance Brasil GT Security Working Group and others. Although the Open Finance Brasil Initial Structure has taken steps to help ensure that the technology is available for distribution, it takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this specification or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any independent effort to identify any such rights. The Open Finance Brasil Initial Structure and the contributors to this specification make no (and hereby expressly disclaim any) warranties (express, implied, or otherwise), including implied warranties of merchantability, non-infringement, fitness for a particular purpose, or title, related to this specification, and the entire risk as to implementing this specification is assumed by the implementer. The Open Finance Brasil Intellectual Property Rights policy requires contributors to offer a patent promise not to assert certain patent claims against other contributors and against implementers. The Open Finance Brasil Initial Structure invites any interested party to bring to its attention any copyrights, patents, patent applications, or other proprietary rights that may cover technology that may be required to practice this specification.

## Author's Address

OFBIS GT Security

Open Finance Brasil Initial Structure

Email: [gt-seguranca@openfinancebrasil.org.br](mailto:gt-seguranca@openfinancebrasil.org.br)

URI: [https://openfinancebrasil.org.br](https://openfinancebrasil.org.br/)
