# Changelog - [SV] Pagamentos - v4.0.0-rc.2 - v3.0.0

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

/info

Alterado - "version"

Alteração

3.0.0

4.0.0

/servers/0

Alterado - "url"

Alteração

[https://api.banco.com.br/open-banking/payments/v3](https://api.banco.com.br/open-banking/payments/v3)

[https://api.banco.com.br/open-banking/payments/v4](https://api.banco.com.br/open-banking/payments/v4)

/servers/1

Alterado - "url"

Alteração

[https://apih.banco.com.br/open-banking/payments/v3](https://apih.banco.com.br/open-banking/payments/v3)

[https://apih.banco.com.br/open-banking/payments/v4](https://apih.banco.com.br/open-banking/payments/v4)

paths

Adicionado - "/pix/payments/consents/{consentId}"

Adição

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

\[Restrição\] Se /data/payment/schedule enviado com valor diferente de single durante a criação do consentimento, apenas os métodos MANU, DICT ou QRES são permitidos.

post/requestBody/data/payment/schedule

Adicionado - "description"

Adição

\[Restrição\] Mutuamente excludente com o campo date.  
Este campo é obrigatório no caso de agendamento.  
Neste caso, o campo date não deverá ser informado.  
O prazo máximo para o consentimento deverá ser de dois anos, contando a partir da data de criação do consentimento retornada na criação do mesmo (campo /data/creationDateTime).  
Agendamento de pagamento único deve utilizar exclusivamente o objeto "single".

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

\[Restrição\] Mutuamente excludente com o campo date.

Este campo é obrigatório no caso de agendamento.

Neste caso, o campo date não deve ser informado.

post/requestBody/data/payment/schedule/oneOf/0/single/date

Alterado - "example"

Alteração

01/01/2021

23/08/2023

post/requestBody/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento.

O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

Observação: Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+365 corridos a partir da data do consentimento considerando o fuso horário de Brasília

Define a data alvo da liquidação do pagamento.  
O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em  
relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+730 corridos a  
partir da data do consentimento, também considerando o fuso horário de Brasília.

/data/payment/schedule/daily /startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/Weekly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/monthly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/weekly/dayOfWeek

Adicionado - “description”

Adição

Define o dia da semana planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/dayOfMonth

Adicionado - “description”

Adição

Define o dia do mês planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/quantity

Adicionado - “description”

Adição

Define a quantidade de pagamentos que serão enviados para liquidação.

/data/payment/schedule/custom/dates

Adicionado - “description”

Adição

Define os dias em que estão planejadas as ocorrências das liquidações.

/data/payment/schedule/daily/quantity

Alterado - maximum

Alteração

730

60

/data/payment/schedule/weekly/quantity

Alterado - maximum

Alteração

104

60

/data/payment/schedule/custom/dates

Alterado - MaxItens

Alteração

730

60

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

\[Restrição\] Se /data/payment/schedule enviado com valor diferente de single durante a criação do consentimento, apenas os métodos MANU, DICT ou QRES são permitidos.

post/responses/201/data/payment/schedule

Adicionado - "description"

Adição

\[Restrição\] Mutuamente excludente com o campo date.  
Este campo é obrigatório no caso de agendamento.  
Neste caso, o campo date não deverá ser informado.  
O prazo máximo para o consentimento deverá ser de dois anos, contando a partir da data de criação do consentimento retornada na criação do mesmo (campo /data/creationDateTime).  
Agendamento de pagamento único deve utilizar exclusivamente o objeto "single".

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

\[Restrição\] Mutuamente excludente com o campo date.

Este campo é obrigatório no caso de agendamento.

Neste caso, o campo date não deve ser informado.

post/responses/201/data/payment/schedule/oneOf/0/single/date

Alterado - "example"

Alteração

01/01/2021

23/08/2023

post/responses/201/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento.

O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

Observação: Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+365 corridos a partir da data do consentimento considerando o fuso horário de Brasília

Define a data alvo da liquidação do pagamento.  
O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em  
relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+730 corridos a  
partir da data do consentimento, também considerando o fuso horário de Brasília.

post/responses/201/data/status

Alterado - "description"

Alteração

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION.  
Este estado será alterado depois da autorização do consentimento na detentora da conta do pagador (Debtor) para AUTHORISED ou REJECTED.  
O consentimento fica no estado CONSUMED após ocorrer a iniciação do pagamento referente ao consentimento.   
Em caso de consentimento expirado a detentora deverá retornar o status REJECTED.   
Estados possíveis:   
AWAITING\_AUTHORISATION - Aguardando autorização   
AUTHORISED - Autorizado    
REJECTED - Rejeitado   
CONSUMED - Consumido

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION. Na situação de múltiplas alçadas PARTIALLY\_ACCEPTED, indica que consentimento precisa da confirmação de mais autorizadores. Este estado será alterado depois da(s) autorização(ões) do(s) consentimento(s) na detentora da conta do pagador (Debtor) para AUTHORISED ou REJECTED. O consentimento fica no estado CONSUMED após ocorrer a iniciação do pagamento referente ao consentimento.

Em caso de consentimento expirado a detentora deverá retornar o status REJECTED.

Estados possíveis:

AWAITING\_AUTHORISATION - Aguardando autorização

PARTIALLY\_ACCEPTED – Aguardando múltiplas alçadas

AUTHORISED - Autorizado

REJECTED - Rejeitado

CONSUMED - Consumido

post/responses/201/data/status/enum

Adicionado - "PARTIALLY\_ACCEPTED"

Adição

enum

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

/data/payment/schedule/daily /startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/Weekly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/monthly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/weekly/dayOfWeek

Adicionado - “description”

Adição

Define o dia da semana planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/dayOfMonth

Adicionado - “description”

Adição

Define o dia do mês planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/quantity

Adicionado - “description”

Adição

Define a quantidade de pagamentos que serão enviados para liquidação.

/data/payment/schedule/custom/dates

Adicionado - “description”

Adição

Define os dias em que estão planejadas as ocorrências das liquidações.

/data/payment/schedule/daily/quantity

Alterado - maximum

Alteração

730

60

/data/payment/schedule/weekly/quantity

Alterado - maximum

Alteração

104

60

/data/payment/schedule/custom/dates

Alterado - MaxItens

Alteração

730

60

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

\[Restrição\] Se /data/payment/schedule enviado com valor diferente de single durante a criação do consentimento, apenas os métodos MANU, DICT ou QRES são permitidos.

get/responses/200/data/payment/schedule

Adicionado - "description"

Adição

\[Restrição\] Mutuamente excludente com o campo date.  
Este campo é obrigatório no caso de agendamento.  
Neste caso, o campo date não deverá ser informado.  
O prazo máximo para o consentimento deverá ser de dois anos, contando a partir da data de criação do consentimento retornada na criação do mesmo (campo /data/creationDateTime).  
Agendamento de pagamento único deve utilizar exclusivamente o objeto "single".

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

\[Restrição\] Mutuamente excludente com o campo date.

Este campo é obrigatório no caso de agendamento.

Neste caso, o campo date não deve ser informado.

get/responses/200/data/payment/schedule/oneOf/0/single/date

Alterado - "example"

Alteração

01/01/2021

23/08/2023

get/responses/200/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento.

O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

Observação: Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+365 corridos a partir da data do consentimento considerando o fuso horário de Brasília

Define a data alvo da liquidação do pagamento.  
O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em  
relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+730 corridos a  
partir da data do consentimento, também considerando o fuso horário de Brasília.

get/responses/200/data/status

Alterado - "description"

Alteração

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION.  
Este estado será alterado depois da autorização do consentimento na detentora da conta do pagador (Debtor) para AUTHORISED ou REJECTED.  
O consentimento fica no estado CONSUMED após ocorrer a iniciação do pagamento referente ao consentimento.   
Em caso de consentimento expirado a detentora deverá retornar o status REJECTED.   
Estados possíveis:   
AWAITING\_AUTHORISATION - Aguardando autorização   
AUTHORISED - Autorizado    
REJECTED - Rejeitado   
CONSUMED - Consumido

Retorna o estado do consentimento, o qual no momento de sua criação será AWAITING\_AUTHORISATION. Na situação de múltiplas alçadas PARTIALLY\_ACCEPTED, indica que consentimento precisa da confirmação de mais autorizadores. Este estado será alterado depois da(s) autorização(ões) do(s) consentimento(s) na detentora da conta do pagador (Debtor) para AUTHORISED ou REJECTED. O consentimento fica no estado CONSUMED após ocorrer a iniciação do pagamento referente ao consentimento.

Em caso de consentimento expirado a detentora deverá retornar o status REJECTED.

Estados possíveis:

AWAITING\_AUTHORISATION - Aguardando autorização

PARTIALLY\_ACCEPTED – Aguardando múltiplas alçadas

AUTHORISED - Autorizado

REJECTED - Rejeitado

CONSUMED - Consumido

get/responses/200/data/status/enum

Adicionado - "PARTIALLY\_ACCEPTED"

Adição

enum

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

/data/payment/schedule/daily /startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/Weekly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/monthly/startDate

Adicionado - “description”

Adição

Define o início da vigência da recorrência.

/data/payment/schedule/weekly/dayOfWeek

Adicionado - “description”

Adição

Define o dia da semana planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/dayOfMonth

Adicionado - “description”

Adição

Define o dia do mês planejado para a ocorrência das liquidações.

/data/payment/schedule/monthly/quantity

Adicionado - “description”

Adição

Define a quantidade de pagamentos que serão enviados para liquidação.

/data/payment/schedule/custom/dates

Adicionado - “description”

Adição

Define os dias em que estão planejadas as ocorrências das liquidações.

/data/payment/schedule/daily/quantity

Alterado - maximum

Alteração

730

60

/data/payment/schedule/weekly/quantity

Alterado - maximum

Alteração

104

60

/data/payment/schedule/custom/dates

Alterado - MaxItens

Alteração

730

60

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   COBRANCA\_INVALIDA: Validação de expiração, validação de vencimento, Status Válido.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status não é "authorised" ou está expirado).
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado. 
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   COBRANCA\_INVALIDA: Validação de expiração, validação de vencimento, Status Válido.
    
-   CONSENTIMENTO\_INVALIDO – Consentimento inválido (em status final).
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado. 
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”)
    

post/responses/422/errors/items/code/enum

Adicionado - "CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   COBRANCA\_INVALIDA: Validação de expiração, validação de vencimento ou Status Válido.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado).
    
-   PARAMETRO\_NAO\_INFORMADO: endToEndId
    
-   PARAMETRO\_INVALIDO: endToEndId
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece às regras de negócio.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\].
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\].
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    

