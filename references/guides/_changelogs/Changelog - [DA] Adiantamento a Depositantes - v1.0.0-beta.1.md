# Changelog - [DA] Adiantamento a Depositantes - v1.0.0-beta.1

Esta é a primeira versão da API e não há base de comparação com versões anteriores, motivo pelo qual a página de changelog está vazia.

No entanto, esta API é derivada da API de Produtos e Serviços, cujo histórico está acessível no link a seguir: API - Produtos e Serviços

GET /personals-unarranged-account-overdraft

**Campo**

**O que foi alterado?**

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses

Adicionado - "504"

get/responses

Adicionado - "529"

get/responses

Adicionado - "default"

get/responses/200/data/brand/companies

Adicionado - "maxItems"

get/responses/200/data/companies/items/companies/cnpjNumber

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items

example

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/fees/priorityServices/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items

example

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/interestRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/properties

Removido resquicio - "interestRate"

get/responses/200/data/brand/companies/items/personalUnarrangedAccountOverdraft/items/termsConditions

pattern

get/responses/200/data/brand/name

pattern

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

get/responses/200/personalUnarrangedAccountOverdraft/fees/services/prices/value

Descrição

get/responses/200/personalUnarrangedAccountOverdraft/fees/services/minimum/value

Descrição

get/responses/200/personalUnarrangedAccountOverdraft/fees/services/maximum/value

Descrição

get/responses/200/companies/personalUnarrangedAccountOverdraft/fees/priorityServices​

Mandatoriedade

get/responses/200/data

Alterado para array

get/responses/200/data/participant​​

Objeto criado

get/responses/200/data/brand/name​​

Nome e caminho

get/responses/200/data/brand/companies/personalUnarrangedAccountOverdraft

Caminho

get/responses/200/data/brand

Removido

get/responses/200/data/brand/companies

Removido

GET /business-unarranged-account-overdraft

**Campo**

**O que foi alterado?**

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses

Adicionado - "504"

get/responses

Adicionado - "529"

get/responses

Adicionado - "default"

get/responses/200/data/brand/companies

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/cnpjNumber

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items

example

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/fees/services/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items

example

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/interestRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/properties

Removido resquicio - "interestRate"

get/responses/200/data/brand/companies/items/businessUnarrangedAccountOverdraft/items/termsConditions

pattern

get/responses/200/data/brand/name

pattern

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

get/responses/200/businessUnarrangedAccountOverdraft/fees/services/prices/value

Descrição

get/responses/200/businessUnarrangedAccountOverdraft/fees/services/minimum/value

Descrição

get/responses/200/businessUnarrangedAccountOverdraft/fees/services/maximum/value

Descrição

get/responses/200/companies/businessUnarrangedAccountOverdraft/fees/services​

Mandatoriedade

get/responses/200/data

Alterado para array

get/responses/200/data/participant​​

Objeto criado

get/responses/200/data/brand/name​​

Nome e caminho

get/responses/200/data/brand/companies/businessUnarrangedAccountOverdraft

Caminho

get/responses/200/data/brand

Removido

get/responses/200/data/brand/companies

Removido
