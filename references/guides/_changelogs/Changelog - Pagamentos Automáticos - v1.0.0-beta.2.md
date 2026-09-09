# Changelog - Pagamentos Automáticos - v1.0.0-beta.2

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

Descrição da API

Alterado - Header

Descrição da API

Alterado - Header

POST /recurring-consents

**Campo**

**O que foi feito?**

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/name

description

post/responses/201/data/recurringConfiguration/recurringConfiguration

Corrigido caminho

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/amount

Mandatoriedade

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/transactionLimit

Mandatoriedade

post/parameters/x-fapi-interaction-id

description

GET /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

data/recurringConfiguration/automatic/contractDebtor/name

Alterado - Descrição

get/responses/200/data/properties

Adicionado - "riskSignals"

get/responses/200/data/recurringConfiguration/recurringConfiguration

Corrigido caminho

get/parameters/x-fapi-auth-date

description

get/parameters/x-fapi-customer-ip-address

description

PATCH /recurring-consents/{recurringConsentId}

**Campo**

**O que foi feito?**

response/data/recurringConfiguration/automatic/contractDebtor/name

Alterado - Descrição

patch/requestBody/data/oneOf/0/properties

Adicionado - "riskSignals"

patch/requestBody/data/oneOf/1/properties

Adicionado - "riskSignals"

patch/responses/200/data/properties

Adicionado - "riskSignals"

patch/responses/200/data/recurringConfiguration/recurringConfiguration

Corrigido caminho

patch/parameters/x-fapi-auth-date

description

patch/parameters/x-fapi-customer-ip-address

description

patch/parameters/x-fapi-interaction-id

description

POST /pix/recurring-payments

**Campo**

**O que foi feito?**

post/responses/422/errors/items/detail

description

GET /pix/recurring-payments

**Campo**

**O que foi feito?**

get/parameters/x-fapi-interaction-id

description

post/parameters/x-fapi-interaction-id

description

GET /pix/recurring-payments/{recurringPaymentId}

**Campo**

**O que foi feito?**

get/parameters/x-fapi-interaction-id

description

PATCH pix/recurring-payments/{recurringPaymentId}/

**Campo**

**O que foi feito?**

patch/parameters/x-fapi-interaction-id

description