Descrição específica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   COBRANCA\_INVALIDA: Validação de expiração, validação de vencimento ou Status Válido.
    
-   CONSENTIMENTO\_INVALIDO – Consentimento inválido (em status final).
    
-   PARAMETRO\_NAO\_INFORMADO: endToEndId
    
-   PARAMETRO\_INVALIDO: endToEndId
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece às regras de negócio.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\].
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\].
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Saldo insuficiente.
    
-   VALOR\_ACIMA\_LIMITE: Acima do limite estabelecido.
    
-   VALOR\_INVALIDO: Valor inválido.
    
-   COBRANCA\_INVALIDA: Cobrança inválida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro com valor inválido.
    
-   NAO\_INFORMADO: Não informado.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Divergência entre pagamento e consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Título específico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Saldo insuficiente.
    
-   VALOR\_ACIMA\_LIMITE: Acima do limite estabelecido.
    
-   VALOR\_INVALIDO: Valor inválido.
    
-   COBRANCA\_INVALIDA: Cobrança inválida.
    
-   CONSENTIMENTO\_INVALIDO – Consentimento inválido (em status final).
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro com valor inválido.
    
-   NAO\_INFORMADO: Não informado.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Divergência entre pagamento e consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

### Response

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

get/responses

Removido - "429"

