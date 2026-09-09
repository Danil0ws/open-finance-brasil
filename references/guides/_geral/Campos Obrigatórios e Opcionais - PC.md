# Campos Obrigatórios e Opcionais - PC

v 1.08

# **Credit Portability API**

## Campos que devem ser informados à PCM via POST

**Campo**

**Definição**

**Regra de preenchimento**

**Obrigatório**

**Tipo**

**Roles**

**Http code**

**Métodos**

**Domínio**

**Endpoints**

**Versões**

**Tamanho máximo**

**Valor mínimo**

**Valor máximo**

**Padrão**

**Exemplo**

clientOrgId

Identificador da organização de onde a chamada foi disparada.

Sim

string <uuid>

CLIENT

SERVER

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

36

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

56411f7e-d58b-44a8-8a2b-ff326d3f2955

clientSSId

Identificador do software statement de onde a chamada foi disparada. A PCM garante que foi esta orgId que obteve o token de acesso utilizado neste reporte.

Sim

string <uuid>

CLIENT

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

36

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

84570da9-567b-4201-9b77-c715bc5bffde

consentId

Código identificador do consentimento de dados utilizado pela instituição proponente para acessar as informações do contrato de crédito do cliente na credora

Sim

string <uuid>

CLIENT

SERVER

Todos exceto 4xx e 5xx

POST

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

100

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD33123

correlationId

ID de correlação que identifica uma sequência de chamadas inter-relacionadas no ecossistema. Diferente do fapiInteractionId que serve para identificar cada par request-response (interação), o identificador de correlação serve para ligar diferentes reportes quando estes representam uma jornada ou uma sequência de chamadas. Este valor é de livre provimento pelo reportador.

Não

string

CLIENT

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

100

^\[- /:\_.',0-9a-zA-Z\]{0,100}$

uGQHwNupARo7I9E2PLJZph18a0M9y7DcUe7ITt3DqUOJd9NVjnskxf2

creationDateTime

Data e hora em que a Proponente registrou a presente proposta (chamada ao POST /portabilities). Uma string com data e hora conforme especificação ISO8601, sempre com a utilização de timezone UTC-0 (UTC time format).

Preencher com o valor do campo "/data/creationDateTime" no response do POST

Sim

string

CLIENT

Todos exceto 4xx e 5xx

POST  
GET

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}

v1

20

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

2020-07-21T08:30:00Z

creditPortabilityStatus

Informação sobre o status de um pedido de portabilidade de crédito

Preencher com o valor do campo "/data/status"

Sim

string

CLIENT

SERVER

Todos exceto 4xx e 5xx

GET

ACCEPTED\_SETTLEMENT\_COMPLETED, ACCEPTED\_SETTLEMENT\_IN\_PROGRESS, CANCELLED, PENDING, PAYMENT\_ISSUE, PORTABILITY\_COMPLETED, RECEIVED, REJECTED

/open-banking/credit-portability/v_x_/portabilities/{portabilityId}

v1

RECEIVED

endpoint

Identificação do endpoint que foi utilizado na transação reportada. A identificação do endpoint deve estar presente na lista de endpoints aceitos pela PCM para ser considerado válido. Nesse campo não deve ser utilizado o path da requisição original.

Não usar o caminho real: é fundamental NÃO utilizar o caminho completo da requisição original, que inclui dados variáveis (ex: IDs).  
Exemplo: Se a requisição foi para /open-banking/credit-cards-accounts/v1/accounts/123456789/transactions, o valor a ser enviado no endpoint deve ser /open-banking/credit-cards-accounts/v1/accounts/{creditCardAccountId}/transactions. O dado real 123456789 não deve ser enviado no campo endpoint.

Sim

string

CLIENT

SERVER

Todos

POST  
GET  
PATCH

Endpoints aceitos pela PCM

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

/open-banking/consents/v2/consents

endpointUriPrefix

