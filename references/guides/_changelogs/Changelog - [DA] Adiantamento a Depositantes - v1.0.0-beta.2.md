# Changelog - [DA] Adiantamento a Depositantes - v1.0.0-beta.2

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

description

description

title

title

GET /personals-unarranged-account-overdraft

**Campo**

**O que foi alterado?**

get/responses/200/data

Adicionado - "minItems"

get/responses/200/data/items/fees/priorityServices/items/chargingTriggerInfo

pattern

get/responses/200/data/items/fees/priorityServices/items/maximum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/priorityServices/items/maximum/value

Adicionado - "minLength"

get/responses/200/data/items/fees/priorityServices/items/minimum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/priorityServices/items/minimum/value

Adicionado - "minLength"

get/responses/200/data/items/fees/priorityServices/items/prices/items/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/priorityServices/items/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/name

Mandatoriedade

get/responses/200/data/items/participant/properties

Removido - "personalUnarrangedAccountOverdraft"

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/termsConditions

pattern

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/400//errors/items/code

pattern

get/responses/400//errors/items/detail

pattern

get/responses/400//errors/items/title

pattern

get/responses/404//errors/items/code

pattern

get/responses/404//errors/items/detail

pattern

get/responses/404//errors/items/title

pattern

get/responses/405//errors/items/code

pattern

get/responses/405//errors/items/detail

pattern

get/responses/405//errors/items/title

pattern

get/responses/429//errors/items/code

pattern

get/responses/429//errors/items/detail

pattern

get/responses/429//errors/items/title

pattern

get/responses/500//errors/items/code

pattern

get/responses/500//errors/items/detail

pattern

get/responses/500//errors/items/title

pattern

get/responses/504//errors/items/code

pattern

get/responses/504//errors/items/detail

pattern

get/responses/504//errors/items/title

pattern

get/responses/529//errors/items/code

pattern

get/responses/529//errors/items/detail

pattern

get/responses/529//errors/items/title

pattern

get/responses/default//errors/items/code

pattern

get/responses/default//errors/items/detail

pattern

get/responses/default//errors/items/title

pattern

get/responses/data/participant/brand

Adicionado - "x-regulatory-required"

get/responses/data/participant/name

Adicionado - "x-regulatory-required"

get/responses/data/participant/cnpjNumber

Adicionado - "x-regulatory-required"

get/responses/data/participant/urlComplementaryList

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/name

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/code

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/chargingTriggerInfo

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/prices/interval

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/prices/value

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/prices/currency

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/prices/customers

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/prices/customers/rate

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/minimum/value

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/minimum/currency

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/maximum/value

Adicionado - "x-regulatory-required"

get/responses/data/fees/priorityServices/maximum/currency

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/referentialRateIndexer

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/rate

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/applications/interval

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/applications/indexer

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/applications/indexer/rate

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/applications/customers

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/applications/customers/rate

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/minimumRate

Adicionado - "x-regulatory-required"

get/responses/data/interestRates/maximumRate

Adicionado - "x-regulatory-required"

get/responses/data/termsConditions

Adicionado - "x-regulatory-required"

data/fees/priorityServices\[\]/name​

Adicionado - exemplo

data/fees/priorityServices\[\]/code​

Adicionado - exemplo

data/fees/priorityServices\[\]/chargingTriggerInfo​

Adicionado - exemplo

data/interestRates\[\]/applications\[\]/interval​

Adicionado - exemplo

data/interestRates\[\]/minimumRate​

Adicionado - exemplo

data/interestRates\[\]/maximumRate​

Adicionado - exemplo

links/prev​

Adicionado - exemplo

links/next​

Adicionado - exemplo

get/responses/200/data

Adicionado - "description"

get/responses/200/data/items/fees

description

get/responses/200/data/items/fees/priorityServices/items/prices/items/customers

Adicionado - "description"

get/responses/200/data/items/interestRates/items/applications/items/customers

Adicionado - "description"

get/responses/200/data/items/participant

Adicionado - "description"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords

GET /business-unarranged-account-overdraft

**Campo**

**O que foi alterado?**

get/responses/200/data

Adicionado - "minItems"

get/responses/200/data/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/items/fees/services/items/maximum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/maximum/value

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/minimum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/minimum/value

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/prices/items/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/name

Mandatoriedade

get/responses/200/data/items/participant/properties

Removido - "personalUnarrangedAccountOverdraft"

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/termsConditions

pattern

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/400//errors/items/code

pattern

get/responses/400//errors/items/detail

pattern

get/responses/400//errors/items/title

pattern

get/responses/404//errors/items/code

pattern

get/responses/404//errors/items/detail

pattern

get/responses/404//errors/items/title

pattern

get/responses/405//errors/items/code

pattern

get/responses/405//errors/items/detail

pattern

get/responses/405//errors/items/title

pattern

get/responses/429//errors/items/code

pattern

get/responses/429//errors/items/detail

pattern

get/responses/429//errors/items/title

pattern

get/responses/500//errors/items/code

pattern

get/responses/500//errors/items/detail

pattern

get/responses/500//errors/items/title

pattern

get/responses/504//errors/items/code

pattern

get/responses/504//errors/items/detail

pattern

get/responses/504//errors/items/title

pattern

get/responses/529//errors/items/code

pattern

get/responses/529//errors/items/detail

pattern

get/responses/529//errors/items/title

pattern

get/responses/default//errors/items/code

pattern

get/responses/default//errors/items/detail

pattern

get/responses/default//errors/items/title

pattern

get/responses/200/data/participant/brand

Adicionado - "x-regulatory-required"

get/responses/200/data/participant/name

Adicionado - "x-regulatory-required"

get/responses/200/data/participant/cnpjNumber

Adicionado - "x-regulatory-required"

get/responses/200/data/participant/urlComplementaryList

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/name

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/code

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/chargingTriggerInfo

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/prices/interval

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/prices/value

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/prices/currency

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/prices/customers

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/prices/customers/rate

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/minimum/value

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/minimum/currency

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/maximum/value

Adicionado - "x-regulatory-required"

get/responses/200/data/fees/services/maximum/currency

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/referentialRateIndexer

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/rate

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/applications/interval

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/applications/indexer

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/applications/indexer/rate

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/applications/customers

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/applications/customers/rate

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/minimumRate

Adicionado - "x-regulatory-required"

get/responses/200/data/interestRates/maximumRate

Adicionado - "x-regulatory-required"

get/responses/200/data/termsConditions

Adicionado - "x-regulatory-required"

data/fees/priorityServices\[\]/name​

Adicionado - exemplo

data/fees/priorityServices\[\]/code​

Adicionado - exemplo

data/fees/priorityServices\[\]/chargingTriggerInfo​

Adicionado - exemplo

data/interestRates\[\]/applications\[\]/interval​

Adicionado - exemplo

data/interestRates\[\]/minimumRate​

Adicionado - exemplo

data/interestRates\[\]/maximumRate​

Adicionado - exemplo

links/prev​

Adicionado - exemplo

links/next​

Adicionado - exemplo

get/responses/200/data

Adicionado - "description"

get/responses/200/data/items/fees

description

get/responses/200/data/items/fees/services/items/prices/items/customers

Adicionado - "description"

get/responses/200/data/items/interestRates/items/applications/items/customers

Adicionado - "description"

get/responses/200/data/items/participant

Adicionado - "description"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords
