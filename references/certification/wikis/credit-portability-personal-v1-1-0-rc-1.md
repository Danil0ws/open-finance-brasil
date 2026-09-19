# Personal v1.1.0 rc.1

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability/Personal-v1.1.0-rc.1](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability/Personal-v1.1.0-rc.1)
**Slug:** `Credit-Portability/Personal-v1.1.0-rc.1`

---

---
title: Personal Credit Portability v1.1.0-rc.1
---

[← Credit Portability](Credit-Portability)

# Overview

Portability of personal credit without payroll deduction, which the
specification calls Crédito Pessoal Sem Consignação and its contracts
CREDITO_PESSOAL_SEM_CONSIGNACAO. The plan walks a portability request from the
consent that authorises reading the contract, through the request itself, to each
of the outcomes the status flow allows: settlement accepted, cancelled, rejected,
and the refusals that protect against a bad request.

This is the release candidate for v1.1.0. The v1.0.0 plan is still published and
has its own page.

# Before you start

- The test user needs at least one CREDITO_PESSOAL_SEM_CONSIGNACAO contract whose portability eligibility is DISPONIVEL with isEligible TRUE. Without it the plan cannot create a portability request and every module fails at the same step.
- Several modules need a person present. They poll for up to 10 minutes waiting for a status transition that the other side has to make, so book the time before starting rather than discovering it mid-run.
- The consent is created with the Credit Operations permission group. A consent granted with a narrower set will be refused at the first call.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Credit Portability API - v1.1.0-rc.1 - Conformance Suite | credit-portability_test-plan_v1-1 | 17 | 28/08/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Credit Portability API - v1.1.0-rc.1 - Conformance Suite - 16 fields</summary>

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
| credit-portability_api_portability-payment_core_test-module_v1-1 | Runs an unsecured contract's portability through to PORTABILITY_COMPLETED once the proposing institution has paid the settlement. |
| credit-portability_api_portability-with_warranty_test-module_v1-1 | Runs the journey through to PORTABILITY_COMPLETED for a contract secured by an OPERACOES_GARANTIDAS_PELO_GOVERNO warranty. |
| credit-portability_api_core_test-module_v1-1 | Checks a portability request over an eligible contract with no warranty is accepted, with creditor, periodicity, term and amount taken from the original contract. |
| credit-portability_api_contract-term_test-module_v1-1 | Checks a proposal is accepted when the number of instalments offered is smaller than the term left on the original contract. |
| credit-portability_api_invalid-status_test-module_v1-1 | Checks a portability request over a contract already in a portability process is refused with EM_ANDAMENTO, and over an ineligible contract with CONTRATO_NAO_ELEGIVEL. |
| credit-portability_api_invalid-contract-terms_test-module_v1-1 | Checks a proposal is refused with CAMPO_INCONSISTENTE, PERIODICIDADE_INVALIDA, PRAZO_ACIMA_LIMITE or NAO_INFORMADO when it diverges from the original contract. |
| credit-portability_api_negative_test-module_v1-1 | Checks a portability request sent without the digital signature proof is refused with SEM_EVIDENCIA_ASSINATURA. |
| credit-portability_api_accepted-settlement_test-module_v1-1 | Checks a portability accepted by the creditor leaves RECEIVED and PENDING behind and settles into ACCEPTED_SETTLEMENT_IN_PROGRESS. |
| credit-portability_api_rejected-portability_test-module_v1-1 | Checks a portability the creditor turns down ends REJECTED with reason RETENCAO_DO_CLIENTE. |
| credit-portability_api_cancelled-portability_test-module_v1-1 | Checks the customer can cancel a portability just created, leaving it CANCELLED with reason CANCELADO_PELO_CLIENTE. |
| credit-portability_api_x-fapi_test-module_v1-1 | Checks every eligibility, portability, account data and payment endpoint refuses a missing or malformed x-fapi-interaction-id and echoes a valid one back. |
| credit-portability_api_expired-consent_test-module_v1-1 | Checks a portability request is refused with 401 when it carries a token from a consent that has expired and moved to REJECTED. |
| credit-portability_api_invalid-token_test-module_v1-1 | Checks each endpoint refuses the wrong grant type, client_credentials on eligibility and creation, authorisation_code on the proposing institution's endpoints. |
| credit-portability_api_invalid-consent_test-module_v1-1 | Checks eligibility and portability creation answer 403 to a token from a customer data consent, and the proposing institution's endpoints answer 403 to its client_credentials token. |
| credit-portability_api_portability-idempotency_test-module_v1-1 | Checks a repeated x-idempotency-key with the same payload returns the same accepted result, and with a changed payload is refused with ERRO_IDEMPOTENCIA. |
| credit-portability_api_portability-invalid-payment_test-module_v1-1 | Checks a settlement paid short of the outstanding balance takes the portability to PAYMENT_ISSUE once the creditor spots the discrepancy. |
| credit-portability_api_portability-patch-unhappy_test-module_v1-1 | Checks a cancellation is refused with 422 once the portability has reached ACCEPTED_SETTLEMENT_COMPLETED. |

# Spreadsheet

[CS-Personal-Credit-Portability-v1.1.0-rc.1.xlsx](uploads/be775677d1b9566c87295107c43bf2b2/CS-Personal-Credit-Portability-v1.1.0-rc.1.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 28/08/2026 | Release candidate 1 of v1.1.0 released, with seventeen modules covering the full status flow. | No |  |

</details>

# Notes

- The contract type this version requires is named CREDITO_PESSOAL_SEM_CONSIGNACAO. The v1.0.0 plan asks for CREDITO_PESSOAL_CLEAN instead. If you are moving from one to the other, the test data has to change with it.

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*1 plan, 17 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:20*
