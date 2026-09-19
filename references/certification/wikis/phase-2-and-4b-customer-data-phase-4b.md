# Phase 4B

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-2-and-4B-Customer-Data/Phase-4B](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-2-and-4B-Customer-Data/Phase-4B)
**Slug:** `Phase-2-and-4B-Customer-Data/Phase-4B`

---

---
title: Phase 4B
---

[← Phase 2 and 4B - Customer Data](Phase-2-and-4B-Customer-Data)

# Overview

The investment APIs: bank fixed incomes, credit fixed incomes, funds, treasure
titles, variable incomes, and exchange.

Eleven plans. Each investment API carries a core plan and a timezone plan, the
second one existing because a transaction dated locally near midnight falls on a
different day in UTC. Exchange has a single plan.

# Before you start

- Set up at least one personal or business account holding the product under test, and provide the user's CPF, or the CPF and CNPJ pair, in the test configuration.
- For each API under test, the user needs one product in AVAILABLE state and one in UNAVAILABLE state. The modules check the second case too, so both are required.
- At least 51 transactions, with one older than six months and one from the current week. A separate module needs 51 transactions all falling between D-6 and D+0.
- The transactions-current module has to run between 21:00 and 23:59 in UTC-3. It is the only module in the suite with a wall-clock window.
- For Variable Incomes, at least one of the first transactions returned has to carry the brokerNoteId.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Bank Fixed Incomes API - v1.1.0 - Conformance Suite | bank-fixed-incomes_test-plan_v1_1 | 10 | 13/02/2026 |
| Bank Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite | bank-fixed-incomes-timezone_test-plan_v1_1 | 2 | 13/02/2026 |
| Credit Fixed Incomes API - v1.1.0 - Conformance Suite | credit-fixed-incomes_test-plan_v1_1 | 10 | 13/02/2026 |
| Credit Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite | credit-fixed-incomes-timezone_test-plan_v1_1 | 2 | 13/02/2026 |
| Exchange API - v1.1.0 - Conformance Suite | exchanges_test-plan_v1-1 | 8 | 16/03/2026 |
| Funds API - v1.1.0 - Conformance Suite | funds_test-plan_v1n1 | 10 | 13/02/2026 |
| Funds API - v1.1.0 - Timezone - Conformance Suite | funds-timezone_test_plan_v1n1 | 2 | 13/03/2026 |
| Treasure Titles API - v1.1.0 - Conformance Suite | treasure-titles_test-plan_v1n1 | 10 | 13/02/2026 |
| Treasure Titles API - v1.1.0 - Timezone - Conformance Suite | treasure-titles-timezone_test_plan_v1n1 | 2 | 13/03/2026 |
| Variable Incomes API - v1.3.0 - Conformance Suite | variable-incomes_test-plan_V1-3-0 | 11 | 13/02/2026 |
| Variable Incomes API - v1.3.0 - Timezone - Conformance Suite | variable-incomes-timezone_test_plan_V1-3-0 | 2 | 13/03/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Bank Fixed Incomes API - v1.1.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.brazilCpfPaginationList<br>resource.brazilCnpjPaginationList<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Bank Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite - 15 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Credit Fixed Incomes API - v1.1.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.brazilCpfPaginationList<br>resource.brazilCnpjPaginationList<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Credit Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite - 15 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Exchange API - v1.1.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.brazilCpfPaginationList<br>resource.brazilCnpjPaginationList<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Funds API - v1.1.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.brazilCpfPaginationList<br>resource.brazilCnpjPaginationList<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Funds API - v1.1.0 - Timezone - Conformance Suite - 15 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Treasure Titles API - v1.1.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.brazilCpfPaginationList<br>resource.brazilCnpjPaginationList<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Treasure Titles API - v1.1.0 - Timezone - Conformance Suite - 15 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Variable Incomes API - v1.3.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.brazilCpfPaginationList<br>resource.brazilCnpjPaginationList<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Variable Incomes API - v1.3.0 - Timezone - Conformance Suite - 15 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Bank Fixed Incomes API - v1.1.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight-adv_test-module_v2 | Confirms the mandatory configuration fields are set and that the organisation's Consents API URI is published on the participants dump. |
| bank-fixed-incomes_api_core_test-module_v1-1 | Calls every endpoint of the Bank Fixed Incomes API and checks each response body, along with the x-v header at version 1.1.0. |
| bank-fixed-incomes_api_transactiondate_test-module_v1-1 | Confirms the Bank Fixed Incomes transactions endpoint honours fromTransactionDate and toTransactionDate, down to a single day range. |
| bank-fixed-incomes_api_resources_test-module_v1-1 | Cross-checks that every BANK_FIXED_INCOME resource marked AVAILABLE on the Resources API also appears on the investments list endpoint. |
| bank-fixed-incomes_api_wrong-permissions_test-module_v1-1 | Checks that a consent holding only the customer permission group is refused with 403 on all five Bank Fixed Incomes endpoints. |
| bank-fixed-incomes_api_operational-limits_test-module_v1-1 | Exercises the operational limits of each Bank Fixed Incomes endpoint, and confirms transactions may go beyond the limit by following the next link. |
| bank-fixed-incomes_api_pagination-transaction_test-module_v1-1 | Validates pagination on the Bank Fixed Incomes transactions endpoint, including a 422 for page-size 1001 and correct self, prev and next links. |
| bank-fixed-incomes_api_pagination-transactions-current_test-module_v1-1 | Validates pagination on the Bank Fixed Incomes transactions-current endpoint over the D-6 window, including the page-size cap and the page links. |
| bank-fixed-incomes_api_pagination-list-cond_test-module_v1-1 | Checks pagination on the Bank Fixed Incomes investments list endpoint, run only when the CPF or CNPJ for the pagination list test is configured. |
| bank-fixed-incomes_api_x-fapi_test-module_v1-1 | Rejects every Bank Fixed Incomes endpoint call with 400 when x-fapi-interaction-id is missing or malformed, and echoes a valid value back. |

