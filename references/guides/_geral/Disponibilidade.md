# Disponibilidade

Todos os endpoints das APIs classificadas como ‘Dados Abertos’, ‘Dados Cadastrais e Transacionais’ e ‘Relatórios e métricas’, deverão satisfazer requisitos mínimos de disponibilidade abaixo. Cada um de seus endpoints deverá estar disponível:

I.95% do tempo a cada 24 horas;

II.99,5% do tempo a cada 3 meses (calculado de acordo com os dados enviados pelas instituições).

Sendo que para o cálculo da disponibilidade diária considera-se:

![image-20240522-114640.png](images/image-20240522-114640.png)

As métricas devem respeitar a individualidade do endpoint implementado pela instituição, isto é: deve-se enviar cada endpoint separadamente, conforme exemplo abaixo, no máximo nível de granularidade:

i. [https://example.api/open-banking/financings/v2/contracts](https://example.api/open-banking/financings/v2/contracts)

ii. [https://example.api/open-banking/financings/v2/contracts/contractId](https://example.api/open-banking/financings/v2/contracts/contractId)

iii. [https://example.api/open-banking/financings/v2/contracts/contractId/warranties](https://example.api/open-banking/financings/v2/contracts/contractId/warranties)

iv. [https://example.api/open-banking/financings/v2/contracts/contractId/scheduled-instalments](https://example.api/open-banking/financings/v2/contracts/contractId/scheduled-instalments)

v. [https://example.api/open-banking/financings/v2/contracts/contractId/payments](https://example.api/open-banking/financings/v2/contracts/contractId/payments)

vi. [https://example.api/open-banking/financings/v2/contracts/{contractId}](https://example.api/open-banking/financings/v2/contracts/%7BcontractId%7D)

vii. [https://example.api/open-banking/financings/v2/contracts/{contractId}/warranties](https://example.api/open-banking/financings/v2/contracts/%7BcontractId%7D/warranties)

viii. [https://example.api/open-banking/financings/v2/contracts/{contractId}/scheduled-instalments](https://example.api/open-banking/financings/v2/contracts/%7BcontractId%7D/scheduled-instalments)

ix. [https://example.api/open-banking/financings/v2/contracts/{contractId}/payments](https://example.api/open-banking/financings/v2/contracts/%7BcontractId%7D/payments)

Observação: Endpoint com path variable, a exemplo {contractId}, podem ser enviados com ou sem chaves {}.

Todos os endpoints das APIs classificadas como ‘Serviços’ deverão possuir a mesma disponibilidade do arranjo de pagamento ou do serviço aos quais estão associadas.

A disponibilidade é checada no endpoint GET /discovery/status, conforme documentada no item [API de Status](data/references/guides/Informa.md).

A cada 30 segundos, a API de status é requisitada com timeout de 1s.

Será considerado _uptime_, se o retorno for:

-   OK.
    

Será considerado _downtime_, se o retorno for:

-   PARTIAL\_FAILURE
    
-   SCHEDULED\_OUTAGE
    
    -   Se a requisição for realizada entre o período de 01h e 07h, o contador de SCHEDULED\_OUTAGE é iniciado com 30 segundos acrescidos
        
    -   Cada nova requisição vai adicionando 30 segundos ao contador de SCHEDULED\_OUTAGE, até que uma requisição volte outro valor ou a requisição for feita depois das 7h
        
-   UNAVAILABLE
    
    -   Se a requisição for realizada entre o período de 7h e 1h
        
    -   Se serviço não responder a requisição
        
    -   O contador de _downtime_ é iniciado com 30 segundos acrescidos
        
    -   Cada nova requisição adicionará 30 segundos ao contador de _downtime_, até que uma requisição retorne OK
        

O _downtime_ deve ser calculado como o número total de segundos simultâneos por requisição da API, por período de 24 horas, começando e terminando à meia-noite, que qualquer endpoint da API não esteja disponível, dividido por 86.400 (total de segundos em 24 horas) e expresso como uma porcentagem.

A disponibilidade é calculada sendo 100% menos a quantidade em percentual da indisponibilidade.

-   De modo geral, consideram-se os erros HTTP Status Code 5XX como erros do servidor, e portanto, atribuíveis ao servidor das APIs
    
-   Erros baseados em HTTP Status Code 4XX são, em grande parte, atribuídos a ações ou falhas dos clientes, e desta forma, não devem ser incluídos no cálculo
