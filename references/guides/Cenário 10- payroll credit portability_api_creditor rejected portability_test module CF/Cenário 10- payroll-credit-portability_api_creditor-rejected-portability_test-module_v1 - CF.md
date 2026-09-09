# Cenário 10: payroll-credit-portability_api_creditor-rejected-portability_test-module_v1 - CF

**Tipo do teste**

Teste funcional

**Descrição**

Rejeição de portabilidade por credora identificar problemas no contrato não relacionados a pagamento

**Objetivo**

Garante que a credora possa rejeitar um pedido de solicitação portabilidade após identificar problemas não relacionados a pagamento

**Requisito de massa**

-   Um contrato com a categoria CONSIGNADO\_SIAPE e com o campo status como 'DISPONIVEL' e o campo isEligible como 'TRUE'
    

## Script

Os passos abaixo são todas as requisições que serão feitas para a jornada do teste acima. Além das requisições temos as respostas esperada para cada requisição a ser realizada para respeitar o teste especifico.

Este cenário se encontra no arquivo disponibilizado em uma página de [WIKI](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-CPC-API?redirected_from=Credit-Portability-API) no Gitlab disponibilizado pela Raidiam.  
Foi feita a tradução para português e criado um diagrama de sequência para auxilio no entendimento do cenário de teste.

**Steps**

**Requisições**

**Respostas esperadas**

**Etapa da Jornada**

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

Status 200 - Recuperando todos os contractIds com data.productSubTypeCategory = "CONSIGNADO\_SIAPE" and companyCnpj

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

Status 202 - Resposta de sucesso

Etapa de criação de solicitação de portabilidade

10

Serão feitas a chamadas de endpoint GET /portabilities/{portabilityId} a cada 10 minutos enquanto status estiver em "RECEIVED" ou "PENDING"

Status 200 - Validação de resposta de acordo com a especificação e data.status igual “ACCEPTED\_SETTLEMENT\_IN\_PROGRESS”

Etapa de contraproposta e Etapa de liquidação

11

Chamada de endpoint GET /portabilities/{portabilityId}/account-data

Status 200 - Resposta de sucesso

Etapa de liquidação

Chamada de endpoint POST /portabilities/{portabilityId}/payment, incluindo detalhes de pagamento:  
paymentAmount = original contractOutstandingBalance

Status 202 - Validação de resposta de acordo com a especificação

12

Serão feitas a chamadas de endpoint GET /portabilities/{portabilityId} a cada 10 minutos enquanto status estiver em "ACCEPTED\_SETTLEMENT\_IN\_PROGRESS"

Status 200 - Validação de resposta de acordo com a especificação e data.status igual “ACCEPTED\_SETTLEMENT\_COMPLETED”

Etapa de validação da liquidação

13

Serão feitas a chamadas de endpoint GET /portabilities/{portabilityId} a cada 10 minutos enquanto status estiver em "ACCEPTED\_SETTLEMENT\_COMPLETED"

Status 200 - Validação de resposta de acordo com a especificação e data.status igual "REJECTED" e statusReason.reasonType como "CLIENTE\_COM\_ACAO\_JUDICIAL"

14

Fim do teste

## Diagrama de sequência

![ct10.svg](images/ct10.svg)
