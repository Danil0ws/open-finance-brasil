# [EN] - Perfil CIBA de Segurança do Open Finance Brasil 2.0

## **Introduction**

The Financial-grade API standard provides a profile for OAuth 2.0 tailored for use in financial services. The OAuth method is a standard used by clients to validate the resource owner's identity on an authorization server via an HTTP redirection. Parts 1 and 2 of this specification support this interaction model and are suitable for use cases where the resource owner interacts with the client on a controlled device with a web browser.

However, there are many use cases for initiating payments where the resource owner does not interact with the client in this manner. For example, the resource owner may wish to authorize a payment at a "point of sale" terminal in a store or gas station.

This document addresses the CIBA (Client-Initiated Backchannel Authentication) profile, or OpenID Connect Client-Initiated Backchannel Authentication Flow, which supports this decoupled interaction method. The CIBA specification allows a client, with knowledge of a user identifier, to obtain tokens from the authorization server. User consent is provided on the user's Authentication Device, mediated by the authorization server.

This document profiles the CIBA specification to align it with other parts of the Financial-grade API (FAPI) and provides security recommendations for its use with APIs requiring financial-grade security.

While it is possible to build an OpenID Provider and a Relying Party from scratch using this specification, the primary audience for this document includes parties with a certified Financial-grade API implementation for the Client-Initiated Backchannel Authentication Profile, seeking certification for the Brazil Open Finance program.

### **Notational Conventions**

The keywords "must," "must not," "should," "should not," "may," and "optional" in this document are to be interpreted as described in ISO Directive Part 2. These keywords are not used in their dictionary sense; they are interpreted strictly as normative terms.

### **1\. Scope**

This document specifies methods for:

●      Applications to obtain OAuth tokens via a backchannel authentication flow in a secure manner suitable for higher-risk data access, meeting Open Finance Brasil requirements.

●      Applications that use OpenID Connect CIBA to suggest client identity.

This document applies to all Open Finance participants in Brazil.

### **2\. Normative References**

The following referenced documents are essential for the application of this document. For dated references, only the cited edition applies. For undated references, the latest edition (including amendments) applies:

●      **ISO/IEC Directives Part 2**

●      **RFC6749** - The OAuth 2.0 Authorization Framework

●      **RFC6750** - The OAuth 2.0 Authorization Framework: Bearer Token Usage

●      **RFC7636** - Proof Key for Code Exchange by OAuth Public Clients

●      **RFC6819** - OAuth 2.0 Threat Model and Security Considerations

●      **RFC7515** - JSON Web Signature (JWS)

●      **RFC7519** - JSON Web Token (JWT)

●      **RFC7591** - OAuth 2.0 Dynamic Client Registration Protocol

●      **RFC7592** - OAuth 2.0 Dynamic Client Registration Management Protocol

●      **BCP195** - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

●      **OIDC** - OpenID Connect Core 1.0

●      **FAPI-CIBA** - Financial-grade API: Client-Initiated Backchannel Authentication Profile

●      **FAPI-BR** - Open Finance Brasil Financial-grade API Security Profile 1.0

### **3\. Terms and Definitions**

For the purposes of this document, the terms defined in RFC6749, RFC6750, RFC7636, OpenID Connect Core, CIBA, and ISO29100 apply.

### **4\. Symbols and Abbreviations**

●      **API**: Application Programming Interface

●      **CIBA**: Client-Initiated Backchannel Authentication

●      **FAPI**: Financial-grade API

●      **HTTP**: Hyper Text Transfer Protocol

●      **OIDF**: OpenID Foundation

●      **TLS**: Transport Layer Security

●      **MFA**: Multi-Factor Authentication

### **5\. Brazil Open Finance Security Profile**

#### **5.1 Introduction**

The Open Finance Brasil Security Profile specifies additional security and identity requirements for high-risk API resources protected by the OAuth 2.0 Authorization Framework, including RFC6749, RFC6750, RFC7636, and FAPI-related specifications.

This profile outlines security provisions and requirements for servers and clients necessary for the Open Finance Brasil program, covering:

●      The need to transmit the Authentication Context Request initiated by an OpenID Provider to a Client, enabling proper risk management of user behavior.

●      The requirement for clients to assert a pre-existing client relationship by declaring client identity within the CIBA flow.

#### **5.2 Open Banking Brasil CIBA Security Provisions**

**Authorization Server Requirements:**

●      Maintain the same consent acceptance time as defined for the Hybrid Flow, respecting product configurations.

●      Ensure that the exp field in all id\_tokens is valid for at least 180 days.

●      Support CIBA poll mode (mandatory).

●      Do not support CIBA push or ping modes.

●      Revoke id\_tokens in cases of fraud or security concerns.

**Parameters**

**Validation**

Iss

The Authorization Server must establish a default identifier or set of "iss" identifiers for use in CIBA transactions.  

-   The Authorization Server must not accept an "iss" different from its own default identifier or set of identifiers.
    

Sub

The Authorization Server must verify if the "sub" identifier in question has already been issued to a client/account and if it is valid according to its requirements.

Aud

The Authorization Server must not accept an "aud" different from the client\_id originating the authorization request for the CIBA flow.

exp

"exp" must be established according to the risk policies of the Account Holder's institution. The Authorization Server must not accept authorization requests with a date/time later than "exp".

iat

No specific validations.

auth\_time

No specific validations.

nonce

No specific validations on the Authorization Server (AS).

acr

If present, the AS must only accept values equal to or higher than the authentication requirements of the Account Holder for authorizing payment operations.

amr

If present, the AS must only accept values equal to or higher than the authentication requirements of the Account Holder for authorizing payment operations.

azp

The Authorization Server must not accept an "azp" different from the client\_id originating the authorization request for the CIBA flow.

Parameters for Signature Validation

**Parameter**

**Description**

**Condition**

**Recommended Values**

alg

The "alg" parameter (algorithm) identifies the cryptographic algorithm used to secure the JWS/JWE. The JWS signature value will be invalid if the "alg" value does not represent a supported algorithm or if no compatible key exists for the algorithm associated with the entity that digitally signed the content.

Mandatory

PS256 ou PS512

kid

The "kid" parameter (Key ID) indicates which key was used to secure the JWS/JWE. This parameter allows senders to explicitly signal a key change to recipients. The "kid" value MUST be a case-sensitive string. When used with a JWK, the "kid" value matches a "kid" parameter value in the JWK.

Mandatory

x5t | x5t#S256

The "x5t" or "x5t#S256" parameter (X.509 Certificate SHA-1/SHA-256 Thumbprint) is a base64url-encoded (hash) SHA-1/SHA-256 thumbprint of the DER encoding of the X.509 certificate (RFC5280) corresponding to the key used to digitally sign the JWS.

Mandatory

typ

The "typ" parameter (Type) is used by JWS applications to declare the media type (IANA.MediaTypes) of this complete JWS. It is intended for use by the application when more than one object type may be present in an application data structure containing a JWS; the application can use this value to disambiguate between the different object types that may be present.

Optional

JWT

**Client-Specific Requirements:**

●      Support parameterized OAuth 2.0 resource scope consent as per clause 6.3.1 of the OIDF FAPI WG Lodging Intent Pattern.

●      Support refresh tokens.

### **6\. Security Considerations**

Participants must adhere to all security considerations specified in FAPI-BR and FAPI-CIBA.

### **7\. Data Sharing Considerations**

Participants must comply with all data-sharing considerations outlined in FAPI-BR.
