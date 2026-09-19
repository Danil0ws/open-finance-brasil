# Discovery of the Mock Bank

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank)
**Slug:** `Discovery-of-the-Mock-Bank`

---

# Pre-Requisites: Creating a Software Statement on Sandbox

[Portuguese version can be found here](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank-%28PT%29)

## The Participant Directory Sandbox

In order to connect with the Mock Bank, a TPP will first need to have a valid Software Statement issued from the Sandbox of the participant directory of the Open Finance.

To access the [Sandbox of the participant directory](https://web.sandbox.directory.openbankingbrasil.org.br/organisations) the user needs to belong to an organization that is an authorized participant of the Open Finance and also be added as a member of one of the organizations present on the directory. This access can be granted by already existing administrators of this organization.

To create a software statement on the directory, the user should refer to the [Participant Directory guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central), which is currently maintained by the central structure of the Open Finance.

The creation of a software statement can also be seen on the video [Mock Bank - Create S.S.](https://www.youtube.com/watch?v=03R2jtrZPuU&ab_channel=OpenBankingBrasil)

## Assign the regulatory roles to the S.S.

To communicate with other servers, which include the Mock Bank, accredited institutions must guarantee that their Software Statements can obtain the needed scopes linked to the regulatory roles. Those roles reflect the institutions' authorization from the Central Bank and, consequently, the APIs they are allowed to use.

On the Sandbox Environment assigning a role to your organization and to your software statement is done in an entirely self-service way. To see how to assign those roles to refer to [Participant Directory guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central)

The mapping between scopes and regulatory roles is specified on the [DCR Security Documentation](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2.md#regulatory-roles-to-openid-and-oauth-20-mappings). This means that the user must make sure that its client holds all the needed regulatory roles prior to interacting with the Mock Bank

## Issuing certificates using the Directory Sandbox PKI

The Open Finance Directory contains a PKI that can be used to create certificates for the Applications being registered. The Sandbox also uses [ICP-Brasil style certificates](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-certificate-standards-1_ID1.md), similar to the ones that are issued by the different certificate authorities to be used on production.

There are two types of certificates that should be issued to be used with the created client, BRCAC and BRSEAL. The first is used for transport or encryption, while the latter is the signing certificate. Please note that while the BRCAC is created on the Software Statement level, under the Software Statement certificates menu, the BRSEAL is created at the organization level, under the Organisation certificates menu. To issue the certificates, one will need a library in order to generate the Certificate Signing Requests that need to be uploaded to the directory.

The generation of the certificates can be seen on item **"12.Criando certificados de transporte e assinatura em Sandbox"** of the [Participant Directory guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central)

Once finished, the participant should have two sets of public and private keys both in PEM formats. For questions regarding the certificate files, please refer to [TPP User Guide - Creating Certificates Session](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/tpp-user-guide.md#14-creating-and-uploading-certificates)

The process to issue the certificates can also be seen on the video [Mock Bank - Issue Certficates](https://www.youtube.com/watch?v=0GSMsVtjw2c&t=1s&ab_channel=OpenBankingBrasil)

# Discovering the Mock Bank APIs

## The Directory APIs

The information from the Participant Directory can be accessed on an API level using two different approaches:

- Accessing the "Data" API, which provides a dump of all the Authorisation Servers registered on the directory - 15 minutes cached. For more information on the details that can be accessed via this API, please consult the [data api swagger](https://openbanking-brasil.github.io/areadesenvolvedor/swagger/swagger_participants.yaml)
- Accessing the mTLS protected "matls-api", which provides granular real-time data of everything that has been registered inside the directory. For more details on the resources that can be accessed, please consult the [matls-api swagger](https://raw.githubusercontent.com/OpenBanking-Brasil/specs-directory/main/openapi.yaml)

> Please note that although both swaggers are for the Participant Directory, they can be used for the sandbox environment with the sole difference that one must add sandbox before the ".directory" on the URI. For example:
>
> - Sandbox: https://data.sandbox.directory.openbankingbrasil.org.br/participants
> - Production: https://data.directory.openbankingbrasil.org.br/participants

Both methods can be used to retrieve the Mock Bank details, however using the data API proves to be a way simpler method, as not only it's an API that can be accessed without any kind of authentication, but all the needed information can be obtained with one single request.

## Obtaining the Mock Bank URIs

The Mock Bank is currently registered under the Open Finance Brasil organization, which has the following organization id:

```
MOCK BANK
"OrganisationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
"OrganisationName": "Open Banking Brasil - Raidiam"
```

It can be found searching for either its Brand Name (CustomerFriendlyName) or its id (AuthorisationServerId):

```
MOCK BANK
"CustomerFriendlyName": "Mock Bank Sandbox"
"AuthorisationServerId": "7844e311-aa1f-4f67-9475-cbd989310b3e"
"OpenIDDiscoveryDocument": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
```

Under the Authorisation Server, it is possible to obtain the well-known endpoint, registered as "OpenIDDiscoveryDocument" and all of the Resources that the Mock Bank currently support, including all of Phase 2 - Customer Data APIs and the Phase 3 - PIX Payments API

Down below is an example of code in Python that allows the recovery of the Mock Bank well-known endpoint and all of its API Resources:

```
import requests

response = requests.get("https://data.sandbox.directory.openbankingbrasil.org.br/participants")
response = response.json()

for Organisation in response:
  for AuthServer in Organisation['AuthorisationServers']:
    if AuthServer['AuthorisationServerId']=='7844e311-aa1f-4f67-9475-cbd989310b3e':
      AS_WellKnown=AuthServer['OpenIDDiscoveryDocument']
      AS_Resources=AuthServer['ApiResources']
```

---

*Conteúdo baixado em 16/09/2026, 15:37:25*
