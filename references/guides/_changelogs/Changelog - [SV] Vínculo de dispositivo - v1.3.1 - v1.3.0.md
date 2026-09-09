# Changelog - [SV] Vínculo de dispositivo - v1.3.1 - v1.3.0

## GET /enrollments/{enrollmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/data/cancellation/reason/rejectionReason​

Alterado - "description"

Alteração

REJEITADO\_TEMPO\_EXPIRADO\_AUTHORISATION ​

REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS

## PATCH /enrollments/{enrollmentId}

### Resquest

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/data/cancellation/reason/rejectionReason​

Alterado - "description"

Alteração

REJEITADO\_TEMPO\_EXPIRADO\_AUTHORISATION ​

REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS

## POST /enrollments/{enrollmentId}/fido-registration-options

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/challenge

Alterado - "description"

Alteração

Sequência de bytes aleatórios gerados pelo servidor FIDO2. Deve ser o valor em formato base64url.

Sequência de bytes aleatórios gerados pelo servidor FIDO2. Deve ser o valor em formato base64url sem padding.

## POST /enrollments/{enrollmentId}/fido-sign-options

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/challenge

Alterado - "description"

Alteração

Sequência de bytes aleatórios gerados pelo servidor FIDO2, codificados em base64.

Sequência de bytes aleatórios gerados pelo servidor FIDO2. Deve ser o valor em formato base64url sem padding.
