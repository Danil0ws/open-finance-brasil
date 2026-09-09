# Changelog - [DC] Câmbio - v1.1.0 - v1.0.0

## GET /operations

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200

Adicionado - "headers"

Adição

get/responses/200/data/items/companyCnpj

Alterado - "description"

Alteração

Número completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde ao número de inscrição no Cadastro de Pessoa...

Registro completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde a representação alfanumérica da inscrição ...

get/responses/200/data/items/companyCnpj

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/first

Alterado - "description"

Alteração

URI da primeira página que originou essa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

URL da primeira página que originou essa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "description"

Alteração

URI da última página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

URL da última página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "description"

Alteração

URI da próxima página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

URL da próxima página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "description"

Alteração

URI da página anterior dessa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

URL da página anterior dessa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "description"

Alteração

URI completo que gerou a resposta atual.

URL completo que gerou a resposta atual.

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /operations/{operationId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200

Adicionado - "headers"

Adição

get/responses/200/data/authorizedInstitutionCnpjNumber

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/intermediaryInstitutionCnpjNumber

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "description"

Alteração

URI completo que gerou a resposta atual.

URL completo que gerou a resposta atual.

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /operations/{operationId}/events

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200

Adicionado - "headers"

Adição

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/first

Alterado - "description"

Alteração

URI da primeira página que originou essa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

URL da primeira página que originou essa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "description"

Alteração

URI da última página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

URL da última página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "description"

Alteração

URI da próxima página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

URL da próxima página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "description"

Alteração

URI da página anterior dessa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

URL da página anterior dessa lista de resultados. Restrição - Obrigatório quando não for a primeira página da resposta

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "description"

Alteração

URI completo que gerou a resposta atual.

URL completo que gerou a resposta atual.

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https?:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/foreignPartie/foreignPartieName

Alterado - "maxLength"

Alteração

80

120
