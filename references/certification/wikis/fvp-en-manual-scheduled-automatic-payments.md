# Automatic Payments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Automatic-Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Automatic-Payments)
**Slug:** `FVP/EN/Manual/Scheduled/Automatic-Payments`

---

---
title: Automatic Payments
---

[← Manual FVP / Restricted FVP](FVP/EN/Manual/Scheduled)

# Manual FVP - Automatic Payments

This page gathers the manual FVP plans for Automatic Payments. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Automatic Payments API - v2.2.0 - Automatic Pix Scheduling - Restricted FVP
Technical name: `fvp-automatic-pix-payments_restricted_test-plan-v2-2`

Validates the full cycle of automatic payments via recurring Pix (sweeping scheduling) on the Automatic Payments API v2.2.0, covering recurring consent creation and authorisation, payment scheduling, status polling and retry flows, both with failure and rescheduling and with a successful retry.

### Before you start
**Account balance**
- D+0: exactly R$ 0.00 (mandatory)
- D+1: exactly R$ 0.00 (mandatory)
- D+2: exactly R$ 0.00 (mandatory)
- D+3: minimum R$ 1.00 (mandatory)
- Execution window: 21:00 to 23:59 BRT on the scheduled days
- must be a CNPJ (Automatic Pix does not accept a CPF as the creditor account identifier)
- "D+N" refers to N calendar days after Module 1 runs, not business days.
- The follow-up tests are only scheduled if Module 1 completes successfully; an error at the start does not trigger the subsequent runs.
- client_id, consent_id, payment_id and refresh_token are persisted automatically by the suite between runs.

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
| automatic-payments_api_automatic-pix-scheduling_1-2_test-module_v2-2 | Creates and authorises the recurring consent and schedules a payment without retry; after polling, the payment reaches Scheduled (SCHD). |
| automatic-payments_api_automatic-pix-scheduling_2-2_test-module_v2-2 | Next-day verification: confirms the scheduled no-retry payment settled (ACSC). |
| automatic-payments_api_automatic-pix-scheduling-retry_1-3_test-module_v2-2 | Creates and authorises the consent with retry enabled and schedules the payment (SCHD) for later verification. |
| automatic-payments_api_automatic-pix-scheduling-retry_2-3_test-module_v2-2 | The original payment is rejected (RJCT) and a retry is scheduled (SCHD) for the next day. |
| automatic-payments_api_automatic-pix-scheduling-retry_3-3_test-module_v2-2 | Confirms that, after the original payment is rejected, the retry does not stay scheduled (status other than SCHD). |
| automatic-payments_api_automatic-pix-scheduling-successful-retry_1-3_test-module_v2-2 | Creates and authorises the consent with retry enabled and schedules the payment (SCHD), setting up the successful-retry scenario. |
| automatic-payments_api_automatic-pix-scheduling-successful-retry_2-3_test-module_v2-2 | The original payment is rejected (RJCT) and a new retry payment is issued and scheduled (SCHD). |
| automatic-payments_api_automatic-pix-scheduling-successful-retry_3-3_test-module_v2-2 | Confirms the retry payment settled successfully (ACSC) after the original was rejected. |

### Notes
- The retry modules (2-3 and 3-3 of each sequence) must run between 21:00 and 23:59 BRT on the scheduled days; outside that window the suite interrupts the test.
- Modules 2 and 3 of each retry sequence are scheduled automatically by the Conformance Suite, using the saved data (consentID, paymentID, clientId, refresh_token) from the previous module. Do not run them manually.
- Keep the participant server online and responsive between 21:00 and 23:59 BRT on the scheduled days (D+2 and D+3 of the retry sequence).

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2025-10-29 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/7233205e3bfbb928cd0020bccbbf49bf/FVP-Automatic-Payments-API-v2.2.0-Automatic-Pix-Scheduling-Restricted-FVP.xlsx)

---

[↑ Restricted FVP](FVP/EN/Manual/Scheduled) · [◀ Enrollments](FVP/EN/Manual/Scheduled/Enrollments) · [Credit Portability ▶](FVP/EN/Manual/Scheduled/Credit-Portability)


---

*Conteúdo baixado em 16/09/2026, 15:37:45*
