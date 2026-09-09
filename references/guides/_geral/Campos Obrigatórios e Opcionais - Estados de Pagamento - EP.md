# Campos Obrigatórios e Opcionais - Estados de Pagamento - EP

v 1.04

Dica: para rolar a tabela horizontalmente, segure SHIFT e utilize o botão de rolagem do mouse.

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Payment Status API**

## Campos que devem ser informados à PCM via POST

**Campo**

**Definição**

**Obrigatório**

**Tipo**

**Regra de preenchimento**

**Roles**

**Domínio**

**Tamanho máximo**

**Padrão**

**Exemplo**

clientOrgId

Identificador da organização de onde a chamada foi disparada.

Sim

string <uuid>

SERVER

36

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

d78fc4e5-37ca-4da3-adf2-9b082bf92280

consentId

Identificador único do consentimento criado para aquele pagamento.

Sim

string

SERVER

100

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9-\]{0,31}:\[a-zA-Z0-9()+,-.:=@;$\_!\*''%/?#\]+

uGQHwNupARo7I9E2PLJZph18a0M9y7DcUe7ITt3DqUOJd9NVjnskxf2

eventDateTime

Data e hora associados à mudança de estados finais reportados, como liquidação, rejeição ou cancelamento. Deve ser informado em UTC-0.

Sim

string <date-time>

SERVER

28

2025-08-18T00:00:00Z

paymentId

Código único para identificar a transação de pagamento

Sim

string

SERVER

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

d78fc4e5-37ca-4da3-adf2-9b082bf92280

paymentStatus

Status de agendamento ou final do pagamento

Sim

enum<string> 

SERVER

ACSC, RJCT, CANC, SCHD

ACSC

paymentType

Tipo de pagamento realizado

Sim

enum<string> 

SERVER

AUTOMATIC, IMMEDIATE, RECURRENT, SCHEDULED, SWEEPING, WITHDRAW, CHANGE

RECURRENT

statusReasonCode

Razão do status informado.

Sim

string

Campo atrelado ao status de pagamento. Quando o status for RJCT (Rejected), o valor deve ser preenchido com o motivo da rejeição (valores previstos em rejectionReason.Code). Quando o status for CANC (Cancelled), o valor deve ser preenchido com o motivo do cancelamento (valores previstos em cancellationReason.Code).

SERVER

**Para paymentStatus = CANC**

CANCELADO\_AGENDAMENTO, CANCELADO\_PENDENCIA, CANCELADO\_MULTIPLAS\_ALCADAS

**Para paymentStatus = RJCT**

AUTENTICACAO\_DIVERGENTE, COBRANCA\_INVALIDA, CONSENTIMENTO\_INVALIDO, CONTA\_NAO\_PERMITE\_PAGAMENTO, CONTAS\_ORIGEM\_DESTINO\_IGUAIS, DETALHE\_PAGAMENTO\_INVALIDO, DETALHE\_TENTATIVA\_INVALIDO, FALHA\_AGENDAMENTO\_PAGAMENTOS, FALHA\_INFRAESTRUTURA, FALHA\_INFRAESTRUTURA\_DETENTORA, FALHA\_INFRAESTRUTURA\_DICT, FALHA\_INFRAESTRUTURA\_ICP, FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR, FALHA\_INFRAESTRUTURA\_SPI, FLUXO\_NAO\_SUPORTADO\_PRODUTO, FORA\_PRAZO\_PERMITIDO, LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO, LIMITE\_PERIODO\_VALOR\_EXCEDIDO, LIMITE\_TENTATIVAS\_EXCEDIDO, LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO, LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO, NAO\_INFORMADO, PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO, PAGAMENTO\_RECUSADO\_DETENTORA, PAGAMENTO\_RECUSADO\_SPI, QRCODE\_INVALIDO, REJEITADO\_USUARIO, SALDO\_INSUFICIENTE, TEMPO\_EXPIRADO\_AUTORIZACAO, TEMPO\_EXPIRADO\_CONSUMO, TITULARIDADE\_INCONSISTENTE, VALOR\_ACIMA\_LIMITE, VALOR\_INVALIDO

FLUXO\_NAO\_SUPORTADO\_PRODUTO

## Campos retornados em response

**Campo**

**Definição**

**Tipo**

**Domínio**

**Tamanho máximo**

**Padrão**

**Exemplo**

paymentId

Código único para identificar a transação de pagamento

string

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

d78fc4e5-37ca-4da3-adf2-9b082bf92280

reportId

Identificador único interno do reporte no formato UUID v4.

string

36

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

efc98fff-6265-4a2d-9f22-e893fb828ec8

status

Informa o status do registro de reporte.

**ACCEPTED**: O status ACCEPTED indica que a validação de formato do reporte não tem erros e este será enviado para processamento.  
**DISCARDED**: O status DISCARDED indica que o reporte enviado pelo participante foi rejeitado pela PCM. O motivo do descarte será enviado com a resposta, podendo ser por conta de um reporte inválido ou por um erro no processamento. Não é possível modificar um reporte DISCARDED, portanto o reportador deverá corrigir o registro que apresentou erro e reenviar via POST.

enum<string>

ACCEPTED, DISCARDED

ACCEPTED

## Campos adicionais retornados no GET

O GET retorna todos os campos enviados no POST e no response, além dos adicionais abaixo

**Campo**

**Definição**

**Tipo**

**Tamanho máximo**

**Padrão**

**Exemplo**

createdAt

Carimbo do tempo do momento da criação do registro

string <date-time>

28

2026-01-14 13:08:25.319000 UTC
