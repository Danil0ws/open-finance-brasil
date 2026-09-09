# Changelog - [DC] Empréstimos - v2.6.0-beta.1 - 2.5.0

none

## GET /contracts

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/companyCnpj

Alterado - "description"

Alteração

Representação alfanumérica completa do CNPJ da instituição responsável pelo contrato de empréstimo afim de identificar a instituiç...

Representação alfanumérica completa do CNPJ da instituição responsável pelo contrato de empréstimo afim de identificar a instituiç...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-v

Adicionado - "description"

Adição

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

get/responses/200/headers/x-v

Adicionado - "required"

Adição

true

get/responses/200/headers/x-v

Removido - "description"

Remoção

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/cnpjConsignee

Alterado - "description"

Alteração

CNPJ do consignante (CNPJ corresponde ao número de inscrição no Cadastro de Pessoa Jurídica). Deve-se ter apenas a representação...

CNPJ do consignante (CNPJ corresponde ao registro alfanumérico de inscrição no Cadastro de Pessoa Jurídica). Deve-se ter apenas ...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-v

Adicionado - "description"

Adição

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

get/responses/200/headers/x-v

Adicionado - "required"

Adição

true

get/responses/200/headers/x-v

Removido - "description"

Remoção

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

## GET /contracts/{contractId}/payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-v

Adicionado - "description"

Adição

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

get/responses/200/headers/x-v

Adicionado - "required"

Adição

true

get/responses/200/headers/x-v

Removido - "description"

Remoção

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

## GET /contracts/{contractId}/scheduled-instalments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/totalNumberOfInstalments

Alterado - "description"

Alteração

Prazo Total segundo o tipo (dia, semana, mês, ano) referente à Modalidade de Crédito informada. \[Restrição\] Obrigatoriamente deve...

Prazo Total segundo o tipo (dia, semana, mês, ano) referente à Modalidade de Crédito informada. Deve corresponder à soma de \`paidI...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-v

Adicionado - "description"

Adição

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

get/responses/200/headers/x-v

Adicionado - "required"

Adição

true

get/responses/200/headers/x-v

Removido - "description"

Remoção

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

## GET /contracts/{contractId}/warranties

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-v

Adicionado - "description"

Adição

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...

get/responses/200/headers/x-v

Adicionado - "required"

Adição

true

get/responses/200/headers/x-v

Removido - "description"

Remoção

Cabeçalho que indica a versão implementada da API pela instituição financeira. Deve ser preenchido de forma completa, por exemplo:...
