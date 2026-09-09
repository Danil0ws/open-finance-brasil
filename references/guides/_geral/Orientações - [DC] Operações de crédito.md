# Orientações - [DC] Operações de crédito

none

### Regras de implementação pela instituição transmissora

No caso de operações de crédito o cliente efetua o compartilhamento por agrupamento de produtos ou seja, todas as modalidades de operações de crédito são compartilhadas escopo do open finance. A categorização das operações de crédito a serem compartilhadas são chamadas de modalidade no Guia de Experiência do Usuário em função do uso da mesma terminologia “modalidade” na circular 4015, porém essa mesma categorização no doc 3040 é chamada de submodalidade. A fim de manter padronização no Open Finance, consideramos o termo “modalidade”. As modalidades definidas na circular 4015 foram baseadas nas submodalidades do 3040, porém não há correspondência exata. Utilizaremos no texto abaixo o termo “passíveis de compartilhamento” para contratos ativos ou que estiveram ativos nos últimos 12m (considerando o momento da consulta pela Receptora).

### Tabela com as modalidades e submodalidades das APIs de operações de crédito

**Domínio**

**Descrição**

**Sub**

**Descrição**

**Circular 4015**

01

Adiantamentos a depositantes

01

Adiantamentos a depositantes

Adiantamentos a depositantes

02

Empréstimos

02

Crédito pessoal - com consignação em folha de pagam.

Crédito pessoal - consignado

02

Empréstimos

03

Crédito pessoal - sem consignação em folha de pagam

Crédito pessoal - sem consignação

02

Empréstimos

11

Home equity

Home equity

02

Empréstimos

12

Microcrédito produtivo orientado

Microcrédito

02

Empréstimos

13

Cheque especial

Cheque especial

02

Empréstimos

14

Conta garantida

Conta garantida

02

Empréstimos

15

Capital de giro com prazo de vencimento de até 365 dias

Capital de giro

02

Empréstimos

16

Capital de giro com prazo de vencimento superior a 365 dias

Capital de giro

02

Empréstimos

17

Capital de giro com teto rotativo

Capital de giro

03

Direitos creditório descontados

01

Desconto de duplicatas

Desconto de duplicatas

03

Direitos creditório descontados

02

Desconto de cheques

Desconto de cheques

03

Direitos creditório descontados

03

Antecipação de faturas de cartão de crédito

Antecipação de faturas de cartão de crédito

03

Direitos creditório descontados

98

Outros direitos creditórios descontados

Desconto de nota promissória

03

Direitos creditório descontados

99

Outros títulos descontados

Desconto de nota promissória

04

Financiamentos

01

Aquisição de bens - veículos automotores

Aquisições de bens móveis

04

Financiamentos

02

Aquisição de bens - outros bens

Aquisições de bens móveis

04

Financiamentos

03

Microcréditos

Microcrédito produtivo orientado

08

Financiamentos

01

Custeiro

Rurais

08

Financiamentos

02

Investimento

Rurais

08

Financiamentos

03

Comercialização

Rurais

08

Financiamentos

04

Industrialização

Rurais

09

Financiamentos

01

Financiamento habitacional - SFH

Sistema Financeiro da Habilitação (SFH)

09

Financiamentos

02

Financiamento habitacional - exceto SFH 

Sistema Financeiro Imobiliário (SFI)

### Diagrama representacional dos status da API de Recursos (Resources)

**Consentimento (ex. 4 meses)**

**Cenários**

**Dia D**

**D +1M**

**D + 2M**

**D + 3M**

**D + 4M**

**D + 5M**

Produto encerrado\* em D -13M

Não é escopo de compartilhamento

Produto encerrado\* em D -11M

AVAILABLE

AVAILABLE

UNAVAILABLE

UNAVAILABLE

UNAVAILABLE

N/A\*\*

Produto encerrado\* em D + 2M

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

N/A\*\*

\*encerrado/liquidado/quitada…

\*\* Consentimento não autorizado

**Glossário:**

-   Dia D: dia do consentimento
    
-   Eixo X: representa o tempo em meses
    
-   Eixo em Y: representa os cenários que são produtos e suas vigências. Ex.: empréstimo que se encerrou em 13 meses.
    
-   O encontro dos eixos representa os status da resources, naquele tempo para aquele produto.
    

### Regras para o preenchimento do campo status do Recurso (PENDING\_AUTHORISATION, AVAILABLE, UNAVAILABLE, TEMPORARILY\_UNAVAILABLE) e a transição entre status.

