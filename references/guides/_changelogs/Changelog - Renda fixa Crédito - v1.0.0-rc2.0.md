# Changelog - Renda fixa Crédito - v1.0.0-rc2.0

GET /investments

**Campo**

**O que foi alterado?**

get/security/0

Alteração os security definitions

get/parameters/page-size

Alterado - "description"

get/parameters/page-size

Alterado - "minimum"

GET /investments/{investmentId}

**Campo**

**O que foi alterado?**

get/security/0

Alteração os security definitions

get/responses/200/data/debtorCnpjNumber

Alterado - "description"

get/responses/200/data/debtorName

Alterado - "description"

get/responses/200/data/isinCode

Alterado - "description"

get/responses/200/data/clearingCode

Alterado - "description"

GET /investments/{investmentId}/balances

**Campo**

**O que foi alterado?**

get/security/0

Alteração os security definitions

get/responses/200/data/postFixedIndexerPercentage

Alterado - "description"

get/responses/200/data/preFixedRate

Alterado - "description"

get/responses/200/data/incomeTax

Alterado - "description"

get/responses/200/data/financialTransactionTax

Alterado - "description"

get/responses/200/data/latePayment

Alterado - "description"

get/responses/200/data/fine

Alterado - "description"

get/responses/200/data/latePayment

Mandatoriedade - “opcional“

get/responses/200/data/fine

Mandatoriedade - “opcional“

GET /investments/{investmentId}/transactions

**Campo**

**O que foi alterado?**

get/description

Alterado - "description"

get/sumary

Alterado - "sumary"

get/responses/200/data/items/typeAdditionalInfo

Alterado - "description"

get/responses/200/data/items/properties

Substituir termo “typeAdditionalInfo” por “trasactionTypeAdditionalInfo”

get/security/0

Alteração os security definitions

get/parameters/page-size

Alterado - "description"

get/parameters/page-size

Alterado - "minimum"

get/responses/200/data/items/transactionQuantity

Alterado - "description"

get/responses/200/data/items/transactionUnitPrice

Alterado - "description"

get/responses/200/data/items/type

Alterado - "description"

GET /investments/{investmentId}/transactions-current

**Campo**

**O que foi alterado?**

get/description

Alterado - "description"

get/sumary

Alterado - "sumary"

get/responses/200/data/items/typeAdditionalInfo

Alterado - "description"

get/responses/200/data/items/properties

Substituir termo “typeAdditionalInfo” por “trasactionTypeAdditionalInfo”

get/security/0

Alteração os security definitions

get/parameters/page-size

Alterado - "description"

get/parameters/page-size

Alterado - "minimum"

get/responses/200/data/items/transactionQuantity

Alterado - "description"

get/responses/200/data/items/transactionUnitPrice

Alterado - "description"

get/responses/200/data/items/type

Alterado - "description"
