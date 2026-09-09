# Changelog - [SV] Vínculo de dispositivo - v1.3.0 - v1.2.0

## POST /enrollments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

## GET /enrollments/{enrollmentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses

Removido - "429"

Remoção

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}..

## PATCH /enrollments/{enrollmentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses

Removido - "429"

Remoção

patch/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/204/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/204/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/204/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/204/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/204/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

patch/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

## POST /enrollments/{enrollmentId}/fido-registration-options

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/requestBody/data/rp

Alterado - "description"

Alteração

Identificador único da Relying Party.

Identificador único da Relying Party, que corresponde ao valor do CN do certificado de transporte da iniciadora.

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/201/data/excludeCredentials/items/properties

Removido - "transports"

Remoção

post/responses/201/data/user/id

Alterado - "description"

Alteração

Identificador único do usuário sob registro.

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/201/links

Removido

Remoção

post/responses/201/data/rp/id

Alterado - "description"

Alteração

Identificador único da Relying Party.

Identificador único da Relying Party. Esse campo deve ser preenchido com o valor que é enviado na requisição no campo /data/rp.

post/responses/201/data/rp/name

Alterado - "description"

Alteração

Nome amigável da Relying Party para exibição aos usuários.

Nome amigável da Relying Party para exibição aos usuários.

post/responses/201/data/challenge

Alterado - "description"

Alteração

Sequência de bytes aleatórios gerados pelo servidor FIDO2. Deve ser o valor em formato base64.

Sequência de bytes aleatórios gerados pelo servidor FIDO2. Deve ser o valor em formato base64url.

## POST /enrollments/{enrollmentId}/fido-registration

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/204/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/204/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/201/data/id

Alterado - "description"

Alteração

Identificador da credencial.

Identificador da credencial. Deve ser o valor em formato base64url do campo rawId da chave pública criada no processo de registro do dispositivo.

post/responses/201/data/rawId

Alterado - "description"

Alteração

Identificador da credencial. Pode ser igual ao campo id.

Identificador da credencial. Para envio ao detentor, o valor deste atributo deve ser idêntico ao valor do atributo id.

post/responses/201/data/response/clientDataJson

Alterado - "description"

Alteração

Agrega as informações do aplicativo que gerou a credencial.

Agrega as informações do aplicativo que gerou a credencial. Deve ser enviado em formato base64url para o detentor.

post/responses/201/data/response/attestationObject

Alterado - "description"

Alteração

Agrega as informações da chave pública da credencial.

Agrega as informações da chave pública da credencial. Deve ser enviado em formato base64url para o detentor.

## POST /enrollments/{enrollmentId}/fido-sign-options

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/requestBody/data/rp

Alterado - "description"

Alteração

Identificador único da Relying Party.

Identificador único da Relying Party, que corresponde ao valor do CN do certificado de transporte da iniciadora.

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/201/data/allowCredentials/items/properties

Removido - "transports"

Remoção

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/201/links

Removido

Remoção

## POST /enrollments/{enrollmentId}/risk-signals

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/204/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/204/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

## POST /consents/{consentId}/authorize

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/data/fidoAssertion/Id

Alterado - Description

Alteração

Identificador da credencial.

Identificador da credencial. Deve ser o valor em formato base64url do campo rawId da chave pública utilizada no processo de autenticação.

post/data/fidoAssertion/rawId

Alterado - Description

Alteração

Identificador da credencial. Pode ser igual ao campo id.

Identificador da credencial. Para envio à detentora de conta, o valor deste atributo deve ser idêntico ao valor do atributo id.

post/data/fidoAssertion/response/clientDataJSON

Alterado - Description

Alteração

Agrega as informações do aplicativo que gerou a credencial.

Agrega as informações do aplicativo que gerou a credencial. Deve ser enviado no formato base64url para a detentora de conta.

post/data/fidoAssertion/authenticatorData

Alterado - Description

Alteração

Representa a estrutura de dados do autenticador.

Representa a estrutura de dados do autenticador. Deve ser enviado no formato base64url para a detentora de conta.

post/data/fidoAssertion/signature

Alterado - Description

Alteração

Sequencia de bytes contendo a assinatura.

Sequencia de bytes contendo a assinatura. Deve ser enviado no formato base64url para a detentora de conta.

post/data/fidoAssertion/userHandle

Alterado - Description

Alteração

Nome de usuário que foi enviado durante a criação da credencial.

Nome de usuário que foi enviado durante a criação da credencial. Deve ser enviado no formato base64url para a detentora de conta.

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/204/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/204/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/204/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/204/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

A detentora deve obrigatoriamente retornar o campo com o mes...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}...