Endereço do servidor de destino da chamada, incluindo o prefixo quando houver. O formato do campo deverá ser o seguinte:  
[https://{host}/{prefixo},](#) sendo:  
host: endereço FQDN do servidor de destino  
prefixo: toda a parte do path que vem antes da string /open-banking

Exemplos:

1.  Para uma requisição em `https://openbanking.instituicao-1.com.br/opbk/open-banking/products-services/v1/business-accounts`, o dado a ser enviado é `https://openbanking.instituicao-1.com.br/opbk`.
    

2.  Para uma requisição em `https://openbanking.instituicao-2.com.br/open-banking/products-services/v1/business-accounts`, o dado a ser enviado é `https://openbanking.instituicao-1.com.br/`.
    

Nos reportes relativos aos endpoints /token e /register este campo deverá conter a URL inteira do request.

Exemplos: `https://oauth2.cartaodummy.opf.instituicao/as/token.oauth2` `https://instituicao.com.br/orgs/instituicao/reg`

Sim

string

CLIENT

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

200

^\[- /:\_.',0-9a-zA-Z\]{0,200}$

[https://openbanking.instituicao-1.com.br/opbk](https://openbanking.instituicao-1.com.br/opbk)

errorCode

Registra os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

Não

string

CLIENT

4xx e 5xx

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

fapiInteractionId

UUID RFC4122 que identifica uma transação específica entre dois participantes no ecossistema Open Finance. Este identificador é derivado do header HTTP x-fapi-interaction-id, conforme especificação RFC4122 para geração de identificadores únicos universais. Serve como chave de correlação fundamental para rastreabilidade, auditoria e conciliação de transações entre instituições participantes. Mais informações em Cabeçalhos HTTP na documentação de produtos do Open Finance Brasil

**Para CLIENT:**

**OBRIGATÓRIO** em todos os cenários onde o x-fapi-interaction-id foi gerado, incluindo respostas com status 4xx (incluindo 408 - timeout), respostas com status 5xx recebidas e transações completadas com sucesso.

**Para SERVER:**

**OBRIGATÓRIO** quando o x-fapi-interaction-id foi recebido na requisição ou quando o Server gerou o x-fapi-interaction-id conforme especificação da API de Produto. Falhas de aplicação, validação, autorização, timeout, indisponibilidade de dependências ou erros internos (5xx) NÃO caracterizam, por si só, falha crítica para fins de ausência do x-fapi-interaction-id, desde que a requisição tenha sido recebida pelo Server.

**Nota:** A ausência do fapiInteractionId compromete significativamente a capacidade de correlação e auditoria das transações no ecossistema Open Finance

Sim

string <uuid>

CLIENT

SERVER

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

36

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

d78fc4e5-37ca-4da3-adf2-9b082bf92280

httpMethod

Método HTTP da solicitação.

Sim

enum<string> 

CLIENT

SERVER

Todos

POST  
GET  
PATCH

DELETE, GET, PATCH, POST, PUT

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

GET

portabilityId

Código identificador do pedido de portabilidade realizado.

O envio dessa informação é obrigatório, exceto nos casos onde ela não esteja disponível como, por exemplo, em respostas com status 5xx, ou em chamadas que terminaram por timeout onde o reporte tem que ser enviado, mas sem esse atributo. Nos demais cenários, o envio é obrigatório.  
Preencher com o valor do campo "/data/portabilityId"​no response do POST

Sim

string <uuid>

CLIENT

SERVER

Todos exceto 4xx e 5xx

POST  
GET

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}

v1

100

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

54d5348c-1a3f-4ff4-a8a8-d0724fb806c6

processTimespan

Tempo em milissegundos inteiros decorrido desde o registro do timestamp até a chegada do primeiro byte da resposta do server.

Não

number

CLIENT

SERVER

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

120.000001

rejectedBy

Usuário responsável pela rejeição da proposta

Quando a origem da informação for a CREDORA, preencher com o valor do campo "/data/rejection/rejectedBy"  
Quando a origem da informação for o PROPONENTE, preencher com o valor enviado no campo "/data/rejectedBy"  
  
Só será preenchido caso o status seja REJECTED ou CANCELLED

Não

string

CLIENT

SERVER

Todos exceto 4xx e 5xx

GET  
PATCH

CREDORA, PROPONENTE, USUARIO

/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel

CREDORA

rejectionReason

Motivo de recusa do pedido de portabilidade

Motivo de recusa do pedido de portabilidade.  
Só será preenchido caso o status seja REJECTED ou CANCELLED  
A consulta ao endpoint de GET é requerida para o fluxo de portabilidade:

-   Quando a origem da informação for a CREDORA, preencher com o valor do campo "/data/statusReason/reasonType”
    
-   Quando a origem da informação for o PROPONENTE, preencher com o valor enviado no campo "/data/reason/type"
    

Não

enum<string> 

CLIENT

SERVER

Todos exceto 4xx e 5xx

GET  
PATCH

POLITICA\_DE\_CREDITO, SALDO\_DEVEDOR\_ATUALIZADO\_SUBSTANCIALMENTE\_DIVERGENTE, CLIENTE\_COM\_ACAO\_JUDICIAL, CONTRATO\_JA\_LIQUIDADO, DECURSO\_DO\_PRAZO\_PARA\_PAGAMENTO, MODALIDADE\_DA\_OPERACAO\_INCOMPATIVEL, PORTABILIDADE\_CANCELADA\_POR\_FALTA\_DE\_LIQUIDACAO, PORTABILIDADE\_EM\_ANDAMENTO, RETENCAO\_DO\_CLIENTE, CANCELADO\_PELO\_CLIENTE, DIVERGENCIA\_DE\_PAGAMENTO\_EFETUADO, OUTROS

/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel

v1

CANCELADO\_PELO\_CLIENTE

statusUpdateDateTime

Data e hora em que o contrato teve o status atualizado. Uma string com data e hora conforme especificação ISO-8601, sempre com a utilização de timezone UTC(UTC time format).

Preencher com o valor do campo "/data/statusUpdateDateTime"

Sim

string

CLIENT

SERVER

Todos exceto 4xx e 5xx

GET

/open-banking/credit-portability/v_x_/portabilities/{portabilityId}

v1

20

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

2020-07-21T08:30:00Z

timestamp

Data/Hora UTC no formato ISO8601 com milissegundos (YYYY-MM-DDTHH:mm:ss.sssZ) do momento em que a chamada foi disparada, imediatamente antes do primeiro byte enviado na requisição.

Sim

string <date-time>

CLIENT

SERVER

Todos

POST  
GET  
PATCH

/open-banking/credit-portability/v_x_/portabilities  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/account-data  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/cancel  
/open-banking/credit-portability/v_x_/portabilities/{portabilityId}/payment  
/open-banking/credit-portability/v_x_/credit-operations/{contractId}/portability-eligibility

v1

28

^\\d{4}-\\d{2}-\\d{2}T(?:\[01\]\\d|2\[0-3\]):\[0-5\]\\d:\[0-5\]\\d(?:\\.\\d+)?(?:Z|\[+-\]\[01\]\\d:\[0-5\]\\d)$

2021-11-11T18:08:08.278Z

## Campos retornados em response

**Campo**

**Definição**

**Tipo**

**Domínio**

**Tamanho máximo**

**Padrão**

**Exemplo**

correlationId

Retorna o valor do atributo correlationId informado na solicitação de inclusão de reporte sem alteração.

string

^\[- /:\_.',0-9a-zA-Z\]{0,100}$

uGQHwNupARo7I9E2PLJZph18a0M9y7DcUe7ITt3DqUOJd9NVjnskxf2

reportId

Identificador único interno do reporte no formato UUID v4.

string

36

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

efc98fff-6265-4a2d-9f22-e893fb828ec8

status

Informa o status do registro de reporte.

string

ACCEPTED, DISCARDED, PAIRED, PAIRED\_INCONSISTENT, UNPAIRED

PAIRED

## Campos adicionais retornados no GET

O GET retorna todos os campos do POST e do response, além dos adicionais abaixo

**Campo**

**Definição**

**Obrigatório**

**Tipo**

**Tamanho máximo**

**Padrão**

**Exemplo**

createdAt

Carimbo do tempo do momento da criação do registro. Esta é a data da criação do reporte na PCM.

Não

string <date-time>

28

2020-07-21T08:30:00Z

pairedReportId

Esse atributo indica o reportId do registro que forma uma correlação com o presente registro. Se essa informação existir, o status do registro atual deverá ser PAIRED

Não

string <uuid>

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

9a97c2df-b261-4fc2-aa66-d1b5168397da

updatedAt

Carimbo do tempo do momento da última atualização do registro. Esta é a data da atualização do reporte na PCM.

Não

string <date-time>

28

2026-01-14 15:53:50.978000 UTC
