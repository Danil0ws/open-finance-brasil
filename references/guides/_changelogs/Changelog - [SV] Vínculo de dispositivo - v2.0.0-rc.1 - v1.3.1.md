# Changelog - [SV] Vínculo de dispositivo - v2.0.0-rc.1 - v1.3.1

## POST /enrollments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Adicionado - "enrollmentName"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido obrigatóriedade no campo 'expirationDateTime'

Remoção

required

post/responses/201/data/properties

Adicionado - "enrollmentName"

Adição

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

O instante de expiração deste vínculo de conta, de acordo com a regulação vigente.

Data e hora definida pelo usuário em que o vínculo do dispositivo deve expirar, perdendo sua validade. \[Restrição\] Campo obrigató...

post/responses/201/links/self

Alterado - "format"

Alteração

uri

url

post/responses/201/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

post/responses/201/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação do vínculo de conta: • PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de conta n...

Códigos de erros previstos na criação do vínculo de conta: - PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de conta nã...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de con...

Descrição específica do erro de acordo com o código reportado: - PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de cont...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • PERMISSOES\_INVALIDAS: Permissões inválidas. • CONTA\_INVAL...

Título específico do erro reportado, de acordo com o código enviado: - PERMISSOES\_INVALIDAS: Permissões inválidas. - CONTA\_INVALID...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

## GET /enrollments/{enrollmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido obrigatóriedade no campo 'expirationDateTime'

Remoção

required

get/responses/200/data/properties

Adicionado - "enrollmentName"

Adição

get/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

O instante de expiração deste vínculo de conta, de acordo com a regulação vigente.

Data e hora definida pelo usuário em que o vínculo do dispositivo deve expirar, perdendo sua validade. \[Restrição\] Campo obrigató...

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500

Removido - "headers"

Remoção

## PATCH /enrollments/{enrollmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos no cancelamento do vínculo de conta: • STATUS\_INVALIDO: O status do vínculo de conta não permite cance...

Códigos de erros previstos no cancelamento do vínculo de conta: - STATUS\_INVALIDO: O status do vínculo de conta não permite cancel...

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_INVALIDO: O status do vínculo de conta não permite cancel...

Descrição específica do erro de acordo com o código reportado: - STATUS\_INVALIDO: O status do vínculo de conta não permite cancela...

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_INVALIDO: Status inválido. • MOTIVO\_REJEICAO: Moti...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_INVALIDO: Status inválido. - MOTIVO\_REJEICAO: Motivo...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500

Removido - "headers"

Remoção

## POST /enrollments/{enrollmentId}/fido-registration

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/clientExtensionResults

Alterado - "additionalProperties"

Alteração

true

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova cred...

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova crede...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que ...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que n...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_VINCULO\_INVALIDO: Status inválido do vínculo de con...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status inválido do vínculo de cont...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

## POST /enrollments/{enrollmentId}/fido-registration-options

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/extensions

Alterado - "additionalProperties"

Alteração

true

post/responses/201/data/user/id

Alterado - "description"

Alteração

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. • STATUS\_VINCULO\_...

Códigos de erros previstos: - RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. - STATUS\_VINCULO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • RP\_INVALIDA: O identificador da Relying Party informado não pode...

Descrição específica do erro de acordo com o código reportado: - RP\_INVALIDA: O identificador da Relying Party informado não pode ...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • RP\_INVALIDA: Relying party inválida. • STATUS\_VINCULO\_INV...

Título específico do erro reportado, de acordo com o código enviado: - RP\_INVALIDA: Relying party inválida. - STATUS\_VINCULO\_INVAL...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

## POST /enrollments/{enrollmentId}/fido-sign-options

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/extensions

Alterado - "additionalProperties"

Alteração

true

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. • STATUS\_VINCULO\_...

Códigos de erros previstos: - RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. - STATUS\_VINCULO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • RP\_INVALIDA: O identificador da Relying Party informado não pode...

Descrição específica do erro de acordo com o código reportado: - RP\_INVALIDA: O identificador da Relying Party informado não pode ...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • RP\_INVALIDA: Relying party inválida. • STATUS\_VINCULO\_INV...

