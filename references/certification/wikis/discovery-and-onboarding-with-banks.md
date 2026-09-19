# Discovery and Onboarding with Banks

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-and-Onboarding-with-Banks](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-and-Onboarding-with-Banks)
**Slug:** `Discovery-and-Onboarding-with-Banks`

---

## Finding Providers of Resources of Interest to our Customers

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



---

*Conteúdo baixado em 16/09/2026, 15:37:24*
