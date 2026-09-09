# Changelog - [DC] Títulos do Tesouro Direto - v1.1.0 - v1.1.0-beta.1

## GET /investments/{investmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/remuneration/postFixedIndexerPercentage

Alterado - "maxLength"

Alteração

9

10

get/responses/200/data/remuneration/postFixedIndexerPercentage

Alterado - "pattern"

Alteração

^-?\\d{1}\\.\\d{6}$

^-?\\d{1,2}\\.\\d{6}$

## GET /investments/{investmentId}/balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/grossAmount

Alterado - "description"

Alteração

Valor do investimento anterior à dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência.

Valor do investimento anterior à dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência. I...

get/responses/200/data/netAmount

Alterado - "description"

Alteração

Valor do investimento posterior a dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência.

Valor do investimento posterior a dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência. ...