</details>

<details>
<summary>Bank Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| bank-fixed-incomes_api_transactions-timezone_test-module_v1_1 | Checks the Bank Fixed Incomes transactions endpoint treats dates as UTC-3, accepting a D-365 range and refusing D-370 with 422. |
| bank-fixed-incomes_api_transactions-current-timezone_test-module_v1_1 | Checks the Bank Fixed Incomes transactions-current endpoint treats dates as UTC-3, accepting a D-6 range and refusing D-7 with 422. |

</details>

<details>
<summary>Credit Fixed Incomes API - v1.1.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight-adv_test-module_v2 | Confirms the mandatory configuration fields are set and that the organisation's Consents API URI is published on the participants dump. |
| credit-fixed-incomes_api_core_test-module_v1-1 | Calls every endpoint of the Credit Fixed Incomes API and checks each response body, along with the x-v header at version 1.1.0. |
| credit-fixed-incomes_api_transactiondate_test-module_v1_1 | Confirms the Credit Fixed Incomes transactions endpoint honours fromTransactionDate and toTransactionDate, down to a single day range. |
| credit-fixed-incomes_api_resources_test-module_v1_1 | Cross-checks that every CREDIT_FIXED_INCOME resource marked AVAILABLE on the Resources API also appears on the investments list endpoint. |
| credit-fixed-incomes_api_wrong-permissions_test-module_v1-1 | Checks that a consent holding only the customer permission group is refused with 403 on all five Credit Fixed Incomes endpoints. |
| credit-fixed-incomes_api_operational-limits_test-module_v1_1 | Exercises the operational limits of each Credit Fixed Incomes endpoint, and confirms transactions may go beyond the limit by following the next link. |
| credit-fixed-incomes_api_pagination-transaction_test-module_v1-1 | Validates pagination on the Credit Fixed Incomes transactions endpoint, including a 422 for page-size 1001 and correct self, prev and next links. |
| credit-fixed-incomes_api_pagination-transactions-current_test-module_v1-1 | Validates pagination on the Credit Fixed Incomes transactions-current endpoint over the D-6 window, including the page-size cap and the page links. |
| credit-fixed-incomes_api_pagination-list-cond_test-module_v1_1 | Checks pagination on the Credit Fixed Incomes investments list endpoint, run only when the CPF or CNPJ for the pagination list test is configured. |
| credit-fixed-incomes_api_x-fapi_test-module_v1_1 | Rejects every Credit Fixed Incomes endpoint call with 400 when x-fapi-interaction-id is missing or malformed, and echoes a valid value back. |

</details>

<details>
<summary>Credit Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| credit-fixed-incomes_api_transactions-timezone_test-module_v1_1 | Checks the Credit Fixed Incomes transactions endpoint treats dates as UTC-3, accepting a D-365 range and refusing D-370 with 422. |
| credit-fixed-incomes_api_transactions-current-timezone_test-module_v1_1 | Checks the Credit Fixed Incomes transactions-current endpoint treats dates as UTC-3, accepting a D-6 range and refusing D-7 with 422. |

</details>

