# Changelog - [DA] Seguros - v2.0.0 - v1.0.1

## GET /personals

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data

Adicionado - "description"

Adição

  

Conjunto de informações referente ao produto Seguros Pessoais.

get/responses/200/data

Adicionado - "minItems"

Adição

  

1

get/responses/200/data

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/coverages/items/typeAdditionalInfos

Alterado - "minItem"

Alteração

1

0

get/responses/200/data/items/participant

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/participant/brand

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/participant/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^(\\d{14})$

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

Adição

  

14

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "maxLength"

Adição

  

14

get/responses/200/data/items/participant/name

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/participant/name

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/participant/urlComplementaryList

Alterado - "pattern"

Alteração

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$|^(NA)$

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "minLength"

Adição

  

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'name'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'code'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'modality'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'coverages'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'additionals'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'termsAndConditions'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'terms'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'financialRegimes'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'indemnityPaymentMethods'

Remoção

required

  

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'targetAudience'

Remoção

required

  

get/responses/200/data/items/properties

Removido - "name"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "code"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "category"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "modality"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "coverages"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "assistanceTypes"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "assistanceTypesAdditionalInfos"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "additionals"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "termsAndConditions"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "globalCapital"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "terms"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "pmbacRemuneration"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "benefitRecalculation"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "ageAdjustment"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "financialRegimes"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "reclaim"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "otherGuaranteedValues"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "allowPortability"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "portabilityGraceTime"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "indemnityPaymentMethods"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "indemnityPaymentIncomes"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "premiumPayment"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "minimumRequirement"

Remoção

  

  

get/responses/200/data/items/properties

Removido - "targetAudience"

Remoção

  

  

get/responses/200/data/items/society

Adicionado - "products"

Adição

  

  

get/responses/200/data/items/society

Alterado - "description"

Alteração

Conjunto de informações relativas à seguradora do produto de open insurance

Objeto que representa a empresa regulada pela SUSEP que oferta produtos definidos em OPIN.

get/responses/200/data/items/society

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society

Adicionado obrigatóriedade no campo 'products'

Adição

  

required

get/responses/200/data/items/society/brand

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/brand

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^(\\d{14})$

get/responses/200/data/items/society/cnpjNumber

Adicionado - "minLength"

Adição

  

14

get/responses/200/data/items/society/cnpjNumber

Adicionado - "maxLength"

Adição

  

14

get/responses/200/data/items/society/name

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/name

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'modality'

Remoção

required

  

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'financialRegimes'

Remoção

required

  

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'indemnityPaymentMethods'

Remoção

required

  

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'targetAudience'

Remoção

required

  

get/responses/200/data/items/society/products/items/ assistanceTypesAdditionalInfos​

Alterado - “Exemplo”

Alteração

Informações Adicionais

\[Informações Adicionais\]​

get/responses/200/data/items/society/products/items/additionals

Alterado - nome do campo

Alteração

additionals

additionalServices

get/responses/200/data/items/society/products/items/additionals

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/additionals

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/additionals

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/additionalServices​

Removido obrigatóriedade no campo

Remoção

required

  

get/responses/200/data/items/society/products/items/additionalServices​/enum

Alteração do Enum

Alteração

  

Removido - NA

get/responses/200/data/items/society/products/items/additionalServices/items/enum

Removido - "NAO\_HA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/ageAdjustment

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/ageAdjustment

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/ageAdjustment/criterias

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/ageAdjustment/criterias

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/ageAdjustment/criterias​/enum

Alteração do Enum

Alteração

  

Removido - NA

get/responses/200/data/items/society/products/items/ageAdjustment/criterias/items

Alterado - "description"

Alteração

Critério escolhido para reenquadramento etário 1. Após período em anos 2. A cada período em anos 3. Por mudança de faixa etá...

Critério escolhido para reenquadramento etário 1. Após período em anos 2. A cada período em anos 3. Por mudança de faixa etá...

get/responses/200/data/items/society/products/items/ageAdjustment/frequency

Removido - "maxLength"

Remoção

3

  

get/responses/200/data/items/society/products/items/ageAdjustment/frequency

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/ageAdjustment/frequency

Adicionado - "maximum"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/allowPortability

