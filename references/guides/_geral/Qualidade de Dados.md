# Qualidade de Dados

v 1.00

## **Objetivo**   

Apontar os casos em que a qualidade dos dados dos reportes enviados pelas organizações dentro de um determinado período não cumpriu as regras definidas.

Para melhor visualização dos dados, é possível consultar os detalhes no Dashboard de Monitoramento Operacional - Aba Qualidade de Reportes

## **Escopo**   

São analisados os dados (comuns e additionalinfo) dos reportes de Dados Transacionais e Cadastrais (fases 2 e 4b) e Dados de Pagamentos (Fase 3), Hybridflow, Segurança e Estoque de Consentimentos.

## **Terminologia**   

Os termos abaixo estão no contexto da Plataforma de Coleta de Métricas, que por sua vez está no contexto do Open Finance Brasil.  

**Client e Server**  

Em uma interação, a parte que solicita os dados é chamada de _client_, ao passo que a parte que devolve os dados é _server_. Portanto, supondo que A faça uma consulta em B pelos dados de uma conta, esses dados serão transmitidos por quem recebeu a solicitação, e recebidos por quem a fez. Neste caso, A é o _client_ e B é o _server_.  

## **Motivos da crítica de qualidade**

Os motivos de crítica de qualidade de um reporte dependem de regras específicas para cada campo de cada API. As regras de validação para cada campo podem ser consultadas em em cada domínio: [https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/1215135767?draftShareId=7d7a2fd7-611e-419d-8342-6729b93eaf62](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/1215135767?draftShareId=7d7a2fd7-611e-419d-8342-6729b93eaf62)

## **Arquivo de evidências**

Todo ticket aberto possui anexado um arquivo de evidências, onde são listados até 5 fapiInteractionId para cada caso encontrado por dia, para facilitar a investigação das causas pelas organizações.

**Campos do arquivo de evidências**  

-   role, orgid, nome: informações da organização que enviou os dados
    
-   data\_referencia: data GMT do envio do reporte
    
-   data\_deescartado: data em que foi feito o descarte do reporte
    
-   serverorgid e clientorgid: dados das organizações envolvidas na comuicação
    
-   api\_family, api\_version, endpoint, httpmethod, statuscode: identificação do reporte enviado
    
-   \*\_status: campo ou additionalinfo que foi identificado como fora da qualidade establelecida pelo ecossistema OFB
    
-   evidencias\_de\_fapi\_\*: lista de até 5 xfapis que foram criticados pelos motivos apresentados em cada campo/additionalinfo. No caso de Hybridflow, são os reportid relacionados.
