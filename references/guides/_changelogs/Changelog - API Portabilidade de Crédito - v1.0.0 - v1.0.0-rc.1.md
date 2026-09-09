# Changelog - API Portabilidade de Crédito - v1.0.0 - v1.0.0-rc.1

## GET /credit-operations/{contractId}/portability-eligibility

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/portability/companyName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/portability/companyCnpj

Alterado - "description"

Alteração

Número completo do CNPJ da instituição O CNPJ corresponde ao número de inscrição no Cadastro de Pessoa Jurídica. Deve-se ter apena...

Número completo do CNPJ da instituição O CNPJ corresponde ao número de inscrição no Cadastro de Pessoa Jurídica. Deve-se ter apena...

## POST /portabilities

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/institution/creditor/companyName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/institution/proposing/companyName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/proposedContract/amortizationScheduledAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/proposedContract/contractedFees/items/feeCode

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/proposedContract/contractedFees/items/feeName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/proposedContract/contractedFinanceCharges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/proposedContract/interestRates/items/additionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

post/requestBody/data/proposedContract/interestRates/items/referentialRateIndexerAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

## GET /portabilities/{portabilityId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/institution/creditor/companyName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/institution/proposing/companyName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/proposedContract/amortizationScheduledAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/proposedContract/contractedFees/items/feeCode

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/proposedContract/contractedFees/items/feeName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/proposedContract/contractedFinanceCharges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/proposedContract/interestRates/items/additionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/proposedContract/interestRates/items/referentialRateIndexerAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/rejection/reason/typeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

get/responses/200/data/statusReason/reasonTypeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

## GET /portabilities/{portabilityId}/account-data

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/strCode/name

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

## PATCH /portabilities/{portabilityId}/cancel

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/reason/typeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/reason/typeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

## POST /portabilities/{portabilityId}/payment

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/transactionId

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/202/data/transactionId

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](?:.\*\[^\\s\])?$
