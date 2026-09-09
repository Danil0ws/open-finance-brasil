# Changelog - Pagamentos - v3.0.0-beta.1

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

Orientações

Alterado texto relativo ao campo PAGTO

description

Alterado - "description"

POST /consents

**Campo**

**O que foi feito?**

post/parameters/x-fapi-interaction-id

Mandatoriedade - “obrigatório“

post/requestBody/data/creditor/name

Alterado - "pattern"

post/requestBody/data/debtorAccount/accountType

Alterado - "description"

post/requestBody/data/payment/details/creditorAccount/accountType

Alterado - "description"

post/responses/201/data/creditor/name

Alterado - "pattern"

post/responses/201/data/debtorAccount

Alterado - "description"

post/responses/201/data/debtorAccount/accountType

Alterado - "description"

post/responses/201/data/payment/details/creditorAccount/accountType

Alterado - "description"

post/responses/400

Alterado - "description"

post/responses/422

Alterado - "description"

post/responses/422/errors/items/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

post/responses/422/errors/items/code/enum

Removido - "DETALHE\_PGTO\_INVALIDO"

GET /consents/{consentId}

**Campo**

**O que foi feito?**

get/parameters/x-fapi-interaction-id

Mandatoriedade - “obrigatório“

get/responses/200/data/creditor/name

Alterado - "pattern"

get/responses/200/data/debtorAccount

Alterado - "description"

get/responses/200/data/debtorAccount/accountType

Alterado - "description"

get/responses/200/data/payment/details/creditorAccount/accountType

Alterado - "description"

get/responses/200/data/properties

Adicionado - "rejectionReason"

POST /pix/payments

**Campo**

**O que foi feito?**

post/parameters/x-fapi-interaction-id

Mandatoriedade - “obrigatório“

post/requestBody/data/creditorAccount/accountType

Alterado - "description"

post/requestBody/data/creditorAccount/accountType/enum

Removido - "SLRY"

post/requestBody/data/properties

Adicionado - "authorisationFlow"

post/responses/201/data/creditorAccount/accountType

Alterado - "description"

post/responses/201/data/creditorAccount/accountType/enum

Removido - "SLRY"

post/responses/201/data/debtorAccount/accountType

Alterado - "description"

post/responses/201/data/debtorAccount/accountType/enum

Removido - "SLRY"

post/responses/201/data/properties

Adicionado - "authorisationFlow"

post/responses/201/data/rejectionReason/code

Alterado - "description"

post/responses/201/data/rejectionReason/code/enum

Adicionado - "CONTAS\_ORIGEM\_DESTINO\_IGUAIS"

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_DETENTORA"

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_DICT"

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_ICP"

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR"

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_SPI"

post/responses/400

Alterado - "description"

post/responses/422

Alterado - "description"

post/responses/422/errors/items/code

Alterado - "description"

post/responses/422/errors/items/code/enum

Removido - "BENEFICIARIO\_INCOMPATIVEL"

post/responses/422/errors/items/code/enum

Removido - "JANELA\_OPER\_INVALIDA"

post/responses/422/errors/items/code/enum

Removido - "VALOR\_INCOMPATIVEL"

get/responses/200/data/rejectionReason/code

Alterado - "description"

GET /pix/payments/{paymentId}

**Campo**

**O que foi feito?**

get/parameters/x-fapi-interaction-id

Mandatoriedade - “obrigatório“

get/responses/200/data/creditorAccount/accountType

Alterado - "description"

get/responses/200/data/creditorAccount/accountType/enum

Removido - "SLRY"

get/responses/200/data/debtorAccount/accountType

Alterado - "description"

get/responses/200/data/debtorAccount/accountType/enum

Removido - "SLRY"

get/responses/200/data/properties

Adicionado - "authorisationFlow"

get/responses/200/data/rejectionReason/code

Alterado - "description"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "CONTAS\_ORIGEM\_DESTINO\_IGUAIS"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_DETENTORA"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_DICT"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_ICP"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_SPI"

get/security/0

Alteração os security definitions

get/responses/200/data/rejectionReason/code

Alterado - "description"

PATCH pix/payments/{paymentId}/

**Campo**

**O que foi feito?**

patch

Alterado - "description"

patch/parameters/x-fapi-interaction-id

Mandatoriedade - “obrigatório“

patch/responses/200/data/properties

Adicionado - "authorisationFlow"

patch/responses/200/data/rejectionReason/code

Alterado - "description"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "CONTAS\_ORIGEM\_DESTINO\_IGUAIS"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_DETENTORA"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_DICT"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_ICP"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR"

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_INFRAESTRUTURA\_SPI"

patch/responses/422

Alterado - "description"

patch/responses/422/errors/items/code

Alterado - "description"

patch/responses/422/errors/items/code

Alterado - "example”

patch/responses/422/errors/items/code/enum

Removido - "BENEFICIARIO\_INCOMPATIVEL"

patch/responses/422/errors/items/code/enum

Removido - "COBRANCA\_INVALIDA"

patch/responses/422/errors/items/code/enum

Removido - "CONSENTIMENTO\_INVALIDO"

patch/responses/422/errors/items/code/enum

Removido - "DETALHE\_PAGAMENTO\_INVALIDO"

patch/responses/422/errors/items/code/enum

Removido - "ERRO\_IDEMPOTENCIA"

patch/responses/422/errors/items/code/enum

Removido - "JANELA\_OPER\_INVALIDA"

patch/responses/422/errors/items/code/enum

Removido - "NAO\_INFORMADO"

patch/responses/422/errors/items/code/enum

Removido - "PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"

patch/responses/422/errors/items/code/enum

Adicionado - "PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO"

patch/responses/422/errors/items/code/enum

Removido - "PAGAMENTO\_RECUSADO\_DETENTORA"

patch/responses/422/errors/items/code/enum

Removido - "PAGAMENTO\_RECUSADO\_SPI"

patch/responses/422/errors/items/code/enum

Removido - "PARAMETRO\_INVALIDO"

patch/responses/422/errors/items/code/enum

Removido - "PARAMETRO\_NAO\_INFORMADO"

patch/responses/422/errors/items/code/enum

Removido - "SALDO\_INSUFICIENTE"

patch/responses/422/errors/items/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

patch/responses/422/errors/items/code/enum

Removido - "VALOR\_INCOMPATIVEL"

patch/responses/422/errors/items/code/enum

Removido - "VALOR\_INVALIDO"

patch/responses/422/errors/items/detail

Alterado - "description"

patch/responses/422/errors/items/detail

Alterado - "example”

patch/responses/422/errors/items/title

Alterado - "description"

patch/responses/422/errors/items/title

Alterado - "example”

patch/responses/422/examples/Saldo insuficiente/value/errors/0

Alterado - "code”

patch/responses/422/examples/Saldo insuficiente/value/errors/0

Alterado - "detail”

patch/responses/422/examples/Saldo insuficiente/value/errors/0

Alterado - "title”

get/responses/200/data/rejectionReason/code

Alterado - "description"
