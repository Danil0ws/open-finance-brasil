# Credit Portability

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Credit-Portability](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Credit-Portability)
**Slug:** `FVP/EN/Manual/Scheduled/Credit-Portability`

---

---
title: Credit Portability
---

[← Manual FVP / Restricted FVP](FVP/EN/Manual/Scheduled)

# Manual FVP - Credit Portability

This page gathers the manual FVP plans for Credit Portability. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Credit Portability API - v1.0.0 - Personal Scheduling - Restricted FVP
Technical name: `fvp-credit-portability_restricted_test-plan-v1`

Validates the full personal credit portability flow (Credit Portability API v1.0.0) in the Restricted FVP profile, covering consent creation, portability submission, cancellation in the ACCEPTED_SETTLEMENT_IN_PROGRESS status and post-cancellation eligibility verification across multiple scheduled days.

### Before you start
- Execution window: Module 1 can run at any time. Modules 2 and 3 are scheduled automatically by the FVP: Module 2 on the next business day (D+1) at 10:10 (GMT-3) and Module 3 on the following day at 00:01 (GMT-3).
- Not applicable: credit portability (CPC) does not use creditor account fields.
- There is no account balance requirement. The prerequisite is having at least one clean personal credit contract (CREDITO_PESSOAL_CLEAN) with concurrentManagement=DISPONIVEL and isEligible=TRUE, linked to the configured CPF/CNPJ.
- Fill only one identification field: brazilCpf (PF, 11 digits) or brazilCnpj (PJ, 14 digits).
- The authorizationServerId field is required; alias, description, publish and the discovery URLs are filled in automatically by the FVP.

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
| credit-portability_api_accepted_settlement_1-3_test-module_v1 | Creates the consent, submits the portability (202) and takes it to Received (RECEIVED). |
| credit-portability_api_accepted_settlement_2-3_test-module_v1 | Follows the portability to settlement in progress (ACCEPTED_SETTLEMENT_IN_PROGRESS) and cancels it on the customer behalf (CANCELADO_PELO_CLIENTE). |
| credit-portability_api_accepted_settlement_3-3_test-module_v1 | Checks the portability eligibility (status DISPONIVEL, isEligible TRUE) and closes the consent (DELETE 204). |

### Notes
- Modules 2 and 3 are scheduled automatically by the suite (Module 2 on D+1 at 10:10 (GMT-3); Module 3 the next day at 00:01 (GMT-3)); do not run them manually.
- While the status is PENDING, Module 2 may reschedule itself to the next day.
- An account balance is not required for CPC; the participant needs a clean personal loan (CREDITO_PESSOAL_CLEAN) with concurrentManagement=DISPONIVEL and isEligible=TRUE.
- Expected maximum cycle duration: up to 5 business days (excluding weekends and holidays). If it elapses without a terminal state, the test is reported as Not Completed / Expired and requires a full re-run.
- Make sure the participant server is online and responsive on the scheduled days; if it is offline during the window, Modules 2 and 3 may fail.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2025-10-31 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/bd65cf1ed6375f8e34ca231322fa1980/FVP-Credit-Portability-API-v1.0.0-Personal-Scheduling-Restricted-FVP.xlsx)

---

[↑ Restricted FVP](FVP/EN/Manual/Scheduled) · [◀ Automatic Payments](FVP/EN/Manual/Scheduled/Automatic-Payments) · [Payments ▶](FVP/EN/Manual/Scheduled/Payments)


---

*Conteúdo baixado em 16/09/2026, 15:37:46*
