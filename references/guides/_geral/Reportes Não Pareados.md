# Reportes Não Pareados

v 1.00

## **Objetivo**   

Apontar os casos em que não houve o pareamento de reportes enviados contra as organizações dentro de um determinado período.

Para melhor visualização dos dados, é possível consultar os detalhes no Dashboard de Monitoramento Operacional - Aba Reportes Não Enviados.

## **Escopo**   

São analisados o pareamento dos reportes de Dados Transacionais e Cadastrais (fases 2 e 4b) e Dados de Pagamentos (Fase 3).

## **Terminologia**   

Os termos abaixo estão no contexto da Plataforma de Coleta de Métricas, que por sua vez está no contexto do Open Finance Brasil.  

**Client e Server**  

Em uma interação, a parte que solicita os dados é chamada de _client_, ao passo que a parte que devolve os dados é _server_. Portanto, supondo que A faça uma consulta em B pelos dados de uma conta, esses dados serão transmitidos por quem recebeu a solicitação, e recebidos por quem a fez. Neste caso, A é o _client_ e B é o _server_.  

**Faltante**

Quando uma organização envia um reporte contra uma outra organização, caso esta última não envie sua contraparte ela será considerada _faltante_ no processo de pareamento.

## **Percentual de pareamento**

O percentual de pareamento é calculado levando-se em conta a quantidade de reportes enviados contra uma organização (total esperado) e sua relação com a quantidade não enviada por esta última (total faltante). É calculado pela fórmula abaixo: 

![image-20250812-170813.png](images/image-20250812-170813.png)

De acordo com a Normativa 575 do Banco Central, o percentual esperado de pareamento é de no mínimo 95% desde 01/07/2025.

## **Identificação do não-paraemento**

O processo de identificação do não-pareamento por organização é apurado da seguinte maneira:

![image-20250812-170639.png](images/image-20250812-170639.png)

Neste exemplo, olhando para a organização A, vemos que foram enviados contra ela 5 reportes (2,3,4,5 e 8), sendo que somente 2 (3 e 5) foram enviados pela organização A. Note que, olhando para a organização A como faltante, os reportes 6 e 7 não são considerados, pois são comunicações entre outras organizações.

Assim, teríamos um percentual de não pareamento igual a 2 / 5 = 40%, portanto fora do mínimo esperado e passível de recebimento de ticket.

## **Arquivo de evidências**

Todo ticket aberto possui anexado um arquivo de evidências, onde são listados até 5 fapiInteractionId para cada caso encontrado por dia, para facilitar a investigação das causas pelas organizações.

**Campos do arquivo de evidências**  

-   org\_faltante, nome\_faltante, role\_faltante: informações da organização que não enviou os dados
    
-   data\_referencia: data GMT do envio do reporte
    
-   api\_family, api\_version, endpoint, httpmethod, statuscode: identificação do reporte enviado
    
-   contagem\_unpaired\_referencia: quantidade de reportes não pareados na data de referência
    
-   contagem\_chamadas\_referencia: quantidade de reportes total na data de referência (pareados, pareados inconsistentes e não pareados)
    
-   perc\_unpaired\_referencia: percentual de não-pareamento na data de referência
    
-   contagem\_total\_unpaired, contagem\_total\_chamadas, perc\_total\_unpaired: valores de referência da API no período selecionado
    
-   evidencias\_de\_xfapi: lista de até 5 xfapis que não estão pareados, informados por outras organizações contra a organização faltante
    

## **Referências**

Fluxo de pareamento de reportes na PCM

Processamento
