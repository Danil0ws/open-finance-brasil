# Diagrama_iniciacao_pagamento_sem_redirecionamento

![Diagrama_iniciacao_pagamento_sem_redirecionamento](Diagrama_iniciacao_pagamento_sem_redirecionamento.png)

## Texto Extraído

Seleciona conta usada para pagamento
sem redirecionamento (debtorAccount)

App ITP Backend ITP Backend Detentora AS-FAPI Detentora eneaner
Detentor:

POST /token
grant_type=client_credentials

access_token

wee ee eb e- We-------- ee

POST /consents {..creditor, payment, debtorAccount,..}
Authorization: Bearer access_token

201 {... status: AWAITING_AUTHORISATION

POST /enrollments/{enrollmentld}/fido-sign-options
Authorization: Bearer access_token
{..consentld}

201

{fidoChallenge ...}
Requisita assinatura
FIDO2
{fidoChallenge ...}

Solicita gesto de autenticagao
para o usuario

Envia fidoAssertion

{signature: ...,
authenticatiorData:...
clientDataJsor
+ Extragdo de sinais de risco do dispositivo

Realiza gesto
(ex.: biometria, PIN)

POST /token
grant_type=refresh_token,
refresh_token = enrollment_refresh_token

201
{payment_access_token, payment_refresh_token}
POST /consents/{consentld}/authorise {riskSignals:..}
Authorization: Bearer payment_access_token.
Validagao da
fidoAssertion

Consentimento de
pagamentos
transita ao status
AUTHORISED

204

POST /pix/payments
{...consentid}
Authorization: Bearer payment_access_token

Executa pagamento

GET /pix/payment/{paymentid}
Authorization: Bearer access_token

Success

---
**Arquivo original:** `Diagrama_iniciacao_pagamento_sem_redirecionamento.png`
**Tamanho:** 216.08 KB