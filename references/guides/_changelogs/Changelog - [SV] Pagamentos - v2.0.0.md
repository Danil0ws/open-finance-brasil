# Changelog - [SV] Pagamentos - v2.0.0

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

Orientações

Atualizado a descrição da Role de PAGTO.

Orientações

Adicionado subseção Regras do arranjo Pix.

Orientações / Controle de Acesso

Adicionado descrição

Texto em todas as Apis

Alterado descrição de Open Banking para Open Finance

Logo

Alterado logo de Open Baning para Open Finance

Aprovações de múltipla alçada

Adicionado descrição sobre - Aprovações de múltipla alçada

Orientações

Adicionado - “Validações“

POST /consents

**Campo**

**O que foi feito?**

payments/date (request)

Alterada a descrição

payments/date (response)

Alterada a descrição

/payment/ibgeTownCode (request)

Alterada descrição

/payment/ibgeTownCode (response)

Alterada descrição

consentId (response)

Alterado pattern

links/self (response)

Alterado pattern

meta

Alterada descrição em todos os responses

status code 201; 400; 401; 403; 404; 405; 406; 415; 422; 429; 500; default

Removido totalPages

status code 201; 400; 401; 403; 404; 405; 406; 415; 422; 429; 500; default

Removido totalRecords

detail (422)

Alterado pattern

title (422)

Alterado pattern

AdditionalProperties

Removida a explicitude do additionalProperties

security

Removido - "OpenId"

data/payment/amount (response)

Alterado descrição

status code 529

Adicionado status code

data/creditor/name (request)

Alterado - "maxLength"

data/creditor/name (request)

Alterado - "pattern"

data/debtorAccount/issuer (request)

Alterado - "pattern"

data/debtorAccount/number (request)

Alterado - "pattern"

data/payment/details/creditorAccount/issuer (request)

Alterado - "pattern"

data/payment/details/creditorAccount/number (request)

Alterado - "pattern"

data/payment/shedule

Adicionado - "schedule"

data/creditor/name (response) (201)

Alterado - "maxLength"

data/creditor/name (response) (201)

Alterado - "pattern"

data/debtorAccount/issuer (response) (201)

Alterado - "pattern"

data/payment/date (response) (201)

Alterado - "description"

data/payment/details/creditorAccount/issuer (response) (201)

Alterado - "pattern"

data/payment/details/creditorAccount/number (response) (201)

Alterado - "pattern"

data/payment/Schedule (response) (201)

Adicionado - "schedule"

data/creditor/personType (request)

Removido - "maxLength"

data/debtorAccount/accountType (request)

Removido - "maxLength"

data/payment/details/creditorAccount/accountType (request)

Removido - "maxLength"

data/payment/details/localInstrument (request)

Removido - "maxLength"

data/payment/schedule (request)

Alterado - "description"

data/payment/schedule/single/date (request)

Alterado - "description"

data/payment/type (request)

Removido - "maxLength"

post/responses/201/data/creditor/personType

Removido - "maxLength"

post/responses/201/data/debtorAccount/accountType

Removido - "maxLength"

post/responses/201/data/payment/details/creditorAccount/accountType

Removido - "maxLength"

post/responses/201/data/payment/details/localInstrument

Removido - "maxLength"

post/responses/201/data/payment/schedule

Alterado - "description"

post/responses/201/data/payment/schedule/single/date

Alterado - "description"

post/responses/201/data/payment/type

Removido - "maxLength"

post/responses/201/data/status

Removido - "maxLength"

post/responses/422/errors/items/code

Alterado - "description"

post/responses/422/errors/items/code

Alterado - "example"

post/responses/422/errors/items/code

Removido - "maxLength"

post/responses/422/errors/items/code/enum

Adicionado - "DATA\_PAGAMENTO\_INVALIDA"

post/responses/422/errors/items/code/enum

Removido - "DATA\_PGTO\_INVALIDA"

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

post/responses/422/errors/items/code/enum

Adicionado - "FORMA\_PAGAMENTO\_INVALIDA"

post/responses/422/errors/items/code/enum

Removido - "FORMA\_PGTO\_INVALIDA"

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

post/responses/422/errors/items/detail

Alterado - "description"

post/responses/422/errors/items/detail

Alterado - "example"

post/responses/422/errors/items/title

Alterado - "description"

post/requestBody/data/debtorAccount/issuer

Adicionado - "minLength"

post/requestBody/data/debtorAccount/number

Alterado - "minLength"

post/requestBody/data/payment/details/creditorAccount/issuer

Adicionado - "minLength"

post/requestBody/data/payment/details/creditorAccount/number

Alterado - "minLength"

post/responses/201/data/debtorAccount/issuer

Adicionado - "minLength"

post/responses/201/data/debtorAccount/number

Alterado - "minLength"

post/responses/201/data/payment/details/creditorAccount/issuer

Adicionado - "minLength"

