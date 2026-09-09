# Changelog - [DA] Direitos Creditórios Descontados​ - v1.0.0-beta.1

Esta é a primeira versão da API e não há base de comparação com versões anteriores, motivo pelo qual a página de changelog está vazia.

No entanto, esta API é derivada da API de Produtos e Serviços, cujo histórico está acessível no link a seguir: API - Produtos e Serviços

GET /personals-invoice-financings

**Campo**

**O que foi alterado?**

get/responses/200/data/brand/companies

Adicionado - 'maxItems'

get/responses/200/data/brand/companies/cnpjNumber

Alterado - ‘pattern’

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services

Adicionado - 'maxItems'

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services/prices/value

Alterado - ‘pattern’

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services/minimum/value

Alterado - ‘pattern’

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services/maximum/value

Alterado - ‘pattern’

get/responses/200/data/brand/companies/personalInvoiceFinancings/interestRates

Adicionado - 'maxItems'

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

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/code

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/name

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/maximumRate

example

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/minimumRate

example

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/interestRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/personalInvoiceFinancings/items/termsConditions

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

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services/prices/value

Descrição

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services/minimum/value

Descrição

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services/maximum/value

Descrição

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees/services​

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

get/responses/200/data/brand/companies/personalInvoiceFinancings/type

Caminho

get/responses/200/data/brand/companies/personalInvoiceFinancings/fees

Caminho

get/responses/200/data/brand/companies/personalInvoiceFinancings/interestRates

Caminho

get/responses/200/data/brand/companies/personalInvoiceFinancings/requiredWarranties

Caminho

get/responses/200/data/brand/companies/personalInvoiceFinancings/termsConditions

Caminho

get/responses/200/data/items/requiredWarranties/items

description

get/responses/200/data/items/requiredWarranties/items/enum

Removido - "NAO\_APLICAVEL"

get/responses/200/data/items/requiredWarranties/items/enum

Adicionado - "NAO\_EXIGE\_GARANTIA"

GET /business-invoice-financings

**Campo**

**O que foi alterado?**

get/responses/200/data/brand/companies

Adicionado - 'maxItems'

get/responses/200/data/brand/companies/cnpjNumber

Alterado - ‘pattern’

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services

Adicionado - 'maxItems'

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services/prices/value

Alterado - ‘pattern’

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services/minimum/value

Alterado - ‘pattern’

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services/maximum/value

Alterado - ‘pattern’

get/responses/200/data/brand/companies/businessInvoiceFinancings/interestRates

Adicionado - 'maxItems'

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/code

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/name

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/maximumRate

example

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/minimumRate

example

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/interestRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/businessInvoiceFinancings/items/termsConditions

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

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services/prices/value

Descrição

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services/minimum/value

Descrição

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services/maximum/value

Descrição

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees/services​

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

get/responses/200/data/brand/companies/businessInvoiceFinancings/type

Caminho

get/responses/200/data/brand/companies/businessInvoiceFinancings/fees

Caminho

get/responses/200/data/brand/companies/businessInvoiceFinancings/interestRates

Caminho

get/responses/200/data/brand/companies/businessInvoiceFinancings/requiredWarranties

Caminho

get/responses/200/data/brand/companies/businessInvoiceFinancings/termsConditions

Caminho

get/responses/200/data/items/requiredWarranties/items

description

get/responses/200/data/items/requiredWarranties/items/enum

Removido - "NAO\_APLICAVEL"

get/responses/200/data/items/requiredWarranties/items/enum

Adicionado - "NAO\_EXIGE\_GARANTIA"
