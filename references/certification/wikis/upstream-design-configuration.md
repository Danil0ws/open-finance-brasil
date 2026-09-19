# Configuration

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Configuration](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Configuration)
**Slug:** `UpStream-Design/Configuration`

---

The **Configuration** of a [`TestModule`](./TestModule) is accomplished using a `JsonObject` provided to the [`TestRunner`](./TestRunner) when the test is started. 

Each [`TestModule`](./TestModule) (and [`Condition`](./Condition)) implementation has its own requirements for the contents of the **Configuration** object. For most OpenID Connect testing modules, the system looks for the following:

`server` has information about the IdP. This object can contain the entire server configuration as specified in the OIDC Discovery document, or alternatively it can have a single `discoveryUrl` member which contains a URL pointing to the OIDC Discovery document, to be fetched by the test. 

`client` has information about the RP. This object can contain the entire client registration object as specified in RFC7491/OIDC Registration, or alternatively it can contain the single `dynamicRegistration` member with the boolean value `true`, to cause the test to register the client dynamically with the server.

---

*Conteúdo baixado em 16/09/2026, 15:38:41*
