# Changelog - [DC] Empréstimos - v2.4.0 - v2.3.0

none

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

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/amortizationScheduledAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/contractedFees/items/feeCode

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/contractedFees/items/feeName

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/contractedFees/items/feeRate

Alterado - "pattern"

Alteração

^\[01\]\\.\\d{6}$

^\\d{1}\\.\\d{6}$

get/responses/200/data/contractedFinanceCharges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/contractedFinanceCharges/items/chargeRate

Alterado - "pattern"

Alteração

^\[01\]\\.\\d{6}$

^\\d{1}\\.\\d{6}$

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

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /contracts/{contractId}/payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/releases/items/overParcel/charges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

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

get/responses/200/data/releases/items/overParcel/fees/items/feeCode

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/releases/items/overParcel/fees/items/feeName

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

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

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /contracts/{contractId}/scheduled-instalments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /contracts/{contractId}/warranties

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$
