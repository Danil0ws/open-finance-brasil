# Phase 1 4A Open Data

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-1-4A-Open-Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-1-4A-Open-Data)
**Slug:** `Phase-1-4A-Open-Data`

---

---
title: Phase 1 and 4A - Open Data
---

# Overview

Open Data is the part of Open Finance Brasil that needs no consent and no customer:
the product and channel information every institution publishes openly.

It is the largest set of plans in the suite, and most carry a single module,
because each one validates the structure of one published endpoint. They fall into
four groups: the personal and business product APIs, the channel APIs, the common
APIs for status and outages, and the opendata APIs for insurance, pension,
capitalization, acquiring services and exchange.

# Certification

Open Data certifies differently from the other phases. There is no Service Desk
submission. Once a plan passes, you register an API Family in the Participant
Directory with the endpoint that will be published; an automated run follows, and a
pass publishes the API with an active certification.

# Before you start

- The endpoints under test have to be reachable without a consent and without a token. These plans call them as any public consumer would.
- Register the endpoint in the Participant Directory before expecting the automated run that certifies it.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Admin API - v2.0.1 - Conformance Suite | admin_test-plan | 1 | 29/01/2024 |
| Business Accounts API - v1.1.0 - Conformance Suite | business-accounts_test-plan_v1n1 | 1 | 24/04/2026 |
| Business Credit Card API - v1.1.0 - Conformance Suite | business-credit_card_test-plan_v1n1 | 1 | 24/04/2026 |
| Business Financings API - v1.1.0 - Conformance Suite | business-financings_test-plan_v1n1 | 1 | 24/04/2026 |
| Business Invoice Financings API - v1.1.0 - Conformance Suite | business-invoice_financings_test-plan_v1n1 | 1 | 24/04/2026 |
| Business Loans API - v1.1.0 - Conformance Suite | business-loans_test-plan_v1n1 | 1 | 24/04/2026 |
| Channels - Banking Agents API - v2.1.0 - Conformance Suite | channels-banking-agents_test-plan_v2n1 | 1 | 24/04/2026 |
| Channels - Branches API - v2.1.0 - Conformance Suite | channels-branches_test-plan_v2n1 | 1 | 24/04/2026 |
| Channels - Electronic Channels API - v2.1.0 - Conformance Suite | channels-electronic-channels_test-plan_v2n1 | 1 | 24/04/2026 |
| Channels - Phone Channels API - v2.1.0 - Conformance Suite | channels-phone-channels_test-plan_v2n1 | 1 | 24/04/2026 |
| Channels - Shared Automated Teller Machines API - v2.1.0 - Conformance Suite | channels-shared-automated-teller-machines_test-plan_v2n1 | 1 | 24/04/2026 |
| Common - Outages API - v2.0.1 - Conformance Suite | common-outages_test-plan | 1 | 04/01/2022 |
| Common - Status API - v2.0.1 - Conformance Suite | common-status_test-plan | 1 | 04/01/2022 |
| Acquiring Services - Business API - v1.1.0 - Conformance Suite | opendata-acquiring-services-business_test-plan_v1n1 | 1 | 24/04/2026 |
| Acquiring Services - Personal API - v1.1.0 - Conformance Suite | opendata-acquiring-services-personal_test-plan_v1n1 | 1 | 24/04/2026 |
| Capitalization Bonds API - v2.1.0 - Conformance Suite | opendata-capitalization-bonds_test-plan_v2n1 | 1 | 05/05/2026 |
| Functional Tests for Exchange - Online Rate API - Based on Swagger version: 1.1.0 | opendata-exchange-online-rate_test-plan_v1n1 | 1 | 24/04/2026 |
| Functional Tests for Exchange - Vet Value API - Based on Swagger version: 1.1.0 | opendata-exchange-vet-value_test-plan_v1n1 | 1 | 24/04/2026 |
| Insurance - Personal Insurance API - v2.1.0 - Conformance Suite | opendata-insurance-personal_test-plan_v2n1 | 1 | 24/04/2026 |
| Functional Tests for Investments - Bank Fixed Income API - Based on Swagger version: 1.1.0 | opendata-investments-bank-fixed-income_test-plan_v1n1 | 1 | 24/04/2026 |
| Functional Tests for Investments - Credit Fixed Incomes API- Based on Swagger version: 1.1.0 | opendata-investments-credit-fixed-income_test-plan_v1n1 | 1 | 24/04/2026 |
| Functional Tests for Investments - Funds API - Based on Swagger version: 1.1.0 | opendata-investments-funds_test-plan_v1n1 | 1 | 24/04/2026 |
| Functional Tests for Investments - Treasure Titles API - Based on Swagger version: 1.1.0 | opendata-investments-treasure-titles_test-plan_v1n1 | 1 | 24/04/2026 |
| Functional Tests for Investments - Variable Incomes API - Based on Swagger version: 1.1.0 | opendata-investments-variable-incomes_test-plan_v1n1 | 1 | 24/04/2026 |
| Pension - Risk Coverages - v2.1.0 - Conformance Suite | opendata-pension-risk-coverages_test-plan_v2n1 | 1 | 05/05/2026 |
| Pension - Survival Coverages - v2.1.0 - Conformance Suite | opendata-pension-survival-coverages_test-plan_v2n1 | 1 | 05/05/2026 |
| Personal Accounts API - v1.1.0 - Conformance Suite | personal-accounts_test-plan_v1n1 | 1 | 24/04/2026 |
| Personal Credit Card API - v1.1.0 - Conformance Suite | personal-credit_card_test-plan_v1n1 | 1 | 24/04/2026 |
| Personal Financings API - v1.1.0 - Conformance Suite | personal-financings_test-plan_v1n1 | 1 | 24/04/2026 |
| Personal Invoice Financings API - v1.1.0 - Conformance Suite | personal-invoice_financings_test-plan_v1n1 | 1 | 24/04/2026 |
| Personal Loans API - v1.1.0 - Conformance Suite | personal-loans_test-plan_v1n1 | 1 | 24/04/2026 |
| Unarranged Account Business Overdraft API - v1.1.0 - Conformance Suite | unarranged_account_business_overdraft_test-plan_v1n1 | 1 | 24/04/2026 |
| Unarranged Account Personal Overdraft API - v1.1.0 - Conformance Suite | unarranged_account_personal_overdraft_test-plan_v1n1 | 1 | 24/04/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Admin API - v2.0.1 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Business Accounts API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Business Credit Card API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Business Financings API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Business Invoice Financings API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Business Loans API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Channels - Banking Agents API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Channels - Branches API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Channels - Electronic Channels API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Channels - Phone Channels API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Channels - Shared Automated Teller Machines API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Common - Outages API - v2.0.1 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Common - Status API - v2.0.1 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Acquiring Services - Business API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Acquiring Services - Personal API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Capitalization Bonds API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Exchange - Online Rate API - Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Exchange - Vet Value API - Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Insurance - Personal Insurance API - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Investments - Bank Fixed Income API - Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Investments - Credit Fixed Incomes API- Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Investments - Funds API - Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Investments - Treasure Titles API - Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Investments - Variable Incomes API - Based on Swagger version: 1.1.0 - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Pension - Risk Coverages - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Pension - Survival Coverages - v2.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Personal Accounts API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Personal Credit Card API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Personal Financings API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Personal Invoice Financings API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Personal Loans API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Unarranged Account Business Overdraft API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Unarranged Account Personal Overdraft API - v1.1.0 - Conformance Suite - 2 fields</summary>