<details>
<summary>Exchange API - v1.1.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight-adv_test-module_v2 | Confirms the mandatory configuration fields are set and that the organisation's Consents API URI is published on the participants dump. |
| exchange_api_core_test-module_v1-1 | Calls the operations list, operation detail and operation events endpoints of the Exchange API, checking each response body and the x-v header at 1.1.0. |
| exchange_api_resources_test-module_v1-1 | Cross-checks that every EXCHANGE resource marked AVAILABLE on the Resources API also appears on the exchange operations list endpoint. |
| exchange_api_x-fapi_test-module_v1-1 | Requires x-fapi-interaction-id on the Exchange operations endpoint, expecting 400 when it is absent or invalid, and polls for up to five minutes on a 202. |
| exchange_api_wrong-permissions_test-module_v1-1 | Checks that a consent holding only the customer permission group is refused with 403 on the Exchange operations list and operation detail endpoints. |
| exchange_api_operational-limits_test-module_v1-1 | Exercises the operational limits of each Exchange endpoint, and confirms the events endpoint may go beyond the limit by following the next link. |
| exchange_api_pagination-list-test-module_v1-1 | Checks pagination on the Exchange operations list endpoint by varying page-size and page, with at least 51 operations shared. |
| exchanges_api_pagination_events-test-module_v1-1 | Checks pagination on the Exchange operation events endpoint by varying page-size and page, with at least 51 events on the chosen operation. |

</details>

<details>
<summary>Funds API - v1.1.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight-adv_test-module_v2 | Confirms the mandatory configuration fields are set and that the organisation's Consents API URI is published on the participants dump. |
| funds_api_core_test-module_v1-1 | Calls every endpoint of the Funds API and checks each response body, along with the x-v header at version 1.1.0. |
| funds_api_transactiondate_test-module_v1n1 | Confirms the Funds transactions endpoint honours fromTransactionConversionDate and toTransactionConversionDate, down to a single day range. |
| funds_api_resources_test-module_v1n1 | Cross-checks that every FUNDS resource marked AVAILABLE on the Resources API also appears on the investments list endpoint. |
| funds_api_wrong-permissions_test-module_v1-1 | Checks that a consent holding only the customer permission group is refused with 403 on all five Funds endpoints. |
| funds_api_operational-limits_test-module_v1n1 | Exercises the operational limits of each Funds endpoint, and confirms transactions may go beyond the limit by following the next link. |
| funds_api_pagination-transaction_test-module_v1-1 | Validates pagination on the Funds transactions endpoint, including a 422 for page-size 1001 and correct self, prev and next links. |
| funds_api_pagination-transactions-current_test-module_v1-1 | Validates pagination on the Funds transactions-current endpoint over the D-6 window, including the page-size cap and the page links. |
| funds_api_pagination-list-cond_test-module_v1n1 | Checks pagination on the Funds investments list endpoint, run only when the CPF or CNPJ for the pagination list test is configured. |
| funds_api_x-fapi_test-module_v1n1 | Rejects every Funds endpoint call with 400 when x-fapi-interaction-id is missing or malformed, and echoes a valid value back. |

</details>

<details>
<summary>Funds API - v1.1.0 - Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| funds_api_transactions-timezone_test-module_v1n1 | Checks the Funds transactions endpoint treats conversion dates as UTC-3, accepting a D-365 range and refusing D-370 with 422. |
| funds_api_transactions-current-timezone_test-module_v1n1 | Checks the Funds transactions-current endpoint treats conversion dates as UTC-3, accepting a D-6 range and refusing D-7 with 422. |

</details>

<details>
<summary>Treasure Titles API - v1.1.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight-adv_test-module_v2 | Confirms the mandatory configuration fields are set and that the organisation's Consents API URI is published on the participants dump. |
| treasure-titles_api_core_test-module_v1-1 | Calls every endpoint of the Treasure Titles API and checks each response body, along with the x-v header at version 1.1.0. |
| treasure-titles_api_transactiondate_test-module_v1n1 | Confirms the Treasure Titles transactions endpoint honours fromTransactionDate and toTransactionDate, down to a single day range. |
| treasure-titles_api_resources_test-module_v1n1 | Cross-checks that every TREASURE_TITLE resource marked AVAILABLE on the Resources API also appears on the investments list endpoint. |
| treasure-titles_api_wrong-permissions_test-module_v1-1 | Checks that a consent holding only the customer permission group is refused with 403 on all five Treasure Titles endpoints. |
| treasure-title_api_operational-limits_test-module_v1n1 | Exercises the operational limits of each Treasure Titles endpoint, and confirms transactions may go beyond the limit by following the next link. |
| treasure-titles_api_pagination-transaction_test-module_v1-1 | Validates pagination on the Treasure Titles transactions endpoint, including a 422 for page-size 1001 and correct self, prev and next links. |
| treasure-titles_api_pagination-transactions-current_test-module_v1-1 | Validates pagination on the Treasure Titles transactions-current endpoint over the D-6 window, including the page-size cap and the page links. |
| treasure-titles_api_pagination-list-cond_test-module_v1n1 | Checks pagination on the Treasure Titles investments list endpoint, run only when the CPF or CNPJ for the pagination list test is configured. |
| treasure-titles_api_x-fapi_test-module_v1n1 | Rejects every Treasure Titles endpoint call with 400 when x-fapi-interaction-id is missing or malformed, and echoes a valid value back. |

