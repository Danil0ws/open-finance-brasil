# Changelog - [DA] Previdência- v2.0.0-beta.1 - v1.0.1

## GET /risk-coverages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data

Adicionado - "description"

Adição

Conjunto de informações referente ao produto previdência

get/responses/200/data/items

Removido - name

Remoção

get/responses/200/data/items

Removido - code​

Remoção

get/responses/200/data/items

Removido - modality ​

Remoção

get/responses/200/data/items

Removido - coverages

Remoção

get/responses/200/data/items

Removido - assistanceTypes

Remoção

get/responses/200/data/items

Removido - assistanceTypesAdditionalInfos

Remoção

get/responses/200/data/items

Removido - additional​

Remoção

get/responses/200/data/items

Removido - termsAndConditions

Remoção

get/responses/200/data/items

Removido - pmbacRemuneration​

Remoção

get/responses/200/data/items

Removido - premiumUpdateIndex​

Remoção

get/responses/200/data/items

Removido - ageAdjustment​

Remoção

get/responses/200/data/items

Removido - financialRegimeContractType​

Remoção

get/responses/200/data/items

Removido - reclaim​

Remoção

get/responses/200/data/items

Removido - otherGuaranteedValues​

Remoção

get/responses/200/data/items

Removido - contributionPayment​

Remoção

get/responses/200/data/items

Removido - minimumRequirement​

Remoção

get/responses/200/data/items

Removido - targetAudience​

Remoção

get/responses/200/data/items

Adicionado - minItens

Adição

1

get/responses/200/data/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/participant

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/participant/brand

Adicionado - minLength

Adição

1

get/responses/200/data/items/participant/brand

Adicionado - maxLength

Adição

80

get/responses/200/data/items/participant/cnpjNumber

Alterado - Pattern

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/participant/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/participant/cnpjNumber

Adicionado - minLength

Adição

14

get/responses/200/data/items/participant/cnpjNumber

Adicionado - maxLength

Adição

14

get/responses/200/data/items/participant/name

Adicionado - minLength

Adição

1

get/responses/200/data/items/participant/name

Adicionado - maxLength

Adição

80

get/responses/200/data/items/participant/urlComplementaryList​

Alterado - Pattern

Alteração

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%._\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%_\\+.~#?&\\/\\/=\]\*))|(NA)$

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$​

get/responses/200/data/items/participant/urlComplementaryList

Alterado - "pattern"

Alteração

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))|(NA)$

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$

get/responses/200/data/items/society

Adicionado - products

Adição

minItems: 1​

description: Lista de produtos de uma empresa.

get/responses/200/data/items/society

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society

Adicionado obrigatóriedade no campo 'products'

Adição

required

get/responses/200/data/items/society/brand​

Adicionado - Brand

Adição

Tipo: string​

maxLength: 80​

minLenght: 1  
example: Marca no OPIN​

pattern: ^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$​

Descrição: Nome da Marca reportada pelo participante do Open Insurance. O conceito a que se refere a 'marca' é em essência uma promessa da empresa em fornecer uma série específica de atributos, benefícios e serviços uniformes aos clientes​

Mandatoriedade do campo: Opcional ​

get/responses/200/data/items/society/cnpjNumber​

Alterado - Pattern

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/society/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/society/cnpjNumber

Adicionado - minLength

Adição

14

get/responses/200/data/items/society/cnpjNumber

Adicionado - maxLength

Adição

14

get/responses/200/data/items/society/name

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/name

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/contributionPayment/contributionPaymentMethod

Alterado - description

Alteração

Forma de pagamento da contribuição.

-   CARTAO\_CREDITO
    
-   DEBITO\_CONTA
    
-   DEBITO\_CONTA\_POUPANCA
    
-   BOLETO\_BANCARIO
    
-   PIX
    
-   TED\_DOC
    
-   CONSIGNACAO\_FOLHA\_PAGAMENTO
    
-   PONTOS\_PROGRAMA\_BENEFICIO
    
-   OUTROS
    

Forma de pagamento da contribuição.

-   CARTAO\_CREDITO
    
-   CARTAO\_DEBITO
    
-   DEBITO\_CONTA
    
-   DEBITO\_CONTA\_POUPANCA
    
-   BOLETO\_BANCARIO
    
-   PIX
    
-   TED\_DOC
    
-   CONSIGNACAO\_FOLHA\_PAGAMENTO
    
-   PONTOS\_PROGRAMA\_BENEFICIO
    
-   OUTROS
    

get/responses/200/data/items/society/products/items

Adicionado - name

Adição

get/responses/200/data/items/society/products/items

