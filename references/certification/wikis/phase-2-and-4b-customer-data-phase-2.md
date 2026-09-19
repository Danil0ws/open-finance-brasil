# Phase 2

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-2-and-4B-Customer-Data/Phase-2](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-2-and-4B-Customer-Data/Phase-2)
**Slug:** `Phase-2-and-4B-Customer-Data/Phase-2`

---

---
title: Phase 2
---

[← Phase 2 and 4B - Customer Data](Phase-2-and-4B-Customer-Data)

# Overview

The consent and the data a customer authorises a receiving institution to read.
Eleven plans in two layers.

Consents and Resources are the machinery: the consent that grants access, and the
resource list that says what the grant reached. Everything else depends on them,
so a failure there explains failures further down.

On top sit the data APIs: accounts, credit cards, loans, financings, invoice
financings, unarranged accounts overdraft, and the personal and business
registration data.

# Before you start

- Set up at least one personal or business account holding the product under test, and provide the user's CPF, or the CPF and CNPJ pair, in the test configuration.
- Accounts and Credit Cards test pagination. The user needs enough transactions for a second page to exist, which in practice means more than 25.
- Resources needs unavailable resources set by hand for the test user. They cannot be produced by the test.
- The operational limits modules may need two accounts under the same CPF or CPF/CNPJ pair, where the institution supports that, with 20 transactions on the current-transactions endpoint so pagination can be exercised.
- Operational limits decide what to test from what the Consents API returns. If the server answers 201 with the permissions, the resources are tested; if it does not, the modules are skipped with a warning, which reads as the institution not controlling those resources.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Accounts API - v2.5.1 - Conformance Suite | accounts_test-plan_v2-5-1 | 16 | 17/07/2026 |
| Consents API - v3.3.1 - Conformance Suite | consents_test-plan_v3-3-1 | 19 | 14/11/2025 |
| Credit Cards API - v2.4.0 - Conformance Suite | credit-cards_test-plan_v2-4 | 11 | 27/03/2026 |
| Customer Business API - v2.3.0 - Conformance Suite | customer-business_test-plan_v2-3 | 6 | 16/03/2026 |
| Customer Personal API - v2.3.0 - Conformance Suite | customer-personal_test-plan_v2-3 | 7 | 16/03/2026 |
| Financings API - v2.4.0 - Conformance Suite | financings_test-plan_v2-4 | 6 | 09/01/2026 |
| Invoice Financings API - v2.4.0 - Conformance Suite | invoice-financings_test-plan_v2-4 | 6 | 09/01/2026 |
| Loans API - v2.6.0 - Conformance Suite | loans_test-plan_v2-6 | 8 | 17/04/2026 |
| Loans API - v2.7.0 - Conformance Suite | loans_test-plan_v2-7 | 7 | 26/08/2026 |
| Resources API - v3.1.0 - Conformance Suite | resources_test-plan_v3-1 | 6 | 09/01/2026 |
| Unarranged Accounts Overdraft API - v2.5.0 - Conformance Suite | unarranged-accounts-overdraft_test-plan_v2-5 | 6 | 09/01/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Accounts API - v2.5.1 - Conformance Suite - 21 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.offersReservedBalances<br>resource.first_account_id<br>resource.second_account_id<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |
| Other | resource.brazilCpfReservedBalancesFalse |

</details>

