# Changelog - [DC] Consentimento - v3.3.0-beta.1 - v3.2.0

16falsenonelisttrue

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-customer-user-agent

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[^\\s\](.\*\[^\\s\])?$

post/parameters/x-customer-user-agent

Alterado - "maxLength"

Alteração

100

255

post/requestBody/data/properties

Adicionado - "isLinked"

Adição

post/requestBody/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

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

post/responses/201/headers

Adicionado - "x-v"

Adição

## DELETE /consents/{consentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

delete/parameters/x-customer-user-agent

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[^\\s\](.\*\[^\\s\])?$

delete/parameters/x-customer-user-agent

Alterado - "maxLength"

Alteração

100

255

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

delete/responses/204/headers

Adicionado - "x-v"

Adição

required

## GET /consents/{consentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-customer-user-agent

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[^\\s\](.\*\[^\\s\])?$

get/parameters/x-customer-user-agent

Alterado - "maxLength"

Alteração

100

255

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado - "journey"

Adição

get/responses/200/data/rejection/reason/additionalInformation

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers

Adicionado - "x-v"

Adição

## POST /consents/{consentId}/extends

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-customer-user-agent

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[^\\s\](.\*\[^\\s\])?$

post/parameters/x-customer-user-agent

Alterado - "maxLength"

Alteração

100

255

post/requestBody/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

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

post/responses/201/headers

Adicionado - "x-v"

Adição

## GET /consents/{consentId}/extensions

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-customer-user-agent

Alterado - "pattern"

Alteração

\[\\w\\W\\s\]\*

^\[^\\s\](.\*\[^\\s\])?$

get/parameters/x-customer-user-agent

Alterado - "maxLength"

Alteração

100

255

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/xCustomerUserAgent

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/items/xCustomerUserAgent

Alterado - "maxLength"

Alteração

100

255

get/responses/200/data/items/xFapiCustomerIpAddress

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

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

get/responses/200/headers

Adicionado - "x-v"

Adição
