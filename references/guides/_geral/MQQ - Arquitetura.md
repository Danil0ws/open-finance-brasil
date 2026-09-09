# MQQ - Arquitetura

1.  Arquitetura
    
2.  Proxy reverso
    
3.  Diagramas de Sequência
    
    1.  Fluxo da Receptora
        
    2.  Fluxo da Transmissora
        
    3.  Fluxo de Atualização de Configuração
        
    4.  Fluxo de Validação
        
    5.  Fluxo de Envio de Resultados
        

## Arquitetura

Apesar de ter sido criada como um monolito, a aplicação MQD – Client foi desenvolvida com um desacoplamento em componentes, o que permitirá futuramente dividi-la em seções menores (microserviços) se necessário.

![image-20240220-204539.png](images/image-20240220-204539.png)

## Componentes

8e2ee32b-6d13-44ab-8a8b-56c006eadd39b1fc1f0a-a7f0-47de-a3dc-d6905baecccd

Serviço

Descrição

Tecnologia

Versão

SERVICE

Serviço executado na Instituição Financeira que envia a resposta obtida ao MQD

N.A

N.A

API

API REST que expõe os métodos necessários para validar as mensagens

Go

1.23

CONFIGURATION MANAGER

Componente responsável por ler os arquivos de configuração do servidor central e estabelecer os valores para uso pela aplicação

Go

1.23

MONITORING

Componente responsável pela criação das métricas da aplicação, tanto de desempenho quanto de negócio

Go / OpenTelemetry

1.23

QUEUE MANAGER

Fila que armazena as mensagens recebidas pela API

Go

1.23

MESSAGE PROCESS WORKER

Componente que lê a fila de tarefas e processa cada uma das mensagens

Go

1.23

VALIDATOR

Componente que valida mensagens convertendo-as em objetos e executando uma validação baseada em JSON Schema para cada endpoint

Go

1.23

QUEUE RESULTS

Fila que salva os resultados das mensagens já validadas

Go

1.23

RESULT PROCESSOR

Componente responsável por processar os resultados, criando um resumo de cada janela de tempo e enviando-os ao servidor MQD

Go

1.23

MQD SERVER PROXY

Servidor proxy reverso responsável por estabelecer uma conexão segura (mTLS) com o servidor

NGINX

1.25

GATEWAY

Camada responsável pelo controle e administração das APIs do servidor MQD

AWS API Gateway

N.A.

wide1800

## Grupos de APIs Suportados

O MQD Client valida respostas de dois grupos de APIs:

75564ab8-15c6-490b-8d6a-4ca6bf78df96a77911d7-9582-48fe-96d5-6ed91f1f4906

Grupo

Modo de Operação

Descrição

Dados do Cliente (DC)

RECEIVER e TRANSMITTER

APIs transacionais — contas, cartão de crédito, operações de crédito, investimentos, câmbio, consentimento, recursos, dados cadastrais

Portabilidade de Crédito (PC)

RECEIVER e TRANSMITTER

API de portabilidade de crédito

wide1800

## Convivência de Versões

O MQD suporta validação de múltiplas versões de uma mesma API simultaneamente. A instituição pode especificar a versão desejada através do header `versionHeader` na requisição ao `/ValidateResponse`. Caso não informado, a versão mais recente configurada será utilizada.

## Arquitetura Server-Side (Visão Resumida)

O lado servidor do MQD é composto por componentes Lambda na AWS que processam os relatórios enviados pelos clientes:

f69cf7b7-ecf1-415b-8ece-a945faee33c961b74ef6-ca77-4a12-b3ae-68a0af3dde10

Componente

Função

Frequência

mqd-server

Recepção de relatórios via API Gateway

Contínuo

mqd-report\_process

Processamento S3 → Database

Event-driven

mqd-aggregator\_day

Agregação diária dos dados

Diário

mqd-ticket\_generator

Geração de tickets de qualidade e operacionais

Semanal (qualidade) / Diário (operacional)

mqd-iqd\_generator

Cálculo mensal do IQD

Mensal (dia 15)

mqd-export\_pad

Exportação de dados para PAD

Diário / Mensal

mqd-notification\_bridge

Envio de notificações ao Service Desk

Event-driven

mqd-notification-monitor

Monitoramento de transações de notificação

Event-driven

mqd-ingestion

Ingestão de dados no banco PAD

Event-driven (S3 trigger)

mqd-schema\_generator

Geração de JSON Schemas a partir de specs OpenAPI

Sob demanda

wide1800