Adicionado - "example"

Adição

  

true

get/responses/200/data/items/society/products/items/assistanceTypes

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/assistanceTypes

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/assistanceTypesAdditionalInfos

Alterado - "example"

Alteração

  

Informações Adicionais

get/responses/200/data/items/society/products/items/assistanceTypesAdditionalInfos

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/assistanceTypesAdditionalInfos

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/assistenceTypes​/enum

Alteração do Enum

Alteração

  

Removido - NA

get/responses/200/data/items/society/products/items/benefitRecalculation

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/benefitRecalculation

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/benefitRecalculation/criterias

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/benefitRecalculation/criterias

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/benefitRecalculation/criterias

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/benefitRecalculation/updateIndexes/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/category

Alterado - "description"

Alteração

Indicar a categoria do Produto&#58;<br><ol><li>Tradicional</li><li>Microsseguro</li><li>NA</li></ol>

Indicar a categoria do Produto

-   Tradicional
    
-   Microsseguro
    

get/responses/200/data/items/society/products/items/category/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/code

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/code

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages

Adicionado - "description"

Adição

  

Informações referente a cobertura do seguro.

get/responses/200/data/items/society/products/items/coverages

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/coverages/items

Removido - "required"

Remoção

  

  

get/responses/200/data/items/society/products/items/coverages/items

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/ typeAdditionalInfos/items​

Alterado - “Exemplo”

Alteração

Informações Adicionais

\[Informações Adicionais\]​

get/responses/200/data/items/society/products/items/coverages/items/attributes

Adicionado - "description"

Adição

  

Informações referente as características da cobertura do seguro.

get/responses/200/data/items/society/products/items/coverages/items/attributes

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes

Removido obrigatóriedade no campo 'indemnityPaymentFrequencies'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes

Removido obrigatóriedade no campo 'excludedRisks'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/allowApartPurchase

Adicionado - "example"

Adição

  

true

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible

Removido obrigatóriedade no campo 'amount'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible

Removido obrigatóriedade no campo 'currency'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible/amount

Adicionado - "description"

Adição

  

Valor de dedução.

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible/amount

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductible/currency

Adicionado - "minLength"

Adição

  

3

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductibleDays

Removido - "maxLength"

Remoção

10

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductibleDays

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/deductibleDays

Adicionado - "maximum"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible

Removido obrigatóriedade no campo 'amount'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible

Removido obrigatóriedade no campo 'currency'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible/amount

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible/amount

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductible/currency

Adicionado - "minLength"

Adição

  

3

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductibleDays

Removido - "maxLength"

Remoção

10

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductibleDays

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedDeductibleDays

Adicionado - "maximum"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedGracePeriod

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/coverages/items/attributes/differentiatedGracePeriod

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisks/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod

Adicionado - "description"

Adição

  

Período de Carência.

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/amount

Alterado - "maximum"

Alteração

9999999999

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/amount

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/amount

Adicionado - "maxLength"

Adição

  

500

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/amount

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/details

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/details

Adicionado - "description"

Adição

  

Descrições adicionais do período de carência.

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/details

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit

Alterado - "description"

Alteração

Informar o critério de carência para a cobertura&#58;<br><ol><li>Dias</li><li>Meses</li><li>Não se aplica</li><li>NA</li></ol>

Informar o critério de carência para a cobertura

-   Dias
    
-   Meses
    
-   Não se aplica
    

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit

Alterado - "description"

Alteração

Informar o critério de carência para a cobertura - Dias - Meses - Não se aplica

Informar o critério de carência para a cobertura - Dias - Meses

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit​

Removido obrigatóriedade no campo

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit​/enum

Alteração do Enum

Alteração

  

Removido - NA

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriods

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriods

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriods/items

Removido - "maxLength"

Remoção

50

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriods/items

Adicionado - "enum"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentFrequencies/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethods

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethods

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethods​

Removido obrigatóriedade no campo

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethods​/enum

Alteração do Enum

Alteração

  

Removido - NA

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethods/items

Adicionado - "example"

Adição

  

PAGAMENTO\_CAPITAL\_SEGURADO\_VALOR\_MONETARIO

