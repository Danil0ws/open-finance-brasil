# Changelog - [DA] Previdência- v2.0.0-beta.2 - v2.0.0-beta.1

## GET /risk-coverages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/participant/name

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society

Alterado - "description"

Alteração

Conjunto de informações relativas à seguradora do produto de open insurance

Objeto que representa a empresa regulada pela SUSEP que oferta produtos definidos em OPIN

get/responses/200/data/items/society/products/items/coverages/items/attributes/excludedRisksURL

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue

Removido obrigatóriedade no campo 'currency'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items/attributes/maxValue

Removido obrigatóriedade no campo 'amount'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue

Removido obrigatóriedade no campo 'currency'

Remoção

required

get/responses/200/data/items/society/products/items/coverages/items/attributes/minValue

Removido obrigatóriedade no campo 'amount'

Remoção

required

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/reclaim/gracePeriod

Removido obrigatóriedade no campo 'amount'

Remoção

required

get/responses/200/data/items/society/products/items/termsAndConditions/items/contractTermsConditions

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

## GET /survival-coverages

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/participant/brand

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/participant/name

Adicionado - "pattern"

Adição

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

get/responses/200/data/items/society

Alterado - "description"

Alteração

Conjunto de informações relativas à seguradora do produto de open insurance

Objeto que representa a empresa regulada pela SUSEP que oferta produtos definidos em OPIN

get/responses/200/data/items/society/products/items/minimumRequirement/contractingMinRequirement

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/data/items/society/products/items/termsAndConditions/items/contractTermsConditions

Adicionado - "pattern"

Adição

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$
