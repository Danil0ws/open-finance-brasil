# Personal v1.0.0

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability/Personal-v1.0.0](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability/Personal-v1.0.0)
**Slug:** `Credit-Portability/Personal-v1.0.0`

---

---
title: Personal Credit Portability v1.0.0
---

[← Credit Portability](Credit-Portability)

# Overview

Portability of personal credit, version 1.0.0. The specification calls this
version Crédito Pessoal Clean and its contracts CREDITO_PESSOAL_CLEAN; version
1.1.0 renamed both to Sem Consignação. Sixteen modules take a
portability request through the status flow: the request itself, settlement
accepted, cancelled, rejected, and the refusals for an expired consent, an invalid
consent, an invalid token, wrong contract terms and a duplicated request.

Version 1.1.0-rc.1 is also published and has its own page. Both are live in the
suite at the same time.

# Before you start

- The test user needs at least one CREDITO_PESSOAL_CLEAN contract whose portability eligibility is DISPONIVEL with isEligible TRUE.
- Several modules poll for up to 10 minutes waiting for a status transition that a person on the other side has to perform.
- The consent is created with the Credit Operations permission group.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Credit Portability API - v1.0.0 - Conformance Suite | credit-portability_test-plan_v1 | 16 | 09/05/2025 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Credit Portability API - v1.0.0 - Conformance Suite - 16 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentId<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

# Test modules

| Test module | What it does |
|---|---|
| credit-portability_api_core_test-module_v1 | Checks a portability request over an eligible personal credit contract is accepted, with creditor, periodicity, term and amount taken from the original contract. |
| credit-portability_api_contract-term_test-module_v1 | Checks a proposal is accepted when the number of instalments offered is smaller than the term left on the original contract. |
| credit-portability_api_invalid-status_test-module_v1 | Checks a portability request over a contract already in a portability process is refused with EM_ANDAMENTO, and over an ineligible contract with CONTRATO_NAO_ELEGIVEL. |
| credit-portability_api_invalid-contract-terms_test-module_v1 | Checks a proposal is refused with CAMPO_INCONSISTENTE, PERIODICIDADE_INVALIDA, PRAZO_ACIMA_LIMITE or NAO_INFORMADO when it diverges from the original contract. |
| credit-portability_api_negative_test-module_v1 | Checks a portability request sent without the digital signature proof is refused with SEM_EVIDENCIA_ASSINATURA. |
| credit-portability_api_accepted-settlement_test-module_v1 | Checks a portability accepted by the creditor leaves RECEIVED and PENDING behind and settles into ACCEPTED_SETTLEMENT_IN_PROGRESS. |
| credit-portability_api_rejected-portability_test-module_v1 | Checks a portability the creditor turns down ends REJECTED with reason RETENCAO_DO_CLIENTE. |
| credit-portability_api_cancelled-portability_test-module_v1 | Checks the customer can cancel a portability just created, leaving it CANCELLED with reason CANCELADO_PELO_CLIENTE. |
| credit-portability_api_portability-payment_core_test-module_v1 | Runs a personal credit portability through to PORTABILITY_COMPLETED once the proposing institution has paid the settlement. |
| credit-portability_api_x-fapi_test-module_v1 | Checks every eligibility, portability, account data and payment endpoint refuses a missing or malformed x-fapi-interaction-id and echoes a valid one back. |
| credit-portability_api_expired-consent_test-module_v1 | Checks a portability request is refused with 401 when it carries a token from a consent that has expired and moved to REJECTED. |
| credit-portability_api_invalid-token_test-module_v1 | Checks each endpoint refuses the wrong grant type, client_credentials on eligibility and creation, authorisation_code on the proposing institution's endpoints. |
| credit-portability_api_invalid-consent_test-module_v1 | Checks every portability endpoint answers 403 to a token from a consent carrying customer data permissions instead of Credit Operations. |
| credit-portability_api_portability-idempotency_test-module_v1 | Checks a repeated x-idempotency-key with the same payload returns the same accepted result, and with a changed payload is refused with ERRO_IDEMPOTENCIA. |
| credit-portability_api_portability-invalid-payment_test-module_v1 | Checks a settlement paid short of the outstanding balance takes the portability to PAYMENT_ISSUE once the creditor spots the discrepancy. |
| credit-portability_api_portability-patch-unhappy_test-module_v1 | Checks a cancellation is refused with 422 once the portability has reached ACCEPTED_SETTLEMENT_COMPLETED. |

# Spreadsheet

[CS-Personal-Credit-Portability-v1.0.0.xlsx](uploads/410a221aacf25df2b55081976089311a/CS-Personal-Credit-Portability-v1.0.0.xlsx)

# Change history

<details>
<summary>2026 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |

</details>

<details>
<summary>2025 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 09/05/2025 | The v1.0.0 plan was released. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*1 plan, 16 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:19*
