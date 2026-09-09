# Changelog - Investimentos - v1.0.0-rc2.0

GET /funds

**Campo**

**O que foi alterado?**

get/responses/200/data/generalConditions/redemption/quotationDays

description

get/responses/200/data/generalConditions/redemption/paymentDays

description

get/responses/200/data/items/anbimaCategory

description

get/responses/200/data/items/generalConditions/

Removido - "currency" de dentro da estrutura “required“

get/responses/200/data/items/admin/name

Adicionado - "pattern"

get/responses/200/data/items/anbimaCategory

Removido - "maxLength"

get/responses/200/data/items/fees/performanceFee/method

Removido - "maxLength"

get/responses/200/data/items/fundManager/name

Adicionado - "pattern"

get/responses/200/data/items/generalConditions/application/quotationDays

Adicionado - "maximum"

get/responses/200/data/items/generalConditions/application/quotationTerm

Removido - "maxLength"

get/responses/200/data/items/generalConditions/fundQuotaType

Removido - "maxLength"

get/responses/200/data/items/generalConditions/redemption/graceDays

Adicionado - "maximum"

get/responses/200/data/items/generalConditions/redemption/graceDays

Adicionado - "minimum"

get/responses/200/data/items/generalConditions/redemption/paymentDays

Adicionado - "maximum"

get/responses/200/data/items/generalConditions/redemption/paymentTerm

Removido - "maxLength"

get/responses/200/data/items/generalConditions/redemption/quotationDays

Adicionado - "maximum"

get/responses/200/data/items/generalConditions/redemption/quotationTerm

Removido - "maxLength"

get/responses/200/data/items/isinCode

Adicionado - "minLength"

get/responses/200/data/items/name

Adicionado - "pattern"

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "maxLength"

get/responses/200/data/items/participant/name

Adicionado - "pattern"

get/responses/200/data/items/taxation

Removido - "maxLength"

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "description"

get/responses

Adicionado - "529"

get/responses/429

Alterado - "description"

GET /bank-fixed-incomes

**Campo**

**O que foi feito?**

get/responses/200/data/index/issueRemunerationRate/prices/operationRate

Substituído de _customerRate_ para _operationRate_

get/responses/200/data/items/index/indexerAdditionalInfo

description

get/responses/200/data/items/index/indexerAdditionalInfo

example

get/responses/200/data/items/index/indexerAdditionalInfo

maxLength

get/responses/200/data/items/index/indexerAdditionalInfo

Adicionado - "pattern"

get/responses/200/data/items/index/issueRemunerationRate/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/investmentConditions/expirationPeriod

Removido - "maxLength"

get/responses/200/data/items/investmentConditions/gracePeriod

Removido - "maxLength"

get/responses/200/data/items/investmentConditions/redemptionTerm

Removido - "maxLength"

get/responses/200/data/items/investmentType

Removido - "maxLength"

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "maxLength"

get/responses/200/data/items/participant/name

Adicionado - "pattern"

get/responses/200/data/items/targetAudience

Removido - "maxLength"

get/responses/200/data/items/index/indexerAdditionalInfo

description

get/responses/200/data/items/index/issueRemunerationRate/maximum

example

get/responses/200/data/items/index/issueRemunerationRate/maximum

Adicionado - "minLength"

get/responses/200/data/items/index/issueRemunerationRate/maximum

pattern

get/responses/200/data/items/index/issueRemunerationRate/minimum

example

get/responses/200/data/items/index/issueRemunerationRate/minimum

Adicionado - "minLength"

get/responses/200/data/items/index/issueRemunerationRate/minimum

pattern

get/responses/200/data/items/index/issueRemunerationRate/prices/items/operationRate

example

get/responses/200/data/items/index/issueRemunerationRate/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/index/issueRemunerationRate/prices/items/operationRate

pattern

get/responses/200/data/items/index/issueRemunerationRate/prices/items/value

example

get/responses/200/data/items/index/issueRemunerationRate/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/index/issueRemunerationRate/prices/items/value

pattern

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "description"

get/responses

Adicionado - "529"

get/responses/429

Alterado - "description"

get/responses/200/data/items/index/indexer

Alterado - "description"

GET /credit-fixed-incomes

**Campo**

**O que foi feito?**

get/responses/200/data/index/issueRemunerationRate/prices/operationRate

Substituído de _customerRate_ para _operationRate_

get/responses/200/data/items/custodyFee/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/investmentType

Removido - "maxLength"

get/responses/200/data/items/loadingRate/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "maxLength"

get/responses/200/data/items/participant/name

