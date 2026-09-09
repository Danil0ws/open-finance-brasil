# Changelog - [DA] Contas - v1.0.0-beta.2

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

tags/description

Adicionado - Description

GET /personals-accounts

**Campo**

**O que foi alterado?**

get/responses/200/data

minItems

get/responses/200/data/items/fees/otherServices/items/chargingTriggerInfo

pattern

get/responses/200/data/items/fees/otherServices/items/code

pattern

get/responses/200/data/items/fees/otherServices/items/maximum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/otherServices/items/maximum/value

Adicionado - "minLength"

get/responses/200/data/items/fees/otherServices/items/minimum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/otherServices/items/minimum/value

Adicionado - "minLength"

get/responses/200/data/items/fees/otherServices/items/name

pattern

get/responses/200/data/items/fees/otherServices/items/prices/items/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/otherServices/items/prices/items/value

Adicionado - "minLength"

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

get/responses/200/data/items/incomeRate/prepaidPaymentAccount

pattern

get/responses/200/data/items/incomeRate/savingAccount

pattern

get/responses/200/data/items/openingClosingChannelsAdditionalInfo

pattern

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/serviceBundles/items/maximum/currency

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/maximum/value

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/minimum/currency

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/minimum/value

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/name

pattern

get/responses/200/data/items/serviceBundles/items/prices/items/currency

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/services/items/chargingTriggerInfo

example

get/responses/200/data/items/serviceBundles/items/services/items/chargingTriggerInfo

pattern

get/responses/200/data/items/serviceBundles/items/services/items/code

pattern

get/responses/200/data/items/termsConditions/closingProcessInfo

pattern

get/responses/200/data/items/termsConditions/elegibilityCriteriaInfo

pattern

get/responses/200/data/items/termsConditions/minimumBalance/currency

Adicionado - "minLength"

get/responses/200/data/items/termsConditions/minimumBalance/value

Adicionado - "minLength"

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

/data\[\]/participant/brand

Adicionado - "x-regulatory-required"

/data\[\]/participant/name

Adicionado - "x-regulatory-required"

/data\[\]/participant/cnpjNumber

Adicionado - "x-regulatory-required"

/data\[\]/participant/urlComplementaryList

Adicionado - "x-regulatory-required"

/data\[\]/type

Adicionado - "x-regulatory-required"

/data\[\]//fees/priorityServices\[\]/name

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/code

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/chargingTriggerInfo

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/prices

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/prices\[\]/interval

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/prices\[\]/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/prices\[\]/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/prices\[\]/customers

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/prices\[\]/customers/rate

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/minimum

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/minimum/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/minimum/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/maximum

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/maximum/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/priorityServices\[\]/maximum/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/name

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/code

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/chargingTriggerInfo

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/chargingTriggerInfo

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/prices\[\]/interval

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/prices\[\]/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/prices\[\]/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/prices\[\]/customers

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/prices\[\]/customers/rate

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/minimum

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/minimum/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/minimum/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/maximum

Adicionado - "x-regulatory-required"

/data\[\]/fees/otherServices\[\]/maximum/value

Adicionado - "x-regulatory-required"

/data\[\]/otherServices\[\]/maximum/currency

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/name

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/chargingTriggerInfo

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/eventLimitQuantity

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/freeEventQuantity

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/interval

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/monthlyFee

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/currency

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/customers

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/customers/rate

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/minimum/value

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/minimum/currency

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/maximum/value

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/maximum/currency

Adicionado - "x-regulatory-required"

/data\[\]/openingClosingChannels

Adicionado - "x-regulatory-required"

/data\[\]/additionalInfo

Adicionado - "x-regulatory-required"

/data\[\]/transactionMethods

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/minimumBalance

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/minimumBalance/value

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/minimumBalance/currency

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/elegibilityCriteriaInfo

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/closingProcessInfo

Adicionado - "x-regulatory-required"

/data\[\]/incomeRate/savingAccount

Adicionado - "x-regulatory-required"

/data\[\]/incomeRate/prepaidPaymentAccount

Adicionado - "x-regulatory-required"

data/fees/priorityServices\[\]/code​

Adicionado - exemplo

data/incomeRate/savingAccount​

Adicionado - exemplo

links/prev​

Adicionado - exemplo

links/next​

Adicionado - exemplo

get/responses/200/data/

Adicionado - descrição

get/responses/200/data/items/participant

Adicionado - descrição

get/responses/200/data/items/fees

Adicionado - descrição

get/responses/200/data/items/fees/priorityServices\[\]/prices\[\]/customers

Adicionado - descrição

get/responses/200/data/items/fees/otherServices\[\]/prices\[\]/customers

