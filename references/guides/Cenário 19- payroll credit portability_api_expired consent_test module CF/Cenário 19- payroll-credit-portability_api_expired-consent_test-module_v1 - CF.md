# Cenário 19: payroll-credit-portability_api_expired-consent_test-module_v1 - CF

**Tipo do teste**

Teste de exceção

**Descrição**

Validações de segurança no comportamento das requisições

**Objetivo**

Garante que o sistema impeça que ocorra uma portabilidade com um consentimento expirado

**Requisito de massa**

-   Um contrato com a categoria CONSIGNADO\_SIAPE e com o campo status como 'DISPONIVEL' e o campo isEligible como 'TRUE'
    

## Script

Os passos abaixo são todas as requisições que serão feitas para a jornada do teste acima. Além das requisições temos as respostas esperada para cada requisição a ser realizada para respeitar o teste especifico.

Este cenário se encontra no arquivo disponibilizado em uma página de [WIKI](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-CPC-API?redirected_from=Credit-Portability-API) no Gitlab disponibilizado pela Raidiam.  
Foi feita a tradução para português e criado um diagrama de sequência para auxilio no entendimento do cenário de teste.

**Steps**

**Requisições**

**Respostas esperadas**

1

Chamada de endpoint POST /consents com o grupo de permissão 'Credit Operations' e configurar o campo expirationDateTime para 5 minutos no futuro

Status 201 - Garantindo de status como AWAITING\_AUTHORISATION

2

Redirecionamento para usuário autorizar o consentimento

3

Chamada de endpoint GET /consents/{consentId}

Status 200 - Garantindo de status como AUTHORISED

4

Chamada de endpoint GET Loans Contracts

Status 200 - Recuperando todos os contractIds com data.productSubTypeCategory = "CONSIGNADO\_SIAPE" and companyCnpj

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

200 - Validate the response and retrieve contractOutstandingBalance

9

Rotina de tempo para chamada de endpoint GET consents para 5 mnutos, uma chamada a cada 30 segundos

10

Continuação de rotina de tempo até o consentimento encontre o status "REJECTED"

11

Chamada de endpoint POST /portabilities enviando os seguintes valores:  
data.institution.creditor.companyCnpj = original companyCnpj  
instalmentPeriodicity = original instalmentPeriodicity  
proposedContract.totalNumberOfInstalments = original dueInstalments  
contractAmount = original contractOutstandingBalance  
Authorization = token associated to the expired consent

Status 401 - Validação de resposta conforme especificação garantindo que o consentimento está expirado

12

Chamada de endpoint POST /portabilities com um x-fapi-interaction-id inválido

Status 400 - Validação de mensagem garantindo que o x-fapi-interaction-id inválido foi enviado

13

Chamada de endpoint POST /portabilities enviando os seguintes valores:  
data.institution.creditor.companyCnpj = original companyCnpj  
instalmentPeriodicity = original instalmentPeriodicity  
proposedContract.totalNumberOfInstalments = original dueInstalments  
contractAmount = original contractOutstandingBalance  
valid x-fapi-interaction-id

Status 202 - Validação de resposta de acordo com a especificação e garante que o x-fapi-interaction-id esta correto

14

Fim do teste

## Diagrama de sequência

![ct19.svg](images/ct19.svg)
