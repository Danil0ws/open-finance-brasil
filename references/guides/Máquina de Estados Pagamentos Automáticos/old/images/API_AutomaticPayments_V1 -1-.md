# API_AutomaticPayments_V1 -1-

![API_AutomaticPayments_V1 -1-](API_AutomaticPayments_V1 -1-.png)

## Texto Extraído

Initial State

AWAITING_AUTHORISATION
O consentimento é sempre criado com o status

AWAITING_AUTHORISATION. Ele so pode ser aprovado
antes do tempo de expiracao de 5 minutos, assumindo o
status AUTHORISED. Se nao, deve assumir o status de
REJECTED caso expire ou seja cancelado pelo usuario.

Tempo para
aprovacao do

consentimento
de 5 minutos.

Com multipla
algada

PARTIALLY_ACCEPTED REJECTED

Sem
multipla
algada

AUTHORISED REVOKED

CONSUMED

Final State

---
**Arquivo original:** `API_AutomaticPayments_V1 -1-.png`
**Tamanho:** 149.09 KB