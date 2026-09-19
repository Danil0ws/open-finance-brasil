# Certification Automated Process

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Certification-Automated-Process](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Certification-Automated-Process)
**Slug:** `Certification-Automated-Process`

---

# Conformance Test Plans - Open Finance Brasil

**What it is** - the current list of Open Finance Brasil conformance test plans the Conformance Suite runs, mapped to the exact option each one appears as in the Service Desk.

**Where it fits** - use it when opening a certification ticket: find the option in the Service Desk API List column, select that same option in the ticket form, and use the other columns to confirm the Conformance Suite plan it maps to.

## References

* [Guia de Certificação de Conformidade](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/155910145/Guia+de+Certifica+o+de+Conformidade)
* [Diretrizes Gerais de Certificação de Conformidade](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/280297514/Diretrizes+Gerais+de+Certifica+o+de+Conformidade)
* [Certification Guide](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Certification-Guide)

## Key ideas

* Sections are grouped by product and version; within each, the Service Desk API List is sorted alphabetically. A single plan may appear under more than one option.
* Service Desk API List is the label to pick when opening the ticket.
* Plan Display Name is the plan as named inside the Conformance Suite.
* Plan Name is the technical test-plan identifier.
* Which plans are mandatory depends on the participant's role and the functionalities it offers; this page is the catalog, not a per-participant obligation list.

## Test plans

### Accounts v2.5.1

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Accounts - v2.5.1 - Com reserved-balances | Accounts API - v2.5.1 - Conformance Suite | accounts_test-plan_v2-5-1 |
| Customer Data - Accounts - v2.5.1 - Não reserved-balances | Accounts API - v2.5.1 - Conformance Suite | accounts_test-plan_v2-5-1 |

### Automatic Payments v2.2.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Automatic Payments – v2.2.0 | Automatic Payments API - v2.2.0 - Automatic Pix - Conformance Suite | automatic-pix-payments_test-plan_v2-2 |
| Automatic Pix Payments Retry - v2.2.0 | Automatic Payments API - v2.2.0 - Automatic Pix Retry - Conformance Suite | automatic-pix-payments-retry_test-plan_v2-2 |
| Automatic Pix Payments Timezone - v2.2.0 | Automatic Payments API - v2.2.0 - Automatic Pix Timezone - Conformance Suite | automatic-pix-payments-timezone_test-plan_v2-2 |
| Automatic Pix Payments Webhook - v2.2.0 | Automatic Payments API - v2.2.0 - Automatic Pix Webhook - Conformance Suite | automatic-pix-payments-webhook_test-plan_v2-2 |
| Automatic Sweeping Payments - v2.2.0 | Automatic Payments API - v2.2.0 - Sweeping - Conformance Suite | automatic-payments_test-plan_v2-2 |
| Automatic Sweeping Payments Timezone - v2.2.0 | Automatic Payments API - v2.2.0 - Sweeping Timezone - Conformance Suite | automatic-payments-timezone_test-plan_v2-2 |
| Automatic Sweeping Payments Webhook - v2.2.0 | Automatic Payments API - v2.2.0 - Sweeping Webhook - Conformance Suite | automatic-payments-webhook_test-plan_v2-2 |

### Bank Fixed Incomes v1.1.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Bank Fixed Incomes - v1.1.0 | Bank Fixed Incomes API - v1.1.0 - Conformance Suite | bank-fixed-incomes_test-plan_v1_1 |
| Customer Data - Bank Fixed Incomes - v1.1.0 - Timezone | Bank Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite | bank-fixed-incomes-timezone_test-plan_v1_1 |

### Consents v3.3.1

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Consents - v3.3.1 | Consents API - v3.3.1 - Conformance Suite | consents_test-plan_v3-3-1 |

### Credit Cards v2.4.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Credit Card - v2.4.0 | Credit Cards API - v2.4.0 - Conformance Suite | credit-cards_test-plan_v2-4 |

### Credit Fixed Incomes v1.1.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Credit Fixed Incomes - v1.1.0 | Credit Fixed Incomes API - v1.1.0 - Conformance Suite | credit-fixed-incomes_test-plan_v1_1 |
| Customer Data - Credit Fixed Incomes - v1.1.0 - Timezone | Credit Fixed Incomes API - v1.1.0 - Timezone - Conformance Suite | credit-fixed-incomes-timezone_test-plan_v1_1 |

### Credit Portability v1.0.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Credit Portability - CPC - v1.0.0 | Credit Portability API - v1.0.0 - Conformance Suite | credit-portability_test-plan_v1 |

### Customer Business Data v2.3.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Business Customer Data - v2.3.0 | Customer Business API - v2.3.0 - Conformance Suite | customer-business_test-plan_v2-3 |

### Customer Personal Data v2.3.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Personal - v2.3.0 - Com Port. de Salário | Customer Personal API - v2.3.0 - Conformance Suite | customer-personal_test-plan_v2-3 |
| Customer Data - Personal - v2.3.0 - Não Port. de Salário | Customer Personal API - v2.3.0 - Conformance Suite | customer-personal_test-plan_v2-3 |

### Enrollments v2.2.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| JSR - Enrollments - Automatic Payments – v2.2.0 | Enrollments API - v2.2.0 - Automatic Payments - Conformance Suite | no-redirect-automatic-payments_api_test-plan_v2-2 |
| JSR - Enrollments - Payments – v2.2.0 | Enrollments API - v2.2.0 - Payments - Conformance Suite | no-redirect-payments_api_test-plan_v2-2 |
| JSR - Enrollments - Webhook – v2.2.0 | Enrollments API - v2.2.0 - Payments Webhook - Conformance Suite | no-redirect-payments-webhook_test-plan_v2-2 |
| JSR - Enrollments – v2.2.0 | Enrollments API - v2.2.0 - Conformance Suite | enrollment_test-plan_v2-2 |

### Exchanges v1.1.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Exchanges - v1.1.0 | Exchange API - v1.1.0 - Conformance Suite | exchanges_test-plan_v1-1 |

### Financings v2.4.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Financings - v2.4.0 | Financings API - v2.4.0 - Conformance Suite | financings_test-plan_v2-4 |

### Funds v1.1.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Funds - v1.1.0 | Funds API - v1.1.0 - Conformance Suite | funds_test-plan_v1n1 |
| Customer Data - Funds - v1.1.0 - Timezone | Funds API - v1.1.0 - Timezone - Conformance Suite | funds-timezone_test_plan_v1n1 |

### Invoice Financings v2.4.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Invoice Financings - v2.4.0 | Invoice Financings API - v2.4.0 - Conformance Suite | invoice-financings_test-plan_v2-4 |

### Loans v2.6.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Loans - v2.6.0 | Loans API - v2.6.0 - Conformance Suite | loans_test-plan_v2-6 |

### Payments v4.0.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Payments - Pix - v4.0.0 - Inclui Múltiplas Alçadas | Payments API - v4.0.1 - Conformance Suite | payments_test-plan_v4 |
| Payments - Pix - v4.0.0 - Inclui Temporização | Payments API - v4.0.1 - Conformance Suite | payments_test-plan_v4 |
| Payments - Pix - v4.0.0 - Inclui Temporização + Múltipla Alçada | Payments API - v4.0.1 - Conformance Suite | payments_test-plan_v4 |
| Payments - Pix - v4.0.0 - QRDN | Payments API - v4.0.1 - QRDN - Conformance Suite | payments-qrdn_test-plan_v4 |
| Payments - Pix - v4.0.0 - Sem Condicionais Executados | Payments API - v4.0.1 - Conformance Suite | payments_test-plan_v4 |
| Payments - Pix - v4.0.0 - Timezone | Payments API - v4.0.1 - Timezone - Conformance Suite | payments-timezone_test-plan_v4 |
| Payments - Pix - v4.0.0 - Webhook | DCR - PAGTO Role - Payments v4.0.1 - Webhook v1.0.0 - Conformance Suite | dcr-dcm-pagto_test-plan-v4 |