get/responses/200/data/items/society/products/items/coverages/items/attributes/maximumQtyIndemnifiableInstallments

Removido - "maxLength"

Remoção

10

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/maximumQtyIndemnifiableInstallments

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/maximumQtyIndemnifiableInstallments

Adicionado - "maximum"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue

Removido obrigatóriedade no campo 'amount'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue

Removido obrigatóriedade no campo 'currency'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/amount

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/amount

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/currency

Adicionado - "minLength"

Adição

  

3

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue

Removido obrigatóriedade no campo 'amount'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue

Removido obrigatóriedade no campo 'currency'

Remoção

required

  

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/amount

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/amount

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/currency

Adicionado - "minLength"

Adição

  

3

get/responses/200/data/items/society/products/items/coverages/items/type/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/coverages/items/typeAdditionalInfos

Alterado - "example"

Alteração

  

Informações Adicionais

get/responses/200/data/items/society/products/items/coverages/items/typeAdditionalInfos

Adicionado - "minItems"

Adição

  

1

get/responses/200/data/items/society/products/items/coverages/items/typeAdditionalInfos

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/financialRegimes/items

Alterado - "description"

Alteração

Listagem de regime financeiro para cada combinação de modalidade/cobertura do produto indicando:

1.  Repartição simples
    
2.  Repartição Capitais Cobertura
    
3.  Capitalização
    
4.  NA
    

Listagem de regime financeiro para cada combinação de modalidade/cobertura do produto indicando:

1.  Repartição simples
    
2.  Repartição Capitais Cobertura
    
3.  Capitalização
    

get/responses/200/data/items/society/products/items/financialRegimes/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/indemnityPaymentIncomes/items

Alterado - "description"

Alteração

Tipo de renda ou pensão, caso modalidade de pagamento de indenização seja sob a forma de renda:

1.  Certa
    
2.  Temporária
    
3.  Temporária reversível
    
4.  Temporário com mínimo garantido
    
5.  Temporária reversível com mínimo garantido
    
6.  Vitalícia
    
7.  Vitalícia reversível
    
8.  Vitalícia com o mínimo garantido
    
9.  Vitalícia reversível como mínimo garantido
    

10\. NA

Tipo de renda ou pensão, caso modalidade de pagamento de indenização seja sob a forma de renda:

1.  Certa
    
2.  Temporária
    
3.  Temporária reversível
    
4.  Temporário com mínimo garantido
    
5.  Temporária reversível com mínimo garantido
    
6.  Vitalícia
    
7.  Vitalícia reversível
    
8.  Vitalícia com o mínimo garantido
    
9.  Vitalícia reversível como mínimo garantido
    

get/responses/200/data/items/society/products/items/indemnityPaymentIncomes/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/indemnityPaymentMethods/items

Alterado - "description"

Alteração

Modalidade de pagamento da indenização, a considerar os domínios abaixo:

1.  Único
    
2.  Sob a forma de renda
    
3.  NA
    

Modalidade de pagamento da indenização, a considerar os domínios abaixo:

1.  Único
    
2.  Sob a forma de renda
    

get/responses/200/data/items/society/products/items/indemnityPaymentMethods/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/minimumRequirement

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/minimumRequirement

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/minimumRequirement

Removido obrigatóriedade no campo 'contractType'

Remoção

required

  

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Alterado - "description"

Alteração

A considerar os domínios abaixo:

1.  Coletivo;
    
2.  Individual
    
3.  NA
    

A considerar os domínios abaixo:

1.  Coletivo;
    
2.  Individual
    

get/responses/200/data/items/society/products/items/minimumRequirement/contractType/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/modality

Alterado - "description"

Alteração

<ol><li>Funeral</li><li>Prestamista (exceto Habitacional e Rural)</li><li>Viagem</li><li>Educacional</li><li>Dotal (Misto e Puro)</li><li>Acidentes Pessoais</li><li>Vida</li><li>Perda do Certificado de Habilitação de Voo – PCHV</li><li>Doenças Graves ou Doença Terminal</li><li>Desemprego/ Perda de Renda</li><li>Eventos Aleatórios</li><li>Pecúlio</li><li>Pensão prazo certo</li><li>Pensão menores 21 anos</li><li>Pensão menores 24 anos</li><li>Pensão cônjuge vitalícia</li><li>Pensão cônjuge temporária</li><li>NA</li></ol>