Adicionado - code​

Adição

get/responses/200/data/items/society/products/items

Adicionado - modality ​

Adição

get/responses/200/data/items/society/products/items

Adicionado - coverages

Adição

get/responses/200/data/items/society/products/items

Adicionado - assistanceTypes

Adição

get/responses/200/data/items/society/products/items

Adicionado - assistanceTypesAdditionalInfos

Adição

get/responses/200/data/items/society/products/items

Adicionado - additional​

Adição

get/responses/200/data/items/society/products/items

Adicionado - termsAndConditions

Adição

get/responses/200/data/items/society/products/items

Adicionado - pmbacRemuneration​

Adição

get/responses/200/data/items/society/products/items

Adicionado - premiumUpdateIndex​

Adição

get/responses/200/data/items/society/products/items

Adicionado - ageAdjustment​

Adição

get/responses/200/data/items/society/products/items

Adicionado - financialRegimeContractType​

Adição

get/responses/200/data/items/society/products/items

Adicionado - reclaim​

Adição

get/responses/200/data/items/society/products/items

Adicionado - otherGuaranteedValues​

Adição

get/responses/200/data/items/society/products/items

Adicionado - contributionPayment​

Adição

get/responses/200/data/items/society/products/items

Adicionado - minimumRequirement​

Adição

get/responses/200/data/items/society/products/items

Adicionado - targetAudience​

Adição

get/responses/200/data/items/society/products/items

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items

Adicionado - "contributionTax"

Adição

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'modality'

Remoção

required

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'premiumUpdateIndex'

Remoção

required

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'otherGuaranteedValues'

Remoção

required

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'targetAudience'

Remoção

required

get/responses/200/data/items/society/products/items/additional

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/additional

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/additional

Alterado - description

Alteração

\-SORTEIO  
\-SERVICOS\_ASSISTENCIAS\_COMPLEMENTARES\_PAGO

\-SERVICOS\_ASSISTENCIA\_COMPLEMENTARES\_GRATUITO

OUTROS

NAO\_HA

\-SORTEIO  
\-SERVICOS\_ASSISTENCIAS\_COMPLEMENTARES\_PAGO

\-SERVICOS\_ASSISTENCIA\_COMPLEMENTARES\_GRATUITO

\- OUTROS  

get/responses/200/data/items/society/products/items/additional

Alterado - nome do campo

Alteração

additional

planAdditional

get/responses/200/data/items/society/products/items/additional/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/ageAdjustment

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/ageAdjustment

Adicionado - "description"

Adição

Reenquadramento etário

get/responses/200/data/items/society/products/items/ageAdjustment/criterias

Adicionado - "description"

Adição

Critério para reenquadramento etário

get/responses/200/data/items/society/products/items/ageAdjustment/criterias/items

Adicionado - minItens

Adição

1

get/responses/200/data/items/society/products/items/ageAdjustment/criterias/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/ageAdjustment/frequency

Removido - maxLength

Remoção

get/responses/200/data/items/society/products/items/assistanceTypes/items

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/assistanceTypes/items

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/assistanceTypes/items/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/assistanceTypesAdditionalInfos/items

Adicionado - minItens

Adição

0

get/responses/200/data/items/society/products/items/assistanceTypesAdditionalInfos/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/code

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/code

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/contributionPayment

Removido - "required"

Remoção

get/responses/200/data/items/society/products/items/contributionPayment

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethod

Alterado - "description"

Alteração

Forma de pagamento da contribuição.

-   CARTAO\_CREDITO
    
-   DEBITO\_CONTA
    
-   DEBITO\_CONTA\_POUPANCA
    
-   BOLETO\_BANCARIO
    
-   PIX
    
-   TED\_DOC
    
-   CONSIGNACAO\_FOLHA\_PAGAMENTO
    
-   PONTOS\_PROGRAMA\_BENEFICIO
    
-   OUTROS
    
-   NA
    

Forma de pagamento da contribuição.

-   CARTAO\_CREDITO
    
-   DEBITO\_CONTA
    
-   DEBITO\_CONTA\_POUPANCA
    
-   BOLETO\_BANCARIO
    
-   PIX
    
-   TED\_DOC
    
-   CONSIGNACAO\_FOLHA\_PAGAMENTO
    
-   PONTOS\_PROGRAMA\_BENEFICIO
    
-   OUTROS
    

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethod

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethod

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethod/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethodAdditionalInfo

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/contributionPayment/contributionPaymentMethodAdditionalInfo

Adicionado - maxLength

Adição

140

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicity

Alterado - "description"

