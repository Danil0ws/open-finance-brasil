# Changelog - [DC] Cartão de Crédito - v2.3.0 - v2.2.1

## GET /accounts/{creditCardAccountId}/limits

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters

Removido - "pagination-key"

Remoção

## GET /accounts/{creditCardAccountId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/billPostDate

Alterado - "description"

Alteração

Data em que a transação foi inserida na fatura

Data em que a transação foi inserida na fatura. Preencher o campo com a data dummy: 0001-01-01, apenas para os casos nos quais ain...

## GET /accounts/{creditCardAccountId}/transactions-current

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/billPostDate

Alterado - "description"

Alteração

Data em que a transação foi inserida na fatura

Data em que a transação foi inserida na fatura. Preencher o campo com a data dummy: 0001-01-01, apenas para os casos nos quais ain...
