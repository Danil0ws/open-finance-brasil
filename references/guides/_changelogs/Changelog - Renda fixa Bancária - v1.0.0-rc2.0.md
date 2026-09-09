# Changelog - Renda fixa Bancária - v1.0.0-rc2.0

GET /investments

**Campo**

**O que foi alterado?**

get/security/0

Adicionado - "OAuth2AuthorizationCode"

get/security/0

Removido - "OAuth2Security"

get/security/0

Removido - "OpenId"

get/parameters/page-size

Alterado - "description"

get/parameters/page-size

Alterado - "minimum"

GET /investments/{investmentId}

**Campo**

**O que foi alterado?**

get/security/0

Adicionado - "OAuth2AuthorizationCode"

get/security/0

Removido - "OAuth2Security"

get/security/0

Removido - "OpenId"

GET /investments/{investmentId}/balances

**Campo**

**O que foi alterado?**

get/security/0

Adicionado - "OAuth2AuthorizationCode"

get/security/0

Removido - "OAuth2Security"

get/security/0

Removido - "OpenId"

get/responses/200/data/financialTransactionTax

Alterado - "description"

get/responses/200/data/incomeTax

Alterado - "description"

get/responses/200/data/postFixedIndexerPercentage

Alterado - "description"

get/responses/200/data/preFixedRate

Alterado - "description"

GET /investments/{investmentId}/transactions

**Campo**

**O que foi alterado?**

get/description

Alterado - "description"

get/sumary

Alterado - "sumary"

get/responses/200/data/items/properties

Substituir termo “typeAdditionalInfo” por “trasactionTypeAdditionalInfo”

get/security/0

Adicionado - "OAuth2AuthorizationCode"

get/security/0

Removido - "OAuth2Security"

get/security/0

Removido - "OpenId"

get/parameters/page-size

Alterado - "description"

get/parameters/page-size

Alterado - "minimum"

get/responses/200/data/items/transactionType

Alterado - "description"

get/responses/200/data/items/transactionType/enum

Adicionado - "AMORTIZACAO"

get/responses/200/data/items/transactionType/enum

Adicionado - "PAGAMENTO\_JUROS"

get/responses/200/data/items/transactionType/enum

Removido - "PAGAMENTO\_JUROS\_AMORTIZACAO"

get/responses/200/data/items/type

Alterado - "description"

GET /investments/{investmentId}/transactions-current

**Campo**

**O que foi alterado?**

get/description

Alterado - "description"

get/sumary

Alterado - "sumary"

get/responses/200/data/items/properties

Substituir termo “typeAdditionalInfo” por “trasactionTypeAdditionalInfo”

get/security/0

Adicionado - "OAuth2AuthorizationCode"

get/security/0

Removido - "OAuth2Security"

get/security/0

Removido - "OpenId"

get/parameters/page-size

Alterado - "description"

get/parameters/page-size

Alterado - "minimum"

get/responses/200/data/items/transactionType

Alterado - "description"

get/responses/200/data/items/transactionType/enum

Adicionado - "AMORTIZACAO"

get/responses/200/data/items/transactionType/enum

Adicionado - "PAGAMENTO\_JUROS"

get/responses/200/data/items/transactionType/enum

Removido - "PAGAMENTO\_JUROS\_AMORTIZACAO"

get/responses/200/data/items/type

Alterado - "description"