Alteração

Periodicidade de pagamento da contribuição.

-   MENSAL
    
-   UNICA
    
-   ANUAL
    
-   TRIMESTRAL
    
-   SEMESTRAL
    
-   BIMESTRAL
    
-   OUTROS
    
-   NA
    

Periodicidade de pagamento da contribuição.

-   MENSAL
    
-   UNICA
    
-   ANUAL
    
-   TRIMESTRAL
    
-   SEMESTRAL
    
-   BIMESTRAL
    
-   OUTROS
    

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicity

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicity

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicity/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicityAdditionalInfo

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/contributionPayment/contributionPeriodicityAdditionalInfo

Adicionado - maxLength

Adição

140

get/responses/200/data/items/society/products/items/coverages

Adicionado - "description"

Adição

Conjunto de informações referente a cobertura

get/responses/200/data/items/society/products/items/coverages/items

Adicionado - coveragePeriod

Adição

get/responses/200/data/items/society/products/items/coverages/items

Removido obrigatóriedade no campo 'type'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/coverages/items

Adicionado - minItens

Adição

1

get/responses/200/data/items/society/products/items/coverages/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/coverages/items/attributes

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/coverages/items/attributes

Removido obrigatóriedade no campo 'indemnityPaymentMethod'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items/attributes

Removido obrigatóriedade no campo 'excludedRisks'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items/attributes

Removido obrigatóriedade no campo 'profitModality'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisks/items

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisks/items

Adicionado - maxLength

Adição

50

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisks/items/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Adicionado - maxLength

Adição

1024

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/amount​

Adicionado - minimum

Adição

0

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit

Alterado - "description"

Alteração

Informar o critério de carência para a cobertura&#58;<br><ol><li>Dias</li><li>Meses</li><li>Não se aplica</li><li>NA</li></ol>

Informar o critério de carência para a cobertura:

1.  Dias
    
2.  Meses
    

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit

Alterado - description

Alteração

Informar o critério de carência para a cobertura:<br><ol><li>Dias</li><li>Meses</li><li>Não se aplica</li></ol>

Informar o critério de carência para a cobertura:  
1\. Dias  
2\. Meses

get/responses/200/data/items/society/products/items/coverages/items/attributes/gracePeriod/unit/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiableDeadline

Adicionado - "example"

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriod

Alterado - "description"

Alteração

Listagem do pagamento para cada benefício:

1.  Quantidade determinada de parcelas;
    
2.  Até o fim de ciclo determinado;
    
3.  NA.
    

Observação: Se for pagamento único, este campo não deve ser informado.

Listagem do pagamento para cada benefício:

1.  Quantidade determinada de parcelas;
    
2.  Até o fim de ciclo determinado.
    

Observação: Se for pagamento único, este campo não deve ser informado.

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriod

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriod

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnifiablePeriod/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethod

Alterado - "description"

Alteração

Modalidade de pagamento da indenização, a considerar os domínios abaixo:

1.  Único
    
2.  Sob a forma de renda
    
3.  NA
    

Modalidade de pagamento da indenização, a considerar os domínios abaixo:

1.  Único
    
2.  Sob a forma de renda
    

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethod

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethod

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/coverages/items/attributes/indemnityPaymentMethod/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/amount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/amount

Adicionado - "description"

Adição

Valor mínimo/máximo de cobertura diária ou parcelada

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/amount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/amount

Adicionado - "description"

Adição

Valor mínimo/máximo de cobertura diária ou parcelada

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

get/responses/200/data/items/society/products/items/coverages/items/attributes/profitModality

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/attributes/profitModality

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/coverages/items/attributes/profitModality/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/coverages/items/coveragePeriod

Mandatoriedade

Alteração

Opcional

Obrigatorio

get/responses/200/data/items/society/products/items/coverages/items/type

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/coverages/items/type

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/coverages/items/type/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/coverages/items/typeAdditionalInfos/items

Adicionado - minItens

Adição

0

get/responses/200/data/items/society/products/items/coverages/items/typeAdditionalInfos/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/financialRegimeContractType

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
    

get/responses/200/data/items/society/products/items/financialRegimeContractType

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/financialRegimeContractType

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/financialRegimeContractType/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/minimumRequirement

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/minimumRequirement

Adicionado - "description"

Adição

Requisitos mínimos

get/responses/200/data/items/society/products/items/minimumRequirement

Removido obrigatóriedade no campo 'contractType'

Remoção

required

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - maxLength

Adição

1024

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Alterado - "description"

Alteração

O tipo de serviço contratado. A considerar os domínios abaixo:

