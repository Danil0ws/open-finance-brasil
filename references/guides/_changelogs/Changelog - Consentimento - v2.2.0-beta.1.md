# Changelog - Consentimento - v2.2.0-beta.1

POST /consents

**Campo**

**O que foi feito?**

post/requestBody/data/expirationDateTime

description

post/responses/201/data/expirationDateTime

description

GET /consents/{consentId}

**Campo**

**O que foi feito?**

get/responses/200/data/expirationDateTime

description

DELETE /consents/{consentId}

**Campo**

**O que foi feito?**

GET /consents/{consentId}/extends

**Campo**

**O que foi feito?**

criação do endpoint

POST /consents/{consentId}/extends

**Campo**

**O que foi feito?**

criação do endpoint

post/responses/422/errors/items/code

description

post/responses/422/errors/items/code

example

post/responses/422/errors/items/code/enum

Adicionado - "DEPENDE\_MULTIPLA\_ALCADA"

post/responses/422/errors/items/code/enum

Removido - "DEPENDE\_MULTIPLA\_ALCADA\_PF"

post/responses/422/errors/items/code/enum

Removido - "DEPENDE\_MULTIPLA\_ALCADA\_PJ"
