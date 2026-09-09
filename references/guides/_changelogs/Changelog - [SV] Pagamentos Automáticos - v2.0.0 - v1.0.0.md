# Changelog - [SV] Pagamentos Automáticos - v2.0.0 - v1.0.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

## GET /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters

Adicionado - "originalRecurringPaymentId"

Adição

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/requestBody/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

\[Restrição\] - Se /data/paymentReference = "zero", as informações da conta de crédito enviadas (/data/creditorAccount) devem ser iguais as presentes na conta de crédito informada na criação do consentimento(\`/data/recurringConfiguration/automatic/firstPayment/creditorAccount\`)

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/properties

Adicionado - "originalRecurringPaymentId"

Adição

get/responses/200/data/items/properties

Adicionado - "paymentReference"

Adição

get/responses/200/data/items/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

get/responses/200/data/items/document

Alterado - "description"

Alteração

Informações do documento identificador.

Informações do documento.

get/responses/200/data/items/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

get/responses/200/data/items/endToEndId

Alterado - "description"

Alteração

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

get/responses/200/data/items/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "CONSENTIMENTO\_REVOGADO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "LIMITE\_TENTATIVAS\_EXCEDIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

get/responses/200/data/items/status

Alterado - "description"

Alteração

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

get/responses/200/data/items/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/529

Adicionado - "headers"

Adição

post/responses/201/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

\[Restrição\] - Se /data/paymentReference = "zero", as informações da conta de crédito enviadas (/data/creditorAccount) devem ser iguais as presentes na conta de crédito informada na criação do consentimento(\`/data/recurringConfiguration/automatic/firstPayment/creditorAccount\`)

get/responses/200/data/items/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

get/responses/200/data/items/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

## POST /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/requestBody/data/properties

Adicionado obrigatóriedade no campo 'creditorAccount'

Adição

required

post/requestBody/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

post/requestBody/data/properties

Adicionado - "paymentReference"

Adição

post/requestBody/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor. \[Restrição\] Se localInstrument for igual a MANU,...

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

post/requestBody/data/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

post/requestBody/data/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/requestBody/data/document

Alterado - "description"

Alteração

Informações do documento identificador.

Informações do documento identificador do recebedor da transação.

post/requestBody/data/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do titular pessoa natural ou jurídica.

Número do documento de identificação oficial do recebedor pessoa natural ou jurídica. O valor informado deve ser igual a um dos v...

post/requestBody/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/requestBody/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

post/requestBody/data/proxy

Alterado - "description"

Alteração

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

post/requestBody/data/riskSignals/automatic/lastLoginDateTime

Alterado - "description"

Alteração

Data e hora do último login do cliente na iniciadora

Caso o usuário pagador tenha acesso ao ambiente da iniciadora de pagamentos, utilizar data e hora da última interação do cliente c...

post/requestBody/data/riskSignals/manual/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

post/requestBody/data/riskSignals/manual/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

post/requestBody/data/riskSignals/manual/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

post/requestBody/data/riskSignals/manual/properties

Removido - "isCallInProgress"

Remoção

post/requestBody/data/riskSignals/manual/properties

Adicionado - "isCallingProgress"

Adição

post/requestBody/data/riskSignals/manual/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Restrição\] Campos de envio obrigatório quando o sistema op...

post/requestBody/data/riskSignals/manual/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

post/requestBody/data/riskSignals/manual/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive; Em di...

Indica o nível de brilho da tela do dispositivo. Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive; Em di...

post/requestBody/data/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/requestBody/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/requestBody/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

\[Restrição\] - Se /data/paymentReference = "zero", as informações da conta de crédito enviadas (/data/creditorAccount) devem ser iguais as presentes na conta de crédito informada na criação do consentimento(\`/data/recurringConfiguration/automatic/firstPayment/creditorAccount\`)

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Adicionado obrigatóriedade no campo 'creditorAccount'

Adição

required

post/responses/201/data/properties

Removido - "ibgeTownCode"

Remoção

post/responses/201/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

post/responses/201/data/properties

Adicionado - "paymentReference"

Adição

post/responses/201/data/cancellation/cancelledBy/document/identification

Alterado - "description"

Alteração

Número do documento do usuário pagador responsável pelo cancelamento do pagamento.

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

post/responses/201/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^\\d{11}$

^(?:\\d{11}|\\d{14})$

post/responses/201/data/cancellation/cancelledBy/document/rel

Removido - "maxLength"

Remoção

3

post/responses/201/data/cancellation/cancelledBy/document/rel

Alterado - "description"

Alteração

Tipo do documento do usuário pagador responsável pelo cancelamento do pagamento.

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

post/responses/201/data/cancellation/cancelledBy/document/rel

Removido - "example"

Remoção

CPF

post/responses/201/data/cancellation/cancelledBy/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{3}$

post/responses/201/data/cancellation/cancelledBy/document/rel

Adicionado - "enum"

Adição

post/responses/201/data/cancellation/reason

Alterado - "description"

Alteração

O preenchimento desse campo para retorno, deve ocorrer pela detentora de contas a partir do status em que o pagamento estiver no m...

O preenchimento desse campo para retorno, deve ocorrer pela detentora de contas a partir do status em que o pagamento estiver no m...

post/responses/201/data/cancellation/reason/enum

Removido - "CANCELADO\_MULTIPLAS\_ALCADAS"

Remoção

enum

post/responses/201/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor. \[Restrição\] Se localInstrument for igual a MANU,...

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

post/responses/201/data/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

post/responses/201/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/responses/201/data/document

Alterado - "description"

Alteração

Informações do documento identificador.

Informações do documento identificador do recebedor da transação.

post/responses/201/data/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do titular pessoa natural ou jurídica.

Número do documento de identificação oficial do recebedor pessoa natural ou jurídica. O valor informado deve ser igual a um dos v...

post/responses/201/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/responses/201/data/endToEndId

Alterado - "description"

Alteração

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

post/responses/201/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

Especifica a forma de iniciação do pagamento - MANU - Inserção manual de dados da conta transacional - DICT - Inserção manual de c...

post/responses/201/data/proxy

Alterado - "description"

Alteração

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

post/responses/201/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

post/responses/201/data/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "LIMITE\_TENTATIVAS\_EXCEDIDO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "CONSENTIMENTO\_REVOGADO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

post/responses/201/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

post/responses/201/data/status

Alterado - "description"

Alteração

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

post/responses/201/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

post/responses/201/links/self

Alterado - "format"

Alteração

uri

url

post/responses/201/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

post/responses/201/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

post/responses/201/headers

Adicionado - "x-v"

Adição

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação da iniciação de pagamento: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para...

Códigos de erros previstos na criação da iniciação de pagamento: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para...

post/responses/422/errors/items/code/enum

Adicionado - "LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "LIMITE\_TENTATIVAS\_EXCEDIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para r...

Descrição específica do erro de acordo com o código reportado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para r...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente ...

Título específico do erro reportado, de acordo com o código enviado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente ...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/529

Adicionado - "headers"

Adição

post/responses/201/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

post/responses/201/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

post/responses/201/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

post/responses/201/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

## GET /pix/recurring-payments/{recurringPaymentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/data/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

get/responses/200/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

get/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

get/responses/200/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado obrigatóriedade no campo 'creditorAccount'

Adição

required

get/responses/200/data/properties

Adicionado obrigatóriedade no campo 'localInstrument'

Adição

required

get/responses/200/data/properties

Removido - "ibgeTownCode"

Remoção

get/responses/200/data/properties

Adicionado - "proxy"

Adição

get/responses/200/data/properties

Adicionado - "localInstrument"

Adição

get/responses/200/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

get/responses/200/data/properties

Adicionado - "paymentReference"

Adição

get/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "description"

Alteração

Número do documento do usuário pagador responsável pelo cancelamento do pagamento.

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

get/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^\\d{11}$

^(?:\\d{11}|\\d{14})$

get/responses/200/data/cancellation/cancelledBy/document/rel

Removido - "maxLength"

Remoção

3

get/responses/200/data/cancellation/cancelledBy/document/rel

Alterado - "description"

Alteração

Tipo do documento do usuário pagador responsável pelo cancelamento do pagamento.

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

get/responses/200/data/cancellation/cancelledBy/document/rel

Removido - "example"

Remoção

CPF

get/responses/200/data/cancellation/cancelledBy/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{3}$

get/responses/200/data/cancellation/cancelledBy/document/rel

Adicionado - "enum"

Adição

get/responses/200/data/cancellation/reason

Alterado - "description"

Alteração

O preenchimento desse campo para retorno, deve ocorrer pela detentora de contas a partir do status em que o pagamento estiver no m...

O preenchimento desse campo para retorno, deve ocorrer pela detentora de contas a partir do status em que o pagamento estiver no m...

get/responses/200/data/cancellation/reason/enum

Removido - "CANCELADO\_MULTIPLAS\_ALCADAS"

Remoção

enum

get/responses/200/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

get/responses/200/data/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

get/responses/200/data/date

Alterado - "description"

Alteração

Data em que o pagamento será realizado.

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

get/responses/200/data/document

Alterado - "description"

Alteração

Informações do documento identificador.

Informações do documento identificador do recebedor da transação.

get/responses/200/data/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do titular pessoa natural ou jurídica.

Número do documento de identificação oficial do recebedor pessoa natural ou jurídica. O valor informado deve ser igual a um dos v...

get/responses/200/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

get/responses/200/data/endToEndId

Alterado - "description"

Alteração

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

get/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

get/responses/200/data/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "LIMITE\_TENTATIVAS\_EXCEDIDO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "CONSENTIMENTO\_REVOGADO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

get/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

get/responses/200/data/status

Alterado - "description"

Alteração

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

get/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/529

Adicionado - "headers"

Adição

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Esse endpoint deve ser usado para cancelar as transações que estejam em uma das seguintes situações: Agendada com sucesso (SCHD),...

Esse endpoint deve ser usado para cancelar as transações que estejam em uma das seguintes situações: Agendada com sucesso (SCHD),...

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/requestBody/data/cancellation/cancelledBy/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do usuário.

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica

patch/requestBody/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^\\d{11}$

^(?:\\d{11}|\\d{14})$

patch/requestBody/data/cancellation/cancelledBy/document/rel

Removido - "maxLength"

Remoção

3

patch/requestBody/data/cancellation/cancelledBy/document/rel

Alterado - "description"

Alteração

Tipo do documento de identificação oficial do usuário.

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

patch/requestBody/data/cancellation/cancelledBy/document/rel

Removido - "example"

Remoção

CPF

patch/requestBody/data/cancellation/cancelledBy/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{3}$

patch/requestBody/data/cancellation/cancelledBy/document/rel

Adicionado - "enum"

Adição

patch/requestBody/data/status

Alterado - "example"

Alteração

REJECTED

CANC

patch/requestBody/data/status/enum

Adicionado - "CANC"

Adição

enum

patch/requestBody/data/status/enum

Removido - "REJECTED"

Remoção

enum

patch/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Adicionado obrigatóriedade no campo 'creditorAccount'

Adição

required

patch/responses/200/data/properties

Adicionado obrigatóriedade no campo 'localInstrument'

Adição

required

patch/responses/200/data/properties

Removido - "ibgeTownCode"

Remoção

patch/responses/200/data/properties

Adicionado - "proxy"

Adição

patch/responses/200/data/properties

Adicionado - "localInstrument"

Adição

patch/responses/200/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

patch/responses/200/data/properties

Adicionado - "paymentReference"

Adição

patch/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "description"

Alteração

Número do documento do usuário pagador responsável pelo cancelamento do pagamento.

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

patch/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^\\d{11}$

^(?:\\d{11}|\\d{14})$

patch/responses/200/data/cancellation/cancelledBy/document/rel

Removido - "maxLength"

Remoção

3

patch/responses/200/data/cancellation/cancelledBy/document/rel

Alterado - "description"

Alteração

Tipo do documento do usuário pagador responsável pelo cancelamento do pagamento.

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

patch/responses/200/data/cancellation/cancelledBy/document/rel

Removido - "example"

Remoção

CPF

patch/responses/200/data/cancellation/cancelledBy/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{3}$

patch/responses/200/data/cancellation/cancelledBy/document/rel

Adicionado - "enum"

Adição

patch/responses/200/data/cancellation/reason

Alterado - "description"

Alteração

O preenchimento desse campo para retorno, deve ocorrer pela detentora de contas a partir do status em que o pagamento estiver no m...

O preenchimento desse campo para retorno, deve ocorrer pela detentora de contas a partir do status em que o pagamento estiver no m...

patch/responses/200/data/cancellation/reason/enum

Removido - "CANCELADO\_MULTIPLAS\_ALCADAS"

Remoção

enum

patch/responses/200/data/creditorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.

patch/responses/200/data/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

patch/responses/200/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

patch/responses/200/data/document

Alterado - "description"

Alteração

Informações do documento identificador.

Informações do documento identificador do recebedor da transação.

patch/responses/200/data/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do titular pessoa natural ou jurídica.

Número do documento de identificação oficial do recebedor pessoa natural ou jurídica. O valor informado deve ser igual a um dos v...

patch/responses/200/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

patch/responses/200/data/endToEndId

Alterado - "description"

Alteração

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

patch/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "LIMITE\_TENTATIVAS\_EXCEDIDO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "CONSENTIMENTO\_REVOGADO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

patch/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

patch/responses/200/data/status

Alterado - "description"

Alteração

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

Estado atual do pagamento. O estado evolui na seguinte ordem: - RCVD (Received) - Indica que a requisição de pagamento foi recebid...

patch/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

patch/responses/200/links/self

Alterado - "format"

Alteração

uri

url

patch/responses/200/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

patch/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

patch/responses/200/headers

Adicionado - "x-v"

Adição

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/529

Adicionado - "headers"

Adição

patch/responses/200/data/date

Alterado - "description"

Alteração

Data em que o recurso foi criado. Uma string com a utilização de timezone UTC(UTC time format).

Data em que o pagamento será realizado. Uma string com a utilização de timezone UTC-3 (UTC time format).

patch/responses/200/data/endToEndId

Alterado - "example"

Alteração

E9040088820210128000800123873170

E9040088820241225150000123873170

patch/requestBody/data/cancellation/cancelledBy/document/identification

Alterado - "maxLength"

Alteração

11

14

patch/responses/200/data/debtorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

patch/responses/422/errors/items/code

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/requestBody/data/properties

Removido - "startDateTime"

Remoção

post/requestBody/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

Adição

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDate'

Adição

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'period'

Remoção

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "period"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "immediatePayment"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "fixedAmount"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "maximumVariableAmount"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "interval"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "firstPayment"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "minimumVariableAmount"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "isRetryAccepted"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

post/requestBody/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1 - Para clientes pessoa física/natural: Deve aceitar apenas um item no array; e; O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.

2 - Para clientes pessoa jurídica: Não há limite para quantidade de itens no array; e; O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`

\*\*Regras para Pix Automático:\*\*

Apenas um item é permitido no array; e; O documento informado deve ser de um recebedor pessoa jurídica

post/requestBody/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador.  
As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente. Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

Objeto que contém a identificação da conta de origem do pagador.  
Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou; Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.  
Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

post/requestBody/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

post/requestBody/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador.  
As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente. Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

post/requestBody/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido - "startDateTime"

Remoção

post/responses/201/data/properties

Adicionado - "authorisedAtDateTime"

Adição

post/responses/201/data/properties

Adicionado - "updatedAtDateTime"

Adição

post/responses/201/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

post/responses/201/data/debtorAccount/properties

Removido - "ibgeTownCode"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'useOverdraftLimit'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDate'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'period'

Remoção

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "period"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "immediatePayment"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "fixedAmount"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "maximumVariableAmount"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "interval"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "firstPayment"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "minimumVariableAmount"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "isRetryAccepted"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "useOverdraftLimit"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping

Adicionado - "required"

Adição

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "useOverdraftLimit"

Adição

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

post/responses/201/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

post/responses/201/data/rejection/reason/code/enum

Adicionado - "AUTENTICACAO\_DIVERGENTE"

Adição

enum

post/responses/201/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

post/responses/201/data/statusUpdateDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento teve o status atualizado. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

post/responses/201/links/self

Alterado - "format"

Alteração

uri

url

post/responses/201/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

post/responses/201/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

post/responses/201/headers

Adicionado - "x-v"

Adição

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/529

Adicionado - "headers"

Adição

post/responses/201

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

post/responses/201/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1 - Para clientes pessoa física/natural: Deve aceitar apenas um item no array; e; O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.

2 - Para clientes pessoa jurídica: Não há limite para quantidade de itens no array; e; O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`

\*\*Regras para Pix Automático:\*\*

Apenas um item é permitido no array; e; O documento informado deve ser de um recebedor pessoa jurídica

post/responses/201/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.  
Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou; Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.  
Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

post/responses/201/data/statusUpdateDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado pelo iniciador na requisição, o detentor deve preencher esse campo com o mesmo valor atribuído ao campo /data/creationDateTime. Caso o campo /data/startDateTime enviado seja anterior ao valor do campo /data/creationDateTime, o detentor deve substituir o valor do campo /data/startDateTime pelo valor do campo /data/creationDateTime

Data e hora em que o consentimento teve o status atualizado. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

post/responses/201/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

post/responses/201/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

post/responses/201/data/statusUpdateDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado pelo iniciador na requisição, o detentor deve preencher esse campo com o mesmo valor atribuído ao campo /data/creationDateTime. Caso o campo /data/startDateTime enviado seja anterior ao valor do campo /data/creationDateTime, o detentor deve substituir o valor do campo /data/startDateTime pelo valor do campo /data/creationDateTime

Data e hora em que o consentimento teve o status atualizado. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

post/responses/201

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

## GET /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido - "startDateTime"

Remoção

get/responses/200/data/properties

Adicionado - "authorisedAtDateTime"

Adição

get/responses/200/data/properties

Adicionado - "updatedAtDateTime"

Adição

get/responses/200/data/properties

Adicionado - "approvalDueDate"

Adição

get/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

get/responses/200/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'useOverdraftLimit'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDate'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'period'

Remoção

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "period"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "immediatePayment"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "fixedAmount"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "maximumVariableAmount"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "interval"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "firstPayment"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "minimumVariableAmount"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "isRetryAccepted"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "useOverdraftLimit"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping

Adicionado - "required"

Adição

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "useOverdraftLimit"

Adição

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

get/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

get/responses/200/data/rejection/reason/code/enum

Adicionado - "AUTENTICACAO\_DIVERGENTE"

Adição

enum

get/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

get/responses/200/data/riskSignals/properties

Removido - "isCallInProgress"

Remoção

get/responses/200/data/riskSignals/properties

Adicionado - "isCallingProgress"

Adição

get/responses/200/links/self

Alterado - "format"

Alteração

uri

url

get/responses/200/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/529

Adicionado - "headers"

Adição

get/responses/200

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

get/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1 - Para clientes pessoa física/natural: Deve aceitar apenas um item no array; e; O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.

2 - Para clientes pessoa jurídica: Não há limite para quantidade de itens no array; e; O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`

\*\*Regras para Pix Automático:\*\*

Apenas um item é permitido no array; e; O documento informado deve ser de um recebedor pessoa jurídica

get/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.  
Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou; Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.  
Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/minimumVariableAmount

Alterado - "description"

Alteração

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização, ele ...

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização (camp...

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

get/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

get/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

get/responses/200

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

get/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/requestBody/data

Alterado - "description"

Alteração

Objeto contendo as informações de rejeição e revogação dos consentimentos

Objeto contendo as informações de rejeição, revogação e edição dos consentimentos

patch/requestBody/data/oneOf

Alterado - "length"

Alteração

2

3

patch/requestBody/data/oneOf

Adicionado - "2"

Adição

patch/requestBody/data/oneOf/0

Adicionado - "required"

Adição

patch/requestBody/data/oneOf/0/properties

Removido - "status"

Remoção

patch/requestBody/data/oneOf/0/properties

Removido - "revocation"

Remoção

patch/requestBody/data/oneOf/0/properties

Removido - "startDateTime"

Remoção

patch/requestBody/data/oneOf/0/properties

Removido - "automatic"

Remoção

patch/requestBody/data/oneOf/0/properties

Adicionado - "recurringConfiguration"

Adição

patch/requestBody/data/oneOf/0/properties

Adicionado - "loggedUser"

Adição

patch/requestBody/data/oneOf/0/properties

Adicionado - "businessEntity"

Adição

patch/requestBody/data/oneOf/0/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). \[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Autom...

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https:/...

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https:/...

patch/requestBody/data/oneOf/0/riskSignals/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

patch/requestBody/data/oneOf/0/riskSignals/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

patch/requestBody/data/oneOf/0/riskSignals/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

patch/requestBody/data/oneOf/0/riskSignals/properties

Removido - "isCallInProgress"

Remoção

patch/requestBody/data/oneOf/0/riskSignals/properties

Adicionado - "isCallingProgress"

Adição

patch/requestBody/data/oneOf/0/riskSignals/antennaInformation

Adicionado - "example"

Adição

CellIdentityLte:{ mCi=2\*\*\*\*\*\*60 mPci=274 mTac=5\*\*\*1 mEarfcn=9510 mBands=\[28\] mBandwidth=2147483647 mMcc=724 mMnc=10 mAlphaLong=VIV...

patch/requestBody/data/oneOf/0/riskSignals/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

ID único do dispositivo gerado pela plataforma. \[Android\] Informação obtida através do \[link\](https://developer.android.com/refer...

patch/requestBody/data/oneOf/0/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\](https://devel...

patch/requestBody/data/oneOf/0/riskSignals/geolocation

Alterado - "description"

Alteração

Dados de geolocalização do cliente enquanto logado na iniciadora

Localização do usuário, obtida com seu consentimento. \[Android\] Informação obtida através do \[link\](https://developers.google.com...

patch/requestBody/data/oneOf/0/riskSignals/integrity/appRecognitionVerdict

Adicionado - "example"

Adição

PLAY\_RECOGNIZED

patch/requestBody/data/oneOf/0/riskSignals/integrity/deviceRecognitionVerdict

Adicionado - "example"

Adição

\[\\"MEETS\_DEVICE\_INTEGRITY\\"\]

patch/requestBody/data/oneOf/0/riskSignals/isCharging

Alterado - "description"

Alteração

Indica se a bateria do dispositivo está sendo carregada.

Indica se a bateria do dispositivo está sendo carregada. \[Android\] Informação obtida através do \[link\](https://developer.android....

patch/requestBody/data/oneOf/0/riskSignals/isMockGPS

Alterado - "description"

Alteração

Indica se o dispositivo está usando um GPS falso.

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo COARSE ou FINE. ...

patch/requestBody/data/oneOf/0/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

patch/requestBody/data/oneOf/0/riskSignals/language

Alterado - "description"

Alteração

Indica o idioma do dispositivo no formato ISO 639-1.

Indica o idioma do dispositivo no formato ISO 639-1. \[Android\] Informação obtida através do \[link\](https://developer.android.com/...

patch/requestBody/data/oneOf/0/riskSignals/osVersion

Alterado - "description"

Alteração

Versão do sistema operacional.

Versão do sistema operacional. \[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/B...

patch/requestBody/data/oneOf/0/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive; Em di...

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

patch/requestBody/data/oneOf/0/riskSignals/screenDimensions

Alterado - "description"

Alteração

Dimensões da tela do dispositivo

Dimensões que o aplicativo ocupa na tela do dispositivo. \[Android\] Informação obtida através do \[link\](https://developer.android....

patch/requestBody/data/oneOf/0/riskSignals/userTimeZoneOffset

Alterado - "description"

Alteração

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permit...

patch/requestBody/data/oneOf/1/properties

Removido - "rejection"

Remoção

patch/requestBody/data/oneOf/1/properties

Removido - "riskSignals"

Remoção

patch/requestBody/data/oneOf/1/properties

Removido - "creditors"

Remoção

patch/requestBody/data/oneOf/1/properties

Removido - "startDateTime"

Remoção

patch/requestBody/data/oneOf/1/properties

Removido - "expirationDateTime"

Remoção

patch/requestBody/data/oneOf/1/properties

Removido - "automatic"

Remoção

patch/requestBody/data/oneOf/1/properties

Adicionado - "revocation"

Adição

patch/requestBody/data/oneOf/1/status

Alterado - "example"

Alteração

REJECTED

REVOKED

patch/requestBody/data/oneOf/1/status/enum

Adicionado - "REVOKED"

Adição

enum

patch/requestBody/data/oneOf/1/status/enum

Removido - "REJECTED"

Remoção

enum

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

Número do documento de identificação oficial do usuário logado na instituição iniciadora.

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\\d{11})$

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Alterado - "description"

Alteração

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

Tipo do documento de identificação oficial do usuário logado na instituição iniciadora.

patch/requestBody/data/oneOf/0/loggedUser/document/rel/enum

Removido - "CNPJ"

Remoção

enum

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

Número do documento de identificação oficial do usuário logado na instituição iniciadora.

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\\d{11})$

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Alterado - "description"

Alteração

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

Tipo do documento de identificação oficial do usuário logado na instituição iniciadora.

patch/requestBody/data/oneOf/0/loggedUser/document/rel/enum

Removido - "CNPJ"

Remoção

enum

patch/requestBody/data/oneOf/0/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um período indeterminado; ou;

Caso enviado, esse campo deve ser, no mínimo, D, sendo D o dia da requisição.

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um período indeterminado; ou;

Caso enviado, esse campo deve ser, no mínimo, D, sendo D o dia da requisição e o horário deve ser às 23:59:59 (UTC).

patch/requestBody/data/oneOf/0/riskSignals

Alterado - "description"

Alteração

Sinais de risco para iniciação de pagamentos automáticos \[Restrição\] Deve ser enviado quando o consentimento for para o produto P...

Sinais de risco para iniciação de pagamentos automáticos \[Restrição\] Deve ser enviado quando o consentimento for para o produto P...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido obrigatóriedade no campo 'loggedUser'

Remoção

required

patch/responses/200/data/properties

Removido - "startDateTime"

Remoção

patch/responses/200/data/properties

Adicionado - "authorisedAtDateTime"

Adição

patch/responses/200/data/properties

Adicionado - "updatedAtDateTime"

Adição

patch/responses/200/data/properties

Adicionado - "approvalDueDate"

Adição

patch/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

patch/responses/200/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'useOverdraftLimit'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDate'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'period'

Remoção

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "period"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "immediatePayment"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "fixedAmount"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "maximumVariableAmount"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "interval"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "firstPayment"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "minimumVariableAmount"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "isRetryAccepted"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "useOverdraftLimit"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping

Adicionado - "required"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "useOverdraftLimit"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/day/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/month/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/week/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/recurringConfiguration/oneOf/2/vrp/periodicLimits/year/quantityLimit

Adicionado - "minimum"

Adição

1

patch/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

patch/responses/200/data/rejection/reason/code/enum

Adicionado - "AUTENTICACAO\_DIVERGENTE"

Adição

enum

patch/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

patch/responses/200/data/riskSignals/properties

Removido - "isCallInProgress"

Remoção

patch/responses/200/data/riskSignals/properties

Adicionado - "isCallingProgress"

Adição

patch/responses/200/links/self

Alterado - "format"

Alteração

uri

url

patch/responses/200/links/self

Alterado - "example"

Alteração

https://api.banco.com.br/open-banking/api/v1/resource

https://api.banco.com.br/open-banking/api/v2/resource

patch/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

patch/responses/200/headers

Adicionado - "x-v"

Adição

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/errors/items/code/enum

Adicionado - "PERMISSAO\_INSUFICIENTE"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "DETALHE\_EDICAO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "FALTAM\_SINAIS\_OBRIGATORIOS\_PLATAFORMA"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do consentimen...

Descrição específica do erro de acordo com o código reportado: - CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do consentimen...

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do conse...

Título específico do erro reportado, de acordo com o código enviado: - CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do conse...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\](https://tools.ietf.org/html/rfc4122) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/529

Adicionado - "headers"

Adição

patch/responses/200

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

patch/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1 - Para clientes pessoa física/natural: Deve aceitar apenas um item no array; e; O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.

2 - Para clientes pessoa jurídica: Não há limite para quantidade de itens no array; e; O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`

\*\*Regras para Pix Automático:\*\*

Apenas um item é permitido no array; e; O documento informado deve ser de um recebedor pessoa jurídica

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/minimumVariableAmount

Alterado - "description"

Alteração

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização, ele ...

Valor definido pelo usuário recebedor. Se o usuário pagador atribuir um valor máximo para os pagamentos daquela autorização (camp...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor, este deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”. A conta de crédito informada no momento do primeiro pagamento deve ser a mesma informada dentro deste objeto. Caso não respeitado, o detentor deve rejeitar o pagamento com o motivo DETALHE\_PAGAMENTO\_INVALIDO, sincronamente (HTTP 422) ou assincronamente (HTTP 200).

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador.

\[Restrição\] Para casos em que conta recebedora e conta pagadora pertencem ao mesmo detentor (/data/debtorAccount/ispb = /data/recurringConfiguration/automatic/firstPayment/creditorAccount/ispb), o detentor deve garantir que a conta de crédito informada pertence ao titular do CNPJ enviado no campo “/data/creditors/cpfCnpj”.

patch/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados devem possuir a mesma raiz do CNPJ enviado no campo /data/businessEntity/document/identification. Em casos de transferências inteligentes para clientes PN, deve-se aceitar apenas um item no array e este item deve conter as informações do recebedor. O CPF informado deve ser o mesmo do /data/loggedUser/document/identification. Caso alguma das regras mencionadas não sejam seguidas, o detentor deve rejeitar a solicitação (sincronamente) com o erro DETALHE\_PAGAMENTO\_INVALIDO, e o detalhe deve ser preenchido com a informação referente ao erro.

\[Restrição\] Caso o consentimento de longa duração seja para o produto Pix Automático (“automatic” selecionado no oneOf do objeto “/data/recurringConfiguration”), apenas um recebedor é permitido e esse deve ser pessoa jurídica.

Objeto contendo os dados do recebedor (creditor).

\*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

\*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

patch/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser trazidas no consentimento para a detentora, caso a iniciadora tenha coletado essas informações do cliente.  
Do contrário, será coletada na detentora e trazida para a iniciadora como resposta à criação do pagamento.

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

Objeto que contém a identificação da conta de origem do pagador.

-   Caso a ITP tenha coletado as informações de conta do usuário pagador, essas poderão ser enviadas no consentimento para a detentora neste objeto, ou;
    
-   Se não coletado pelo ITP, o usuário pagador precisará definir durante a autorização do consentimento.
    
-   Mesmo se enviado pela ITP, o usuário pagador pode alterar durante a autorização do consentimento.
    

\[Restrições\]

-   Objeto obrigatório que deverá ser retornado quando o consentimento estiver ou passar pelo status AUTHORISED;
    

patch/responses/200

Alterado - "description"

Alteração

Objeto contendo as informações de consentimento para a iniciação de pagamento individual.

Objeto contendo as informações de consentimento para iniciação de pagamento automático.

patch/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC (UTC time format).

\[Restrição\] Caso o consentimento seja para Pix Automático ("automatic" selecionado no oneOf "/data/recurringConfiguration/") o horário de expiração do consentimento precisa ser às 23:59:59 (UTC).

patch/responses/422/errors/items/code

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
    

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    

-   PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO: Pagamento está com um status que não permite cancelamento.
    
-   CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO: O usuário solicitou o cancelamento fora da janela de tempo permitido.
    
-   PARAMETRO\_INVALIDO: Os parâmetros informados não obedecem a formatação especificada.
    
-   PARAMETRO\_NAO\_INFORMADO: Algum ou todos os campos obrigatórios não foram informados.
