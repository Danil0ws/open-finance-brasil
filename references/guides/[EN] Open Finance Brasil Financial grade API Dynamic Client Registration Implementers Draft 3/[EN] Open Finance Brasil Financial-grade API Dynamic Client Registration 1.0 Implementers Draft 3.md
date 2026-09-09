# [EN] Open Finance Brasil Financial-grade API Dynamic Client Registration 1.0 Implementers Draft 3

## Foreword

Este documento também está disponível em português

The Open Finance Brasil Initial Structure is responsible for creating standards and specifications necessary to meet the requirements and obligations of the Brasil Open Finance Legislation as originally outlined by the [Brasil Central Bank](https://www.bcb.gov.br/content/config/Documents/BCB_Open_Banking_Communique-April-2019.pdf). There is a possibility that some of the elements of this document may be the subject to patent rights. OFBIS shall not be held responsible for identifying any or all such patent rights.

Open Finance Brasil Financial-grade API Security Profile 1.0 consists of the following parts:

-   [Open Finance Brasil Financial-grade API Security Profile 1.0](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76283925/EN+Open+Finance+Brasil+Financial-grade+API+Security+Profile+1.0+Implementers+Draft+3)
    
-   Open Finance Brasil Dynamic Client Registration Profile 1.0
    

These parts are intended to be used with [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [OIDC](https://openid.net/specs/openid-connect-core-1_0.html), [OIDR](https://openid.net/specs/openid-connect-registration-1_0.html), [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592), [FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) and [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html)

## Introduction

The Open Finance Brasil Financial-grade API Dynamic Client Registration Profile is a profile of [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592) and [OIDR](https://openid.net/specs/openid-connect-registration-1_0.html) that aims to provide specific implementation guidelines for security and interoperability which can be applied to the identification, registration and management of OAuth Clients operating in the Brasil Open Finance ecosystem.

Although it is possible to code an OpenID Provider and Relying Party from scratch using this specification, the main audience for this specification are parties who already have a certified implementation of [OpenID Connect](https://openid.net/specs/openid-connect-core-1_0.html) and seek to obtain certification for the Brasil Open Finance programme.

## Notational Conventions

The key words "shall", "shall not", "should", "should not", "may", and "can" in this document are to be interpreted as described in [ISO Directive Part 2](https://www.iso.org/sites/directives/current/part2/index.xhtml). These key words are not to be used as lexicon terms such that any occurrence of them shall be interpreted as key words and are not to be interpreted with their natural language meanings.

## 1\. Scope

This document specifies the method of

-   applications registered in the [Open Finance Directory of Participants](https://web.directory.openbankingbrasil.org.br/) to discover OpenID Providers offering services in the Open Finance Brasil ecosystem;
    
-   applications to use [OpenID Connect Registration](https://openid.net/specs/openid-connect-registration-1_0.html) to onboard their applications with Bank OpenID Providers; and
    
-   applications to use [OAuth 2.0 Dynamic Client Registration Management Protocol](https://tools.ietf.org/html/rfc7592) to manage their applications with OpenID Providers;
    

This document is applicable to all participants engaging in Open Finance in Brasil.

## 2\. Normative references

The following referenced documents are indispensable for the application of this document. For dated references, only the edition cited applied. For undated references, the latest edition of the referenced document (including any amendments) applies.

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

[RFC6749](https://tools.ietf.org/html/rfc6749) - The OAuth 2.0 Authorization Framework

[RFC6750](https://tools.ietf.org/html/rfc6750) - The OAuth 2.0 Authorization Framework: Bearer Token Usage

[RFC7636](https://tools.ietf.org/html/rfc7636) - Proof Key for Code Exchange by OAuth Public Clients

[RFC6819](https://tools.ietf.org/html/rfc6819) - OAuth 2.0 Threat Model and Security Considerations

[RFC7519](https://tools.ietf.org/html/rfc7519) - JSON Web Token (JWT)

[RFC7591](https://tools.ietf.org/html/rfc7591) - OAuth 2.0 Dynamic Client Registration Protocol

[RFC7592](https://tools.ietf.org/html/rfc7592) - OAuth 2.0 Dynamic Client Registration Management Protocol

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[OIDC](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0 incorporating errata set 1

[FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[RFC4514](https://www.rfc-editor.org/rfc/rfc4514) - Lightweight Directory Access Protocol (LDAP): String Representation of Distinguished Names

[RFC4517](https://www.rfc-editor.org/rfc/rfc4517) - Lightweight Directory Access Protocol (LDAP): Syntaxes and Matching Rules

[OIDD](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0 incorporating errata set 1

[OIDR](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0 incorporating errata set 1

[RFC8705](https://tools.ietf.org/html/rfc8705) - OAuth 2.0 Mutual TLS Client Authentication and Certificate Bound Access Tokens

[JARM](https://bitbucket.org/openid/fapi/src/master/Financial_API_JWT_Secured_Authorization_Response_Mode.md) - Financial-grade API: JWT Secured Authorization Response Mode for OAuth 2.0 (JARM)

[PAR](https://tools.ietf.org/html/draft-ietf-oauth-par) - OAuth 2.0 Pushed Authorization Requests

[JAR](https://tools.ietf.org/html/draft-ietf-oauth-jwsreq) - OAuth 2.0 JWT Secured Authorization Request

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[OFB-FAPI](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-financial-api-1_ID3.html) - Open Finance Brasil Financial-grade API Security Profile 1.0

[OFB-Cert-Standards](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-certificate-standards-1_ID1.html) - Open Finance Brasil x.509 Certificate Standards

[OFB-DCR/DCM-Swagger](https://raw.githubusercontent.com/OpenBanking-Brasil/specs-seguranca/main/dcr_review/dcr-dcm-swagger.yaml) - DCR & DCM Swagger

## 3\. Terms and definitions

For the purpose of this document, the terms defined in [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [OpenID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html) and ISO29100 apply.

## 4\. Symbols and Abbreviated terms

-   **API** - Application Programming Interface
    
-   **DCR** - Dynamic Client Registration
    
-   **FAPI** - Financial-grade API
    
-   **HTTP** - Hyper Text Transfer Protocol
    
-   **OIDF** - OpenID Foundation
    
-   **REST** - Representational State Transfer
    
-   **SS** - Software Statement
    
-   **SSA** - Software Statement Assertion
    
-   **TLS** - Transport Layer Security
    

## 5\. Introduction

Brasil Open Finance ecosystem leverages a federation trust provider or _directory of participants_ as the golden source of information on accredited participants and software that are authorized to partake in the Open Finance Brasil ecosystem.

The services by the Directory include

-   Software registration and management.
    
-   Software credential registration and management using ICP Certificates.
    
-   Software Statement Assertion (SSA) generation
    

Participants within the ecosystem must leverage these services to facilitate API driven OAuth client registration using the process outlined in clause 3.1.1 of [RFC7591](https://tools.ietf.org/html/rfc7591) with additional metadata necessary to support OpenID Connect defined in [OpenID Connect Registration](https://openid.net/specs/openid-connect-registration-1_0.html).

It's important to remember that the client registration payload has most of its attributes as non-mandatory, and that assigned values that conflict with those in the software statement assertion _will be overridden by the values of the software statement assertion issued by the Directory of Participants_. Not all metadata a client wishes to provide may be contained in a software statement, e.g alternative [Metadata Languages and Script values](https://openid.net/specs/openid-connect-registration-1_0.html#LanguagesAndScripts). There are some cases where the client metadata are subset of the existing values in the SSA, such as redirect\_URIs.

## 6\. Open Finance Brasil OpenID Connect Discovery provisions

### 6.1. Authorization server

The Authorization Server shall support [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) as required by [Financial-grade API Security Profile 1.0 - Part 1: Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html). This support shall be explicit in Participant Directory configurations, and in the declaration of its attributes in the Discovery file (well-known), respecting the authentication mechanisms certified by the institution through the Open Finance Brazil compliance tests.

In addition, the Authorization Server:

1.  shall advertise its presence in the Open Finance Brasil ecosystem by being listed on the Directory of Participants;
    
2.  shall advertise all Open Finance Brasil REST API resources protected by the OpenID Provider on the Directory of Participants;
    
3.  shall advertise support for all signing, encryption, authentication mechanisms and standards required to support [Open Finance Brasil Financial API](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-financial-api-1_ID3.html);
    
4.  shall advertise support for [OpenID Dynamic Client Registration](https://openid.net/specs/openid-connect-registration-1_0.html);
    
5.  may advertise `mtls_endpoint_aliases` as per clause [5 RFC 8705 OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://tools.ietf.org/html/rfc8705) the `token_endpoint`, `registration_endpoint` and `userinfo_endpoint`;
    
6.  if supporting [OAuth 2.0 Pushed Authorization Requests](https://tools.ietf.org/html/draft-ietf-oauth-par) shall advertise through [OIDD](https://openid.net/specs/openid-connect-discovery-1_0.html) `mtls_endpoint_aliases` the `pushed_authorization_request_endpoint`;
    
7.  if supporting [Financial API - Client Initiated Back Channel Authentication](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) shall advertise through [OIDD](https://openid.net/specs/openid-connect-discovery-1_0.html) `mtls_endpoint_aliases` the `backchannel_authentication_endpoint`;
    

### 6.2. Client

The Client shall support [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) as required by [Financial-grade API Security Profile 1.0 - Part 1: Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html)

In addition, the Client

1.  shall rely on ecosystem discovery services provided by Directory of Participants only;
    
2.  shall derive necessary Authorisation Server metadata by relying on an Authorization Servers OpenID Connect Discovery services only;
    
3.  where present, shall use endpoints advertised in `mtls_endpoint_aliases` as per clause 5 [RFC 8705 OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://tools.ietf.org/html/rfc8705);
    

## 7\. Open Finance Brasil OpenID Connect Registration Provisions

### 7.1. [Authorization server](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID3.html#name-authorization-server-2)

The Authorization Server shall support the RFC RFCs Dynamic Client Registration (DCR) [RFC7591](https://tools.ietf.org/html/rfc7591), Dynamic Client Management (DCM) [RFC7592](https://tools.ietf.org/html/rfc7592) and [OpenID Registration](https://openid.net/specs/openid-connect-registration-1_0.html)

In addition, the Authorization Server

1.  shall reject dynamic client registration requests not performed over a connection secured with mutual tls using certificates issued by Brazil ICP (production) or the Directory of Participants (sandbox);
    
2.  shall validate that the request contains software\_statement JWT signed using the `PS256` algorithim issued by the Open Finance Brasil directory of participants;
    
3.  shall validate that the `software_statement` was issued (iat) not more than 5 minutes prior to the request being received;
    
4.  shall validate that the attribute `jwks` (key set by value) was **not** included; but declared as a reference in the `jwks_uri` attribute;
    
5.  shall, when informed, validate that `jwks_uri` matches the `software_jwks_uri` provided in the `software_statement`;
    
6.  shall require and validate that `redirect_uris` matches or contains a sub set of software\_redirect\_uris provided in the `software_statement`;
    
7.  shall require and validate that all client authentication mechanism adhere to the requirements defined in [RFC7591](https://tools.ietf.org/html/rfc7591) and [RFC7592](https://tools.ietf.org/html/rfc7592), validating the `registration_access_token` and, through a secure connection, the certificate chain of ICP-Brasil;
    
8.  _removed_;
    
9.  shall validate that the requested scopes are adequate for accredited institutions and their regulatory roles and contained in the `software_statement`. The list of regulatory permissions and the corresponding scopes are described in the following sections;
    
10.  where possible, shall compare client metadata asserted by a client to the metadata provided in the `software_statement`, choosing values in the SSA with precedence;
     
11.  shall accept all x.500 AttributeType name strings defined in the Distinguished Name of the x.509 Certificate Profiles defined in [Open Finance Brasil x.509 Certificate Standards](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76710230/EN+Padr+o+de+Certificados+Open+Finance+Brasil+1.0);
     
12.  if supporting `tls_client_auth` client authentication mechanism as defined in [RFC8705](https://tools.ietf.org/html/rfc8705) shall only accept `tls_client_auth_subject_dn` as an indication of the certificate subject value as defined in clause 2.1.2 [RFC8705](https://tools.ietf.org/html/rfc8705);
     
13.  The value of the field _UID_ of the certificate should match the one sent in the SSA, where the _UID_ field should contain the value of the _software\_id_ field of the SSA.
     
14.  The _organizationIdentifier_ field will be found in the subject\_DN in ASN.1 format and must be decoded respecting the corresponding encoding string. The value of the _organizationIdentifier_ field of the certificate which must contain the prefix corresponding to the Registration Reference _OFBBR-_ followed by the value of the _org\_id_ field of the SSA. You must convert the values ​​of the OID 2.5.4.97 field from ASN.1 format to human-readable text. For certificates issued before August 31, 2022: The value of the _OR_ field of the certificate must contain the value of the _org\_id_ field of the SSA.
     
15.  shall, during the TLS handshake process, use the `distinguishedNameMatch` rule to compare the DN values as defined in [RFC4517](https://www.rfc-editor.org/rfc/rfc4517).
     
16.  shall ensure the integrity of the stock of active consents, even after any systemic changes, so that such changes are transparent to the data receiver institutions (TPP).
     
17.  shall perform a recertification on OIDF FAPI and DCR after any systemic changes.
     
18.  The value of the software\_api\_webhook\_uris attribute contained as an attribute in the JWS in software\_statement must be compared with the webhook\_uris field. If the values are not exactly the same, the error must be returned, with the HTTP status code set to 400, `error` filled in as `invalid_webhook_uris` and `error_description` filled in with `The content of the webhook_uris field different from what was Registered in the software_statement noted via the JWS software_api_webhook_uris` field.
     
19.  If the webhook\_uris field is not declared in the payload, the webhook functionality shall be considered disabled for the specific client.
     

These provisions apply equally to the processing of [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592) and [OpenID Registration](https://openid.net/specs/openid-connect-registration-1_0.html) requests

#### 7.1.1. Applying Server Defaults

Whenever properties of a DCR request are not included nor mandatory in the specification, the Authorisation Server shall apply client defaults in the following manner:

1.  shall select and apply the encryption algorithm and cipher choice from the most recommended of the IANA cipher suites that is supported by the Authorisation Server;
    
2.  shall populate defaults from values within the `software_statement` assertion where possible;
    
3.  shall grant the client permission to the complete set of potential scopes based on the softwares regulatory permissions included in the `software_statement`;
    

#### 7.1.2. Certificate Distinguished Name Parsing

Clause 3 of [Lightweight Directory Access Protocol (LDAP): String Representation of Distinguished Names](https://www.rfc-editor.org/rfc/rfc4514) defines the mandatory OIDs whose AttributeType strings (descriptors) must be recognized by implementers. This mandatory list does not include several of the OIDs defined in [Open Finance Brasil x.509 Certificate](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76710230/EN+Padr+o+de+Certificados+Open+Finance+Brasil+1.0) [Standards](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-certificate-standards-1_ID1.html) nor is there a defined mechanism for Authorisation Servers to publish information regarding the format that they would expect a Dynamic Client Registration request that includes a `tls_client_auth_subject_dn` to be presented in.

To address this ambiguity, the Authorization Server shall accept only the AttributeTypes (descriptors) defined in the last paragraph of clause 3 [RFC4514](https://www.rfc-editor.org/rfc/rfc4514) in string format, it shall also accept in OID format, with their values in ASN.1, all the AttributeTypes defined in Distinguished Name [Open Finance Brasil x.509 Certificate Standards](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76710230/EN+Padr+o+de+Certificados+Open+Finance+Brasil+1.0) or added by the Certificate Authority.

In case of non-compliance with these requirements, the Authorization Server shall reject the registration.

In terms of format, follow below how decoding should be done:

-   Obtain in reverse order the certificate attributes.
    
-   Append each RDN (RelativeDistinguishedName) segment with a comma ','.
    
-   Use the RFC strings (CN, L, ST, O, OR, C, Street, DC, UID) with the value of their attributes in human-readable format.
    
-   Use the OIDs of the attributes defined in this specification for use in the OFB (businessCategory = OID 2.5.4.15, jurisdictionCountryName = OID 1.3.6.1.4.1.311.60.2.1.3, serialNumber = OID 2.5.4.5, organizationIdentifier = OID 2.5.4.97) with values in ASN.1 format, following the RFC4514, being that:
    
    -   Attribute names shall be defined according to dot-decimal notation, without adding the prefix "OID", ie. "2.5.4.15", followed by ('=#') plus the hexadecimal value of the attribute, here follows a complete example: 2.5.4.15=#0C1450726976617465204F7267616E697A6174696F6E
        
    -   There are no restrictions for encoding and formatting attribute values. The hexadecimal value presented on the utilized attribute must be respected (PrintableString, UTF8String, etc). This item complies with opcionality of the format stabilished by the AC face ICP normatives and items 2.3, 2.4 e 5.2 of the RFC4514. -To comply with DCR standard, convert ASN.1 values from OID 2.5.4.97 organizationIdentifier to human readable text, use features of your API gateway or a standard library of type ASN.1 or if necessary still develop manually. To do so, retrieve the full value of the OID 2.5.4.97 contained in the subject\_DN. Remove dot-decimal notation (2.5.4.97). Remove the ('=#') signs. Convert the hex value to text. Apply a filter using regular expression to retrieve the org\_id after ('OFBBR-'), for example: 2.5.4.97=#132A4F464242522D36376335373838322D303433622D313165632D396130332D303234326163313330303033. Remove dot-decimal notation and signs ('=#'): 2.5.4.97=#. Convert the hexadecimal value 132A4F464242522D36376335373838322D303433622D313165632D396130332D303234326163313330303033 to text: \*\*OFBBR-67c57882-043b-031ec Apply the regular expression and retrieve the org\_id that is contained after 'OFBBR-':67c57882-043b-11ec-9a03-0242ac130003.
        

Below are examples of required attributes for CAs active until August 31, 2022:

ubject\_dn

Issuer

UID=67c57882-043b-11ec-9a03-0242ac130003,1.3.6.1.4.1.311.60.2.1.3=#13024252,2.5.4.15=#131450726976617465204f7267616e697a6174696f6e,2.5.4.5=#130e3133333533323336303030313839,[CN=mycn.bank.gov.br](http://cn%3Dmycn.bank.gov.br/),OU=497e1ffe-b2a2-4a4e-8ef0-70633fd11b59,O=My Public Bank,L=BRASILIA,ST=DF,C=BR

issuer=CN=Open Banking SANDBOX Issuing CA - G1,OU=Open Banking,O=Open Banking Brasil,C=BR

UID=67c57882-043b-11ec-9a03-0242ac130003,1.3.6.1.4.1.311.60.2.1.3=#13024252,2.5.4.15=#0C0F427573696E65737320456E74697479,[CN=mycn.bank.gov.br](http://cn%3Dmycn.bank.gov.br/),2.5.4.5=#130e3133333533323336303030313839,OU=497e1ffe-b2a2-4a4e-8ef0-70633fd11b59,O=My Public Bank,L=BRASILIA,ST=DF,C=BR

issuer=CN=Autoridade Certificadora do SERPRO SSLv1,OU=Autoridade Certificadora Raiz Brasileira v10,O=ICP-Brasil,C=BR

1.3.6.1.4.1.311.60.2.1.3=#13024252,2.5.4.15=#131450726976617465204f7267616e697a6174696f6e,UID=67c57882-043b-11ec-9a03-0242ac130003,[CN=openbanking.mybank.com.br](http://cn%3Dopenbanking.mybank.com.br/),2.5.4.5=#130e3133333533323336303030313839,OU=497e1ffe-b2a2-4a4e-8ef0-70633fd11b59,L=Goiania,ST=GO,O=MyBank SA,C=BR

issuer=CN=AC SOLUTI SSL EV,OU=Autoridade Certificadora Raiz Brasileira v10,O=ICP-Brasil,C=BR

[CN=mycn.bank.com.br](http://cn%3Dmycn.bank.com.br/),UID=67c57882-043b-11ec-9a03-0242ac130003,OU=497e1ffe-b2a2-4a4e-8ef0-70633fd11b59,L=Sao Paulo,ST=SP,O=MyBank SA,C=BR,2.5.4.5=#130e3133333533323336303030313839,1.3.6.1.4.1.311.60.2.1.3=#13024252,2.5.4.15=#0C0F427573696E65737320456E74697479

issuer=CN=AC SERASA SSL EV,OU=Autoridade Certificadora Raiz Brasileira v10,O=ICP-Brasil,C=BR

Below are examples of required attributes for CAs active after August 31, 2022:

subject\_dn

Issuer

UID=67c57882-043b-11ec-9a03-0242ac130003,2.5.4.97=#0C2A4F464242522D36376335373838322D303433622D313165632D396130332D303234326163313330303033,1.3.6.1.4.1.311.60.2.1.3=#13024252,2.5.4.15=#131450726976617465204f7267616e697a6174696f6e,2.5.4.5=#130e3133333533323336303030313839,[CN=mycn.bank.gov.br](http://cn%3Dmycn.bank.gov.br/),OU=497e1ffe-b2a2-4a4e-8ef0-70633fd11b59,O=My Public Bank,L=BRASILIA,ST=DF,C=BR

issuer=CN=AC SERASA SSL EV,OU=Autoridade Certificadora Raiz Brasileira v10,O=ICP-Brasil,C=BR

UID=67c57882-043b-11ec-9a03-0242ac130003,1.3.6.1.4.1.311.60.2.1.3=#13024252,2.5.4.15=#131450726976617465204f7267616e697a6174696f6e,[CN=mycn.bank.gov.br](http://cn%3Dmycn.bank.gov.br/),2.5.4.5=#130e3133333533323336303030313839,2.5.4.97=#132A4F464242522D36376335373838322D303433622D313165632D396130332D303234326163313330303033,O=My Public Bank,L=BRASILIA,ST=DF,C=BR

### 7.2. Regulatory Roles for OpenID and OAuth 2.0 Mappings

To participate in the Open Finance ecosystem, accredited institutions must register themselves in the directory of participants according to their regulatory roles. Those roles reflect the institutions authorization from the Central Bank and, consequently, the APIs they are allowed to use.

The following table describes the regulatory roles for Open Finance and the related OAuth 2.0 scopes mapping. If the scopes are omitted during the DCR process, the authorization server shall grant the complete set of potential scopes based on the registering bank's regulatory roles, as described in the Server Defaults section.

Regulatory Role

Description

Allowed Scopes

Target Phase

DADOS

Instituição transmissora ou receptora de dados (AISP)

openid

accounts

credit-cards-accounts

consents

customers

invoice-financings

financings

loans

unarranged-accounts-overdraft

resources

credit-fixed-incomes

exchanges

Phase 2 and Phase 4

PAGTO

Instituição prestadora de serviço de iniciação de pagamentos (PISP)

openid

payments

Phase 3

CONTA

Instituição detentora de conta (ASPSP)

openid

Phase 3

CCORR

Correspondente de crédito

openid

Phase 3\*

It is requiread that the active roles in the application's _software\_statement_ are validated. The field \_software\_statement\_roles shall be used for validation and currently listed roles shall be active.

### 7.3. Client Registration

Section 4.2.11 of RFC 4517 (caseIgnoreMatch) must be respected. Upon registering using the _tls\_client\_auth_ authentication method, the client shall forward the _tls\_client\_auth\_subject\_dn_ field with the AttibuteTypes(Descriptors) using the defined format under item [Certificate Distinguished Name Parsing](https://openfinancebrasil.atlassian.net/wiki/pages/viewpage.action?pageId=82051199&pageVersion=10#). Non adherence to this format shall cause rejection of the registration.

## 8\. Software Statement Assertion

A Software Statement Assertion (_software\_statement_) is a JSON Web Token (JWT) [RFC7519](https://tools.ietf.org/html/rfc7519) that asserts the metadata values of the client software as a whole. On the Open Finance Brasil structure, this _software\_statement_ is signed by the Participants Directory and it's signature MUST be validated by the Authorization Servers using the public keys available on the following session.

### 8.1. Attributes of the Software Statement Assertion (Claims)

The following example contains all attributes currently included in a _software\_statement_:

## 9\. Processing of the Dynamic Client Registration claim

![image-20230328-193430.png?version=5&modificationDate=1692204129558&cacheVersion=1&api=v2](images/image-20230328-193430.png-version=5&modificationDate=1692204129558&cacheVersion=1&api=v2.png)

The steps of the subject\_DN extraction process are described in section [Certificate Distinguished Name Parsing](https://openfinancebrasil.atlassian.net/wiki/pages/viewpage.action?pageId=82051199&pageVersion=10#)

![image-20230328-193534.png?version=4&modificationDate=1689882893589&cacheVersion=1&api=v2](images/image-20230328-193534.png-version=4&modificationDate=1689882893589&cacheVersion=1&api=v2.png)

The following is an example of Javascript code for extracting the subject\_DN and the respective certificate teste.pem used in this example.

### 9.1. Sending a Registration Claim with a Software Statement

This example includes several optional fields, some of those may not be applicable to some implememntations. For a complete guide to attributes and its mandate, consult the DCR Swagger [OFB-DCR/DCM-Swagger](https://raw.githubusercontent.com/OpenBanking-Brasil/specs-seguranca/main/dcr_review/dcr-dcm-swagger.yaml). Line breaks inside values serve presentation purposes only.

### 9.2. Open Finance Brasil SSA Key Store and Issuer Details

The following links point to public keys of the Participant Directory and must be used to verify the signature validity of the _software\_statements_ presented during the client registration process.

**Production**

[https://keystore.directory.openbankingbrasil.org.br/openbanking.jwks](https://keystore.directory.openbankingbrasil.org.br/openbanking.jwks)

Open Finance Open Finance Brasil production SSA issuer

**Sandbox**

[https://keystore.sandbox.directory.openbankingbrasil.org.br/openbanking.jwks](https://keystore.sandbox.directory.openbankingbrasil.org.br/openbanking.jwks)

Open Finance Open Finance Brasil sandbox SSA issuer

### 9.3. About authentication and authorization mechanisms for DCR and DCM services

As they are auxiliary services to the main flow of Open Finance Brasil, the dynamic registration and maintenance services for clients do not use the same access control mechanisms. For example, it is not possible to require an OAuth 2.0 _access\_token_ from a client application that isn't registered yet with the transmitting institution.

To extend [RFC7591](https://tools.ietf.org/html/rfc7591) and [RFC7592](https://tools.ietf.org/html/rfc7592), which recommend minimum mechanisms for authentication of their services, institutions that support the registration flows and dynamic maintenance of clients must implement the following controls:

#### 9.3.1. Client registration - POST /register

1.  validate that the certificate presented by the client application is subordinate to the ICP-Brasil chains defined in the Open Finance Brasil Certificates Standard;
    
2.  As long as there is a need for the coexistence period (mentioned in section 7.1), validation must be implemented for both cases: certificates that have the value _org\_id_ in the _organizationUnitName_ field (_OU_) and certificates that have the value _org\_id_ in the _organizationIdentifier_ field.
    
3.  ensure that the signature of the `software_statement`\_ presented by the client application during registration has been made by the Directory of Participants using the public keys described in the previous section;
    
4.  ensure that the `software_statement` presented by the client application during registration corresponds to the same institution as the client certificate presented, validating it through the attributes that bring `organization_id` in the X.509 certificate.
    
5.  Multiple DCR registrations for the same Software Statement should not be allowed, in a way that in case of a new registration attempt for an already registered Software Statement, the Error Response procedure defined on item 3.2.2 of the RFC7591 must be enforced.
    
6.  issue, on the registry response, a `registration_access_token` to be used as an authentication token on maintaining operations of the registered client application, following specifications described in [RFC7592](https://tools.ietf.org/html/rfc7592).
    

#### 9.3.2. Client Maintenance - GET /register - PUT /register - DELETE /register

1.  Removed
    
2.  Validate the presence and matching of the Bearer header `Authorization` containing the value of the `registration_access_token` attribute returned during registration of the corresponding client.
    
3.  When the invoked method is PUT / register, carry out the validations of sub-items 1, 3, 4, and 6 of item [Client registration - POST /register](data/references/guides/EN.md).
    
4.  When the invoked method is GET /register, carry out the validations of sub-items 1 and 6 of item [Client registration - POST /register](data/references/guides/EN.md).
    
5.  When the invoked method is DELETE /register, carry out the validation of sub-item 1 of item [Client registration - POST /register](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82051199/EN+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3).
    

Note: [RFC7592](https://tools.ietf.org/html/rfc7592) provides the possibility of rotating the `registration_access_token` issued by the Authorization Server with each use, making it a single-use token. When registering their client applications, institutions should consider this aspect to receive and update the `registration_access_token` for the new value received in client maintenance (DCM) operations.

### 9.4. Signature certificates validation

-   The directory uses **cert rescan** function hourly to validation process. 
    
-   The organization shall ensure that the validation process was completed.
    
-   Each organization must have a continuity plan in case of unavailability validation service.
    
-   If the signature certificate is not valid because it has a revoked status according to the CA’s OCSP/CRL issuer, or is inactive in the directory register, the set of public keys is moved to the inactive key storage.
    
-   The validation process should include:
    
    -   Resource server (Data Transmitter) message signature validation, to be done by the Client (Data Receiver)
        
        -   Validate that the message was signed in line with what’s defined on the Message Signature Guidelines, including that the iss is equal to the organisation\_id of the server that issued the message.
            
        -   Fetch the “iss” claim from the JWT and build the directory application JWKS uri for that specific server.
            
        -   Make sure that the kid present on the message JWT header is present on the directory JWKS.
            
        -   Validate that the private key for the corresponding kid is able to validate the message signature.
            
    -   Client (Data Receiver) message signature validation, to be done by the Resource Server
        
        -   Validate how the message was signed in line with what’s defined on the Message Signature Guidelines.
            
        -   Obtain the org\_jwks\_uri which was presented on the SSA by the client on the moment of the registration (DCR)
            
        -   Make sure that the kid present on the message JWT header is present on the directory JWKS.
            
        -   Validate that the private key for the corresponding kid is able to validate the message signature.
            

## 10\. Acknowledgement

With thanks to all who have set the foundations for secure and safe data sharing through the formation of the OpenID Foundation FAPI Working Group, the Open Finance Brasil GT Security and to the pioneers who will stand on their shoulders.

The following people contributed to this document:

-   Alexandre Daniel Dalabrida (Cooperativa Central Ailos)
    
-   Alexandre Siqueira (Mercado Pago)
    
-   André Borges (Banco Fibra)
    
-   Bernardo Vale (Banco Inter)
    
-   Caio Zanolla (Belvo)
    
-   Danilo Sasaki (Banco Itaú)
    
-   João Rodolfo Vieira da Silva (Banco Itaú)
    
-   Michelle Bandarra (Chicago)
    
-   Nic Marcondes (Quanto)
    
-   Rafael Gonzalez Hashimoto (Banco C6)
    
-   Ralph Bragg (Raidiam)
    

## Appendix A. Notices

Copyright (c) 2023 Open Finance Brasil Initial Structure.

The Open Finance Brasil Initial Structure (OFBIS) grants to any Contributor, developer, implementer, or other interested party a non-exclusive, royalty-free, worldwide copyright license to reproduce, prepare derivative works from, distribute, perform and display, this Implementers Draft or Final Specification solely for the purposes of (i) developing specifications, and (ii) implementing Implementers Drafts and Final Specifications based on such documents, provided that attribution be made to the OFBIS as the source of the material, but that such attribution does not indicate an endorsement by the OFBIS.

The technology described in this specification was made available from contributions from various sources, including members of the OpenID Foundation, the Open Finance Brasil GT Security Working Group and others. Although the Open Finance Brasil Initial Structure has taken steps to help ensure that the technology is available for distribution, it takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this specification or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any independent effort to identify any such rights. The Open Finance Brasil Initial Structure and the contributors to this specification make no (and hereby expressly disclaim any) warranties (express, implied, or otherwise), including implied warranties of merchantability, non-infringement, fitness for a particular purpose, or title, related to this specification, and the entire risk as to implementing this specification is assumed by the implementer. The Open Finance Brasil Intellectual Property Rights policy requires contributors to offer a patent promise not to assert certain patent claims against other contributors and against implementers. The Open Finance Brasil Initial Structure invites any interested party to bring to its attention any copyrights, patents, patent applications, or other proprietary rights that may cover technology that may be required to practice this specification.

### A.1. Appendix A. Example Software Statement Assertion

## Author's Address

**OFBIS GT Security**

Open Finance Brasil Initial Structure

Email: [gt-seguranca@openfinancebrasil.org.br](mailto:gt-seguranca@openfinancebrasil.org.br)

URI: [https://openfinancebrasil.org.br](https://openfinancebrasil.org.br/)
