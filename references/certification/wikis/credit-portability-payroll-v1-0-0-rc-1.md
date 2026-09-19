# Payroll v1.0.0 rc.1

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability/Payroll-v1.0.0-rc.1](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability/Payroll-v1.0.0-rc.1)
**Slug:** `Credit-Portability/Payroll-v1.0.0-rc.1`

---

---
title: Payroll Credit Portability v1.0.0-rc.1
---

[← Credit Portability](Credit-Portability)

# Overview

Portability of federal payroll credit, which the specification calls Consignado
Federal. Every module acts on contracts whose productSubTypeCategory is
CONSIGNADO_SIAPE, the federal public servant payroll, so this is not payroll
credit in general.

The emphasis differs from the unsecured personal plan: a larger share of the
modules are refusals, covering a contract already under concurrent
management, a request missing required parameters, and the creditor rejecting the
portability for a payment that was wrong or never arrived.

# Before you start

- The test user needs at least one CONSIGNADO_SIAPE contract whose portability eligibility is DISPONIVEL with isEligible TRUE.
- One module needs TWO such contracts, one of them with its concurrent-management status set to EM ANDAMENTO, so that the refusal it is testing can happen. This is the requirement most likely to be missing on the first attempt.
- Several modules need a person to act during the run, and they wait.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Payroll Credit Portability API - v1.0.0-rc.1 - Conformance Suite | payroll-credit-portability_test-plan_v1 | 21 | 29/11/2025 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Payroll Credit Portability API - v1.0.0-rc.1 - Conformance Suite - 16 fields</summary>

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
| payroll-credit-portability_api_contract-invalid-status_test-module_v1 | Checks a portability request over a contract already in a portability process is refused with EM_ANDAMENTO, and over an ineligible contract with CONTRATO_NAO_ELEGIVEL. |
| payroll-credit-portability_api_contract-invalid-terms_test-module_v1 | Checks a proposal is refused with CAMPO_INCONSISTENTE, PERIODICIDADE_INVALIDA, PRAZO_ACIMA_LIMITE or VALOR_DIVERGENTE when it diverges from the original contract. |
| payroll-credit-portability_api_contract-no-sign_test-module_v1 | Checks a portability request sent without the digital signature proof is refused with SEM_EVIDENCIA_ASSINATURA. |
| payroll-credit-portability_api_user-create-portability_test-module_v1 | Checks a portability request over an eligible payroll contract is accepted, with creditor, periodicity, term and amount taken from the original contract. |
| payroll-credit-portability_api_x-fapi_test-module_v1 | Checks every eligibility, portability, account data and payment endpoint refuses a missing or malformed x-fapi-interaction-id and echoes a valid one back. |
| payroll-credit-portability_api_expired-consent_test-module_v1 | Checks a portability request is refused with 401 when it carries a token from a consent that has expired and moved to REJECTED. |
| payroll-credit-portability_api_invalid-token_test-module_v1 | Checks each endpoint refuses the wrong grant type, client_credentials on eligibility and creation, authorisation_code on the proposing institution's endpoints. |
| payroll-credit-portability_api_portability-idempotency_test-module_v1 | Checks a repeated x-idempotency-key with the same payload returns the same accepted result, and with a changed payload is refused with ERRO_IDEMPOTENCIA. |
| payroll-credit-portability_api_creditor-rejected-portability_test-module_v1 | Follows a portability to ACCEPTED_SETTLEMENT_COMPLETED and checks the creditor can still reject it for reasons unrelated to payment, with CLIENTE_COM_ACAO_JUDICIAL. |
| payroll-credit-portability_api_user-cancelled-portability_test-module_v1 | Checks the customer can cancel a portability still in RECEIVED, leaving it CANCELLED with reason CANCELADO_PELO_CLIENTE. |
| payroll-credit-portability_api_user-cancelled-counteroffer_test-module_v1 | Checks the customer can cancel while the portability sits in PENDING awaiting the creditor's counteroffer, leaving it CANCELLED with CANCELADO_PELO_CLIENTE. |
| payroll-credit-portability_api_user-cancelled-counteroffer-progress_test-module_v1 | Checks a cancellation by the customer is still accepted after the portability has moved to ACCEPTED_SETTLEMENT_IN_PROGRESS, with reason CANCELADO_PELO_CLIENTE. |
| payroll-credit-portability_api_user-accepted-counteroffer_test-module_v1 | Checks that when the customer takes the creditor's counteroffer the portability ends REJECTED by CREDORA with reason RETENCAO_DO_CLIENTE. |
| payroll-credit-portability_api_user-cancelled-settlement-completed_test-module_v1 | Checks a cancellation is refused with CANCELAMENTO_NAO_EFETUADO once the portability has reached ACCEPTED_SETTLEMENT_COMPLETED. |
| payroll-credit-portability_api_creditor-rejected-payment-nofound_test-module_v1 | Checks the creditor rejects a portability with DECURSO_DO_PRAZO_PARA_PAGAMENTO when the settlement payment is never made. |
| payroll-credit-portability_api_creditor-rejected-payment-error_test-module_v1 | Checks a settlement paid for the wrong amount moves to PAYMENT_ISSUE and, left uncorrected, ends REJECTED with DIVERGENCIA_DE_PAGAMENTO_EFETUADO. |
| payroll-credit-portability_api_proposer-rejected-discharged_test-module_v1 | Checks a discharge request on a settled portability can end in rejection by the proposing institution with reason RESERVA_DA_MARGEM. |
| payroll-credit-portability_api_proposer-rejected_test-module_v1 | Checks the proposing institution can reject a portability during settlement with SALDO_DEVEDOR_ATUALIZADO_SUBSTANCIALMENTE_DIVERGENTE. |
| payroll-credit-portability_api_payment-issue-completed_test-module_v1 | Runs the journey with a settlement paid for the wrong amount, then corrected, and checks it recovers from PAYMENT_ISSUE through to PORTABILITY_COMPLETED. |
| payroll-credit-portability_api_invalid-consent_test-module_v1 | Checks every portability endpoint answers 403 to a token from a consent carrying customer data permissions instead of Credit Operations. |
| payroll-credit-portability_api_portability_completed_test-module_v1 | Runs the whole journey to PORTABILITY_COMPLETED, including the registering entity call that returns payrollContractNumber. |

# Spreadsheet

[CS-Payroll-Credit-Portability-v1.0.0-rc.1.xlsx](uploads/ec4290dedbea58b7f1b1fac6f5e7b1c5/CS-Payroll-Credit-Portability-v1.0.0-rc.1.xlsx)

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
| 29/11/2025 | Release candidate 1 released, with twenty-one modules. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*1 plan, 21 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:18*