-   Funeral
    
-   Prestamista (exceto Habitacional e Rural)
    
-   Viagem
    
-   Educacional
    
-   Dotal (Misto e Puro)
    
-   Acidentes Pessoais
    
-   Vida
    
-   Perda do Certificado de Habilitação de Voo – PCHV
    
-   Doenças Graves ou Doença Terminal
    
-   Desemprego/ Perda de Renda
    
-   Eventos Aleatórios
    
-   Pecúlio
    
-   Pensão prazo certo
    
-   Pensão menores 21 anos
    
-   Pensão menores 24 anos
    
-   Pensão cônjuge vitalícia
    
-   Pensão cônjuge temporária
    

get/responses/200/data/items/society/products/items/modality/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/name

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/name

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/otherGuaranteedValues/items

Alterado - Enum

Alteração

SALDAMENTO  
BENEFICIO\_PROLONGADO  
NAO\_APLICA

SALDAMENTO  
BENEFICIO\_PROLONGADO

get/responses/200/data/items/society/products/items/otherGuaranteedValues/items

Alterado - "description"

Alteração

1.  Saldamento
    
2.  Benefício Prolongado
    
3.  Não se aplica
    
4.  NA
    

1.  Saldamento
    
2.  Benefício Prolongado
    
3.  Não se aplica
    

get/responses/200/data/items/society/products/items/otherGuaranteedValues/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/pmbacRemuneration

Adicionado - "description"

Adição

  

Somente informado se Regime Financeiro for igual a Capitalização.

get/responses/200/data/items/society/products/items/pmbacRemuneration

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/pmbacRemuneration/ updateIndexes​

Alterado - “Exemplo”

Alteração

IPCA

IPC-FGV

get/responses/200/data/items/society/products/items/pmbacRemuneration/interestRate

Alterado - "pattern"

Alteração

^(\\d{1}\\.\\d{6})$|^(-1.000000)$​

^(\\d{1}\\.\\d{6})$

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items

Alterado - "description"

Alteração

Índice utilizado na atualização da PMBaC:

1.  IPCA (IBGE)
    
2.  IGP-M (FGV)
    
3.  INPC (IBGE)
    
4.  NA
    

Índice utilizado na atualização da PMBaC:

1.  IPC-FGV
    
2.  IGP-DI-FGV
    
3.  IPCA-IBGE
    
4.  IGPM-FGV
    
5.  INPC-IBGE
    
6.  TR
    
7.  OUTROS
    

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "IPC-FGV"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "IGP-DI-FGV"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "IPCA-IBGE"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "IGPM-FGV"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "INPC-IBGE"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "TR"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Adicionado - "OUTROS"

Adição

  

enum

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Removido - "IPCA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Removido - "IGP\_M"

Remoção

enum

  

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Removido - "INPC"

Remoção

enum

  

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/portabilityGraceTime

Adicionado - "description"

Adição

  

Período de carência (Somente informado se Regime Financeiro for igual a Capitalização).

get/responses/200/data/items/society/products/items/portabilityGraceTime

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/portabilityGraceTime

Removido obrigatóriedade no campo 'unit'

Remoção

required

  

get/responses/200/data/items/society/products/items/portabilityGraceTime

Removido obrigatóriedade no campo 'amount'

Remoção

required

  

get/responses/200/data/items/society/products/items/portabilityGraceTime/amount

Alterado - "maximum"

Alteração

9999999999

2147483647

get/responses/200/data/items/society/products/items/portabilityGraceTime/amount

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/portabilityGraceTime/unit​

Alterado - Enum

Alteração

DIAS  
MESES  
NAO\_APLICA

DIAS  
MESES

get/responses/200/data/items/society/products/items/portabilityGraceTime/unit

Alterado - "description"

Alteração

Informar o critério de carência para a cobertura&#58;<br><ol><li>Dias</li><li>Meses</li><li>Não se aplica</li><li>NA</li></ol>

