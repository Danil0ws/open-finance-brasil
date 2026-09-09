# Changelog - [DA] Previdência- v2.0.0 - v2.0.0-rc.1

## GET /risk-coverages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/participant/urlComplementaryList

Removido - "pattern"

Remoção

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "format"

Adição

url

get/responses/200/data/items/society/products/items/assistanceTypes/items

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/assistanceTypes/items

Removido - "maxLength"

Remoção

80

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethod

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethod

Removido - "maxLength"

Remoção

80

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicity

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicity

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisks/items

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisks/items

Removido - "maxLength"

Remoção

50

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Adicionado - "format"

Adição

url

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriod

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriod

Removido - "maxLength"

Remoção

80

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethod

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethod

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/coverages/items/attributes/profitModality

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/profitModality

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/coverages/items/type

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/coverages/items/type

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/financialRegimeContractType

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/financialRegimeContractType

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - "format"

Adição

url

get/responses/200/data/items/society/products/items/modality

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/modality

Removido - "maxLength"

Remoção

80

get/responses/200/data/items/society/products/items/otherGuaranteedValues

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/otherGuaranteedValues

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/planAdditional

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/planAdditional

Removido - "maxLength"

Remoção

80

get/responses/200/data/items/society/products/items/premiumUpdateIndex

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/premiumUpdateIndex

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/targetAudience

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/targetAudience

Removido - "maxLength"

Remoção

23

get/responses/200/data/items/society/products/items/termsAndConditions/items/contractTermsConditions

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/termsAndConditions/items/contractTermsConditions

Adicionado - "format"

Adição

url

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /survival-coverages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/participant/urlComplementaryList

Removido - "pattern"

Remoção

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "format"

Adição

url

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/typePerformanceFee

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/typePerformanceFee

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/typePerformanceFee

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/typePerformanceFee

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - "format"

Adição

url

get/responses/200/data/items/society/products/items/modality

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/modality

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/segment

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/segment

Removido - "maxLength"

Remoção

20

get/responses/200/data/items/society/products/items/termsAndConditions/items/contractTermsConditions

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/termsAndConditions/items/contractTermsConditions

Adicionado - "format"

Adição

url

get/responses/200/data/items/society/products/items/type

Removido - "minLength"

Remoção

1

get/responses/200/data/items/society/products/items/type

Removido - "maxLength"

Remoção

80

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$
