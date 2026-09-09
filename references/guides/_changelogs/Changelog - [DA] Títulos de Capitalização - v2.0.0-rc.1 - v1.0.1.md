# Changelog - [DA] Títulos de Capitalização - v2.0.0-rc.1 - v1.0.1

## GET /bonds

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/capitalizationPeriod/contributionAmount/items/periodicityAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data/capitalizationPeriod/updateIndexAdditionalInfo​

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

get/responses/200/data/items

Removido - "required"

Remoção

get/responses/200/data/items/participant/brand​

Alterado - "minlength"

Alteração

1​

get/responses/200/data/items/participant/brand​

Alterado - "maxlength"

Alteração

80​

get/responses/200/data/items/participant/brand​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/participant/cnpjNumber​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/participant/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/participant/name​

Alterado - "minlength"

Alteração

1​

get/responses/200/data/items/participant/name​

Alterado - "maxlength"

Alteração

80​

get/responses/200/data/items/participant/name​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/participant/name

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/participant/urlComplementaryList

Alterado - "pattern"

Alteração

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)|(NA)$

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

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

get/responses/200/data/items/society​

Alterado - "description"

Alteração

Conjunto de informações relativas à seguradora do produto de open insurance

Dados sobre a seguradora participante do OPIN​

get/responses/200/data/items/society

Alterado - "description"

Alteração

Conjunto de informações relativas à seguradora do produto de open insurance

Objeto que representa a empresa regulada pela SUSEP que oferta produtos definidos em OPIN.

get/responses/200/data/items/society/cnpjNumber​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/cnpjNumber​

Alterado - "description"

Alteração

CNPJ da sociedade seguradora participante do OPIN​

get/responses/200/data/items/society/cnpjNumber

Alterado - "pattern"

Alteração

^(\\d{14})$|^(NA)$

^\\d{14}$

get/responses/200/data/items/society/name​

Alterado - "minlength"

Alteração

1​

get/responses/200/data/items/society/name​

Alterado - "maxlength"

Alteração

80​

get/responses/200/data/items/society/name​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products​

Alterado - "description"

Alteração

Lista de produtos de uma empresa

Lista de produtos da sociedade seguradora participante do OPIN​

get/responses/200/data/items/society/products/items

Removido obrigatóriedade no campo 'additionalDetails'

Remoção

required

get/responses/200/data/items/society/products/items/​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/additionalInfo​

Alterado nome do campo

Alteração

additionalInfo​

additionalDetails​

get/responses/200/data/items/society/products/items/additionalInfo​

Alterado - "description"

Alteração

Campo aberto (possibilidade de incluir URL) Observação: As URLs são limitadas a 2048 caracteres mas, para o contexto do Open Insurance , foi adotado a metade deste tamanho (1024).

Campo livre para preenchimento das informações adicionais referente ao produto da sociedade seguradora participante do OPIN. Pode-se incluir URL​

get/responses/200/data/items/society/products/items/capitalizationPeriod​

Alterado - "description"

Alteração

Informações relativas ao período de capitalização​

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items​

Alterado - "description"

Alteração

description: |  
Corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização para a aquisição do título de capitalização, podendo ser única, periódica ou mensal (Resolução CNSP 384/20). Valores em reais (R$). Esclarecimentos adicionais SUSEP.  
Na modalidade Tradicional, informar a faixa de valor mínimo e máximo em R$ de contribuição ao plano.  
Para as demais modalidades, informar a lista com os valores permitidos de contribuição ao plano.  
Em todas as situações indicar para qual periodicidade de pagamento se aplicam os valores: pagamento mensal, pagamento único ou periódico.

Informações sobre a contribuição financeira em reais (R$),  abrangendo periodicidade, valor mínimo, valor máximo e montante pago​

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/allowedValue​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/allowedValue​

Alterado - "description"

Alteração

Condicional: Quando modalidade for diferente de 'TRADICIONAL'  
Lista com os valores permitidos de contribuição ao plano.