Informar o critério de carência para a cobertura

-   Dias
    
-   Meses
    
-   Não se aplica
    

get/responses/200/data/items/society/products/items/portabilityGraceTime/unit/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/premiumPayment

Removido - "required"

Remoção

  

  

get/responses/200/data/items/society/products/items/premiumPayment

Adicionado - "description"

Adição

  

Campo sem descrição na API em OPIN.

get/responses/200/data/items/society/products/items/premiumPayment

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/premiumPayment

Adicionado - "paymentMethodAdittionalInfo"

Adição

  

  

get/responses/200/data/items/society/products/items/premiumPayment/contributionTax

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/premiumPayment/contributionTax

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/premiumPayment/frequencies/items

Alterado - "description"

Alteração

Periodicidade de pagamento do prêmio:

1.  Diária
    
2.  Mensal
    
3.  Única
    
4.  Anual
    
5.  Trimestral
    
6.  Semestral
    
7.  Fracionado
    
8.  Outra
    
9.  NA
    

Periodicidade de pagamento do prêmio:

1.  Diária
    
2.  Mensal
    
3.  Única
    
4.  Anual
    
5.  Trimestral
    
6.  Semestral
    
7.  Fracionado
    
8.  Outra
    

get/responses/200/data/items/society/products/items/premiumPayment/frequencies/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/premiumPayment/paymentMethods/items

Alterado - "description"

Alteração

Meio de pagamento escolhido pelo segurado. A considerar os domínios abaixo:

1.  Cartão de Crédito
    
2.  Cartão de Débito
    
3.  Débito em conta corrente
    
4.  Débito em conta poupança
    
5.  Boleto bancário
    
6.  PIX
    
7.  Consignação em Folha de Pagamento
    
8.  Pontos de Programa de Benefício
    
9.  Regra de Parceiro
    

10\. NA

Meio de pagamento escolhido pelo segurado. A considerar os domínios abaixo:

1.  Cartão de Crédito
    
2.  Cartão de Débito
    
3.  Débito em conta corrente
    
4.  Débito em conta poupança
    
5.  Boleto bancário
    
6.  PIX
    
7.  Consignação em Folha de Pagamento
    
8.  Pontos de Programa de Benefício
    
9.  Regra de Parceiro
    

10\. TED e DOC  
11\. Outros

get/responses/200/data/items/society/products/items/premiumPayment/paymentMethods/items/enum

Adicionado - "TED\_DOC"

Adição

  

enum

get/responses/200/data/items/society/products/items/premiumPayment/paymentMethods/items/enum

Adicionado - "OUTROS"

Adição

  

enum

get/responses/200/data/items/society/products/items/premiumPayment/paymentMethods/items/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/properties

Adição - "name"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "code"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "category"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "modality"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "coverages"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "assistanceTypes"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "assistanceTypesAdditionalInfos"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "additionals"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "termsAndConditions"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "globalCapital"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "terms"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "pmbacRemuneration"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "benefitRecalculation"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "ageAdjustment"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "financialRegimes"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "reclaim"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "otherGuaranteedValues"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "allowPortability"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "portabilityGraceTime"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "indemnityPaymentMethods"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "indemnityPaymentIncomes"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "premiumPayment"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "minimumRequirement"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adição - "targetAudience"

Adição

  

  

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'name'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'code'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'modality'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'coverages'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'additionals'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'termsAndConditions'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'terms'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'financialRegimes'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'indemnityPaymentMethods'

Adição

  

required

get/responses/200/data/items/society/products/items/properties

Adicionado obrigatóriedade no campo 'targetAudience'

Adição

  

required

get/responses/200/data/items/society/products/items/reclaim

Adicionado - "description"

Adição

  

Somente informado se Regime Financeiro for igual a Capitalização.

get/responses/200/data/items/society/products/items/reclaim

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/reclaim/differenciatedPercentage

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/reclaim/differenciatedPercentage

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Adicionado - "description"

Adição

  

Período de carência.

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Removido obrigatóriedade no campo 'unit'

Remoção

required

  

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Removido obrigatóriedade no campo 'amount'

Remoção

required

  

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/amount

Alterado - "maximum"

Alteração

9999999999

