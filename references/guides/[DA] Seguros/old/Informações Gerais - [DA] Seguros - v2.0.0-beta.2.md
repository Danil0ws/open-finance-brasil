# Informações Gerais - [DA] Seguros - v2.0.0-beta.2

17

## **Contexto sobre a API**

A API Seguros fornece dados pertinente aos produtos relativos a seguros. As instituições participantes do OFB devem reportar este produto por meio desta API no endpoint /personals para seguros pessoais.

Esta API interopera, via demanda regulatória do Banco Central na Resolução Conjunta n.º 5, Art. 1º, com a API Person – Fase 1 do ecossistema OPIN (Open Insurence), a qual é gerenciada e regulada pela SUSEP (Superintendência de Seguros Privados).

No âmbito do OFB, a instituição é obrigada a divulgar todos os dados relacionados ao produto em questão, independentemente de ser de sua propriedade ou de uma empresa parceira.

## **Prefixo**

Prefixo do(s) endpoint(s): /opendata-insurance/v2

## **Lista de Endpoints**

Lista de todos os títulos de capitalização de uma instituição: GET /personals

## **Visão de alto nível**

A estrutura base do endpoint disponibilizado nesta API é visualizada na Figura abaixo, onde as informações sobre os seguros pessoais comercializados pelas instituições participantes do OFB encontra-se no objeto products, abaixo de society.

![API\_Seguros (1).png](images/API_Seguros%20-1-.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-getPersonalInsurance_v2.md)

## DE-PARA de campos

**API Seguros (Open Finance)**`​`  
_**Endpoint**_ **/personals**​

**API Person - Fase 1 (Open Insurance)**`​`  
_**Endpoint**_ **/person**​

/data\[\]​

\-​

/data\[\]//participant/brand​

\-​

/data\[\]//participant/name​

\-​

/data\[\]//participant/cnpjNumber​

\-​

/data\[\]//participant/urlComplementaryList​

\-​

/data\[\]/society/brand​

/data/brand/name​

/data\[\]/society/name​

/data/brand/companies/name​

/data\[\]/society/cnpjNumber​

/data/brand/companies/cnpjNumber​

/data\[\]/society/products/name​

/data/brand/companies/products/name​

/data\[\]/society/products/code​

/data/brand/companies/products/code​

/data\[\]/society/products/category​

/data/brand/companies/products/category​

/data\[\]/society/products/modality​

/data/brand/companies/products/insuranceModality​

/data\[\]/society/products/coverages\[\]​

/data/brand/companies/products/coverages\[\]​

/data\[\]/society/products/coverages\[\]/type​

/data/brand/companies/products/coverages\[\]/coverages​

/data\[\]/society/products\[\]/coverages/type​

/data/brand/companies/products/coverages/coverage​

/data\[\]/society/products\[\]/coverages/typeAdditionalInfos​

/data/brand/companies/products/coverages/coverageOthers​

/data\[\]/society/products\[\]/coverages/attributes​

/data/brand/companies/products/coverages/coverageAttributes​

/data\[\]/society/products\[\]/coverages/attributes/indemnityPaymentMethods​

/data/brand/companies/products/coverages/coverageAttributes/indemnityPaymentMethod​

/data\[\]/society/products\[\]/coverages/attributes/indemnityPaymentFrequencies​

/data/brand/companies/products/coverages/coverageAttributes/indemnityPaymentFrequency​

/data\[\]/society/products\[\]/coverages/attributes/minValue​

/data/brand/companies/products/coverages/coverageAttributes/minValue​

/data\[\]/society/products\[\]/coverages/attributes/minValue/amount​

/data/brand/companies/products/coverages/coverageAttributes/minValue/amount​

/data\[\]/society/products\[\]/coverages/attributes/minValue/currency​

/data/brand/companies/products/coverages/coverageAttributes/minValue/unit/code​

\-​

/data/brand/companies/products/coverages/coverageAttributes/minValue/unit/description​

/data\[\]/society/products\[\]/coverages/attributes/maxValue​

/data/brand/companies/products/coverages/coverageAttributes/maxValue​

/data\[\]/society/products\[\]/coverages/attributes/maxValue/amount​

/data/brand/companies/products/coverages/coverageAttributes/maxValue/amount​

