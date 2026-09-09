# Changelog - [SV] Vínculo de dispositivo - v2.2.0-rc.1 - v2.1.0

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "version"

Alteração

2.1.0

2.2.0-rc.1

## POST /enrollments

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## GET /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/cancellation/reason/oneOf/0/rejectionReason

Alterado - "description"

Alteração

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis: • REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS: Expiração automá...

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis: • REJEITADO\_TITULARIDADE\_DIVERGENTE: A titularidade do us...

get/responses/200/data/cancellation/reason/oneOf/0/rejectionReason/enum

Adicionado - "REJEITADO\_TITULARIDADE\_DIVERGENTE"

Adição

enum

get/responses/500

Adicionado - "headers"

Adição

get/responses/529

Adicionado - "headers"

Adição

patch/requestBody/data/cancellation/reason/oneOf/0/rejectionReason

Alterado - "description"

Alteração

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis: • REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS: Expiração automá...

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis: • REJEITADO\_TITULARIDADE\_DIVERGENTE: A titularidade do us...

patch/requestBody/data/cancellation/reason/oneOf/0/rejectionReason/enum

Adicionado - "REJEITADO\_TITULARIDADE\_DIVERGENTE"

Adição

enum

patch/responses/500

Adicionado - "headers"

Adição

patch/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/fido-registration-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post

Alterado - "description"

Alteração

Método para obter os parâmetros para criação de uma nova credencial FIDO2. Um novo challenge deve ser criado a cada chamada. Os pa...

Método para obter os parâmetros para criação de uma nova credencial FIDO2. Um novo challenge deve ser criado \*\*para cada enrollmen...

post/responses/201/data/excludeCredentials

Adicionado - "description"

Adição

Lista de IDs de credenciais já existentes para este usuário e autenticador. É utilizado para evitar a criação de múltiplas credenc...

post/responses/201/data/timeout

Alterado - "description"

Alteração

Timeout, em milissegundos, para registro da credencial FIDO2.

Representa, em milissegundos, o tempo de validade do challenge para registro da credencial FIDO2. O valor desse campo deverá ser 3...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: - RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. - STATUS\_VINCULO\_IN...

Códigos de erros previstos: - RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. - STATUS\_VINCULO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "MAXIMO\_CHALLENGES\_ATINGIDO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - RP\_INVALIDA: O identificador da Relying Party informado não pode ...

Descrição específica do erro de acordo com o código reportado: - RP\_INVALIDA: O identificador da Relying Party informado não pode ...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - RP\_INVALIDA: Relying party inválida. - STATUS\_VINCULO\_INVAL...

Título específico do erro reportado, de acordo com o código enviado: - RP\_INVALIDA: Relying party inválida. - STATUS\_VINCULO\_INVAL...

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/fido-registration

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/risk-signals

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/fido-sign-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /consents/{consentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody

Alterado - "description"

Alteração

Payload para criação de vínculo de conta.

Payload para autorização de consentimento a partir de um vínculo de conta.

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. - STATUS\_CONSENTIMENTO\_IN...

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. - STATUS\_CONSENTIMENTO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "ORIGEM\_FIDO\_INVALIDA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição
