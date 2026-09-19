# Optimised Journey

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Optimised-Journey](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Optimised-Journey)
**Slug:** `FVP/EN/Manual/Immediate/Optimised-Journey`

---

---
title: Optimised Journey
---

[← Manual FVP / Open FVP](FVP/EN/Manual/Immediate)

# Manual FVP - Optimised Journey

This page gathers the manual FVP plans for Optimised Journey. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Optimised Journey - v1.0 - Automatic Payments API - v2.2.0 - Open FVP
Technical name: `fvp-optimised-journey_automatic-payments_test-plan_v1`

Validates the Optimised Journey with automatic payments via sweeping, covering creation and authorisation of linked consents, payment execution and polling, revocation of data and payment consents, and failure scenarios in the PAR and the journey object.

### Before you start
- Execution window: Immediate plan: no time window. Keep the participant server online throughout the run.
- Must be PF, with the same ownership as whoever runs the test (sweeping tests require a creditor account belonging to the debtor's owner).
- Recommended minimum balance: R$ 2.00 in the debtor account at the start of the run. Two R$ 1.00 payments are executed (the payments-balances and revoked-consent_payments modules); the other modules do not pay.
- All Optimised Journey payments are fixed at R$ 1.00 by the FVP, even if another paymentAmount is sent in the JSON.

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
| fvp-optimised-journey_sweeping_payments-balances_test-module-v1 | Optimised journey with sweeping: runs a linked payment (settled, ACSC), confirms the balance drop and revokes the consent. |
| fvp-optimised-journey_sweeping_revoked-consent_payments_test-module-v1 | Revokes the data consent before the payment and confirms the recurring consent remains and the payment settles (ACSC). |
| fvp-optimised-journey_sweeping_revoked-recurring-consent_test-module-v1 | Revokes the recurring consent via PATCH and confirms both the recurring and the data consents are updated correctly. |
| fvp-optimised-journey_sweeping_invalid-par_test-module-v1 | A PAR without the recurringConsentId makes authorisation fail; both the data and the recurring consents are rejected. |
| fvp-optimised-journey_sweeping_invalid-request_test-module-v1 | A recurring consent without the journey object is accepted (201) but rejected at authorisation for the missing linkId. |

### Notes
- All 5 modules in this plan are immediate: there is no scheduling or asynchronous execution. Keep the participant server online throughout the run; if it becomes unavailable midway, the subsequent modules fail and the plan must be re-run from the start.
- For the sweeping tests, all creditor account data (ISPB, issuer, number, type, name, CPF/CNPJ) must belong to the same owner as whoever runs the test; do not use a third-party account.
- All Optimised Journey payments are fixed at R$ 1.00 by the FVP, even if another paymentAmount is sent in the JSON.
- Configure this plan with a PF creditor (same ownership as the debtor).

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-04-20 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/38ce1faf3ab955edec44547f566d41de/FVP-Optimised-Journey-v1.0-Automatic-Payments-API-v2.2.0-Open-FVP.xlsx)

## ⚙️ 2) Optimised Journey - v1.0 - Enrollments API - v2.2.0 - Open FVP
Technical name: `fvp-optimised-journey_no-redirect-payments_test-plan_v1`

Validates the Optimised Journey on the No Redirect journey (Enrollments API v2.2.0), covering the full FIDO enrollment cycle, payment via FIDO_FLOW, consent revocation, enrollment revocation and failure scenarios from an invalid request.

### Before you start
- Execution window: Immediate plan: no time window. Run at any time with the participant server online.
- The creditor account may be PF or PJ (both accepted in this plan).
- Recommended minimum balance: R$ 2.00 in the debtor account at the start of the run (two R$ 1.00 payments are debited: the enrollments-balances and enrollments_revoked-consent_payments modules).
- Unlike the Automatic Payments plan (which requires the same ownership), this plan accepts any creditor configuration.
- All Optimised Journey payments are fixed at R$ 1.00 by the FVP, even if another paymentAmount is sent in the JSON.

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
| brazilCpf | Required | The 'CPF' value to be used in the consent creation request. It is also used as the Logged User Identification (it replaces the former loggedUser field). |
| brazilCnpj | Optional | The 'CNPJ' value to be used in the consent creation request. It is also used as the Business Entity Identification (it replaces the former businessEntity field). |
| description | Optional | Free-text description of this run. Optional; can be left blank. |

