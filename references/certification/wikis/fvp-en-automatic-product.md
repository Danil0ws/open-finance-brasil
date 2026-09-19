# Product

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic/Product](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic/Product)
**Slug:** `FVP/EN/Automatic/Product`

---

---
title: Product tests
---

[← Automatic FVP](FVP/EN/Automatic)

# Automatic FVP - Product tests

This category gathers the per-API functional modules that run through the flow up to consent authorization and stop there, which is why they require no user interaction. The list below describes each module and what it verifies.

## Modules and what to expect
| Test module | What it verifies |
| --- | --- |
| fvp-payments-consents-server-certificate-v2 | Validates that the server endpoint certificates follow the Brazilian standard (RFC5246-7.4.2 chain, OPF CA) on the token, registration and up to 12 functional endpoints. |
| fvp_payments_consents_api_bad-logged_test-module_v5 | Uses a freshly registered client to create a payment consent with a well-formed dummy payload; expects 201 and validates the JWT signature. |
| fvp_consents_api_bad-logged_test-module_v3-3-1 | Uses a freshly registered client to create a data consent with a well-formed dummy payload; expects 201 and validates the response. |
| fvp-payments_api_pixscheduling-dates-unhappy_test-module_v5 | Five negative date scenarios on the payment consent (date and schedule together, today, past, far future, no date); expects 422 (DATA_PAGAMENTO_INVALIDA / PARAMETRO_NAO_INFORMADO). |
| fvp-payments_api_recurring-payments-consent-limit_test-module_v5 | Checks that recurring-payment consents breaching the limit rules (dates outside the window, quantity above the allowed) are rejected with 422. |
| fvp-payments_api_recurring-payments-wrong-custom-quantity_test-module_v5 | Checks that a custom recurring consent with fewer payments than the minimum allowed is rejected with 422 PARAMETRO_INVALIDO. |
| fvp-payments_api_dict_test-module_v5 | Checks the error when localInstrument is DICT and a QR Code is sent; expects 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp-payments_api_manu-fail_test-module_v5 | Checks the error when localInstrument is MANU and a QR Code or proxy is sent; expects 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp-payments_api_qres-code-enforcement_test-module_v5 | Checks that a QR Code is required when localInstrument is QRES; without the qrcode, expects 422 PARAMETRO_NAO_INFORMADO. |
| fvp-payments_api_force-check-signature_test-module_v5 | Checks that a consent request with an invalid signature is rejected with 400 (and that a valid signature returns 201). |
| fvp-payments_api_consents_negative_test-module_v5 | Five inconsistent scenarios on the payment consent (invalid payment type, person type, currency, date and x-fapi-interaction-id); expects 400/422 PARAMETRO_INVALIDO. |
| fvp-payments_api_json-accept-header-jwt-returned_test-module_v5 | Checks that, when a JSON Accept header is sent on the consent GET, the server returns 200 (with a JWT) or 406. |
| fvp-payments_api_consent-purpose-validation-unhappy-path-invalid-combination_test-module_v5 | Checks that the consent is rejected (422 PROPOSITO_INVALIDO) when the payment purpose is incompatible with the given date or schedule. |
| fvp-consents_api_extension-invalid-status_test-module_v3-3-1 | Checks that a consent cannot be extended while in AWAITING_AUTHORISATION; the extension call returns 401 or 403. |
| fvp-consents_api_negative_test-module_v3-3-1 | Various negative permission-combination and date scenarios on the data consent; expects 422 (COMBINACAO_PERMISSOES_INCORRETA, DATA_EXPIRACAO_INVALIDA) or 400. |
| fvp-consents_api_bad-consents_test-module_v3-3-1 | Checks that incompatible consents are rejected: personal and business permissions together (422 PERMISSAO_PF_PJ_EM_CONJUNTO) and a missing or invalid x-fapi-interaction-id (400). |
| fvp-consents_api_permission-groups_test-module_v3-3-1 | Checks that the consent API accepts every valid permission group, returning 201 with the matching permissions or 422 SEM_PERMISSOES_FUNCIONAIS_RESTANTES when the server does not support the group. |
| fvp-enrollments_api_invalid-parameters_test-module_v2-2 | Checks that an enrollment with invalid parameters is rejected: wrong header or signature (400) and missing or invalid fields (422 PARAMETRO_NAO_INFORMADO / PARAMETRO_INVALIDO / PERMISSOES_INVALIDAS). |
| fvp_dcr_automatic-payments_api_automatic-pix-invalid-creditor_open_test-module_v2-2 | Checks that an Automatic Pix consent with invalid creditor data (two business accounts, or one personal) is rejected with 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp_dcr_automatic-payments_api_automatic-pix-invalid-parameters_open_test-module_v2-2 | Checks that an Automatic Pix consent with invalid fields (fixedAmount as text, first payment date in the past) is rejected with 422 (PARAMETRO_INVALIDO / DATA_PAGAMENTO_INVALIDA). |
| fvp_dcr_automatic-payments_api_automatic-pix-negative-consent_open_test-module_v2-2 | Checks that an Automatic Pix consent with values breaking the business rules (inconsistent fixed/variable limits) is rejected with 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp_dcr_automatic-payments_api_negative-consents_test-module_v2-2 | Checks the validations on the recurring-consent POST: missing sweeping field, inconsistent dates and a missing or invalid x-fapi-interaction-id; expects 422/400. |
| fvp_dcr_automatic-payments_api_rejected-consent_test-module_v2-2 | Checks that a recurring consent becomes REJECTED when the PATCH is called before approval, with rejectedBy USUARIO, rejectedFrom INICIADORA and reason REJEITADO_USUARIO. |
| fvp_dcr_automatic-payments_api_sweeping-accounts-invalid-creditor_test-module_v2-2 | Checks that a sweeping consent with an invalid creditor account (different from the logged user) is rejected with 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp_credit-portability_api_invalid_token_test-module_v1 | Checks that the Credit Portability POST /portabilities endpoint is responsive in the Directory and rejects a client_credentials token with 401 or 403. |
| fvp-optimised-journey_invalid-permissions_test-module-v1 | Checks the failure when an optimised-journey consent is created with an incorrect permission combination; expects 422 COMBINACAO_PERMISSOES_INCORRETA. |

[Download this category spreadsheet](uploads/3740a0139b5f3c92944ea40db49aa197/FVP-Product-tests.xlsx)

---

[↑ Automatic FVP](FVP/EN/Automatic) · [◀ Directory tests](FVP/EN/Automatic/Directory) · [Manual FVP ▶](FVP/EN/Manual)


---

*Conteúdo baixado em 16/09/2026, 15:37:36*
