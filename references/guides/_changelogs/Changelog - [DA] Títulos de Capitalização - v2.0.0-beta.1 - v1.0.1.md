# Changelog - [DA] Títulos de Capitalização - v2.0.0-beta.1 - v1.0.1

## GET /`bonds`

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/termsAndConditions/detail​

Alterado - nome do campo

Alteração

detail

termsRegulations   

get/responses/200/data/capitalizationPeriod/updateIndexAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data/capitalizationPeriod/contributionAmount\[\]/periodicityAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data/contributionPayment/paymentMethodAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data/contributionPayment/updateIndexAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data/society/products\[\]/draws\[\]/timeIntervalAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data\[\]/society/products\[\]/draws\[\]/ruleDescription​

Alterado - "example"

Alteração

Sorteios próprios às terças-feiras. Toda quarta-feira sorteios através da loteria federal​

get/responses/200/data\[\]/society/products\[\]/quotas\[\]/quota​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/validity​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/serieSize​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/capitalizationPeriod/earlyRedemptions\[\]/quota​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/capitalizationPeriod/gracePeriodRedemption​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/latePayment/suspensionMonths​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/draws\[\]/quantity​

Removido - "maxlength"

Remoção

get/responses/200/data\[\]/society/products\[\]/draws\[\]/prizeMultiplier​

Removido - "maxlength"

Remoção

/data\[\]/society/products\[\]/quotas\[\]/quota​

Adicionado - "maximum"

Adição

2147483647​

/data\[\]/society/products\[\]/validity​

Adicionado - "maximum"

Adição

2147483647​

/data\[\]/society/products\[\]/serieSize​

Adicionado - "maximum"

Adição

2147483647​

/data\[\]/society/products\[\]/capitalizationPeriod/earlyRedemptions\[\]/quota​

Adicionado - "maximum"

Adição

2147483647​

/data\[\]/society/products\[\]/capitalizationPeriod/gracePeriodRedemption​

Adicionado - "maximum"

Adição

2147483647​

/data\[\]/society/products\[\]/draws\[\]/prizeMultiplier​

Adicionado - "maximum"

Adição

2147483647​

/data\[\]/society/products\[\]/termsAndConditions/susepProcessNumber​

Alterado - "minlength"

Alteração

 2​

/data\[\]/participant/brand​

Alterado - "minlength"

Alteração

1​

/data\[\]/participant/name​

Alterado - "minlength"

Alteração

1​

/data\[\]/society/name​

Alterado - "minlength"

Alteração

1​

/data\[\]/society/products\[\]/name​

Alterado - "minlength"

Alteração

1​

/data\[\]/society/products\[\]/code​

Alterado - "minlength"

Alteração

1​

/data\[\]/society/products\[\]/termsAndConditions/susepProcessNumber​

Alterado - "maxlength"

Alteração

30​

/data\[\]/participant/brand​

Alterado - "maxlength"

Alteração

80​

/data\[\]/participant/name​

Alterado - "maxlength"

Alteração

80​

/data\[\]/society/name​

Alterado - "maxlength"

Alteração

80​

/data\[\]/society/products\[\]/name​

Alterado - "maxlength"

Alteração

80​

/data\[\]/society/products\[\]/code​

Alterado - "maxlength"

Alteração

100​

get/responses/200/data/items

Removido - "required"

Remoção

get/responses/200/data/items/properties

Removido - "name"

Remoção

get/responses/200/data/items/properties

Removido - "code"

Remoção

get/responses/200/data/items/properties

Removido - "modality"

Remoção

get/responses/200/data/items/properties

Removido - "costType"

Remoção

get/responses/200/data/items/properties

Removido - "termsAndConditions"

Remoção

get/responses/200/data/items/properties

Removido - "quotas"

Remoção

get/responses/200/data/items/properties

Removido - "validity"

Remoção

get/responses/200/data/items/properties

Removido - "serieSize"

Remoção

get/responses/200/data/items/properties

Removido - "capitalizationPeriod"

Remoção

get/responses/200/data/items/properties

Removido - "latePayment"

Remoção

get/responses/200/data/items/properties

Removido - "contributionPayment"

Remoção

get/responses/200/data/items/properties