PENDING\_AUTHORISATION: indica a existência de pendências para o compartilhamento do recurso, em caso de múltiplas alçadas, quando é necessário o consentimento de mais de um titular. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:

wide1800

UNAVAILABLE: indica que o recurso (contrato) se encontra indisponível para consulta na API de Operação de crédito. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:

wide1800

TEMPORARILY\_UNAVAILABLE: indica que o recurso (contrato) se encontra temporariamente indisponível para consulta nas APIs de operações de crédito da modalidade em questão. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:

wide1800

### Tabela descritiva das possibilidades de interação entre API de Recursos (Resources) e as APIs de Operações de Crédito

(A tabela abaixo explicita os status esperados par as APIs de Operações de crédito com a utilização da API de Adiantamento a Depositantes (Unarranged-Accounts-Overdraft) como exemplo)

Cenário

Status do recurso na Transmissora

API Resources (.../resources/v1/resources)

API Listagem Produto (.../unarranged-accounts-overdraft/v1/contracts)

APIs Dados Produto

(.../unarranged-accounts-overdraft/v1/contracts/{contractId}

Sem consentimento

\-

401 unauthorized

401 unauthorized

401 unauthorized

Com consentimento não autorizado

\-

401 unauthorized

401 unauthorized

401 unauthorized

Com consentimento autorizado (pendente múltipla alçada)

\-

200 - Retorna recurso com status PENDING\_AUTHORISATION

.../resources/v1/resources

\[

{

“resourceId”: “1234”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “PENDING\_

AUTHORISATION”

}

\]

200 Não retorna

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[\]

...

}

403 forbidden

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“code”: “status\_RESOURCE\_

PENDING\_AUTHORISATION”,

“title”: “Aguardando autorização

de múltiplas alçadas”,

“detail”: “xxxxxx”

}

Com consentimento autorizado (aprovado múltipla alçada)

OK

200 - Retorna o recurso com status AVAILABLE

.../resources/v1/resources

\[

{

“resourceId”: “1234”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “AVAILABLE”

},

{

“resourceId”: “4321”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “AVAILABLE”

}

\]

200 retorna o recurso na lista

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[

{

“contractId”: “1234”,

“brandName”: “Organização A”,

“companyCnpj”:

“60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “123456”

},

{

“contractId”: “4321”,

“brandName”: “Organização A”,

“companyCnpj”:

“60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “654321”

} \] ...

200 retorna dados para o recurso

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“data”: \[

{

“contractId”: “1234”,

“brandName”: “Organização A”,

“companyCnpj”: “60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “123456”

},

\] ...

}

Com consentimento autorizado (aprovado múltipla alçada)

Bloqueio Temporário

200 - Retorna o recurso com status TEMPORARY\_UNAVAILABLE

.../resources/v1/resources

\[

{

“resourceId”: “1234”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “TEMPORARY\_

UNAVAILABLE”

},

{

“resourceId”: “4321”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “AVAILABLE”

}

\]

200 Não retorna na lista o recurso “bloqueado”

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[

{

“contractId”: “4321”,

“brandName”: “Organização A”,

“companyCnpj”:

“60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “654321”

}

\] ...

}

403 forbidden

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“code”: “status\_RESOURCE\_

PENDING\_AUTHORISATION”,

“title”: “Aguardando autorização

de múltiplas alçadas”,

“detail”: “(uso a critério do

transmissor)”

}

Com consentimento autorizado (aprovado múltipla alçada)

Liquidado a menos de 12 meses

200 - Retorna o recurso como status AVAILABLE

.../resources/v1/resources

\[

{

“resourceId”: “1234”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “AVAILABLE”

},

{

“resourceId”: “4321”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “AVAILABLE”

}

\]

200 retorna o recurso na lista

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[

{

“contractId”: “1234”,

“brandName”: “Organização A”,

“companyCnpj”:

“60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “123456”

},

{

“contractId”: “4321”,

“brandName”: “Organização A”,

“companyCnpj”:

“60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “654321”

}\] ...}

200 retorna os dados

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“data”: \[

{

“contractId”: “1234”,

“brandName”: “Organização A”,

“companyCnpj”: “60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “123456”

},

\] ...

}

Com consentimento autorizado (aprovado múltipla alçada)

Liquidado a mais de 12 meses (recurso nunca compartilhado na vigência do consentimento)

200 – Não retorna o recurso

obs.: como exemplo o

recurso de resourceId 1234

foi liquidado a mais de 12

meses

.../resources/v1/resources

