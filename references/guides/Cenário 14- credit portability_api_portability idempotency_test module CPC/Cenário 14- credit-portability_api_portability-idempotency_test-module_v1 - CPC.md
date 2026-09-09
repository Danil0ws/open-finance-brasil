# Cenário 14: credit-portability_api_portability-idempotency_test-module_v1 - CPC

**Tipo do teste**

Teste de exceção

**Descrição**

Validação de mensagens e comportamentos do sistema em situações de inconsistências na credencial de verificação de respostas.

**Objetivo**

Garantir que há validações de idempotência

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

5

Chamada de endpoint GET /credit-operations/{contractId}/portability-eligibility com x-fapi-interaction-id válido, para cada contractId até encontrar ao menos um com status como "DISPONIVEL" e isEligible como "TRUE"

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

Chamada de endpoint POST /portabilities utilizando os seguintes valores:  
data.institution.creditor.companyCnpj = original companyCnpj  
instalmentPeriodicity = original instalmentPeriodicity  
proposedContract.totalNumberOfInstalments = original dueInstalments  
contractAmount = original contractOutstandingBalance

10

Chamada de endpoint POST /portabilities com o mesmo x-idempotency-key e payload da requisição anterior

Status 202 - Validação de resposta de acordo com especificação

11

Chamada de endpoint POST /portabilities com o mesmo x-idempotency-key mas com payload diferente da requisição anterior

Status 422 - Validação de mensagem de erro como 'ERRO\_IDEMPOTENCIA'

12

Fim do teste

## Diagrama de sequência

![ct14DS.svg](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/1329299886/child/attachment/att1329299903/download)
