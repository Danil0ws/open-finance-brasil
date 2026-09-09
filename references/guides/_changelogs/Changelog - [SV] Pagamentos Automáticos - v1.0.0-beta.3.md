# Changelog - [SV] Pagamentos Automáticos - v1.0.0-beta.3

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

POST /recurring-consents

**Campo**

**O que foi feito?**

post/responses/201/data/debtorAccount/

removido - overdraftLimit

post/responses/201/data/debtorAccount/ibgeTownCode

description

post/responses/201/data/properties

Removido - "ibgeTownCode"

GET /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

get/200/data/debtorAccount/

removido - overdraftLimit

get/responses/200/data/debtorAccount/ibgeTownCode

description

get/responses/200/data/properties

Removido - "ibgeTownCode"

PATCH /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

patch/requestBody/data/ConsentRejection/

Adicionado - creditors

patch/requestBody/data/ConsentRejection/

Adicionado - startDateTime

patch/requestBody/data/ConsentRejection/

Adicionado - expirationDateTime

patch/requestBody/data/ConsentRejection/

Adicionado - automatic

patch/requestBody/data/ConsentRevocation/

Adicionado - creditors

patch/requestBody/data/ConsentRevocation/

Adicionado - startDateTime

patch/requestBody/data/ConsentRevocation/

Adicionado - expirationDateTime

patch/requestBody/data/ConsentRevocation/

Adicionado - automatic

patch/response/201/data/debtorAccount/

removido - overdraftLimit

patch

description

patch/requestBody/data/oneOf/0/status

Mandatoriedade

patch/requestBody/data/oneOf/1/status

Mandatoriedade

patch/responses/200/data/debtorAccount/ibgeTownCode

description

patch/responses/200/data/properties

Removido - "ibgeTownCode"

POST /pix/recurring-payments

**Campo**

**O que foi feito?**

post/requestBody/data/properties

Mandatoriedade

post/requestBody/data/recurringConsentId

description

post/responses/201/data/properties

Mandatoriedade

post/responses/201/data/recurringConsentId

description

GET /pix/recurring-payments

**Campo**

**O que foi feito?**

get/responses/200/data/items/properties

Mandatoriedade

get/responses/200/data/items/recurringConsentId

description

GET /pix/recurring-payments/{recurringPaymentId}

**Campo**

**O que foi feito?**

get/responses/200/data/properties

Mandatoriedade

get/responses/200/data/recurringConsentId

description

PATCH pix/recurring-payments/{recurringPaymentId}/

**Campo**

**O que foi feito?**

patch/

Alterado - Summary

patch/responses/200/data/properties

Mandatoriedade

patch/responses/200/data/recurringConsentId

description
