# MQD - Fluxo de Envio de Resultados

Este fluxo representa o processo de envio de resultados (relatórios) executado na aplicação MQD Client.

![image-20240220-210313.png](images/image-20240220-210313.png)

## Passos

5bc1254e-69d3-48e7-b5a6-650fe67ec020b85ff96d-0cc2-4974-861a-87d6a01f8f72

Passo

Participante

Descrição

RESULT\_PROCESSOR

A cada intervalo definido (REPORT\_EXECUTION\_WINDOW) ou ao atingir o limite de mensagens (REPORT\_EXECUTION\_NUMBER), o componente inicia o processo de envio

RESULT\_PROCESSOR

O componente solicita ao Validador a lista de resultados processados

2.  e 3.
    

VALIDATOR

Após retornar os resultados, o validador limpa a lista para um novo ciclo

RESULT\_PROCESSOR

O componente gera um novo resumo (report) com a lista de resultados obtidos

RESULT\_PROCESSOR

O componente solicita um token de acesso ao proxy do servidor

PROXY

Solicita o token ao servidor utilizando certificados para estabelecer mTLS

7.  e 8.
    

GATEWAY

O Gateway valida as credenciais do client (client\_credentials) e retorna um token JWT

PROXY

Proxy retorna o token ao RESULT\_PROCESSOR

10.

RESULT\_PROCESSOR

O componente envia o report criado para o servidor usando o token como autorização

11.

PROXY

O proxy estabelece conexão mTLS e envia o relatório ao servidor

12.

GATEWAY

O Gateway valida o token e encaminha para o MQD Server

13.

MQD SERVER

O servidor armazena o relatório com timestamp de recebimento

14\. e 15.

GATEWAY/PROXY

Retorna a resposta do servidor para o RESULT\_PROCESSOR

wide1800

## Gatilhos de Envio

O envio de relatórios é disparado por dois critérios (o que ocorrer primeiro):

9cde177d-f5c4-4e4d-94b0-f91f362ec87d417f9988-33c6-4780-854f-571731bb36f2

Critério

Variável de Ambiente

Padrão

Janela de tempo

REPORT\_EXECUTION\_WINDOW

Configurado no servidor central

Quantidade de mensagens

REPORT\_EXECUTION\_NUMBER

Configurado no servidor central

wide1800

## Esquema de Report Enviado

![image-20240220-210334.png](images/image-20240220-210334.png)

O report contém:

-   Identificação da organização (SERVER\_ORG\_ID)
    
-   Período de referência (início e fim da janela)
    
-   Lista de endpoints validados com contagem de requisições e erros
    
-   Detalhes de erros por campo/propriedade (até um limite configurado)
    

## Retentativas

Em caso de falha no envio:

-   O relatório é mantido em memória para reenvio
    
-   Novos resultados continuam sendo acumulados
    
-   Na próxima janela de tempo, os relatórios pendentes são reenviados
