# Changelog - [SV] Pagamentos - v4.0.0 - v3.0.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos, responsável por viabilizar as operações de iniciação de pagamentos para o Open Finance Brasil. Par...

API de Iniciação de Pagamentos, responsável por viabilizar as operações de iniciação de pagamentos para o Open Finance Brasil. Par...

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/Authorization

Adicionado - "minLength"

Adição

1

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-idempotency-key

Adicionado - "minLength"

Adição

1

post/requestBody/data

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para a iniciação de pagamento.

post/requestBody/data/payment/details/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

post/requestBody/data/payment/schedule

Adicionado - "description"

Adição

\[Restrição\] Mutuamente excludente com o campo date. Este campo é obrigatório no caso de agendamento. Neste caso, o campo date nã...

post/requestBody/data/payment/schedule/oneOf

Alterado - "length"

Alteração

1

5

post/requestBody/data/payment/schedule/oneOf

Adicionado - "1"

Adição

post/requestBody/data/payment/schedule/oneOf

Adicionado - "2"

Adição

post/requestBody/data/payment/schedule/oneOf

Adicionado - "3"

Adição

post/requestBody/data/payment/schedule/oneOf

Adicionado - "4"

Adição

post/requestBody/data/payment/schedule/oneOf/0

Removido - "description"

Remoção

\[Restrição\] Mutuamente excludente com o campo date. Este campo é obrigatório no caso de agendamento. Neste caso, o campo date ...

post/requestBody/data/payment/schedule/oneOf/0/single/date

Alterado - "example"

Alteração

2021-01-01

2023-08-23

post/requestBody/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre...

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre o...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/201/data

Alterado - "description"

Alteração

Objeto contendo as informações de resposta do consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para a iniciação de pagamento.

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento da iniciação de pagamento expira, devendo ser sempre o creationDateTime mais 5 minutos. Uma str...

Data e hora em que o consentimento da iniciação de pagamento expira. Para consentimentos em status AWAITING\_AUTHORISATION, deve s...

post/responses/201/data/payment/details/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

post/responses/201/data/payment/schedule

Adicionado - "description"

Adição

\[Restrição\] Mutuamente excludente com o campo date. Este campo é obrigatório no caso de agendamento. Neste caso, o campo date nã...

post/responses/201/data/payment/schedule/oneOf

Alterado - "length"

Alteração

1

5

post/responses/201/data/payment/schedule/oneOf

Adicionado - "1"

Adição

post/responses/201/data/payment/schedule/oneOf

Adicionado - "2"

Adição

post/responses/201/data/payment/schedule/oneOf

Adicionado - "3"

Adição

post/responses/201/data/payment/schedule/oneOf

Adicionado - "4"

Adição

post/responses/201/data/payment/schedule/oneOf/0

Removido - "description"

Remoção

\[Restrição\] Mutuamente excludente com o campo date. Este campo é obrigatório no caso de agendamento. Neste caso, o campo date ...

post/responses/201/data/payment/schedule/oneOf/0/single/date

Alterado - "example"

Alteração

2021-01-01

2023-08-23

post/responses/201/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre...

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre o...

post/responses/201/data/status

Alterado - "description"

Alteração

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION. Este estado será alterado depois ...

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION. Na situação de múltiplas alçadas ...

post/responses/201/data/status/enum

Adicionado - "PARTIALLY\_ACCEPTED"

Adição

enum

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

## GET /consents/{consentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/Authorization

Adicionado - "minLength"

Adição

1

get/parameters/consentId

Adicionado - "minLength"

Adição

1

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

get/responses

Removido - "429"

Remoção

get/responses/200/data

Alterado - "description"

Alteração

Objeto contendo as informações de resposta do consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para a iniciação de pagamento.

get/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento da iniciação de pagamento expira, devendo ser sempre o creationDateTime mais 5 minutos. Uma str...

Data e hora em que o consentimento da iniciação de pagamento expira. Para consentimentos em status AWAITING\_AUTHORISATION, deve s...

get/responses/200/data/payment/details/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

get/responses/200/data/payment/schedule

Adicionado - "description"

Adição

\[Restrição\] Mutuamente excludente com o campo date. Este campo é obrigatório no caso de agendamento. Neste caso, o campo date nã...

get/responses/200/data/payment/schedule/oneOf

Alterado - "length"

Alteração

1

5

get/responses/200/data/payment/schedule/oneOf

Adicionado - "1"

Adição

get/responses/200/data/payment/schedule/oneOf

Adicionado - "2"

Adição

get/responses/200/data/payment/schedule/oneOf

