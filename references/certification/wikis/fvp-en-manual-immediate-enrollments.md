# Enrollments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Enrollments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Enrollments)
**Slug:** `FVP/EN/Manual/Immediate/Enrollments`

---

---
title: Enrollments
---

[← Manual FVP / Open FVP](FVP/EN/Manual/Immediate)

# Manual FVP - Enrollments

This page gathers the manual FVP plans for Enrollments. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Enrollments API - v2.2.0 - Automatic Payments - Open FVP
Technical name: `fvp-no-redirect-automatic-pix-payments_open_test-plan-v2-2`

Validates automatic Pix payments on the Enrollments API v2.2.0 (Open FVP), covering device enrollment, recurring consent authorisation, first-payment execution, scheduling of subsequent payments and negative scenarios for the amount limit and an unsupported product.

### Before you start
**Account balance**
- D+0: minimum R$ 1.50 (mandatory) - Covers the plan's two payments: R$ 1.00 (first) and R$ 0.50 (second, scheduled).
- Execution window: Immediate plan: no restricted time window. Run at any time and keep the participant server online throughout the run.
- The creditor account CPF/CNPJ must be a CNPJ for Automatic Pix.
- loggedUserIdentification is always a CPF (11 digits), even for a PJ debtor.
- For a PJ debtor, fill businessEntityIdentification and brazilCnpj (14 digits). For a PF debtor, fill only brazilCpf (11 digits). Do not send brazilCpf and brazilCnpj at the same time.

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
| fvp-enrollments_automatic-payments_authorised-executed-scheduled-successfully_v2-2 | Core no-redirect automatic-payment flow: the first payment settles (ACSC) and the second is scheduled (SCHD). |
| fvp-enrollments_api_automatic-payment_enrollment-limits_negative_test-module_v2-2 | A payment above the enrollment's per-transaction limit is rejected (LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO). |
| fvp-enrollments_api_automatic-payments_enrollment-limits_v2-2 | Executes the first payment at the per-transaction limit (settled, ACSC) and schedules the next payment (SCHD). |
| fvp-enrollments_automatic-payments_sweeping-consent-not-authorised_v2-2 | A consent carrying sweeping-accounts data is not authorised in the no-redirect flow (422 PARAMETRO_INVALIDO; rejection FLUXO_NAO_SUPORTADO_PRODUTO). |

### Notes
- In the authorised-executed-scheduled-successfully module, during the redirect step you must select an indefinite term for the test to succeed.
- This is an immediate plan (not scheduled): the modules run in a single session, with no automatically scheduled modules. Do not confuse it with the No Redirect Automatic Pix Payments Scheduling plan (long-running, with an automatic Module 2).
- For Automatic Pix, the creditor account CPF/CNPJ (Creditor Account CPF/CNPJ) must be a CNPJ.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-01-29 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/0b56b7b2771ef7fa92b9aa219d270885/FVP-Enrollments-API-v2.2.0-Automatic-Payments-Open-FVP.xlsx)

## ⚙️ 2) Enrollments API - v2.2.0 - Payments - Open FVP
Technical name: `fvp-no_redirect_payments_open_test-plan-v2-2`

Validates the No Redirect payment journey (JSR) via the Enrollments API v2.2.0, including the full FIDO flow (enrollment, sign-options, authorisation and payment), error scenarios on challenge, origin, public key, rp_id and invalid fields, and payment attempts with the enrollment in an invalid state.

### Before you start
- Execution window: Immediate plan: no time window. Run at any time and keep the server online during the run.
- The creditor account may be a CPF or a CNPJ.
- A balance sufficient for the payments-core module's R$ 0.50 payment is recommended in the debtor account.
- loggedUserIdentification is always a CPF (11 digits), regardless of whether the debtor is PF or PJ.
- For a PJ debtor, businessEntityIdentification and brazilCnpj must be a CNPJ (14 digits).
- The contractDebtorName and contractDebtorIdentification fields are not required in this plan; they are exclusive to the Automatic Payments plans.
- The institution must have a Software Statement registered in the Directory with the software_origin_uris used in the plan.

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
| fvp-enrollments-api-pre-flight-test-v2 | Checks the server Directory registration for the enrollments (v2), payments-consents (v4.0.0) and payments-pix (v4.0.0) families. |
| fvp-enrollments_api_payments-core_open_test-module_v2-2 | Core FIDO flow: creates the enrollment, the consent and the sign-options, and completes the payment through to settlement (ACSC). |
| fvp-enrollments_api_invalid-challenge_open_test-module_v2-2 | FIDO registration with an invalid challenge is refused (422 CHALLENGE_INVALIDO) and the enrollment is rejected for FIDO failure. |
| fvp-enrollments_api_invalid-origin_open_test-module_v2-2 | FIDO registration with an invalid origin is refused (422 ORIGEM_FIDO_INVALIDA) and the enrollment is rejected for FIDO failure. |
| fvp-enrollments_api_invalid-public-key_open_test-module_v2-2 | FIDO registration with an invalid public key is refused (422 PUBLIC_KEY_INVALIDA) and the enrollment is rejected. |
| fvp-enrollments_api_invalid-rpid_open_test-module_v2-2 | FIDO registration with an invalid rp_id is refused (422 RP_INVALIDA) and the enrollment is rejected for FIDO failure. |
| fvp-enrollments_api_invalid-status-sign-options_open_test-module_v2-2 | A sign-options call with the enrollment in an invalid status is refused (422 STATUS_VINCULO_INVALIDO). |
| fvp-enrollments_api_payments-pre-enrollment_open_test-module_v2-2 | Authorising the consent before the enrollment is complete is refused (422 STATUS_VINCULO_INVALIDO) and the consent is rejected. |
| fvp-enrollments_api_payments-unmatching-fields_open_test-module_v2-2 | Payments with mismatched fields (authorisationFlow HYBRID_FLOW or a missing consentId) are refused or rejected (DETALHE_PAGAMENTO_INVALIDO). |
| fvp-enrollments_api_payments-keys-swap_open_test-module_v2-2 | A consent signed with a key different from the one registered in the enrollment is refused (422 RISCO) and rejected. |

### Notes
- This is an immediate plan (no scheduled tests): all modules run in the same manual session, with no specific time window.
- Only the payments-core module produces a successful payment (R$ 0.50). The error modules (invalid-challenge, invalid-origin, invalid-public-key, invalid-rpid, invalid-status-sign-options, payments-keys-swap) do not run a payment; payments-pre-enrollment and payments-unmatching-fields attempt a payment but are not expected to succeed.
- For a PJ debtor, fill businessEntityIdentification and brazilCnpj. For a PF debtor, fill brazilCpf. Never fill PF and PJ at the same time; the run may be rejected.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-01-28 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/5186918b38ac15a8909d7f8e833b4ccc/FVP-Enrollments-API-v2.2.0-Payments-Open-FVP.xlsx)

---

[↑ Open FVP](FVP/EN/Manual/Immediate) · [◀ Optimised Journey](FVP/EN/Manual/Immediate/Optimised-Journey) · [Automatic Payments ▶](FVP/EN/Manual/Immediate/Automatic-Payments)


---

*Conteúdo baixado em 16/09/2026, 15:37:41*
