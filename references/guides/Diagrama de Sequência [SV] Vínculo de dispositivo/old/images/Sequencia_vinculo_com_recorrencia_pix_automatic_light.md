# Sequencia_vinculo_com_recorrencia_pix_automatic_light

![Sequencia_vinculo_com_recorrencia_pix_automatic_light](Sequencia_vinculo_com_recorrencia_pix_automatic_light.png)

## Texto Extraído

Diagrama de sequéncia para iniciagdo de pagamentos sem redirecionamentos

Solcita gesto de autenticacao
para o usuario

Realza gesto
(ex: biometria, PIN)

j Success

App ITP:

Seleciona conta usada para pagamento
‘sem redirecionamento (debtorAccount)
paeeerrrroowrrerrrn—e—ems

Backend ITP

POST token
cgrant_type=client_credentials

access_token

POST Irecuring-consents
{creditor reeuringConfiguation, debtorAccount..)
Authorisation: Saarer access, foken

201 {... status: AWAITING_AUTHORISATION

POST lenrolments{enrolmentle\ide-sign-options
‘Authorstion: Sesrer access, fen
{.-recurringConsentis)

—_ematorset) __yig.

ie

201 :
{fidoChallenge ...} H
<_ rr

Requisita assinatura
FIDO
{idoChallenge ..}

5 < $s

Envia fidoAssertion
‘signature:
authenticatiorData
clientDatadson:..}
+ Extragdo de sinais de risco do dispositive

eer Ft

POST token
cgrant_type=refresh_token,
refresh_token = enrollmentrefresh token!
per vec————rererer vie
201
{recurting_payment_access_token,
recurring payment_teftesh_token}

POST irecuring-consents/recuringConsentidyauthorise
{fskSignals:.)
Authorization: Bearer payment_sccess_token

Backend Detentora

204

POST /pixitecurting-payments

{..recurringConsenti¢ H
Authorization: Bearer recurting_payment_access_token!

201 {. status: RCVD}

GET /pivrecurring-payments/{tecurringPaymentid)
‘Authorization: Bearer access_token

*

200 status: ACSC, SCHD}

AS-FAPI Detentora

>

Consentimento de
agamentos
transita 20 status,
AUTHORISED

Executa pagamento ou agendamento

FIDO2 Server
Detentora

Validagao da
fidoAssertion

---
**Arquivo original:** `Sequencia_vinculo_com_recorrencia_pix_automatic_light.png`
**Tamanho:** 249.58 KB