Adicionado - "3"

Adição

get/responses/200/data/payment/schedule/oneOf

Adicionado - "4"

Adição

get/responses/200/data/payment/schedule/oneOf/0

Removido - "description"

Remoção

\[Restrição\] Mutuamente excludente com o campo date. Este campo é obrigatório no caso de agendamento. Neste caso, o campo date ...

get/responses/200/data/payment/schedule/oneOf/0/single/date

Alterado - "example"

Alteração

2021-01-01

2023-08-23

get/responses/200/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre...

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre o...

get/responses/200/data/status

Alterado - "description"

Alteração

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION. Este estado será alterado depois ...

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION. Na situação de múltiplas alçadas ...

get/responses/200/data/status/enum

Adicionado - "PARTIALLY\_ACCEPTED"

Adição

enum

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

## POST /pix/payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/Authorization

Adicionado - "minLength"

Adição

1

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/parameters/x-idempotency-key

Adicionado - "minLength"

Adição

1

post/requestBody/data

Alterado - "type"

Alteração

object

array

post/requestBody/data

Removido - "description"

Remoção

Objeto contendo dados do pagamento e do recebedor (creditor).

post/requestBody/data

Removido - "required"

Remoção

post/requestBody/data

Removido - "properties"

Remoção

post/requestBody/data

Adicionado - "minItems"

Adição

1

post/requestBody/data

Adicionado - "items"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Removido - "429"

Remoção

post/responses/201/data

Alterado - "type"

Alteração

object

array

post/responses/201/data

Removido - "description"

Remoção

Objeto contendo dados do pagamento e da conta do recebedor (creditor).

post/responses/201/data

Removido - "required"

Remoção

post/responses/201/data

Removido - "properties"

Remoção

post/responses/201/data

Adicionado - "items"

Adição

post/responses/201/links/self

Alterado - "description"

Alteração

URI completo que gerou a resposta atual.

URI completo para o primeiro item presente na resposta.

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/201/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/415/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/415/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/415/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação da iniciação de pagamento: • SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente par...

Códigos de erros previstos na criação da iniciação de pagamento: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para...

post/responses/422/errors/items/code/enum

Adicionado - "CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficie...

Descrição específica do erro de acordo com o código reportado: - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficien...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • SALDO\_INSUFICIENTE: Saldo insuficiente. • VALOR\_ACIMA\_LIM...

Título específico do erro reportado, de acordo com o código enviado: - SALDO\_INSUFICIENTE: Saldo insuficiente. - VALOR\_ACIMA\_LIMIT...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

post/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

post/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

post/security

Alterado - "length"

Alteração

1

2

post/security

Adicionado - "1"

Adição

## GET /pix/payments/{paymentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/Authorization

Adicionado - "minLength"

Adição

1

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

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

get/responses

Removido - "429"

Remoção

get/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

get/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Define o código da razão pela qual o pagamento foi rejeitado - SALDO\_INSUFICIENTE - A conta selecionada não possui saldo suficien...

Define o código da razão pela qual o pagamento foi rejeitado - SALDO\_INSUFICIENTE - A conta selecionada não possui saldo suficien...

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_AGENDAMENTO\_PAGAMENTOS"

Adição

enum

get/responses/200/data/status

Alterado - "description"

Alteração

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem: 1. RCVD (Received) - Indica que a requisição de pag...

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem: 1. RCVD (Received) - Indica que a requisição de pagam...

get/responses/200/data/status/enum

Removido - "PATC"

Remoção

enum

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

## PATCH pix/payments/{paymentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Esse endpoint deve ser usado para cancelar, a pedido do cliente pagador, as transações que estejam em uma das seguintes situações...

Esse endpoint deve ser usado para cancelar, a pedido do cliente pagador, as transações que estejam em uma das seguintes situações:...

patch/parameters/Authorization

Adicionado - "minLength"

Adição

1

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses

Removido - "429"

Remoção

patch/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

Especifica a forma de iniciação do pagamento: - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de ...

patch/responses/200/data/status

Alterado - "description"

Alteração

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem: 1. RCVD (Received) - Indica que a requisição de pag...

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem: 1. RCVD (Received) - Indica que a requisição de pagam...

patch/responses/200/data/status/enum

Removido - "PATC"

Remoção

enum

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/400/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/400/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/401/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/401/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/403/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/403/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/404/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/404/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/405/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/405/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/406/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/406/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/422/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/422/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

patch/responses/500/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

patch/responses/500/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

## PATCH pix/payments/consents/{consentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

endpoint

Adicionado - "/pix/payments/consents/{consentId}"

Adição
