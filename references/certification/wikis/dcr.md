# DCR

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/DCR](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/DCR)
**Slug:** `DCR`

---

---
title: DCR
---

# Overview

DCR (Dynamic Client Registration) and DCM (Dynamic Client Management) are how a
receiving institution registers itself as a client on a transmitting
institution's authorisation server, with no manual onboarding step. The client
is created from a Software Statement Assertion issued by the Participant
Directory, and the roles carried in that assertion decide what the resulting
client may ask for.

These plans validate that side of the implementation: that a valid assertion
produces a working client, that one carrying the wrong role does not, that
another participant cannot take over a client that is not theirs, and that the
webhook endpoint declared during DCM is accepted and actually called.

They stop where a usable client exists. That is the precondition for every other
test plan in the suite, which is why a failure here usually explains failures
elsewhere.

# Before you start

- The Software Statement decides which plan you can run. The DADOS plan needs an assertion carrying the DADOS role and the PAGTO plans need PAGTO. The suite obtains the assertion from the Brazil sandbox directory using clients hardcoded into the test suite, so the role checks run against a known-good counterpart.
- Clear any client left over from a previous run of the BRCAC plan. That test uses a fixed certificate issued from the Software Statement 10120340-3318-4baf-99e2-0b56729c4ab2, which is shared with other tests, so a client already registered for that software makes the run start dirty.
- The webhook endpoint must be reachable and must match the assertion. The PAGTO plans check that webhook_uris sent during DCM matches software_api_webhook_uris on the assertion, and that the endpoint is genuinely called when a payment status changes, including for scheduled payments and after a failed delivery is retried.
- One plan deliberately leaves the client registered. dcr-no-delete_test-plan registers a client with the full scope set and does not unregister it at the end. That is the point of the test, so expect the client to still be there.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| DCR - BRCAC new Format - Conformance Suite | dcr-brcac-new_test-plan | 1 | 13/09/2022 |
| DCR - DADOS Role - Conformance Suite | dcr-dados_test-plan | 3 | 29/09/2022 |
| DCR - PAGTO Role - Payments v5.0.0 - Webhook v1.3.0 - Conformance Suite | dcr-dcm-pagto_test-plan-v5 | 5 | 11/04/2026 |
| DCR - Automatic FVP Homologation - Conformance Suite | dcr-fvp-homologation_test-plan | 2 | 25/10/2022 |
| DCR - Delete Not Executed - Conformance Suite | dcr-no-delete_test-plan | 1 | 13/09/2022 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>DCR - BRCAC new Format - Conformance Suite - 10 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.scope<br>client.org_jwks |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>DCR - DADOS Role - Conformance Suite - 13 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>DCR - PAGTO Role - Payments v5.0.0 - Webhook v1.3.0 - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.webhookWaitTime<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.apibase<br>directory.keystore |

</details>

<details>
<summary>DCR - Automatic FVP Homologation - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.authorisationServerId |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Second client TLS certificates | mtls2.cert<br>mtls2.key<br>mtls2.ca |
| Third client TLS certificates | mtls3.cert<br>mtls3.key<br>mtls3.ca |
| Resource | resource.brazilOrganizationId<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory2.client_id<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>DCR - Delete Not Executed - Conformance Suite - 13 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>DCR - BRCAC new Format - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| dcr_api_brcac2022-support_test-module | Checks the server accepts both the old and the new BRCAC certificate formats, using a certificate issued from a fixed software statement. |

</details>

<details>
<summary>DCR - DADOS Role - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| dcr_api_dados-happy-flow_test-module_v2 | Registers a new client from a DADOS software statement and completes an authorisation flow against it. |
| dcr_api_dados_unauthorized-client_test-module_v2 | Checks a software statement holding only the PAGTO role cannot obtain the resources scope, and that asking for it fails with invalid_scope. |
| dcr_api_dados-attempt-client-takeover_test-module_v2 | Registers a client, then attempts to take it over using valid credentials belonging to a different client, which must be refused. |

</details>

<details>
<summary>DCR - PAGTO Role - Payments v5.0.0 - Webhook v1.3.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| dcr_api_dcm-pagto-webhook-acsc_test-module-v5 | Checks the webhook endpoint is implemented and is called when a payment status changes, for the payments v5 API. |
| dcr_api_dcm-pagto-webhook-schd_test-module-v5 | Checks the webhook endpoint is called when a scheduled payment moves to SCHD, for the payments v5 API. |
| dcr_api_dcm-pagto-webhook_test-module-v5 | Checks a webhook endpoint registered during client management is accepted and then called when a payment status changes, for the payments v5 API. |
| dcr_api_dcm-pagto-remove-webhook_test-module-v5 | Checks a client management request can remove the webhook endpoint, and that a webhook is retried after a failure response, for the payments v5 API. |
| dcr_api_dcm-pagto-wrong-webhook_test-module-v5 | Checks webhook_uris is validated against software_api_webhook_uris on the software statement and a mismatch is refused, for the payments v5 API. |

</details>

<details>
<summary>DCR - Automatic FVP Homologation - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| dcr_api_fvp-brcac2022-support_test-module | Checks the server accepts both the old and the new BRCAC certificate formats, using a certificate issued from a fixed software statement. |
| fvp-payments-consents-server-certificate-v2 | Checks the certificate presented on the server's phase 2 and 3 endpoints follows the Brazilian certificate standard. |

</details>

<details>
<summary>DCR - Delete Not Executed - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| dcr_api_all-scopes-no-unregistration_test-module | Registers a client carrying every phase 2 and 3 scope and leaves it in place, returning its client_id for use by other tests. |

</details>

# Spreadsheet

[CS-DCR.xlsx](uploads/50e6b08b896473124242396c31575d9e/CS-DCR.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 11/04/2026 | The PAGTO role plan for Payments v5.0.0 with Webhook v1.3.0 was released. It runs the same five checks as the v4.0.1 plan against the newer versions. | No |  |

</details>

<details>
<summary>2022 - 3 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 25/10/2022 | The FVP homologation plan was released. | No |  |
| 29/09/2022 | The DADOS role plan was released, covering the happy path, an attempted takeover of a client belonging to another participant, and the refusal of the resources scope to an assertion that does not carry the role. | No |  |
| 13/09/2022 | First DCR plans released: registration with a certificate in the new BRCAC format, and a registration with the full scope set that deliberately leaves the client in place. | No |  |

</details>

# Notes

- The two PAGTO plans differ only in the versions they target, Payments v4.0.1 with Webhook v1.0.0 and Payments v5.0.0 with Webhook v1.3.0. The modules are otherwise the same checks.

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*5 plans, 12 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:23*
