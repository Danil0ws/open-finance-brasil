# Changelog - [SV] Vínculo de dispositivo - 2.0.0-beta.1 - v1.3.1

## POST /enrollments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/links/self

Alterado - "format"

Alteração

uri

url

post/responses/201/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/201/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

## GET /enrollments/{enrollmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

get/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

get/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

get/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

get/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

get/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

get/responses/500

Removido - "headers"

Remoção

patch/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

patch/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

## POST /enrollments/{enrollmentId}/fido-registration

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/clientExtensionResults

Alterado - "additionalProperties"

Alteração

true

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/201/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/201/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permit...

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

## POST /enrollments/{enrollmentId}/risk-signals

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

Dimensões que o aplicativo ocupa na tela do dispositivo. \[Android\] Informação obtida através do \[link\]([https://developer.androi](https://developer.androi)...

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

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/204/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/400/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/401/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/403/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/404/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/405/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/406/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/415/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta.

post/responses/422/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser "espelhado" pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.