post/responses/201/data/payment/details/creditorAccount/number

Alterado - "minLength"

post/requestBody/data/payment/amount

Alterado - "description"

GET /consents{consentId}

**Campo**

**O que foi feito?**

consentId

Alterado pattern

payment/date

Alterada descrição

ibgeTownCode

Alterada descrição

links/self

Alterado pattern

meta

Alterada descrição em todos os responses

status code 200; 400; 401; 403; 404; 405; 406;429; 500; default

Removido totalPages

status code 200; 400; 401; 403; 404; 405; 406; 429; 500; default

Removido totalRecords

AdditionalProperties

Removida a explicitude do additionalProperties

status code 529

Adicionado status code

data/creditor/name

Alterado - "maxLength"

data/creditor/name

Alterado - "pattern"

data/debtorAccount/issuer

Alterado - "pattern"

data/debtorAccount/number

Alterado - "pattern"

data/payment/details/creditorAccount/issuer

Alterado - "pattern"

data/payment/details/creditorAccount/number

Alterado - "pattern"

get/responses/200/data/creditor/personType

Removido - "maxLength"

get/responses/200/data/debtorAccount/accountType

Removido - "maxLength"

get/responses/200/data/payment/date

Alterado - "description"

get/responses/200/data/payment/details/creditorAccount/accountType

Removido - "maxLength"

get/responses/200/data/payment/details/localInstrument

Removido - "maxLength"

get/responses/200/data/payment/date

Alterado mandatoriedade

get/responses/200/data/payment/properties

Adicionado - "schedule"

get/responses/200/data/payment/type

Removido - "maxLength"

get/responses/200/data/status

Removido - "maxLength"

get/responses/200/data/debtorAccount/issuer

Adicionado - "minLength"

get/responses/200/data/debtorAccount/number

Alterado - "minLength"

get/responses/200/data/payment/details/creditorAccount/issuer

Adicionado - "minLength"

get/responses/200/data/payment/details/creditorAccount/number

Alterado - "minLength"

POST /pix/payments

**Campo**

**O que foi feito?**

debtorAccount (response)

Adicionado objeto

ibgetowncode (request)

Alterada descrição

ibgetowncode (response)

Alterada descrição

transactionIdentification (request)

Alterado maxLength

transactionIdentification (request)

Alterado pattern

transactionIdentification (response)

Alterado maxLength

transactionIdentification (response)

Alterado pattern

consentId

Alterado pattern

links/self

Alterado pattern

detail (422)

Alterado pattern

