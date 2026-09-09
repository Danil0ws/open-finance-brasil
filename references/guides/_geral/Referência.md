# Referência

## Relatórios e Métricas

### API Admin

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /metrics

Baixa

4000

15

NA

NA

NA

### API Comum (Discovery)

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /status

Baixa

4000

15

NA

NA

NA

GET /outages

Baixa

4000

15

NA

NA

NA

## Dados Abertos

### \[DA\] API Produtos e Serviços

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /personal-accounts

Baixa

4000

15

500

300

NA

GET /business-accounts

Baixa

4000

15

500

300

NA

GET /personal-loans

Baixa

4000

15

500

300

NA

GET /business-loans

Baixa

4000

15

500

300

NA

GET /personal-credit-cards

Baixa

4000

15

500

300

NA

GET /business-credit-cards

Baixa

4000

15

500

300

NA

GET /personal-financings

Baixa

4000

15

500

300

NA

GET /business-financings

Baixa

4000

15

500

300

NA

GET /personal-invoice-financings

Baixa

4000

15

500

300

NA

GET /business-invoice-financings

Baixa

4000

15

500

300

NA

GET /personal-unarranged-account-overdraft

Baixa

4000

15

500

300

NA

GET /business-unarranged-account-overdraft

Baixa

4000

15

500

300

NA

### [\[DA\] API Canais de Atendimento](https://openfinancebrasil.atlassian.net/wiki/pages/createpage.action?spaceKey=of&title=API%20-%20Canais%20de%20Atendimentos&linkCreation=true&fromPageId=17957025)

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /banking-agents

Baixa

4000

15

500

300

NA

GET /branches

Baixa

4000

15

500

300

NA

GET /electronic-channels

Baixa

4000

15

500

300

NA

GET /phone-channels

Baixa

4000

15

500

300

NA

GET /shared-automated-teller-machines

Baixa

4000

15

500

300

NA

### \[DA\] API Títulos de Capitalização

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /bonds

Baixa

4000

15

500

300

NA

### \[DA\] API Investimentos

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /funds

Baixa

4000

15

500

300

NA

GET /bank-fixed-incomes

Baixa

4000

15

500

300

NA

GET /credit-fixed-incomes

Baixa

4000

15

500

300

NA

GET /variable-incomes

Baixa

4000

15

500

300

NA

GET /treasure-titles

Baixa

4000

15

500

300

NA

### \[DA\] API Câmbio

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /online-rates

Alta

1500

15

500

300

NA

GET /vet-values

Baixa

4000

15

500

300

NA

### \[DA\] API Credenciamento

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /businesses

Baixa

4000

15

500

300

NA

GET /personals

Baixa

4000

15

500

300

NA

### \[DA\] API Previdência

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /risk-coverages

Baixa

4000

15

500

300

NA

GET /survival-coverages

Baixa

4000

15

500

300

NA

### \[DA\] API Seguros

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /automotives

Baixa

4000

15

500

300

NA

GET /homes

Baixa

4000

15

500

300

NA

GET /personals

Baixa

4000

15

500

300

NA

## Dados do Cliente

### \[DC\] API Consentimento

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

POST /consents

Alta

1500

15

NA

300

NA

GET /consents​/{consentId}

Alta

1500

15

NA

300

NA

DELETE /consents​/{consentId}

Alta

1500

15

NA

300

NA

POST /consents/{consentId}/extends​

Baixa

4000

15

NA

300

NA

GET /consents/​{consentId}/extensions​

Baixa

4000

15

NA

300

NA

### \[DC\] API Recursos

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /resources

Alta

1500

15

NA

300

NA

### \[DC\] API Dados Cadastrais

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/personal​/identifications

Baixa

4000

15

1000

300

8

GET ​/personal​/qualifications

Baixa

4000

15

1000

300

8

GET ​/personal​/financial-relations

Baixa

4000

15

1000

300

8

GET ​/business​/identifications

Baixa

4000

15

1000

300

8

GET ​/business​/qualifications

Baixa

4000

15

1000

300

8

GET ​/business​/financial-relations

Baixa

4000

15

1000

300

8

### \[DC\] API Cartão de Crédito

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/accounts

Baixa

4000

15

1000

300

8

GET ​/accounts​/{creditCardAccountId}

Média-Alta

1500

15

2000

300

120

GET ​/accounts​/{creditCardAccountId}​/bills

Média

2000

15

1500

300

30

GET ​/accounts​/{creditCardAccountId}​/bills​/{billId}​/transactions

Média

2000

15

1500

300

30

GET ​/accounts​/{creditCardAccountId}​/limits

Alta

1500

15

a) quando a quantidade de consentimentos ativos for ≤ 6 milhões, aplica-se a tabela:

QCA | TPM

0 < QCA ≤ 1 000 000 → 2 500

1 000 000 < QCA ≤ 2 000 000 → 5 000

2 000 000 < QCA ≤ 3 000 000 → 8 000

3 000 000 < QCA ≤ 6 000 000 → 10 000

b) para QCA > 6 000 000, o TPM é calculado em faixas de 2 milhões, somando-se 2 000 ao limite da faixa anterior (ex.: 6-8 MM → 12 000 TPM).

300

240

GET ​/accounts​/{creditCardAccountId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/accounts​/{creditCardAccountId}​/transactions-current

Alta

1500

15

a) quando a quantidade de consentimentos ativos for ≤ 6 milhões, aplica-se a tabela:

QCA | TPM

0 < QCA ≤ 1 000 000 → 2 500

1 000 000 < QCA ≤ 2 000 000 → 5 000

2 000 000 < QCA ≤ 3 000 000 → 8 000

3 000 000 < QCA ≤ 6 000 000 → 10 000

b) para QCA > 6 000 000, o TPM é calculado em faixas de 2 milhões, somando-se 2 000 ao limite da faixa anterior (ex.: 6-8 MM → 12 000 TPM).

300

240

### \[DC\] API Contas

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/accounts

Baixa

4000

15

1000

300

8

GET ​/accounts​/{accountId}

Baixa

4000

15

1000

300

8

GET ​/accounts​/{accountId}​/balances

Alta

1500

15

a) quando a quantidade de consentimentos ativos for ≤ 6 milhões, aplica-se a tabela:

QCA | TPM

0 < QCA ≤ 1 000 000 → 2 500

1 000 000 < QCA ≤ 2 000 000 → 5 000

2 000 000 < QCA ≤ 3 000 000 → 8 000

3 000 000 < QCA ≤ 6 000 000 → 10 000

b) para QCA > 6 000 000, o TPM é calculado em faixas de 2 milhões, somando-se 2 000 ao limite da faixa anterior (ex.: 6-8 MM → 12 000 TPM).

300

420

GET /accounts/{accountId}/reserved-balances

Alta

1500

15

a) quando a quantidade de consentimentos ativos for ≤ 6 milhões, aplica-se a tabela:

QCA | TPM

0 < QCA ≤ 1 000 000 → 2 500

1 000 000 < QCA ≤ 2 000 000 → 5 000

2 000 000 < QCA ≤ 3 000 000 → 8 000

3 000 000 < QCA ≤ 6 000 000 → 10 000

b) para QCA > 6 000 000, o TPM é calculado em faixas de 2 milhões, somando-se 2 000 ao limite da faixa anterior (ex.: 6-8 MM → 12 000 TPM).

300

420

GET ​/accounts​/{accountId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/accounts​/{accountId}​/transactions-current

Alta

1500

15

a) quando a quantidade de consentimentos ativos for ≤ 6 milhões, aplica-se a tabela:

QCA | TPM

0 < QCA ≤ 1 000 000 → 2 500

1 000 000 < QCA ≤ 2 000 000 → 5 000

2 000 000 < QCA ≤ 3 000 000 → 8 000

3 000 000 < QCA ≤ 6 000 000 → 10 000

