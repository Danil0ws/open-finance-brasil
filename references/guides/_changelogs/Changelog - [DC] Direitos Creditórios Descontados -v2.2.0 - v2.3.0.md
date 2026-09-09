# Changelog - [DC] Direitos Creditórios Descontados -v2.2.0 - v2.3.0

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /contracts

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/brandName

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/contractedFinanceCharges/items/chargeRate

Alterado - "pattern"

Alteração

^\[01\]\\.\\d{6}$

^\\d{1}\\.\\d{6}$

get/responses/200/data/CET

Alterado - "pattern"

Alteração

^\\d{1,2}\\.\\d{6}$

^\\d{1,6}\\.\\d{6}$

get/responses/200/data/CET

Alterado - maxLength

Alteração

9

13

get/responses/200/data/amortizationScheduledAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/contractedFinanceCharges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/instalmentPeriodicityAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/interestRates/items/additionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/interestRates/items/referentialRateIndexerAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/productName

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

## GET /contracts/{contractId}/warranties

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /contracts/{contractId}/scheduled-instalments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /contracts/{contractId}/payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/releases/items/overParcel/charges/items/chargeAmount

Alterado - "pattern"

Alteração

^\\d{1,15}\\.\\d{2,4}$

^-?\\d{1,15}\\.\\d{2,4}$

get/responses/200/data/releases/items/overParcel/charges/items/chargeAmount

Alterado - "maxLength"

Alteração

20

21

get/responses/200/data/releases/items/paidAmount

Alterado - "pattern"

Alteração

^\\d{1,15}\\.\\d{2,4}$

^-?\\d{1,15}\\.\\d{2,4}$

get/responses/200/data/releases/items/paidAmount

Alterado - "maxLength"

Alteração

20

21

get/responses/200/data/releases/items/instalmentId

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/releases/items/overParcel/charges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$