Remoção

get/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

\[Restrição\] Se /data/payment/schedule enviado com valor diferente de single durante a criação do consentimento, apenas os métodos MANU, DICT ou QRES são permitidos.

get/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Define o código da razão pela qual o pagamento foi rejeitado

-   SALDO\_INSUFICIENTE - A conta selecionada não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE - O valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO - O valor enviado não é válido para o QR Code informado.
    
-   COBRANCA\_INVALIDA - Validação de expiração, validação de vencimento ou Status Válido.
    
-   NAO\_INFORMADO - Não reportado/identificado pela instituição detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO - Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO - Parâmetro \[nome\_campo\] não obedecer às regras de negócio.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA - \[Descrição do motivo de recusa\].
    
-   PAGAMENTO\_RECUSADO\_SPI - \[Código de erro conforme tabela de domínios reason PACS.002\].
    
-   FALHA\_INFRAESTRUTURA - \[Descrição de qual falha na infraestrutura inviabilizou o processamento\].
    
-   FALHA\_INFRAESTRUTURA\_SPI - Indica uma falha no Sistema de Pagamentos Instantâneos (SPI).
    
-   FALHA\_INFRAESTRUTURA\_DICT - Indica uma falha no Diretório de Identificadores de Contas Transacionais (DICT).
    
