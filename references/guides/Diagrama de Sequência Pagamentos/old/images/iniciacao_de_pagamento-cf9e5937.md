# iniciacao_de_pagamento-cf9e5937

![iniciacao_de_pagamento-cf9e5937](iniciacao_de_pagamento-cf9e5937.png)

## Texto Extraído

Iniciagao de pagamento - Caso de Sucesso (Alto Nivel)

Debtor Iniciadora

Detentora

Creditor

Seleciona detentora +
dados pagamento

1__ 20008 pagamento _y

0 fluxo alternativo abaixo se aplica caso a iniciacdo de H
' pagamento ndo for via Pix Dados Manuais com agéncia e conta !

Teondicional QRCode (dinamico)]

consulta dados

Estabelece mTLS

POST /token (Pedido de access_token e scope:payments, openid)
[OAuth 2.0 client_credentials flow]

\Valida certificado SSL e scopes

gera access_token

if

access-token (scope: payments, openid)

status do consentimento AWAITING_AUTHORISATION

redirecionamento '

1

Aplicagao da Dententora

Autenticacao (FAP!)

»

Autentica Debtor

Tselegao de Conta]

Seleciona conta de
débito

Exibe informacées
do pagamento

ss

| Autoriza iniciaco
1 de pagamento

[FAPI Hybrid flow]

access-token (scope: payments, openid)

POST payments/v1/pix/payments

Validacdes de negécios

201 Created

‘status do pagamento
1 (ACCEPTED_SETTLEMENT_COMPLETED

'
e o

potting |

GET payments/v1/pix/payments/{paymentid}

Exibe comprovante '
de iniciacao de pagamento

---
**Arquivo original:** `iniciacao_de_pagamento-cf9e5937.png`
**Tamanho:** 207.55 KB