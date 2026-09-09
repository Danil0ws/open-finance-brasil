# Changelog - [DC] Cartão de Crédito - v2.4.0-beta.2 - v2.4.0-beta.1

## GET /accounts/{creditCardAccountId}/bills/{billId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/payeeMCC

Alterado - "description"

Alteração

O MCC ou o código da categoria do estabelecimento comercial. Os MCCs são agrupados segundo suas similaridades. O MCC é usado para ...

O MCC ou o código da categoria do estabelecimento comercial. Os MCCs são agrupados segundo suas similaridades. O MCC é usado para ...

et/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora da transação disponível para os clientes nos canais digitais da instituição. Neste momento, é obrigatório preencher c...

Data e hora da transação. Nas compras parceladas, o \`transactionDateTime\` deve ser idêntico em todas as parcelas. O campo deve...

## GET /accounts/{creditCardAccountId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/properties

Adicionado obrigatóriedade no campo 'billForecastDate'

Adição

required

get/responses/200/data/items/properties

Adicionado - "billForecastDate"

Adição

get/responses/200/data/items/payeeMCC

Alterado - "description"

Alteração

O MCC ou o código da categoria do estabelecimento comercial. Os MCCs são agrupados segundo suas similaridades. O MCC é usado para ...

O MCC ou o código da categoria do estabelecimento comercial. Os MCCs são agrupados segundo suas similaridades. O MCC é usado para ...

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora da transação disponível para os clientes nos canais digitais da instituição. Neste momento, é obrigatório preencher c...

Data e hora da transação. Nas compras parceladas, o \`transactionDateTime\` deve ser idêntico em todas as parcelas. O campo deve...

## GET /accounts/{creditCardAccountId}/transactions-current

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/properties

Adicionado obrigatóriedade no campo 'billForecastDate'

Adição

required

get/responses/200/data/items/properties

Adicionado - "billForecastDate"

Adição

get/responses/200/data/items/payeeMCC

Alterado - "description"

Alteração

O MCC ou o código da categoria do estabelecimento comercial. Os MCCs são agrupados segundo suas similaridades. O MCC é usado para ...

O MCC ou o código da categoria do estabelecimento comercial. Os MCCs são agrupados segundo suas similaridades. O MCC é usado para ...

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora da transação disponível para os clientes nos canais digitais da instituição. Neste momento, é obrigatório preencher c...

Data e hora da transação. Nas compras parceladas, o \`transactionDateTime\` deve ser idêntico em todas as parcelas. O campo deve...