<details>
<summary>Consents API - v3.3.1 - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Second client | client2.client_id<br>client2.jwks |
| Second client TLS certificates | mtls2.cert<br>mtls2.key<br>mtls2.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Credit Cards API - v2.4.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.first_credit_card_account_id<br>resource.second_credit_card_account_id<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Customer Business API - v2.3.0 - Conformance Suite - 17 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Customer Personal API - v2.3.0 - Conformance Suite - 18 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.employerDataCpf<br>resource.receivesSalaryPortability<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Financings API - v2.4.0 - Conformance Suite - 17 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Invoice Financings API - v2.4.0 - Conformance Suite - 17 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Loans API - v2.6.0 - Conformance Suite - 18 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfCreditPortability |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Loans API - v2.7.0 - Conformance Suite - 18 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfCreditPortability |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Resources API - v3.1.0 - Conformance Suite - 18 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.authorisationServerId |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Unarranged Accounts Overdraft API - v2.5.0 - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.first_unarranged_account_overdraft_account_id<br>resource.second_unarranged_account_overdraft_account_id<br>resource.brazilCpfOperational<br>resource.brazilCnpjOperationalBusiness<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Accounts API - v2.5.1 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| accounts_api_core_test-module_v2-5-1 | Checks every accounts API resource returns a spec compliant payload under a consent holding only the accounts permissions, with the x-v header set to 2.5.1. |
| accounts_api_current-transactions_test-module_v2-5-1 | Exercises the current accounts transactions resource: today's entries, the seven day booking date window, newest first ordering, and a 422 outside the valid period. |
| accounts_api_wrong-permissions_test-module_v2-5-1 | Confirms the accounts resources answer 200 under the accounts permission group and 403 under a consent carrying only customer data permissions. |
| accounts_api_permissions-restriction_test-module_v2-5-1 | Checks that an incomplete accounts permission set reaches only what it covers, 200 on accounts and transactions, 403 on balances and overdraft limits. |
| accounts_api_ux_test-module_v2-5-1 | Covers the login, MFA and consent screens the institution presents while an accounts consent is being authorised. |
| accounts_api_page-size_test-module_v2-5-1 | Checks the paging rules on the accounts list when it is requested with page-size set to 1000. |
| accounts_api_big-page-size_test-module_v2-5-1 | Confirms a request for accounts with a page-size above 1000, here 1001, is rejected with a 422. |
| accounts_api_max-page-size_test-module_v2-5-1 | Checks the accounts list honours the institution's own maximum page-size and that the next link in the metadata returns at least one further record. |
| accounts_api_bookingdate_test-module_v2-5-1 | Checks the accounts transactions endpoint honours fromBookingDate and toBookingDate, over the last six months, over an older window, and for one exact date. |
| accounts_api_operational-limits_test-module_v2-5-1 | Confirms the accounts, balances, limits and transactions endpoints stay open under the accounts operational limits, including the transactions next link. |
| accounts_api_reserved_balances_test-module_v2-5-1 | Checks the reserved balances endpoint returns data for an account flagged hasReservedBalance TRUE, and an empty list for one flagged FALSE. |
| accounts_api_reserved_balances_false_test-module_v2-5-1 | Ensure that a Reserved Balances request for an account with no reserved balance returns an empty list. |
| accounts_api_reserved_balances_permissions_v2-5-1 | Confirms balances and reserved balances both answer 403 when the consent does not carry ACCOUNTS_BALANCES_READ. |
| accounts_api_reserved_balances_operations_limits_v2-5-1 | Checks the reserved balances endpoint answers 200 across 420 consecutive calls, so the operational limits do not block it. |
| accounts_api_reserved_balances_not_found_v2-5-1 | Confirms an institution that does not offer reserved balances has not registered the endpoint and answers 404 on every account. |

</details>

