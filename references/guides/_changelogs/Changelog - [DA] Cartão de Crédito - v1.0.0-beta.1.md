# Changelog - [DA] Cartão de Crédito - v1.0.0-beta.1

Esta é a primeira versão da API e não há base de comparação com versões anteriores, motivo pelo qual a página de changelog está vazia.

No entanto, esta API é derivada da API de Produtos e Serviços, cujo histórico está acessível no link a seguir: API - Produtos e Serviços

GET /personals-credit-cards

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

get/responses/200/data/brand/companies/items/personalCreditCards

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalCreditCards/items/fees/services/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/identification/creditCard/additionalInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/identification/creditCard/additionalInfo

Renomeado para - "networkAdditionalInfo"

get/responses/200/data/brand/companies/items/personalCreditCards/items/identification/product/additionalInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/identification/product/additionalInfo

Renomeado para - "typeAdditionalInfo"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/maximumRate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/minimumRate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/rate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/instalmentRates/items/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/otherCredits/items/additionalInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/otherCredits/items/additionalInfo

Renomeado para - "codeAdditionalInfo"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/maximumRate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/minimumRate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/rate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/rate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/rates/items/rate

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/name

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/rewardsProgram/rewardProgramInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/additionalInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/closingProcessInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/elegibilityCriteriaInfo

pattern

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/minimumFeeRate

example

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/minimumFeeRate

maxLength

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/minimumFeeRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalCreditCards/items/termsConditions/minimumFeeRate

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

get/responses/200/personalCreditCards/fees/services/prices/value

Descrição

get/responses/200/personalCreditCards/fees/services/minimum/value

Descrição

get/responses/200/personalCreditCards/fees/services/maximum/value

Descrição

get/responses/200/data/brand/companies/items/personalCreditCards/items/identification/product/typeAdditionalInfo

Descrição

get/responses/200/data/brand/companies/items/personalCreditCards/items/identification/creditCard/networkAdditionalInfo

Descrição

get/responses/200/data/brand/companies/items/personalCreditCards/items/interest/otherCredits/codeAdditionalInfo

Descrição

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

get/responses/200/data/brand/companies/personalCreditCards/name

Caminho

get/responses/200/data/brand/companies/personalCreditCards/identification

Caminho

get/responses/200/data/brand/companies/personalCreditCards/rewardsProgram

Caminho

get/responses/200/data/brand/companies/personalCreditCards/fees

Caminho

get/responses/200/data/brand/companies/personalCreditCards/interest

Caminho

get/responses/200/data/brand/companies/personalCreditCards/termsConditions

Caminho

get/responses/200/data/items/fees/services

Mandatoriedade

GET /business-credit-cards

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

get/responses/200/data/brand/companies/items/businessCreditCards

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessCreditCards/items/fees/services/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/identification/creditCard/additionalInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/identification/creditCard/additionalInfo

Renomeado para - "networkAdditionalInfo"

get/responses/200/data/brand/companies/items/businessCreditCards/items/identification/product/additionalInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/identification/product/additionalInfo

Renomeado para - "typeAdditionalInfo"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/maximumRate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/minimumRate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/rate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/instalmentRates/items/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/otherCredits/items/additionalInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/otherCredits/items/additionalInfo

Renomeado para - "typeAdditionalInfo"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/indexer/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/indexer/rate

maxLength

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/indexer/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/applications/items/indexer/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/maximumRate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/maximumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/maximumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/maximumRate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/minimumRate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/minimumRate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/minimumRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/minimumRate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/rate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/rate

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/rates/items/rate

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/name

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/rewardsProgram/rewardProgramInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/additionalInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/closingProcessInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/elegibilityCriteriaInfo

pattern

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/minimumFeeRate

example

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/minimumFeeRate

maxLength

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/minimumFeeRate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessCreditCards/items/termsConditions/minimumFeeRate

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

get/responses/200/data/brand/companies/items/businessCreditCards/fees/services/prices/value

Descrição

get/responses/200/data/brand/companies/items/businessCreditCards/fees/services/minimum/value

Descrição

get/responses/200/data/brand/companies/items/businessCreditCards/fees/services/maximum/value

Descrição

get/responses/200/data/brand/companies/items/businessCreditCards/items/identification/product/typeAdditionalInfo

Descrição

get/responses/200/data/brand/companies/items/businessCreditCards/items/identification/creditCard/networkAdditionalInfo

Descrição

get/responses/200/data/brand/companies/items/businessCreditCards/items/interest/otherCredits/codeAdditionalInfo

Descrição

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

get/responses/200/data/brand/companies/businessCreditCards/name

Caminho

get/responses/200/data/brand/companies/businessCreditCards/identification

Caminho

get/responses/200/data/brand/companies/businessCreditCards/rewardsProgram

Caminho

get/responses/200/data/brand/companies/businessCreditCards/fees

Caminho

get/responses/200/data/brand/companies/businessCreditCards/interest

Caminho

get/responses/200/data/brand/companies/businessCreditCards/termsConditions

Caminho

get/responses/200/data/items/fees/services

Mandatoriedade