b) para QCA > 6 000 000, o TPM é calculado em faixas de 2 milhões, somando-se 2 000 ao limite da faixa anterior (ex.: 6-8 MM → 12 000 TPM).

300

240

GET ​/accounts​/{accountId}​/overdraft-limits

Alta

1500

15

a) quando a quantidade de consentimentos ativos for ≤ 6 milhões, aplica-se a tabela:

QCA | TPM

0 < QCA ≤ 1 000 000 → 2 500

1 000 000 < QCA ≤ 2 000 000 → 5 000

2 000 000 < QCA ≤ 3 000 000 → 8 000

3 000 000 < QCA ≤ 6 000 000 → 10 000

b) para QCA > 6 000 000, o TPM é calculado em faixas de 2 milhões, somando-se 2 000 ao limite da faixa anterior (ex.: 6-8 MM → 12 000 TPM).

300

420

### \[DC\] API Operações de Crédito - Empréstimo

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/contracts

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}​/warranties

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/scheduled-instalments

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}​/payments

Média-Alta

1500

15

2000

300

120

### \[DC\] API Operações de Crédito - Financiamento

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/contracts

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/warranties

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/scheduled-instalments

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}​/payments

Média

2000

15

1500

300

30

### \[DC\] API Operações de Crédito - Adiantamento a Depositantes

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/contracts

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/warranties

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/scheduled-instalments

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}​/payments

Média

2000

15

1500

300

30

### \[DC\] API Operações de Crédito - Direitos Creditórios Descontados

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/contracts

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/warranties

Baixa

4000

15

1000

300

8

GET ​/contracts​/{contractId}​/scheduled-instalments

Média

2000

15

1500

300

30

GET ​/contracts​/{contractId}​/payments

Média

2000

15

1500

300

30

### \[DC\] API Investimentos - Renda Fixa Bancária

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/investments

Média

2000

15

1500

300

30

GET ​/investments​/{investimentId}

Baixa

4000

15

1000

300

8

GET /investments​/{investimentId}​/balances

Média-alta

1500

15

2000

300

120