1.  Coletivo;
    
2.  Individual.
    
3.  NA
    

O tipo de serviço contratado. A considerar os domínios abaixo:

1.  Coletivo;
    
2.  Individual.
    

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/minimumRequirement/contractType/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/modality

Alterado - "description"

Alteração

<ol><li>Funeral</li><li>Prestamista (exceto Habitacional e Rural)</li><li>Viagem</li><li>Educacional</li><li>Dotal (Misto e Puro)</li><li>Acidentes Pessoais</li><li>Vida</li><li>Perda do Certificado de Habilitação de Voo – PCHV</li><li>Doenças Graves ou Doença Terminal</li><li>Desemprego/ Perda de Renda</li><li>Eventos Aleatórios</li><li>Pecúlio</li><li>Pensão prazo certo</li><li>Pensão menores 21 anos</li><li>Pensão menores 24 anos</li><li>Pensão cônjuge vitalícia</li><li>Pensão cônjuge temporária</li><li>NA</li></ol>

<ol><li>Funeral</li><li>Prestamista (exceto Habitacional e Rural)</li><li>Viagem</li><li>Educacional</li><li>Dotal (Misto e Puro)</li><li>Acidentes Pessoais</li><li>Vida</li><li>Perda do Certificado de Habilitação de Voo – PCHV</li><li>Doenças Graves ou Doença Terminal</li><li>Desemprego/ Perda de Renda</li><li>Eventos Aleatórios</li><li>Pecúlio</li><li>Pensão prazo certo</li><li>Pensão menores 21 anos</li><li>Pensão menores 24 anos</li><li>Pensão cônjuge vitalícia</li><li>Pensão cônjuge temporária</li></ol>

get/responses/200/data/items/society/products/items/modality

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/modality

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/modality/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/name

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/name

Adicionado - maxLength

Adição

80

get/responses/200/data/items/society/products/items/otherGuaranteedValues

Alterado - "description"

Alteração

1.  Saldamento
    
2.  Benefício Prolongado
    
3.  Não se aplica
    
4.  NA
    

1.  Saldamento
    
2.  Benefício Prolongado
    

get/responses/200/data/items/society/products/items/otherGuaranteedValues

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/otherGuaranteedValues

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/otherGuaranteedValues/enum

Removido - "NAO\_APLICA"

Remoção

enum

get/responses/200/data/items/society/products/items/otherGuaranteedValues/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/planAdditional

Adicionado - "description"

Adição

Adicional do plano

get/responses/200/data/items/society/products/items/pmbacRemuneration

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/pmbacRemuneration

Adicionado - "description"

Adição

Atualização/ Remuneração da PMBaC

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes

Adicionado - "description"

Adição

Índice utilizado na atualização da PMBaC

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items

Adicionado - minItens

Adição

0

get/responses/200/data/items/society/products/items/pmbacRemuneration/updateIndexes/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/premiumUpdateIndex

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/premiumUpdateIndex

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/premiumUpdateIndex/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/reclaim

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/reclaim

Adicionado - "description"

Adição

Resgate

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Adicionado - "description"

Adição

Período de carência

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Removido obrigatóriedade no campo 'unit'

Remoção

required

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Alterado - "description"

Alteração

Informar o critério de carência para resgate:

1.  Dias;
    
2.  Meses;
    
3.  Não se aplica.
    
4.  NA
    

Informar o critério de carência para resgate:

1.  Dias;
    
2.  Meses;
    

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit

Adicionado - maxLength

Adição

20

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit/enum

Removido - "NAO\_APLICA"

Remoção

enum

get/responses/200/data/items/society/products/items/reclaim/gracePeriod/unit/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/reclaim/table

Adicionado - "description"

Adição

Percentual de resgate para PMBaC para cada conjunto aplicável

get/responses/200/data/items/society/products/items/reclaim/table/items

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/reclaim/table/items

Adicionado - minItens

Adição

1

get/responses/200/data/items/society/products/items/reclaim/table/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/reclaim/table/items/finalMonthRange

Removido - maxLength

Remoção

get/responses/200/data/items/society/products/items/reclaim/table/items/finalMonthRange

Adicionado - "description"

Adição

Mês final do range

get/responses/200/data/items/society/products/items/reclaim/table/items/initialMonthRange

Removido - maxLength

Remoção

get/responses/200/data/items/society/products/items/reclaim/table/items/initialMonthRange

Adicionado - "description"

Adição

Mês inicial do range

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
    

get/responses/200/data/items/society/products/items/targetAudience

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/targetAudience

Adicionado - maxLength

Adição

23