Removido - "redemptionPercentageEndTerm"

Remoção

get/responses/200/data/items/properties

Removido - "finalRedemptionRate"

Remoção

get/responses/200/data/items/properties

Removido - "draws"

Remoção

get/responses/200/data/items/properties

Removido - "additionalInfo"

Remoção

get/responses/200/data/items/properties

Removido - "minimumRequirementDetails"

Remoção

get/responses/200/data/items/properties

Removido - "targetAudience"

Remoção

get/responses/200/data/items/participant/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/participant/urlComplementaryList

Alterado - "pattern"

Alteração

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)|(NA)$

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society/properties

Adicionado obrigatoriedade no campo 'brand'

Adição

required

get/responses/200/data/items/society/properties

Adicionado - "products"

Adição

get/responses/200/data/items/society/properties

Adicionado - "brand"

Adição

get/responses/200/data/items/society/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/meta/totalRecords

Alterado - "example"

Alteração

1

10

get/responses/400//meta/totalRecords

Alterado - "example"

Alteração

1

10

get/responses/404//meta/totalRecords

Alterado - "example"

Alteração

1

10

get/responses/405//meta/totalRecords

Alterado - "example"

Alteração

1

10

/data\[\]/society/products\[\]/​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/modality​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/costType​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/termsAndConditions/susepProcessNumber​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/capitalizationPeriod/updateIndex​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/periodicity​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/contributionPayment/paymentMethod​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/contributionPayment/updateIndex​

Alterado - "obrigatoriedade"

Alteração

required

/data\[\]/society/products\[\]/draws\[\]/timeInterval​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data\[\]/society/products\[\]/modality​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/costType​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/capitalizationPeriod/updateIndex​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/periodicity​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/contributionPayment/paymentMethod​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/contributionPayment/updateIndex​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/draws\[\]/timeInterval​

Removido - "NA"

Remoção

get/responses/200/data\[\]/society/products\[\]/targetAudience​

Removido - "NA"

Remoção

/data\[\]/participant/brand​

Adicionado - x-regulatory-required

Adição

/data\[\]/participant/name​

Adicionado - x-regulatory-required

Adição

/data\[\]/participant/cnpjNumber​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/name​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/cnpjNumber​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/modality​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/costType​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/termsAndConditions/susepProcessNumber​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/termsAndConditions/detail​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/quotas\[\]/quota​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/quotas\[\]/capitalizationQuota​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/quotas\[\]/raffleQuota​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/quotas\[\]/chargingQuota​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/validity​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/serieSize​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/interestRate​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/updateIndex​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/periodicity​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/minimum​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/maximum​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/allowedValue​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/earlyRedemptions\[\]​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/redemptionPercentageEndTerm​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/capitalizationPeriod/gracePeriodRedemption​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/latePayment/suspensionMonths​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/latePayment/periodExtensionOption​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/contributionPayment/paymentMethod​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/contributionPayment/updateIndex​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/redemptionPercentageEndTerm​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/finalRedemptionRate​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/timeInterval​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/quantity​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/prizeMultiplier​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/earlySettlementRaffle​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/mandatoryContemplation​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/ruleDescription​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/draws\[\]/minimumContemplationProbability​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/minimumRequirementDetails​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/targetAudience​

Adicionado - x-regulatory-required

Adição

/data\[\]/society/products\[\]/latePayment/suspensionMonths

Alterado - type

Alteração

Number

Integer

/data\[\]/society/products\[\]/draws/quantity

Alterado - type

Alteração

Number

Integer

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount/minimum

Alterado - pattern

Alteração

^(d{1,16}\\.\\d{2,4})$|^(NA)$

^(d{1,16}\\.\\d{2,4})$

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount/maximum

Alterado - pattern

Alteração

^(d{1,16}\\.\\d{2,4})$|^(NA)$

^(d{1,16}\\.\\d{2,4})$

/data\[\]/society​

Alterado - "description"

Alteração

Conjunto de informações relativas à seguradora do produto de open insurance

Dados sobre a seguradora participante do OPIN​

/data\[\]/society/cnpjNumber​

Alterado - "description"

Alteração

CNPJ da sociedade seguradora participante do OPIN​

