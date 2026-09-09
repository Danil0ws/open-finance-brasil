# SLA de Envio de Reportes - 99% até 7 dias da transação

v 1.01

## **Objetivo**   

Apontar os casos em as instituições não enviaram em até 7 dias o mínimo de 99% dos reportes esperados, a partir da data e horário das transações ou cuja quantidade de reportes UNPAIRED ou PAIRED\_INCONSISTENT  seja superior a 1% do total de reportes esperados.

## **Escopo**   

São analisados envios dos reportes de Dados Cadastrais e Transacionais (Fases 2 e 4b) e Dados de Pagamentos (Fase 3)

## **Terminologia**   

Os termos abaixo estão no contexto da Plataforma de Coleta de Métricas, que por sua vez está no contexto do Open Finance Brasil.  

**Client e Server**  

Em uma interação, a parte que solicita os dados é chamada de _client_, ao passo que a parte que devolve os dados é _server_. Portanto, supondo que A faça uma consulta em B pelos dados de uma conta, esses dados serão transmitidos por quem recebeu a solicitação, e recebidos por quem a fez. Neste caso, A é o _client_ e B é o _server_.  

**Faltante**

Quando uma organização envia um reporte contra uma outra organização, caso esta última não envie sua contraparte ela será considerada _faltante_ no processo de pareamento.

## **Forma de avaliação do percentual de SLA 99%**

Diariamente são apurados os reportes que não cumpriram o SLA de envio da seguinte forma:

1.  Contam-se todos os reportes enviados pela organização que foram recebidos pela PCM até 7 dias da data da transação, por endpoint e método
    
    1.  Dentro do total de reportes enviados considera-se os reportes com status:
        
        1.  PAIRED
            
        2.  PAIRED\_INCONSISTENT do role CLIENT, statusCode = 408 e processTimeSpan superior a 15.000 ms
            
2.  Em seguida, contam-se os reportes não-pareados por endpoint e método:
    
    1.  Enviados contra a organização e que não foram pareados (status UNPAIRED)
        
    2.  Enviados pela organização que estão com status PAIRED\_INCONSISTENT, desde que não sejam do role CLIENT e statusCode = 408 e processTimeSpan superior a 15.000 ms
        
3.  **IMPORTANTE:** se um reporte PAIRED\_INCONSISTENT estiver no role CLIENT, statusCode = 408 e processTimeSpan superior a 15.000 ms, tanto o role CLIENT quanto o role SERVER são considerados enviados.
    
4.  Calcula-se o total de reportes esperados: não pareados + recebidos até 7 dias da data da transação
    
5.  O quociente entre os faltantes pelos esperados representa o percentual de não cumprimento, e o SLA do dia para a organização é calculado por **\[1-(não pareados/esperados)\]\*100**
    

Em um exemplo prático:

-   Apuração em 11/08/2025 para o Banco X
    
-   Quantidade de reportes transacionados de 03/08/2025 enviados pelo banco X até 10/08/2025 para o endpoint /payments, método POST com status PAIRED --> 12
    
-   Quantidade de reportes transacionados de 03/08/2025 enviados pelo banco X até 10/08/2025 para o endpoint /payments, método POST com status PAIRED\_INCONSISTENT cujo role é CLIENT, statusCode = 408 e processTimeSpan >= 15.000 --> 3
    
-   Total de reportes enviados = 12 + 3 = 15
    
-   Quantidade de reportes transacionados de 03/08/2025 enviados contra o Banco X, endpoint /payments, método POST e que não foram pareados (status UNPAIRED) --> 3
    
-   Quantidade de reportes transacionados de 03/08/2025 enviados pelo banco X até 10/08/2025 para o endpoint /payments, método POST com status PAIRED\_INCONSISTENT e que não se enquadram no critério role = CLIENT, statusCode = 408 e processTimeSpan >= 15.000 --> 2
    
-   Total de reportes não pareados = 3+ 2 = 5
    
-   Total de reportes esperados transacionados em 03/08/2025 = 15 +5 = 20
    
-   SLA do Banco X de 03/08/2025 para o endpoint /payments e método POST = \[1 - (5/20)\] \* 100 = 75%
    
-   Neste exemplo, o Banco X receberá um ticket de não cumprimento do SLA de 99%
    

## **Pontos importantes**

-   O envio do ticket ocorre se o total reportado pela organização para qualquer endpoint e contra a organização estiver abaixo de 99% durante 7 dias a partir da data de transação, independente do total de envios realizados pela organização no dia. 
    
-   Neste caso, se uma organização enviar reportes de 10 endpoints diferentes mas 1 deles estiver com SLA abaixo de 99%, o ticket será enviado independente do percentual dos outros endpoints.
    

## **Arquivo de evidências**

Todo ticket aberto possui anexado um arquivo de evidências, onde são listados até 5 fapiInteractionId para cada caso encontrado por dia, para facilitar a investigação das causas pelas organizações.

**Campos do arquivo de evidências**  

-   org\_reportada: organização que não enviou o reporte, identificado através de reportes onde ela é a contraparte faltante no pareamento
    
-   nome\_reportado: nome da organização que não enviou o reporte
    
-   data\_referencia: data da transação do reporte no formato GMT
    
-   endpoint: endpoint do reporte que não cumpriu o SLA
    
-   httpmethod: método do reporte que não cumpriu o SLA
    
-   clientorgid: id da organização identificada com client no reporte encontrado contra a organização notificada
    
-   serverorgid: id da organização identificada com server no reporte encontrado contra a organização notificada
    
-   perc\_sla\_metodo\_endpoint: percentual calculado do SLA por método e endpoint
    
-   perc\_unpaired\_inconistent: percentual dos reportes com status PAIRED\_INCONSISTENT e UNPAIRED na data de referência
    
-   total\_paired: total de reportes com status PAIRED
    
-   total\_paired\_inconsistent: total de reportes com status PAIRED\_INCOSNSISTENT
    
-   total\_unpaired: total de reportes com status UNPAIRED (reportados contra a organização que recebeu o ticket)
    
-   evidencias\_de\_xfapi: até 5 xfapis aleatórios que violaram o SLA ou os percentuais de UNPAIRED ou PAIRED\_INCONSISTENT