-   FALHA\_INFRAESTRUTURA\_ICP - Indica uma falha na Infraestrutura de Chaves Públicas (ICP).
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR - Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento.
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA - indica uma falha na infraestrutura da instituição detentora das informações ou recursos.
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS - Indica uma tentativa de pagamento onde a conta origem e a conta de destino são iguais.
    

O rejectionReason FALHA\_INFRAESTRUTURA não será excluído, apenas deixará de ser utilizado, permitindo assim, retrocompatibilidade e integridade entre os participantes.

Define o código da razão pela qual o pagamento foi rejeitado

-   SALDO\_INSUFICIENTE - A conta selecionada não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE - O valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO - O valor enviado não é válido para o QR Code informado.
    
-   COBRANCA\_INVALIDA - Validação de expiração, validação de vencimento ou Status Válido.
    
-   NAO\_INFORMADO - Não reportado/identificado pela instituição detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO - Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO - Parâmetro \[nome\_campo\] não obedecer às regras de negócio.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA - \[Descrição do motivo de recusa\].
    
-   PAGAMENTO\_RECUSADO\_SPI - \[Código de erro conforme tabela de domínios reason PACS.002\].
    
-   FALHA\_INFRAESTRUTURA - \[Descrição de qual falha na infraestrutura inviabilizou o processamento\].
    
-   FALHA\_INFRAESTRUTURA\_SPI - Indica uma falha no Sistema de Pagamentos Instantâneos (SPI).
    
-   FALHA\_INFRAESTRUTURA\_DICT - Indica uma falha no Diretório de Identificadores de Contas Transacionais (DICT).
    
-   FALHA\_INFRAESTRUTURA\_ICP - Indica uma falha na Infraestrutura de Chaves Públicas (ICP).
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR - Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento.
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA - indica uma falha na infraestrutura da instituição detentora das informações ou recursos.
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS - Indica uma tentativa de pagamento onde a conta origem e a conta de destino são iguais.
    
-   FALHA\_AGENDAMENTO\_PAGAMENTOS - Falha ao agendar pagamentos.
    

O rejectionReason FALHA\_INFRAESTRUTURA não será excluído, apenas deixará de ser utilizado, permitindo assim, retrocompatibilidade e integridade entre os participantes.

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FALHA\_AGENDAMENTO\_PAGAMENTOS"

Adição

enum

get/responses/200/data/status

Alterado - "description"

Alteração

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem: 

1.  RCVD (Received) - Indica que a requisição de pagamento foi recebida com sucesso pela detentora, mas ainda há validações a serem feitas antes de ser submetida para liquidação.
    
2.  PATC (Partially Accepted Technical Correct) - Indica que a transação precisa da confirmação de mais autorizadores para que o processamento do pagamento possa prosseguir. 
    
3.  CANC (Cancelled) - Indica que a transação Pix pendente foi cancelada com sucesso pelo usuário antes que fosse confirmada (ACCP) ou rejeitada (RJCT) pela detentora.
    