get/responses/200/data/items/society/products/items/targetAudience/enum

Removido - "NA"

Remoção

enum

get/responses/200/data/items/society/products/items/termsAndConditions

Adicionado - "description"

Adição

Conjunto de informações referente aos termos e condições conforme número do processo SUSEP

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - minItens

Adição

1

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - maxItens

Adição

2147483647

get/responses/200/data/items/society/products/items/termsAndConditions/items/detail

Adicionado - minLength

Adição

1

get/responses/200/data/items/society/products/items/termsAndConditions/items/detail

Adicionado - maxLength

Adição

1024

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber​

Alterado - Pattern

Alteração

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$|^(NA)$

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$​

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber

Alterado - "pattern"

Alteração

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$|^(NA)$

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$

get/responses/200/data/items/society/produts/items/coverages/items/attributes/maxValue/currency​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

get/responses/200/data/items/society/produts/items/coverages/items/attributes/minValue/currency​

Alterado - Pattern

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$​

get/responses/200/data/reclaim/gracePeriod/amount​

Adicionado - minimum

Adição

0

get/responses/200/data/reclaim/table/items/finalMonthRange​

Removido - MaxLength

Remoção

2

get/responses/200/data/reclaim/table/items/finalMonthRange​

Adicionado - minimum

Adição

1

get/responses/200/data/reclaim/table/items/finalMonthRange​

Adicionado - maximum

Adição

12​

get/responses/200/data/reclaim/table/items/initialMonthRange​

Removido - MaxLength

Remoção

2

get/responses/200/data/reclaim/table/items/initialMonthRange​

Adicionado - minimum

Adição

1

get/responses/200/data/reclaim/table/items/initialMonthRange​

Adicionado - maximum

Adição

12​

## GET /survival-coverages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

N° Proposta

Data homologação

get/responses/200/data

Adicionado - "description"

Adição

Conjunto de informações referente ao produto previdência

PDA263

get/responses/200/data/items

Removido - name

Remoção

PDA249

get/responses/200/data/items

Removido - code​

Remoção

PDA249

get/responses/200/data/items

Removido - segment​

Remoção

PDA249

get/responses/200/data/items

Removido - modality​

Remoção

PDA249

get/responses/200/data/items

Removido - additionalInfo​

Remoção

PDA249

get/responses/200/data/items

Removido - termsAndConditions

Remoção

PDA249

get/responses/200/data/items

Removido - type​

Remoção

PDA249

get/responses/200/data/items

Removido - defferalPeriod​

Remoção

PDA249

get/responses/200/data/items

Removido - grantPeriodBenefit​

Remoção

PDA249

get/responses/200/data/items

Removido - costs​

Remoção

PDA249

get/responses/200/data/items

Removido - minimumRequirement​

Remoção

PDA249

get/responses/200/data/items

Removido - targetAudience​

Remoção

PDA249

get/responses/200/data/items

Adicionado - minItens

Adição

1

PDA255

get/responses/200/data/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/participant

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/participant/brand

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/participant/brand

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/participant/cnpjNumber`​`  

Alterado - Pattern

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/participant/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/participant/cnpjNumber

Adicionado - minLength

Adição

14

PDA253

get/responses/200/data/items/participant/cnpjNumber

Adicionado - maxLength

Adição

14

PDA253

get/responses/200/data/items/participant/name

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/participant/name

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/participant/urlComplementaryList​

Alterado - Pattern

Alteração

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%._\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%_\\+.~#?&\\/\\/=\]\*))|(NA)$

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$​

PDA252

get/responses/200/data/items/participant/urlComplementaryList

Alterado - "pattern"

Alteração

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))|(NA)$

^((https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*))$

PDA252

get/responses/200/data/items/society

Adicionado - products

Adição

minItems: 1​

description: Lista de produtos de uma empresa.

PDA249

get/responses/200/data/items/society

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society

Adicionado obrigatóriedade no campo 'products'

Adição

required

PDA252

get/responses/200/data/items/society/brand​

Adicionado - Brand

Adição

Tipo: string​

maxLength: 80​

minLenght: 1  
example: Marca no OPIN​

pattern: ^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$​

Descrição: Nome da Marca reportada pelo participante do Open Insurance. O conceito a que se refere a 'marca' é em essência uma promessa da empresa em fornecer uma série específica de atributos, benefícios e serviços uniformes aos clientes​

Mandatoriedade do campo: Opcional ​

PDA250

get/responses/200/data/items/society/cnpjNumber​

Alterado - Pattern

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/society/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/society/cnpjNumber

Adicionado - minLength

