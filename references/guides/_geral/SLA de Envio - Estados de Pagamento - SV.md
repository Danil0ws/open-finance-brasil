# SLA de Envio - Estados de Pagamento - SV

v 1.00

## **Objetivo**   

Apontar os casos em que o envio dos reportes pelas organizações não ocorreu dentro do SLA de D+1 até às 8:00.

## **Escopo**   

São analisados envios dos reportes de Estados de Pagamento.

## **Terminologia**   

Os termos abaixo estão no contexto da Plataforma de Coleta de Métricas, que por sua vez está no contexto do Open Finance Brasil.  

**Client e Server**  

Em uma interação, a parte que solicita os dados é chamada de _client_, ao passo que a parte que devolve os dados é _server_. Portanto, supondo que A faça uma consulta em B pelos dados de uma conta, esses dados serão transmitidos por quem recebeu a solicitação, e recebidos por quem a fez. Neste caso, A é o _client_ e B é o _server_.  

## **Forma de avaliação do percentual de SLA**

Diariamente são apurados os reportes que não cumpriram o SLA de envio da seguinte forma:

1.  Contam-se todos os reportes de uma determinada referência, enviados pela organização que foram recebidos pela PCM após D+1 às 08:00 (GMT)
    

Em um exemplo prático:

-   Apuração em 03/08/2025 para o Banco X
    
-   Quantidade de reportes de 01/08/2025 enviados pelo Banco X após 02/08/2025 às 08:00 = 2
    
-   Neste exemplo, o Banco X receberá um ticket de não cumprimento do SLA
    

## **Pontos importantes**

-   Diferentemente do cálculo de SLA de 95% até D+1 08:00, não existe pareamento para reportes de Estado de Pagamento e, por consequência, não existem reportes “faltantes” na visão de contraparte. 
    
-   Não existe um percentual mínimo, envio recebimento de reporte fora do SLA de D+1 08:00 provoca a emissão de ticket.
    

## **Arquivo de evidências**

Todo ticket aberto possui anexado um arquivo de evidências, onde são listados até 5 reportId para cada caso encontrado por dia, para facilitar a investigação das causas pelas organizações.

**Campos do arquivo de evidências**  

-   oragnisation\_id: id da organização reportadora do reporte
    
-   name: nome da organização reportadora do reporte
    
-   data\_ref: data de referência do reporte (eventDateTime)
    
-   qtd\_reportes\_fora\_sla: quantidade de reportes enviados fora do SLA de D+1 08:00
    
-   evidencias\_reports: reportId de exemplo