4.  ACCP( Accepted Customer Profile) - Indica que todas as verificações necessárias já foram realizadas pela detentora e que a transação está pronta para ser enviada para liquidação (no SPI se for Pix para outra instituição ou internamente se for para outra conta na mesma instituição).
    
5.  ACPD (Accepted Clearing Processed) - Indica que a detentora já submeteu a transação para liquidação, mas ainda não tem a confirmação se foi liquidada ou rejeitada.
    
6.  RJCT (Rejected) Indica que a transação foi rejeitada pela detentora ou pelo SPI.
    
7.  ACSC (Accepted Settlement Completed Debitor Account) - Indica que a transação foi efetivada pela detentora ou pelo SPI.
    
8.  PDNG (Pending) - Indica que a detentora reteve temporariamente a transação Pix para análise.
    
9.  SCHD (Scheduled) - Indica que a transação Pix foi agendada com sucesso na detentora.
    

Em caso insucesso:  
   
RJCT (REJECTED) - Instrução de pagamento rejeitada.

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem:

1.  RCVD (Received) - Indica que a requisição de pagamento foi recebida com sucesso pela detentora, mas ainda há validações a serem feitas antes de ser submetida para liquidação.
    
2.  CANC (Cancelled) - Indica que a transação Pix pendente foi cancelada com sucesso pelo usuário antes que fosse confirmada (ACCP) ou rejeitada (RJCT) pela detentora.
    
3.  ACCP( Accepted Customer Profile) - Indica que todas as verificações necessárias já foram realizadas pela detentora e que a transação está pronta para ser enviada para liquidação (no SPI se for Pix para outra instituição ou internamente se for para outra conta na mesma instituição).
    
4.  ACPD (Accepted Clearing Processed) - Indica que a detentora já submeteu a transação para liquidação, mas ainda não tem a confirmação se foi liquidada ou rejeitada.
    
5.  RJCT (Rejected) Indica que a transação foi rejeitada pela detentora ou pelo SPI.
    
6.  ACSC (Accepted Settlement Completed Debitor Account) - Indica que a transação foi efetivada pela detentora ou pelo SPI.
    
7.  PDNG (Pending) - Indica que a detentora reteve temporariamente a transação Pix para análise.
    
8.  SCHD (Scheduled) - Indica que a transação Pix foi agendada com sucesso na detentora.
    

Em caso insucesso:

RJCT (REJECTED) - Instrução de pagamento rejeitada.

get/responses/200/data/status/enum

Removido - "PATC"

Remoção

enum

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Esse endpoint deve ser usado para cancelar, a pedido do cliente pagador, as transações que estejam em uma das seguintes situações: Agendada com sucesso (SCHD), retida para análise (PDNG) ou aguardando autorização de múltiplas alçadas (PATC). 

-   Caso a requisição seja bem sucedida, a transação vai para a situação CANC.
    
-   Caso o status do pagamento seja diferente de SCHD/PDNG/PATC ou alguma outra regra de negócio impeça o cancelamento, a requisição PATCH retorna HTTP Status 422 com o code PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO.
    
-   Caso receba um 422, a iniciadora deve fazer uma requisição GET no pagamento para verificar a situação atual dele, bem como detalhes associados. 
    

O cancelamento de pagamento agendado (SCHD) pode ser enviado até 23:59 (Horário de Brasília) do dia anterior à data de efetivação do pagamento. 

Esse endpoint deve ser usado para cancelar, a pedido do cliente pagador, as transações que estejam em uma das seguintes situações: Agendada com sucesso (SCHD) ou retida para análise (PDNG).

-   Caso a requisição seja bem sucedida, a transação vai para a situação CANC.
    
-   Caso o status do pagamento seja diferente de SCHD/PDNG ou alguma outra regra de negócio impeça o cancelamento, a requisição PATCH retorna HTTP Status 422 com o code PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO.
    
-   Caso receba um 422, a iniciadora deve fazer uma requisição GET no pagamento para verificar a situação atual dele, bem como detalhes associados.
    

