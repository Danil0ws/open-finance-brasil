# Changelog - [DC] Consentimento - v3.0.0-rc.1 - v2.2.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

tags/0

Alterado - "description"

Alteração

Operações para criação, consulta e revogação do consentimento dado pelo cliente.

Operações para criação, consulta, renovação e revogação do consentimento dado pelo cliente.

server/0

Alterado - "url"

Alteração

[https://api.banco.com.br/open-banking/consents/v2](https://api.banco.com.br/open-banking/consents/v2)

[https://api.banco.com.br/open-banking/consents/v3](https://api.banco.com.br/open-banking/consents/v3)

server/1

Alterado - "url"

Alteração

[https://apih.banco.com.br/open-banking/consents/v2](https://apih.banco.com.br/open-banking/consents/v2)

[https://apih.banco.com.br/open-banking/consents/v3](https://apih.banco.com.br/open-banking/consents/v3)

description

Alterado - "description"

Alteração

API que trata da criação, consulta e revogação de consentimentos para o Open Finance Brasil Dados cadastrais e transacionais - cus...

API que trata da criação, consulta, renovação e revogação de consentimentos para o Open Finance Brasil Dados cadastrais e transaci...

paths

Alterado - "/consents/{consentId}/extensions"

Alteração

/consents/{consentId}/extends

/consents/{consentId}/extensions

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

post/requestBody/data

Adicionado - "x-regulatory-required"

Adição

post/requestBody/data/businessEntity

Alterado - "description"

Alteração

Titular, pessoa jurídica a quem se referem os dados que são objeto de compartilhamento.

Titular, pessoa jurídica a quem se referem os dados que são objeto de compartilhamento. É obrigatório que o número do CNPJ utiliz...

post/requestBody/data/businessEntity/document

Adicionado - "x-regulatory-required"

Adição

post/requestBody/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. De preenchimento obrigatório, reflete a data limite de validade do consentimento. Uma strin...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

post/requestBody/data/expirationDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

post/requestBody/data/loggedUser

Alterado - "description"

Alteração

Usuário (pessoa natural) que encontra-se logado na instituição receptora e que iniciará o processo de consentimento para compartil...

Usuário (pessoa natural) que encontra-se logado na instituição receptora e que iniciará o processo de consentimento para compartil...

post/requestBody/data/loggedUser/document

Adicionado - "x-regulatory-required"

Adição

post/requestBody/data/permissions/items/enum

Adicionado - "EXCHANGES\_READ"

Adição

enum

post/requestBody/data/properties

Removido obrigatóriedade no campo "expirationDateTime"

Remoção

required

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data

Adicionado - "x-regulatory-required"

Adição

post/responses/201/data/creationDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. De preenchimento obrigatório, reflete a data limite de validade do consentimento. Uma strin...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

post/responses/201/data/expirationDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

post/responses/201/data/permissions/items/enum

Adicionado - "EXCHANGES\_READ"

Adição

enum

post/responses/201/data/properties

Removido obrigatóriedade no campo 'expirationDateTime'

Remoção

required

post/responses/201/data/statusUpdateDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduz...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

post/responses/201/headers/x-fapi-interaction-id

Alterado - "example"

Alteração

73cac523-d3ae-2289-b106-330a6218710d

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/201/links/properties

Removido - "first"

Remoção

post/responses/201/links/properties

Removido - "last"

Remoção

post/responses/201/links/properties

Removido - "next"

Remoção

post/responses/201/links/properties

Removido - "prev"

Remoção

post/responses/201/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/201/meta/properties

Removido - "totalPages"

Remoção

post/responses/201/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/201/meta/properties

Removido - "totalRecords"

Remoção

post/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/400//meta/properties

Removido - "totalPages"

Remoção

post/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/400//meta/properties

Removido - "totalRecords"

Remoção

post/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/401//meta/properties

Removido - "totalPages"

Remoção

post/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/401//meta/properties

Removido - "totalRecords"

Remoção

post/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/403//meta/properties

Removido - "totalPages"

Remoção

post/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/403//meta/properties

Removido - "totalRecords"

Remoção

post/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/404//meta/properties

Removido - "totalPages"

Remoção

post/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/404//meta/properties

Removido - "totalRecords"

Remoção

post/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/405//meta/properties

Removido - "totalPages"

Remoção

post/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/405//meta/properties

Removido - "totalRecords"

Remoção

post/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/406//meta/properties

Removido - "totalPages"

Remoção

post/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/406//meta/properties

Removido - "totalRecords"

Remoção

post/responses/415//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/415//meta/properties

Removido - "totalPages"

Remoção

post/responses/415//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/415//meta/properties

Removido - "totalRecords"

Remoção

post/responses/422//errors/items/code

Alterado - "description"

Alteração

Código de erro específico do endpoint

-   SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES - INFORMACOES\_PJ\_NAO\_INFORMADAS - PERMISSOES\_PJ\_INCORRETAS - PERMISSAO\_PF\_PJ\_EM\_CONJUNTO - C...
    

post/responses/422//errors/items/code

Adicionado - "enum"

Adição

post/responses/422//errors/items/code

Adicionado - "example"

Adição

SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES

post/responses/422//errors/items/code

Removido - "maxLength"

Remoção

255

post/responses/422//errors/items/code

Removido - "pattern"

Remoção

\[\\w\\W\\s\]\*

post/responses/422//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/422//meta/properties

Removido - "totalPages"

Remoção

post/responses/422//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/422//meta/properties

Removido - "totalRecords"

Remoção

post/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/429//meta/properties

Removido - "totalPages"

Remoção

post/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/429//meta/properties

Removido - "totalRecords"

Remoção

post/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/500//meta/properties

Removido - "totalPages"

Remoção

post/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/500//meta/properties

Removido - "totalRecords"

Remoção

post/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/504//meta/properties

Removido - "totalPages"

Remoção

post/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/504//meta/properties

Removido - "totalRecords"

Remoção

post/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/529//meta/properties

Removido - "totalPages"

Remoção

post/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/529//meta/properties

Removido - "totalRecords"

Remoção

post/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/default/meta/properties

Removido - "totalPages"

Remoção

post/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/default/meta/properties

Removido - "totalRecords"

Remoção

## GET /consents/{consentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/creationDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. De preenchimento obrigatório, reflete a data limite de validade do consentimento. Uma strin...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

get/responses/200/data/expirationDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/data/permissions/items/enum

Adicionado - "EXCHANGES\_READ"

Adição

enum

get/responses/200/data/properties

Removido obrigatóriedade no campo "expirationDateTime"

Remoção

required

get/responses/200/data/rejection/reason/additionalInformation

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Define o código da razão pela qual o consentimento foi rejeitado. - CONSENT\_EXPIRED – consentimento que ultrapassou o tempo limit...

Define o código da razão pela qual o consentimento foi rejeitado. - CONSENT\_EXPIRED – consentimento que ultrapassou o tempo limit...

get/responses/200/data/statusUpdateDateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduz...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

get/responses/200/headers/x-fapi-interaction-id

Alterado - "example"

Alteração

92cac523-d3ae-2289-b106-330a6218710d

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/links/properties

Removido - "first"

Remoção

get/responses/200/links/properties

Removido - "last"

Remoção

get/responses/200/links/properties

Removido - "next"

Remoção

get/responses/200/links/properties

Removido - "prev"

Remoção

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400//meta/properties

Removido - "totalPages"

Remoção

get/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400//meta/properties

Removido - "totalRecords"

Remoção

get/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401//meta/properties

Removido - "totalPages"

Remoção

get/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401//meta/properties

Removido - "totalRecords"

Remoção

get/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403//meta/properties

Removido - "totalPages"

Remoção

get/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403//meta/properties

Removido - "totalRecords"

Remoção

get/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404//meta/properties

Removido - "totalPages"

Remoção

get/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404//meta/properties

Removido - "totalRecords"

Remoção

get/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405//meta/properties

Removido - "totalPages"

Remoção

get/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405//meta/properties

Removido - "totalRecords"

Remoção

get/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406//meta/properties

Removido - "totalPages"

Remoção

get/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406//meta/properties

Removido - "totalRecords"

Remoção

get/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429//meta/properties

Removido - "totalPages"

Remoção

get/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429//meta/properties

Removido - "totalRecords"

Remoção

get/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500//meta/properties

Removido - "totalPages"

Remoção

get/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500//meta/properties

Removido - "totalRecords"

Remoção

get/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504//meta/properties

Removido - "totalPages"

Remoção

get/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504//meta/properties

Removido - "totalRecords"

Remoção

get/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529//meta/properties

Removido - "totalPages"

Remoção

get/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529//meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

## DELETE /consents/{consentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

delete/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

delete/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

delete/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

delete/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

delete/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

delete/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

delete/responses

Adicionado - "422"

Adição

delete/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduz...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

delete/responses/204/headers/x-fapi-interaction-id

Alterado - "example"

Alteração

85bac523-d3ae-2289-b106-330a6218710d

d78fc4e5-37ca-4da3-adf2-9b082bf92280

delete/responses/204/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

delete/responses/204/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

delete/responses/204/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

delete/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/400//meta/properties

Removido - "totalPages"

Remoção

delete/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/400//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/401//meta/properties

Removido - "totalPages"

Remoção

delete/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/401//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/403//meta/properties

Removido - "totalPages"

Remoção

delete/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/403//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/404//meta/properties

Removido - "totalPages"

Remoção

delete/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/404//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/405//meta/properties

Removido - "totalPages"

Remoção

delete/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/405//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/406//meta/properties

Removido - "totalPages"

Remoção

delete/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/406//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/429//meta/properties

Removido - "totalPages"

Remoção

delete/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/429//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/500//meta/properties

Removido - "totalPages"

Remoção

delete/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/500//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/504//meta/properties

Removido - "totalPages"

Remoção

delete/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/504//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/529//meta/properties

Removido - "totalPages"

Remoção

delete/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/529//meta/properties

Removido - "totalRecords"

Remoção

delete/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

delete/responses/default/meta/properties

Removido - "totalPages"

Remoção

delete/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

delete/responses/default/meta/properties

Removido - "totalRecords"

Remoção

## GET /consents/{consentId}/extensions

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter detalhes de extensões consentimento identificado por consentId.

Método para obter histórico de extensões de consentimento identificado por consentId. IMPORTANTE: A lista do payload de resposta ...

get/parameters

Adicionado - "page"

Adição

get/parameters

Adicionado - "page-size"

Adição

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e ...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. De preenchimento obrigatório, reflete a data limite de validade do consentimento. Uma strin...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

get/responses/200/data/items/properties

Adicionado - "previousExpirationDateTime"

Adição

get/responses/200/data/items/properties

Adicionado - "xCustomerUserAgent"

Adição

get/responses/200/data/items/properties

Adicionado - "xFapiCustomerIpAddress"

Adição

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduz...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

get/responses/200/headers/x-fapi-interaction-id

Alterado - "example"

Alteração

92cac523-d3ae-2289-b106-330a6218710d

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400//meta/properties

Removido - "totalPages"

Remoção

get/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400//meta/properties

Removido - "totalRecords"

Remoção

get/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401//meta/properties

Removido - "totalPages"

Remoção

get/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401//meta/properties

Removido - "totalRecords"

Remoção

get/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403//meta/properties

Removido - "totalPages"

Remoção

get/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403//meta/properties

Removido - "totalRecords"

Remoção

get/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404//meta/properties

Removido - "totalPages"

Remoção

get/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404//meta/properties

Removido - "totalRecords"

Remoção

get/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405//meta/properties

Removido - "totalPages"

Remoção

get/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405//meta/properties

Removido - "totalRecords"

Remoção

get/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406//meta/properties

Removido - "totalPages"

Remoção

get/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406//meta/properties

Removido - "totalRecords"

Remoção

get/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429//meta/properties

Removido - "totalPages"

Remoção

get/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429//meta/properties

Removido - "totalRecords"

Remoção

get/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500//meta/properties

Removido - "totalPages"

Remoção

get/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500//meta/properties

Removido - "totalRecords"

Remoção

get/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504//meta/properties

Removido - "totalPages"

Remoção

get/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504//meta/properties

Removido - "totalRecords"

Remoção

get/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529//meta/properties

Removido - "totalPages"

Remoção

get/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529//meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

## POST /consents/{consentId}/extends

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post

Alterado - "description"

Alteração

Método para renovar consentimento identificado por consentId, exceto casos com múltiplas alçadas. Nos casos de múltiplas alçadas, ...

Método utilizado para renovação de consentimento do cliente. O consentimento só pode ser renovado caso esteja ativo (status AUTHOR...

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e ...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/requestBody/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. De preenchimento obrigatório, reflete a data limite de validade do consentimento. Uma strin...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

post/requestBody/data/properties

Removido obrigatóriedade no campo 'expirationDateTime'

Remoção

required

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduz...

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

post/responses/201/headers/x-fapi-interaction-id

Alterado - "example"

Alteração

73cac523-d3ae-2289-b106-330a6218710d

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/201/links/properties

Removido - "first"

Remoção

post/responses/201/links/properties

Removido - "last"

Remoção

post/responses/201/links/properties

Removido - "next"

Remoção

post/responses/201/links/properties

Removido - "prev"

Remoção

post/responses/201/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/201/meta/properties

Removido - "totalPages"

Remoção

post/responses/201/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/201/meta/properties

Removido - "totalRecords"

Remoção

post/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/400//meta/properties

Removido - "totalPages"

Remoção

post/responses/400//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/400//meta/properties

Removido - "totalRecords"

Remoção

post/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/401//meta/properties

Removido - "totalPages"

Remoção

post/responses/401//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/401//meta/properties

Removido - "totalRecords"

Remoção

post/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/403//meta/properties

Removido - "totalPages"

Remoção

post/responses/403//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/403//meta/properties

Removido - "totalRecords"

Remoção

post/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/404//meta/properties

Removido - "totalPages"

Remoção

post/responses/404//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/404//meta/properties

Removido - "totalRecords"

Remoção

post/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/405//meta/properties

Removido - "totalPages"

Remoção

post/responses/405//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/405//meta/properties

Removido - "totalRecords"

Remoção

post/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/406//meta/properties

Removido - "totalPages"

Remoção

post/responses/406//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/406//meta/properties

Removido - "totalRecords"

Remoção

post/responses/415//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/415//meta/properties

Removido - "totalPages"

Remoção

post/responses/415//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/415//meta/properties

Removido - "totalRecords"

Remoção

post/responses/422//errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na durante o processo de extensão do consentimento: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de...

Códigos de erros previstos na durante o processo de extensão do consentimento: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de...

post/responses/422//errors/items/code/enum

Removido - "REFRESH\_TOKEN\_JWT"

Remoção

enum

post/responses/422//errors/items/detail

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: O consentimento informado não pode...

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: O consentimento informado não pode...

post/responses/422//errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de múltipla a...

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de múltipla a...

post/responses/422//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/422//meta/properties

Removido - "totalPages"

Remoção

post/responses/422//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/422//meta/properties

Removido - "totalRecords"

Remoção

post/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/429//meta/properties

Removido - "totalPages"

Remoção

post/responses/429//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/429//meta/properties

Removido - "totalRecords"

Remoção

post/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/500//meta/properties

Removido - "totalPages"

Remoção

post/responses/500//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/500//meta/properties

Removido - "totalRecords"

Remoção

post/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/504//meta/properties

Removido - "totalPages"

Remoção

post/responses/504//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/504//meta/properties

Removido - "totalRecords"

Remoção

post/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/529//meta/properties

Removido - "totalPages"

Remoção

post/responses/529//meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/529//meta/properties

Removido - "totalRecords"

Remoção

post/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

post/responses/default/meta/properties

Removido - "totalPages"

Remoção

post/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

post/responses/default/meta/properties

Removido - "totalRecords"

Remoção
