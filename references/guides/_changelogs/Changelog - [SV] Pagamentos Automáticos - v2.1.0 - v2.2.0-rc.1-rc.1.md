# Changelog - [SV] Pagamentos Automáticos - v2.1.0 - v2.2.0-rc.1-rc.1

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

/info

Alterado - "version"

Alteração

2.1.0

2.2.0-rc.1

paths

Adicionado - "/pix/recurring-payments/{originalRecurringPaymentId}/retry"

Adição

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/originalRecurringPaymentId

Alterado - "description"

Alteração

Campo que contém o código ou o identificador da tentativa original de pagamento que falhou. Código ou identificador único criado ...

Campo que contém o código ou o identificador da tentativa original de pagamento que falhou. Código ou identificador único criado...

get/responses/200/data/items/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/items/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

get/responses/200/data/items/paymentReference

Alterado - "maxLength"

Alteração

10

14

get/responses/200/data/items/paymentReference

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detent...

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta...

get/responses/200/data/items/paymentReference

Adicionado - "example"

Adição

23-07-2025/P1W

get/responses/200/data/items/paymentReference

Adicionado - "minLength"

Adição

4

get/responses/200/data/items/paymentReference

Adicionado - "pattern"

Adição

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

get/responses/200/data/items/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## POST /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/requestBody/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

post/requestBody/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

post/requestBody/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

post/requestBody/data/paymentReference

Alterado - "maxLength"

Alteração

10

14

post/requestBody/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detent...

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta...

post/requestBody/data/paymentReference

Adicionado - "example"

Adição

23-07-2025/P1W

post/requestBody/data/paymentReference

Adicionado - "minLength"

Adição

4

post/requestBody/data/paymentReference

Adicionado - "pattern"

Adição

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

post/requestBody/data/recurringConsentId

Alterado - "description"

Alteração

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada. Deverá ser um URN - Uniform...

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada. Deverá ser um URN - Uniform...

post/requestBody/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/responses/201/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/responses/201/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

post/responses/201/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

post/responses/201/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/responses/201/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

post/responses/201/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

post/responses/201/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

post/responses/201/data/paymentReference

Alterado - "maxLength"

Alteração

10

14

post/responses/201/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detent...

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta...

post/responses/201/data/paymentReference

Adicionado - "example"

Adição

23-07-2025/P1W

post/responses/201/data/paymentReference

Adicionado - "minLength"

Adição

4

post/responses/201/data/paymentReference

Adicionado - "pattern"

Adição

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

post/responses/201/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

get/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

get/responses/200/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

get/responses/200/data/paymentReference

Alterado - "maxLength"

Alteração

10

14

get/responses/200/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detent...

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta...

get/responses/200/data/paymentReference

Adicionado - "example"

Adição

23-07-2025/P1W

get/responses/200/data/paymentReference

Adicionado - "minLength"

Adição

4

get/responses/200/data/paymentReference

Adicionado - "pattern"

Adição

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

get/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## PATCH /pix/recurring-payments/{recurringPaymentId}

### request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

patch/responses/200/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

patch/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

patch/responses/200/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

patch/responses/200/data/paymentReference

Alterado - "maxLength"

Alteração

10

14

patch/responses/200/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detent...

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta...

patch/responses/200/data/paymentReference

Adicionado - "example"

Adição

23-07-2025/P1W

patch/responses/200/data/paymentReference

Adicionado - "minLength"

Adição

4

patch/responses/200/data/paymentReference

Adicionado - "pattern"

Adição

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

patch/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/requestBody/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/dat...

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência. Uma string com data e hora conform...

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com ...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/responses/201/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/dat...

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência. Uma string com data e hora conform...

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com ...

post/responses/201/data/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

post/responses/201/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

post/responses/201/data/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

post/responses/201/data/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

post/responses/201/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/dat...

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência. Uma string com data e hora conform...

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com ...

get/responses/200/data/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

get/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

get/responses/200/data/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

get/responses/200/data/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

get/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

patch/requestBody/data/oneOf/0/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

patch/requestBody/data/oneOf/2/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

patch/requestBody/data/oneOf/2/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

patch/requestBody/data/oneOf/2/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

patch/requestBody/data/oneOf/2/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

patch/requestBody/data/oneOf/2/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

patch/responses/200/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/dat...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência. Uma string com data e hora conform...

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com ...

patch/responses/200/data/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

patch/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

patch/responses/200/data/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

patch/responses/200/data/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

patch/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...
