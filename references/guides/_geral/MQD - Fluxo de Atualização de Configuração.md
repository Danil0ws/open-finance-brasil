# MQD - Fluxo de Atualização de Configuração

Este fluxo representa o processo de atualização de configuração do MQD Client.

![image-20240220-210734.png](images/image-20240220-210734.png)

## Passos

e5d12599-39b4-41c2-9a38-f34adbe3501a9e2ba00a-a32a-4a39-b19b-e11b32b262c3

Passo

Participante

Descrição

CONFIGURATION\_MANAGER

O componente solicita ao proxy um token usando o OrganizationID configurado (SERVER\_ORG\_ID)

PROXY

O proxy solicita o token do servidor usando o OrganizationID enviado no cabeçalho, via conexão mTLS

GATEWAY

O Gateway valida o ID do cliente (client\_credentials) e retorna um token JWT

PROXY

Proxy retorna o token recebido ao CONFIGURATION\_MANAGER

CONFIGURATION\_MANAGER

O componente solicita a configuração (GET /settings) através do proxy

PROXY

O proxy estabelece conexão mTLS e solicita a configuração ao servidor

GATEWAY

O servidor retorna a configuração com a versão e lista de APIs suportadas

PROXY

O proxy retorna a configuração ao CONFIGURATION\_MANAGER

CONFIGURATION\_MANAGER

O componente compara a versão recebida com a versão local

CONFIGURATION\_MANAGER

Se for uma versão diferente da mais recente, o componente solicita os JSON Schemas dos diferentes grupos de APIs através do proxy

10.

PROXY

O proxy estabelece conexão mTLS e solicita os arquivos de schemas

11.

GATEWAY

O servidor valida a existência dos arquivos e os retorna (schemas por grupo/family\_type/versão)

12.

PROXY

O proxy retorna os schemas ao CONFIGURATION\_MANAGER

13.

CONFIGURATION\_MANAGER

O componente atualiza a configuração local (schemas, endpoints suportados e regras de validação)

wide1800

## O que é sincronizado

O objeto `ConfigurationSettings` recebido no passo 6 contém:

d1616b44-0b92-4e92-ba0b-5b44508e53da881a7355-01aa-4b39-ab81-d98137bc596d

Campo

Tipo

Descrição

`Version`

string

Versão da configuração (ex: "1.2.3")

`ValidationSettings.APIGroupSettings`

array

Lista de grupos de APIs com suas versões

`ValidationSettings.*ThroughputValidationRate`

int

Taxa de amostragem por nível de throughput (1-100%)

`ReportSettings.ReportExecutionWindow`

int

Janela de envio de reports em minutos

`ReportSettings.SendOnReportNumber`

int

Limite de mensagens antes de forçar envio

`SecuritySettings.AttributesToMask`

array

Campos sensíveis a mascarar em logs

wide1800

### Estrutura de APIGroupSettings

jsonwide1800true

### Grupos de APIs suportados atualmente

d45cf85a-7df8-47f8-9d46-1ef2bb06d8ace961bc16-886f-497e-b178-9d9405c8560a

Grupo

Código

APIs

Dados do Cliente

DC

Consentimento, Recursos, Dados Cadastrais, Contas, Cartão de Crédito, Empréstimos, Financiamento, Adiantamento a Depositantes, Direitos Creditórios, Investimentos (5 subtipos), Câmbio

Portabilidade de Crédito

PC

Portabilidade de Crédito

wide1800

### Taxas de Amostragem por Throughput

O MQD classifica endpoints por volume de tráfego e aplica taxas de amostragem diferenciadas:

39024753-2a1b-4dae-9b64-015beee6fb130320e795-6577-49c3-9f28-bfa240ac9d1a

Classificação

Descrição

Taxa Padrão

ExtremelyHigh

Endpoints com volume extremamente alto

100%

High

Endpoints com volume alto

100%

Medium

Endpoints com volume médio

100%

Low

Endpoints com volume baixo

100%

VeryLow

Endpoints com volume muito baixo

100%

wide1800

> Nota: As taxas padrão são 100% (validação total). O servidor central pode ajustar esses valores conforme necessidade operacional.

## Esquema de Definições de Configuração

O objeto recebido pelo cliente no momento da atualização da configuração está definido abaixo.

![image-20240220-210751.png](images/image-20240220-210751.png)

## Frequência de Sincronização

O CONFIGURATION\_MANAGER executa a sincronização:

-   Na **inicialização** do container
    
-   **Periodicamente** a cada **6 horas** (intervalo padrão configurado)
    

Se a versão recebida for igual à versão local, nenhum download adicional de schemas é feito (apenas a verificação de versão consome rede).

## Fluxo de Decisão

wide1800true