### Payments v5.0.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Payments v5.0.0 - APDN - Com JSR | Payments API - v5.0.0 - APDN - Conformance Suite | payments-apdn_test-plan_v5 |
| Payments v5.0.0 - APES - Com JSR | Payments API - v5.0.0 - APES - Conformance Suite | payments-apes_test-plan_v5 |
| Payments v5.0.0 - Change QRDN - Com JSR | Payments API - v5.0.0 - Change QRDN - Conformance Suite | payments-change-qrdn_test-plan_v5 |
| Payments v5.0.0 - Change QRDN - Não JSR | Payments API - v5.0.0 - Change QRDN - Conformance Suite | payments-change-qrdn_test-plan_v5 |
| Payments v5.0.0 - Com JSR | Payments API - v5.0.0 - Conformance Suite | payments_test-plan_v5 |
| Payments v5.0.0 - Não JSR | Payments API - v5.0.0 - Conformance Suite | payments_test-plan_v5 |
| Payments v5.0.0 - QRDN - Com JSR | Payments API - v5.0.0 - QRDN - Conformance Suite | payments-qrdn_test-plan_v5 |
| Payments v5.0.0 - QRDN - Não JSR | Payments API - v5.0.0 - QRDN - Conformance Suite | payments-qrdn_test-plan_v5 |
| Payments v5.0.0 - Timezone - Com JSR | Payments API - v5.0.0 - Timezone - Conformance Suite | payments-timezone_test-plan_v5 |
| Payments v5.0.0 - Timezone - Não JSR | Payments API - v5.0.0 - Timezone - Conformance Suite | payments-timezone_test-plan_v5 |
| Payments v5.0.0 - Webhook - Com JSR | DCR - PAGTO Role - Payments v5.0.0 - Webhook v1.3.0 - Conformance Suite | dcr-dcm-pagto_test-plan-v5 |
| Payments v5.0.0 - Webhook - Não JSR | DCR - PAGTO Role - Payments v5.0.0 - Webhook v1.3.0 - Conformance Suite | dcr-dcm-pagto_test-plan-v5 |
| Payments v5.0.0 - Withdraw QRES - Com JSR | Payments API - v5.0.0 - Withdraw - Conformance Suite | payments-withdraw_test-plan_v5 |
| Payments v5.0.0 - Withdraw QRES - Não JSR | Payments API - v5.0.0 - Withdraw - Conformance Suite | payments-withdraw_test-plan_v5 |

### Resources v3.1.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Resources - v3.1.0 | Resources API - v3.1.0 - Conformance Suite | resources_test-plan_v3-1 |

### Treasure Titles v1.1.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Treasure Titles - v1.1.0 | Treasure Titles API - v1.1.0 - Conformance Suite | treasure-titles_test-plan_v1n1 |
| Customer Data - Treasure Titles - v1.1.0 - Timezone | Treasure Titles API - v1.1.0 - Timezone - Conformance Suite | treasure-titles-timezone_test_plan_v1n1 |

### Unarranged Overdraft v2.5.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Unarranged Accounts Overdraft - v2.5.0 | Unarranged Accounts Overdraft API - v2.5.0 - Conformance Suite | unarranged-accounts-overdraft_test-plan_v2-5 |

### Variable Incomes v1.3.0

| Service Desk API List | Plan Display Name | Plan Name |
|---|---|---|
| Customer Data - Variable Incomes - v1.3.0 | Variable Incomes API - v1.3.0 - Conformance Suite | variable-incomes_test-plan_V1-3-0 |
| Customer Data - Variable Incomes - v1.3.0 - Timezone | Variable Incomes API - v1.3.0 - Timezone - Conformance Suite | variable-incomes-timezone_test_plan_V1-3-0 |

---
_Auto-generated on 2026-08-02 from commit 301349e. 45 plans, 56 Service Desk options._


---

*Conteúdo baixado em 16/09/2026, 15:37:13*
