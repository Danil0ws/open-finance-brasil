# [EN] Guia do Usuário para Instituições Receptores de Dados e Iniciadores de Pagamento (TTP/PISP)

## 1\. Registering an Application

At a high level the following major steps are required in order to onboard a new application into the Open Finance Brasil ecosystem.

1.  Register your organisation on the directory of participants (User Interface)
    
2.  Register your application on the directory of participants (User Interface)
    
3.  Obtain credentials for your application from the Brasil ICP (Out of scope of this document)
    
4.  Register your credentials for your application on the directory of participants (User Interface)
    
5.  Identify providers of Account information or Payment Services of interest to customers of your application by searching the directory of participants (API)
    
6.  Register your application with each provider (API)
    

### 1.1. Sequence Diagram

![att\_4\_for\_157385052.png](images/att_4_for_157385052.png)

### 1.2. Directory Overview

The trust framework services provided by Open Finance Brasil provide all of the discovery services necessary for TPPs and ASPSPs to interact with each other without being required to validate the authenticity of each others’ Identity, Authorizations, Consumer Offerings (Apps), APIs or Credentials for the Applications. In addition it provides a single registry of all consumer propositions being offered in the market and a single control plane for the regulatory authorities granting permissions to manage participants within the ecosystem.

The trust framework does not have visibility or view of interactions that occur between TPPs and Providers. It is designed to provide trust and surety of identity and authorization only. It does not sit within the communication flow between a consumer and a provider and it has no knowledge or visbility of any customer data. This trust framework model is known as transitive trust. Where two parties, a TPP and an ASPSP agree to trust a common trust providers statements and attestations regarding the legitimacy of each other and then proceed with communicating whatever they would like with no additional costly validation or checking being required.

### 1.3. Accessing the Directory

This user guide assumes that participating organisations have already been through the onboarding process with the Open Finance Brasil Initial Structure and have completed all of the necessary onboarding, contract signing and individual administrator onboarding processes.

![att\_2\_for\_157385052.png](images/att_2_for_157385052.png)

### 1.4. Creating a new Software Statement

A software statement is an ‘App’ on what can be thought of as the Open Finance Brasil App Store. This App record contains all of the information necessary for a Bank to Technically Identity and Interact with it as well as containing all of the information that assist consumers using the application with confirming its legitimacy.

A new application or software statement can be registered by logging on to the Directory, navigating to ‘Software Statements’ and clicking ‘Create New’ and populating the form. Help text is provided for each field on the screen. Please remember that the majority of this information will be displayed to customers by the Banks as part of the redirection or authorization process. As such it is important that all URIs and Descriptions are relevant for customer audience.

![att\_1\_for\_157385052.png](images/att_1_for_157385052.png)

#### 1.4.1. Assigning Software Regulatory Roles

In a complex and diverse data sharing ecosystem, the regulatory roles that an organisation can have can change. They can be added and revoked. This means that software added to the directory can be given permission to have 0 or more regulatory roles. A administrator can assign to a given software any and all permissions that the organisation that owns the software can have.

Should an organisation lose a regulatory role then all software with that regulatory role will be revoked from the ecosystem so it is very important that an application is only given the roles that it actually needs in order to function.

A real world example of this could be ‘Amazon’, Amazon has two applications, ‘Amazon Accounting’ and ‘Amazon Prime’. Amazon as an organisation is an authorized DADOS and PISP, and is allowed to handle customer data as well as make Open Finance Payments. Amazon Accounting should be assigned the domain role of DADOS and Amazon Prime should be assigned a domain role of PISP.

In the future, should Amazon lose regulatory permission to be a PISP then only the Amazon Prime application would be removed from the ecosystem. Amazon Account would continue to function without issue.

### 1.5. Creating and Uploading Certificates

#### 1.5.1. Sandbox

The Open Finance Directory contains a PKI that can be used to create certificates for the Applications being registered. Simply select certificates from the drop down menu and follow the instructions.

The directory supports multiple certificate and key types and an openssl command and configuration file is made available as an example. Once you have created the necessary Certificate Signing Request (CSR) for both a “Transport” and “Signing” certificate you can submit them to the directory to be validated and minted into certificates.

Please remember to follow your organisations key management practices for certificate generation. These credentials and keys need to be handled carefully. A significant key compromise event could lead to customer data being compromised.

#### 1.5.2. Production

Certificates must be provided by the Brasil ICP. The steps to follow are included in the [Open Finance Brasil Certificate Guide](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-ICP-certificate-guide.pdf)

#### 1.5.3. What is a JWT, JWE, JWS and JWK