### Modules and what to expect
| Test module | What it does |
| --- | --- |
| fvp-optimised-journey_enrollments-balances_test-module-v1 | Optimised no-redirect journey: completes the FIDO enrollment, runs a linked payment (settled, ACSC) and confirms the balance drop. |
| fvp-optimised-journey_enrollments_revoked-consent_payments_test-module-v1 | Revokes the data consent and confirms the enrollment stays authorised and the next payment settles (ACSC). |
| fvp-optimised-journey_enrollments_revoked-enrollment_test-module-v1 | Revokes the enrollment and confirms the linked data consent is rejected. |
| fvp-optimised-journey_enrollments-invalid-request_test-module-v1 | An enrollment without the journey object makes authorisation fail; the consent and the enrollment are rejected for internal security. |
| fvp-optimised-journey_enrollments-invalid_par_test-module-v1 | A PAR carrying only the consentId (no enrollmentId) makes authorisation fail; the consent and the enrollment are rejected for internal security. |

### Notes
- All modules in this plan are immediate: no scheduling or asynchronous execution. Keep the participant server online during the run; if it becomes unavailable midway, the subsequent modules fail and the plan must be re-run from the start.
- Two R$ 1.00 payments are executed in this plan: enrollments-balances and enrollments_revoked-consent_payments. The other modules do not run a payment.
- In the creditor account fields (ISPB, issuer, number, type, name, CPF/CNPJ), use the data of the account that will receive the payments; it may be PF or PJ depending on the configuration.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-04-20 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/a5f4fe0e615dbe770f6876e161e0e9e9/FVP-Optimised-Journey-v1.0-Enrollments-API-v2.2.0-Open-FVP.xlsx)

## ⚙️ 3) Optimised Journey - v1.0 - Core - Open FVP
Technical name: `fvp-optimised-journey_test-plan_v1`

Validates that the Optimised Journey (journey.isLinked=true) cannot run with the automatic Pix payments API nor with the single-payments API, confirming that the consent is rejected in both flows.

### Before you start
- Execution window: Immediate plan: no time window. Run at any time with the participant server online.
- Configure this plan with a PJ (CNPJ) creditor.
- No payment is executed (all modules are rejection flows): the debtor account balance does not matter, as long as the account exists, is active and is eligible to authorise the consent.
- All Optimised Journey payments are fixed at R$ 1.00 by the FVP, even if another paymentAmount is sent in the JSON.

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
| fvp-optimised-journey_automatic-pix_test-module-v1 | Confirms the optimised journey cannot be used with automatic Pix payments: the recurring and the data consents are both rejected. |
| fvp-optimised-journey_payments_test-module-v1 | Confirms the optimised journey cannot be used with single payments: the payment consent expires and is rejected, along with the data consent. |

### Notes
- The single-payments module instructs the suite to wait 5 minutes (sleep) before checking the payment status.
- All modules in this plan are rejection flows: no payment is debited.
- Configure this plan with a PJ (CNPJ) creditor.
- All modules are immediate: there is no scheduling or asynchronous execution; just keep the participant server online during the run.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-04-20 | Test plan created in FVP. |  |
| 2026-05-18 | Invalid permissions module moved to the Automatic FVP. | The module now runs in the automatic plan. |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/4e9b620e201e4a4085f598f3d5d9fe8a/FVP-Optimised-Journey-v1.0-Core-Open-FVP.xlsx)

---

[↑ Open FVP](FVP/EN/Manual/Immediate) · [◀ Open FVP](FVP/EN/Manual/Immediate) · [Enrollments ▶](FVP/EN/Manual/Immediate/Enrollments)


---

*Conteúdo baixado em 16/09/2026, 15:37:42*
