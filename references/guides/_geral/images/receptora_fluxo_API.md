# receptora_fluxo_API

![receptora_fluxo_API](receptora_fluxo_API.png)

## Texto Extraído

Fluxo Receptora - Motor Qual

RECEPTORA

1. ARECEPTORA faz a solicitacao para
‘TRANSMISORA com o fluxo normal

i

jade de Dados

TRANSMISORA

<

3 Response (Corpo + Cabecall

>"
2 Proce:

I

0)

2. Asolicitacao deve ser atualizada incluindo
a resposta enviada para a RECEPTORA
(Corpo + Cabecalho), adicionando os parametros
clientOrgID (ID RECEPTORA) e endpointName ao cabecalho

(enviar somente validacdes de solicitacées bem-sucedidas - 2xx)

5 POST /ValidateResponse |
eee

| 4 UpdateRequest

—_

3. MQD valida
do Cabecalho,

adiciona a me:

as informacoes
se estiver completo,
e se 0 Endpoint é suportado,
ssagem na Fila

8 OK

| 6 ValidateResponse '
7 Queue Messsage p

s Request

---
**Arquivo original:** `receptora_fluxo_API.png`
**Tamanho:** 47.19 KB