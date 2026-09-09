# Changelog - [DA] Contas - v1.0.0-beta.1

Esta é a primeira versão da API e não há base de comparação com versões anteriores, motivo pelo qual a página de changelog está vazia.

No entanto, esta API é derivada da API de Produtos e Serviços, cujo histórico está acessível no link a seguir: API - Produtos e Serviços

GET /personals-accounts

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

get/responses/200/data/brand/companies/items/personalAccounts/items/additionalInfo

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/code

Adicionado - "pattern"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/name

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/otherServices/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/fees/priorityServices/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/incomeRate/prepaidPaymentAccount

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/incomeRate/prepaidPaymentAccount

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/incomeRate/prepaidPaymentAccount

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/incomeRate/savingAccount

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/incomeRate/savingAccount

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/incomeRate/savingAccount

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/properties

Removido resquicio - "incomeRates"

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles

mandatoriedade

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles

description

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/name

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/prices/items/monthlyFee

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/services

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/serviceBundles/items/services/items/code

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/termsConditions/closingProcessInfo

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/termsConditions/elegibilityCriteriaInfo

pattern

get/responses/200/data/brand/companies/items/personalAccounts/items/termsConditions/minimumBalance/value

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

get/responses/200/data/brand/companies/personalAccounts/type

Caminho

get/responses/200/data/brand/companies/personalAccounts/fees

Caminho

get/responses/200/data/brand/companies/personalAccounts/serviceBundles

Caminho

get/responses/200/data/brand/companies/personalAccounts/openingClosingChannels

Caminho

get/responses/200/data/brand/companies/personalAccounts/additionalInfo

Caminho

get/responses/200/data/brand/companies/personalAccounts/transactionMethods

Caminho

get/responses/200/data/brand/companies/personalAccounts/termsConditions

Caminho

get/responses/200/data/brand/companies/personalAccounts/incomeRate

Caminho

get/responses/200/data/items/fees/otherServices/items/prices/items/value

Descrição

get/responses/200/data/items/fees/otherServices/items/minimum/value

Descrição

get/responses/200/data/items/fees/otherServices/items/maximum/value

Descrição

get/responses/200/data/items/serviceBundles/items/prices/items/monthlyFee

Descrição

get/responses/200/data/items/serviceBundles/items/minimum/value

Descrição

get/responses/200/data/items/serviceBundles/items/maximum/value

Descrição

/data/brand/companies\[\]/personalAccounts\[\]/additionalInfo​

MaxLength

/data/brand/companies\[\]/personalAccounts\[\]/additionalInfo​

Example

/data/brand/companies\[\]/personalAccounts\[\]/additionalInfo​

Descrição

/data/brand/companies\[\]/personalAccounts\[\]/additionalInfo​

modificado para openingClosingChannelsAdditionalInfo

get/responses/200/data/items/serviceBundles

Descrição

get/responses/200/data/items/incomeRate/savingAccount

Descrição

GET /business-accounts

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

get/responses/200/data/brand/companies/items/businessAccounts/items/additionalInfo

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/code

Adicionado - "pattern"

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/name

Adicionado - "pattern"

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/fees/services/items/prices/items/value

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/incomeRate/prepaidPaymentAccount

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/incomeRate/prepaidPaymentAccount

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/incomeRate/prepaidPaymentAccount

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/incomeRate/savingAccount

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/incomeRate/savingAccount

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/incomeRate/savingAccount

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/properties

mandatoriedade

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles

description

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/maximum/value

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/minimum/value

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/name

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/customers/rate

example

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/customers/rate

maxLength

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/customers/rate

Adicionado - "minLength"

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/customers/rate

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/interval

Removido - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/interval

Removido - "minItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/prices/items/monthlyFee

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/services

Adicionado - "maxItems"

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/services/items/chargingTriggerInfo

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/serviceBundles/items/services/items/code

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/termsConditions/closingProcessInfo

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/termsConditions/elegibilityCriteriaInfo

pattern

get/responses/200/data/brand/companies/items/businessAccounts/items/termsConditions/minimumBalance/value

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

get/responses/200/data/brand/companies/businessAccounts/type

Caminho

get/responses/200/data/brand/companies/businessAccounts/fees

Caminho

get/responses/200/data/brand/companies/businesslAccounts/serviceBundles

Caminho

get/responses/200/data/brand/companies/businessAccounts/openingClosingChannels

Caminho

get/responses/200/data/brand/companies/businessAccounts/additionalInfo

Caminho

get/responses/200/data/brand/companies/businessAccounts/transactionMethods

Caminho

get/responses/200/data/brand/companies/businessAccounts/termsConditions

Caminho

get/responses/200/data/brand/companies/businessAccounts/incomeRate

Caminho

get/responses/200/data/items/fees/services/items/prices/items/value

Descrição

get/responses/200/data/items/fees/services/items/minimum/value

Descrição

get/responses/200/data/items/fees/services/items/maximum/value

Descrição

get/responses/200/data/items/serviceBundles/items/prices/items/monthlyFee

Descrição

get/responses/200/data/items/serviceBundles/items/minimum/value

Descrição

get/responses/200/data/items/serviceBundles/items/maximum/value

Descrição

get/responses/200/data/items/properties

Removido resquicio - "incomeRate"

/data/brand/companies\[\]/businessAccounts\[\]/additionalInfo​

MaxLength

/data/brand/companies\[\]/businessAccounts\[\]/additionalInfo​

Example

/data/brand/companies\[\]/businessAccounts\[\]/additionalInfo​

Descrição

/data/brand/companies\[\]/businessAccounts\[\]/additionalInfo​

modificado para openingClosingChannelsAdditionalInfo

get/responses/200/data/items/serviceBundles

Descrição

get/responses/200/data/items/incomeRate/savingAccount

Descrição
