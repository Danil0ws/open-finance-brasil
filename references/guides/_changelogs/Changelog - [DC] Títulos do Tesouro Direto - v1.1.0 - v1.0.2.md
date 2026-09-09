# Changelog - [DC] Títulos do Tesouro Direto - v1.1.0 - v1.0.2

## GET /investments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-v

Adicionado - "header"

Adição

get/parameters/x-fapi-interaction-id

Adicionado - "header"

Adição

get/responses/200/data/items/brandName

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[^\\s\](.\*\[^\\s\])?$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/400/

Removido - "additionalProperties"

Remoção

get/responses/400/errors/items

Removido - "additionalProperties"

Remoção

get/responses/400/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/400/meta

Removido - "additionalProperties"

Remoção

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

get/responses/401/

Removido - "additionalProperties"

Remoção

get/responses/401/errors/items

Removido - "additionalProperties"

Remoção

get/responses/401/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/401/meta

Removido - "additionalProperties"

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

get/responses/403/

Removido - "additionalProperties"

Remoção

get/responses/403/errors/items

Removido - "additionalProperties"

Remoção

get/responses/403/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/403/meta

Removido - "additionalProperties"

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

get/responses/404/

Removido - "additionalProperties"

Remoção

get/responses/404/errors/items

Removido - "additionalProperties"

Remoção

get/responses/404/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/404/meta

Removido - "additionalProperties"

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

get/responses/405/

Removido - "additionalProperties"

Remoção

get/responses/405/errors/items

Removido - "additionalProperties"

Remoção

get/responses/405/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/405/meta

Removido - "additionalProperties"

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

get/responses/406/

Removido - "additionalProperties"

Remoção

get/responses/406/errors/items

Removido - "additionalProperties"

Remoção

get/responses/406/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/406/meta

Removido - "additionalProperties"

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

get/responses/422/

Removido - "additionalProperties"

Remoção

get/responses/422/errors/items

Removido - "additionalProperties"

Remoção

get/responses/422/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/422/meta

Removido - "additionalProperties"

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

get/responses/423/

Removido - "additionalProperties"

Remoção

get/responses/423/errors/items

Removido - "additionalProperties"

Remoção

get/responses/423/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/423/meta

Removido - "additionalProperties"

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

get/responses/429/

Removido - "additionalProperties"

Remoção

get/responses/429/errors/items

Removido - "additionalProperties"

Remoção

get/responses/429/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/429/meta

Removido - "additionalProperties"

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

get/responses/500/

Removido - "additionalProperties"

Remoção

get/responses/500/errors/items

Removido - "additionalProperties"

Remoção

get/responses/500/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/500/meta

Removido - "additionalProperties"

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

get/responses/504/

Removido - "additionalProperties"

Remoção

get/responses/504/errors/items

Removido - "additionalProperties"

Remoção

get/responses/504/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/504/meta

Removido - "additionalProperties"

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

get/responses/529/

Removido - "additionalProperties"

Remoção

get/responses/529/errors/items

Removido - "additionalProperties"

Remoção

get/responses/529/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/529/meta

Removido - "additionalProperties"

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

get/responses/default/

Removido - "additionalProperties"

Remoção

get/responses/default/errors/items

Removido - "additionalProperties"

Remoção

get/responses/default/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/default/meta

Removido - "additionalProperties"

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

## GET /investments/{investmentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-v

Adicionado - "header"

Adição

get/parameters/x-fapi-interaction-id

Adicionado - "header"

Adição

get/responses/200/data/remuneration/postFixedIndexerPercentage

Alterado - "description"

Alteração

Percentual do indexador da aquisição do contrato. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o cam...

Percentual do indexador da aquisição do contrato. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o cam...

get/responses/200/data/remuneration/postFixedIndexerPercentage

Alterado - "maxLength"

Alteração

8

10

get/responses/200/data/remuneration/postFixedIndexerPercentage

Alterado - "pattern"

Alteração

^\\d{1}\\.\\d{6}$

^-?\\d{1,2}\\.\\d{6}$

get/responses/200/data/remuneration/preFixedRate

Alterado - "description"

Alteração

Valor da taxa da aquisição do contrato. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando o campo 'indexe...

