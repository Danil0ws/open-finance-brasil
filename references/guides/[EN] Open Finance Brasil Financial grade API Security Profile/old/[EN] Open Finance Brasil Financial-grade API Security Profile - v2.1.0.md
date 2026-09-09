# [EN] Open Finance Brasil Financial-grade API Security Profile - v2.1.0

13falsedefaultlisttrue

## **Foreword**

Este material também está disponível em Português  
  
Associação Open Finance Brasil is responsible for creating standards and specifications necessary to meet the requirements and obligations of the Brasil Open Finance Legislation, as originally outlined by the [Brasil Central Bank](https://www.bcb.gov.br/content/config/Documents/BCB_Open_Banking_Communique-April-2019.pdf) and the National Monetary Council. There is a possibility that some of the elements of this document may be subject to copyright or patent rights. Associação Open Finance Brasil shall not be held responsible for identifying any or all such rights.

The Open Finance Brasil Security Profile (FAPI-BR) consists of the following parts:

-   Open Finance Brasil Financial-grade API Security Profile - v2.1.0
    
-   Open Finance Brasil Dynamic Client Registration - v2.1.0
    

## 1\. **Introduction**

The Open Finance Brasil Security Profile is an implementation of the [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) profile that provides specific implementation guidelines for security and interoperability that shall be applied to APIs exposed in the Open Finance Brasil ecosystem. The Open Finance Brasil Security Profile is a subset of the [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html); however, this subset does not refer to the removal of security mechanisms from the original profile, but rather to the mandatory use of certain characteristics of that profile in order to facilitate interoperability among financial institutions.

This profile describes the capabilities and security features that shall be provided by servers and clients that are necessary for the Open Finance Brasil ecosystem, defining measures to mitigate or address:

-   attacks that address privacy considerations identified in clause 9.1 of [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html);
    
-   the requirement to support fine-grained access to resources, for data minimisation purposes;
    
-   the requirement to convey the Authentication Context Request (acr claim) that was performed by an OpenID Provider, in order to enable appropriate risk management arising from user access.
    

This profile also specifies the method for applications to:

-   obtain the OAuth tokens in an appropriately secure manner for access to critical data in a manner that meets the requirements of [Open Finance Brasil](data/references/Resolução_Conjunta_1.md);
    
-   use OpenID Connect to identify the Open Finance user; and
    
-   use OpenID Connect to assert the identity of the client.
    

Although it is possible to code from scratch an Authorization Server that complies with the Open Finance Brasil Security Profile, the target audience of this specification is providers that already have a certified implementation of [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and wish to make the necessary adjustments to obtain certification for the Open Finance Brasil Security Profile.

These parts are intended to be used with [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [OIDC](https://openid.net/specs/openid-connect-core-1_0.html), [FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) and [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html).

## 2\. Notational Conventions

The key words "shall", "shall not", "should", "should not", "may", and "can" in this document are to be interpreted as described in [ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml).

These key words are not to be used as lexicon terms such that any occurrence of them shall be interpreted as key words and are not to be interpreted with their natural language meanings.

## 3\. **Normative references**

The following referenced documents are indispensable for the application of this document. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments) applies.

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md) - OIDF FAPI WG Lodging Intent Working Paper

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

[JAR](https://tools.ietf.org/html/draft-ietf-oauth-jwsreq) - OAuth 2.0 JWT Secured Authorization Request

[OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0

[OIDC-Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0

[OIDC-Registration](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0

[PAR](https://tools.ietf.org/html/draft-ietf-oauth-par) - OAuth 2.0 Pushed Authorization Requests

[RFC4648](https://tools.ietf.org/html/rfc4648) - The Base16, Base32, and Base64 Data Encodings

[RFC6749](https://tools.ietf.org/html/rfc6749) - The OAuth 2.0 Authorization Framework

[RFC6750](https://tools.ietf.org/html/rfc6750) - The OAuth 2.0 Authorization Framework: Bearer Token Usage

[RFC6819](https://tools.ietf.org/html/rfc6819) - OAuth 2.0 Threat Model and Security Considerations

[RFC7515](https://tools.ietf.org/html/rfc7515) - JSON Web Signature (JWS)

[RFC7519](https://tools.ietf.org/html/rfc7519) - JSON Web Token (JWT)

[RFC7591](https://tools.ietf.org/html/rfc7591) - OAuth 2.0 Dynamic Client Registration Protocol

[RFC7592](https://tools.ietf.org/html/rfc7592) - OAuth 2.0 Dynamic Client Registration Management Protocol

[RFC7636](https://tools.ietf.org/html/rfc7636) - Proof Key for Code Exchange by OAuth Public Clients

[RFC8414](https://tools.ietf.org/html/rfc8414) - OAuth 2.0 Authorization Server Metadata

[RFC8705](https://tools.ietf.org/html/rfc8705) - OAuth 2.0 Mutual TLS Client Authentication and Certificate Bound Access Tokens

## 4\. Symbols and abbreviated terms

-   **API** \- Application Programming Interface
    
-   **DCR** \- Dynamic Client Registration
    
-   **FAPI** \- Financial-grade API
    
-   **HTTP** \- Hyper Text Transfer Protocol
    
-   **MFA** \- Multi-Factor Authentication
    
-   **OIDF** \- OpenID Foundation
    
-   **REST** \- Representational State Transfer
    
-   **TLS** \- Transport Layer Security
    

## 5\. Open Finance Brasil Security Profile

### 5.1. Authorization Server

To address the privacy considerations identified in Open Finance Brasil, which were not fully addressed in the final [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) specification, and to support client management in the Open Finance Brasil ecosystem, the Open Finance Brasil Security Profile establishes that the Authorization Server shall support the provisions specified in clause 5.2.2 of [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html).

In addition, the Authorization Server shall:

1.  shall perform client authentication using private\_key\_jwt;
    
2.  shall require Pushed Authorization Requests (PAR);
    
3.  shall publish discovery metadata (including the authorization endpoint) via the metadata document as specified in [OIDC-Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) and [RFC8414](https://tools.ietf.org/html/rfc8414) (".well-known");
    
4.  shall support the claims parameter as defined in clause 5.5 of [OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html);
    
5.  shall support the acr value "urn:brasil:openbanking:loa2" as defined in clause 5.1.1.1;
    
6.  should support the acr value "urn:brasil:openbanking:loa3" as defined in clause 5.1.1.1;
    
7.  shall implement the userinfo endpoint as defined in clause 5.3 of [OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html);
    
8.  shall support the parameterized scope as defined in clause 6.3.1 of [FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
9.  may support [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md);
    
10.  shall support refresh tokens;
     
11.  shall issue access tokens with an expiry time between 300 seconds (minimum) and 900 seconds (maximum);
     
12.  shall support the response\_type value "code id\_token";
     
13.  shall not allow refresh token rotation;
     
14.  shall ensure that, in case of sharing the Authorization Server for other services, in addition to Open Finance, it does not disclose and/or allow the use of non-certified methods in the Open Finance environment;
     
15.  shall ensure that the settings disclosed to other participants through OpenID Discovery (indicated by the Well-Known file registered in the Directory) are restricted to the operating modes to which the institution has certified;
     
16.  shall refuse requests, for the Open Finance environment, that are outside the modes of operation to which the institution has certified its Authorization Server;
     
17.  the minimum expiration time of request\_uri must be 60 seconds;
     
18.  shall refuse requests that do not present the x-fapi-interaction-id header on protected resource endpoints;
     
19.  shall require the use of Proof Key for Code Exchange (PKCE);
     
20.  shall require the use of subject\_type "public";
     
21.  shall require the use of response\_mode "fragment";
     
22.  shall issue refresh\_tokens (JWT or opaque) with no expiration time in scenarios where they are required.
     

#### **5.1.1. ID Token**

The Authorization Server shall support the provisions specified in clause 5.2.2.1 of [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and, in addition, in order to meet specific requirements of the Open Finance Brasil Security Profile, it shall:

1.  shall encrypt the id\_token in callback and token endpoint calls;
    
2.  for the encryption of the id\_token, a key of type "enc" available in the JWKS informed in the jwks\_uri parameter of the client registration (DCR) must be used. The kid of the key used for the id\_token encryption must be indicated in the kid attribute of the JWT header;
    
3.  shall always include the acr claim in the id\_token. The value of the acr claim must be one of the allowed values as defined in the section Authentication contexts (acr);
    
4.  The use of other headers to indicate the key used, such as x5u, x5c, jku or jkw, is prohibited as defined in clause 2 of [OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html).
    

##### 5.1.1.1. **Authentication contexts (acr) - "urn:brasil:openbanking:loa2" or "urn:brasil:openbanking:loa3"**

This profile defines _urn:brasil:openbanking:loa2 (LoA2)_ and _urn:brasil:openbanking:loa3 (LoA3)_ as new Authentication Context Request (ACR) classes.

-   LoA2: authentication mechanism using a single factor;
    
-   LoA3: authentication mechanism using multiple authentication factors.
    

The following guidance must be observed for the authentication mechanism of Open Finance Brasil APIs:

-   In accordance with Art. 17 of Joint Resolution no. 01, institutions must adopt procedures and controls for client authentication compatible with those applicable to access to their electronic service channels.
    
-   In accordance with the regulation in force, it is suggested that:
    
    -   For user authentication in authorisations to access data sharing APIs, Authorization Servers should adopt, at least, a method compatible with LoA2; and
        
    -   For user authentication in authorisations to access payment initiation or service/product contracting APIs, Authorization Servers should adopt an authentication method compatible with LoA3 or higher.
        

In all cases, the adoption of a more rigorous authentication mechanism (LoA3 or higher) is at the discretion of the transmitting/account-holding institution, according to its risk assessment and in a manner compatible with the mechanisms usually employed.

Additional clarification on authentication factors

Authentication factors are:

-   Something you know, such as a password or secret phrase;
    
-   Something you have, such as a token, smartcard or device;
    
-   Something you are, that is, authentication conditioned on the presentation of a physical characteristic that is exclusively yours, such as biometric validation.
    

To perform multi-factor authentication (MFA), it is necessary that the user presents at least two different factors from those listed above. A single factor used more than once – for example, presenting two passwords that the user knows – cannot be accepted as MFA.

#### **5.1.2. "sub" Claim clarifications**

This profile uses the official definition found at: Analise requisitos de criptografia ID\_TOKEN. This means that the sub is an identifier that is never transferred or changed for the end user within the issuer (account-holding/transmitting institution).

#### 5.1.3 **Mandatory scopes on the well-known endpoint**

The authorization server shall mandatorily declare the scopes below in its well-known endpoint, regardless of whether the institution provides the products related to the scopes listed below:

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
    

Scopes not listed above must be declared if the institution provides products related to them (e.g. accounts, payments, etc.).

### 5.2. Cliente confidencial

A confidential client is any client created through a secure method and that has specific access credentials. In the Open Finance Brasil ecosystem, confidential clients are clients that were created through DCR (Dynamic Client Registration). A confidential client shall support the provisions specified in clause 5.2.3 of [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and, in addition, in order to meet specific requirements of the Open Finance Brasil Security Profile, it shall:

1.  shall support encrypted request objects;
    
2.  shall support _PAR_ (pushed authorization requests);
    
3.  shall support the parameterized scope as defined in clause 6.3.1 of [FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
4.  shall support refresh tokens;
    
5.  shall not populate the acr claim with required values;
    
6.  shall require the acr claim as an essential claim;
    
7.  shall support the _private\_key\_jwt_ authentication method;
    
8.  shall not allow the refresh token rotation feature;
    
9.  shall send the _x-fapi-interaction-id_ header on FAPI endpoints.
    

## 6\. Security considerations

Participants shall support all security considerations specified in clause 8 of [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) and in the [Manual de Segurança de Banco Central do Brasil](data/references/Instrução_Normativa_BCB_305.md).

The Brazilian ICP issues RSA x509 certificates only; therefore, for simplicity, this section removes support for EC algorithms and requires that only encryption algorithms recommended by IANA be used.

### 6.1. **Message content signing considerations (JWS)**

JWS standard defined in RFC7515 shall be adopted to ensure integrity and non-repudiation of information processed in sensitive API's (message sign requirement is indicated at API's documentation/swagger), which includes:

-   Header (JSON Object Signing and Encryption - JOSE Header), which defines the algorithm used and includes information about the public key or certificate that can be used to validate the signature;
    
-   Payload (JWS Payload): the content itself as detailed in the API specification;
    
-   Digital signature (JWS Signature): digital signature, performed according to the header parameters.
    

1.  Each of the elements above must be encoded using the Base64url pattern [RFC4648](https://tools.ietf.org/html/rfc4648#section-5) and, once this is done, the elements must be concatenated with "." (JWS Compact Serialization method, as defined in [RFC7515](https://tools.ietf.org/html/rfc7515)).
    
2.  The payload of signed messages (request JWT and response JWT) shall include the following claims as defined in [RFC7519](https://openbanking-brasil.github.io/specs-seguranca/JWT):
    

-   aud (in the JWT request): the Resource Provider (e.g. the institution holding the account) must validate whether the value of the aud field matches the endpoint being triggered;
    
-   aud (in the JWT response): the API client (e.g. initiating institution) shall validate whether the value of the aud field matches its own organisationId listed in the directory;
    
-   iss (in the JWT request and in the JWT response): the receiver of the message shall validate whether the value of the iss field matches the organisationId of the sender;
    
-   jti (in the JWT request and in the JWT response): the value of the jti field shall be filled with the UUID defined by the institution in accordance with \[RFC4122\] using version 4;
    
-   iat (in the JWT request and in the JWT response): the value of the iat field shall be filled with the message generation time and in accordance with the standard established in [RFC7519](#) for the NumericDate format.
    
-   cty (in the JWT request and in the JWT response): the value of the cty field shall be filled in; in the normal case in which nested signing or encryption operations are not employed, the use of this header parameter is not recommended. In the case that nested signing or encryption is employed, this header parameter must be present; in this case, the value must be "JWT", to indicate that a nested JWT is carried in this JWT. While media type names are not case sensitive, it is recommended that "JWT" always be spelled using uppercase characters for compatibility with legacy implementations.
    

1.  The HTTP content-type of requests and responses with JWS messages shall be defined as: "application/jwt".
    
2.  The JOSE header must contain the following attributes:
    

-   alg - shall be filled with the value PS256";
    
-   kid - shall be filled with the key identifier value used for the signature;
    
-   typ - shall be filled with the value JWT.
    
-   In case of error in signature validation by Resource Provider the API provider shall return HTTP error message with status code 400 and the ResponseError content shall include, in the code property, the content BAD\_SIGNATURE.
    
-   Errors in validating the signed messages received by the client application (e.g. payment initiator) must be logged and the Resource Provider (e.g. account-holding institution) must be notified.
    

1.  The receiver shall validate the consistency of the JWS message's digital signature exclusively based on the information obtained from the directory, that is, based on the keys published in the institution's JWKS in the directory.
    
2.  Signatures must be performed using the digital signature certificate specified in the [Open Finance Brazil Certificates Standard](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76710230);
    
3.  the iat claim must be numeric in Unix Time format GMT+0 with a tolerance of +/- 60 seconds;
    
4.  the jti claim must be unique for a clientId within a time frame of 86,400 seconds (24h), and cannot be reused within this period. In case of reuse, the HTTP error code 403 shall be return. Any other case must follow RFC 6749 instructions in item 5.2.
    

### 6.2. Signing algorithm considerations

For JWS, both clients and authorization servers shall use the PS256 algorithm.

### 6.3. Encryption algorithm considerations

For JWE, both clients and authorization servers shall use RSA-OAEP with A256GCM.

### 6.4. Secure use of Transport Layer Security considerations

For TLS, Authentication Server endpoints and Resource Server endpoints used directly by the client:

-   shall support TLS\_ECDHE\_RSA\_WITH\_AES\_128\_GCM\_SHA256;
    
-   shall support TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384;
    
-   The "TLS Session Resumption" and "TLS Renegotiation" features shall be disabled.
    

## 7\. **Parameterized scope considerations**

Existing mechanisms for appropriately managing access to resources defined in [RFC6749](https://tools.ietf.org/html/rfc6749) are insufficient to meet the requirements of a modern data sharing ecosystem. Using static scope strings does not provide consumers with sufficient control and granularity to manage data sharing or resource management with third parties. Open Finance Brasil has elected to implement the parameterized scope ([FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md)) associated with consent/binding APIs to manage fine-grained access to resources.

### 7.1. **Dynamic Consent Scope Definition**

This profile defines OAuth 2.0 dynamic scope "consent" as follows:

-   string "consent", "recurring-consent" or "enrollment"; and
    
-   delimiter of a colon ":"; and
    
-   Consent Resource Id returned by a successful creation of the resource to be granted (e.g. consent, recurring-consent, enrollment).
    

In addition:

-   the Consent Resource Id must include url safe characters only;
    
-   the Consent Resource Id must be namespaced;
    
-   the Consent Resource Id must have the properties of a nonce;
    

Due to the characteristics of the Consent Resource Id and for ease of implementation, many institutions choose to use a UUIDv4 key as the Consent Resource Id; however, this is not a rule, and each institution may choose other methods provided that the rules presented above and also those defined in each API specification are respected.

#### 7.1.1. **Dynamic consent scope example**

Considering that the transmitting/account-holding institution is Banco Exemplo and that it is using UUIDv4 as the Consent Resource Id, the consents/recurring consents/device bindings created against this institution would have the following format, respectively:

-   consent:urn:bancoexemplo:830ce3c6-e9e7-4800-ae93-3e9b29b470f1
    
-   recurring-consent:urn:bancoexemplo:c9a8a741-39a6-4014-bb75-e05934f9d711
    
-   enrollment:urn:bancoexemplo:eb093d20-ccc5-4242-a271-6658f6663712
    

## 8\. **Consent life cycle**

Consent is a fundamental business object, strongly linked to security artefacts (refresh and access tokens). However, its life cycle must be managed independently through its own state machine. The functional API specifications published by Open Finance Brasil define the state transitions, expected behaviours and error conditions for REST resources protected by this profile, ensuring appropriate control over the consent life cycle.

The following requirements aim to instruct the behaviour of the Authorization Server (AS) in relation to the consent life cycle, ensuring that authorisation practices are aligned with regulatory expectations and the security of the entire ecosystem.

### 8.1. Authorization Server

In addition to the requirements outlined in Open Finance Brasil security provisions the Authorization Server:

1.  shall only issue refresh\_tokens when linked to an active and valid consent;
    
    1.  Must not issue refresh\_token when consent status is "CONSUMED" (for payment services);
        
    2.  Must issue an access\_token through the grant\_type client credentials when consent status is "CONSUMED" (for payment services);
        
    3.  In an optimised journey, it shall issue refresh\_tokens as long as at least one of the linked consents is active and valid.
        
2.  shall only share access to resources when presented access\_token linked to an active consent and with the status "AUTHORISED“. For tokens generated with the scope: payments or recurring-payments, the status of the consent will not be validated.
    
    1.  In the scenario of receiving an invalid token, status code 401 should be returned.
        
3.  shall revoke refresh tokens and, access tokens where aplicable, when the linked Consent Resource is deleted;
    
    1.  In an optimised journey, it shall perform the revocation of refresh\_tokens and access\_tokens only if both linked consents are revoked.
        
4.  shall ensure access tokens are issued with sufficient scope necessary for access to data specified in the Permission element of a linked Consent Resource object;
    
5.  shall not reject an authorisation request requesting scopes broader than those necessary to access data specified in the Permissions element of a linked Consent Resource object;
    
6.  may reduce requested scope to a level sufficient to enable access to data resources specified in the Permissions element of a linked Consent Resource object;
    
7.  shall retain records on the consent history to allow the appropriate formation of audit trails in accordance with the regulation in force;
    
8.  shall return authentication failure and the return code access\_denied in the error parameter (as specified in section 4.1.2.1 of [RFC6749](https://tools.ietf.org/html/rfc6749)) if the CPF of the authenticated user is not the same as indicated in the loggedUser element of the related Consent Resource Object;
    
9.  shall return authentication failure and the return code access\_denied in the error parameter (as specified in section 4.1.2.1 of [RFC6749](https://tools.ietf.org/html/rfc6749)) if the businessEntity element has not been populated in the related Consent Resource Object and the user has selected or authenticated using credentials related to a legal entity (business) account;
    
10.  shall condition the authentication or selection of legal entity (business) accounts to the consistency between the CNPJ related to the account(s) and the value present in the businessEntity element of the Consent Resource Object. In case of divergence, it shall return authentication failure and the return code access\_denied in the error parameter (as specified in section 4.1.2.1 of [RFC6749](https://tools.ietf.org/html/rfc6749));
     
11.  shall issue a refresh\_token with a validity period not shorter than the validity of the consent to which it is related, while respecting the other criteria above.
     

### 8.2. **Confidential client**

In addition to the requirements outlined in Open Finance Brasil security provisions, the Confidential Client

1.  shall revoke where possible and cease usage of refresh and access tokens that are bound to a Consent Resource that has been deleted;
    
2.  shall delete Consent Resource that are expired;
    

## Appendix A. Avisos

Copyright (c) 2025 Associação Open Finance Brasil

Associação Open Finance Brasil grants to any Contributor, developer, implementer, or other interested party a non-exclusive, royalty-free, worldwide copyright license to reproduce, prepare derivative works from, distribute, perform and display, this Implementers Draft or Final Specification solely for the purposes of (i) developing specifications, and (ii) implementing Implementers Drafts and Final Specifications based on such documents, provided that attribution be made to Associação Open Finance Brasil as the source of the material, but that such attribution does not indicate an endorsement by Associação Open Finance Brasil.

The technology described in this specification was made available from contributions from various sources, including members of the OpenID Foundation, the Open Finance Brasil Security Working Group and others. Although Associação Open Finance Brasil has taken steps to help ensure that the technology is available for distribution, it takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this specification or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any independent effort to identify any such rights. Associação Open Finance Brasil and the contributors to this specification make no (and hereby expressly disclaim any) warranties (express, implied, or otherwise), including implied warranties of merchantability, non-infringement, fitness for a particular purpose, or title, related to this specification, and the entire risk as to implementing this specification is assumed by the implementer. The Open Finance Brasil Intellectual Property Rights policy requires contributors to offer a patent promise not to assert certain patent claims against other contributors and against implementers. Associação Open Finance Brasil invites any interested party to bring to its attention any copyrights, patents, patent applications, or other proprietary rights that may cover technology that may be required to practice this specification.

## Author's Address

Associação Open Finance - GT Security

Email: [gt-seguranca@openfinancebrasil.org.br](mailto:gt-seguranca@openfinancebrasil.org.br)

URI: [https://openfinancebrasil.org.br](https://openfinancebrasil.org.br/)