\[​

{​

“resourceId”: “4321”,​

“type”: “UNARRANGED\_​

ACCOUNT\_OVERDRAFT”,​

“status”: “AVAILABLE”​

}​

\]

200 – Não retorna o recurso

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[

{

“contractId”: “4321”,

“brandName”: “Organização A”,

“companyCnpj”:

“60500998000144”,

“productType”: “ADIANTAMENTO\_A\_

DEPOSITANTES”,

“productSubType”:

“ADIANTAMENTO\_A\_DEPOSITANTES”,

“ipocCode”: “654321”

}

\] ...

}

403 forbidden

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“code”: “RESOURCE\_FORBIDDEN”,

“title”: “Recurso inacessível”,

“detail”: “(uso a critério do transmissor)”

}

Com consentimento autorizado (aprovado múltipla alçada)

Liquidado a mais de 12 meses (recurso já compartilhado na vigência do consentimento)

200 - Retorna o recurso como status UNAVAILABLE

.../resources/v1/resources

\[

{

“resourceId”: “1234”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “UNAVAILABLE”

}

\]

200 – Não retorna o recurso

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[\]

...

}

403 forbidden

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“code”: “status\_RESOURCE\_

UNAVAILABLE”,

“title”: “Aguardando autorização

de múltiplas alçadas”,

“detail”: “(uso a critério do

transmissor)”

}

Com consentimento autorizado (recusado múltipla alçada)

\-

200 - Retorna recurso com status UNAVAILABLE

.../resources/v1/resources

\[

{

“resourceId”: “1234”,

“type”: “UNARRANGED\_

ACCOUNT\_OVERDRAFT”,

“status”: “UNAVAILABLE”

}

\]

200 Não retorna recurso recusado na lista

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[\]

...

}

403 forbidden

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“code”: “status\_RESOURCE\_

UNAVAILABLE”,

“title”: “Aguardando autorização

de múltiplas alçadas”,

“detail”: “(uso a critério do

transmissor)”

}

Com consentimento autorizado (recurso inexistente)

HTTP 200 - Retorna array vazio

.../resources/v1/resources

\[

\]

200 Não retorna

.../unarranged-accounts-overdraft/v1/contracts

{

“data”: \[\]

...

}

403 forbidden

.../unarranged-accounts-overdraft/v1/contracts/1234

{

“code”: “RESOURCE\_FORBIDDEN”,

“title”: “Recurso inexistente”,

“detail”: “(uso a critério do transmissor)”

}

Com consentimento revogado ou expirado**\***

401 unauthorized

401 unauthorized

401 unauthorized

-   **Para os cenários de consentimento revogado ou expirado, conforme determinado na especificação de segurança o access token associado ao mesmo é invalidado impossibilitando a consulta as APIs produtos por parte da Receptora.**
    

### Casos de uso de Operações de Crédito e o respectivo status a ser informado pela API de Recursos (Resources).

-   Operações de crédito liquidadas nos últimos 12 meses em relação à data da consulta pela Receptora devem retornar o status AVAILABLE;
    
-   Operações de crédito liquidadas há mais que 12 meses em relação a data da consulta pela Receptora devem retornar o status UNAVAILABLE;
    
-   Casos de uso que um cliente final efetue um consentimento para a qual um dos contratos exija a aprovação de múltiplas alçadas (PENDING\_AUTHORISATION) e o outro contrato esteja disponível para consulta (AVAILABLE), o comportamento esperado é que cada contrato tenha seu status representado de forma independente, disponibilizando imediatamente os contratos já aprovados.
    
-   Operações de crédito canceladas não são escopo de exposição no Open Finance. Contratos nessa situação deixam de ser escopo de exposição em novos consentimentos, já para consentimentos onde esse contrato já foi compartilhado, o recurso deve se tornar UNAVAILABLE;
    
-   Operações de crédito que tenham ido para perda não são escopo de exposição no Open Finance. Contratos nessa situação devem parar de ter suas informações compartilhadas, e o recurso correspondente deve ter seu status atualizado para UNAVAILABLE.
    
-   Operações de crédito portadas para outra instituição deixam de ser escopo de exposição no Open Finance. Contratos nessa situação deixam de ser escopo de exposição em novos consentimentos, já para consentimentos onde esse contrato já foi compartilhado, o recurso deve se tornar UNAVAILABLE.
    

### **Orientações para Preenchimento de Campos e Realização de Consultas de Endpoints das APIs de Operações de Crédito**