title (422

Alterado pattern

meta

Alterada descrição em todos os responses

status code 201; 400; 401; 403; 404; 405; 406; 415; 422; 429; 500; default

Removido totalPages

status code 201; 400; 401; 403; 404; 405; 406; 415; 422; 429; 500; default

Removido totalRecords

debtorAccount (request)

Campo removido

transactionIdentification (request)

Alterado descrição

endToEndId (201)

Alterado descrição

endToEndId (201)

Alterado mandatoriedade

transactionIdentification (response - 201)

Alterado descrição

AdditionalProperties

Removida a explicitude do additionalProperties

security/OAuth2AuthorizationCode

Adicionado - "openid"

data/status (response) (201)

Alterado descrição

data/status (response) (201)

removido maxLength

Response error (422)

Alterada descrição

Adicionado ao code - "DETALHE\_PGTO\_INVALIDO"

Adicionado ao title - "Detalhe do pagamento inválido"

data/status/enum (response) (201)

Removido - "ACCC"

data/status/enum (response) (201)

Adicionado - "ACCP"

data/status/enum (response) (201)

Adicionado - "ACPD"

data/status/enum (response) (201)

Removido - "ACSP"

data/status/enum (response) (201)

Adicionado - "CANC"

data/status/enum (response) (201)

Removido - "PART"

data/status/enum (response) (201)

Adicionado - "PATC"

data/status/enum (response) (201)

Adicionado - "RCVD"

erros/items/detail (response) (422)

Adicionado - "DETALHE\_PGTO\_INVALIDO"

errors/items/detail (response) (422)

Alterado descrição

erros/items/code (response) (422)

Alterado descrição

errors/items/title (response) (422)

Alterado descrição

data/payment/amount (response) (201)

Alterada descrição

status code 529

Adicionado status code

data/payments/amount (request)

Alterado descrição

data/rejectionReason (response) (201)

Alterado descrição

data/rejectionReason (response) (201)

Convertido de enum para objeto

data/status

Alterado descrição

data/status/enum

Adicionado - "SCHD"

data/creditorAccount/issuer (response) (201)

Alterado - "pattern"

data/creditorAccount/number (response) (201)

Alterado - "pattern"

ata/creditorAccount/issuer (response) (201)

Alterado - "pattern"

data/creditorAccount/number (response) (201)

Alterado - "pattern"

data/debtorAccount/issuer (response) (201)

Alterado - "pattern"

data/debtorAccount/number (response) (201)

Alterado - "pattern"

post/requestBody/data/creditorAccount/accountType

Removido - "maxLength"

post/requestBody/data/endToEndId

Alterado - "description"

post/requestBody/data/localInstrument

Removido - "maxLength"

post/responses/201/data/creditorAccount/accountType

Removido - "maxLength"

post/responses/201/data/debtorAccount/accountType

Removido - "maxLength"

post/responses/201/data/localInstrument

Removido - "maxLength"

post/responses/201/data/rejectionReason/properties

Alterado mandatoriedade

post/responses/201/data/rejectionReason/properties

Alterado mandatoriedade

post/responses/201/data/rejectionReason/properties

Removido - "status"

post/responses/422/errors/items/code

Alterado - "description"

post/responses/422/errors/items/code

Removido - "maxLength"

post/responses/422/errors/items/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

post/responses/422/errors/items/code/enum

Removido - "DETALHE\_PGTO\_INVALIDO"

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

post/responses/422/errors/items/code/enum

Adicionado - "PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"

post/responses/422/errors/items/code/enum

Removido - "PAGAMENTO\_DIVERGENTE\_DO\_CONSENTIMENTO"

post/responses/422/errors/items/code/enum

Adicionado - "PAGAMENTO\_RECUSADO\_DETENTORA"

post/responses/422/errors/items/code/enum

Adicionado - "PAGAMENTO\_RECUSADO\_SPI"

post/responses/422/errors/items/detail

Alterado - "description"

post/responses/422/errors/items/title

Alterado - "description"

post/requestBody/data/creditorAccount/issuer

Adicionado - "minLength"

post/requestBody/data/creditorAccount/number

Alterado - "minLength"

post/responses/201/data/creditorAccount/issuer

Adicionado - "minLength"

post/responses/201/data/creditorAccount/number

Alterado - "minLength"

post/responses/201/data/debtorAccount/issuer

Adicionado - "minLength"

post/responses/201/data/debtorAccount/number

Alterado - "minLength"

GET /pix/payments/{paymentId}

**Campo**

**O que foi feito?**

consentId

Alterado pattern

transactionIdentification

Alterado maxLength

transactionIdentification

Alterado pattern

ibgetowncode

Alterada descrição

debtorAccount

Adicionado objeto

meta

Alterada descrição em todos os responses

status code 200; 400; 401; 403; 404; 405; 406;429; 500; default

Removido totalPages

status code 200; 400; 401; 403; 404; 405; 406; 429; 500; default

Removido totalRecords

links/self

Alterado pattern

endToEndId

Alterado descrição

endToEndId

Alterado mandatoriedade

transactionIdentification

Alterado descrição

AdditionalProperties

Removida a explicitude do additionalProperties

security/OAuth2AuthorizationCode

Adicionado - "openid"

data/rejectionReason

Alterado descrição

data/rejectionReason/enum

Adicionado - "DETALHE\_PGTO\_INVALIDO"

data/rejectionReason/enum

Adicionado - "NAO\_INFORMADO"

data/status

Alterado descrição

data/status

Removido maxLength

data/status/enum

Removido - "ACCC"

data/status/enum

Adicionado - "ACCP"

data/status/enum

Adicionado - "ACPD"

data/status/enum

Removido - "ACSP"

data/status/enum

Adicionado - "CANC"

data/status/enum

Removido - "PART"

data/status/enum

Adicionado - "PATC"

data/status/enum

Adicionado - "RCVD"

data/rejectionReason/enum

Adicionado - “DETALHE\_PGTO\_INVALIDO“

data/rejectionReason/enum

Adicionado - “NAO\_INFORMADO “

status code 529

Adicionado status code

data/payment/amount

Alterado descrição

data/rejectionReason

Convertido de enum para objeto

data/rejectionReason

Alterado descrição

data/status

Alterado descrição

data/status

Adicionado - "SCHD"

data/creditorAccount/issuer

Alterado - "pattern"

data/creditorAccount/number

Alterado - "pattern"

data/debtorAccount/issuer

Alterado - "pattern"

data/debtorAccount/number

Alterado - "pattern"

get/responses/200/data/creditorAccount/accountType

Removido - "maxLength"

get/responses/200/data/debtorAccount/accountType

Removido - "maxLength"

get/responses/200/data/localInstrument

Removido - "maxLength"

get/responses/200/data/rejectionReason/properties

Alterado mandatoriedade

get/responses/200/data/creditorAccount/issuer

Adicionado - "minLength"

get/responses/200/data/creditorAccount/number

Alterado - "minLength"

get/responses/200/data/debtorAccount/issuer

Adicionado - "minLength"

get/responses/200/data/debtorAccount/number

Alterado - "minLength"

get/responses/200/data/properties

Adicionado - "cancellation"

PATCH pix/payments/{paymentId}/

Adicionado novo endpoint