/data\[\]/society/products\[\]​

Alterado - "description"

Alteração

Lista de produtos de uma empresa

Lista de produtos da sociedade seguradora participante do OPIN​

/data\[\]/society/products\[\]/costType​

Alterado - "description"

Alteração

Pagamento efetuado ao subscritor à sociedade de capitalização para aquisição do título de capitalização, podendo ser única, periódica ou mensal.  
1\. Pagamento Único  
2\. Pagamento Mensal  
3\. Pagamento Periódico

Pagamento efetuado ao subscritor à sociedade de capitalização para aquisição do título de capitalização, podendo ser única, periódica ou mensal.​

/data\[\]/society/products\[\]/termsAndConditions​

Alterado - "description"

Alteração

Informações relativas aos termos e condições​

/data\[\]/society/products\[\]/termsAndConditions/termsRegulations

Alterado - "description"

Alteração

'Representam as Condições Gerais, Condições Especiais e Condições ou Cláusulas Particulares de um mesmo produto. (Circular SUSEP 321/06). Campo aberto (possibilidade de incluir URL)'

Campo aberto para representar as Condições Gerais, Condições Especiais e Condições ou Cláusulas Particulares de um mesmo produto, confrome Circular SUSEP 321/06. Pode-se incluir URL que apresenta esse termos e condições​

/data\[\]/society/products\[\]/modality​

Alterado - "description"

Alteração

1.  Tradicional: A modalidade tradicional tem por objetivo restituir ao titular, ao final do prazo de vigência, no mínimo, o valor total das contribuições efetuadas pelo subscritor, desde que todas as contribuições previstas tenham sido realizadas nas datas programadas. (Res CNSP 384/20)  
    2\. Instrumento de Garantia: A modalidade tem por objetivo propiciar que a provisão matemática para capitalização do título de capitalização seja utilizada para assegurar o cumprimento de obrigação assumida em contrato principal pelo titular perante terceiro. (Res CNSP 384/20)  
    3\. Compra Programada: A modalidade compra programada garante o valor de resgate em moeda corrente nacional, sendo disponibilizada ao assim desejar e sem qualquer outro custo, pelo recebimento do bem e/ou serviço referenciado no subsidiado por acordos comerciais celebrados com indústrias, atacadistas, empresas comerciais ou prestadores de serviço. (Res CNSP 384/20)  
    4\. Popular: A modalidade popular tem por objetivo propiciar a capitalização da contribuição e a participação do titular em sorteios, sem que haja devolução integral do valor pago. (Res CNSP 384/20)  
    5\. Incentivo: A modalidade incentivo tem por objetivo a vinculação a um evento promocional de caráter comercial instituído pelo subscritor para alavancar a venda de seu(s) produto(s) ou serviços ou para fidelizar seus clientes. (Res CNSP 384/20)  
    6\. Filantropia Premiável: A modalidade filantropia premiável é destinada ao subscritor interessado em contribuir com entidades beneficentes de assistências sociais, certificadas nos termos da legislação vigente, e participar de sorteio(s). (Res CNSP 384/20)
    

Modalidades de capitalização permitidas pela Susep para comercialização:                                                                                                                                        

1.  Tradicional: A modalidade tradicional tem por objetivo restituir ao titular, ao final do prazo de vigência, no mínimo, o valor total das contribuições efetuadas pelo subscritor, desde que todas as contribuições previstas tenham sido realizadas nas datas programadas. (Res CNSP 384/20)
    
2.  Instrumento de Garantia: A modalidade tem por objetivo propiciar que a provisão matemática para capitalização do título de capitalização seja utilizada para assegurar o cumprimento de obrigação assumida em contrato principal pelo titular perante terceiro. (Res CNSP 384/20)
    
3.  Compra Programada: A modalidade compra programada garante o valor de resgate em moeda corrente nacional, sendo disponibilizada ao assim desejar e sem qualquer outro custo, pelo recebimento do bem e/ou serviço referenciado no subsidiado por acordos comerciais celebrados com indústrias, atacadistas, empresas comerciais ou prestadores de serviço. (Res CNSP 384/20)
    