When certificates are uploaded to the directory, the trust framework advertises them in [JSON Web Key Sets](https://tools.ietf.org/html/rfc7517) with each JSON Web Key or JWK having a unique ‘KID’ or Key ID. JWK’s in addition to having specific properties describing the algorithm and cipher suites that they support also advertise their ‘use’ which can either be of type ‘enc’ for encryption or ‘sig’ for signing.

These ‘sig’ keys and ‘enc’ key pairs are used in many places within the Open Finance ecosystem to encrypt or to sign data using the standards defined in [RFC 7519 JSON Web Token](https://tools.ietf.org/html/rfc7519) which should be read in detail by developers.

Types of JWT include

-   OpenID Connect Request Objects defined in [Open ID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html)
    
-   OpenID Connect id\_token defined in [Open ID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html)
    

Amongst many others.

These JWT’s may be encrypted also be encrypted using JSON Web Encryption (JWE). In the majority of cases the keys that should be used to validate a JSON Web Signature (JWS) or the key that was used to encrypt a JWE is usually published as a JSON Web Key in a JSON Web Key Set with the reference to the key being carried in the ‘kid’ (Key ID) header field.

**As a worked example: An example JWT Request Object**

The example above is decoded below. In the header is ‘kid’ of `PWAi5ruQcHfzPzq2JFdpY7nAUh6LzTTQtDBUpOM37JQ` which can be located in the JSON Web KeySet for this client [here](https://keystore.sandbox.directory.openbankingbrasil.org.br/74e929d9-33b6-4d85-8ba7-c146c867a817/1509a662-6b3a-4cb8-b7c0-ffb6e596eb0d/application.jwks)

The public JWK from the JWKS taken from the uri given earlier

The private key that was used to create the JWS

## 2\. Interacting with the Trust Services APIs

When an application is registered on the Directory, the central service uses the provided meta data and certificates to create for the software a OAuth 2.0 client that has a grant type of ‘client credentials’ as defined in [RFC6749](https://tools.ietf.org/html/rfc6749) with a client authentication mechanism of ‘`tls_client_auth`' as defined in [RFC 8705](https://tools.ietf.org/html/rfc8705)

Using the ClientID listed on the software statement in the Directory, [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) and the OpenID Provider Issuer configuration below, a participant has all of the necessary infomation to discover, authenticate and interact with the Directory APIs.

### 2.1. Trust Framework Issuer

Production: [https://auth.directory.openbankingbrasil.org.br/](https://auth.directory.openbankingbrasil.org.br/)

Sandbox: [https://auth.sandbox.directory.openbankingbrasil.org.br/](https://auth.sandbox.directory.openbankingbrasil.org.br/)

### 2.2. How to communicate with the Directory Authorization Server

Use the OpenID Issuer and Clause 4 of the OpenID Discovery Specification to retrieve the ‘openid-configuration’ document.

Retrieve the Mutual TLS token endpoint alias as defined by [RFC8705 - OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://tools.ietf.org/html/rfc8705)

Establish a Mutual TLS connection using the transport certificate registered early and request an access token with the scope ‘`directory:software`'

Use the OpenID Issuer and Clause 4 of the OpenID Discovery Specification to retrieve the ‘openid-configuration’ document.

Retrieve the Mutual TLS token endpoint alias as defined by [RFC8705 - OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://tools.ietf.org/html/rfc8705)

Establish a Mutual TLS connection using the transport certificate registered early and request an access token with the scope ‘`directory:software`'

Retrieve the Mutual TLS token endpoint alias as defined by [RFC8705 - OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://tools.ietf.org/html/rfc8705)

Establish a Mutual TLS connection using the transport certificate registered early and request an access token with the scope ‘directory:software’

### 2.3. How to communicate with the Directory APIs

The Directory APIs are RESTful resources secured using the Brasil Open Banking Security Profile, this means that they have the same security posture as Banks APIs. All of the Directories APIs require OAuth 2.0 resource scope of directory:software and are secured using Mutual TLS.

Please see the Directory OpenAPI v3 specification for full set of endpoints available.

### 2.4. Discovering Banks Authorization Servers

Interrogate the participants (public information) resource and retrieve a list of all participants and their Authorization Servers.

Filter the participants to those that have Authorization Servers protecting resources that you are interested in accessing for your product. In the example above, there are two Authorization Servers for ‘Amazing Bank’ one for the Retail Business and one for the Business Banking.

The App now has discovered the list of Banks that are offering APIs that might be useful to customers of the Application and the App can now generate a list of Banks ‘Customer Friendly Names’ and Logos to display to consumers to enable them to select the bank from which they want to share data.

## 3\. Registering the application with a provider

![att\_3\_for\_157385052.png](images/att_3_for_157385052.png)

From the example given above we can see that the location of the “OpenIDDiscoveryDocument” is advertised by each of the Authorization Servers

### 3.1. Creating a Software Statement

A software statement assertion (SSA) is a signed JWT from the Directory that contains all of the information about an application that exists at a point in time on the directory. It includes the location of all of the public keys that are linked to this software statement and all of the other metadata a bank needs to validate the legitimacy of the application.

An SSA does not have an expiry, it is simply a point in time record of what existed as valid attributes at the point of time that it was created. Banks should accept an SSA that is less than a few minutes old but the exact window may differ between providers.

Obtain an access token and then retrieve the software statement for a application on the Directory.

### 3.2. Sending an RFC7591 Dynamic Client Registration Request

Please see [Open Finance Brasil Dynamic Client Registration](data/references/guides/EN.md)

### 3.3. Saving the RFC7592 Dynamic Client Management Token

Please see [Open Finance Brasil Dynamic Client Registration](data/references/guides/EN.md)

### 3.4. Modifying a client using RFC7592 Dynamic Client Management Token

Please see [Open Finance Brasil Dynamic Client Registration](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82051199/EN+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3)

## 4\. Obtaining Access to Customers Resources

![att\_5\_for\_157385052.png](images/att_5_for_157385052.png)

For all options including all permission codes please see the [Consent API](https://openbanking-brasil.github.io/areadesenvolvedor/swagger/swagger_consents_apis.yaml). The following examples are minimal but functional examples to demonstrate end to end flow. These examples are assuming that the client is communicating with an OpenID Provider leveraging the ‘tls\_client\_auth’ token endpoint authentication mechanism. Alternative examples are available in the appendix.

### 4.1. Pre-requisites

These non normative examples assumes that the OAuth Client has discovered the locations of all of the necessary endpoints to communicate with the banks resources from the Directory including the consents resource, the data resources and the OpenID authorization discovery document from the Directory.

### 4.2. Creating Consent

1.  Obtain an Access Token with the scope 'consents'
    

1.  Create a consent resource
    

### 4.3. Authorizing Consent - Redirect

#### 4.3.1. Create OpenID Connect Request Object

Different methods of authentication (private\_key\_jwt and tls\_client\_auth) and of sending Request Object (with and without PAR) can be supported by Authorization Servers according to the [FAPI-1.0 Part 2 - Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) specification. Therefore, how does it reinforce the security profile for Open Finance Brasil (item 8 of section 5.2.3 of the [security requirements for the confidential client](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-financial-api-1_ID3.html#section-5.2.3)), all combinations (table below) must be supported by API clients.

The table below reflects the different security profiles and combinations that shall be supported by all API clients (as per the [OIDF certified profiles for Open Finance Brazil](https://openid.net/certification/#FAPI_OPs)) .

**OIDF Certification Profile**

BR-OB Adv. OP w/ Private Key, PAR

All requirements for the OpenID Request Object are included in Brasil Open Finance Security Profile

Signature ommited for brevity

#### 4.3.2. Redirect User to Authorization Server for Authorization

As per OpenID Connect Core.

#### 4.3.3. Obtaining Access Token via Authorization Code Exchange

As per [RFC 7636 Proof Key for Code Exchange](https://tools.ietf.org/html/rfc7636)

#### 4.3.4. Checking Consent Resource Status

At this point, a TPP can optionally check the status of the consent request to see if it has changed to a status of fully authorized. For resources that do not require multi party consent this step should not be necessary however for business accounts or joint accounts with special access requirements then it may take a while for the bank to obtain the additional authorizations necessary for this consent to become completely authorized. TPPs should not abuse checking the consent status API

#### 4.3.5. Access Resources

With the access token that was returned in 4.3.3, the TPP now has the ability to call customers resources.

## Appendix

### A.1 private\_key\_jwt client credentials grant

### A.2 Example decoded request object body

### A.3 Example decoded request object body with specific claim values being requested

In this example a client is requesting that the Authorization Server only authenticates the customer if the cpf claim matches the provided value. The processing requirements for requests with a specific ‘cpf’ value are defined in the Open Finance Brasil Security Profile.

### A.4 Example CIBA decoded Authentication Request body

In this example a CIBA request is being made to request consent authorization using a previously issued id\_token as the indication of the resource owner that the bank should contact to obtain authorization.
