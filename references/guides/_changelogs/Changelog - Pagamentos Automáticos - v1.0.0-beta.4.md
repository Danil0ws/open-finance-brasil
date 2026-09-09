# Changelog - Pagamentos Automáticos - v1.0.0-beta.4

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

POST /recurring-consents

**Campo**

**O que foi feito?**

post/requestBody/data/expirationDateTime

Mandatoriedade

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/amount

description

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/transactionLimit

description

post/responses/201/data/expirationDateTime

Mandatoriedade

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/amount

description

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/transactionLimit

description

OAuth2ClientCredentials

padrão dos scopes

GET /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

get/responses/200/data/properties

Mandatoriedade

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/amount

description

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/transactionLimit

description

OAuth2ClientCredentials

padrão dos scopes

PATCH /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

patch/responses/200/data/properties

Mandatoriedade

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/amount

description

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/transactionLimit

description

OAuth2ClientCredentials

padrão dos scopes

post/sumarry

alterado sumarry

POST /pix/recurring-payments

**Campo**

**O que foi feito?**

OAuth2AuthorizationCode

padrão dos scopes

GET /pix/recurring-payments

**Campo**

**O que foi feito?**

OAuth2ClientCredentials

padrão dos scopes

GET /pix/recurring-payments/{recurringPaymentId}

**Campo**

**O que foi feito?**

OAuth2ClientCredentials

padrão dos scopes

PATCH pix/recurring-payments/{recurringPaymentId}/

**Campo**

**O que foi feito?**

OAuth2ClientCredentials

padrão dos scopes