4.  Popular: A modalidade popular tem por objetivo propiciar a capitalização da contribuição e a participação do titular em sorteios, sem que haja devolução integral do valor pago. (Res CNSP 384/20)
    
5.  Incentivo: A modalidade incentivo tem por objetivo a vinculação a um evento promocional de caráter comercial instituído pelo subscritor para alavancar a venda de seu(s) produto(s) ou serviços ou para fidelizar seus clientes. (Res CNSP 384/20)
    
6.  Filantropia Premiável: A modalidade filantropia premiável é destinada ao subscritor interessado em contribuir com entidades beneficentes de assistências sociais, certificadas nos termos da legislação vigente, e participar de sorteio(s). (Res CNSP 384/20)​
    

/data\[\]/society/products\[\]/quotas\[\]​

Alterado - "description"

Alteração

Informações relativas às taxas da Quotas praticadas para cada Parcela

Informações relativas às taxas da cotas praticadas para cada parcela​

/data\[\]/society/products\[\]/quotas\[\]/capitalizationQuota​

Alterado - "description"

Alteração

Percentual da contribuição destinado à constituição de capital referente ao direito de resgate. (Resolução CNSP 384/20) Em porcentagem(%).

Percentual da contribuição destinado à constituição de capital referente ao direito de resgate. (Resolução CNSP 384/20)​

/data\[\]/society/products\[\]/quotas\[\]/raffleQuota​

Alterado - "description"

Alteração

'Percentual da contribuição destinado a custear os sorteios, se previstos no plano. (Resolução CNSP 384/20) Em porcentagem(%).'

Percentual da contribuição destinado a custear os sorteios, se previstos no plano. (Resolução CNSP 384/20)​

/data\[\]/society/products\[\]/quotas\[\]/chargingQuota​

Alterado - "description"

Alteração

'Percentual da contribuição destinado aos custos de despesas com corretagem, colocação e administração do título de capitalização, emissão, divulgação, lucro da sociedade de capitalização e eventuais despesas relativas ao custeio da contemplação obrigatória e da distribuição de bônus. (Resolução CNSP 384/20) Em porcentagem(%).'

Percentual da contribuição destinado aos custos de despesas com corretagem, colocação e administração do título de capitalização, emissão, divulgação, lucro da sociedade de capitalização e eventuais despesas relativas ao custeio da contemplação obrigatória e da distribuição de bônus. (Resolução CNSP 384/20)​

/data\[\]/society/products\[\]/validity​

Alterado - "description"

Alteração

Período entre a data de início e a data final para constituição do capital a ser pago ao(s) titular(es) do direito de resgate. Prazo de vigência do título de capitalização em meses (Resolução CNSP 384/20). Em meses.

Período entre a data de início e a data final para constituição do capital a ser pago ao(s) titular(es) do direito de resgate. Prazo de vigência do título de capitalização em meses (Resolução CNSP 384/20)​

/data\[\]/society/products\[\]/serieSize​

Alterado - "description"

Alteração

'Os títulos de capitalização que prevejam sorteio devem ser estruturados em séries, ou seja, em sequências ou em grupos de títulos submetidos às mesmas condições e características, à exceção do valor do pagamento.'

Os títulos de capitalização com sorteio devem ser estruturados em séries, ou seja, em sequências ou em grupos de títulos submetidos às mesmas condições e características, à exceção do valor do pagamento​

/data\[\]/society/products\[\]/capitalizationPeriod​

Alterado - "description"

Alteração

Informações relativas ao período de capitalização​

/data\[\]/society/products\[\]/capitalizationPeriod/updateIndexAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao índice utilizado na atualização dos pagamentos mensais.`​`  
`​`  
           \[Restrição\] Obrigatório quando "updateIndex" for igual 'OUTROS'​

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]​

Alterado - "description"

Alteração

description: |  
Corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização para a aquisição do título de capitalização, podendo ser única, periódica ou mensal (Resolução CNSP 384/20). Valores em reais (R$). Esclarecimentos adicionais SUSEP.  
Na modalidade Tradicional, informar a faixa de valor mínimo e máximo em R$ de contribuição ao plano.  
Para as demais modalidades, informar a lista com os valores permitidos de contribuição ao plano.  
Em todas as situações indicar para qual periodicidade de pagamento se aplicam os valores: pagamento mensal, pagamento único ou periódico.

