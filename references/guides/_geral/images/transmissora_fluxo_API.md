# transmissora_fluxo_API

![transmissora_fluxo_API](transmissora_fluxo_API.png)

## Texto Extraído

Fluxo Transmissora - Motor Quali

jade de Dados

1. ARECEPTORA faz a solicitacao para
TRANSMISORA com o fluxo normal

ponse (Corpo + Cabecalh:

Lyi

—

2 Process Request

TRANSMISORA

2. A solicitacao deve ser atuali

izada incluindo

a resposta enviada para a RECEPTORA

(Corpo + Cabecalho), adiciona

indo os parémetros
clientOrgID(ID RECEPTORA) e endpointName ao cabecalho
(enviar somente validacdes de solicitacées bem-sucedidas - 2xx)

N

| 4 UpdateRequest

| 5 POST Ni

lateResponse
3. MQD valida as informacoes

do Cabecalho, se estiver completo,
e se 0 Endpoint é suportado,
adiciona a messagem na Fila

6 ValidateResponse
Pum

Jueue Messsage
eH

---
**Arquivo original:** `transmissora_fluxo_API.png`
**Tamanho:** 46.52 KB