# Changelog - Comum (Discovery) - v2.0.0 - v1.0.2

23

## GET /outages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/parameters/page-size

Adicionado - "format"

Adição

int32

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

Adicionado - "maxItems"

Adição

1000

get/responses/200/data/items

Adicionado - "type"

Adição

object

get/responses/200/data/items/duration

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/explanation

Alterado - "description"

Alteração

Explicação sobre os motivos da indisponibilidade.

Explicação sobre os motivos da indisponibilidade, podendo a instituição indicar quais implementações estarão indisponíveis.

get/responses/200/data/items/explanation

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/outageTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000

## GET /status

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "summary"

Alteração

a descrição referente ao código de status retornado pelas APIs

Descrição do status da implementação das APIs do OFB

get

Alterado - "description"

Alteração

descrição referente ao código de status retornado pelas APIs

Descrição do status da implementação das APIs do OFB

get/parameters/page

Adicionado - "maximum"

Adição

2147483647

get/parameters/page

Adicionado - "format"

Adição

int32

get/parameters/page-size

Adicionado - "maximum"

Adição

1000

get/parameters/page-size

Adicionado - "format"

Adição

int32

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

Alterado - "description"

Alteração

código de status retornado pelas APIs

Descrição do status da implementação das APIs do OFB

get/responses/200/data/status

Adicionado - "maxItems"

Adição

1000

get/responses/200/data/status/items/code

Alterado - "description"

Alteração

Condição atual da API: \* \`OK\` - A implementação é totalmente funcional \* \`PARTIAL\_FAILURE\` - Um ou mais endpoints estão indisp...

Condição atual da Implementação das APIs do OFB: - OK - A implementação de todas as APIs foi concluída e está totalmente funcional...

get/responses/200/data/status/items/detectionTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/data/status/items/detectionTime

Adicionado - "maxLength"

Adição

20

get/responses/200/data/status/items/expectedResolutionTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/data/status/items/expectedResolutionTime

Adicionado - "maxLength"

Adição

20

get/responses/200/data/status/items/explanation

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/status/items/explanation

Adicionado - "maxLength"

Adição

2000

get/responses/200/data/status/items/unavailableEndpoints

Adicionado - "maxItems"

Adição

1000

get/responses/200/data/status/items/unavailableEndpoints/example

Adicionado - "[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)"

Adição

example

get/responses/200/data/status/items/unavailableEndpoints/example

Removido - "[https://api.banco.com.br/open-banking/channels/v1/electronic-channels](https://api.banco.com.br/open-banking/channels/v1/electronic-channels)"

Remoção

example

get/responses/200/data/status/items/unavailableEndpoints/items

Adicionado - "maxLength"

Adição

2000

get/responses/200/data/status/items/updateTime

Adicionado - "pattern"

Adição

^(\\d{4})-(1\[0-2\]|0?\[1-9\])-(3\[01\]|\[12\]\[0-9\]|0?\[1-9\])T(?:\[01\]\\d|2\[0123\]):(?:\[012345\]\\d):(?:\[012345\]\\d)Z$

get/responses/200/data/status/items/updateTime

Adicionado - "maxLength"

Adição

20

get/responses/200/links/first

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/first

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/first

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/last

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/last

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/next

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/prev

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Adicionado - "maxLength"

Adição

2000

get/responses/200/links/prev

Adicionado - "example"

Adição

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/self

Alterado - "example"

Alteração

[https://api.banco.com.br/open-banking/channels/v1/](https://api.banco.com.br/open-banking/channels/v1/)<resource>

[https://api.banco.com.br/open-banking/common/v2/resource](https://api.banco.com.br/open-banking/common/v2/resource)

get/responses/200/links/self

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/self

Adicionado - "maxLength"

Adição

2000