Valor da taxa da aquisição do contrato. \[Restrição\] Campo de preenchimento obrigatório pelas participantes quando houver \`PRE\_FIX...

get/responses/200/data/remuneration/preFixedRate

Alterado - "maxLength"

Alteração

8

9

get/responses/200/data/remuneration/preFixedRate

Alterado - "pattern"

Alteração

^\\d{1}\\.\\d{6}$

^-?\\d{1}\\.\\d{6}$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

URI da última página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta.

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

Alterado - "maxLength"

Alteração

2000

4048

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

Alterado - "maxLength"

Alteração

2000

4048

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

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/400/

Removido - "additionalProperties"

Remoção

get/responses/400/errors/items

Removido - "additionalProperties"

Remoção

get/responses/400/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/400/meta

Removido - "additionalProperties"

Remoção

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

get/responses/401/

Removido - "additionalProperties"

Remoção

get/responses/401/errors/items

Removido - "additionalProperties"

Remoção

get/responses/401/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/401/meta

Removido - "additionalProperties"

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

get/responses/403/

Removido - "additionalProperties"

Remoção

get/responses/403/errors/items

Removido - "additionalProperties"

Remoção

get/responses/403/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/403/meta

Removido - "additionalProperties"

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

get/responses/404/

Removido - "additionalProperties"

Remoção

get/responses/404/errors/items

Removido - "additionalProperties"

Remoção

get/responses/404/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/404/meta

Removido - "additionalProperties"

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

get/responses/405/

Removido - "additionalProperties"

Remoção

get/responses/405/errors/items

Removido - "additionalProperties"

Remoção

get/responses/405/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/405/meta

Removido - "additionalProperties"

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

get/responses/406/

Removido - "additionalProperties"

Remoção

get/responses/406/errors/items

Removido - "additionalProperties"

Remoção

get/responses/406/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/406/meta

Removido - "additionalProperties"

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

get/responses/422/

Removido - "additionalProperties"

Remoção

get/responses/422/errors/items

Removido - "additionalProperties"

Remoção

get/responses/422/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/422/meta

Removido - "additionalProperties"

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

get/responses/423/

Removido - "additionalProperties"

Remoção

get/responses/423/errors/items

Removido - "additionalProperties"

Remoção

get/responses/423/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/423/meta

Removido - "additionalProperties"

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

get/responses/429/

Removido - "additionalProperties"

Remoção

get/responses/429/errors/items

Removido - "additionalProperties"

Remoção

get/responses/429/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/429/meta

Removido - "additionalProperties"

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

get/responses/500/

Removido - "additionalProperties"

Remoção

get/responses/500/errors/items

Removido - "additionalProperties"

Remoção

get/responses/500/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/500/meta

Removido - "additionalProperties"

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

get/responses/504/

Removido - "additionalProperties"

Remoção

get/responses/504/errors/items

Removido - "additionalProperties"

Remoção

get/responses/504/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/504/meta

Removido - "additionalProperties"

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

get/responses/529/

Removido - "additionalProperties"

Remoção

get/responses/529/errors/items

Removido - "additionalProperties"

Remoção

get/responses/529/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/529/meta

Removido - "additionalProperties"

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

get/responses/default/

Removido - "additionalProperties"

Remoção

get/responses/default/errors/items

Removido - "additionalProperties"

Remoção

get/responses/default/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/default/meta

Removido - "additionalProperties"

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

## GET /investments/{investmentId}/balances

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-v

Adicionado - "header"

Adição

get/parameters/x-fapi-interaction-id

Adicionado - "header"

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

URI da última página dessa lista de resultados. Restrição - Obrigatório quando não for a última página da resposta.

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

Alterado - "maxLength"

Alteração

2000

4048

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

Alterado - "maxLength"

Alteração

2000

4048

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

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/400/

Removido - "additionalProperties"

Remoção

get/responses/400/errors/items

Removido - "additionalProperties"

Remoção

get/responses/400/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/400/meta

Removido - "additionalProperties"

Remoção

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

get/responses/401/

Removido - "additionalProperties"

Remoção

get/responses/401/errors/items

Removido - "additionalProperties"

Remoção

get/responses/401/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/401/meta

Removido - "additionalProperties"

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

get/responses/403/

Removido - "additionalProperties"

Remoção

get/responses/403/errors/items

Removido - "additionalProperties"

Remoção

get/responses/403/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/403/meta

Removido - "additionalProperties"

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

get/responses/404/

Removido - "additionalProperties"

Remoção

get/responses/404/errors/items

Removido - "additionalProperties"

Remoção

get/responses/404/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/404/meta

Removido - "additionalProperties"

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

get/responses/405/

Removido - "additionalProperties"

Remoção

get/responses/405/errors/items

Removido - "additionalProperties"

Remoção

get/responses/405/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/405/meta

Removido - "additionalProperties"

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

get/responses/406/

Removido - "additionalProperties"

Remoção

get/responses/406/errors/items

Removido - "additionalProperties"

Remoção

get/responses/406/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/406/meta

Removido - "additionalProperties"

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

get/responses/422/

Removido - "additionalProperties"

Remoção

get/responses/422/errors/items

Removido - "additionalProperties"

Remoção

get/responses/422/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/422/meta

Removido - "additionalProperties"

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

get/responses/423/

Removido - "additionalProperties"

Remoção

get/responses/423/errors/items

Removido - "additionalProperties"

Remoção

get/responses/423/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/423/meta

Removido - "additionalProperties"

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

get/responses/429/

Removido - "additionalProperties"

Remoção

get/responses/429/errors/items

Removido - "additionalProperties"

Remoção

get/responses/429/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/429/meta

Removido - "additionalProperties"

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

get/responses/500/

Removido - "additionalProperties"

Remoção

get/responses/500/errors/items

Removido - "additionalProperties"

Remoção

get/responses/500/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/500/meta

Removido - "additionalProperties"

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

get/responses/504/

Removido - "additionalProperties"

Remoção

get/responses/504/errors/items

Removido - "additionalProperties"

Remoção

get/responses/504/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/504/meta

Removido - "additionalProperties"

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

get/responses/529/

Removido - "additionalProperties"

Remoção

get/responses/529/errors/items

Removido - "additionalProperties"

Remoção

get/responses/529/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/529/meta

Removido - "additionalProperties"

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

get/responses/default/

Removido - "additionalProperties"

Remoção

get/responses/default/errors/items

Removido - "additionalProperties"

Remoção

get/responses/default/meta

Alterado - "description"

Alteração

Meta informações referente a API requisitada.

Meta informações referente à API requisitada.

get/responses/default/meta

Removido - "additionalProperties"

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

get/responses/200/data/grossAmount

Alterado - "description"

Alteração

Valor do investimento anterior à dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência.

Valor do investimento anterior à dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência. I...

get/responses/200/data/netAmount

Alterado - "description"

Alteração

Valor do investimento posterior a dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência.

Valor do investimento posterior a dedução de impostos, taxas e tarifas (se houver), atualizado (a mercado) na data de referência. ...

## GET /investments/{investmentId}/transactions

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/fromTransactionDate

Alterado - "description"

Alteração

Data inicial de filtragem. \[Restrição\] Deve obrigatoriamente ser enviado caso o campo toTransactionDate seja informado. Caso não ...

Data inicial de filtragem. \[Restrição\] Deve obrigatoriamente sempre ser enviado em conjunto com o campo \`toTransactionDate\`. Cas...

get/parameters/toTransactionDate

Alterado - "description"

Alteração

Data final de filtragem. \[Restrição\] Deve obrigatoriamente ser enviado caso o campo fromTransactionDate seja informado. Caso não ...

Data final de filtragem. \[Restrição\] Deve obrigatoriamente sempre ser enviado em conjunto com o campo \`fromTransactionDate\`. Caso...

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-v

Adicionado - "header"

Adição

get/parameters/x-fapi-interaction-id

Adicionado - "header"

Adição

get/responses/200/data/items/remunerationTransactionRate

Alterado - "maxLength"

Alteração

8

9

get/responses/200/data/items/remunerationTransactionRate

Alterado - "pattern"

Alteração

^\\d{1}\\.\\d{6}$

^-?\\d{1}\\.\\d{6}$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /investments/{investmentId}/transactions-current

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/fromTransactionDate

Alterado - "description"

Alteração

Data inicial de filtragem. O período máximo utilizado no filtro é de 7 dias inclusive (D-6). \[Restrição\] Deve obrigatoriamente se...

Data inicial de filtragem. O período máximo utilizado no filtro é de 7 dias inclusive (D-6). \[Restrição\] Deve obrigatoriamente s...

get/parameters/toTransactionDate

Alterado - "description"

Alteração

Data final de filtragem. O período máximo utilizado no filtro é de 7 dias inclusive (D-6). \[Restrição\] Deve obrigatoriamente ser ...

Data final de filtragem. O período máximo utilizado no filtro é de 7 dias inclusive (D-6). \[Restrição\] Deve obrigatoriamente sem...

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID RFC4122 usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (clie...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-v

Adicionado - "header"

Adição

get/parameters/x-fapi-interaction-id

Adicionado - "header"

Adição

get/responses/200/data/items/remunerationTransactionRate

Alterado - "maxLength"

Alteração

8

9

get/responses/200/data/items/remunerationTransactionRate

Alterado - "pattern"

Alteração

^\\d{1}\\.\\d{6}$

^-?\\d{1}\\.\\d{6}$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$
