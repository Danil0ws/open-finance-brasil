# SS17_SequenciaVinculoDispositivo

![SS17_SequenciaVinculoDispositivo](SS17_SequenciaVinculoDispositivo.png)

## Texto Extraído

FIDO2 Server

App ITP Backend ITP Detentora AS-FAPI Detentora
Detentora

POST /token

Selegdo da detentora de conta grant_type = client_credentials

access_token, refresh_token

POST /enrollments
{...permissions [“PAYMENT_INITIATE’]}
Authorization: Bearer access_token

Armazena 0 vinculo de
dispositivo para uso com status
AWAITING_RISK_SIGNALS

201 {enrollmentid:“enrollment:urn:bank: 1234”,
Status: “AWAITING_RISK_SIGNALS’ ...}

POST /enrollments/{enrollmentid}/risk-signals
{riskSignals}

Sinais de risco Authorization: Bearer access_token

Altera o status do Vinculo para
AWAITING_ACCOUNT_HOLDER_VALIDATION

OQ wane nn ee ee eee eee eee eee

Redirecionamento p/ ambiente da detentora (FAPI hybrid flow)

Solicita autorizagdo para 0 vinculo

Autentica, seleciona o detentor de conta e confirma o vinculo

Armazena 0 debtorAccount
selecionado no objeto
do vinculo de dispositivo

Estabelece o status
de vinculo como
<M ‘AWAITING_ENROLLMENT”

Oe T

Redireciona p/ ambiente do ITP {authorization code 1234}

POST /token
{authorization code: 1234}

201 OK
{refreshToken: enrollment_refresh_token, accessToken:
enrollment_access_token}

POST /enrollments/{enrollmentid}/fido-registration-options
Authorization: Bearer enrollment_access_token

Se a, Se

201 OK { fidoChallenge... }

Requisita a criagdo da credencial FIDO2 {fidoChalleng

Requisita um challenge FIDO2 para o
usuario

Realiza o gesto de autenticagao
(ex.: biometria, PIN)

Cria a credencial FIDO2

Envia a credencial publica
{ attestationObject:..., clientDataJson:...}

POST /enrollments/{enrollmentid}/fido-registration
Authorization: Bearer enrollment_access_token
{credential: credential ...}

Valida e armazena credencial

Alterar status do vinculo de
dispositivo para AUTHORISED

204 OK

Co oe

---
**Arquivo original:** `SS17_SequenciaVinculoDispositivo.png`
**Tamanho:** 596.63 KB