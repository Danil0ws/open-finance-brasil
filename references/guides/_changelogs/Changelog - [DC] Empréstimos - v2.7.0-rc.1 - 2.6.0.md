# Changelog - [DC] Empréstimos - v2.7.0-rc.1 - 2.6.0

none

## GET /contracts

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/productSubTypeCategory

Removido

Remoção

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/productSubTypeCategory

Removido

Remoção

get/responses/200/data/hasInsuranceContracted

Alterado - "description"

Alteração

Campo que identifica se existe seguro contratado para o Empréstimo, onde seguro contratado é \`true\` e não contratado é \`false\`. 

\[Restrição\] Este campo é de envio obrigatório caso o campo productSubTypeCategory seja preenchido \`CREDITO\_PESSOAL\_CLEAN\` ou \`CONSIGNADO\_SIAPE\`.   

Campo que identifica se existe seguro contratado para o Empréstimo, onde seguro contratado é \`true\` e não contratado é \`false\`. 

\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubType\` seja preenchido com \`CREDITO\_PESSOAL\_SEM\_CONSIGNACAO\`.​             

get/responses/200/data/interestRates

Alterado - "description"

Alteração

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade de crédito. Caso o contrato não possua taxas de juros, deve ser compartilhada uma lista vazia. Caso o contrato possua uma taxa de juros com valor 0, deve ser compartilhado um objeto com o valor 0 de forma explícita. Para contratos em renegociação, a taxa de empréstimo compartilhada deve se manter a taxa do contrato vigente, sendo alterada para a renegociada ao fim do processo de renegociação. Para os produtos CPC (campo \`productSubTypeCategory\` preenchido com \`CREDITO\_PESSOAL\_CLEAN\`) ou Consignado Federal (campo \`productSubTypeCategory\` preenchido com \`CONSIGNADO\_SIAPE\`) deve-se obrigatoriamente conter a taxa nominal e a taxa efetiva (campo taxPeriodicity) com periodicidade a.a. (ao ano), podendo adicionalmente conter, além das taxas nominal e efetiva ao ano, outras com outra periodicidade.   

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade de crédito. Caso o contrato não possua taxas de juros, deve ser compartilhada uma lista vazia. Caso o contrato possua uma taxa de juros com valor 0, deve ser compartilhado um objeto com o valor 0 de forma explícita. Para contratos em renegociação, a taxa de empréstimo compartilhada deve se manter a taxa do contrato vigente, sendo alterada para a renegociada ao fim do processo de renegociação. Para o campo \`productSubType\` preenchido com \`CREDITO\_PESSOAL\_SEM\_CONSIGNACAO\` deve-se obrigatoriamente conter a taxa nominal e a taxa efetiva (campo \`taxPeriodicity\`) com periodicidade \`a.a.\` (ao ano), podendo adicionalmente conter, além das taxas nominal e efetiva ao ano, outras com outra periodicidade.​  

get/responses/200/data/nextInstalmentAmount

Alterado - "description"

Alteração

Informa o valor de face (corresponde ao valor da parcela no vencimento). Para contratos liquidados, retornar zero, seguindo o pattern.  
\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubTypeCategory\` seja preenchido \`CREDITO\_PESSOAL\_CLEAN\` ou \`CONSIGNADO\_SIAPE\` no endpoint /contracts/{contractId}.   

Informa o valor de face (corresponde ao valor da parcela no vencimento). Para contratos liquidados, retornar zero, seguindo o pattern.  
\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubType\` seja preenchido com \`CREDITO\_PESSOAL\_SEM\_CONSIGNACAO\`.​  

## GET /contracts/{contractId}/payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/lastUpdatedContractOutstandingBalance

Alterado - "description"

Alteração

Data e hora da última atualização do valor do campo contractOutstandingBalance, conforme especificação RFC-3339, formato UTC.

\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubTypeCategory\` seja preenchido \`CREDITO\_PESSOAL\_CLEAN\` ou \`CONSIGNADO\_SIAPE\` no endpoint /contracts/{contractId}.   

Data e hora da última atualização do valor do campo contractOutstandingBalance, conforme especificação RFC-3339, formato UTC.

\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubType\` seja preenchido \`CREDITO\_PESSOAL\_SEM\_CONSIGNACAO\` no endpoint \`/contracts/{contractId}\`.​  

get/responses/200/data/totalRemainingAmount

Alterado - "description"

Alteração

Valor total que falta para o cliente liquidar o contrato, considerando o somatório total de todas as parcelas a vencer e vencidas, bem como todas as taxas, tarifas e encargos das parcelas. Nos casos de contrato com taxas pós-fixadas, considerar apenas valores pré-fixados, visto que o cálculo pós-fixado ocorre apenas em momento futuro, e que o valor está sujeito às variações de seu indexador.

\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubTypeCategory\` seja preenchido \`CREDITO\_PESSOAL\_CLEAN\` ou \`CONSIGNADO\_SIAPE\` no endpoint /contracts/{contractId}.   

Valor total que falta para o cliente liquidar o contrato, considerando o somatório total de todas as parcelas a vencer e vencidas, bem como todas as taxas, tarifas e encargos das parcelas. Nos casos de contrato com taxas pós-fixadas, considerar apenas valores pré-fixados, visto que o cálculo pós-fixado ocorre apenas em momento futuro, e que o valor está sujeito às variações de seu indexador.

\[Restrição\] Este campo é de envio obrigatório caso o campo \`productSubTypeCategory\` seja preenchido \`CREDITO\_PESSOAL\_CLEAN\` ou \`CONSIGNADO\_SIAPE\` no endpoint /contracts/{contractId}.