</details>

<details>
<summary>Treasure Titles API - v1.1.0 - Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| treasure-titles_api_transactions-timezone_test-module_v1n1 | Checks the Treasure Titles transactions endpoint treats dates as UTC-3, accepting a D-365 range and refusing D-370 with 422. |
| treasure-title_api_transactions-current-timezone_test-module_v1n1 | Checks the Treasure Titles transactions-current endpoint treats dates as UTC-3, accepting a D-6 range and refusing D-7 with 422. |

</details>

<details>
<summary>Variable Incomes API - v1.3.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight-adv_test-module_v2 | Confirms the mandatory configuration fields are set and that the organisation's Consents API URI is published on the participants dump. |
| variable-incomes_api_core_test-module_v1-3 | Calls every endpoint of the Variable Incomes API and checks each response body, along with the x-v header at version 1.3.0. |
| variable-incomes_api_transactiondate_test-module_v1-3-0 | Confirms the Variable Incomes transactions endpoint honours fromTransactionDate and toTransactionDate, down to a single day range. |
| variable-incomes_api_resources_test-module_v1-3-0 | Cross-checks that every VARIABLE_INCOMES resource marked AVAILABLE on the Resources API also appears on the investments list endpoint. |
| variable-incomes_api_wrong-permissions_test-module_v1-3 | Checks that a consent holding only the customer permission group is refused with 403 on all five Variable Incomes endpoints. |
| variable-incomes_api_broker-note_test-module_v1-3-0 | Checks the broker note details endpoint, using a brokerNoteId taken from a Variable Incomes transaction, returns every field defined for it. |
| variable-incomes_api_operational-limits_test-module_v1-3-0 | Exercises the operational limits of each Variable Incomes endpoint, and confirms transactions may go beyond the limit by following the next link. |
| variable-incomes_api_pagination-transaction_test-module_v1-3 | Validates pagination on the Variable Incomes transactions endpoint, including a 422 for page-size 1001 and correct self, prev and next links. |
| variable-incomes_api_pagination-transactions-current_test-module_v1-3 | Validates pagination on the Variable Incomes transactions-current endpoint over the D-6 window, including the page-size cap and the page links. |
| variable-incomes_api_pagination-list-cond_test-module_v1-3-0 | Checks pagination on the Variable Incomes investments list endpoint, run only when the CPF or CNPJ for the pagination list test is configured. |
| variable-incomes_api_x-fapi_test-module_v1-3-0 | Rejects every Variable Incomes endpoint call with 400 when x-fapi-interaction-id is missing or malformed, and echoes a valid value back. |

</details>

<details>
<summary>Variable Incomes API - v1.3.0 - Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| variable-incomes_api_transactions-timezone_test-module_v1-3-0 | Checks the Variable Incomes transactions endpoint treats dates as UTC-3, accepting a D-365 range and refusing D-370 with 422. |
| variable-incomes_api_transactions-current-timezone_test-module_v1-3-0 | Checks the Variable Incomes transactions-current endpoint treats dates as UTC-3, accepting a D-6 range and refusing D-7 with 422. |

</details>

# Spreadsheet

[CS-Phase-4B.xlsx](uploads/236609bbea00c97e2bba8bddf6da7385/CS-Phase-4B.xlsx)

# Change history

<details>
<summary>2026 - 4 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 16/03/2026 | The Exchange API plan was released. | No |  |
| 13/03/2026 | Timezone plans added for funds, treasure titles and variable incomes. | No |  |
| 13/02/2026 | The five investment APIs were released: bank fixed incomes, credit fixed incomes, funds, treasure titles and variable incomes, with the timezone plans for the first two. | No |  |

</details>

<details>
<summary>2023 - 5 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 22/12/2023 | The Exchange API test plan was released. | No |  |
| 18/08/2023 | The five Investments APIs were updated to v1.0.0. | No |  |
| 21/07/2023 | The timezone test modules were moved into separate test plans. | No |  |
| 21/06/2023 | The five Investments APIs were updated to v1.0.0-rc2.0. | No |  |
| 16/06/2023 | The first five Investments API test plans were released at v1.0.0-rc1.0: bank fixed incomes, credit fixed incomes, variable incomes, funds and treasure titles. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*11 plans, 69 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:19*
