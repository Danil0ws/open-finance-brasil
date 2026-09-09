# Changelog - [SV] Pagamentos Automáticos - v2.0.0-rc.1 - v2.0.0-beta.2

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/500

Adicionado - "headers"

Adição

get/responses/504

Adicionado - "headers"

Adição

get/responses/529

Adicionado - "headers"

Adição

## POST /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

post/responses/201/data/endToEndId

Alterado - "description"

Alteração

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

Trata-se de um identificador único, gerado na instituição iniciadora de pagamento e recebido na instituição detentora de conta, pe...

post/responses/201/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

post/responses/201/data/rejectionReason/code/enum

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

post/responses/201/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

post/responses/201/headers

Adicionado - "x-v"

Adição

post/responses/500

Adicionado - "headers"

Adição

post/responses/504

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

get/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/500

Adicionado - "headers"

Adição

get/responses/504

Adicionado - "headers"

Adição

get/responses/529

Adicionado - "headers"

Adição

## PATH /pix/recurring-payments/{recurringPaymentId}

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

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

Adicionado - "DETALHE\_PAGAMENTO\_INVALIDO"

Adição

enum

patch/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

patch/responses/200/headers

Adicionado - "x-v"

Adição

patch/responses/500

Adicionado - "headers"

Adição

patch/responses/504

Adicionado - "headers"

Adição

patch/responses/529

Adicionado - "headers"

Adição

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

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

Removido obrigatóriedade no campo 'referenceStartDateTime'

Remoção

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "referenceStartDateTime"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. - A conta de créd...

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que ...

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping

Removido - "required"

Remoção

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/debtorAccount/properties

Removido - "ibgeTownCode"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

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

Removido obrigatóriedade no campo 'referenceStartDateTime'

Remoção

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "referenceStartDateTime"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. - A conta de créd...

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que ...

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

post/responses/201/headers

Adicionado - "x-v"

Adição

post/responses/500

Adicionado - "headers"

Adição

post/responses/504

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado - "approvalDueDate"

Adição

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

Adicionado obrigatóriedade no campo 'referenceStartDate'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'period'

Remoção

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'referenceStartDateTime'

Remoção

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "referenceStartDateTime"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. - A conta de créd...

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que ...

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

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/500

Adicionado - "headers"

Adição

get/responses/504

Adicionado - "headers"

Adição

get/responses/529

Adicionado - "headers"

Adição

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https:/...

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https:/...

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "description"

Alteração

Número do documento de identificação oficial do usuário.

Número do documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

patch/requestBody/data/oneOf/0/loggedUser/document/identification

Alterado - "pattern"

Alteração

^\\d{11}$

^(?:\\d{11}|\\d{14})$

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Removido - "maxLength"

Remoção

3

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Alterado - "description"

Alteração

Tipo do documento de identificação oficial do usuário.

Tipo de documento de identificação oficial do pagador ou recebedor, pessoa natural ou jurídica.

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Removido - "example"

Remoção

CPF

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{3}$

patch/requestBody/data/oneOf/0/loggedUser/document/rel

Adicionado - "enum"

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

patch/requestBody/data/oneOf/0/riskSignals/isCallingProgress

Alterado - "description"

Alteração

Indica chamada ativa no momento do vínculo. \[Restrição\] Caso o sinal de risco esteja disponível (cliente permitiu que fosse colet...

Indica chamada ativa no momento da solicitação. \[Android\] Informação obtida através do \[link\](https://developer.android.com/refer...

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

Removido - "riskSignals"

Remoção

patch/requestBody/data/oneOf/2/properties

Removido - "riskSignals"

Remoção

patch/requestBody/data/oneOf/2/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

Código indicador do motivo de rejeição. - NAO\_INFORMADO - FALHA\_INFRAESTRUTURA - TEMPO\_EXPIRADO\_AUTORIZACAO - REJEITADO\_USUARIO - ...

patch/requestBody/data/oneOf/2/rejection/reason/code/enum

Adicionado - "AUTENTICACAO\_DIVERGENTE"

Adição

enum

patch/requestBody/data/oneOf/2/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\` - NAO\_INFORMADO: Não informada pela detentora d...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no município de cadastro do usuário pagador no detentor.

\[Restrições\]

-   Campo obrigatório quando o oneOf utilizado do recurringConfiguration for “automatic”.
    

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no município de cadastro do usuário pagador no detentor.

\[Restrições\]  
Campo de preenchimento obrigatório quando o oneOf utilizado do recurringConfiguration for “automatic”, e o consentimento passar pelo estado AUTHORISED.

patch/responses/200/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

patch/responses/200/data/properties

Adicionado - "approvalDueDate"

Adição

patch/responses/200/data/properties

Adicionado - "approvalDueDate"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. - A conta de créd...

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que ...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment

Alterado - "description"

Alteração

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. - A conta de créd...

Definições para o primeiro pagamento. É considerado como o pagamento da adesão ao serviço pelo usuário pagador. Para casos em que ...

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'interval'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'period'

Remoção

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido obrigatóriedade no campo 'referenceStartDateTime'

Remoção

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "referenceStartDateTime"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDate"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDate'

Adição

required

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

patch/responses/200/headers

Adicionado - "x-v"

Adição

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

patch/responses/500

Adicionado - "headers"

Adição

patch/responses/504

Adicionado - "headers"

Adição

patch/responses/529

Adicionado - "headers"

Adição
