# Changelog - [SV] Vínculo de dispositivo - v2.1.0 - v2.0.0

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

Família de API para permitir o pagamento sem redirecionamento via Open Finance Brasil. Permite tanto o gerenciamento dos disposi...

Família de API para permitir o pagamento sem redirecionamento via Open Finance Brasil. Permite tanto o gerenciamento dos disposi...

/info

Alterado - "version"

Alteração

2.0.0

2.1.0

## GET /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/dailyLimit

Alterado - "description"

Alteração

Limite diário cumulativo para este vínculo de conta. Este limite não garante a autorização de iniciações de pagamento; servindo co...

Limite diário cumulativo para este vínculo de conta. Este limite não garante a autorização de iniciações de pagamento; servindo co...

## POST /enrollments/{enrollmentId}/fido-registration-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/rp/name

Alterado - "description"

Alteração

Nome amigável da Relying Party para exibição aos usuários. Pode ser obtido através do Software Statement Assertion, atributo softw...

Nome amigável da Relying Party para exibição aos usuários. Deve ser obtido através do Software Statement Assertion, atributo softw...

post/responses/201/data/user/displayName

Alterado - "description"

Alteração

Identificador do usuário para fins de apresentação.

Identificador do usuário para fins de apresentação. Deve ser formado pelo nome social, se existente, ou nome e sobrenome do cadast...

## POST /consents/{consentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/fidoAssertion/response/userHandle

Alterado - "description"

Alteração

Nome de usuário que foi enviado durante a criação da credencial. Deve ser enviado no formato base64url para a detentora de conta.

Nome de usuário que foi enviado durante a criação da credencial. Deve ser enviado no formato base64url para a detentora de conta. ...