GET /investments​/{investimentId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/investments​/{investimentId}​/transactions-current

Média-alta

1500

15

2000

300

120

### \[DC\] API Investimentos - Renda Fixa Crédito

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/investments

Média

2000

15

1500

300

30

GET ​/investments​/{investimentId}

Baixa

4000

15

1000

300

8

GET /investments​/{investimentId}​/balances

Média-alta

1500

15

2000

300

120

GET /investments​/{investimentId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/investments​/{investimentId}​/transactions-current

Média-alta

1500

15

2000

300

120

### \[DC\] API Investimentos - Renda Variável

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/investments

Média

2000

15

1500

300

30

GET ​/investments​/{investimentId}

Baixa

4000

15

1000

300

8

GET /investments​/{investimentId}​/balances

Média

2000

15

1500

300

30

GET /investments​/{investimentId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/investments​/{investimentId}​/transactions-current

Média

2000

15

1500

300

30

GET ​/broker-notes/{brokerNoteId}

Média

2000

15

1500

300

30

### \[DC\] API Investimentos - Títulos do Tesouro Direto

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/investments

Média

2000

15

1500

300

30

GET ​/investments​/{investimentId}

Baixa

4000

15

1000

300

8

GET /investments​/{investimentId}​/balances

Média-alta

1500

15

2000

300

120

GET /investments​/{investimentId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/investments​/{investimentId}​/transactions-current

Média-alta

1500

15

2000

300

120

### \[DC\] API Investimentos - Fundos de Investimento

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/investments

Média

2000

15

1500

300

30

GET ​/investments​/{investimentId}

Baixa

4000

15

1000

300

8

GET /investments​/{investimentId}​/balances

Média-alta

1500

15

2000

300

120

GET /investments​/{investimentId}​/transactions

Baixa

4000

15

1000

300

8

GET ​/investments​/{investimentId}​/transactions-current

Média-alta

1500

15

2000

300

120

### \[DC\] API Câmbio

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET ​/operations

Média

2000

15

1500

300

30

GET ​/operations​/{operationId}

Baixa

4000

15

1000

300

8

GET ​/operations​/{operationId}/events

Média

2000

15

1500

300

30

## Serviços

### \[SV\] API Pagamentos

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

POST ​/consents

Alta

1500

15

NA

300

NA

GET ​/consents​/{consentId}

Alta

1500

15

NA

300

NA

POST ​/pix​/payments

Alta

1500

15

NA

300

NA

GET ​/pix​/payments​/{paymentId}

Alta

1500

15

NA

300

NA

PATCH /pix/payments/{paymentld}

Alta

1500

15

NA

300

NA

### \[SV\] API Pagamentos Automáticos

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

POST /recurring-consents

Alta

1500

15

NA

300

NA

GET /recurring-consents/{recurringConsentId}

Alta

1500

15

NA

300

NA

PATCH /recurring-consents/{recurringConsentId}

Alta

1500

15

NA

300

NA

POST /pix/recurring-payments

Alta

1500

15

NA

300

NA

GET /pix/recurring-payments/{recurringPaymentId}

Alta

1500

15

NA

300

NA

GET /pix/recurring-payments

Alta

1500

15

NA

300

NA

PATCH /pix/recurring-payments/{recurringPaymentId}

Alta

1500

15

NA

300

NA

POST /pix/recurring-payments/{originalRecurringPaymentId}/retry

Alta

1500

15

NA

300

NA

### \[SV\] API Pagamentos sem Redirecionamento

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

POST /enrollments

Alta

1500

15

N/A

300

N/A

GET /enrollments/{enrollmentId}

Alta

1500

15

N/A

300

N/A

PATCH /enrollments/{enrollmentId}

Alta

1500

15

N/A

300

N/A

POST /enrollments/{enrollmentId}/fido-registration-options

Alta

1500

15

N/A

300

N/A

POST /enrollments/{enrollmentId}/fido-registration

Alta

1500

15

N/A

300

N/A

POST /enrollments/{enrollmentId}/fido-sign-options

Alta

1500

15

N/A

300

N/A

POST /enrollments/{enrollmentId}/risk-signals

Alta

1500

15

N/A

300

N/A

POST /consents/{consentId}/authorise

Alta

1500

15

N/A

300

N/A

POST /recurring-consents/{recurringConsentId}/authorise

Alta

1500

15

N/A

300

N/A

## Portabilidade de Crédito

### \[PC\] - API Portabilidade de Crédito

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

GET /credit-operations/{contractId}/portability-eligibility

Alta

1500

15

NA

300

NA

POST / portabilities

Média

2000

15

NA

300

NA

GET /portabilities/{portabilityId}

Alta

1500

15

NA

300

NA

PATCH /portabilities/{portabilityId}/cancel

Média

2000

15

NA

300

NA

GET /account-data

Baixa

4000

15

NA

300

NA

POST /portabilities/{portability}/payment

Média

2000

15

NA

300

NA

## Webhook

### Webhook - Todas as APIs

**Endpoint**

**Frequência**

**SLA (ms)\***

**Timeout (s)**

**TPM**

**TPS**

**Limite Operacional**

**(consultas/mês)**

POST ​/payments/\[Versão da API\]/consents/{consentId}

Alta

1500

15

NA

300

NA

POST ​/payments/\[Versão da API\]/pix/payments/{paymentId}

Alta

1500

15

NA

300

NA

POST ​/automatic-payments/\[Versão da API\]/pix/recurring-payments/{recurringPaymentId}

Alta

1500

15

NA

300

NA

POST ​/automatic-payments/\[Versão da API\]/recurring-consents/{recurringConsentId}

Alta

1500

15

NA

300

NA

POST ​/enrollments/\[Versão da API\]/enrollments/{enrollmentId}

Alta

1500

15

NA

300

NA

**Legenda**  
NA - Não se aplica

-   \- Percentil 95
