# Changelog - [DC] Renda fixa Bancária - v1.1.0 - v1.1.0-beta.1

## GET /investments/{investmentId}/balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/quantity

Alterado - "maxLength"

Alteração

24

26

get/responses/200/data/quantity

Alterado - "pattern"

Alteração

^\\d{1,15}\\.\\d{2,8}$

^\\d{1,15}\\.\\d{2,10}$

get/responses/200/data/updatedUnitPrice/amount

Alterado - "maxLength"

Alteração

24

26

get/responses/200/data/updatedUnitPrice/amount

Alterado - "pattern"

Alteração

^\\d{1,15}\\.\\d{2,8}$

^\\d{1,15}\\.\\d{2,10}$

## GET /investments/{investmentId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/financialTransactionTax

Alterado - "description"

Alteração

Valor do IOF recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o campo 'type' for...

Valor do IOF recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório para os produtos aos quais essa taxa se aplic...

get/responses/200/data/items/incomeTax

Alterado - "description"

Alteração

Valor do imposto de renda recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o cam...

Valor do imposto de renda recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório para os produtos aos quais essa ...

get/responses/200/data/items/transactionUnitPrice

Alterado - "description"

Alteração

Preço unitário bruto negociado nas transferências de custódia, quando o PU original (da instituição de origem) não estiver dispo...

Preço unitário bruto negociado na transação. Para os casos de \`transactionType\` definido como \`TRANSFERENCIA\_CUSTODIA\`, quando o...

## GET /investments/{investmentId}/transactions-current

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/financialTransactionTax

Alterado - "description"

Alteração

Valor do IOF recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o campo 'type' for...

Valor do IOF recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório para os produtos aos quais essa taxa se aplic...

get/responses/200/data/items/incomeTax

Alterado - "description"

Alteração

Valor do imposto de renda recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o cam...

Valor do imposto de renda recolhido na transação. \[Restrição\] Campo de preenchimento obrigatório para os produtos aos quais essa ...

get/responses/200/data/items/transactionUnitPrice

Alterado - "description"

Alteração

Preço unitário bruto negociado nas transferências de custódia, quando o PU original (da instituição de origem) não estiver dispo...

Preço unitário bruto negociado na transação. Para os casos de \`transactionType\` definido como \`TRANSFERENCIA\_CUSTODIA\`, quando o...