| Section | Fields |
|---|---|
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

# Test modules

| Test module / Plan | What it does |
|---|---|
| admin_api_core_test-module<br>*admin_test-plan* | Validates the admin API resources, the metrics an institution publishes about the availability and use of its Open Finance endpoints. |
| business-accounts_api_structural_test-module_v1n1<br>*business-accounts_test-plan_v1n1* | Checks the business accounts endpoint, listing the current, savings and prepaid accounts offered to companies with their fees and packages. |
| business-credit_card_api_structural_test-module_v1n1<br>*business-credit_card_test-plan_v1n1* | Validates the business credit cards endpoint, covering each card's network, annual fee, interest rates and other charges for companies. |
| business-financings_api_structural_test-module_v1n1<br>*business-financings_test-plan_v1n1* | Reads the business financings endpoint and checks each financing product for companies carries its rates, fees and contract terms. |
| business-invoice_financings_api_structural_test-module_v1n1<br>*business-invoice_financings_test-plan_v1n1* | Validates the business invoice financings endpoint, the discounted receivables products offered to companies with their rates and fees. |
| business-loans_api_structural_test-module_v1n1<br>*business-loans_test-plan_v1n1* | Checks the business loans endpoint, listing every loan product for companies with its interest rates, fees and repayment terms. |
| channels-banking-agents_api_structural_test-module_v2n1<br>*channels-banking-agents_test-plan_v2n1* | Checks the public banking agents endpoint returns each correspondent outlet with its address, opening hours and the services it provides. |
| channels-branches_api_structural_test-module_v2n1<br>*channels-branches_test-plan_v2n1* | Validates the branches endpoint, covering each branch's address, telephone numbers, opening hours and the services offered there. |
| channels-electronic-channels_api_structural_test-module_v2n1<br>*channels-electronic-channels_test-plan_v2n1* | Checks the electronic channels endpoint describes the internet, mobile and other digital channels and the services available on each. |
| channels-phone-channels_api_structural_test-module_v2n1<br>*channels-phone-channels_test-plan_v2n1* | Reads the phone channels endpoint and confirms every telephone service channel and its available services follow the specification. |
| channels-shared-automated-teller-machines_api_structural_test-module_v2n1<br>*channels-shared-automated-teller-machines_test-plan_v2n1* | Checks the shared automated teller machines endpoint returns each shared ATM's location, availability and services in the expected shape. |
| common-outages_api_structural_test-module<br>*common-outages_test-plan* | Validates the common outages endpoint, where an institution publishes the scheduled unavailability windows of its Open Finance APIs. |
| common-status_api_structural_test-module<br>*common-status_test-plan* | Checks the common status endpoint, the availability an institution publishes for each of its Open Finance APIs in real time. |
| opendata-acquiring-services-business_api_structural_test-module_v1n1<br>*opendata-acquiring-services-business_test-plan_v1n1* | Validates the business acquiring services endpoint, the card acquiring offers for companies with their settlement terms and charges. |
| opendata-acquiring-services-personal_api_structural_test-module_v1n1<br>*opendata-acquiring-services-personal_test-plan_v1n1* | Checks the personal acquiring services endpoint, the card acquiring offers for individual sellers with their settlement terms and charges. |
| opendata-capitalization-bonds_api_structural_test-module_v2n1<br>*opendata-capitalization-bonds_test-plan_v2n1* | Checks the capitalization bonds endpoint, covering each bond's modality, contributions, redemption rules and prize draws. |
| opendata-exchange-online-rate_api_structural_test-module_v1n1<br>*opendata-exchange-online-rate_test-plan_v1n1* | Validates the exchange online rate endpoint, the purchase and sale rates an institution publishes per currency and operation type. |
| opendata-exchange-vet-value_api_structural_test-module_v1n1<br>*opendata-exchange-vet-value_test-plan_v1n1* | Checks the exchange VET value endpoint, the total effective value published for foreign exchange operations by currency and value band. |
| opendata-insurance-personal_api_structural_test-module_v2n1<br>*opendata-insurance-personal_test-plan_v2n1* | Checks the personal insurance endpoint, covering the insurance products sold to individuals with their coverages, terms and charges. |
| opendata-investments-bank-fixed-income_api_structural_test-module_v1n1<br>*opendata-investments-bank-fixed-income_test-plan_v1n1* | Validates the bank fixed income endpoint, covering CDB, RDB, LCI and LCA offers with their indexes, yields and minimum investment. |
| opendata-investments-credit-fixed-income_api_structural_test-module_v1n1<br>*opendata-investments-credit-fixed-income_test-plan_v1n1* | Checks the credit fixed income endpoint, covering debentures, CRI and CRA offers with their indexes, yields and investment conditions. |
| opendata-investments-funds_api_structural_test-module_v1n1<br>*opendata-investments-funds_test-plan_v1n1* | Checks the investment funds endpoint, covering each fund's class, manager, charges and minimum application as published in open data. |
| opendata-investments-treasure-titles_api_structural_test-module_v1n1<br>*opendata-investments-treasure-titles_test-plan_v1n1* | Validates the treasury titles endpoint, the Tesouro Direto securities an institution distributes with their yields and custody fees. |
| opendata-investments-variable-incomes_api_structural_test-module_v1n1<br>*opendata-investments-variable-incomes_test-plan_v1n1* | Checks the variable income endpoint, covering the shares, BDRs and other variable income products offered with their trading charges. |
| opendata-pension-risk-coverages_api_structural_test-module_v2n1<br>*opendata-pension-risk-coverages_test-plan_v2n1* | Checks the pension risk coverages endpoint, covering the death and disability cover sold with a pension plan and its conditions. |
| opendata-pension-survival-coverages_api_structural_test-module_v2n1<br>*opendata-pension-survival-coverages_test-plan_v2n1* | Validates the pension survival coverages endpoint, covering PGBL and VGBL accumulation plans with their charges and income options. |
| personal-accounts_api_structural_test-module_v1n1<br>*personal-accounts_test-plan_v1n1* | Validates the personal accounts endpoint, with the current, savings and prepaid accounts sold to individuals and the fees charged on each. |
| personal-credit_card_api_structural_test-module_v1n1<br>*personal-credit_card_test-plan_v1n1* | Checks the personal credit cards endpoint, covering each card's network, annual fee, interest rates and other charges for individuals. |
| personal-financings_api_structural_test-module_v1n1<br>*personal-financings_test-plan_v1n1* | Checks the personal financings endpoint, where financing products for individuals are published with their interest rates, fees and terms. |
| personal-invoice_financings_api_structural_test-module_v1n1<br>*personal-invoice_financings_test-plan_v1n1* | Checks the personal invoice financings endpoint, the discounted receivables products offered to individuals with their rates and fees. |
| personal-loans_api_structural_test-module_v1n1<br>*personal-loans_test-plan_v1n1* | Validates the personal loans endpoint, listing every loan product for individuals with its interest rates, fees and repayment terms. |
| unarranged_account_business_overdraft_api_structural_test-module_v1n1<br>*unarranged_account_business_overdraft_test-plan_v1n1* | Checks the unarranged overdraft endpoint for companies, covering the rates and charges applied when a business account goes overdrawn. |
| unarranged_account_personal_overdraft_api_structural_test-module_v1n1<br>*unarranged_account_personal_overdraft_test-plan_v1n1* | Validates the unarranged overdraft endpoint for individuals, covering the rates and charges applied when a personal account goes overdrawn. |

# Spreadsheet

[CS-Phase-1-and-4A-Open-Data.xlsx](uploads/e9ec59d8a8daf2d5dbadee16f29e5a20/CS-Phase-1-and-4A-Open-Data.xlsx)

# Change history

<details>
<summary>2026 - 3 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 05/05/2026 | Capitalization bonds and the two pension coverage plans were released. | No |  |
| 24/04/2026 | Twenty-seven plans released together: the personal and business product APIs at v1.1.0, the five channel APIs at v2.1.0, and the opendata APIs for insurance, acquiring services and exchange. | No |  |

</details>

<details>
<summary>2024 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 29/01/2024 | The Admin API plan was released. | No |  |

</details>

<details>
<summary>2022 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 04/01/2022 | The common Status and Outages plans were released. | No |  |

</details>

# Previous versions

These versions no longer run in the suite. Their test plans were removed.

| Version | Retired | Test plans |
|---|---|---|
| Phase 4A v1 | 11/06/2026 | [Spreadsheet](uploads/3fce4cc1a5fe9627931bf178ba3276cd/4A_Tests.xlsx) |

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*33 plans, 33 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:17*
