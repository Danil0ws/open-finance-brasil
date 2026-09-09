# Changelog - API Portabilidade de Crédito - v1.0.0-rc.1 - v1.0.0-beta.3

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

A API de Portabilidade de Crédito permite que usuários transfiram suas operações de crédito e arrendamento mercantil entre institu...

A API de Portabilidade de Crédito permite que usuários transfiram suas operações de crédito e arrendamento mercantil entre institu...

## POST /portabilities

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'contractAmount'

Adição

required

post/requestBody/data/proposedContract/properties

Adicionado - "contractAmount"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/202/data/properties

Adicionado obrigatóriedade no campo 'portabilityId'

Adição

required

post/responses/202/data/portabilityId

Alterado - "maxLength"

Alteração

100

36

post/responses/202/data/portabilityId

Alterado - "minLength"

Alteração

1

36

## GET /portabilities/{portabilityId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/portabilityId

Alterado - "maxLength"

Alteração

100

36

get/parameters/portabilityId

Adicionado - "minLength"

Adição

36

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/portabilityId

Alterado - "maxLength"

Alteração

100

36

get/responses/200/data/portabilityId

Alterado - "minLength"

Alteração

1

36

get/responses/200/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'contractAmount'

Adição

required

get/responses/200/data/proposedContract/properties

Adicionado - "contractAmount"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/portabilityId

Alterado - "maxLength"

Alteração

100

36

get/responses/200/data/portabilityId

Alterado - "minLength"

Alteração

1

36

get/responses/200/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'contractAmount'

Adição

required

get/responses/200/data/proposedContract/properties

Adicionado - "contractAmount"

Adição

## GET /portabilities/{portabilityId}/account-data

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/portabilityId

Alterado - "maxLength"

Alteração

100

36

get/parameters/portabilityId

Adicionado - "minLength"

Adição

36

## PATCH /portabilities/{portabilityId}/cancel

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/parameters/portabilityId

Alterado - "maxLength"

Alteração

100

36

patch/parameters/portabilityId

Adicionado - "minLength"

Adição

36

## POST /portabilities/{portabilityId}/payment

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/portabilityId

Alterado - "maxLength"

Alteração

100

36

post/parameters/portabilityId

Adicionado - "minLength"

Adição

36

post/requestBody/data/portabilityId

Alterado - "maxLength"

Alteração

100

36

post/requestBody/data/portabilityId

Alterado - "minLength"

Alteração

1

36

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/202/data/portabilityId

Alterado - "maxLength"

Alteração

100

36

post/responses/202/data/portabilityId

Alterado - "minLength"

Alteração

1

36
