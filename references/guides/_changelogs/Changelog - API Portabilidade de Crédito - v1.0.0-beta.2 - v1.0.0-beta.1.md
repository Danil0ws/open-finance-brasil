# Changelog - API Portabilidade de Crédito - v1.0.0-beta.2 - v1.0.0-beta.1

## GET /account-data

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses

Removido - "423"

Remoção

get/responses

Removido - "429"

Remoção

get/responses/200/data/strCode/properties

Adicionado obrigatóriedade no campo 'hasFinancialAgent'

Adição

required

get/responses/200/data/strCode/properties

Removido obrigatóriedade no campo 'hasfinancialAgent'

Remoção

required

get/responses/200/data/strCode/properties

Removido obrigatóriedade no campo 'accountNumber'

Remoção

required

get/responses/200/data/strCode/properties

Removido - "hasfinancialAgent"

Remoção

get/responses/200/data/strCode/properties

Adicionado - "hasFinancialAgent"

Adição

get/responses/400/errors

Alterado - "minItems"

Alteração

1

get/responses/401/errors

Alterado - "minItems"

Alteração

1

get/responses/403/errors

Alterado - "minItems"

Alteração

1

get/responses/404/errors

Alterado - "minItems"

Alteração

1

get/responses/405/errors

Alterado - "minItems"

Alteração

1

get/responses/406/errors

Alterado - "minItems"

Alteração

1

get/responses/422/errors

Alterado - "minItems"

Alteração

1

get/responses/500/errors

Alterado - "minItems"

Alteração

1

get/responses/504/errors

Alterado - "minItems"

Alteração

1

get/responses/529/errors

Alterado - "minItems"

Alteração

1

get/responses/default/errors

Alterado - "minItems"

Alteração

1

## GET /credit-operations/{contractId}/portability-eligibility

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses

Removido - "423"

Remoção

get/responses

Removido - "429"

Remoção

get/responses/400/errors

Alterado - "minItems"

Alteração

1

get/responses/401/errors

Alterado - "minItems"

Alteração

1

get/responses/403/errors

Alterado - "minItems"

Alteração

1

get/responses/404/errors

Alterado - "minItems"

Alteração

1

get/responses/405/errors

Alterado - "minItems"

Alteração

1

get/responses/406/errors

Alterado - "minItems"

Alteração

1

get/responses/422/errors

Alterado - "minItems"

Alteração

1

get/responses/500/errors

Alterado - "minItems"

Alteração

1

get/responses/504/errors

Alterado - "minItems"

Alteração

1

get/responses/529/errors

Alterado - "minItems"

Alteração

1

get/responses/default/errors

Alterado - "minItems"

Alteração

1

## POST /portabilities

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters

Adicionado - "x-idempotency-key"

Adição

post/requestBody/data/customerContact

Alterado - "minItems"

Alteração

1

post/requestBody/data/proposedContract/interestRates/items/properties

Removido - "EnumContractReferentialRateIndexerSubType"

Remoção

post/requestBody/data/proposedContract/interestRates/items/referentialRateIndexerSubType

Adicionado - "example"

Adição

TJLP

post/requestBody/data/proposedContract/interestRates/items/referentialRateIndexerSubType/enum

Adicionado - "OUTROS\_INDEXADORES"

Adição

enum

post/requestBody/data/proposedContract/interestRates/items/referentialRateIndexerSubType/enum

Removido - "OUTROS\_INDE"

Remoção

enum

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "423"

Remoção

post/responses

Removido - "429"

Remoção

post/responses/202/data/properties

Removido obrigatóriedade no campo 'contractId'

Remoção

required

post/responses/202/data/properties

Removido obrigatóriedade no campo 'contractNumber'

Remoção

required

post/responses/202/data/properties

Removido obrigatóriedade no campo 'ipocCode'

Remoção

required

post/responses/202/data/properties

Removido obrigatóriedade no campo 'portability'

Remoção

required

post/responses/202/data/properties