Adição

14

PDA253

get/responses/200/data/items/society/cnpjNumber

Adicionado - maxLength

Adição

14

PDA253

get/responses/200/data/items/society/name

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/name

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/society/products/items

Adicionado - name

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - code​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - segment​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - modality​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - additionalInfo​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - termsAndConditions

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - type​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - defferalPeriod​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - grantPeriodBenefit​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - costs​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - minimumRequirement​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - targetAudience​

Adição

PDA249

get/responses/200/data/items/society/products/items

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'segment'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'modality'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'targetAudience'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items/additionalInfo

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/additionalInfo

Adicionado - maxLength

Adição

1024

PDA253

get/responses/200/data/items/society/products/items/code

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/code

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/society/products/items/costs

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/costs/loadingAntecipated

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/costs/loadingLate

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod

Adicionado - premiumPaymentMethodsAdditionalInfo

Adição

PDA258

get/responses/200/data/items/society/products/items/defferalPeriod

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod

Removido obrigatóriedade no campo 'updateIndex'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/betweenPortabilityRequests​

Adicionado - minimum

Adição

0

PDA254

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/betweenPortabilityRequests

Alterado - "type"

Alteração

number

integer

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/betweenRedemptionRequests​

Adicionado - minimum

Adição

0

PDA254

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/betweenRedemptionRequests

Alterado - "type"

Alteração

number

integer

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/portability​

Adicionado - minimum

Adição

0

PDA254

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/portability

Alterado - "type"

Alteração

number

integer

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/redemption​

Adicionado - minimum

Adição

0

PDA254

get/responses/200/data/items/society/products/items/defferalPeriod/gracePeriod/redemption

Alterado - "type"

Alteração

number

integer

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds

Adicionado - "description"

Adição

Lista com as informações do(s) Fundo(s) de Investimento(s) disponíveis para o período de diferimento/acumulação ou de concessão

PDA263

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items

Adicionado - minItens

Adição

0

PDA255

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items

Removido obrigatóriedade no campo 'typePerformanceFee'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/cnpjNumber​

Alterado - Pattern

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/cnpjNumber

Adicionado - minLength

Adição

14

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/cnpjNumber

Adicionado - maxLength

Adição

14

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/currency​

Alterado - Pattern

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$​

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/currency

Adicionado - minLength

Adição

3

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/currency

Adicionado - maxLength

Adição

3

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumContributionAmount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumContributionAmount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumContributionAmount

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumContributionAmount

Adicionado - maxLength

Adição

21

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumMathematicalProvisionAmount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumMathematicalProvisionAmount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumMathematicalProvisionAmount

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/minimumMathematicalProvisionAmount

Adicionado - maxLength

Adição

21

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/name

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/name

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/properties

Adicionado - "minimumContributionValue"

Adição

PDA267

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/typePerformanceFee

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/typePerformanceFee

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/typePerformanceFee/enum

Removido - "NAO\_APLICA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/investmentFunds/items/typePerformanceFee/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums

Adicionado - "description"

Adição

Valor mínimo do prêmio/contribuição aceita pela sociedade ao plano (identificar valor mensal e/ou aporte único)

PDA263

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items

Adicionado - minItens

Adição

0

PDA255

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/amount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/amount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/currency​

Alterado - Pattern

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$​

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/currency

Adicionado - minLength

Adição

3

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/currency

Adicionado - maxLength

Adição

3

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicity

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicity

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicity/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicityDescription

Alterado - "minLength"

Alteração

1

5

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicityDescription

Alterado - "maxLength"

Alteração

20

15

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicityDescription

Removido - "enum"

Remoção

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicityDescription

Adicionado - "description"

Adição

Descrição da periodicidade do prêmio/contribuição

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/minimumPremiums/items/periodicityDescription

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/otherMinimumPerformanceGarantees

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/otherMinimumPerformanceGarantees

Adicionado - maxLength

Adição

12

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/portabilityPaymentTerm​

Adicionado - minimum

Adição

0

PDA254

get/responses/200/data/items/society/products/items/defferalPeriod/portabilityPaymentTerm

Alterado - "type"

Alteração

number

integer

PDA262

get/responses/200/data/items/society/products/items/defferalPeriod/premiumPaymentMethods

Adicionado - "description"

Adição

Meio de pagamento escolhido pelo segurado

PDA263

get/responses/200/data/items/society/products/items/defferalPeriod/premiumPaymentMethods/items

Adicionado - minItens

Adição

0

PDA255

get/responses/200/data/items/society/products/items/defferalPeriod/premiumPaymentMethods/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/defferalPeriod/properties