Adicionado - descrição

get/responses/200/data/items/servicesBundles\[\]/prices\[\]/customers

Adicionado - descrição

get/200/links/

Adicionado - descrição

get/200/meta/

Adicionado - descrição

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

GET /business-accounts

**Campo**

**O que foi alterado?**

get/responses/200/data

minItems

get/responses/200/data/items/fees/services/items

pattern

get/responses/200/data/items/fees/services/items/chargingTriggerInfo

pattern

get/responses/200/data/items/fees/services/items/maximum

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/maximum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/minimum

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/minimum/currency

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/minimum/value

pattern

get/responses/200/data/items/fees/services/items/prices/items

Adicionado - "minLength"

get/responses/200/data/items/fees/services/items/prices/items/customers

Adicionado - "minLength"

get/responses/200/data/items/incomeRate

pattern

get/responses/200/data/items/incomeRate/prepaidPaymentAccount

pattern

get/responses/200/data/items/incomeRate/savingAccount

pattern

get/responses/200/data/items/participant

pattern

get/responses/200/data/items/participant/brand

Adicionado - "minLength"

get/responses/200/data/items/participant/cnpjNumber

pattern

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/serviceBundles/items/maximum

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/maximum/currency

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/minimum

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/minimum/currency

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/minimum/value

pattern

get/responses/200/data/items/serviceBundles/items/prices/items

Adicionado - "minLength"

get/responses/200/data/items/serviceBundles/items/services/items

example

get/responses/200/data/items/serviceBundles/items/services/items/chargingTriggerInfo

pattern

get/responses/200/data/items/serviceBundles/items/services/items/chargingTriggerInfo

pattern

get/responses/200/data/items/termsConditions

pattern

get/responses/200/data/items/termsConditions/closingProcessInfo

pattern

get/responses/200/data/items/termsConditions/minimumBalance

Adicionado - "minLength"

get/responses/200/data/items/termsConditions/minimumBalance/currency

Adicionado - "minLength"

get/responses/200/data/items/termsConditions/minimumBalance/value

Adicionado - "minLength"

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

pattern

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

/data\[\]/participant/brand

Adicionado - "x-regulatory-required"

/data\[\]/participant/name

Adicionado - "x-regulatory-required"

/data\[\]/participant/cnpjNumber

Adicionado - "x-regulatory-required"

/data\[\]/participant/urlComplementaryList

Adicionado - "x-regulatory-required"

/data\[\]/type

Adicionado - "x-regulatory-required"

/data\[\]//fees/services\[\]/name

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/code

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/chargingTriggerInfo

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/prices

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/prices\[\]/interval

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/prices\[\]/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/prices\[\]/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/prices\[\]/customers

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/prices\[\]/customers/rate

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/minimum

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/minimum/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/minimum/currency

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/maximum

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/maximum/value

Adicionado - "x-regulatory-required"

/data\[\]/fees/services\[\]/maximum/currency

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/name

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/chargingTriggerInfo

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/eventLimitQuantity

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/services\[\]/freeEventQuantity

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/interval

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/monthlyFee

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/currency

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/customers

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/prices\[\]/customers/rate

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/minimum/value

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/minimum/currency

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/maximum/value

Adicionado - "x-regulatory-required"

/data\[\]/serviceBundles\[\]/maximum/currency

Adicionado - "x-regulatory-required"

/data\[\]/openingClosingChannels

Adicionado - "x-regulatory-required"

/data\[\]/additionalInfo

Adicionado - "x-regulatory-required"

/data\[\]/transactionMethods

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/minimumBalance

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/minimumBalance/value

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/minimumBalance/currency

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/elegibilityCriteriaInfo

Adicionado - "x-regulatory-required"

/data\[\]/termsConditions/closingProcessInfo

Adicionado - "x-regulatory-required"

/data\[\]/incomeRate/savingAccount

Adicionado - "x-regulatory-required"

/data\[\]/incomeRate/prepaidPaymentAccount

Adicionado - "x-regulatory-required"

data/incomeRate/savingAccount​

Adicionado - exemplo

links/prev​

Adicionado - exemplo

links/next​

Adicionado - exemplo

get/responses/200/data/

Adicionado - descrição

get/responses/200/data/items/participant

Adicionado - descrição

get/responses/200/data/items/fees

Adicionado - descrição

get/responses/200/data/items/fees/services\[\]/prices\[\]/customers

Adicionado - descrição

get/responses/200/data/items/servicesBundles\[\]/prices\[\]/customers

Adicionado - descrição

get/200/links/

Adicionado - descrição

get/200/meta/

Adicionado - descrição

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
