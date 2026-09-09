# Changelog - [DA] Financiamentos - v1.0.0-beta.1

Esta é a primeira versão da API e não há base de comparação com versões anteriores, motivo pelo qual a página de changelog está vazia.

No entanto, esta API é derivada da API de Produtos e Serviços, cujo histórico está acessível no link a seguir: API - Produtos e Serviços

GET /personals-financings

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

Alterado - ‘pattern’

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/code

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/name

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalFinancings/items/fees/services/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications

example

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/maximumRate

example

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/maximumRate

maxLength

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/minimumRate

example

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/minimumRate

maxLength

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalFinancings/items/interestRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/personalFinancings/items/termsConditions

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

get/responses/200/personalFinancings/fees/services/prices/value

Descrição

get/responses/200/personalFinancings/fees/services/minimum/value

Descrição

get/responses/200/personalFinancings/fees/services/maximum/value

Descrição

get/responses/200/companies/personalFinancings/fees/services​

Mandatoriedade

get/responses/200/data

Alterado para array

get/responses/200/data/participant

Adicionado

get/responses/200/data/brand/name

Caminho e nome

get/responses/200/data/companies/name

Caminho

get/responses/200/data/companies/cnpjNumber

Caminho

get/responses/200/data/companies/urlComplementaryList

Caminho

get/responses/200/data/brand/companies/personalFinancings/type

Caminho

get/responses/200/data/brand/companies/personalFinancings/fees

Caminho

get/responses/200/data/brand/companies/personalFinancings/interestRates

Caminho

get/responses/200/data/brand/companies/personalFinancings/termsConditions

Caminho

get/responses/200/data/items/requiredWarranties/items

description

get/responses/200/data/items/requiredWarranties/items/enum

Removido - "NAO\_APLICAVEL"

get/responses/200/data/items/requiredWarranties/items/enum

Adicionado - "NAO\_EXIGE\_GARANTIA"

GET /business-financings

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

Alterado - ‘pattern’

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/code

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/name

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessFinancings/items/fees/services/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications

example

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/maximumRate

example

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/maximumRate

maxLength

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/minimumRate

example

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/minimumRate

maxLength

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessFinancings/items/interestRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/businessFinancings/items/termsConditions

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

get/responses/200/businessFinancings/fees/services/prices/value

Descrição

get/responses/200/businessFinancings/fees/services/minimum/value

Descrição

get/responses/200/businessFinancings/fees/services/maximum/value

Descrição

get/responses/200/companies/businessFinancings/fees/services​

Mandatoriedade

get/responses/200/data

Alterado para array

get/responses/200/data/participant

Adicionado

get/responses/200/data/brand/name

Caminho e nome

get/responses/200/data/companies/name

Caminho

get/responses/200/data/companies/cnpjNumber

Caminho

get/responses/200/data/companies/urlComplementaryList

Caminho

get/responses/200/data/brand/companies/businessFinancings/type

Caminho

get/responses/200/data/brand/companies/businessFinancings/fees

Caminho

get/responses/200/data/brand/companies/businessFinancings/interestRates

Caminho

get/responses/200/data/brand/companies/businessFinancings/termsConditions

Caminho

get/responses/200/data/items/requiredWarranties/items

description

get/responses/200/data/items/requiredWarranties/items/enum

Removido - "NAO\_APLICAVEL"

get/responses/200/data/items/requiredWarranties/items/enum

Adicionado - "NAO\_EXIGE\_GARANTIA"