Informações sobre a contribuição financeira em reais (R$),  abrangendo periodicidade, valor mínimo, valor máximo e montante pago​

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/periodicity​

Alterado - "description"

Alteração

Intervalo de tempo regular previsto entre os sorteios. Conforme os domínios:  
1\. Único  
2\. Diário  
3\. Semanal  
4\. Quinzenal  
5\. Mensal  
6\. Bimestral  
7\. Trimestral  
8\. Quadrimestral  
9\. Semestral  
10\. Anual  
11\. Outros

Intervalo de tempo regular previsto entre os sorteios. Na integração entre os sistemas OFB  
e OPIN, a correspondência do item ‘PERIODICO' no OPIN está relacionada ao item 'OUTROS'  
no OFB. Detalhes adicionais sobre esse cenário podem ser descritos no campo  
'periodicityAdditionalInfo’

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/periodicityAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao intervalo de tempo regular previsto entre os sorteios.`​`  
           \[Restrição\] Obrigatório quando "periodicity" for igual 'OUTROS'​

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/minimum​

Alterado - "description"

Alteração

Condicional: Quando modalidade for igual 'TRADICIONAL'  
Valor mínimo correspondente ao pagamento efetuado pelo subscritor à sociedade de capitalização.

Valor mínimo. Para a modalidade 'TRADICIONAL' o valor mínimo corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização​

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/maximum​

Alterado - "description"

Alteração

Condicional: Quando modalidade for igual 'TRADICIONAL'  
Valor máximo correspondente ao pagamento efetuado pelo subscritor à sociedade de capitalização.

Valor máximo. Para a modalidade 'TRADICIONAL' o valor máximo corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização​

/data\[\]/society/products\[\]/capitalizationPeriod/contributionAmount\[\]/allowedValue​

Alterado - "description"

Alteração

Condicional: Quando modalidade for diferente de 'TRADICIONAL'  
Lista com os valores permitidos de contribuição ao plano.

Valor permitido. Para a modalidade 'TRADICIONAL' o valor permitido corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização.​

/data\[\]/society/products\[\]/capitalizationPeriod/earlyRedemptions\[\]​

Alterado - "description"

Alteração

Informações relativas ao resgate antecipado​

/data\[\]/society/products\[\]/latePayment​

Alterado - "description"

Alteração

Conforme manual SUSEP: Prazo máximo (contínuo ou intermitente) em meses que o título fica suspenso por atraso de pagamento, antes de ser cancelado (não aplicável a pagamento único).

Informações relativas ao atraso de pagamento​

/data\[\]/society/products\[\]/latePayment/suspensionMonths​

Alterado - "description"

Alteração

'Conforme manual SUSEP: Prazo máximo (contínuo ou intermitente) em meses que o título fica suspenso por atraso de pagamento, antes de ser cancelado (não aplicável a pagamento único).'

Prazo máximo (contínuo ou intermitente) em meses que o título fica suspenso por atraso  
de pagamento, antes de ser cancelado, exceto pagamento único,  
conforme as diretrizes do manual da SUSEP

/data\[\]/society/products\[\]/latePayment/periodExtensionOption​

Alterado - "description"

Alteração

Alteração do prazo de vigência original, pela suspensão (não aplicável a pagamento único). A considerar os seguintes domínios:  
1\. true  
2\. false

Alteração do prazo de vigência original, pela suspensão, exceto pagamento único​

/data\[\]/society/products\[\]/contributionPayment​

Alterado - "description"

Alteração

Informações relativas ao pagamento da contribuição​

/data\[\]/society/products\[\]/contributionPayment/paymentMethod​

Alterado - "description"

Alteração

Meio de Pagamento utilizado para pagamento da contribuição. A considerar os domínios abaixo:  
1\. Cartão de Crédito  
2\. Cartão de Débito  
3\. Débito em conta corrente  
4\. Débito em conta poupança  
5\. Boleto bancário  
6\. PIX  
7\. Consignação em Folha de Pagamento  
8\. Pontos de Programas de Benefício  
9\. Outros

