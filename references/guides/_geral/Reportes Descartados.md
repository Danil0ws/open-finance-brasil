# Reportes Descartados

v 1.01

## **Objetivo**   

Apontar os casos em que os reportes enviados pelas organizações dentro de um determinado período foram descartados e seus motivos.

Para melhor visualização dos dados, é possível consultar os detalhes no Dashboard de Monitoramento Operacional - Aba Reportes Descartados.

## **Escopo**   

São analisados os descartes dos reportes de Dados Transacionais e Cadastrais (fases 2 e 4b) e Dados de Pagamentos (Fase 3), Hybridflow e Segurança.

## **Terminologia**   

Os termos abaixo estão no contexto da Plataforma de Coleta de Métricas, que por sua vez está no contexto do Open Finance Brasil.  

**Client e Server**  

Em uma interação, a parte que solicita os dados é chamada de _client_, ao passo que a parte que devolve os dados é _server_. Portanto, supondo que A faça uma consulta em B pelos dados de uma conta, esses dados serão transmitidos por quem recebeu a solicitação, e recebidos por quem a fez. Neste caso, A é o _client_ e B é o _server_.  

## **Motivos de descartes**

Os motivos de descarte de um reporte dependem de regras específicas para cada campo de cada API. As regras de descarte para cada campo podem ser consultadas em em cada domínio: [https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/1215135767?draftShareId=7d7a2fd7-611e-419d-8342-6729b93eaf62](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/1215135767?draftShareId=7d7a2fd7-611e-419d-8342-6729b93eaf62).

## **Descarte do reporte**

O processo de identificação e descarte do reporte pode ser encontrado em Processamento

## **Arquivo de evidências**

Todo ticket aberto possui anexado um arquivo de evidências, onde são listados até 5 fapiInteractionId para cada caso encontrado por dia, para facilitar a investigação das causas pelas organizações.

**Campos do arquivo de evidências**  

-   role, orgid, nome: informações da organização que enviou os dados
    
-   data\_referencia: data GMT do envio do reporte
    
-   data\_deescartado: data em que foi feito o descarte do reporte
    
-   serverorgid e clientorgid: dados das organizações envolvidas na comuicação
    
-   api\_family, api\_version, endpoint, httpmethod, statuscode: identificação do reporte enviado
    
-   mensagem\_erro\_1, mensagem\_erro\_2, mensagem\_erro\_3, mensagem\_erro\_4: motivo pelo qual o relatório foi descartado; é apresentado em até 4 campos separados porque é possível que o reporte tenha sido descartado por mais de um motivo. Neste caso, cada motivo será demonstrado separadamente
    
-   campo\_error\_1, campo\_erro\_2, campo\_erro\_3, campo\_erro\_4: campo do reporte que foi validado para o desscarte
    
-   evidencias\_de\_xfapi: lista de até 5 xfapis que foram descartados pelos motivos apresentados em cada linha do arquivo de evidências. No caso de Hybridflow, são os reportid relacionados.
    

## **Referências**

Fluxo de pareamento de reportes na PCM

Processamento