<details>
<summary>Consents API - v3.3.1 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v3 | Validates the mTLS certificate before an access token is requested with the directory client_id, generates an SSA from the directory, then checks the mandatory fields. |
| consents_api_core_test-module_v3-3-1 | Checks a consent created with every existing permission is spec compliant and reads back as AUTHORISED once the customer has authorised it. |
| consents_api_client-limits_test-module_v3-3-1 | Confirms a second client can neither read nor delete another client's consent, both answering 403, while the owning client's delete moves it to a rejected state. |
| consents_api_delete_test-module_v3-3-1 | Checks that once a consent is deleted the access token already issued answers 401 and the refresh token no longer yields a new one. |
| consents_api_revoked-aspsp_test-module_v3-3-1 | Checks a consent revoked by the customer inside the institution reaches REJECTED, with rejectedBy USER and reason CUSTOMER_MANUALLY_REVOKED. |
| consents_api_extension-invalid-status-rejected_test-module_v3-3-1 | Confirms an extension is refused once the consent has already reached REJECTED, with 401, 403 or 422 ESTADO_CONSENTIMENTO_INVALIDO. |
| consents_api_invalid-logged-user-extension_test-module_v3-3-1 | Confirms an extension carrying a logged user or businessEntity that is not registered at the account holder is refused with 401 or 403. |
| consents_api_extension-invalid-status_test-module_v3-3-1 | Confirms an extension is refused with 401 or 403 while the consent is still AWAITING_AUTHORISATION. |
| consents_api_multiple-consents-extension-cond_test-module_v3-3-1 | Confirms a consent that depends on more than one signatory cannot be extended, the request failing with 422 DEPENDE_MULTIPLA_ALCADA. |
| consents_api_extension-security_test-module_v3-3-1 | Checks an extension sent without the x-fapi-customer-ip-address header returns 400, and one presented with a client credentials token 401 or 403. |
| consents_api_extension-past-expiration_test-module_v3-3-1 | Confirms an extension asking for an expirationDateTime in the past is refused with 422 DATA_EXPIRACAO_INVALIDA. |
| consents_api_extension-core_test-module_v3-3-1 | Checks a consent can be extended, that the new expirationDateTime is reflected on both the consent and the extensions list, and that x-v reads 3.3.1. |
| consents_api_multiples-extensions_test-module_v3-3-1 | Checks a consent can be extended several times and that all three extensions come back on the list with the dates requested. |
| consents_api_negative-extensions_test-module_v3-3-1 | Checks the extension business rules, a date not later than the current one failing with 422 DATA_EXPIRACAO_INVALIDA, and the list ordered by request date, newest first. |
| consents_api_negative_test-module_v3-3-1 | Confirms incomplete or invalid permission combinations are refused with 422 COMBINACAO_PERMISSOES_INCORRETA, and a malformed or past expiry date with a 400 or 422. |
| consents_api_permission-groups_test-module_v3-3-1 | Checks each valid permission group is accepted with a 201, or refused with 422 SEM_PERMISSOES_FUNCIONAIS_RESTANTES where the institution does not offer it. |
| consents_api_operational-limits_test-module_v3-3-1 | Checks the consents endpoint answers 200 across 600 consecutive reads of the same authorised consent, so no operational limit applies to it. |
| consents_api_expired-consent_test-module_v3-3-1 | Checks a consent reaches REJECTED with rejectedBy ASPSP and reason CONSENT_MAX_DATE_REACHED once its expiry passes, and that deleting it then returns 422. |
| consents_api_bad-consents_test-module_v3-3-1 | Confirms personal and business permissions sent together are refused with 422 PERMISSAO_PF_PJ_EM_CONJUNTO, and a missing or invalid x-fapi-interaction-id with a 400. |

</details>

