# MQD - Fluxo da Receptora

Este fluxo representa o processo de enfileramento de messagens e integração com o MQD na visão da RECEPTORA.

![receptora\_fluxo\_API.png](images/receptora_fluxo_API.png)

## Passos

f88afacc-41f6-4eb9-ad86-8729b7521357b7a24ce9-3d07-4427-90c0-0903f1a72264

Passo

Participante

Descrição

SERVICE

O serviço da receptora gera uma solicitação para a API da TRANSMISSORA

API TRANSMISSORA

A API processa a solicitação recebida

API TRANSMISSORA

A API retorna um resultado para a solicitação

SERVICE

O Serviço gera uma nova requisição ao MQD, tendo como base a Resposta da TRANSMISSORA, incluindo no cabeçalho: `endpointName`, `serverOrgId` (ID do transmissor) e `x-fapi-interaction-id`. Enviar somente validações de solicitações bem-sucedidas (2xx).

SERVICE

O serviço envia a nova solicitação para a API do MQD (`POST /ValidateResponse`)

MQD

MQD valida se as informações do cabeçalho estão completas e corretas

MQD

MQD encaminha as informações para a fila para processamento posterior

MQD

MQD responde HTTP 200 se o processo de enfileiramento foi bem-sucedido

wide1800

## Headers da Requisição

37544083-d6f9-4214-be37-30ce4ed12b8964d7f4ed-3e89-441a-8870-eedc1a13a4d8

Header

Descrição

Obrigatório

Exemplo

endpointName

Nome do endpoint conforme tabela de endpoints aceitos

Sim

/loans/v2/contracts/{contractId}/payments

serverOrgId

Organisation ID da **TRANSMISSORA** (Diretório Central)

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

consentID

ID do consentimento associado

Não

urn:bancoex:C1DD33123

wide1800

## Exemplo de Requisição

wide1800true

**Referência de endpoints aceitos:** [Tabela de endpoints validados pelo MQD](https://file+.vscode-resource.vscode-cdn.net/c%3A/code/ofb/mqd/mqd-architecture/docs/confluence-updates/link-tabela-endpoints)