Removido obrigatóriedade no campo 'productType'

Remoção

required

post/responses/202/data/properties

Removido obrigatóriedade no campo 'productSubType'

Remoção

required

post/responses/202/data/status/enum

Adicionado - "CANCELLED"

Adição

enum

post/responses/202/data/status/enum

Removido - "CANCELED"

Remoção

enum

post/responses/400/errors

Alterado - "minItems"

Alteração

1

post/responses/401/errors

Alterado - "minItems"

Alteração

1

post/responses/403/errors

Alterado - "minItems"

Alteração

1

post/responses/404/errors

Alterado - "minItems"

Alteração

1

post/responses/405/errors

Alterado - "minItems"

Alteração

1

post/responses/406/errors

Alterado - "minItems"

Alteração

1

post/responses/422/errors

Alterado - "minItems"

Alteração

1

post/responses/500/errors

Alterado - "minItems"

Alteração

1

post/responses/504/errors

Alterado - "minItems"

Alteração

1

post/responses/529/errors

Alterado - "minItems"

Alteração

1

post/responses/default/errors

Alterado - "minItems"

Alteração

1

## GET /portabilities/{portabilityId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses

Removido - "423"

Remoção

get/responses

Removido - "429"

Remoção

get/responses/200/data/contractIdentification/properties

Removido obrigatóriedade no campo 'contractDate'

Remoção

required

get/responses/200/data/contractIdentification/properties

Removido obrigatóriedade no campo 'paidInstallments'

Remoção

required

get/responses/200/data/contractIdentification/properties

Removido obrigatóriedade no campo 'contractOutstandingBalance'

Remoção

required

get/responses/200/data/customerContact

Alterado - "minItems"

Alteração

1

get/responses/200/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'CET'

Adição

required

get/responses/200/data/proposedContract/properties

Removido obrigatóriedade no campo 'cet'

Remoção

required

get/responses/200/data/proposedContract/properties

Removido obrigatóriedade no campo 'installmentPeriodicityAdditionalInfo'

Remoção

required

get/responses/200/data/proposedContract/properties

Removido - "cet"

Remoção

get/responses/200/data/proposedContract/properties

Adicionado - "CET"

Adição

get/responses/200/data/proposedContract/interestRates/items/properties

Removido - "EnumContractReferentialRateIndexerSubType"

Remoção

get/responses/200/data/proposedContract/interestRates/items/referentialRateIndexerSubType

Adicionado - "example"

Adição

TJLP

get/responses/200/data/proposedContract/interestRates/items/referentialRateIndexerSubType/enum

Adicionado - "OUTROS\_INDEXADORES"

Adição

enum

get/responses/200/data/proposedContract/interestRates/items/referentialRateIndexerSubType/enum

Removido - "OUTROS\_INDE"

Remoção

enum

get/responses/200/data/rejection

Alterado - "description"

Alteração

Objeto contendo detalhes do cancelamento do pedido de portabilidade de crédito junto a Instituição Credora. \[RESTRIÇÃO\] Campo de ...

Objeto contendo detalhes do cancelamento do pedido de portabilidade de crédito junto a Instituição Credora. \[RESTRIÇÃO\] Campo de ...

get/responses/200/data/status

Alterado - "description"

Alteração

