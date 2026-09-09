# iniciacao_de_pagamento_v2-a8b12627

![iniciacao_de_pagamento_v2-a8b12627](iniciacao_de_pagamento_v2-a8b12627.png)

## Texto Extraído

Iniciagao de pagamento - Caso de Sucesso (Alto Nivel)

Debtor Detentora pict Creditor

Seleciona detentora +

dados pagamento

O fluxo alternativo abaixo se aplica caso a iniciagao de
pagamento nao for via Pix Dados Manuais com agéncia e conta

[condicional QR Code e/ou Chave Pix]

Icondicional QRCode (dinamico)]

consulta dados GR Code

consulta dados

"4 Estabelece mTLS »

POST /token (Pedido de access_token e scope: payments, openid) .

Valida certificado
\___sSLe scopes

scess_token

' POST /payments/v1/consents

201 Created i

redirecionamento

Autenticagéo (FAPI)

[Selegao de Conta}

Seleciona conta
de débito

| Exibe informacées
do pagamento

Autoriza iniciago
do pagamento|

[condicional PIX normal]

POST /token
(Pedido de access_token (code) e scope: payments, openid)

Valida certificado
SSLe scopes

\ecess_token

n (Scope: payme!

POST payments/v1/pix/payments

‘bes de negécios

[condicional PIX agendamento}

Cria agendamento
do PIX

Marca o pagamento como
mento completato

status do pagamento
SCHEDULE_ACCEPTED_SETTLEMENT_COMPLETED

' 1
{status do consentimento CONSUMED

OBS: caso o fluxo abaixo seja oriundo
de um PIX Agendamento, a efetivagao
do pagamento ocorrerd somente na
data agendada

Efetivagao do pagamento <kassync>>

1
status do pagamento 1
| ACCEPTED_SETTLEMENT_COMPLETED !

[potiing}

GET payments/v1/pix/payments/{paymentid}

Exibe comprovante de
iniciagao de pagamento

---
**Arquivo original:** `iniciacao_de_pagamento_v2-a8b12627.png`
**Tamanho:** 225.65 KB