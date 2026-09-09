# Changelog - [SV] Vínculo de dispositivo - v2.3.0-rc.1 - v2.2.0

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

2.2.0

2.3.0-rc.1

## POST /enrollments

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/transactionLimit

Alterado - "description"

Alteração

Valor máximo, por transação, admitido para este vínculo de conta. Este limite não garante a autorização de iniciações de pagamento...

Valor máximo, por transação, admitido para este vínculo de conta. Este limite não garante a autorização de iniciações de pagamento...

## PATCH /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /enrollments/{enrollmentId}/fido-registration-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/user/id

Alterado - "description"

Alteração

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

## POST /enrollments/{enrollmentId}/fido-registration

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /enrollments/{enrollmentId}/risk-signals

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /enrollments/{enrollmentId}/fido-sign-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /consents/{consentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /recurring-consents/{recurringConsentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**
