# Alphanumeric CNPJ

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Alphanumeric-CNPJ](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Alphanumeric-CNPJ)
**Slug:** `Alphanumeric-CNPJ`

---

---
title: Alphanumeric CNPJ
---

# Overview

The CNPJ is becoming alphanumeric. Every place in Open Finance Brasil that
carries one has to accept the new pattern, and that is not one API but a property
of all of them.

So this is not a product. It is a cross-cutting profile: one plan per area that
handles a CNPJ, each running the smallest set of modules that proves the
area accepts the new format. Open Data, Customer Data, Payments, Automatic
Payments, Enrollments and Credit Portability.

# Before you start

- The test data must carry a CNPJ in the new alphanumeric format. A run against the numeric-only data you already use for the other plans proves nothing here.
- Each plan carries the data requirements of the area it exercises. The Payments plan still needs an account able to receive a payment, the Credit Portability plan still needs an eligible contract, and so on.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Functional Tests for Alphanumeric CNPJ - Automatic Payments API | automatic-payments_alphanumeric-cnpj_test-plan | 4 | 30/06/2026 |
| Functional Tests for Alphanumeric CNPJ - Credit Portability API | credit-portability_alphanumeric-cnpj_test-plan | 1 | 30/06/2026 |
| Functional Tests for Alphanumeric CNPJ - Customer Data | customer-data_alphanumeric-cnpj_test-plan | 10 | 30/06/2026 |
| Functional Tests for Alphanumeric CNPJ - Enrollments API | enrollments_alphanumeric-cnpj_test-plan | 3 | 30/06/2026 |
| Functional Tests for Alphanumeric CNPJ - Open Data | open-data_alphanumeric-cnpj_test-plan | 2 | 30/06/2026 |
| Functional Tests for Alphanumeric CNPJ - Payments API | payments_alphanumeric-cnpj_test-plan | 3 | 30/06/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Automatic Payments API - 36 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.creditorAccountSweepingIspb<br>resource.creditorAccountSweepingIssuer<br>resource.creditorAccountSweepingNumber<br>resource.creditorAccountSweepingAccountType<br>resource.creditorAccountSweepingName<br>resource.creditorSweepingCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Credit Portability API - 10 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.authorisationServerId |
| Client | client.org_jwks |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Customer Data - 10 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.authorisationServerId |
| Client | client.org_jwks |
| Resource | resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Enrollments API - 31 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Open Data - 3 fields</summary>

| Section | Fields |
|---|---|
| Server | server.authorisationServerId |
| Resource | resource.resourceUrl<br>resource.brazilOrganizationId |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Payments API - 22 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Automatic Payments API</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_automatic-pix-semanal-core_alphanumeric_cnpj_test-module_v2-2 | Checks a weekly automatic Pix consent carrying alphanumeric CNPJs in businessEntity.document.identification and creditors.cpfCnpj pays to ACSC and cancels its scheduled payment. |
| automatic-payments_api_automatic-pix-revoked_alphanumeric_cnpj_test-module_v2-2 | Checks that revoking a weekly automatic Pix consent held under an alphanumeric CNPJ leaves the already scheduled payment in CANC with reason CANCELADO_AGENDAMENTO. |
| automatic-payments_api_multiple-consents-core_alphanumeric_cnpj_test-module_v2-2 | Checks an automatic Pix recurring payment under an alphanumeric CNPJ is refused with 422 CONSENTIMENTO_PENDENTE_AUTORIZACAO while the consent is PARTIALLY_ACCEPTED, then succeeds. |
| automatic-payments_api_sweeping-accounts-core_alphanumeric_cnpj_test-module_v2-2 | Checks a sweeping accounts consent carrying alphanumeric CNPJs funds two payments against its 600.00 limit and moves to CONSUMED once the amount is reached. |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Credit Portability API</summary>

| Test module | What it does |
|---|---|
| credit-portability_api_portability-payment_core_alphanumeric_cnpj_test-module_v1-1 | Checks a portability request whose proposing institution.companyCnpj is alphanumeric is accepted, and that GET /portabilities returns the proponent CNPJ in that form. |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Customer Data</summary>

