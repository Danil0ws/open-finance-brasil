# Payments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Payments)
**Slug:** `FVP/EN/Manual/Immediate/Payments`

---

---
title: Payments
---

[← Manual FVP / Open FVP](FVP/EN/Manual/Immediate)

# Manual FVP - Payments

This page gathers the manual FVP plans for Payments. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Payments API - v5.0.0 - Open FVP
Technical name: `fvp-payments-e2e_open_test-plan-v5`

Validates the full Pix payment flow (E2E) in production on the v5 API, from the server-configuration pre-flight through debtor-account selection, an invalid proxy and recurring payments in the custom, daily and monthly formats, with creation, authorisation, scheduling and cancellation of consents and payments.

### Before you start
**Account balance**
- D+0: exactly R$ 2.00 (mandatory)
- D+1: exactly R$ 2.00 (mandatory)
- D+2: exactly R$ 1.00 (mandatory)
- Execution window: 05:00 to 06:59 BRT on the scheduled days (Module 2, automatic)
- The creditor account may be a CPF or a CNPJ.
- Module 1 (manual): schedules two Pix payments, the first for D+1 and the second for D+2. Expected flow: Awaiting authorisation → Authorised → Scheduled.
- Module 2 (automatic): the suite verifies that both scheduled payments completed with status ACSC.
- D+N refers to N calendar days after Module 1 runs.

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
| Payment consent - Creditor Account CPF / CNPJ | Required | Creditor Account CPF / CNPJ. This will be used as part of the body of the request sent to the payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules, except the qrdn test module and the optional test modules. |
| Payment consent - Creditor Account Proxy | Required | Creditor Account Proxy. This will be used as part of the body of the request sent to the payment consent endpoint. Those fields will be used to create the Consent Request Payload of all the test modules, except the qrdn test module and the optional test modules. |
| brazilCpf | Required | The 'CPF' value to be used in the consent creation request. It is also used as the Logged User Identification (it replaces the former loggedUser field). |
| brazilCnpj | Optional | The 'CNPJ' value to be used in the consent creation request. It is also used as the Business Entity Identification (it replaces the former businessEntity field). |
| description | Optional | Free-text description of this run. Optional; can be left blank. |

### Modules and what to expect
| Test module | What it does |
| --- | --- |
| fvp-preflight-cert-check-payments-test-v5 | Checks, before the flow, that the server has published the v5.0.0 payment endpoints in the Directory. |
| payments_api_no-debtor-account_open_test-module_v5 | Pays a Pix without providing the debtor account in the request, leaving the choice to the holder; the payment settles normally (ACSC). |
| payments_api_fake-email-proxy_open_test-module_v5 | A payment with an invalid email as the proxy key is rejected (RJCT) or refused outright (422 DETALHE_PAGAMENTO_INVALIDO / PAGAMENTO_RECUSADO_DETENTORA). |
| fvp-payments_api_recurring-payments-custom-core_open_test-module_v5 | Creates a custom recurring consent (5 dates) and confirms the 5 scheduled payments (SCHD). |
| fvp-payments_api_recurring-payments-patch_open_test-module_v5 | Creates a recurring consent of 5 daily payments and validates cancellation by the initiator, first of a single payment and then of all. |
| fvp-payments_api_recurring-payments-monthly-core_open_test-module_v5 | Creates a monthly recurring consent (day 31, adjusted for shorter months) and confirms the 5 scheduled payments (SCHD). |
| fvp-payments_api_recurring-payments-custom-not-cancelled_open_test-module_v5 | Creates a custom recurring consent of 2 payments and confirms both stay scheduled (SCHD). |

### Notes
- Module 2 is scheduled automatically by the Conformance Suite; do not run it manually.
- Keep the participant server online and responsive between 05:00 and 06:59 BRT on the scheduled days.
- D+N refers to N calendar days after Module 1 runs.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-07-03 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/47c61c6cc4319d6bf6ab8904d67b5e9e/FVP-Payments-API-v5.0.0-Open-FVP.xlsx)

---

[↑ Open FVP](FVP/EN/Manual/Immediate) · [◀ Customer Data](FVP/EN/Manual/Immediate/Customer-Data) · [Restricted FVP ▶](FVP/EN/Manual/Scheduled)


---

*Conteúdo baixado em 16/09/2026, 15:37:43*