/data\[\]/society/products\[\]/coverages/attributes/maxValue/currency​

/data/brand/companies/products/coverages/coverageAttributes/maxValue/unit/code​

\-​

/data/brand/companies/products/coverages/coverageAttributes/maxValue/unit/description​

/data\[\]/society/products\[\]/coverages/attributes/indemnifiablePeriods​

/data/brand/companies/products/coverages/coverageAttributes/indemnifiablePeriod​

/data\[\]/society/products\[\]/coverages/attributes/maximumQtyIndemnifiableInstallments​

/data/brand/companies/products/coverages/coverageAttributes/maximumQtyIndemnifiableInstallments​

/data\[\]/society/products\[\]/coverages/attributes/gracePeriod​

/data/brand/companies/products/coverages/coverageAttributes/gracePeriod​

/data\[\]/society/products\[\]/coverages/attributes/gracePeriod/details​

/data/brand/companies/products/coverages/coverageAttributes/gracePeriod/details​

/data\[\]/society/products\[\]/coverages/attributes/gracePeriod/amount​

/data/brand/companies/products/coverages/coverageAttributes/gracePeriod/amount​

/data\[\]/society/products\[\]/coverages/attributes/gracePeriod/unit​

/data/brand/companies/products/coverages/coverageAttributes/gracePeriod/unit​

/data\[\]/society/products\[\]/coverages/attributes/differentiatedGracePeriod​

/data/brand/companies/products/coverages/coverageAttributes/differentiatedGracePeriod​

/data\[\]/society/products\[\]/coverages/attributes/deductibleDays​

/data/brand/companies/products/coverages/coverageAttributes/deductibleDays​

/data\[\]/society/products\[\]/coverages/attributes/differentiatedDeductibleDays​

/data/brand/companies/products/coverages/coverageAttributes/differentiatedDeductibleDays​

/data\[\]/society/products\[\]/coverages/attributes/deductible/amount​

/data/brand/companies/products/coverages/coverageAttributes/deductibleBRL​

/data\[\]/society/products\[\]/coverages/attributes/deductible/currency​

\-​

/data\[\]/society/products\[\]/coverages/attributes/differentiatedDeductible/amount​

/data/brand/companies/products/coverages/coverageAttributes/differentiatedDeductibleBRL​

/data\[\]/society/products\[\]/coverages/attributes/differentiatedDeductible/currency​

\-​

/data\[\]/society/products\[\]/coverages/attributes/excludedRisks​

/data/brand/companies/products/coverages/coverageAttributes/excludedRisks​

/data\[\]/society/products\[\]/coverages/attributes/excludedRisksURL​

/data/brand/companies/products/coverages/coverageAttributes/excludedRisksURL​

/data\[\]/society/products\[\]/coverages/attributes/allowApartPurchase​

/data/brand/companies/products/coverages/coverageAttributes/allowApartPurchase​

/data\[\]/society/products\[\]/assistanceTypes​

/data/brand/companies/products/assistanceType​

/data\[\]/society/products\[\]/assistanceTypesAdditionalInfos​

/data/brand/companies/products/assistanceTypeOthers​

/data\[\]/society/products\[\]/additionals​

/data/brand/companies/products/additional​

/data\[\]/society/products\[\]/termsAndConditions​

/data/brand/companies/products/termsAndConditions​

/data\[\]/society/products\[\]/termsAndConditions/susepProcessNumber​

/data/brand/companies/products/termsAndConditions/susepProcessNumber​

/data\[\]/society/products\[\]/pmbacRemuneration/updateIndexes​

/data/brand/companies/products/pmbacRemuneration/pmbacUpdateIndex​

/data\[\]/society/products\[\]/benefitRecalculation​

/data/brand/companies/products/benefitRecalculation​

/data\[\]/society/products\[\]/benefitRecalculation/criterias​

/data/brand/companies/products/benefitRecalculation/benefitRecalculationCriteria​

/data\[\]/society/products\[\]/benefitRecalculation/updateIndexes​

/data/brand/companies/products/benefitRecalculation/benefitUpdateIndex​

/data\[\]/society/products\[\]/ageAdjustment​

/data/brand/companies/products/ageAdjustment​

/data\[\]/society/products\[\]/ageAdjustment/criterias​

