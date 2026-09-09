# Changelog - API Portabilidade de Crédito - v1.0.0-beta.3 - v1.0.0-beta.2

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

post/requestBody/data/institution/creditor/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/institution/proposing/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/proposedContract/digitalSignatureProof/documentId

Alterado - "pattern"

Alteração

^\[0-9a-fA-F\]{8}\\b-\[0-9a-fA-F\]{4}\\b-\[0-9a-fA-F\]{4}\\b-\[0-9a-fA-F\]{4}\\b-\[0-9a-fA-F\]{12}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/requestBody/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'instalmentPeriodicity'

Adição

required

post/requestBody/data/proposedContract/properties

Removido obrigatóriedade no campo 'installmentPeriodicity'

Remoção

required

post/requestBody/data/proposedContract/properties

Removido - "installmentPeriodicity"

Remoção

post/requestBody/data/proposedContract/properties

Adicionado - "instalmentPeriodicity"

Adição

post/requestBody/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'dueDate'

Adição

required

post/requestBody/data/proposedContract/properties

Adicionado - "dueDate"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/202/data/status/enum

Removido - "TECHNICAL\_VALIDATION\_IN\_PROCESS"

Remoção

enum

post/responses/202/data/status/enum

Removido - "ACCEPTED\_SETTLEMENT\_IN\_PROCESS"

Remoção

enum

post/responses/202/data/status/enum

Removido - "ACCEPTED\_SETTLEMENT\_COMPLETED"

Remoção

enum

post/responses/202/data/status/enum

Removido - "PORTABILITY\_COMPLETED"

Remoção

enum

post/responses/202/data/status/enum

Removido - "REJECTED"

Remoção

enum

post/responses/202/data/status/enum

Removido - "ACCEPTED\_WITH\_CHANGE"

Remoção

enum

## GET /portabilities/{portabilityId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/institution/creditor/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/institution/proposing/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/properties

Removido - "receipt"

Remoção

get/responses/200/data/properties

Adicionado - "loanSettlementInstruction"

Adição

get/responses/200/data/proposedContract/properties

Adicionado obrigatóriedade no campo 'instalmentPeriodicity'

Adição

required

get/responses/200/data/proposedContract/properties

Removido obrigatóriedade no campo 'installmentPeriodicity'

Remoção

required

get/responses/200/data/proposedContract/properties

Removido - "installmentPeriodicity"

Remoção

get/responses/200/data/proposedContract/properties

Adicionado - "instalmentPeriodicity"

Adição

get/responses/200/data/status

Alterado - "description"

Alteração

Informação sobre o status de um pedido de portabilidade de crédito, onde: - \`RECEIVED\`: Estado inicial. Indica que o pedido de po...

Informação sobre o status de um pedido de portabilidade de crédito, onde: - \`RECEIVED\`: Estado inicial. Indica que o pedido de po...

get/responses/200/data/status/enum

Adicionado - "ACCEPTED\_SETTLEMENT\_IN\_PROGRESS"

Adição

enum

get/responses/200/data/status/enum

Removido - "ACCEPTED\_SETTLEMENT\_IN\_PROCESS"

Remoção

enum

get/responses/200/data/statusReason/properties

Removido - "paymentIssueDetail"

Remoção

## PATCH /portabilities/{portabilityId}/cancel

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/properties

Adicionado obrigatóriedade no campo 'rejectedBy'

Adição

required

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Adicionado obrigatóriedade no campo 'rejectedBy'

Adição

required

## POST /portabilities/{portabilityId}/payment

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/transactionId

Alterado - "description"

Alteração

Identificador da transação utilizada para Proponente liquidar portabilidade de crédito com a Credora. No contexto de STR0047, uti...

Identificador da transação utilizada para proponente liquidar a portabilidade de crédito com a credora. No contexto da STR0052, u...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/202/data/transactionId

Alterado - "description"

Alteração

Identificador da transação utilizada para Proponente liquidar portabilidade de crédito com a Credora. No contexto de STR0047, uti...

Identificador da transação utilizada para proponente liquidar a portabilidade de crédito com a credora. No contexto da STR0052, u...

## GET /credit-operations/{contractId}/portability-eligibility

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters

Removido - "page"

Remoção

get/parameters

Removido - "page"

Remoção

get/parameters

Removido - "pagination-key"

Remoção

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/portability/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

## GET /portabilities/{portabilityId}/account-data

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

url

Alterado - “url“

Alteração

/account-data

/portabilities/{portabilityId}/account-data

get/parameters

Adicionado - "portabilityId"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/strCode/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/strCode/ispb

Alterado - "type"

Alteração

number

string

get/responses/200/data/strCode/ispb

Alterado - "example"

Alteração

22896431

22896431

get/responses/200/data/strCode/ispb

Adicionado - "pattern"

Adição

^\[0-9A-Z\]{8}$

get/responses/200/data/strCode/ispb

Adicionado - "maxLength"

Adição

8

get/responses/200/data/strCode/ispb

Adicionado - "minLength"

Adição

8
