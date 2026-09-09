# Changelog - [SV] Pagamentos Automáticos - v2.0.0-beta.2 - v1.0.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/servers/0

Alterado - "url"

Alteração

[https://api.banco.com.br/open-banking/automatic-payments/v1](https://api.banco.com.br/open-banking/automatic-payments/v1)

[https://api.banco.com.br/open-banking/automatic-payments/v2](https://api.banco.com.br/open-banking/automatic-payments/v2)

/servers/1

Alterado - "url"

Alteração

[https://apih.banco.com.br/open-banking/automatic-payments/v1](https://apih.banco.com.br/open-banking/automatic-payments/v1)

[https://apih.banco.com.br/open-banking/automatic-payments/v2](https://apih.banco.com.br/open-banking/automatic-payments/v2)

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

get/responses/200/data/items/document

Alterado - "description"

Alteração

Informações do documento identificador.

Informações do documento.

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500

Removido - "headers"

Remoção

get/responses/504

Removido - "headers"

Remoção

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

post/responses/201/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

post/responses/504

Removido - "headers"

Remoção

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500

Removido - "headers"

Remoção

get/responses/504

Removido - "headers"

Remoção

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

patch/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500

Removido - "headers"

Remoção

patch/responses/504

Removido - "headers"

Remoção

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/requestBody/data/properties

Removido - "startDateTime"

Remoção

post/requestBody/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

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

Adicionado - "firstPayment"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "minimumVariableAmount"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "isRetryAccepted"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDateTime"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/month

Alterado - "description"

Alteração

Mês previstos para ocorrer transações. - JANEIRO - FEVEREIRO - MARCO - ABRIL - MAIO - JUNHO - JULHO - AGOSTO - SETEMBRO - OUTUBRO ...

Mês previstos para ocorrer transações. Caso consentimento seja para pagamentos trimestrais ou semestrais, o campo representa o mês...

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "example"

Alteração

DIARIO

SEMANAL

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "description"

Alteração

Define a periodicidade permitida para realização de transações - DIARIO - SEMANAL - MENSAL - ANUAL

Define a periodicidade permitida para realização de transações - SEMANAL - MENSAL - ANUAL - SEMESTRAL - TRIMESTRAL

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "SEMESTRAL"

Adição

enum

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "TRIMESTRAL"

Adição

enum

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/period/enum

Removido - "DIARIO"

Remoção

enum

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping

Adicionado - "required"

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

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'useOverdraftLimit'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

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

Adicionado - "referenceStartDateTime"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/month

Alterado - "description"

Alteração

Mês previstos para ocorrer transações. - JANEIRO - FEVEREIRO - MARCO - ABRIL - MAIO - JUNHO - JULHO - AGOSTO - SETEMBRO - OUTUBRO ...

Mês previstos para ocorrer transações. Caso consentimento seja para pagamentos trimestrais ou semestrais, o campo representa o mês...

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "example"

Alteração

DIARIO

SEMANAL

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "description"

Alteração

Define a periodicidade permitida para realização de transações - DIARIO - SEMANAL - MENSAL - ANUAL

Define a periodicidade permitida para realização de transações - SEMANAL - MENSAL - ANUAL - SEMESTRAL - TRIMESTRAL

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "SEMESTRAL"

Adição

enum

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "TRIMESTRAL"

Adição

enum

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/period/enum

Removido - "DIARIO"

Remoção

enum

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

post/responses/201/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500

Removido - "headers"

Remoção

post/responses/504

Removido - "headers"

Remoção

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

get/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'useOverdraftLimit'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

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

Adicionado - "referenceStartDateTime"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/month

Alterado - "description"

Alteração

Mês previstos para ocorrer transações. - JANEIRO - FEVEREIRO - MARCO - ABRIL - MAIO - JUNHO - JULHO - AGOSTO - SETEMBRO - OUTUBRO ...

Mês previstos para ocorrer transações. Caso consentimento seja para pagamentos trimestrais ou semestrais, o campo representa o mês...

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "example"

Alteração

DIARIO

SEMANAL

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "description"

Alteração

Define a periodicidade permitida para realização de transações - DIARIO - SEMANAL - MENSAL - ANUAL

Define a periodicidade permitida para realização de transações - SEMANAL - MENSAL - ANUAL - SEMESTRAL - TRIMESTRAL

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "SEMESTRAL"

Adição

enum

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "TRIMESTRAL"

Adição

enum

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/period/enum

Removido - "DIARIO"

Remoção

enum

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

get/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500

Removido - "headers"

Remoção

get/responses/504

Removido - "headers"

Remoção

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

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

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

Removido - "isCallInProgress"

Remoção

patch/requestBody/data/oneOf/0/riskSignals/properties

Adicionado - "isCallingProgress"

Adição

patch/requestBody/data/oneOf/1/properties

Removido - "rejection"

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

patch/requestBody/data/oneOf/1/riskSignals/properties

Removido - "isCallInProgress"

Remoção

patch/requestBody/data/oneOf/1/riskSignals/properties

Adicionado - "isCallingProgress"

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido - "startDateTime"

Remoção

patch/responses/200/data/properties

Adicionado - "authorisedAtDateTime"

Adição

patch/responses/200/data/properties

Adicionado - "updatedAtDateTime"

Adição

patch/responses/200/data/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

Objeto contendo os dados do recebedor (creditor). Em casos de transferências inteligentes para clientes PJ, os CNPJs informados de...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'isRetryAccepted'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'useOverdraftLimit'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "amount"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "transactionLimit"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfMonth"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "dayOfWeek"

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

Adicionado - "referenceStartDateTime"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/month

Alterado - "description"

Alteração

Mês previstos para ocorrer transações. - JANEIRO - FEVEREIRO - MARCO - ABRIL - MAIO - JUNHO - JULHO - AGOSTO - SETEMBRO - OUTUBRO ...

Mês previstos para ocorrer transações. Caso consentimento seja para pagamentos trimestrais ou semestrais, o campo representa o mês...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "example"

Alteração

DIARIO

SEMANAL

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/period

Alterado - "description"

Alteração

Define a periodicidade permitida para realização de transações - DIARIO - SEMANAL - MENSAL - ANUAL

Define a periodicidade permitida para realização de transações - SEMANAL - MENSAL - ANUAL - SEMESTRAL - TRIMESTRAL

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "SEMESTRAL"

Adição

enum

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/period/enum

Adicionado - "TRIMESTRAL"

Adição

enum

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/period/enum

Removido - "DIARIO"

Remoção

enum

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

[https://api.banco.com.br/open-banking/api/v1/resource](https://api.banco.com.br/open-banking/api/v1/resource)

[https://api.banco.com.br/open-banking/api/v2/resource](https://api.banco.com.br/open-banking/api/v2/resource)

patch/responses/200/links/self

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500

Removido - "headers"

Remoção

patch/responses/504

Removido - "headers"

Remoção