Adicionado - "otherMinGuaranteesPercentage"

Adição

PDA267

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex

Alterado - "description"

Alteração

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:

1.  IPCA (IBGE);
    
2.  IGP-M (FGV);
    
3.  INPC (IBGE).
    
4.  Não se aplica
    
5.  NA
    

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:

1.  IPCA (IBGE);
    
2.  IGP-M (FGV);
    
3.  INPC (IBGE).
    

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex

Alterado - description

Alteração

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:  
1\. IPCA (IBGE);  
2\. IGP-M (FGV);  
3\. INPC (IBGE).  
4\. Não se aplica

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:  
1\. IPCA (IBGE);  
2\. IGP-M (FGV);  
3\. INPC (IBGE).

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex/enum

Removido - "NAO\_SE\_APLICA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/defferalPeriod/updateIndex/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit

Removido obrigatóriedade no campo 'updateIndex'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/biometricTable

Adicionado - "description"

Adição

Obrigatório caso modalidade de renda seja diferente de (PAGAMENTO\_UNICO, RENDA\_PRAZO\_CERTO). Tábua biométrica é o instrumento que ...

PDA263

get/responses/200/data/items/society/products/items/grantPeriodBenefit/biometricTable/items

Adicionado - minItens

Adição

0

PDA255

get/responses/200/data/items/society/products/items/grantPeriodBenefit/biometricTable/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/grantPeriodBenefit/incomeModalities

Adicionado - "description"

Adição

Modalidades de renda disponíveis para contratação. A considerar os seguintes domínios

PDA263

get/responses/200/data/items/society/products/items/grantPeriodBenefit/incomeModalities/items

Adicionado - minItens

Adição

1

PDA255

get/responses/200/data/items/society/products/items/grantPeriodBenefit/incomeModalities/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds

Adicionado - "description"

Adição

Lista com as informações do(s) Fundo(s) de Investimento(s) disponíveis para o período de diferimento/acumulação ou de concessão.

PDA263

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items

Adicionado - minItens

Adição

0

PDA255

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items

Removido obrigatóriedade no campo 'typePerformanceFee'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/cnpjNumber​

Alterado - Pattern

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/cnpjNumber

Adicionado - minLength

Adição

14

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/cnpjNumber

Adicionado - maxLength

Adição

14

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/currency​

Alterado - Pattern

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$​

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/currency

Alterado - "pattern"

Alteração

^(\[A-Z\]{3})$|^(NA)$

^(\[A-Z\]{3})$

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/currency

Adicionado - minLength

Adição

3

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/currency

Adicionado - maxLength

Adição

3

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/minimumContributionAmount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/minimumContributionAmount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/minimumMathematicalProvisionAmount​

Alterado - Pattern

Alteração

^(\\d{1,16}\\.\\d{2,4})$​

^(\\d{1,16}\\.\\d{2,4})$​

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/minimumMathematicalProvisionAmount

Alterado - "pattern"

Alteração

^(\\d{1,16}\\.\\d{2,4})$|^(NA)$

^(\\d{1,16}\\.\\d{2,4})$

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/name

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/name

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/properties

Adicionado - "minimumContributionValue"

Adição

PDA267

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/typePerformanceFee

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/typePerformanceFee

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/typePerformanceFee/enum

Removido - "NAO\_APLICA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/investmentFunds/items/typePerformanceFee/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex

Alterado - "description"

Alteração

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:

1.  IPCA (IBGE);
    
2.  IGP-M (FGV);
    
3.  INPC (IBGE).
    
4.  Não se aplica
    
5.  NA
    

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:

1.  IPCA (IBGE);
    
2.  IGP-M (FGV);
    
3.  INPC (IBGE).
    

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex

Alterado - description

Alteração

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:  
1\. IPCA (IBGE);  
2\. IGP-M (FGV);  
3\. INPC (IBGE).  
4\. Não se aplica

Índice utilizado na atualização do prêmio e do capital segurado, caso critério de atualização por meio de índice:  
1\. IPCA (IBGE);  
2\. IGP-M (FGV);  
3\. INPC (IBGE).

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex/enum

Removido - "NAO\_SE\_APLICA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/grantPeriodBenefit/updateIndex/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/minimumRequirement

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/minimumRequirement

Adicionado - "description"

Adição

Requerimento mínimo do serviço contratado

PDA263

get/responses/200/data/items/society/products/items/minimumRequirement

Removido obrigatóriedade no campo 'contractType'

Remoção

required

PDA252

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - maxLength

Adição

1024

PDA253

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Alterado - "description"

