# Changelog - API Portabilidade de Crédito - v1.1.0-rc.1 - v1.0.0

## GET /credit-operations/{contractId}/portability-eligibility

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/portability/isEligible

Alterado - "description"

Alteração

Sinaliza se as características do contrato é elegível para pedido de portabilidade de crédito via OFB (sem considerar a disponibilidade da portabilidade de crédito)

Sinaliza se as características do contrato é elegível para pedido de portabilidade de crédito via OFB (sem considerar a disponibilidade da portabilidade de crédito)

Caso o contrato esteja classificado no CADOC 3040 como Domínio 02 Empréstimos  Sub Domínio 03 Crédito Pessoal Sem Consignação e não exista nenhum outro bloqueio que impeça a portabilidade (pela registradora ou OFB), deve informar \`TRUE\`;​

Caso contrário deve informar \`FALSE\`​  

## POST /portabilities

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'totalNumberOfInstalments'

Adição

required

post/requestBody/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'instalmentAmount'

Adição

required

post/requestBody/data/proposedContract/properties

Removido obrigatóriedade no campo 'totalNumberOfInstallments'

Remoção

required

post/requestBody/data/proposedContract/properties

Removido obrigatóriedade no campo 'installmentAmount'

Remoção

required

post/requestBody/data/proposedContract/properties

Removido - "totalNumberOfInstallments"

Remoção

post/requestBody/data/proposedContract/properties

Removido - "installmentAmount"

Remoção

post/requestBody/data/proposedContract/properties

Adicionado - "totalNumberOfInstalments"

Adição

post/requestBody/data/proposedContract/properties

Adicionado - "instalmentAmount"

Adição

## GET /portabilities/{portabilityId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'totalNumberOfInstalments'

Adição

required

get/responses/200/data/proposedContract/properties

Removido obrigatóriedade no campo 'totalNumberOfInstallments'

Remoção

required

get/responses/200/data/proposedContract/properties

Removido - "totalNumberOfInstallments"

Remoção

get/responses/200/data/proposedContract/properties

Removido - "installmentAmount"

Remoção

get/responses/200/data/proposedContract/properties

Adicionado - "totalNumberOfInstalments"

Adição

get/responses/200/data/proposedContract/properties

Adicionado - "instalmentAmount"

Adição
