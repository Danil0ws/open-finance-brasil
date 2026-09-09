# Cenário 7: credit-portability_api_rejected-portability_test-module_v1 - CPC

**Tipo do teste**

Teste de exceção

**Descrição**

Validação de mensagens e comportamentos do sistema em situações de erro no processo de verificação de respostas.

**Objetivo**

Garante que o pedido de portabilidade seja rejeitado quando o cliente aceitou a contraproposta

**Requisito de massa**

-   Um contrato do tipo CREDITO\_PESSOAL\_CLEAN com o campo status como 'DISPONIVEL' e o campo isEligible como 'TRUE'
    
-   Deverá haver uma interação humana para que realize um pool para validar o estado 'REJECTED'
    

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

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility para cada contractId até encontrar ao menos um com status como "DISPONIVEL" e isEligible como "TRUE"

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

Status 202 - Validação de resposta de acordo com especificação

Etapa de criação de solicitação de portabilidade

10

Rotina de tempo com a chamada de endpoint GET /portabilities/{portabilityId} por 10 minutos enquanto encontrar status igual a “RECEIVED” ou “PENDING”

Status 200 - Validação de resposta e garantia que o status seja igual "REJECTED" e statusReason.reasonType como 'RETENCAO\_DO\_CLIENTE'

Etapa de criação de contra proposta

11

Fim do teste

## Diagrama de sequência

![ct7DS.svg](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/1329299683/child/attachment/att1329299697/download)