Alteração

O tipo de serviço contratado. A considerar os domínios abaixo:

1.  Coletivo Averbado;
    
2.  Coletivo instituído;
    
3.  Individual.
    
4.  NA
    

O tipo de serviço contratado. A considerar os domínios abaixo:

1.  Coletivo Averbado;
    
2.  Coletivo instituído;
    
3.  Individual.
    

PDA252

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/minimumRequirement/contractType

Adicionado - maxLength

Adição

30

PDA253

get/responses/200/data/items/society/products/items/minimumRequirement/contractType/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/modality

Alterado - "description"

Alteração

1.  Contribuição Variável;
    
2.  Benefício Definido.
    
3.  NA
    

1.  Contribuição Variável;
    
2.  Benefício Definido.
    

PDA252

get/responses/200/data/items/society/products/items/modality

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/modality

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/modality/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/name

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/name

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/society/products/items/segment

Alterado - "description"

Alteração

Segmento do qual se trata o produto contratado

1.  Seguro de Pessoas
    
2.  Previdência
    
3.  NA
    

Segmento do qual se trata o produto contratado

1.  Seguro de Pessoas
    
2.  Previdência
    

PDA252

get/responses/200/data/items/society/products/items/segment

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/segment

Adicionado - maxLength

Adição

20

PDA253

get/responses/200/data/items/society/products/items/segment/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/targetAudience

Alterado - "description"

Alteração

A considerar os domínios abaixo:

1.  Pessoa Natural
    
2.  Pessoa Jurídica
    
3.  NA
    

A considerar os domínios abaixo:

1.  Pessoa Natural
    
2.  Pessoa Jurídica
    

PDA252

get/responses/200/data/items/society/products/items/targetAudience

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/targetAudience

Adicionado - maxLength

Adição

30

PDA253

get/responses/200/data/items/society/products/items/targetAudience/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/items/society/products/items/termsAndConditions

Adicionado - "description"

Adição

Conjunto de informações referente aos termos e condições conforme número do processo SUSEP

PDA263

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - "x-regulatory-required"

Adição

PDA252

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - minItens

Adição

1

PDA255

get/responses/200/data/items/society/products/items/termsAndConditions/items

Adicionado - maxItens

Adição

2147483647

PDA255

get/responses/200/data/items/society/products/items/termsAndConditions/items/detail

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/termsAndConditions/items/detail

Adicionado - maxLength

Adição

1024

PDA253

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber​

Alterado - Pattern

Alteração

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$|^(NA)$

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$​

PDA252

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber

Alterado - "pattern"

Alteração

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$|^(NA)$

^(\\d{5}\\.\\d{6}\\/\\d{4}-\\d{2}$|^\\d{2}\\.\\d{6}\\/\\d{2}-\\d{2}$|^\\d{3}-\\d{5}\\/\\d{2}$|^\\d{5}\\.\\d{6}\\/\\d{2}-\\d{2})$

PDA252

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/termsAndConditions/items/susepProcessNumber

Adicionado - maxLength

Adição

30

PDA253

get/responses/200/data/items/society/products/items/type

Alterado - "description"

Alteração

1.  PGBL
    
2.  PRGP
    
3.  PAGP
    
4.  PRSA
    
5.  PRI
    
6.  PDR
    
7.  VGBL
    
8.  VRGP
    
9.  VAGP
    

10\. VRSA  
11\. VRI  
12\. VDR  
13\. Demais produtos de Previdência.  
14\. NA

1.  PGBL
    
2.  PRGP
    
3.  PAGP
    
4.  PRSA
    
5.  PRI
    
6.  PDR
    
7.  VGBL
    
8.  VRGP
    
9.  VAGP
    

10\. VRSA  
11\. VRI  
12\. VDR  
13\. Demais produtos de Previdência.

PDA252

get/responses/200/data/items/society/products/items/type

Adicionado - minLength

Adição

1

PDA253

get/responses/200/data/items/society/products/items/type

Adicionado - maxLength

Adição

80

PDA253

get/responses/200/data/items/society/products/items/type

Adicionado - "example"

Adição

PGBL

PDA264

get/responses/200/data/items/society/products/items/type/enum

Removido - "NA"

Remoção

enum

PDA252

get/responses/200/data/society/products/defferalPeriod/minimumPremi  
ums/items/periodicity

Alterado - nome do campo

Alteração

periodicity

periodicityDescription

PDA260

get/responses/200/data/society/products/termsAndConditions/items/detail

Alterado - nome do campo

Alteração

detail

contractTermsCond  
itions

PDA260