| Test module | What it does |
|---|---|
| consents_api_alphanumeric_cnpj_test-module_v3-3-1 | Checks a consent created for a legal entity whose businessEntity CNPJ is alphanumeric can be authorised and then extended to a later expiry. |
| customer-business_api_alphanumeric_cnpj_test-module_v2-3 | Checks business customer data returns alphanumeric CNPJs in cnpjNumber, in parties.documentNumber for involved parties, and in procurators.cnpjCpfNumber. |
| customer-personal_api_alphanumeric_cnpj_test-module_v2-3 | Checks personal customer data returns alphanumeric CNPJs in employers.cnpjCpf, employerCnpjCpf and paycheckBankCnpj. |
| accounts_api_alphanumeric_cnpj_test-module_v2-5-1 | Checks both the transactions and transactions-current endpoints return a counterparty partieCnpjCpf holding an alphanumeric CNPJ. |
| loans_api_alphanumeric_cnpj_test-module_v2-7 | Checks a loan contract returns the consignee's cnpjConsignor as an alphanumeric CNPJ. |
| exchange_api_alphanumeric_cnpj_test-module_v1-1 | Checks a foreign exchange operation returns authorizedInstitutionCnpjNumber and intermediaryInstitutionCnpjNumber as alphanumeric CNPJs. |
| funds_api_alphanumeric_cnpj_test-module_v1-1 | Checks an investment fund position returns the fund's own cnpjNumber as an alphanumeric CNPJ. |
| bank-fixed-incomes_api_alphanumeric_cnpj_test-module_v1-1 | Checks a bank fixed income investment returns issuerInstitutionCnpjNumber as an alphanumeric CNPJ. |
| credit-fixed-incomes_api_alphanumeric_cnpj_test-module_v1-1 | Checks a credit fixed income investment returns issuerInstitutionCnpjNumber, and debtorCnpjNumber on CRI and CRA products, as alphanumeric CNPJs. |
| variable-incomes_api_alphanumeric_cnpj_test-module_v1-3 | Checks a variable income investment returns issuerInstitutionCnpjNumber as an alphanumeric CNPJ. |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Enrollments API</summary>

| Test module | What it does |
|---|---|
| enrollments_api_core-enrollment_alphanumeric_cnpj_test-module_v2-3 | Runs a device enrollment for a legal entity whose businessEntity document identification is alphanumeric, from risk signals through FIDO registration to AUTHORISED. |
| enrollments_api_payments-core_alphanumeric_cnpj_test-module_v2-3 | Checks a no redirect payment signed over an enrollment with no expiry reaches ACSC, with alphanumeric CNPJs in the consent's businessEntity and creditor.cpfCnpj. |
| enrollments_api_automatic-payments_alphanumeric_cnpj_test-module_v2-3 | Checks a weekly automatic Pix consent authorised by FIDO signature over an enrollment pays to ACSC and schedules the next payment as SCHD, with alphanumeric CNPJs throughout. |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Open Data</summary>

| Test module | What it does |
|---|---|
| opendata-investments_api_alphanumeric_cnpj_test-module_v1-1 | Checks the unauthenticated open data endpoints return alphanumeric CNPJs in a fund's cnpjNumber, admin.cnpjNumber, fundManager.cnpjNumber and issuerInstitutionCnpjNumber. |
| opendata-insurance_api_alphanumeric_cnpj_test-module_v2-1 | Checks the unauthenticated open data personal insurance endpoint returns participant.cnpjNumber and society.cnpjNumber as alphanumeric CNPJs. |

</details>

<details>
<summary>Functional Tests for Alphanumeric CNPJ - Payments API</summary>

| Test module | What it does |
|---|---|
| payments_api_recurring-payments-daily-core_alphanumeric_cnpj_test-module_v5 | Checks a daily recurring payments consent carrying alphanumeric CNPJs schedules its five payments, each ending in SCHD. |
| payments_api_multiple-consents-conditional_alphanumeric_cnpj_test-module_v5 | Checks a payment under multiple account consents, held with an alphanumeric CNPJ, is refused with 422 CONSENTIMENTO_PENDENTE_AUTORIZACAO until all are granted, then reaches ACSC. |
| payments_api_dict-pix-response_alphanumeric_cnpj_test-module_v5 | Checks a payment reaches ACSC when localInstrument is DICT and the creditor key is the alphanumeric CNPJ registered in the Sandbox DICT. |

</details>

# Spreadsheet

[CS-Alphanumeric-CNPJ.xlsx](uploads/c48cf3f416d142d3ce2940a9dcf36229/CS-Alphanumeric-CNPJ.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 30/06/2026 | All six Alphanumeric CNPJ plans released, one per area that handles a CNPJ. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*6 plans, 23 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:08*
