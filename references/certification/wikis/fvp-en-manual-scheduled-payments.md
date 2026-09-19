# Payments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Payments)
**Slug:** `FVP/EN/Manual/Scheduled/Payments`

---

---
title: Payments
---

[← Manual FVP / Restricted FVP](FVP/EN/Manual/Scheduled)

# Manual FVP - Payments

This page gathers the manual FVP plans for Payments. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Payments API - v5.0.0 - Scheduling - Restricted FVP
Technical name: `fvp-payments-e2e_restricted_test-plan-v5`

Validates the scheduled-payment flow in production (v5 API): consent creation and authorisation, scheduling of two payments for D+1 and D+2, and later verification that both were settled successfully.

### Before you start
**Account balance**
- D+0: exactly R$ 2.00 (mandatory)
- D+1: exactly R$ 2.00 (mandatory)
- D+2: exactly R$ 1.00 (mandatory)
- Execution window: 05:00 to 06:59 BRT on the scheduled days (Module 2, automatic)
- The creditor account may be a CPF or a CNPJ (unlike Automatic Pix, which requires a CNPJ).
- Module 1 (scheduling the two Pix payments, for D+1 and D+2) is manual; Module 2 (verifying that both reach ACSC) is scheduled automatically by the suite.
- The consentID, paymentIDs and refreshToken are persisted by the suite between the modules.
- If Module 1 fails, Module 2 is not scheduled.

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
| payments_api_scheduled-pix-verification_1-2_test-module_v5 | Creates and authorises the consent and schedules two Pix payments for D+1 and D+2, which reach Scheduled (SCHD). |
| payments_api_scheduled-pix-verification_2-2_test-module_v5 | Verifies that both scheduled payments settled (ACSC). |

### Notes
- Module 2 is scheduled automatically by the suite, reusing the consentID, paymentIDs and refreshToken saved by Module 1; do not run it manually.
- Server availability window: 05:00 to 06:59 BRT on the scheduled days (Module 2).
- Exact balances are required: R$ 2.00 on D+0 and D+1, and R$ 1.00 on D+2. Insufficient balance causes Module 2 to fail.
- The creditor account may be a CPF or a CNPJ in this plan (unlike Automatic Pix, which requires a CNPJ).

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-07-03 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/067b39f242f01c59725b5d0be800cb7c/FVP-Payments-API-v5.0.0-Scheduling-Restricted-FVP.xlsx)

---

[↑ Restricted FVP](FVP/EN/Manual/Scheduled) · [◀ Credit Portability](FVP/EN/Manual/Scheduled/Credit-Portability) · [Client Management ▶](FVP/EN/Manual/Scheduled/Client-Management)


---

*Conteúdo baixado em 16/09/2026, 15:37:48*