Informação sobre o status de um pedido de portabilidade de crédito, onde: \`RECEIVED\` - Estado inicial. Indica que o pedido de por...

Informação sobre o status de um pedido de portabilidade de crédito, onde: - RECEIVED: Estado inicial. Indica que o pedido de port...

get/responses/200/data/status/enum

Adicionado - "CANCELLED"

Adição

enum

get/responses/200/data/status/enum

Removido - "CANCELED"

Remoção

enum

get/responses/400/errors

Alterado - "minItems"

Alteração

1

get/responses/401/errors

Alterado - "minItems"

Alteração

1

get/responses/403/errors

Alterado - "minItems"

Alteração

1

get/responses/404/errors

Alterado - "minItems"

Alteração

1

get/responses/405/errors

Alterado - "minItems"

Alteração

1

get/responses/406/errors

Alterado - "minItems"

Alteração

1

get/responses/422/errors

Alterado - "minItems"

Alteração

1

get/responses/500/errors

Alterado - "minItems"

Alteração

1

get/responses/504/errors

Alterado - "minItems"

Alteração

1

get/responses/529/errors

Alterado - "minItems"

Alteração

1

get/responses/default/errors

Alterado - "minItems"

Alteração

1

## PATCH /portabilities/{portabilityId}/cancel

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "operationId"

Alteração

creditPortabilityPostPortabilitiesPortabilityIdCancel

creditPortabilityPatchPortabilitiesPortabilityIdCancel

patch/requestBody/data/reason/typeAdditionalInfo

Alterado - "description"

Alteração

Informação adicional sobre rejeição de portabilidade de crédito. Ao utilizar essa opção, é fortemente recomendável enviar um ticke...

Informação adicional sobre rejeição de portabilidade de crédito. Ao utilizar essa opção, é fortemente recomendável enviar um tick...

patch/requestBody/data/rejectedBy

Alterado - "description"

Alteração

Informar usuário responsável pela rejeição da proposta, onde: \`PROPONETE \` - Indica que o pedido de portabilidade de crédito foi ...

Informar usuário responsável pela rejeição da proposta, onde: \`PROPONENTE \` - Indica que o pedido de portabilidade de crédito foi...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses

Removido - "423"

Remoção

patch/responses

Removido - "429"

Remoção

patch/responses/200/data/reason/typeAdditionalInfo

Alterado - "description"

Alteração

Informação adicional sobre rejeição de portabilidade de crédito. Ao utilizar essa opção, é fortemente recomendável enviar um ticke...

Informação adicional sobre rejeição de portabilidade de crédito. Ao utilizar essa opção, é fortemente recomendável enviar um tick...

patch/responses/200/data/rejectedBy

Alterado - "description"

Alteração

Informar usuário responsável pela rejeição da proposta, onde: \`PROPONETE \` - Indica que o pedido de portabilidade de crédito foi ...

Informar usuário responsável pela rejeição da proposta, onde: \`PROPONENTE \` - Indica que o pedido de portabilidade de crédito foi...

patch/responses/400/errors

Alterado - "minItems"

Alteração

1

patch/responses/401/errors

Alterado - "minItems"

Alteração

1

patch/responses/403/errors

Alterado - "minItems"

Alteração

1

patch/responses/404/errors

Alterado - "minItems"

Alteração

1

patch/responses/405/errors

Alterado - "minItems"

Alteração

1

patch/responses/406/errors

Alterado - "minItems"

Alteração

1

patch/responses/422/errors

Alterado - "minItems"

Alteração

1

patch/responses/500/errors

Alterado - "minItems"

Alteração

1

patch/responses/504/errors

Alterado - "minItems"

Alteração

1

patch/responses/529/errors

Alterado - "minItems"

Alteração

1

patch/responses/default/errors

Alterado - "minItems"

Alteração

1

## POST /portabilities/{portabilityId}/payment

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "423"

Remoção

post/responses

Removido - "429"

Remoção

post/responses/400/errors

Alterado - "minItems"

Alteração

1

post/responses/401/errors

Alterado - "minItems"

Alteração

1

post/responses/403/errors

Alterado - "minItems"

Alteração

1

post/responses/404/errors

Alterado - "minItems"

Alteração

1

post/responses/405/errors

Alterado - "minItems"

Alteração

1

post/responses/406/errors

Alterado - "minItems"

Alteração

1

post/responses/422/errors

Alterado - "minItems"

Alteração

1

post/responses/500/errors

Alterado - "minItems"

Alteração

1

post/responses/504/errors

Alterado - "minItems"

Alteração

1

post/responses/529/errors

Alterado - "minItems"

Alteração

1

post/responses/default/errors

Alterado - "minItems"

Alteração

1
