# Changelog - Pagamentos Automáticos - v1.0.0-beta.5

**A implementação e certificação do Pix Automático está pausada no momento. O produto Transferência Inteligentes (Sweeping Accounts) continua disponível para implementação e certificação.**

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

Alterado x-fapi-interaction-id

Alterado - descrição

POST /recurring-consents

**Campo**

**O que foi feito?**

post/requestBody/data/recurringConfiguration/sweeping/amount

Alterado - nome do campo.

post/responses/201/data/recurringConfiguration/sweeping/amount

Alterado - nome do campo.

post/requestBody/data/debtorAccount/issuer

Alterado - Mandatoriedade

post/responses/201/data/debtorAccount/issuer

Alterado - Mandatoriedade

post/responses/201/data/debtorAccount/ibgeTownCode

Alterado - Mandatoriedade

post/requestBody/data/properties

Mandatoriedade

post/requestBody/data/recurringConfiguration/automatic

Mandatoriedade

post/requestBody/data/recurringConfiguration/sweeping

Mandatoriedade

post/requestBody/data/recurringConfiguration/vrp

Mandatoriedade

post/responses/201/data/properties

Mandatoriedade

post/responses/201/data/recurringConfiguration/automatic

Mandatoriedade

post/responses/201/data/recurringConfiguration/sweeping

Mandatoriedade

post/responses/201/data/recurringConfiguration/vrp

Mandatoriedade

GET /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

get/responses/200/data/recurringConfiguration/sweeping/amount

Alterado - nome do campo.

get/responses/200/data/debtorAccount/issuer

Alterado - Mandatoriedade

get/responses/200/data/debtorAccount/ibgeTownCode

Alterado - Mandatoriedade

get/responses/200/data/riskSignals

Alterado - Restrição

get/responses/200/data/properties

Mandatoriedade

get/responses/200/data/recurringConfiguration/automatic

Mandatoriedade

get/responses/200/data/recurringConfiguration/sweeping

Mandatoriedade

get/responses/200/data/recurringConfiguration/vrp

Mandatoriedade

PATCH /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

Patch/responses/200/data/recurringConfiguration/sweeping/amount

Alterado - nome do campo.

Patch/responses/200/data/debtorAccount/issuer

Alterado - Mandatoriedade

Patch/responses/200/data/debtorAccount/ibgeTownCode

Alterado - Mandatoriedade

Patch/responses/200/data/riskSignals

Alterado - Restrição

Patch/requestBody/data/riskSignals

Alterado - Restrição

patch/responses/200/data/properties

Mandatoriedade

patch/responses/200/data/recurringConfiguration/automatic

Mandatoriedade

patch/responses/200/data/recurringConfiguration/sweeping

Mandatoriedade

patch/responses/200/data/recurringConfiguration/vrp

Mandatoriedade

POST /pix/recurring-payments

**Campo**

**O que foi feito?**

Request/data

adicionado - objeto document

Response/201/data

adicionado - objeto document

post/requestBody/data/riskSignals/automatic/pixKeyRegistrationDateTime

description

post/requestBody/data/riskSignals/automatic/pixKeyRegistrationDateTime

Mandatoriedade

GET /pix/recurring-payments

**Campo**

**O que foi feito?**

get/responses/data/

adicionado - objeto document

GET /pix/recurring-payments/{recurringPaymentId}

**Campo**

**O que foi feito?**

get/responses/data/

adicionado - objeto document

PATCH pix/recurring-payments/{recurringPaymentId}/

**Campo**

**O que foi feito?**

Response/200/data

adicionado - objeto document
