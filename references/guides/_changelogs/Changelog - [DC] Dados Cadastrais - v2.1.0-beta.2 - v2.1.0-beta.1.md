# Changelog - [DC] Dados Cadastrais - v2.1.0-beta.2 - v2.1.0-beta.1

16falsenonelisttrue

## GET /personal/identifications

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

## GET /personal/qualifications

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

## GET /personal/financial-relations

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/portabilitiesReceived

Alterado - "description"

Alteração

Lista de informações de empregador recebidos através de portabilidade de salário solicitada pelo cliente da transmissora à institu...

Lista de informações de empregador recebidos através de portabilidade de salário solicitada pelo cliente da transmissora à institu...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

## GET /business/identifications

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

0

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

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

## GET /business/qualifications

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

## GET /business/financial-relations

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

true

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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
