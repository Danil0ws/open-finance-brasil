# Client Management

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Client-Management](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled/Client-Management)
**Slug:** `FVP/EN/Manual/Scheduled/Client-Management`

---

---
title: Client Management
---

[← Manual FVP / Restricted FVP](FVP/EN/Manual/Scheduled)

# Manual FVP - Client Management

This page gathers the manual FVP plans for Client Management. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Manual Client Deletion - Restricted FVP
Technical name: `fvp-manual-client-deletion_test-plan-v1`

Validates the deletion of the pre-registered clients (payments and credit portability) from an authorisation server, removing the client through the Client Management endpoint (DELETE) and clearing the record from the database.

### Configuration Form Fields
| Field | Requirement | Description |
| --- | --- | --- |
| Type | Optional | Execution type for this run (optional). Leave empty to run as normal. Selecting 'Test' requires a Cycle; selecting 'Retest' requires a Cycle and an SD Ticket. These values are appended to the test description. (Options: —, Test, Retest) |
| Cycle | Optional | Cycle this run belongs to. Required when a Type (Test or Retest) is selected. |
| SD Ticket | Optional | Service Desk ticket for this run. Required when the Type is 'Retest'. |
| Authorisation Server ID | Required | Authorisation Server ID is used to find both OrganisationId and OpenIDDiscoveryDocument in the /participants endpoint. |
| brazilCpf | Required | The 'CPF' value to be used in the consent creation request. It is also used as the Logged User Identification (it replaces the former loggedUser field). |
| description | Optional | Free-text description of this run. Optional; can be left blank. |

### Modules and what to expect
| Test module | What it does |
| --- | --- |
| manual_client_deletion_payments_test-module_v1 | Deletes the pre-registered payments client via DELETE on the Client Management endpoint (if the DCM fails, the suite raises a warning and proceeds). |
| manual_client_deletion_credit-portability_test-module_v1 | Deletes the pre-registered credit-portability client via DELETE on the Client Management endpoint (if the DCM fails, the suite raises a warning and proceeds). |

### Notes
- If the Client Management (DCM) endpoint returns an error during deletion, the suite raises a Warning but continues.

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2026-03-03 | Test plan created in FVP. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |

[Download this plan spreadsheet](uploads/cefc6bd4f661c00b0a240f18be3b210a/FVP-Manual-Client-Deletion-Restricted-FVP.xlsx)

---

[↑ Restricted FVP](FVP/EN/Manual/Scheduled) · [◀ Payments](FVP/EN/Manual/Scheduled/Payments) · [Release Notes ▶](FVP/EN/Release-Notes)


---

*Conteúdo baixado em 16/09/2026, 15:37:45*