<details>
<summary>Credit Cards API - v2.4.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| credit-cards_api_transactions-current_test-module_v2-4 | Exercises the current credit card transactions resource: today's entries, the seven day transaction date window, newest first ordering, and a 422 beyond that period. |
| credit-cards_api_core_test-module_v2-4 | Checks every credit card resource, accounts, limits, transactions, bills and bill transactions, returns a spec compliant payload with x-v set to 2.4.0. |
| credit-cards_api_wrong-permissions_test-module_v2-4 | Confirms the credit card resources answer 200 under the credit cards permission group and 403 under a consent carrying only customer data permissions. |
| credit-cards_api_page-size_test-module_v2-4 | Checks credit card accounts can be requested with page-size set to 1000 and that the response follows the paging rules. |
| credit-cards_api_big-page-size_test-module_v2-4 | Confirms a request for credit card accounts with a page-size above 1000 is rejected with a 422. |
| credit-cards_api_max-page-size_test-module_v2-4 | Checks the credit card transactions list honours the institution's own maximum page-size and that the next link returns at least one further record. |
| credit-cards_api_resources_test-module_v2-4 | Compares the ids returned by the credit cards API with those the resources API reports as AVAILABLE, and expects them to match. |
| credit-cards_api_operational-limits_test-module_v2-4 | Confirms the credit card accounts, bills, limits and transactions endpoints stay open under the operational limits, and that the pagination key still works. |
| credit-cards_api_instalment_test-module_v2-4 | Checks billForecastDate is present on correlated A_PRAZO instalment transactions and falls on the next consecutive months. |
| credit-cards_api_validate_billForecastDate_test-module_v2-4 | Checks billForecastDate on an A_PRAZO instalment purchase follows the expected pattern and differs from one instalment to the next. |

</details>

<details>
<summary>Customer Business API - v2.3.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| customer_api_preflight_test-module_v2 | Runs the pre-flight checks: the mTLS certificate, an access token issued with the directory client_id, an SSA from the directory, and the mandatory fields. |
| customer-business_api_businessentity-personal-permissions_test-module_v2-3 | Confirms a consent request that carries businessEntity together with personal customer data permissions is refused by the server. |
| customer-business_api_core_test-module_v2-3 | Checks the business customer data resources return a spec compliant payload under the customer business permissions, with x-v set to 2.3.0. |
| customer-business_api_wrong-permissions_test-module_v2-3 | Confirms the business qualifications and financial relations resources answer 403 under a consent holding every permission except the customer ones. |
| customer-business_api_operational-limits_test-module_v2-3 | Checks the business identifications, qualifications and financial relations endpoints stay open across repeated calls under the operational limits. |
| customer-business_api_x-fapi_test-module_v2-3 | Checks the business identifications endpoint refuses a missing or invalid x-fapi-interaction-id with a 400, and honours the 202 polling path when it is valid. |

</details>

<details>
<summary>Customer Personal API - v2.3.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| customer_api_preflight_test-module_v2 | Runs the pre-flight checks: the mTLS certificate, an access token issued with the directory client_id, an SSA from the directory, and the mandatory fields. |
| customer-personal_api_core_test-module_v2-3 | Checks the personal customer data resources return a spec compliant payload under the customer personal permissions, with x-v set to 2.3.0. |
| customer-personal_api_wrong-permissions_test-module_v2-3 | Confirms the personal qualifications and financial relations resources answer 403 under a consent holding every permission except the customer ones. |
| customer-personal_api_operational-limits_test-module_v2-3 | Checks the personal identifications, qualifications and financial relations endpoints stay open across repeated calls under the operational limits. |
| customer-personal_api_portability_test-module_v2-3 | Checks the personal financial relations resource carries portabilitiesReceived, for an institution that offers salary portability. |
| customer-personal_api_conditional-employer-data_test-module_v2-3 | Checks the personal financial relations resource carries paychecksBankLink, for an institution that receives employer data through a salary account. |
| customer-personal_api_x-fapi_test-module_v2-3 | Checks the personal identifications endpoint refuses a missing or invalid x-fapi-interaction-id with a 400, and honours the 202 polling path when it is valid. |

</details>

<details>
<summary>Financings API - v2.4.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| financings_api_core_test-module_v2-4 | Checks every financings resource, contracts, warranties, payments and scheduled instalments, returns a spec compliant payload with x-v set to 2.4.0. |
| financings_api_wrong-permissions_test-module_v2-4 | Confirms the financings resources answer 200 under the credit operations permission group and 403 under a customer data consent. |
| financings_api_resources_test-module_v2-4 | Compares the ids returned by the financings API with those the resources API reports as AVAILABLE, and expects them to match. |
| financings_api_operational-limits_test-module_v2-4 | Confirms the financings contract, warranties, scheduled instalments and payments endpoints stay open under the operational limits, across two active contracts. |
| financings_api_x-fapi_test-module_v2-4 | Checks every financings endpoint refuses a missing or malformed x-fapi-interaction-id with a 400 and echoes a valid one back. |

