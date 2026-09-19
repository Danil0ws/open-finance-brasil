# Customer Data

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Customer-Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate/Customer-Data)
**Slug:** `FVP/EN/Manual/Immediate/Customer-Data`

---

---
title: Customer Data
---

[← Manual FVP / Open FVP](FVP/EN/Manual/Immediate)

# Manual FVP - Customer Data

This page gathers the manual FVP plans for Customer Data. Each section describes a plan: what it verifies, what to prepare before running it, and the fields that must be filled in.

## ⚙️ 1) Customer Data APIs - v2/v3 - Happy Path - Open FVP
Technical name: `fvp-customer-data-happy-path_open_test-plan_v3`

Validates the structural conformance of the customer data APIs (consents, resources, accounts, credit cards, financings, loans, unarranged overdraft, and personal and business registration data) in their V2/V3 versions, covering the full flow from consent creation and authorisation through to the GET calls on every endpoint registered in the Directory.

### Before you start
- Execution window: Immediate plan: no execution window, it can run at any time.
- There is no account balance requirement: the modules validate the response structure of the data APIs and no payment is initiated.
- There is no creditor account: this plan has no payment flow.
- Before running, make sure the test user (CPF provided in brazilCpf) has at least one active account for each product under test (Accounts, Credit Cards, Loans, Financings, Invoice Financings, Unarranged Overdraft, Customer Personal/Business).
- The Resources module may require unavailable resources to be configured manually for the test user before running.

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
| fvp-preflight-check-test-v3 | Checks the pre-conditions: the token returns 200, the server is registered in the Directory and the consents v3 and resources v3 families are published. |
| fvp_consents_api_core_test-module_v3-3-1 | Creates and authorises a data consent and confirms GET Consents (200, x-v 3.3.1). |
| resources_api_core_test-module_v3-1 | Authorises the consent and validates GET Resources (200, polling until 200), closing with DELETE Consents (204). |
| accounts_api_core_consents_v3_test-module_v2-5-1 | Validates the Accounts API endpoints (list, account, balances, transactions, limits and reserved balances), all returning 200. |
| credit-cards_api_core_consents_v3-3_test-module_v2-4 | Validates the Credit Cards API endpoints (accounts, limits, transactions and bills), all returning 200. |
| financings_api_core_consents_v3-3_test-module_v2-4 | Validates the Financings API endpoints (contracts, warranties, payments and instalments), all returning 200. |
| customer-business_api_core_consents_v3-3_test-module_v2-3 | Validates the business customer-data endpoints (qualifications, identifications and financial relations) and closes the consent (204). |
| customer-personal_api_core_consents_v3-3_test-module_v2-3 | Validates the personal customer-data endpoints (qualifications, identifications and financial relations) and closes the consent (204). |
| invoice-financings_api_core_consents_v3-2_test-module_v2-4 | Validates the Invoice Financings API endpoints (contracts, warranties, payments and instalments), all returning 200. |
| loans_api_core_consents_v3-3_test-module_v2-6 | Validates the Loans API endpoints (contracts, warranties, payments and instalments), all returning 200 (x-v 2.6.0). |
| unarranged-accounts-overdraft_api_core_consents_v3-3_test-module_v2-5 | Validates the Unarranged Accounts Overdraft API endpoints (contracts, warranties, payments and instalments), all returning 200. |
| fvp-accounts_api_core_consents_all_permissions_v3-3_test-module_v2-5-1 | Creates a consent with no expiry and all permissions, validates the Accounts API endpoints (200) and closes with DELETE (204). |
| fvp-customer_data_unique_happy_path_test-module | Single customer-data flow: with one consent without expiry, runs GET on every registered API endpoint (all 200) and closes with DELETE (204). |

### Notes
- This is an immediate plan (not scheduled): all modules run in the same session, with no dependency on dates or BRT windows. There are no payments, so no minimum balance is required.
- If brazilCnpj is provided, select "Business Personal Permission" in the FVP form; otherwise use "Customer Personal Permission". Provide only one option (CPF, or CPF+CNPJ): sending both without selecting the correct profile can cause the consent to fail.
- Operational Limits checks permissions through the Consents API: if the server returns the permissions with 201, the resources are tested; if it does not, the test is skipped with a WARNING (the institution does not control those resources).

### Change history
| Date | Adjustment summary | Notes |
| --- | --- | --- |
| 2024-10-18 | Test plan created in FVP. |  |
| 2025-02-27 | Validators updated. | Consents 3.1, loans 2.4, financings 2.3, discounted credit rights 2.3 and unarranged accounts overdraft 2.4. |
| 2025-09-02 | Loans updated to 2.5. |  |
| 2025-12-02 | Consents updated to 3.3. |  |
| 2026-01-12 | Consents now require the x-v header. | In addition to the response structure, the module now checks for the x-v header with version 3.3.1. |
| 2026-01-29 | Validators updated. | Discounted credit rights 2.4, financings 2.4, resources 3.1 and unarranged accounts overdraft 2.5. |
| 2026-05-12 | Customer data updated to 2.3. | Personal and business. |
| 2026-05-26 | Loans updated to 2.6. |  |
| 2026-06-08 | Accounts 2.5 and credit cards 2.4. |  |
| 2026-07-13 | Plan documentation restructured. | A dedicated page with summary, configuration form fields, modules, warnings and change history, in Portuguese and English. |
| 2026-07-22 | Accounts updated to 2.5.1. |  |

[Download this plan spreadsheet](uploads/91dc4404d7185e822dd84e290723de8a/FVP-Customer-Data-APIs-v2-v3-Happy-Path-Open-FVP.xlsx)

---

[↑ Open FVP](FVP/EN/Manual/Immediate) · [◀ Credit Portability](FVP/EN/Manual/Immediate/Credit-Portability) · [Payments ▶](FVP/EN/Manual/Immediate/Payments)


---

*Conteúdo baixado em 16/09/2026, 15:37:40*
