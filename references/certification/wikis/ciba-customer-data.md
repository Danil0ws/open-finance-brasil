# Customer Data

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA/Customer-Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA/Customer-Data)
**Slug:** `CIBA/Customer-Data`

---

---
title: Customer Data
---

[← CIBA](CIBA)

# Overview

Decoupled authorisation of a Customer Data consent, from client registration to a
call on a protected resource. The plan checks that the transmitting institution
publishes the backchannel capability, accepts a backchannel authorisation request
bound to an existing consent, notifies the receiver through the ping delivery
mode, and issues a token the Resources API accepts.

It does not re-validate the payload of the Consents or Resources APIs. Those are
used here only to prove the flow reached an authorised consent and a usable token.

# Before you start

- The Software Statement must expose the notification endpoint. Its software_api_webhook_uris has to contain https://web.conformance.directory.openbankingbrasil.org.br/test-mtls/a/<alias>, where <alias> is the alias field in the test configuration. The test registers its client with that URI as the backchannel notification endpoint, and the notification is rejected without it.
- The client is created by the test. It performs a DCR call for a CIBA enabled client, with backchannel_token_delivery_mode as ping, and deletes it at the end even when the test fails.
- The notification endpoint must be mTLS protected.
- A tester must approve the consent in the decoupled channel. The suite waits up to 10 minutes and nothing is redirected to a browser.
- The test user must own at least one resource. After the token is issued the Resources API is polled every 30 seconds for up to 5 minutes and must return something.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| CIBA - v2.1.0-beta.1 - Customer Data - Conformance Suite | ciba_customer-data_test-plan_v2-1 | 3 | 28/08/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>CIBA - v2.1.0-beta.1 - Customer Data - Conformance Suite - 18 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.jwks |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |
| Other | resource.redirectFallbackTrigger |

</details>

# Test modules

| Test module | What it does |
|---|---|
| ciba_consent-approval_ping_happy-path_test-module_v2-1 | Runs the full CIBA ping flow for a data consent, from client credentials through to resource access, with no fallback to redirect. |
| ciba_redirect-start_ciba-fallback_test-module_v2-1 | Begins as a standard redirect (FAPI hybrid) authorization and then falls back to CIBA to complete the authorization. |
| ciba_ping-to-poll-fallback_test-module_v2-1 | Validate the ping to poll fallback: when the ping callback fails repeatedly, the receiver falls back to polling the consent status until authorization completes. |

# Spreadsheet

[CS-Customer-Data.xlsx](uploads/c6123fbbda50e10a1fb7a869296bcb6e/CS-Customer-Data.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 28/08/2026 | First beta released, with the ping happy path: register a CIBA enabled client, create the consent, call bc-authorize, receive the ping notification, exchange the auth_req_id for a token and reach the Resources API. | No |  |

</details>

# Notes

- The configuration form offers Enable Redirect Fallback. Only the ping happy path runs in this beta, so the field has no effect yet.

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*1 plan, 3 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:12*
