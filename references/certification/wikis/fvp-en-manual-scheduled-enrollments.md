# Enrollments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Enrollments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Enrollments)
**Slug:** `FVP/EN/Manual/Scheduled/Enrollments`

---

---
title: Enrollments
---

[← Manual FVP / Restricted FVP](FVP/EN/Manual/Scheduled)

# Manual FVP - Enrollments

This page gathers the manual FVP plans for Enrollments. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Enrollments API - v2.2.0 - Automatic Payments Scheduling - Restricted FVP
Technical name: `fvp-no-redirect-automatic-pix-payments_restricted_test-plan-v2-2`

Validates automatic Pix payment scheduling via the No Redirect journey (JSR), covering the full flow of enrollment, recurring consent creation and authorisation, payment triggering and scheduled-status (SCHD) verification, followed by revocation of the consent and the enrollment.

### Before you start
**Account balance**
- D+0: any R$ 0.00 - A minimum balance of R$ 1.00 is recommended to start the test.
- D+1: any R$ 0.00
- D+2: minimum R$ 1.00 (mandatory)
- D+3: any R$ 0.00
- Execution window: Module 1 can run at any time. Module 2 runs automatically at 21:00 BRT on D+3.
- The creditor account CPF/CNPJ (recipient) must be a CNPJ for Automatic Pix.
- D+N refers to N calendar days after Module 1 runs.
- Maximum full-cycle duration: 3 calendar days (including non-business days).

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
| enrollments_api_automatic-payments_automatic-pix-scheduling_1-2_test-module_v2-2 | Creates the enrollment and recurring consent, authorises and schedules the payment (SCHD) for later verification. |
| enrollments_api_automatic-payments_automatic-pix-scheduling_2-2_test-module_v2-2 | Verifies the scheduled payment settled (ACSC) and revokes the consent and the enrollment (204). |

### Notes
- Module 2 is scheduled automatically by the suite for D+3 at 21:00 BRT, using the consentId, paymentId, clientId and refresh_token saved by Module 1; do not run it manually.
- Running Module 2 manually opens an incorrect ticket against the institution, with a wrong Test Manager link.
- The participant server must be online and responsive from 21:00 BRT on D+3; if it is offline during the window, Module 2 fails and the run must restart from Module 1.
- For Automatic Pix, the creditor account CPF/CNPJ (Creditor Account CPF/CNPJ) must be a CNPJ.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-01-29 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/55b4b3274be99849b38be158d8f03c95/FVP-Enrollments-API-v2.2.0-Automatic-Payments-Scheduling-Restricted-FVP.xlsx)

## ⚙️ 2) Enrollments API - v2.2.0 - Payments Scheduling - Restricted FVP
Technical name: `fvp-no_redirect_payments_restricted_test-plan-v2-2`

Validates Pix payment scheduling and settlement via the No Redirect journey (Enrollments API v2.2.0): consent creation with daily scheduling, FIDO authorisation, payments issued on D+1 and D+2, and settlement confirmation (ACSC) in a later scheduled run.

### Before you start
**Account balance**
- D+0: any - A minimum balance of R$ 2.00 is recommended to start the test.
- D+1: minimum R$ 1.00 (mandatory)
- D+2: minimum R$ 1.00 (mandatory)
- D+3: any
- Execution window: Module 1 can run at any time. Module 2 runs automatically at 05:00 BRT on D+3.
- The creditor account may be a CPF or a CNPJ.
- The consent, payment and enrollment data are persisted automatically by the suite between Modules 1 and 2.

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
| enrollments_api_payments_scheduled-pix-verification_1-2_test-module_v5 | Creates the FIDO enrollment and schedules two daily Pix payments (D+1 and D+2), which reach Scheduled (SCHD). |
| enrollments_api_payments_scheduled-pix-verification_2-2_test-module_v5 | Verifies that both scheduled payments settled (ACSC). |

### Notes
- Module 2 is scheduled automatically by the Conformance Suite after Module 1 completes successfully; do not run it directly (that opens an incorrect ticket against the institution, with a wrong Test Manager link).
- Make sure the participant server is online and responsive at the scheduled time (05:00 BRT on D+3); if it is offline, Module 2 fails.
- D+N refers to N calendar days after Module 1 runs (not business days).

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-01-29 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |
| 2026-08-21 | Both modules in the plan now validate the Payments API v5. | The module names now end in v5, and the consent and the payment are checked against version 5. |

[Download this plan spreadsheet](uploads/5c954ae2ac9d9b9da4d1b906365c406c/FVP-Enrollments-API-v2.2.0-Payments-Scheduling-Restricted-FVP.xlsx)

---

[↑ Restricted FVP](FVP/EN/Manual/Scheduled) · [◀ Restricted FVP](FVP/EN/Manual/Scheduled) · [Automatic Payments ▶](FVP/EN/Manual/Scheduled/Automatic-Payments)


---

*Conteúdo baixado em 16/09/2026, 15:37:47*