Título específico do erro reportado, de acordo com o código enviado: - RP\_INVALIDA: Relying party inválida. - STATUS\_VINCULO\_INVAL...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

## POST /consents/{consentId}/authorise

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post

Alterado - "description"

Alteração

Autorização de um consentimento de pagamentos em status \`AWAITING\_AUTHORISATION\` a partir do access\_token emitido pela jornada sem...

Autorização de um consentimento de pagamentos em status \`AWAITING\_AUTHORISATION\` a partir do access\_token emitido pela jornada sem...

post/requestBody/data/fidoAssertion/clientExtensionResults

Removido - "properties"

Remoção

post/requestBody/data/fidoAssertion/clientExtensionResults

Adicionado - "additionalProperties"

Adição

true

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido - "isCallInProgress"

Remoção

post/requestBody/data/riskSignals/properties

Adicionado - "isCallingProgress"

Adição

post/requestBody/data/riskSignals/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

ID único do dispositivo gerado pela plataforma. Utiliza-se a propriedade do sistema que identifica a combinação de usuário logado...

post/requestBody/data/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

post/requestBody/data/riskSignals/geolocation

Adicionado - "description"

Adição

Localização do usuário, obtida com seu consentimento. \[Android\] Informação obtida através do \[link\]([https://developers.google.com](https://developers.google.com)...

post/requestBody/data/riskSignals/integrity

Alterado - "description"

Alteração

Informa a integridade do dispositivo e app. No Android, conforme documentação \[Play API Integrity\]([https://developer.android.com](https://developer.android.com)...

Informa a integridade do dispositivo e app. \[Android\] Conforme documentação Play API Integrity, \[link\]([https://developer.android](https://developer.android)....

post/requestBody/data/riskSignals/isCharging

Alterado - "description"

Alteração

Indica se a bateria do dispositivo está sendo carregada.

Indica se a bateria do dispositivo está sendo carregada. \[Android\] Informação obtida através do \[link\]([https://developer.android](https://developer.android)....

post/requestBody/data/riskSignals/isMockGPS

Alterado - "description"

Alteração

Indica se o dispositivo está usando um GPS falso.

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo \`COARSE\` ou \`FIN...

post/requestBody/data/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

post/requestBody/data/riskSignals/language

Alterado - "description"

Alteração

Indica o idioma do dispositivo no formato ISO 639-1.

Indica o idioma do dispositivo no formato ISO 639-1. \[Android\] Informação obtida através do \[link\]([https://developer.android.com/](https://developer.android.com/)...

post/requestBody/data/riskSignals/osVersion

Alterado - "description"

Alteração

Versão do sistema operacional.

Versão do sistema operacional. \[Android\] Informação obtida através do \[link\]([https://developer.android.com/reference/android/os/B](https://developer.android.com/reference/android/os/B)...

post/requestBody/data/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive; Em di...

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

post/requestBody/data/riskSignals/screenDimensions

Alterado - "description"

Alteração

Dimensões da tela do dispositivo

Dimensões que o aplicativo ocupa na tela do dispositivo. \[Android\] Informação obtida através do \[link\]([https://developer.android](https://developer.android)....

post/requestBody/data/riskSignals/userTimeZoneOffset

Alterado - "description"

Alteração

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. • STATUS\_CONSENTIMENTO\_I...

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. - STATUS\_CONSENTIMENTO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

## POST /enrollments/{enrollmentId}/risk-signals

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

post/requestBody/data/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

post/requestBody/data/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

post/requestBody/data/properties

Removido - "isCallInProgress"

Remoção

post/requestBody/data/properties

Adicionado - "isCallingProgress"

Adição

post/requestBody/data/accountTenure

Alterado - "example"

Alteração

2023-08-20

post/requestBody/data/antennaInformation

Adicionado - "example"

Adição

CellIdentityLte:{ mCi=2\*\*\*\*\*\*60 mPci=274 mTac=5\*\*\*1 mEarfcn=9510 mBands=\[28\] mBandwidth=2147483647 mMcc=724 mMnc=10 mAlphaLong=VIV...

post/requestBody/data/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

ID único do dispositivo gerado pela plataforma. Utiliza-se a propriedade do sistema que identifica a combinação de usuário logado...

post/requestBody/data/deviceId

Adicionado - "example"

Adição

00aa11bb22cc33dd

post/requestBody/data/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

post/requestBody/data/elapsedTimeSinceBoot

Adicionado - "example"

Adição

6356027

post/requestBody/data/geolocation

Adicionado - "description"

Adição

Localização do usuário, obtida com seu consentimento. \[Android\] Informação obtida através do \[link\]([https://developers.google.com](https://developers.google.com)...

post/requestBody/data/geolocation/latitude

Adicionado - "example"

Adição

\-15.738602

post/requestBody/data/geolocation/longitude

Adicionado - "example"

Adição

\-47.926498

post/requestBody/data/geolocation/type

Adicionado - "example"

Adição

FINE

post/requestBody/data/integrity

Alterado - "description"

Alteração

Informa a integridade do dispositivo e app. No Android, conforme documentação \[Play API Integrity\]([https://developer.android.com](https://developer.android.com)...

Informa a integridade do dispositivo e app. \[Android\] Conforme documentação Play API Integrity, \[link\]([https://developer.android](https://developer.android)....

post/requestBody/data/integrity/appRecognitionVerdict

Adicionado - "example"

Adição

PLAY\_RECOGNIZED

post/requestBody/data/integrity/deviceRecognitionVerdict

Adicionado - "example"

Adição

\[\\"MEETS\_DEVICE\_INTEGRITY\\"\]

post/requestBody/data/isCharging

Alterado - "description"

Alteração

Indica se a bateria do dispositivo está sendo carregada.

Indica se a bateria do dispositivo está sendo carregada. \[Android\] Informação obtida através do \[link\]([https://developer.android](https://developer.android)....

post/requestBody/data/isCharging

Adicionado - "example"

Adição

post/requestBody/data/isDevModeEnabled

Adicionado - "example"

Adição

post/requestBody/data/isEmulated

Adicionado - "example"

Adição

post/requestBody/data/isMockGPS

Alterado - "description"

Alteração

Indica se o dispositivo está usando um GPS falso.

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo \`COARSE\` ou \`FIN...

post/requestBody/data/isMockGPS

Adicionado - "example"

Adição

post/requestBody/data/isMonkeyRunner

Adicionado - "example"

Adição

post/requestBody/data/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

post/requestBody/data/isRootedDevice

Adicionado - "example"

Adição

post/requestBody/data/isUsbConnected

Adicionado - "example"

Adição

post/requestBody/data/language

Alterado - "description"

Alteração

Indica o idioma do dispositivo no formato ISO 639-1.

Indica o idioma do dispositivo no formato ISO 639-1. \[Android\] Informação obtida através do \[link\]([https://developer.android.com/](https://developer.android.com/)...

post/requestBody/data/osVersion

Alterado - "description"

Alteração

Versão do sistema operacional.

Versão do sistema operacional. \[Android\] Informação obtida através do \[link\]([https://developer.android.com/reference/android/os/B](https://developer.android.com/reference/android/os/B)...

post/requestBody/data/osVersion

Adicionado - "example"

Adição

14

post/requestBody/data/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive; Em di...

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

post/requestBody/data/screenBrightness

Adicionado - "example"

Adição

255

post/requestBody/data/screenDimensions

Alterado - "description"

Alteração

Dimensões da tela do dispositivo

Dimensões que o aplicativo ocupa na tela do dispositivo. \[Android\] Informação obtida através do \[link\]([https://developer.android](https://developer.android)....

post/requestBody/data/screenDimensions/height

Adicionado - "example"

Adição

2340

post/requestBody/data/screenDimensions/width

Adicionado - "example"

Adição

1080

post/requestBody/data/userTimeZoneOffset

Alterado - "description"

Alteração

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permit...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompatível com a operação.

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompatível com a operação. - FALTAM\_SINAI...

post/responses/422/errors/items/code/enum

Adicionado - "FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompat...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompat...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção
