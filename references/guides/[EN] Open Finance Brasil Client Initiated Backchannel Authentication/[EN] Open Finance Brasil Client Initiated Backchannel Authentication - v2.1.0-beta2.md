# [EN] Open Finance Brasil Client Initiated Backchannel Authentication - v2.1.0-beta2

13falsenonelisttrue

## **1\. Introduction**

Open Finance Brasil adopts the Financial-grade API (FAPI) standard to ensure adequate security for financial services offered in the ecosystem. This document specifies the implementation profile of Client Initiated Backchannel Authentication (CIBA) - or Client Initiated Backchannel Authentication Flow - as an integral part of the Open Finance Brasil security architecture.

While it is possible to build an OpenID Provider and a Relying Party from scratch using this specification, the main audience of this document are parties that already have a certified implementation in the [Financial-grade API: Client Initiated Backchannel Authentication Profile (FAPI-CIBA)](https://openid.net/specs/openid-financial-api-ciba-ID1.html) and wish to obtain certification for the Open Finance Brasil program.

## **2\. Notational Conventions**

The keywords "shall", "shall not", "should", "should not", "may" and "optional" in this document shall be interpreted as described in [ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml). These keywords are not used as dictionary terms, so that any occurrence of them shall be interpreted as keywords and shall not be interpreted with their natural language meanings.

## **3\. Scope**

This document specifies the method of:

1.  Applications obtaining OAuth tokens through a backchannel authentication flow in an appropriately secure manner for higher risk access to data in a way that meets Open Finance Brasil requirements;
    
2.  Applications using OpenID Connect CIBA to suggest the client's identity.
    

This document is applicable to all Open Finance Brasil participants that implement CIBA flows within the ecosystem.

## **4\. Normative References**

The following referenced documents are indispensable for the application of this document. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments) applies.

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) - OpenID Connect Client Initiated Backchannel Authentication Core

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md) - OIDF FAPI WG Lodging Intent Working Paper

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

OFB-FAPI-BR – Open Finance Brasil Financial-grade API Security Profile

OFB-FAPI-BR-DCR - Open Finance Brasil Financial-grade API Dynamic Client Registration Profile

[OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0

[OIDC-Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0

[OIDC-Registration](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0

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

## **5\. Symbols and Abbreviations**

-   **API** \- Application Programming Interface
    
-   **DCR** \- Dynamic Client Registration
    
-   **FAPI** \- Financial-grade API
    
-   **HTTP** \- Hyper Text Transfer Protocol
    
-   **JSR -** No-Redirect Journey
    
-   **MFA** \- Multi-Factor Authentication
    
-   **OIDF** \- OpenID Foundation
    
-   **REST** \- Representational State Transfer
    
-   **TLS** \- Transport Layer Security
    

## **6\. CIBA Security Profile for Open Finance Brasil**

### **6.1 Overview**

The Open Finance Brasil security profile specifies additional security and identity requirements for high-risk API resources protected by the OAuth 2.0 Authorization Framework ([RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636)), by the Financial-grade API profiles ([FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html), [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html)), by [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html), and by other related specifications.

This profile describes the security provisions and functional requirements for authorization servers and clients that implement CIBA in the context of Open Finance Brasil, defining in particular:

-   the requirement to transmit to the Client, in a standardized manner, the authentication context that was executed by an OpenID Provider, enabling appropriate management of user conduct risk by the client;
    
-   the requirement that clients indicate, by means of a consent identifier or a device-binding identifier, the resource that will be used to identify the user in-journey as part of the CIBA flow.
    

The requirements of this profile are additional and restrictive in relation to the [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) and [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) specifications, and shall be observed jointly with OFB-FAPI-BR.

### **6.2 Authorization Server**

#### 6.2.1 **Basic conformance**

The CIBA Authorization Server in Open Finance Brasil shall:

-   Meet the provisions specified in clause 5.2.2 of [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html);
    
-   Be compliant with the applicable security requirements of OFB-FAPI-BR for authorization servers.
    

#### 6.2.2. **CIBA delivery modes**

In the context of Open Finance Brasil, the CIBA Authorization Server shall:

-   Support CIBA ping mode;
    
-   Require that clients register, via DCR/DCM, only for use of CIBA ping mode, in accordance with [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592) and OFB-FAPI-BR-DCR.
    
-   Not accept nor advertise, in its dynamic registration process or in its configuration, any CIBA token delivery modes or notification modes other than ping mode.
    

Note: As established in [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html), clients registered for ping mode are implicitly enabled to use poll mode as a complementary mechanism. In the context of Open Finance Brasil, the use of poll mode is reserved exclusively as a fallback mechanism for situations in which:

-   There is suspicion or evidence of failure in delivering the ping notification to the Client endpoint;
    
-   The Client has not received the notification within the expected timeframe, considering network characteristics and the availability requirements established in OFB-FAPI-BR;
    
-   It is necessary to ensure continuity of the user experience in scenarios of temporary technical degradation.
    

The Client shall implement appropriate timeout and notification failure detection mechanisms before resorting to poll mode as a fallback.

#### **6.2.3. login\_hint parameter and user identification**

The CIBA Authorization Server shall:

-   Support receiving the login\_hint parameter containing the consent identifier or the device-binding identifier, to identify the user who must perform authentication;
    
-   Use the login\_hint value to locate, in its internal records, the data necessary for user identification and authentication associated with the provided consent or binding;
    
-   Not require that login\_hint contain directly identifiable personal data of the user (such as CPF, email, or phone number). The identifier shall be opaque from the Client’s point of view and represent only the consent or the device binding (JSR) established between the parties.
    
-   In addition to the error codes for HTTP status 400 set out in [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html), section 13, the CIBA Authorization Server in Open Finance Brasil shall adopt the following additional code:
    
    -   invalid\_login\_hint: shall be returned when the value sent in login\_hint is invalid, cannot be interpreted by the Authorization Server, or cannot be associated with a valid and active consent or device binding in the context of that Client.
        

The format and characteristics of the consent identifier or the device-binding identifier shall be defined by the business and security rules of each account-holding institution, respecting the policies of Open Finance Brasil.

#### 6.2.4. Client registration and user\_code parameter

The CIBA Authorization Server:

-   Shall not accept nor advertise support for the use of the `user_code` parameter in CIBA flows within the context of Open Finance Brasil;
    
-   Shall not accept dynamic client registration or dynamic client management requests (DCR/DCM) that include the `backchannel_user_code_parameter` parameter with value `true`. In such cases, the CIBA Authorization Server shall reject the DCR/DCM request with HTTP status code 400 and error `invalid_client_metadata`, as specified in RFC7591, RFC7592 and OFB-FAPI-BR-DCR;
    
-   Shall not accept CIBA authorization requests that use the `user_code` parameter. If the `user_code` parameter is received in a CIBA request, the CIBA Authorization Server shall reject the request with error `invalid_request`, as specified in [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html).
    

#### 6.2.5. binding\_message parameter

The CIBA Authorization Server:

-   May accept the optional `binding_message` parameter, as defined in CIBA-Core and subject to the specific rules applicable to the product, service or journey in question.
    
-   The acceptance, validation, processing and possible display of the `binding_message` to the user shall be specifically defined in the rules applicable to each Open Finance Brasil product, service or journey.
    
-   `binding_message` shall not be used to transmit directly identifiable personal data of the user (for example, CPF, e-mail, telephone number), confidential data (including passwords, authentication codes, OTP), URLs or marketing and advertising information.
    
-   When accepted, `binding_message` shall be treated by the CIBA Authorization Server as auxiliary context information, with optional display to the user, in accordance with the experience, security and business rules applicable to the corresponding product, service or journey.
    

#### 6.2.6. requested\_expiry parameter and the validity period of the authentication request (expires\_in)

The CIBA Authorization Server:

-   Shall consider the `requested_expiry` value sent by the Client, provided that it is a positive integer.
    
-   Shall determine the validity period of the CIBA authentication request, specified in the `expires_in` parameter, as follows:
    
    -   when `requested_expiry` is present and its value is less than or equal to the applicable maximum period, `expires_in` shall be assigned the value requested by the Client;
        
    -   when `requested_expiry` is absent or its value exceeds the applicable maximum period, `expires_in` shall be assigned the maximum period defined for the approval of the consent or the device binding, according to the specific rule of the product or service.
        
-   Shall not assign to `expires_in` a value greater than the maximum period established by the specific rule of the product or service.
    
-   Shall refuse attempts to use the `auth_req_id` after the end of its validity period, returning the applicable error as defined in [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) and [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md).
    

#### 6.2.7. Handling requests in cases of fraud or security

The account-holding institution, acting as the CIBA Authorization Server, may:

-   Deny new authentication requests in cases of suspected fraud or for security reasons, in accordance with its internal policies and with OFB-FAPI-BR;
    
-   In such cases, shall return to the Client an appropriate error code, in accordance with [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) and [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) (for example, access\_denied or another error permitted by the specifications), avoiding the disclosure of sensitive information about the reasons for the denial.
    

#### 6.2.8. PING notifications and idempotency

The CIBA Authorization Server:

-   Shall implement retry mechanisms for delivering the PING notification to the Client in cases where temporary communication failures or transient errors occur in the call to the Client’s notification endpoint.
    
-   May, as a result of these retries, produce multiple PING notifications referring to the same `auth_req_id`.
    

### **6.3. Confidential Client**

The confidential Client that participates in CIBA flows in Open Finance Brasil shall meet the following additional requirements to those established in OFB-FAPI-BR and [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md).

#### 6.3.1. Parameterized scope (Lodging Intent)

The confidential Client shall:

-   Support the parameterized scope as defined in item 6.3.1 of [FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
-   Be able to associate the consent identifier issued with parameterized scope to the login\_hint parameter used in subsequent CIBA requests.
    

#### 6.3.2. Use of login\_hint

The confidential Client shall:

-   Send, in CIBA requests to the Authorization Server, the login\_hint parameter containing the consent identifier or the device-binding identifier agreed with the account-holding institution;
    
-   Treat the login\_hint value as an opaque identifier, and shall not infer or reconstruct the user’s civil identity from that value;
    
-   Not include directly identifiable personal data of the user in login\_hint, unless expressly provided for in a regulation or complementary Open Finance Brasil specification.
    

#### 6.3.3. Support for refresh tokens

The confidential Client shall:

-   Support the use of refresh tokens, in compliance with OFB-FAPI-BR and [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md).
    

#### 6.3.4. Support for ping mode

The confidential Client:

-   Shall be able to operate in CIBA ping mode, in alignment with the Authorization Server requirements described in section 6.2.2;
    
-   Shall expose a notification endpoint compatible with ping mode, duly protected, in accordance with OFB-FAPI-BR, including the use of TLS as specified in [BCP195](https://tools.ietf.org/html/bcp195) and mutual authentication via certificate, as specified in [RFC8705](https://tools.ietf.org/html/rfc8705);
    
-   Shall validate the notifications received from the CIBA Authorization Server, including the authenticity of the origin, the integrity of the message and the correct association with the previously issued `auth_req_id`;
    
-   Shall, after receiving the ping notification, follow the token endpoint flow as specified in [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) and [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) to obtain the tokens associated with the `auth_req_id`.
    

#### 6.3.4.1. Use of poll mode as fallback

The confidential Client:

-   May use poll mode as a fallback mechanism only in situations of failure or suspected failure in the delivery of the PING notification, absence of receipt of the notification within the expected time, or temporary degradation of the notification mechanism.
    
-   Shall observe the `interval` parameter returned by the CIBA Authorization Server, as specified in CIBA-Core, when using poll mode.
    
-   Shall not use poll mode as the primary mode of operation when ping mode is available and functioning properly.
    
-   Shall implement mechanisms for timeout, failure detection and controlled retry before resorting to poll mode as fallback.
    

#### 6.3.5. Client registration and user\_code parameter

The confidential Client:

-   Shall not include the `backchannel_user_code_parameter` parameter with value `true` in dynamic client registration or dynamic client management requests (DCR/DCM) sent to the CIBA Authorization Server in the context of Open Finance Brasil.
    
-   Shall not send the `user_code` parameter in CIBA requests in the context of Open Finance Brasil.
    

#### 6.3.6. binding\_message parameter

The confidential Client:

-   May send the optional `binding_message` parameter to assist the user in identifying the context of the operation, subject to the specific rules applicable to the product, service or journey in question.
    
-   The sending of `binding_message` does not imply its acceptance, processing or display by the CIBA Authorization Server. The acceptance, validation, processing and possible display of `binding_message` to the user shall observe the rules applicable to each Open Finance Brasil product, service or journey.
    
-   `binding_message` shall not contain directly identifiable personal data of the user (for example, CPF, e-mail, telephone number), confidential data (including passwords, authentication codes, OTP), URLs or marketing and advertising content.
    
-   `binding_message` shall observe the limits, policies, formats and restrictions that may be established for the corresponding product, service or journey.
    

#### 6.3.7. requested\_expiry parameter

The confidential Client:

-   May send the `requested_expiry` parameter to request a validity period for the CIBA authentication request. When sent, its value shall be a positive integer.
    
-   Shall consider the `expires_in` value returned by the CIBA Authorization Server as the source of truth for the validity of the CIBA request and for the planning of any fallback, including eventual use of poll mode.
    

#### 6.3.8. Dynamic client registration (DCR/DCM)

The confidential Client shall:

-   Register with the Authorization Server via DCR/DCM, in accordance with [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592) and OFB-FAPI-BR-DCR;
    
-   Declare, in the registration process, support for CIBA ping mode, in alignment with the requirements established in section 6.2.2 of this document;
    
-   Keep its registration metadata up to date, including the endpoints required for ping mode and any other information required by OFB-FAPI-BR-DCR and OFB-FAPI-BR.
    

## 7\. Security considerations

Participants shall support all security considerations specified in all clauses and subclauses of OFB-FAPI-BR and [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md), as well as the security recommendations related to OAuth 2.0 ([RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC6819](https://tools.ietf.org/html/rfc6819)), the use of JWS/JWT ([RFC7515](https://tools.ietf.org/html/rfc7515), [RFC7519](https://tools.ietf.org/html/rfc7519)), and the secure use of TLS ([BCP195](https://tools.ietf.org/html/bcp195), [RFC8705](https://tools.ietf.org/html/rfc8705)).

## 8\. Data sharing considerations

Participants shall support all data sharing considerations specified in OFB-FAPI-BR.
