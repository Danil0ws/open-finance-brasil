# Changelog - [SV] Pagamentos - v4.0.0-rc.2 - v4.0.0-rc.1

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

OAuth2ClientCredentials

Alterado - “Description”

Alteração

Fluxo OAuth necessário para que a iniciadora possa iniciar pagamentos. Requer o processo de redirecionamento e autenticação do usuário. Apenas pagamentos iniciados pela mesma iniciadora de pagamentos podem ser consultados ou cancelados através de modelo client credentials.

Fluxo OAuth necessário para que a iniciadora possa consultar ou cancelar pagamentos e criar ou consultar consentimentos. Apenas pagamentos e consentimentos iniciados pela mesma iniciadora de pagamentos podem ser consultados ou cancelados através deste modelo.

/info

Alterado - “Description”

Alteração

API de Iniciação de Pagamentos, responsável por viabilizar as operações de iniciação de pagamentos para o Open Finance Brasil. Par...

API de Iniciação de Pagamentos, responsável por viabilizar as operações de iniciação de pagamentos para o Open Finance Brasil. Par...

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/data

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para a iniciação de pagamento.

/data/payment/schedule/daily /startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/Weekly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/monthly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/weekly/dayOfWeek

Adicionado - “description”

Adição

Define o dia da semana planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/dayOfMonth

Adicionado - “description”

Adição

Define o dia do mês planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/quantity

Adicionado - “description”

Adição

Define a quantidade de pagamentos que serão enviados para liquidação.

/data/payment/schedule/custom/dates

Adicionado - “description”

Adição

Define os dias em que estão planejadas as ocorrências das liquidações.

/data/payment/schedule/daily/quantity

Alterado - maximum

Alteração

730

60

/data/payment/schedule/weekly/quantity

Alterado - maximum

Alteração

104

60

/data/payment/schedule/custom/dates

Alterado - MaxItens

Alteração

730

60

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/data

Alterado - "description"

Alteração

Objeto contendo as informações de resposta do consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para a iniciação de pagamento.

/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento da iniciação de pagamento expira, devendo ser sempre o creationDateTime mais 5 minutos. Uma str...

Data e hora em que o consentimento da iniciação de pagamento expira. Para consentimentos em status AWAITING\_AUTHORISATION, deve s...

/data/payment/schedule/daily /startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/Weekly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/monthly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/weekly/dayOfWeek

Adicionado - “description”

Adição

Define o dia da semana planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/dayOfMonth

Adicionado - “description”

Adição

Define o dia do mês planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/quantity

Adicionado - “description”

Adição

Define a quantidade de pagamentos que serão enviados para liquidação.

/data/payment/schedule/custom/dates

Adicionado - “description”

Adição

Define os dias em que estão planejadas as ocorrências das liquidações.

/data/payment/schedule/daily/quantity

Alterado - maximum

Alteração

730

60

/data/payment/schedule/weekly/quantity

Alterado - maximum

Alteração

104

60

/data/payment/schedule/custom/dates

Alterado - MaxItens

Alteração

730

60

## GET /consents/{consentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/data

Alterado - "description"

Alteração

Objeto contendo as informações de resposta do consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para a iniciação de pagamento.

/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento da iniciação de pagamento expira, devendo ser sempre o creationDateTime mais 5 minutos. Uma str...

Data e hora em que o consentimento da iniciação de pagamento expira. Para consentimentos em status AWAITING\_AUTHORISATION, deve s...

/data/payment/schedule/daily /startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/Weekly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/monthly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/weekly/dayOfWeek

Adicionado - “description”

Adição

Define o dia da semana planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/dayOfMonth

Adicionado - “description”

Adição

Define o dia do mês planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/quantity

Adicionado - “description”

Adição

Define a quantidade de pagamentos que serão enviados para liquidação.

/data/payment/schedule/custom/dates

Adicionado - “description”

Adição

Define os dias em que estão planejadas as ocorrências das liquidações.

/data/payment/schedule/daily/quantity

Alterado - maximum

Alteração

730

60

/data/payment/schedule/weekly/quantity

Alterado - maximum

Alteração

104

60

/data/payment/schedule/custom/dates

Alterado - MaxItens

Alteração

730

60

## POST /pix/payments

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /pix/payments/{paymentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## PATCH pix/payments/{paymentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## PATCH pix/payments/consents/{consentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**