Valor permitido. Para a modalidade 'TRADICIONAL' o valor permitido corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização.​

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/maximum​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/maximum​

Alterado - "description"

Alteração

Condicional: Quando modalidade for igual 'TRADICIONAL'  
Valor máximo correspondente ao pagamento efetuado pelo subscritor à sociedade de capitalização.

Valor máximo. Para a modalidade 'TRADICIONAL' o valor máximo corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização​

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/minimum​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/minimum​

Alterado - "description"

Alteração

Condicional: Quando modalidade for igual 'TRADICIONAL'  
Valor mínimo correspondente ao pagamento efetuado pelo subscritor à sociedade de capitalização.

Valor mínimo. Para a modalidade 'TRADICIONAL' o valor mínimo corresponde ao pagamento efetuado pelo subscritor à sociedade de capitalização​

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/periodicity​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/periodicity​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/periodicity​

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

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/periodicity​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/items/periodicityAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao intervalo de tempo regular previsto entre os sorteios.`​`  
           \[Restrição\] Obrigatório quando "periodicity" for igual 'OUTROS'​

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/maximum

Alterado - pattern

Alteração

^(d{1,16}\\.\\d{2,4})$|^(NA)$

^(d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/capitalizationPeriod/contributionAmount/minimum

Alterado - pattern

Alteração

^(d{1,16}\\.\\d{2,4})$|^(NA)$

^(d{1,16}\\.\\d{2,4})$

get/responses/200/data/items/society/products/items/capitalizationPeriod/earlyRedemptions/items​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/earlyRedemptions/items​

Alterado - "description"

Alteração

Informações relativas ao resgate antecipado​

get/responses/200/data/items/society/products/items/capitalizationPeriod/earlyRedemptions/items/quota​

Adicionado - "maximum"

Adição

2147483647​

get/responses/200/data/items/society/products/items/capitalizationPeriod/earlyRedemptions/items/quota​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/capitalizationPeriod/gracePeriodRedemption​

Adicionado - "maximum"

Adição

2147483647​

get/responses/200/data/items/society/products/items/capitalizationPeriod/gracePeriodRedemption​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/gracePeriodRedemption​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/capitalizationPeriod/interestRate​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/redemptionPercentageEndTerm​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/updateIndex​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/capitalizationPeriod/updateIndex​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/capitalizationPeriod/updateIndex​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/capitalizationPeriod/updateIndexAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao índice utilizado na atualização dos pagamentos mensais.`​`  
`​`  
           \[Restrição\] Obrigatório quando "updateIndex" for igual 'OUTROS'​

get/responses/200/data/items/society/products/items/code​

Alterado - "minlength"

Alteração

1​

get/responses/200/data/items/society/products/items/code​

Alterado - "maxlength"

Alteração

100​

get/responses/200/data/items/society/products/items/contributionPayment​

Alterado - "description"

Alteração

Informações relativas ao pagamento da contribuição​

get/responses/200/data/items/society/products/items/contributionPayment/paymentMethod​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/contributionPayment/paymentMethod​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/contributionPayment/paymentMethod​

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

get/responses/200/data/items/society/products/items/contributionPayment/paymentMethod​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/contributionPayment/paymentMethodAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao meio de  
Pagamento utilizado para pagamento da contribuição  
\[Restrição\] Obrigatório quando "paymentMethod" for igual 'OUTROS'

get/responses/200/data/items/society/products/items/contributionPayment/updateIndex​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/contributionPayment/updateIndex​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/contributionPayment/updateIndex​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/contributionPayment/updateIndexAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao índice utilizado na atualização dos pagamentos mensais`​`  
           \[Restrição\] Obrigatório quando "updateIndex" for igual 'OUTROS'​

get/responses/200/data/items/society/products/items/costType​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/costType​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/costType​

Alterado - "description"

Alteração

Pagamento efetuado ao subscritor à sociedade de capitalização para aquisição do título de capitalização, podendo ser única, periódica ou mensal.  
1\. Pagamento Único  
2\. Pagamento Mensal  
3\. Pagamento Periódico

Pagamento efetuado ao subscritor à sociedade de capitalização para aquisição do título de capitalização, podendo ser única, periódica ou mensal.​

get/responses/200/data/items/society/products/items/costType​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/draws/items/earlySettlementRaffle​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/earlySettlementRaffle​

Alterado - "description"

Alteração

Modelo de sorteio que acarreta, ao título contemplado, o seu resgate total obrigatório (Resolução Normativa 384/20). Conforme os domínios:  
1\. true  
2\. false

Modelo de sorteio que acarreta, ao título contemplado, o seu resgate total obrigatório (Resolução Normativa 384/20)​

get/responses/200/data/items/society/products/items/draws/items/mandatoryContemplation​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/mandatoryContemplation​

Alterado - "description"

Alteração

Possibilidade de realização de sorteio com previsão de que o título sorteado seja obrigatoriamente um título comercializado, desde que atingidos os requisitos definidos nas condições gerais do plano. Conforme os domínios:  
1\. true  
2\. false

Indicador da possibilidade de realização de sorteio com previsão de que o título sorteado seja obrigatoriamente um título comercializado, desde que atingidos os requisitos definidos nas condições gerais do plano​

get/responses/200/data/items/society/products/items/draws/items/minimumContemplationProbability​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/minimumContemplationProbability​

Alterado - "description"

Alteração

'Número representativo da probabilidade mínima de contemplação nos sorteios, em porcentagem (%).'

Percentual da probabilidade mínima de contemplação nos sorteios​

get/responses/200/data/items/society/products/items/draws/items/prizeMultiplier​

Adicionado - "maximum"

Adição

2147483647​

get/responses/200/data/items/society/products/items/draws/items/prizeMultiplier​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/prizeMultiplier​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/draws/items/quantity​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/quantity​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/draws/items/ruleDescription​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/ruleDescription​

Alterado - "example"

Alteração

Sorteios próprios às terças-feiras. Toda quarta-feira sorteios através da loteria federal​

get/responses/200/data/items/society/products/items/draws/items/timeInterval​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/draws/items/timeInterval​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/draws/items/timeInterval​

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

get/responses/200/data/items/society/products/items/draws/items/timeInterval​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/draws/items/timeIntervalAdditionalInfo​

Alterado - "description"

Alteração

'Restrição: Campo obrigatório para complementar a informação quando selecionada a opção ''OUTROS'''

Campo livre para preenchimento das informações adicionais referente ao intervalo de tempo regular previsto entre os sorteios.`​`  
           \[Restrição\] Obrigatório quando "timeInterval" for igual 'OUTROS'​

get/responses/200/data/items/society/products/items/draws/quantity

Alterado - type

Alteração

Number

Integer

get/responses/200/data/items/society/products/items/finalRedemptionRate​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/latePayment​

Alterado - "description"

Alteração

Conforme manual SUSEP: Prazo máximo (contínuo ou intermitente) em meses que o título fica suspenso por atraso de pagamento, antes de ser cancelado (não aplicável a pagamento único).

Informações relativas ao atraso de pagamento​

get/responses/200/data/items/society/products/items/latePayment/periodExtensionOption​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/latePayment/periodExtensionOption​

Alterado - "description"

Alteração

Alteração do prazo de vigência original, pela suspensão (não aplicável a pagamento único). A considerar os seguintes domínios:  
1\. true  
2\. false

Alteração do prazo de vigência original, pela suspensão, exceto pagamento único​

get/responses/200/data/items/society/products/items/latePayment/suspensionMonths​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/latePayment/suspensionMonths

Alterado - type

Alteração

Number

Integer

get/responses/200/data/items/society/products/items/latePayment/suspensionMonths​

Alterado - "description"

Alteração

'Conforme manual SUSEP: Prazo máximo (contínuo ou intermitente) em meses que o título fica suspenso por atraso de pagamento, antes de ser cancelado (não aplicável a pagamento único).'

Prazo máximo (contínuo ou intermitente) em meses que o título fica suspenso por atraso  
de pagamento, antes de ser cancelado, exceto pagamento único,  
conforme as diretrizes do manual da SUSEP

get/responses/200/data/items/society/products/items/latePayment/suspensionMonths​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/minimumRequirementDetails

Alterado - "example"

Alteração

[https://ACME.exemplo/capitalizacao/tradicional/pdf/condicoes\_gerais](https://ACME.exemplo/capitalizacao/tradicional/pdf/condicoes_gerais)

[https://ACME.com/capitalizacao/tradicional/pdf/condicoes\_gerais](https://acme.com/capitalizacao/tradicional/pdf/condicoes_gerais)

get/responses/200/data/items/society/products/items/minimumRequirementDetails​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/minimumRequirementDetails​

Alterado - "description"

Alteração

Campo aberto (possibilidade de incluir URL). Observação: As URLs são limitadas a 2048 caracteres mas, para o contexto do Open Insurance , foi adotado a metade deste tamanho (1024). tamanho. p.ex. ‘[https:/ACME.exemplo/capitalizacao/tradicional/pdf/condicoes\_gerais.’](https://ACME.exemplo/capitalizacao/tradicional/pdf/condicoes_gerais.%E2%80%99)

Campo livre para preenchimento das informações adicionais referente ao requerimento mínimo. Pode-se incluir URL​

get/responses/200/data/items/society/products/items/minimumRequirementDetails

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/modality​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/modality​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/modality​

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
    

get/responses/200/data/items/society/products/items/modality​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/name​

Alterado - "minlength"

Alteração

1​

get/responses/200/data/items/society/products/items/name​

Alterado - "maxlength"

Alteração

80​

get/responses/200/data/items/society/products/items/quotas/items​

Alterado - "description"

Alteração

Informações relativas às taxas da Quotas praticadas para cada Parcela

Informações relativas às taxas da cotas praticadas para cada parcela​

get/responses/200/data/items/society/products/items/quotas/items/capitalizationQuota​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/quotas/items/capitalizationQuota​

Alterado - "description"

Alteração

Percentual da contribuição destinado à constituição de capital referente ao direito de resgate. (Resolução CNSP 384/20) Em porcentagem(%).

Percentual da contribuição destinado à constituição de capital referente ao direito de resgate. (Resolução CNSP 384/20)​

get/responses/200/data/items/society/products/items/quotas/items/chargingQuota​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/quotas/items/chargingQuota​

Alterado - "description"

Alteração

'Percentual da contribuição destinado aos custos de despesas com corretagem, colocação e administração do título de capitalização, emissão, divulgação, lucro da sociedade de capitalização e eventuais despesas relativas ao custeio da contemplação obrigatória e da distribuição de bônus. (Resolução CNSP 384/20) Em porcentagem(%).'

Percentual da contribuição destinado aos custos de despesas com corretagem, colocação e administração do título de capitalização, emissão, divulgação, lucro da sociedade de capitalização e eventuais despesas relativas ao custeio da contemplação obrigatória e da distribuição de bônus. (Resolução CNSP 384/20)​

get/responses/200/data/items/society/products/items/quotas/items/quota​

Adicionado - "maximum"

Adição

2147483647​

get/responses/200/data/items/society/products/items/quotas/items/quota​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/quotas/items/quota​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/quotas/items/raffleQuota​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/quotas/items/raffleQuota​

Alterado - "description"

Alteração

'Percentual da contribuição destinado a custear os sorteios, se previstos no plano. (Resolução CNSP 384/20) Em porcentagem(%).'

Percentual da contribuição destinado a custear os sorteios, se previstos no plano. (Resolução CNSP 384/20)​

get/responses/200/data/items/society/products/items/redemptionPercentageEndTerm​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/serieSize​

Adicionado - "maximum"

Adição

2147483647​

get/responses/200/data/items/society/products/items/serieSize​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/serieSize​

Alterado - "description"

Alteração

'Os títulos de capitalização que prevejam sorteio devem ser estruturados em séries, ou seja, em sequências ou em grupos de títulos submetidos às mesmas condições e características, à exceção do valor do pagamento.'

Os títulos de capitalização com sorteio devem ser estruturados em séries, ou seja, em sequências ou em grupos de títulos submetidos às mesmas condições e características, à exceção do valor do pagamento​

get/responses/200/data/items/society/products/items/serieSize​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/items/targetAudience​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/targetAudience​

Alterado - "description"

Alteração

A considerar os domínios abaixo:  
1\. Pessoa Natural  
2\. Pessoa Jurídica  
3\. Ambas (Pessoa Natural e Jurídica)

Públio alvo do produto da sociedade seguradora participante do OPIN​

get/responses/200/data/items/society/products/items/targetAudience​

Removido - "NA"

Remoção

get/responses/200/data/items/society/products/items/termsAndConditions​

Alterado - "description"

Alteração

Informações relativas aos termos e condições​

get/responses/200/data/items/society/products/items/termsAndConditions/detail​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/termsAndConditions/susepProcessNumber​

Alterado - "minlength"

Alteração

 2​

get/responses/200/data/items/society/products/items/termsAndConditions/susepProcessNumber​

Alterado - "maxlength"

Alteração

30​

get/responses/200/data/items/society/products/items/termsAndConditions/susepProcessNumber​

Alterado - "obrigatoriedade"

Alteração

required

get/responses/200/data/items/society/products/items/termsAndConditions/susepProcessNumber​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/termsAndConditions/termsRegulations

Alterado - "description"

Alteração

'Representam as Condições Gerais, Condições Especiais e Condições ou Cláusulas Particulares de um mesmo produto. (Circular SUSEP 321/06). Campo aberto (possibilidade de incluir URL)'

Campo aberto para representar as Condições Gerais, Condições Especiais e Condições ou Cláusulas Particulares de um mesmo produto, confrome Circular SUSEP 321/06. Pode-se incluir URL que apresenta esse termos e condições​

get/responses/200/data/items/society/products/items/termsAndConditions/termsRegulations

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/validity​

Adicionado - "maximum"

Adição

2147483647​

get/responses/200/data/items/society/products/items/validity​

Adicionado - x-regulatory-required

Adição

get/responses/200/data/items/society/products/items/validity​

Alterado - "description"

Alteração

Período entre a data de início e a data final para constituição do capital a ser pago ao(s) titular(es) do direito de resgate. Prazo de vigência do título de capitalização em meses (Resolução CNSP 384/20). Em meses.

Período entre a data de início e a data final para constituição do capital a ser pago ao(s) titular(es) do direito de resgate. Prazo de vigência do título de capitalização em meses (Resolução CNSP 384/20)​

get/responses/200/data/items/society/products/items/validity​

Removido - "maxlength"

Remoção

get/responses/200/data/items/society/products/redemptionPercentageEndTerm

Campo Removido

Remoção

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

get/responses/200/data/society/products/items/draws/items/timeIntervalAdditionalInfo​

Alterado - "example"

Alteração

Informações adicionais​

get/responses/200/data/termsAndConditions/detail​

Alterado - nome do campo

Alteração

detail

termsRegulations   

get/responses/200/links

Alterado - "description"

Alteração

Referências para outros recusos da API requisitada.

Referências para outros recursos da API requisitada.​

get/responses/200/meta/totalRecords

Alterado - "example"

Alteração

1

10

get/responses/400/meta/totalRecords

Alterado - "example"

Alteração

1

10

get/responses/404/meta/totalRecords

Alterado - "example"

Alteração

1

10

get/responses/405/meta/totalRecords

Alterado - "example"

Alteração

1

10