O cancelamento de pagamento agendado (SCHD) pode ser enviado até 23:59 (Horário de Brasília) do dia anterior à data de efetivação do pagamento.

patch/parameters/Authorization

Adicionado - "minLength"

Adição

1

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

patch/responses

Removido - "429"

Remoção

patch/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

Especifica a forma de iniciação do pagamento:

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   QRDN - QR code dinâmico
    
-   QRES - QR code estático
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido.
    

\[Restrição\] Se /data/payment/schedule enviado com valor diferente de single durante a criação do consentimento, apenas os métodos MANU, DICT ou QRES são permitidos.

patch/responses/200/data/status

Alterado - "description"

Alteração

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem: 

1.  RCVD (Received) - Indica que a requisição de pagamento foi recebida com sucesso pela detentora, mas ainda há validações a serem feitas antes de ser submetida para liquidação.
    
2.  PATC (Partially Accepted Technical Correct) - Indica que a transação precisa da confirmação de mais autorizadores para que o processamento do pagamento possa prosseguir. 
    
3.  CANC (Cancelled) - Indica que a transação Pix pendente foi cancelada com sucesso pelo usuário antes que fosse confirmada (ACCP) ou rejeitada (RJCT) pela detentora.
    
4.  ACCP( Accepted Customer Profile) - Indica que todas as verificações necessárias já foram realizadas pela detentora e que a transação está pronta para ser enviada para liquidação (no SPI se for Pix para outra instituição ou internamente se for para outra conta na mesma instituição).
    
5.  ACPD (Accepted Clearing Processed) - Indica que a detentora já submeteu a transação para liquidação, mas ainda não tem a confirmação se foi liquidada ou rejeitada.
    
6.  RJCT (Rejected) Indica que a transação foi rejeitada pela detentora ou pelo SPI.
    
7.  ACSC (Accepted Settlement Completed Debitor Account) - Indica que a transação foi efetivada pela detentora ou pelo SPI.
    
8.  PDNG (Pending) - Indica que a detentora reteve temporariamente a transação Pix para análise.
    
9.  SCHD (Scheduled) - Indica que a transação Pix foi agendada com sucesso na detentora.
    

Em caso insucesso:  
   
RJCT (REJECTED) - Instrução de pagamento rejeitada.

Estado atual da iniciação de pagamento. O estado evolui na seguinte ordem:

1.  RCVD (Received) - Indica que a requisição de pagamento foi recebida com sucesso pela detentora, mas ainda há validações a serem feitas antes de ser submetida para liquidação.
    
2.  CANC (Cancelled) - Indica que a transação Pix pendente foi cancelada com sucesso pelo usuário antes que fosse confirmada (ACCP) ou rejeitada (RJCT) pela detentora.
    
3.  ACCP( Accepted Customer Profile) - Indica que todas as verificações necessárias já foram realizadas pela detentora e que a transação está pronta para ser enviada para liquidação (no SPI se for Pix para outra instituição ou internamente se for para outra conta na mesma instituição).
    
4.  ACPD (Accepted Clearing Processed) - Indica que a detentora já submeteu a transação para liquidação, mas ainda não tem a confirmação se foi liquidada ou rejeitada.
    
5.  RJCT (Rejected) Indica que a transação foi rejeitada pela detentora ou pelo SPI.
    
6.  ACSC (Accepted Settlement Completed Debitor Account) - Indica que a transação foi efetivada pela detentora ou pelo SPI.
    
7.  PDNG (Pending) - Indica que a detentora reteve temporariamente a transação Pix para análise.
    
8.  SCHD (Scheduled) - Indica que a transação Pix foi agendada com sucesso na detentora.
    

Em caso insucesso:

RJCT (REJECTED) - Instrução de pagamento rejeitada.

patch/responses/200/data/status/enum

Removido - "PATC"

Remoção

enum

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. A detentora deve obrigatoriamente retornar o campo com o mesmo valor recebido da iniciadora.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela iniciadora (client) e o seu valor deve ser “espelhado” pela detentora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a detentora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP status code 400. A iniciadora deve acatar o valor recebido da detentora.

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

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**