</details>

<details>
<summary>Invoice Financings API - v2.4.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| invoice-financings_api_core_test-module_v2-4 | Checks every discounted credit rights resource, contracts, warranties, payments and scheduled instalments, returns a spec compliant payload with x-v set to 2.4.0. |
| invoice-financings_api_wrong-permissions_test-module_v2-4 | Confirms the discounted credit rights resources answer 200 under the credit operations permission group and 403 under a customer data consent. |
| invoice-financings_api_resources_test-module_v2-4 | Compares the ids returned by the discounted credit rights API with those the resources API reports as AVAILABLE, and expects them to match. |
| invoice-financings_api_operational-limits_test-module_v2-4 | Confirms the invoice financings contract, warranties, scheduled instalments and payments endpoints stay open under the operational limits, across two active contracts. |
| invoice-financings_api_x-fapi_test-module_v2-4 | Checks every discounted credit rights endpoint refuses a missing or malformed x-fapi-interaction-id with a 400 and echoes a valid one back. |

</details>

<details>
<summary>Loans API - v2.6.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| loans_api_core_test-module_v2-6 | Checks every loans resource, contracts, warranties, payments and scheduled instalments, returns a spec compliant payload with x-v set to 2.6.0. |
| loans_api_wrong-permissions_test-module_v2-6 | Confirms the loans 2.6.0 resources answer 200 under the credit operations permission group and 403 under a customer data consent. |
| loans_api_resources_test-module_v2-6 | Compares the ids returned by the loans 2.6.0 API with those the resources API reports as AVAILABLE, and expects them to match. |
| loans_api_operational-limits_test-module_v2-6 | Confirms the loans 2.6.0 contract, warranties, scheduled instalments and payments endpoints stay open under the operational limits, across two active contracts. |
| loans_api_x-fapi_test-module_v2-6 | Checks every loans 2.6.0 endpoint refuses a missing or malformed x-fapi-interaction-id with a 400 and echoes a valid one back. |
| loans_api_credit-portability_test-module_v2-6 | Checks a CREDITO_PESSOAL_CLEAN loan carries every field credit portability needs, on the contracts list, the contract and the payments endpoints. |
| loans_api_credit-portability_payroll_test-module_v2-6 | Checks a CONSIGNADO_SIAPE payroll loan carries every field credit portability needs, on the contracts list, the contract and the payments endpoints. |

</details>

<details>
<summary>Loans API - v2.7.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| loans_api_core_test-module_v2-7 | Checks every loans resource, contracts, warranties, payments and scheduled instalments, returns a spec compliant payload with x-v set to 2.7.0. |
| loans_api_wrong-permissions_test-module_v2-7 | Confirms the loans 2.7.0 resources answer 200 under the credit operations permission group and 403 under a customer data consent. |
| loans_api_resources_test-module_v2-7 | Compares the ids returned by the loans 2.7.0 API with those the resources API reports as AVAILABLE, and expects them to match. |
| loans_api_operational-limits_test-module_v2-7 | Confirms the loans 2.7.0 contract, warranties, scheduled instalments and payments endpoints stay open under the operational limits, across two active contracts. |
| loans_api_x-fapi_test-module_v2-7 | Checks every loans 2.7.0 endpoint refuses a missing or malformed x-fapi-interaction-id with a 400 and echoes a valid one back. |
| loans_api_credit-portability_test-module_v2-7 | Checks a CREDITO_PESSOAL_SEM_CONSIGNACAO loan carries every field credit portability needs, and that interestRates holds at least one entry. |

</details>