Adicionado - "pattern"

get/responses/200/data/items/targetAudience

Removido - "maxLength"

get/responses/200/data/items/custodyFee/maximum

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/maximum

pattern

get/responses/200/data/items/custodyFee/minimum

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/minimum

pattern

get/responses/200/data/items/custodyFee/prices/items/operationRate

example

get/responses/200/data/items/custodyFee/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/prices/items/operationRate

pattern

get/responses/200/data/items/custodyFee/prices/items/value

example

get/responses/200/data/items/custodyFee/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/prices/items/value

pattern

get/responses/200/data/items/loadingRate/maximum

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/maximum

pattern

get/responses/200/data/items/loadingRate/minimum

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/minimum

pattern

get/responses/200/data/items/loadingRate/prices/items/operationRate

example

get/responses/200/data/items/loadingRate/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/prices/items/operationRate

pattern

get/responses/200/data/items/loadingRate/prices/items/value

example

get/responses/200/data/items/loadingRate/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/prices/items/value

pattern

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "description"

get/responses

Adicionado - "529"

get/responses/429

Alterado - "description"

GET /variable-incomes

**Campo**

**O que foi feito?**

get/responses/200/data/index/issueRemunerationRate/prices/operationRate

Substituído de _customerRate_ para _operationRate_

get/responses/200/data

Adicionado - “exemplo“

get/responses/200/meta/totalRecords

Alterado - “exemplo“

get/responses/200/data/items/custodyFee/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/investmentType

Removido - "maxLength"

get/responses/200/data/items/loadingRate/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "maxLength"

get/responses/200/data/items/participant/name

Adicionado - "pattern"

get/responses/200/data/items/targetAudience

Removido - "maxLength"

get/responses/200/data/items/custodyFee/maximum

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/maximum

pattern

get/responses/200/data/items/custodyFee/minimum

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/minimum

pattern

get/responses/200/data/items/custodyFee/prices/items/operationRate

example

get/responses/200/data/items/custodyFee/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/prices/items/operationRate

pattern

get/responses/200/data/items/custodyFee/prices/items/value

example

get/responses/200/data/items/custodyFee/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/prices/items/value

pattern

get/responses/200/data/items/loadingRate/maximum

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/maximum

pattern

get/responses/200/data/items/loadingRate/minimum

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/minimum

pattern

get/responses/200/data/items/loadingRate/prices/items/operationRate

example

get/responses/200/data/items/loadingRate/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/prices/items/operationRate

pattern

get/responses/200/data/items/loadingRate/prices/items/value

example

get/responses/200/data/items/loadingRate/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/prices/items/value

pattern

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "description"

get/responses

Adicionado - "529"

get/responses/429

Alterado - "description"

GET /treasure-titles

**Campo**

**O que foi alterado?**

get/responses/200/data/index/issueRemunerationRate/prices/operationRate

Substituído de _customerRate_ para _operationRate_

get/responses/200/data/items/custodyFee/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/investmentType

Removido - "maxLength"

get/responses/200/data/items/loadingRate/prices/items/interval

Removido - "maxLength"

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "maxLength"

get/responses/200/data/items/participant/name

Adicionado - "pattern"

get/responses/200/data/items/custodyFee/maximum

example

get/responses/200/data/items/custodyFee/maximum

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/maximum

pattern

get/responses/200/data/items/custodyFee/minimum

example

get/responses/200/data/items/custodyFee/minimum

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/minimum

pattern

get/responses/200/data/items/custodyFee/prices/items/operationRate

example

get/responses/200/data/items/custodyFee/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/prices/items/operationRate

pattern

get/responses/200/data/items/custodyFee/prices/items/value

example

get/responses/200/data/items/custodyFee/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/custodyFee/prices/items/value

pattern

get/responses/200/data/items/loadingRate/maximum

example

get/responses/200/data/items/loadingRate/maximum

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/maximum

pattern

get/responses/200/data/items/loadingRate/minimum

example

get/responses/200/data/items/loadingRate/minimum

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/minimum

pattern

get/responses/200/data/items/loadingRate/prices/items/operationRate

example

get/responses/200/data/items/loadingRate/prices/items/operationRate

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/prices/items/operationRate

pattern

get/responses/200/data/items/loadingRate/prices/items/value

example

get/responses/200/data/items/loadingRate/prices/items/value

Adicionado - "minLength"

get/responses/200/data/items/loadingRate/prices/items/value

pattern

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "description"

get/responses

Adicionado - "529"

get/responses/429

Alterado - "description"
