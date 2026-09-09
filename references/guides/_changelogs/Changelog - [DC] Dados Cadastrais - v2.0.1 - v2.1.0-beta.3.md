# Changelog - [DC] Dados Cadastrais - v2.0.1 - v2.1.0-beta.3

16falsenonelisttrue

## GET /personal/identifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/data/items/contacts/emails/items/email

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[a-z0-9.!#$&'\*+\\/=?^\_\`{|}~-\]+@\[a-z0-9\](?:\[a-z0-9-\]{0,61}\[a-z0-9\])?(?:\\.\[a-z0-9\](?:\[a-z0-9-\]{0,61}\[a-z0-9\])?)\*$

get/responses/200/data/items/contacts/phones/items/areaCode

Removido - "enum"

Remoção

get/responses/200/data/items/contacts/phones/items/areaCode

Adicionado - "maxLength"

Adição

3

get/responses/200/data/items/contacts/phones/items/areaCode

Adicionado - "minLength"

Adição

2

get/responses/200/data/items/contacts/phones/items/areaCode

Adicionado - "pattern"

Adição

^(\\d{2,3})$

get/responses/200/data/items/contacts/phones/items/number

Alterado - "maxLength"

Alteração

11

13

get/responses/200/data/items/contacts/phones/items/number

Alterado - "pattern"

Alteração

^(\[0-9\]{8,11})$

^(\[0-9\]{6,13})$

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /personal/qualifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /personal/financial-relations

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/data/properties

Adicionado - "portabilitiesReceived"

Adição

get/responses/200/data/properties

Adicionado - "paychecksBankLink"

Adição

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /business/identifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/data/items/contacts/emails/items/email

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[a-z0-9.!#$&'\*+\\/=?^\_\`{|}~-\]+@\[a-z0-9\](?:\[a-z0-9-\]{0,61}\[a-z0-9\])?(?:\\.\[a-z0-9\](?:\[a-z0-9-\]{0,61}\[a-z0-9\])?)\*$

get/responses/200/data/items/contacts/phones/items/areaCode

Removido - "enum"

Remoção

get/responses/200/data/items/contacts/phones/items/areaCode

Adicionado - "maxLength"

Adição

3

get/responses/200/data/items/contacts/phones/items/areaCode

Adicionado - "minLength"

Adição

2

get/responses/200/data/items/contacts/phones/items/areaCode

Adicionado - "pattern"

Adição

^(\\d{2,3})$

get/responses/200/data/items/contacts/phones/items/number

Alterado - "maxLength"

Alteração

11

13

get/responses/200/data/items/contacts/phones/items/number

Alterado - "pattern"

Alteração

^(\[0-9\]{8,11})$

^(\[0-9\]{6,13})$

get/responses/200/data/items/contacts/postalAddresses

Alterado - "minItems"

Alteração

1

get/responses/200/data/items/contacts/postalAddresses/items/address

Alterado - "pattern"

Alteração

^\\w{2}\[\\w\\W\\s\]\*$

^\[\\w\\W\\s\]\*$

get/responses/200/data/items/contacts/postalAddresses/items/townName

Alterado - "pattern"

Alteração

^\\w{2}\[\\w\\W\\s\]\*$

^\[\\w\\W\\s\]\*$

get/responses/200/data/items/parties/items/civilName

Alterado - "description"

Alteração

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o registro de seu nascimento, com o qual será identificada por toda a sua vida, bem como após a sua morte)

\[Restrição\] O campo civilName deve ser obrigatoriamente preenchido quando personType for PESSOA\_JURIDICA.

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o registro de seu nascimento, com o qual será identificada por toda a sua vida, bem como após a sua morte)

\[Restrição\] O campo civilName deve ser obrigatoriamente preenchido quando personType for PESSOA\_NATURAL.

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /business/qualifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /business/financial-relations

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção
