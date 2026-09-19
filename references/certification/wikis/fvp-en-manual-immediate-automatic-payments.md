# Automatic Payments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Automatic-Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Automatic-Payments)
**Slug:** `FVP/EN/Manual/Immediate/Automatic-Payments`

---

---
title: Automatic Payments
---

[← Manual FVP / Open FVP](FVP/EN/Manual/Immediate)

# Manual FVP - Automatic Payments

This page gathers the manual FVP plans for Automatic Payments. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Automatic Payments API - v2.2.0 - Sweeping - Open FVP
Technical name: `fvp-automatic-sweeping-payments_open_test-plan-v2-2`

Validates the creation, authorisation and execution of Sweeping Accounts recurring consents and payments, including expiry by term and by total amount, revocation, rejection on a divergent creditor, blocking by a future startDateTime, and scope validation.

### Before you start
- Execution window: Immediate plan: all modules run in the same session, with no night-time window. Keep the participant server online during the run.
- Must be a CNPJ (Automatic Pix does not accept a CPF as the creditor account).
- The debtor account needs enough balance for the payments executed in the session: the core modules settle up to R$ 1.00 in total, and the wrong-creditor module attempts payments of R$ 300.00 each.
- If brazilCpf/brazilCnpj are not configured, the core modules use the fallback CPF 99991111140.

### Configuration Form Fields
| Field | Requirement | Description |
| --- | --- | --- |
| Type | Optional | Execution type for this run (optional). Leave empty to run as normal. Selecting 'Test' requires a Cycle; selecting 'Retest' requires a Cycle and an SD Ticket. These values are appended to the test description. (Options: —, Test, Retest) |
| Cycle | Optional | Cycle this run belongs to. Required when a Type (Test or Retest) is selected. |
| SD Ticket | Optional | Service Desk ticket for this run. Required when the Type is 'Retest'. |
| Authorisation Server ID | Required | Authorisation Server ID is used to find both OrganisationId and OpenIDDiscoveryDocument in the /participants endpoint. |
| Payment consent - Creditor Account ISPB | Required | Must be filled with the ISPB (Identificador do Sistema de Pagamentos Brasileiros) of the credited account from the SPI (Sistema de Pagamentos Instantâneos). Enter only numbers, 8 digits. |
| Payment consent - Creditor Account Issuer | Required | Code of the issuing branch without the check digit. Only numbers, up to 4 digits. |
| Payment consent - Creditor Account Number | Required | Must be filled with the account number of the receiving user, including the check digit (if applicable). If there is an alphanumeric character, it should be converted to 0. Only numbers, up to 20 digits. |
| Payment consent - Creditor Account Type | Required | Types of accounts used for payment. Must follow the formats defined in the API's Swagger documentation. |
| Payment consent - Creditor Account Name | Required | Creditor Account Name. This will be used as part of the body of the request sent to the payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules, except the qrdn test module and the optional test modules. |
| brazilCpf | Required | The 'CPF' value to be used in the consent creation request. It is also used as the Logged User Identification (it replaces the former loggedUser field). |
| brazilCnpj | Optional | The 'CNPJ' value to be used in the consent creation request. It is also used as the Business Entity Identification (it replaces the former businessEntity field). |
| description | Optional | Free-text description of this run. Optional; can be left blank. |

### Modules and what to expect
| Test module | What it does |
| --- | --- |
| fvp_automatic-payments_api_revoked-consent_test-module_v2-2 | A consent with no expiry is revoked; after revocation, payment attempts are blocked (401/422) and the refresh token stops working. |
| fvp_automatic-payments_api_sweeping-accounts-consent-edition_test-module_v2-2 | An attempt to edit the sweeping consent via PATCH is refused (CAMPO_NAO_PERMITIDO) and the fields remain unchanged. |
| fvp_automatic-payments_api_sweeping-accounts-core_test-module_v2-2 | Core sweeping flow: two payments summing to the consent's total (BRL 1.00) settle (ACSC) and the consent is consumed. |
| fvp_automatic-payments_api_sweeping-accounts-totalAllowedAmount_test-module_v2-2 | A payment exceeding the consent's total allowed amount is rejected (LIMITE_VALOR_TOTAL_CONSENTIMENTO_EXCEDIDO). |
| fvp_automatic-payments_api_expirationDateTime_test-module_v2-2 | Confirms the consent expires at its expirationDateTime and that payments after expiry are blocked (401/422). |
| fvp_automatic-payments_api_invalid-scope_test-module_v2-2 | A consent authorised with an incorrect scope fails at redirect or has the payment blocked (403). |
| fvp_automatic-payments_api_startDateTime_test-module_v2-2 | A payment issued before the consent's start date (startDateTime) is rejected (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_sweeping-accounts-consents-core_test-module_v2-2 | Confirms the sweeping consent does not expire within 5 minutes while awaiting authorisation (the suite waits 7 minutes before checking). |
| fvp_automatic-payments_api_sweeping-accounts-wrong-creditor_test-module_v2-2 | Several payment attempts with a diverging creditor (document, proxy, account) are rejected (PAGAMENTO_DIVERGENTE_CONSENTIMENTO / PARAMETRO_NAO_INFORMADO). |

### Notes
- The expirationDateTime module waits 2 minutes (a suite sleep) to check the consent expiry; allow extra time in the run.
- The sweeping-accounts-consents-core module waits 7 minutes (a suite sleep) to validate that the consent does not expire prematurely.
- The creditor account (Creditor Account CPF/CNPJ) must be a CNPJ for Automatic Pix plans (including Sweeping Accounts); a CPF is not accepted as the creditor.
- Fill brazilCpf OR brazilCnpj according to the debtor type (PF or PJ); never both at the same time.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2025-10-29 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/07e33112b5dcadbed4436436d24eefe8/FVP-Automatic-Payments-API-v2.2.0-Sweeping-Open-FVP.xlsx)

## ⚙️ 2) Automatic Payments API - v2.2.0 - Automatic Pix - Open FVP
Technical name: `fvp-automatic-pix-payments_open_test-plan-v2-2`

Validates the full cycle of automatic payments via recurring Pix (v2.2.0) in the Open FVP profile, covering recurring consent authorisation and execution, instalment scheduling, consent limit editing, revocation and rejection on divergent amounts, dates or creditor.

### Before you start
**Account balance**
- D+0: exactly R$ 0.00 (mandatory)
- D+1: exactly R$ 0.00 (mandatory)
- D+2: exactly R$ 0.00 (mandatory)
- D+3: minimum R$ 1.00 (mandatory) - Minimum balance for the scheduled retry run (Module 3).
- Execution window: 21:00 to 23:59 BRT on the scheduled days (Modules 2 and 3 of scheduling/retry)
- must be a CNPJ (Automatic Pix does not support a CPF as the creditor)
- D+N refers to N calendar days after Module 1 runs.
- The follow-up modules (Module 2 and Module 3) are started automatically by the FVP at the scheduled time; do not run them manually.

### Configuration Form Fields
| Field | Requirement | Description |
| --- | --- | --- |
| Type | Optional | Execution type for this run (optional). Leave empty to run as normal. Selecting 'Test' requires a Cycle; selecting 'Retest' requires a Cycle and an SD Ticket. These values are appended to the test description. (Options: —, Test, Retest) |
| Cycle | Optional | Cycle this run belongs to. Required when a Type (Test or Retest) is selected. |
| SD Ticket | Optional | Service Desk ticket for this run. Required when the Type is 'Retest'. |
| Authorisation Server ID | Required | Authorisation Server ID is used to find both OrganisationId and OpenIDDiscoveryDocument in the /participants endpoint. |
| Recurring Payment consent - Contract Debtor Name | Required | Contract Debtor Name. This will be used as part of the body of the request sent to the recurring payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules that send firstPayment field. |
| Recurring Payment consent - Contract Debtor Identification | Required | Contract Debtor Identification. This will be used as part of the body of the request sent to the recurring payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules that send firstPayment field. |
| Payment consent - Creditor Account ISPB | Required | Must be filled with the ISPB (Identificador do Sistema de Pagamentos Brasileiros) of the credited account from the SPI (Sistema de Pagamentos Instantâneos). Enter only numbers, 8 digits. |
| Payment consent - Creditor Account Issuer | Required | Code of the issuing branch without the check digit. Only numbers, up to 4 digits. |
| Payment consent - Creditor Account Number | Required | Must be filled with the account number of the receiving user, including the check digit (if applicable). If there is an alphanumeric character, it should be converted to 0. Only numbers, up to 20 digits. |
| Payment consent - Creditor Account Type | Required | Types of accounts used for payment. Must follow the formats defined in the API's Swagger documentation. |
| Payment consent - Creditor Account Name | Required | Creditor Account Name. This will be used as part of the body of the request sent to the payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules, except the qrdn test module and the optional test modules. |
| Payment consent - Creditor Account CPF / CNPJ | Required | Creditor Account CPF / CNPJ. This will be used as part of the body of the request sent to the payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules, except the qrdn test module and the optional test modules. |
| brazilCpf | Required | The 'CPF' value to be used in the consent creation request. It is also used as the Logged User Identification (it replaces the former loggedUser field). |
| brazilCnpj | Optional | The 'CNPJ' value to be used in the consent creation request. It is also used as the Business Entity Identification (it replaces the former businessEntity field). |
| description | Optional | Free-text description of this run. Optional; can be left blank. |

### Modules and what to expect
| Test module | What it does |
| --- | --- |
| fvp_automatic-payments_api_automatic-pix-semanal-core_open_test-module_v2-2 | Core weekly automatic-payment flow: the first payment settles (ACSC) and the second instalment is scheduled and then cancelled. |
| fvp_automatic-payments_api_automatic-pix-scheduled-firstPayment_open_test-module_v2-2 | First payment without a debtor account; checks the server returns the debtor account after authorisation and schedules the next instalment. |
| fvp_automatic-payments_api_automatic-pix-consent-edition-permissive_open_test-module_v2-2 | Edits the consent via PATCH (creditor name, amount limit, expiry) and confirms the next payment is scheduled normally. |
| fvp_automatic-payments_api_automatic-pix-failed-firstPayment_open_test-module_v2-2 | The first payment with an amount diverging from the consent is refused (RJCT / PAGAMENTO_DIVERGENTE_CONSENTIMENTO); the next instalment is scheduled (SCHD). |
| fvp_automatic-payments_api_automatic-pix-revoked_open_test-module_v2-2 | After the first payment settles (ACSC), revokes the consent via PATCH; the next instalment is cancelled or rejected due to the revoked consent. |
| fvp_automatic-payments_api_automatic-pix-consent-edition-negative_open_test-module_v2-2 | Four invalid consent-edit attempts via PATCH, all refused with 422 (DETALHE_EDICAO_INVALIDO / PARAMETRO_NAO_INFORMADO). |
| fvp_automatic-payments_api_automatic-pix-firstPayment-invalid-creditor_open_test-module_v2-2 | A payment to a creditor account different from the consent's is rejected (RJCT / PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_automatic-pix-maximumVariableAmount_open_test-module_v2-2 | An instalment above the consent's maximum variable amount is rejected (LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO). |
| fvp_automatic-payments_api_automatic-pix-no-limits_test-module_v2-2 | Consent with no amount limits and no defined first payment; both instalments are scheduled (SCHD) normally. |
| fvp_automatic-payments_api_automatic-pix-invalid-dates-later_test-module_v2-2 | An instalment scheduled beyond the allowed window is rejected (FORA_PRAZO_PERMITIDO). |
| fvp_automatic-payments_api_automatic-pix-referenceStartDate_test-module_v2-2 | An instalment dated before the consent's reference start date is rejected (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_automatic-pix-scheduling-before-firstPayment_test-module_v2-2 | An instalment scheduled before the first-payment date is rejected (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_automatic-pix-invalid-dates-sooner_test-module_v2-2 | An instalment scheduled before the minimum allowed window is rejected (FORA_PRAZO_PERMITIDO). |
| fvp_automatic-payments_api_automatic-pix-unmatching-creditor_test-module_v2-2 | A payment to a creditor with the Central Bank ISPB and a random account is accepted by the holder (the failure is expected only at SPI settlement). |
| fvp_automatic-payments_api_automatic-pix-fixedAmount_test-module_v2-2 | An instalment with an amount different from the consent's fixed amount is rejected (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |

### Notes
- The follow-up modules (scheduling/retry) are scheduled automatically by the Conformance Suite; do not run them manually.
- Keep the participant server online and responsive between 21:00 and 23:59 BRT on the days scheduled for the retry modules.
- Automatic Pix is intended exclusively for payments to legal entities (CNPJ). The creditor account must belong to a company; payments to a CPF are not valid in this flow.
- The creditorCpfCnpj field (Creditor Account CPF/CNPJ) must be filled with a CNPJ for Automatic Pix; a CPF is not accepted in this plan.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2025-10-29 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/42857dfedda1a19cadeb99a92b15635c/FVP-Automatic-Payments-API-v2.2.0-Automatic-Pix-Open-FVP.xlsx)

---

[↑ Open FVP](FVP/EN/Manual/Immediate) · [◀ Enrollments](FVP/EN/Manual/Immediate/Enrollments) · [Credit Portability ▶](FVP/EN/Manual/Immediate/Credit-Portability)


---

*Conteúdo baixado em 16/09/2026, 15:37:39*
