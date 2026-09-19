# Credit Portability

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Credit-Portability](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Credit-Portability)
**Slug:** `FVP/EN/Manual/Immediate/Credit-Portability`

---

---
title: Credit Portability
---

[← Manual FVP / Open FVP](FVP/EN/Manual/Immediate)

# Manual FVP - Credit Portability

This page gathers the manual FVP plans for Credit Portability. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Credit Portability API - v1.0.0 - Personal - Open FVP
Technical name: `fvp-credit-portability_open_test-plan-v1`

Validates the personal credit portability flow (CREDITO_PESSOAL_CLEAN) on the Credit Portability API v1, covering rejections on invalid terms, progression to the RECEIVED status and cancellation, plus the grant type, x-fapi-interaction-id and idempotency validations on the portability endpoints.

### Before you start
- Execution window: The three modules in this plan are immediate and can run at any time.
- Not applicable: credit portability (CPC) does not use creditor account fields.
- There is no account balance requirement. The prerequisite is having at least one clean personal credit contract (CREDITO_PESSOAL_CLEAN) linked to the configured CPF/CNPJ, with portability-eligibility DISPONIVEL and isEligible=TRUE.
- The authorizationServerId field is required; alias, description, publish and the discovery URLs are filled in automatically by the FVP from the authorizationServerId.

### Configuration Form Fields
| Field | Requirement | Description |
| --- | --- | --- |
| Type | Optional | Execution type for this run (optional). Leave empty to run as normal. Selecting 'Test' requires a Cycle; selecting 'Retest' requires a Cycle and an SD Ticket. These values are appended to the test description. (Options: —, Test, Retest) |
| Cycle | Optional | Cycle this run belongs to. Required when a Type (Test or Retest) is selected. |
| SD Ticket | Optional | Service Desk ticket for this run. Required when the Type is 'Retest'. |
| Authorisation Server ID | Required | Authorisation Server ID is used to find both OrganisationId and OpenIDDiscoveryDocument in the /participants endpoint. |
| brazilCpf | Required | The 'CPF' value to be used in the consent creation request. It is also used as the Logged User Identification (it replaces the former loggedUser field). |
| brazilCnpj | Optional | The 'CNPJ' value to be used in the consent creation request. It is also used as the Business Entity Identification (it replaces the former businessEntity field). |
| description | Optional | Free-text description of this run. Optional; can be left blank. |

### Modules and what to expect
| Test module | What it does |
| --- | --- |
| fvp-credit-portability_api_invalid-contract-terms_test-module_v1 | Portability proposals with terms diverging from the original contract are refused (422: CAMPO_INCONSISTENTE, PERIODICIDADE_INVALIDA, PRAZO_ACIMA_LIMITE, NAO_INFORMADO). |
| fvp-credit-portability_api_received-portability_test-module_v1 | A portability with terms matching the original contract is created (202), reaches RECEIVED and is cancelled by the customer (CANCELADO_PELO_CLIENTE). |
| fvp-credit-portability_api_invalid_grant_type_invalid_x-fapi_invalid_idempodency_test-module_v1 | Protocol error scenarios: wrong grant type (401/403), missing or invalid x-fapi-interaction-id (400) and reuse of the idempotency key with a different payload (422 ERRO_IDEMPOTENCIA). |

### Notes
- No creditor account is configured for this plan: CPC does not require Payment consent fields (ISPB, Issuer, Number, Type, Name, recipient CPF/CNPJ). Do not fill those fields.
- An account balance is not required. The prerequisite is having at least one CREDITO_PESSOAL_CLEAN contract with concurrentManagement=DISPONIVEL and isEligible=TRUE linked to the configured CPF/CNPJ.
- The three modules in this plan run manually and independently; there is no automatic scheduling between them.
- Fill only one identification field: brazilCpf (PF, 11 digits) or brazilCnpj (PJ, 14 digits). Sending both can cause the run to be rejected.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2025-10-31 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/0e619f797a91486e13e5e424258579bb/FVP-Credit-Portability-API-v1.0.0-Personal-Open-FVP.xlsx)

---

[↑ Open FVP](FVP/EN/Manual/Immediate) · [◀ Automatic Payments](FVP/EN/Manual/Immediate/Automatic-Payments) · [Customer Data ▶](FVP/EN/Manual/Immediate/Customer-Data)


---

*Conteúdo baixado em 16/09/2026, 15:37:40*
