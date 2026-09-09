# Cenário 10: credit-portability_api_x-fapi_test-module_v1 - CPC

**Tipo do teste**

Teste de exceção

**Descrição**

Validação de mensagens e comportamentos do sistema em situações de inconsistências na credencial de verificação de respostas.

**Objetivo**

Verificação de x-fapi nos endpoints

**Requisito de massa**

Um contrato do tipo CREDITO\_PESSOAL\_CLEAN com o campo status como 'DISPONIVEL' e o campo isEligible como 'TRUE'

## Script

Os passos abaixo são todas as requisições que serão feitas para a jornada do teste acima. Além das requisições temos as respostas esperada para cada requisição a ser realizada para respeitar o teste especifico.

Este cenário se encontra no arquivo disponibilizado em uma página de [WIKI](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-CPC-API?redirected_from=Credit-Portability-API) no Gitlab disponibilizado pela Raidiam.  
Foi feita a tradução para português e criado um diagrama de sequência para auxilio no entendimento do cenário de teste.

**Steps**

**Requisições**

**Respostas esperadas**

1

Chamada de endpoint POST /consents com o grupo de permissão 'Credit Operations'

Status 201 - Garantindo de status como AWAITING\_AUTHORISATION

2

Redirecionamento para usuário autorizar o consentimento

3

Chamada de endpoint GET /consents/{consentId}

Status 200 - Garantindo de status como AUTHORISED

4

Chamada de endpoint GET Loans Contracts

Status 200 - Recuperando todos os contractIds com productSubType = “CREDITO\_PESSOAL\_CLEAN” e companyCnpj

6

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility sem o x-fapi-interaction-id

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id não foi enviado

7

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility com um x-fapi-interaction-id inválido

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id inválido foi enviado

8

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility com x-fapi-interaction-id válido, para cada contractId até encontrar ao menos um com status como "DISPONIVEL" e isEligible como "TRUE"

9

Chamada de endpoint GET Loans Contracts/{contractId}

Status 200 - Recuperando instalmentPeriodicity

10

Chamada de endpoint GET Loans Contracts/{contractId}/scheduled-installments

Status 200 - Recuperando dueInstalments

11

Chamada de endpoint GET Loans Contracts/{contractId}/payments

Status 200 - Recuperando contractOutstandingBalance

12

Chamada de endpoint POST /portabilities sem o x-fapi-interaction-id

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id não foi enviado

13

Chamada de endpoint POST /portabilities com um x-fapi-interaction-id inválido

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id inválido foi enviado

14

Chamada do endpoint POST /portabilities enviando os seguintes valores:  
data.institution.creditor.companyCnpj = original companyCnpj  
instalmentPeriodicity = original instalmentPeriodicity  
proposedContract.totalNumberOfInstalments = original dueInstalments  
contractAmount = original contractOutstandingBalance  
valid x-fapi-interaction-id

Status 202 - Validando resposta conforme especificação e garantindo que x-fapi-interaction-id válido

15

Chamada de endpoint Get /portabilities/{portabilityId} sem o x-fapi-interaction-id

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id não foi enviado

16

Chamada de endpoint Get /portabilities/{portabilityId} com um x-fapi-interaction-id inválido

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id inválido foi enviado

17

Chamada de endpoint PATCH /portabilities/{portabilityId}/cancel sem o x-fapi-interaction-id

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id não foi enviado

18

Chamada de endpoint PATCH /portabilities/{portabilityId}/cancel com o x-fapi-interaction-id inválido

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id inválido foi enviado

19

Chamada de endpoint GET portabilities/{portabilityId}/account-data sem o x-fapi-interaction-id

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id não foi enviado

20

Chamada de endpoint GET portabilities/{portabilityId}/account-data com um x-fapi-interaction-id inválido

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id inválido foi enviado

21

Chamada de endpoint POST /portabilities/{portabilityId}/payment sem o x-fapi-interaction-id

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id não foi enviado

22

Chamada de endpoint POST /portabilities/{portabilityId}/payment com um x-fapi-interaction-id inválido

Status 400 - Validando mensagem de erro garantido que um x-fapi-interaction-id inválido foi enviado

23

Fim do teste

## Diagrama de sequência

![ct10DS.svg](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/1329299770/child/attachment/att1329299784/download)