2147483647

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/amount

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/details

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/details

Adicionado - "description"

Adição

  

Descrições adicionais do período de carência.

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/details

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Alterado - Enum

Alteração

DIAS  
MESES  
NAO\_APLICA

DIAS  
MESES

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Alterado - "description"

Alteração

Informar o critério de carência para a cobertura&#58;<br><ol><li>Dias</li><li>Meses</li><li>Não se aplica</li><li>NA</li></ol>

Informar o critério de carência para a cobertura

-   Dias
    
-   Meses
    
-   Não se aplica
    

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/reclaim/table

Adicionado - "description"

Adição

  

Listagem de percentuais de resgate da PMBaC para cada conjunto de prazo aplicável e para cada combinação de modalidade/cobertura estruturados em regime de capitalização.

get/responses/200/data/items/society/products/items/reclaim/table

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/reclaim/table/items

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/reclaim/table/items/finalMonthRange

Removido - "maxLength"

Remoção

2

  

get/responses/200/data/items/society/products/items/reclaim/table/items/finalMonthRange

Adicionado - "description"

Adição

  

Mês final do range.

get/responses/200/data/items/society/products/items/reclaim/table/items/finalMonthRange

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/reclaim/table/items/finalMonthRange

Adicionado - "maximum"

Adição

  

12

get/responses/200/data/items/society/products/items/reclaim/table/items/initialMonthRange

Removido - "maxLength"

Remoção

2

  

get/responses/200/data/items/society/products/items/reclaim/table/items/initialMonthRange

Adicionado - "description"

Adição

  

Mês inicial do range.

get/responses/200/data/items/society/products/items/reclaim/table/items/initialMonthRange

Adicionado - "minimum"

Adição

  

  

get/responses/200/data/items/society/products/items/reclaim/table/items/initialMonthRange

Adicionado - "maximum"

Adição

  

12

get/responses/200/data/items/society/products/items/reclaim/table/items/percentagem

Alterado - "pattern"

Alteração

^(\\d{1}\\.\\d{6})$|^(-1.000000)$​

^(\\d{1}\\.\\d{6})$

get/responses/200/data/items/society/products/items/targetAudience

Alterado - "description"

Alteração

A considerar os domínios abaixo:

1.  Pessoa Natural
    
2.  Pessoa Jurídica
    
3.  Ambas (Pessoa Natural e Jurídica)
    
4.  NA
    

A considerar os domínios abaixo:

1.  Pessoa Natural
    
2.  Pessoa Jurídica
    
3.  Ambas (Pessoa Natural e Jurídica)
    

get/responses/200/data/items/society/products/items/targetAudience/enum

Removido - "NA"

Remoção

enum

  

get/responses/200/data/items/society/products/items/terms

Adicionado - "minItems"

Adição

  

  

get/responses/200/data/items/society/products/items/terms

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/terms​

Removido obrigatóriedade no campo

Remoção

required

  

get/responses/200/data/items/society/products/items/terms​/enum

Alteração do Enum

Alteração

  

Removido - NA

get/responses/200/data/items/society/products/items/terms/items

Alterado - "description"

Alteração

Define o prazo do plano contratado<br><ol><li>Vitalícia</li><li>Temporária - prazo fixo</li><li>Temporária – intermitente</li><li>...

Define o prazo do plano contratado 1. Vitalícia 2. Temporária - prazo fixo 3. Temporária – intermitente

get/responses/200/data/items/society/products/items/termsAndConditions

Adicionado - "description"

Adição

  

Termos e condições do produto Seguros.

get/responses/200/data/items/society/products/items/termsAndConditions

Adicionado - "maxItems"

Adição

  

2147483647

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - "x-regulatory-required"

Adição

  

  

get/responses/200/data/items/society/products/items/termsAndConditions/items/detail

Adicionado - "pattern"

Adição

  

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/products/items/termsAndConditions/items/detail

Adicionado - "minLength"

Adição

  

1

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber

Alterado - "pattern"

Alteração

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$|^(NA)$

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$

get/responses/200/data/items/participant/urlComplementaryList

Removido - "pattern"

Remoção

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$

get/responses/200/data/items/participant/urlComplementaryList

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