/data/brand/companies/products/ageAdjustment/criterion​

/data\[\]/society/products\[\]/ageAdjustment/frequency​

/data/brand/companies/products/ageAdjustment/frequency​

/data\[\]/society/products\[\]/financialRegimes​

/data/brand/companies/products/contractType​

/data\[\]/society/products\[\]/reclaim​

/data/brand/companies/products/reclaim​

/data\[\]/society/products\[\]/reclaim/table​

/data/brand/companies/products/reclaim/reclaimTable​

/data\[\]/society/products\[\]/reclaim/table/initialMonthRange​

/data/brand/companies/products/reclaim/reclaimTable/initialMonthRange​

/data\[\]/society/products\[\]/reclaim/table/finalMonthRange​

/data/brand/companies/products/reclaim/reclaimTable/finalMonthRange​

/data\[\]/society/products\[\]/reclaim/table/percentage​

/data/brand/companies/products/reclaim/reclaimTable/percentage​

/data\[\]/society/products\[\]/reclaim/gracePeriod​

/data/brand/companies/products/reclaim/gracePeriod​

/data\[\]/society/products\[\]/reclaim/gracePeriod/amount​

/data/brand/companies/products/reclaim/gracePeriod/amount​

/data\[\]/society/products\[\]/reclaim/gracePeriod/unit​

/data/brand/companies/products/reclaim/gracePeriod/unit​

/data\[\]/society/products\[\]/reclaim/gracePeriod/details​

/data/brand/companies/products/reclaim/gracePeriod/details​

/data\[\]/society/products\[\]/reclaim/differenciatedPercentage​

/data/brand/companies/products/reclaim/diferentiatedPercentage​

/data\[\]/society/products\[\]/otherGuaranteedValues​

/data/brand/companies/products/otherGuaranteedValues​

/data\[\]/society/products\[\]/allowPortability​

/data/brand/companies/products/allowPortability​

/data\[\]/society/products\[\]/portabilityGraceTime/amount​

/data/brand/companies/products/portabilityGraceTime​

/data\[\]/society/products\[\]/portabilityGraceTime/unit​

\-​

/data\[\]/society/products\[\]/indemnityPaymentMethods​

/data/brand/companies/products/indemnityPaymentMethod​

/data\[\]/society/products\[\]/indemnityPaymentIncomes​

/data/brand/companies/products/indemnityPaymentIncome​

/data\[\]/society/products\[\]/premiumPayment​

/data/brand/companies/products/premiumPayment​

/data\[\]/society/products\[\]/premiumPayment/paymentMethods​

/data/brand/companies/products/premiumPayment/paymentMethod​

/data/premiumPayment/frequencies​

/data/brand/companies/products/premiumPayment/frequency​

/data/premiumPayment/contributionTax​

/data/brand/companies/products/premiumPayment/premiumTax​

/data/minimumRequirement​

/data/brand/companies/products/minimunRequirements​

/data/minimumRequirement/contractType​

/data/brand/companies/products/minimunRequirements/contractingType​

/data/minimumRequirement/contractingMinRequirement​

/data/brand/companies/products/minimunRequirements/contractingMinRequirement​

/data/targetAudience​

/data/brand/companies/products/targetAudience​

## **DE-PARA dos parâmetros**

**API Seguros (Open Finance)**`​`  
_**Endpoint /personals**_​

**API Person (Open Insurance)**`​`  
_**Endpoint /person**_​

\-​

parameters/cache-Control​

\-​

parameters/cnpjNumber​

\-​

parameters/content-Security-Policy​

\-​

parameters/content-Type​

\-​

parameters/strict-Transport-Security​

\-​

parameters/x-Content-Type-Options​

\-​

parameters/x-Frame-Options​

## **DE-PARA dos status code**

**API Seguros (Open Finance)**`​`  
_**Endpoint**_ **/**_**personals**_​

**API Person Title (Open Insurance)**`​`  
_**Endpoint**_ **/**_**person**_​

\-​

Status code: 401​

\-​

Status code: 403​

\-​

Status code: 406​

\-​

Status code: default​

400 404 405 429 500 /meta/requestDateTime​

400 401 403 404 405 406 422 429 500 /erros/requestDateTime​