Modo de pagamento utilizado para realizar o pagamento da contribuição​

/data\[\]/society/products\[\]/contributionPayment/paymentMethodAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao meio de  
Pagamento utilizado para pagamento da contribuição  
\[Restrição\] Obrigatório quando "paymentMethod" for igual 'OUTROS'

/data\[\]/society/products\[\]/contributionPayment/updateIndexAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao índice utilizado na atualização dos pagamentos mensais`​`  
           \[Restrição\] Obrigatório quando "updateIndex" for igual 'OUTROS'​

/data\[\]/society/products\[\]/draws\[\]/timeInterval​

Alterado - "description"

Alteração

Intervalo de tempo regular previsto entre os sorteios. Conforme os domínios:  
\- UNICO  
\- DIÁRIO  
\- SEMANAL  
\- QUINZENAL  
\- MENSAL  
\- BIMESTRAL  
\- TRIMESTRAL  
\- QUADRIMESTRAL  
\- SEMESTRAL  
\- ANUAL  
\- OUTROS

Período de tempo regular estabelecido entre as ocorrências dos sorteios​

/data\[\]/society/products\[\]/draws\[\]/timeIntervalAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao intervalo de tempo regular previsto entre os sorteios.`​`  
           \[Restrição\] Obrigatório quando "timeInterval" for igual 'OUTROS'​

/data\[\]/society/products\[\]/draws\[\]/earlySettlementRaffle​

Alterado - "description"

Alteração

Modelo de sorteio que acarreta, ao título contemplado, o seu resgate total obrigatório (Resolução Normativa 384/20). Conforme os domínios:  
1\. true  
2\. false

Modelo de sorteio que acarreta, ao título contemplado, o seu resgate total obrigatório (Resolução Normativa 384/20)​

/data\[\]/society/products\[\]/draws\[\]/mandatoryContemplation​

Alterado - "description"

Alteração

Possibilidade de realização de sorteio com previsão de que o título sorteado seja obrigatoriamente um título comercializado, desde que atingidos os requisitos definidos nas condições gerais do plano. Conforme os domínios:  
1\. true  
2\. false

Indicador da possibilidade de realização de sorteio com previsão de que o título sorteado seja obrigatoriamente um título comercializado, desde que atingidos os requisitos definidos nas condições gerais do plano​

/data\[\]/society/products\[\]/draws\[\]/minimumContemplationProbability​

Alterado - "description"

Alteração

'Número representativo da probabilidade mínima de contemplação nos sorteios, em porcentagem (%).'

Percentual da probabilidade mínima de contemplação nos sorteios​

/data\[\]/society/products\[\]/additionalInfo​

Alterado - "description"

Alteração

Campo aberto (possibilidade de incluir URL) Observação: As URLs são limitadas a 2048 caracteres mas, para o contexto do Open Insurance , foi adotado a metade deste tamanho (1024).

Campo livre para preenchimento das informações adicionais referente ao produto da sociedade seguradora participante do OPIN. Pode-se incluir URL​

/data\[\]/society/products\[\]/minimumRequirementDetails​

Alterado - "description"

Alteração

Campo aberto (possibilidade de incluir URL). Observação: As URLs são limitadas a 2048 caracteres mas, para o contexto do Open Insurance , foi adotado a metade deste tamanho (1024). tamanho. p.ex. ‘[https://ACME.exemplo/capitalizacao/tradicional/pdf/condicoes\_gerais.’](https://ACME.exemplo/capitalizacao/tradicional/pdf/condicoes_gerais.%E2%80%99)

Campo livre para preenchimento das informações adicionais referente ao requerimento mínimo. Pode-se incluir URL​

/data\[\]/society/products\[\]/targetAudience​

Alterado - "description"

Alteração

A considerar os domínios abaixo:  
1\. Pessoa Natural  
2\. Pessoa Jurídica  
3\. Ambas (Pessoa Natural e Jurídica)

Públio alvo do produto da sociedade seguradora participante do OPIN​

/links​

Alterado - "description"

Alteração

Referências para outros recusos da API requisitada.

Referências para outros recursos da API requisitada.​

/data\[\]/society/products/redemptionPercentageEndTerm

Campo Removido

Remoção
