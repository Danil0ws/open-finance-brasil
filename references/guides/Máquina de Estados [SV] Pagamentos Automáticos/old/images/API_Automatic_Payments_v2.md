# API_Automatic_Payments_v2

![API_Automatic_Payments_v2](API_Automatic_Payments_v2.png)

## Texto Extraído

Initial State

AWAITING_AUTHORISATION

O consentimento é sempre criado com o status
AWAITING_AUTHORISATION. Em casos de
consentimentos sem miltiplas algadas aprovadoras,
deve ser aprovado pelo unico aprovador antes do
tempo de expira¢gao (60 minutos), assumindo o status
AUTHORISED. Caso existam multiplos aprovadores, o
consentimento deve ir para o status
PARTIALLY_ACCEPTED e permanecer nele até que
todos aprovem. Caso o consentimento nao seja
aprovado ou tenham se passados mais de 60 minutos
no status AWAITING_AUTHORISATION, o mesmo
devera ser movido para REJECTED.

Tempo para
aprovacao do
consentimento
de 60 minutos.

Com miltipla
algada

REJECTED

PARTIALLY_ACCEPTED
Sem

multipla
algada

AUTHORISED REVOKED

CONSUMED

Final State

---
**Arquivo original:** `API_Automatic_Payments_v2.png`
**Tamanho:** 360.14 KB