# Changelog - Pagamentos - v3.0.0-beta.2

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

description

Alterado - "description"

description

Alterado - "description"

servers/0

Alterado - "url"

servers/1

Alterado - "url"

POST /consents

**Campo**

**O que foi feito?**

post/requestBody/data/debtorAccount/accountType

Alterado - "description"

post/requestBody/data/debtorAccount/accountType/enum

Removido - "SLRY"

post/requestBody/data/debtorAccount/issuer

Alterado - "description"

post/requestBody/data/payment/details/creditorAccount/accountType

Alterado - "description"

post/requestBody/data/payment/details/creditorAccount/accountType/enum

Removido - "SLRY"

post/requestBody/data/payment/details/creditorAccount/issuer

Alterado - "description"

post/responses/201/data/debtorAccount/accountType

Alterado - "description"

post/responses/201/data/debtorAccount/accountType/enum

Removido - "SLRY"

post/responses/201/data/debtorAccount/issuer

Alterado - "description"

post/responses/201/data/payment/details/creditorAccount/accountType

Alterado - "description"

post/responses/201/data/payment/details/creditorAccount/accountType/enum

Removido - "SLRY"

post/responses/201/data/payment/details/creditorAccount/issuer

Alterado - "description"

GET /consents/{consentId}

**Campo**

**O que foi feito?**

get/responses/200/data/debtorAccount/accountType

Alterado - "description"

get/responses/200/data/debtorAccount/accountType/enum

Removido - "SLRY"

get/responses/200/data/debtorAccount/issuer

Alterado - "description"

get/responses/200/data/payment/details/creditorAccount/accountType

Alterado - "description"

get/responses/200/data/payment/details/creditorAccount/accountType/enum

Removido - "SLRY"

get/responses/200/data/payment/details/creditorAccount/issuer

Alterado - "description"

get/responses/200/data/rejectionReason/detail

Alterado - "description"

POST /pix/payments

**Campo**

**O que foi feito?**

post/requestBody/data/authorisationFlow

Alterado - "description"

post/requestBody/data/authorisationFlow/enum

Adicionado - "FIDO\_FLOW"

post/requestBody/data/creditorAccount/issuer

Alterado - "description"

post/responses/201/data/authorisationFlow

Alterado - "description"

post/responses/201/data/authorisationFlow/enum

Adicionado - "FIDO\_FLOW"

post/responses/201/data/creditorAccount/issuer

Alterado - "description"

post/responses/201/data/debtorAccount/issuer

Alterado - "description"

GET /pix/payments/{paymentId}

**Campo**

**O que foi feito?**

get/responses/200/data/creditorAccount/issuer

Alterado - "description"

get/responses/200/data/debtorAccount/issuer

Alterado - "description"

get/responses/200/data/authorisationFlow

Alterado - "description"

get/responses/200/data/authorisationFlow/enum

Adicionado - "FIDO\_FLOW"

PATCH pix/payments/{paymentId}/

**Campo**

**O que foi feito?**

patch/responses/200/data/authorisationFlow

Alterado - "description"

patch/responses/200/data/authorisationFlow/enum

Adicionado - "FIDO\_FLOW"

patch/responses/200/data/creditorAccount/accountType

Alterado - "description"

patch/responses/200/data/creditorAccount/accountType/enum

Removido - "SLRY"

patch/responses/200/data/creditorAccount/issuer

Alterado - "description"

patch/responses/200/data/debtorAccount/accountType

Alterado - "description"

patch/responses/200/data/debtorAccount/accountType/enum

Removido - "SLRY"

patch/responses/200/data/debtorAccount/issuer

Alterado - "description"
