# MQD - Fluxo da Transmissora

Este fluxo representa o processo de enfileramento de messagens e integração com o MQD na visão da TRANSMISSORA.

![transmissora\_fluxo\_API.png](images/transmissora_fluxo_API.png)

8e8c714d-d920-4d50-a9bc-4716b6049dcc6108ae88-094d-43a4-8852-45efac71459f

## Passos

Passo

Participante

Descrição

SERVICE

O serviço da receptora gera uma solicitação para a API da TRANSMISSORA

API

A API da transmissora processa a solicitação recebida

API

A API retorna um resultado para a solicitação à receptora

API

A API atualiza a solicitação, incluindo a resposta enviada para a RECEPTORA (Corpo+Cabeçalho), adicionando: `serverOrgId` (OrganisationID da Receptora que solicitou a informação) e `endpointName`. Enviar somente validações de solicitações bem-sucedidas (2xx).

API

A API da TRANSMISSORA envia a resposta válida para o MQD

MQD

MQD valida se as informações do cabeçalho estão completas e corretas

MQD

MQD encaminha as informações para a fila para processamento posterior

MQD

MQD responde HTTP 200 se o processo de enfileiramento foi bem-sucedido

## Headers da Requisição

Header

Descrição

Obrigatório

Exemplo

endpointName

Nome do endpoint conforme tabela de endpoints aceitos

Sim

/loans/v2/contracts/{contractId}/payments

serverOrgId

Organisation ID da **RECEPTORA** que solicitou a informação

Sim

c73bcdcc-2669-4bf6-81d3-e4ae73fb11fd

x-fapi-interaction-id

UUID usado na transação original

Sim

241e202-e8f0-5f5a-9651-ebc257371e24

versionHeader

Versão da API para validação (convivência)

Não

2.4.0

transmitterID

ID alternativo do transmissor (se diferente do SERVER\_ORG\_ID configurado)

Não

UUID

## Diferença em relação ao modo RECEIVER

No modo TRANSMITTER, o `serverOrgId` contém o ID da **RECEPTORA** (quem pediu a informação), pois a variável de ambiente `SERVER_ORG_ID` já identifica a transmissora.

## Exemplo de Requisição

true

**Referência de endpoints aceitos:** [Tabela de endpoints validados pelo MQD](https://file+.vscode-resource.vscode-cdn.net/c%3A/code/ofb/mqd/mqd-architecture/docs/confluence-updates/link-tabela-endpoints)

wide1800
