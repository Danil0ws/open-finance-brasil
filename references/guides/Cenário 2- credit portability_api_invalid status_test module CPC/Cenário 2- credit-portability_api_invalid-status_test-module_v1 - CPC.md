# Cenário 2: credit-portability_api_invalid-status_test-module_v1 - CPC

**Tipo do teste**

Teste de exceção

**Descrição**

Validação de mensagens e comportamentos do sistema em situações de erro no processo de verificação de respostas.

**Objetivo**

Garante que o pedido de portabilidade seja rejeitado quando o campo status do endpoint conconrrent-manamente estiver como “EM\_ANDAMENTO“ ou o campo IsEligible for igual a “FALSE“

**Requisito de massa**

-   Um contrato do tipo CREDITO\_PESSOAL\_CLEAN com o campo status como 'EM ANDAMENTO' e o campo isEligible como 'TRUE'
    
-   Um contrato do tipo CREDITO\_PESSOAL\_CLEAN com o campo status como ‘EM ANDAMENTO' e o campo isEligible como 'FALSE'
    

## Script

Os passos abaixo são todas as requisições que serão feitas para a jornada do teste acima. Além das requisições temos as respostas esperada para cada requisição a ser realizada para respeitar o teste especifico.

Este cenário se encontra no arquivo disponibilizado em uma página de [WIKI](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-CPC-API?redirected_from=Credit-Portability-API) no Gitlab disponibilizado pela Raidiam.  
Foi feita a tradução para português e criado um diagrama de sequência para auxilio no entendimento do cenário de teste.

**Steps**

**Requisições**

**Respostas esperadas**

**Etapa de Jornada**

1

Chamada de endpoint POST /consents com o grupo de permissão 'Credit Operations'

Status 201 - Garantindo de status como AWAITING\_AUTHORISATION

Etapa de consentimento

2

Redirecionamento para usuário autorizar o consentimento

3

Chamada de endpoint GET /consents/{consentId}

Status 200 - Garantindo de status como AUTHORISED

4

Chamada de endpoint GET Loans Contracts

Status 200 - Recuperando todos os contractIds com productSubType = “CREDITO\_PESSOAL\_CLEAN” e companyCnpj

Etapa de busca e validação de contrato

5

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility para cada contractId até encontrar ao menos um com status como "EM ANDAMENTO" e isEligible como "TRUE"

6

Chamada de endpoint GET Loans Contracts/{contractId}

Status 200 - Recuperando instalmentPeriodicity

7

Chamada de endpoint GET Loans Contracts/{contractId}/scheduled-installments

Status 200 - Recuperando dueInstalments

8

Chamada de endpoint GET Loans Contracts/{contractId}/payments

Status 200 - Recuperando contractOutstandingBalance

9

Chamada do endpoint POST /portabilities enviando os seguintes valores:  
data.institution.creditor.companyCnpj = original companyCnpj  
instalmentPeriodicity = original instalmentPeriodicity  
proposedContract.totalNumberOfInstalments = original dueInstalments  
contractAmount = original contractOutstandingBalance

Status 422 - Validação de resposta e esperado código de erro como 'EM\_ANDAMENTO'

Etapa de criação de solicitação de portabilidade

10

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility para cada contractId até encontrar ao menos um com isEligible como "FALSE"

Etapa de busca e validação de contrato

11

Chamada de endpoint GET Loans Contracts/{contractId}

Status 200 - Recuperando instalmentPeriodicity

12

Chamada de endpoint GET Loans Contracts/{contractId}/scheduled-installments

Status 200 - Recuperando dueInstalments

13

Chamada de endpoint GET Loans Contracts/{contractId}/payments

Status 200 - Recuperando contractOutstandingBalance

14

Chamada do endpoint POST /portabilities enviando os seguintes valores:  
data.institution.creditor.companyCnpj = original companyCnpj  
instalmentPeriodicity = original instalmentPeriodicity  
proposedContract.totalNumberOfInstalments = original dueInstalments  
contractAmount = original contractOutstandingBalance

Status 422 - Validação de resposta e esperado código de erro como 'CONTRATO\_NAO\_ELEGIVEL'

Etapa de criação de solicitação de portabilidade

15

Fim do teste

## Diagrama de sequência

![ct2DS.svg](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/1329299528/child/attachment/att1329299551/download)
