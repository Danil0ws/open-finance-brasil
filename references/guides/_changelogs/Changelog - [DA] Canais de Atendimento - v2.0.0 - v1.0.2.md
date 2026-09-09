# Changelog - [DA] Canais de Atendimento - v2.0.0 - v1.0.2

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "title"

Alteração

APIs OpenData do Open Finance Brasil

API OpenData Channels do Open Finance Brasil

/info

Alterado - "description"

Alteração

As APIs descritas neste documento são referentes as APIs da fase OpenData do Open Finance Brasil.

A API descrita neste documento é referente as API Channels da fase OpenData do Open Finance Brasil.

/info

Alterado - "version"

Alteração

1.0.2

2.0.0-rc.2

/servers/0

Alterado - "url"

Alteração

[http://api.banco.com.br/open-banking/channels/v1](http://api.banco.com.br/open-banking/channels/v1)

[http://api.banco.com.br/open-banking/channels/v2](http://api.banco.com.br/open-banking/channels/v2)

/tags/0

Alterado - "description"

Alteração

Operações para listagem de canais de atendimentos

Operações para listagem de canais de atendimento

## GET /banking-agents

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page-size

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/responses

Adicionado - "400"

Adição

get/responses

Adicionado - "404"

Adição

get/responses

Adicionado - "405"

Adição

get/responses

Adicionado - "429"

Adição

get/responses

Adicionado - "500"

Adição

get/responses

Adicionado - "504"

Adição

get/responses

Adicionado - "529"

Adição

get/responses

Adicionado - "default"

Adição

get/responses/200

Removido - "example"

Remoção

get/responses/200/data

Alterado - "type"

Alteração

object

array

get/responses/200/data

Removido - "required"

Remoção

get/responses/200/data

Removido - "properties"

Remoção

get/responses/200/data

Adicionado - "items"

Adição

get/responses/200/data

Adicionado - "minItems"

Adição

1

get/responses/200/links

Adicionado - "description"

Adição

Referências para outros recursos da API requisitada

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/first

Adicionado - "minLength"

Adição

5

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "minLength"

Adição

5

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/self

Adicionado - "minLength"

Adição

5

get/responses/200/meta

Adicionado - "description"

Adição

Meta informações referente à API requisitada

## GET /branches

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page-size

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/responses

Adicionado - "400"

Adição

get/responses

Adicionado - "404"

Adição

get/responses

Adicionado - "405"

Adição

get/responses

Adicionado - "429"

Adição

get/responses

Adicionado - "500"

Adição

get/responses

Adicionado - "504"

Adição

get/responses

Adicionado - "529"

Adição

get/responses

Adicionado - "default"

Adição

get/responses/200

Removido - "example"

Remoção

get/responses/200/data

Alterado - "type"

Alteração

object

array

get/responses/200/data

Removido - "required"

Remoção

get/responses/200/data

Removido - "properties"

Remoção

get/responses/200/data

Adicionado - "description"

Adição

Conjunto de informações referente as dependências próprias da instituição.

get/responses/200/data

Adicionado - "minItems"

Adição

1

get/responses/200/data

Adicionado - "items"

Adição

get/responses/200/links

Adicionado - "description"

Adição

Referências para outros recursos da API requisitada

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/first

Adicionado - "minLength"

Adição

5

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "minLength"

Adição

5

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/self

Adicionado - "minLength"

Adição

5

get/responses/200/meta

Adicionado - "description"

Adição

Meta informações referente à API requisitada

## GET /electronic-channels

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page-size

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/responses

Adicionado - "400"

Adição

get/responses

Adicionado - "404"

Adição

get/responses

Adicionado - "405"

Adição

get/responses

Adicionado - "429"

Adição

get/responses

Adicionado - "500"

Adição

get/responses

Adicionado - "504"

Adição

get/responses

Adicionado - "529"

Adição

get/responses

Adicionado - "default"

Adição

get/responses/200

Removido - "example"

Remoção

get/responses/200/data

Alterado - "type"

Alteração

object

array

get/responses/200/data

Removido - "required"

Remoção

get/responses/200/data

Removido - "properties"

Remoção

get/responses/200/data

Adicionado - "description"

Adição

Conjunto de informações referente aos canais eletrônicos de atendimento da instituição

get/responses/200/data

Adicionado - "minItems"

Adição

1

get/responses/200/data

Adicionado - "items"

Adição

get/responses/200/links

Adicionado - "description"

Adição

Referências para outros recursos da API requisitada

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/first

Adicionado - "minLength"

Adição

5

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "minLength"

Adição

5

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/self

Adicionado - "minLength"

Adição

5

get/responses/200/meta

Adicionado - "description"

Adição

Meta informações referente à API requisitada

## GET /phone-channels

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page-size

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/responses

Adicionado - "400"

Adição

get/responses

Adicionado - "404"

Adição

get/responses

Adicionado - "405"

Adição

get/responses

Adicionado - "429"

Adição

get/responses

Adicionado - "500"

Adição

get/responses

Adicionado - "504"

Adição

get/responses

Adicionado - "529"

Adição

get/responses

Adicionado - "default"

Adição

get/responses/200

Removido - "example"

Remoção

get/responses/200/data

Alterado - "type"

Alteração

object

array

get/responses/200/data

Removido - "required"

Remoção

get/responses/200/data

Removido - "properties"

Remoção

get/responses/200/data

Adicionado - "description"

Adição

Conjunto de informações referente aos canais telefônicos de atendimento da instituição

get/responses/200/data

Adicionado - "minItems"

Adição

1

get/responses/200/data

Adicionado - "items"

Adição

get/responses/200/links

Adicionado - "description"

Adição

Referências para outros recursos da API requisitada

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/first

Adicionado - "minLength"

Adição

5

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "minLength"

Adição

5

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/self

Adicionado - "minLength"

Adição

5

get/responses/200/meta

Adicionado - "description"

Adição

Meta informações referente à API requisitada

## GET /shared-automated-teller-machines

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page-size

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/responses

Adicionado - "400"

Adição

get/responses

Adicionado - "404"

Adição

get/responses

Adicionado - "405"

Adição

get/responses

Adicionado - "429"

Adição

get/responses

Adicionado - "500"

Adição

get/responses

Adicionado - "504"

Adição

get/responses

Adicionado - "529"

Adição

get/responses

Adicionado - "default"

Adição

get/responses/200/data

Alterado - "type"

Alteração

object

array

get/responses/200/data

Removido - "properties"

Remoção

get/responses/200/data

Adicionado - "description"

Adição

Conjunto de informações referente aos terminais compartilhados de autoatendimento da instituição

get/responses/200/data

Adicionado - "minItems"

Adição

1

get/responses/200/data

Adicionado - "items"

Adição

get/responses/200/links

Adicionado - "description"

Adição

Referências para outros recursos da API requisitada

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/first

Adicionado - "minLength"

Adição

5

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "minLength"

Adição

5

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "minLength"

Adição

5

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/channels/v2/resource](https://api.banco.com.br/open-banking/channels/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/self

Adicionado - "minLength"

Adição

5

get/responses/200/meta

Adicionado - "description"

Adição

Meta informações referente à API requisitada
