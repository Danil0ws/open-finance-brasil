# Changelog - [DC] Consentimento - v3.0.0-beta.1

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi feito?**

Description

Alterado

Description

Alterado

Description

Alterado

Description

Alterado

Description

Alterado

Description

Alterado

tags/0

description

POST /consents

**Campo**

**O que foi feito?**

post/parameters/x-fapi-interaction-id

description

post/parameters/x-fapi-interaction-id

Mandatoriedade

post/requestBody/data/businessEntity

description

post/requestBody/data/loggedUser

description

post/requestBody/data/permissions/items/enum

Adicionado - "EXCHANGES\_READ"

post/responses/201/data/permissions/items/enum

Adicionado - "EXCHANGES\_READ"

post/responses/400

Removido - totalPages e totalRecords

post/responses/401

Removido - totalPages e totalRecords

post/responses/403

Removido - totalPages e totalRecords

post/responses/404

Removido - totalPages e totalRecords

post/responses/405

Removido - totalPages e totalRecords

post/responses/406

Removido - totalPages e totalRecords

post/responses/415

Removido - totalPages e totalRecords

post/responses/422

Removido - totalPages e totalRecords

post/responses/429

Removido - totalPages e totalRecords

post/responses/500

Removido - totalPages e totalRecords

post/responses/504

Removido - totalPages e totalRecords

post/responses/529

Removido - totalPages e totalRecords

post/requestBody/data/expirationDateTime

Alterado - Madatoriedade

post/requestBody/data/expirationDateTime

Alterado - Descrição

post/responses/201/data/expirationDateTime

Alterado - Madatoriedade

post/responses/201/data/expirationDateTime

Alterado - Descrição

post/requestBody/data/expirationDateTime

Adicionado - Pattern

post/responses/201/data/creationDateTime

Adicionado - Pattern

post/responses/201/data/creationDateTime

Adicionado - Pattern

post/responses/201/data/expirationDateTime

Adicionado - Pattern

post/responses/201/meta/properties

Removido - "totalPages"

post/responses/201/meta/properties

Removido - "totalRecords"

post/requestBody/data/permissions​

Adicionado - x-regulatory-required

post/requestBody/data/expirationDateTime​

Adicionado - x-regulatory-required

post/requestBody/data/loggedUser/document/identification​

Adicionado - x-regulatory-required

post/requestBody/data/businessEntity/document/identification​

Adicionado - x-regulatory-required

post/responses/201/data/permissions​

Adicionado - x-regulatory-required

post/responses/201/data/expirationDateTime​

Adicionado - x-regulatory-required

GET /consents/{consentId}

**Campo**

**O que foi feito?**

/data/rejection/reason/additionalInformation

Pattern

get/parameters/x-fapi-interaction-id

description

get/parameters/x-fapi-interaction-id

Mandatoriedade

get/responses/200/data/permissions/items/enum

Adicionado - "EXCHANGES\_READ"

get/responses/400

Removido - totalPages e totalRecords

get/responses/401

Removido - totalPages e totalRecords

get/responses/403

Removido - totalPages e totalRecords

get/responses/404

Removido - totalPages e totalRecords

get/responses/405

Removido - totalPages e totalRecords

get/responses/406

Removido - totalPages e totalRecords

get/responses/429

Removido - totalPages e totalRecords

get/responses/500

Removido - totalPages e totalRecords

get/responses/504

Removido - totalPages e totalRecords

get/responses/529

Removido - totalPages e totalRecords

get/responses/200/data/expirationDateTime

Alterado - Madatoriedade

get/responses/200/data/expirationDateTime

Alterado - Descrição

get/responses/200/data/creationDateTime

Adicionado - Pattern

get/responses/200/data/statusUpdateDateTime

Adicionado - Pattern

get/responses/200/data/expirationDateTime

Adicionado - Pattern

get/responses/200/meta/properties

Removido - "totalPages"

get/responses/200/meta/properties

Removido - "totalRecords"

get/responses/200/data/permissions​

Adicionado - x-regulatory-required

get/responses/200/data/expirationDateTime​

Adicionado - x-regulatory-required

DELETE /consents/{consentId}

**Campo**

**O que foi feito?**

Erros

Adicionado - 422

delete/parameters/x-fapi-interaction-id

description

delete/parameters/x-fapi-interaction-id

Mandatoriedade

delete/responses/400

Removido - totalPages e totalRecords

delete/responses/401

Removido - totalPages e totalRecords

delete/responses/403

Removido - totalPages e totalRecords

delete/responses/404

Removido - totalPages e totalRecords

delete/responses/405

Removido - totalPages e totalRecords

delete/responses/406

Removido - totalPages e totalRecords

delete/responses/422

Removido - totalPages e totalRecords

delete/responses/429

Removido - totalPages e totalRecords

delete/responses/500

Removido - totalPages e totalRecords

delete/responses/504

Removido - totalPages e totalRecords

delete/responses/529

Removido - totalPages e totalRecords

GET /consents/{consentId}/extensions

**Campo**

**O que foi feito?**

get/responses/200/data/items/expirationDateTime

description

get

description

get/responses/200/data/items/properties

Adicionado - "previousExpirationDateTime"

get/responses/200/data/items/properties

Adicionado - "xCustomerUserAgent"

get/responses/200/data/items/properties

Adicionado - "xFapiCustomerIpAddress"

get/responses/200/meta/properties

Removido - "totalPages"

get/responses/200/meta/properties

Removido - "totalRecords"

url

alterado para - “/consents/{consentId}/extensions“

POST /consents/{consentId}/extends

**Campo**

**O que foi feito?**

post

description

post/responses/422//errors/items/code/enum

Removido - "REFRESH\_TOKEN\_JWT"

post/responses/201/meta/properties

Removido - "totalPages"

post/responses/201/meta/properties

Removido - "totalRecords"

post/requestBody/data/expirationDateTime

description

post/requestBody/data/properties

Mandatoriedade

post

description