<details>
<summary>Resources API - v3.1.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v3 | Validates the mTLS certificate before an access token is requested with the directory client_id, generates an SSA from the directory, then checks the mandatory fields. |
| resources_api_core_test-module_v3-1 | Checks the resources API returns a spec compliant payload with x-v 3.1.0 under a consent holding every permission, including the 202 polling path. |
| resources_api_200-customer-data_test-module_v3-1 | Checks the resources API returns 200 with an empty data object when the consent carries only customer data permissions. |
| resources_api_x-fapi_test-module_v3-1 | Checks the resources endpoint refuses a missing or invalid x-fapi-interaction-id with a 400, and honours the 202 polling path when it is valid. |
| resources_api_unavailable_test-module_v3-1 | Checks a resource reported as TEMPORARILY_UNAVAILABLE or UNAVAILABLE is left out of the list endpoints and answers 403 with the matching error code. |
| resources_api_operational-limits_test-module_v3-1 | Checks the resources endpoint answers 200 across 450 calls for each of three separate consents, so no operational limit applies to it. |

</details>

<details>
<summary>Unarranged Accounts Overdraft API - v2.5.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| consents_api_preflight_test-module_v2 | Validates the mTLS certificate, takes an access token with the directory client_id, generates an SSA from the Open Finance Brasil directory and checks the mandatory fields. |
| unarranged-accounts-overdraft_api_core_test-module_V2-5 | Checks every unarranged overdraft resource, contracts, warranties, payments and scheduled instalments, returns a spec compliant payload with x-v set to 2.5.0. |
| unarranged-accounts-overdraft_api_operational-limits_test-module_V2-5 | Confirms the unarranged overdraft contract, warranties, scheduled instalments and payments endpoints stay open under the operational limits, across two active contracts. |
| unarranged-accounts-overdraft_api_resources_test-module_V2-5 | Compares the ids returned by the unarranged overdraft API with those the resources API reports as AVAILABLE, and expects them to match. |
| unarranged-accounts-overdraft_api_wrong-permissions_test-module_V2-5 | Confirms the unarranged overdraft resources answer 200 under the credit operations permission group and 403 under a customer data consent. |
| unarranged-accounts-overdraft_api_x-fapi_test-module_v2-5 | Checks every unarranged overdraft endpoint refuses a missing or malformed x-fapi-interaction-id with a 400 and echoes a valid one back. |

</details>

# Spreadsheet

[CS-Phase-2.xlsx](uploads/2b4695f6b184771486f517cde2131274/CS-Phase-2.xlsx)

# Change history

<details>
<summary>2026 - 7 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 26/08/2026 | Loans released at v2.7.0. The v2.6.0 plan is still published, so both are selectable in the suite. | No |  |
| 17/07/2026 | Accounts released at v2.5.1. | No |  |
| 17/04/2026 | Loans released at v2.6.0. | No |  |
| 27/03/2026 | Credit Cards released at v2.4.0. | No |  |
| 16/03/2026 | Customer Personal and Customer Business released at v2.3.0. | No |  |
| 09/01/2026 | Resources v3.1.0 released, together with financings, invoice financings and unarranged accounts overdraft at v2.4 and v2.5. | No |  |

</details>

<details>
<summary>2025 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 14/11/2025 | Consents v3.3.1 released. | No |  |

</details>

<details>
<summary>2023 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2023 | Test plans for Accounts, Credit Cards, Loans, Financings, Invoice Financings and Unarranged Accounts Overdraft released at version 2.1. | No |  |

</details>

<details>
<summary>2022 - 3 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 29/09/2022 | Certification opened for the Phase 2 v2 APIs, with requests accepted on the Open Finance Service Desk. | No |  |
| 02/08/2022 | Tests released in a Beta version, based on version 2.0.1 of the APIs. | No |  |
| 22/07/2022 | Tests released in an Alpha version, based on version 2.0.0 of the APIs. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*11 plans, 98 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:19*