-   Na API Empréstimos, para os contratos já liquidados até a entrada em produção - Go Live - do versionamento 2.5.0 dessa API, o campo productSubtypeCategory poderá ser enviado com a opção "OUTRO“. Para contratos já liquidados, o envio dos campos relacionados a Portabilidade de Crédito listados abaixo, torna-se opcional.
    
-   Os campos relacionados à portabilidade de crédito são:
    

Endpoint

Campo

GET /contracts/{contractId}​

/data/hasInsuranceContracted​

GET /contracts/{contractId}​

/data/nextInstalmentAmount​

GET /contracts/{contractId}/payments​

/data/totalRemainingAmount​

GET /contracts/{contractId}/payments​

/data/lastUpdatedContractOutstandingBalance

-   Para evitar uso de recursos desnecessários nas infraestruturas das instituições, é recomendada a preservação de uso máximo dos limites operacionais para o endpoint `GET /contracts/{contractId}/payments` da API Empréstimos, só utilizando o máximo permitido de 120 consultas ao mês para o fluxo de realização de Portabilidade de Crédito.
    
-   Em situações normais, é suficiente uma consulta diária para informações que não são de alta volatilidade, dado que a informação fornecida por esse endpoint só deve ser alterada uma vez por mês. Pode haver a necessidade de consultas adicionais nos casos de contratos portados
    
-   A tabela abaixo traz instruções de preenchimento para os dados compartilhados no endpoint **GET /contracts/{contractId/payments** dos produtos de Crédito Rotativo para as APIs Empréstimos e Adiantamento a Depositantes
    

**Endpoint**

**Objeto**

**Campo(s)**

**Instruções de Preenchimento**

**Cheque especial**

**Conta garantida**

**Adiantamento a Depositantes**

Pagamentos

Pagamentos

contractOutstandingBalance

Informar saldo  
devedor (utilizado)

Informar saldo  
devedor (utilizado)

Informar saldo  
devedor (utilizado)

lastUpdatedcontractOutstandingBalanceDateTime

Não enviar

Não enviar

Campo não aplicável

totalRemainingAmount

Não enviar

Não enviar

Campo não aplicável

paidInstalments

Não enviar

Não enviar

Não enviar

Lista de pagamentos (/releases)

isOverParcelPayment

TRUE

TRUE

TRUE

paymentId

Informar identificador para o pagamento efetuado

Informar identificador para o pagamento efetuado

Informar identificador para o pagamento efetuado

instalmentId

Não enviar

Não enviar

Não enviar

paidDate

Data do débito do encargo, tarifa, multa, etc.

Data do débito do encargo, tarifa, multa, etc.

Data do débito do encargo, tarifa, multa, etc.

currency

BRL

BRL

BRL

paidAmount

Valor debitado de encargo e tarifa. (no caso de listagem de vários valores para as estruturas ovelParcel o campo deve ser a soma do(s) encargo(s) e tarifa(s) listados)

Valor debitado de encargo e tarifa. (no caso de listagem de vários valores para as estruturas ovelParcel o campo deve ser a soma do(s) encargo(s) e tarifa(s) listados)

Valor debitado de encargo e tarifa. (no caso de listagem de vários valores para as estruturas ovelParcel o campo deve ser a soma do(s) encargo(s) e tarifa(s) listados)

Pagamentos Tarifas fora da parcela (/releases/overParcel/fees)

Todos os campos do objeto

Preencher caso o pagamento seja de tarifas

Preencher caso o pagamento seja de tarifas

Preencher caso o pagamento seja de tarifas

Pagamentos encargos fora da parcela (/releases/overParcel/charges)

chargeType

Preencher caso o pagamento seja de encargo

Preencher caso o pagamento seja de encargo

Preencher caso o pagamento seja de encargo

chargeAdditionalInfo

Preencher se tratar de pagamento de encargo não constante do domínio delimitado

Preencher se tratar de pagamento de encargo não constante do domínio delimitado

Preencher se tratar de pagamento de encargo não constante do domínio delimitado

chargeAmount

Preencher caso o pagamento seja de encargo

Preencher caso o pagamento seja de encargo

Preencher caso o pagamento seja de encargo

-   O preenchimento do campo hasInsuranceContracted deve seguir as seguintes regras de preenchimento para os contratos das APIs Financiamento, Adiantamentos a Depositantes e Direitos Creditórios Descontados:
    
    -   Para consentimentos anteriores à publicação da versão:
        
        -   Contratos antigos o campo é opcional
            
        -   Contratos novos o campo deve ser informado
            
    -   Para consentimentos posteriores à publicação da versão:
        
        -   Todos os contratos deverão informar o campo
