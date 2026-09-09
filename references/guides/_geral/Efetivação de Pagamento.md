# Efetivação de Pagamento

:info:atlassian-info#F4F5F7wide180061falsenonelisttrue

# 1\. Controle de Versão

**Versão**

**Data**

**Resumo das Alterações**

1

05 de ago. de 2026

Versão Inicial

# 2\. Introdução e Objetivos

Esta métrica tem como propósito monitorar a eficiência das jornadas de Pagamentos com Redirecionamento, Pagamentos sem Redirecionamento, Pix Automático e Transferências Inteligentes no ecossistema do Open Finance. O objetivo é assegurar padrões ideais na efetivação e liquidação das transações, refletindo a qualidade, a confiabilidade e a eficácia do processamento financeiro entre as instituições participantes e seus clientes.

wide1030

Nenhuma métrica apresentada neste painel utiliza os dados de instituições marcadas como ambiente de teste (FVP). As instituições desconsideradas correspondem aos seguintes `orgid's`:

-   d7384bd0-842f-43c5-be02-9d2b2d5efc2c
    

-   1dbfe32a-5f1e-4841-a30c-9f1b5f24ad36
    
-   b2a8233c-eda6-4c46-8263-813d71508f1b
    

# 3\. Sobre a Métrica

Esta métrica foca em quatro produtos, cada um representando uma jornada distinta para o cliente.

**I. Pagamentos com redirecionamento:** A Taxa de Efetivação de Pagamentos é calculada com base na proporção de transações liquidadas com sucesso em relação ao número de solicitações de pagamento válidas, direcionadas para a instituição detentora.

**II. Pagamentos sem redirecionamento:** Aplica-se a mesma metodologia de cálculo descrita no item **I**.

**III. Transferências inteligentes:** Aplica-se a mesma metodologia de cálculo descrita no item **I**.

**IV. Pix automático:** A Taxa de Efetivação de Pix Automático é calculada com base na proporção de pagamentos liquidados com sucesso em relação ao número de solicitações válidas de efetivação, direcionadas para a instituição detentora. Para este produto, a análise contempla individualmente os ciclos de cobrança programados (Pix recorrente) e as cobranças avulsas (Pix Avulso), mensurando o sucesso da liquidação na janela temporal de cada ciclo.

wide1800

Somente para o produto **Pagamentos com redirecionamento** ficam **excluídos** do cálculo os fluxos sem redirecionamento (FIDO Flow / JSR)

## **3.1. Fontes informacionais**

A apuração das taxas de efetivação de pagamento e o cálculo correspondente da meta (descrito na [**seção 6.1**](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#6.1.-C%C3%A1lculo-das-Metas-\(TOP-3\))) utilizam como fonte exclusiva de dados a **Plataforma de Coleta de Métricas (PCM)**, uma plataforma centralizada da Estrutura de Governança do Open Finance que coleta as métricas a partir das chamadas de API entre os participantes. 

# 4\. Total de Solicitações de Pagamento

O Total de Solicitações de Pagamento representa o volume de chamadas recebidas pelas APIs de pagamento.

Para operacionalizar o cálculo do total de solicitações de pagamentos, apresentamos a seguir a lógica de códigos aplicável a cada produto:

Pagamento com Redirecionamento1800true serverorgid -- Tratamento de possíveis erros. AND role = 'CLIENT' AND httpmethod = 'POST' AND (additionalinfo\_authorisationflow = 'HYBRID\_FLOW' AND endpoint LIKE '%pix/payments%') -- Endpoint específico para pagamento com redirecionamento     \]\]>Pagamento sem Redirecionamento1800true serverorgid -- Tratamento de possíveis erros. AND role = 'CLIENT' AND httpmethod = 'POST' AND (additionalinfo\_authorisationflow = 'FIDO\_FLOW') -- Endpoint específico para pagamento sem redirecionamento    \]\]>

# 5\. Cálculo da Taxa de Efetivação de Pagamento

#F4F5F7wide1800

**TAXA DE EFETIVAÇÃO DE PAGAMENTO = (QTD DE PAGAMENTOS LIQUIDADOS ) / (QTD DE SOLICITAÇÕES DE PAGAMENTO VÁLIDAS )**

wide1540

A Taxa de Efetivação também pode ser obtida por meio da análise do _funil de efetivação (detalhado na_ [_seção 9.5._](data/references/guides/Efetiva.md)_)_ disponível no painel de produtos, utilizando as etapas do funil na relação a seguir.

**TAXA DE EFETIVAÇÃO = Pagamento Liquidado / (Pagamento Rejeitado + Pagamento Pendente + Pagamento Liquidado)**

## **5.1. Período de apuração**

Antes de detalhar o numerador e o denominador da taxa, é necessário definir o critério de apuração temporal do indicador. As taxas são calculadas **mensalmente**, com base em ciclos semanais que se iniciam aos **sábados** e encerram-se às **sextas-feiras**. Para fins de consolidação, uma semana pertence ao mês de referência quando a sua respectiva **sexta-feira** estiver contida dentro daquele mês. Na prática, a apuração de **junho/2026**, por exemplo, não considera o mês exato (01/06/2026 a 30/06/2026), mas o ciclo operacional compreendido entre **30/05/2026 e 26/06/2026.**

EXEMPLO ILUSTRATIVO1800![ChatGPT Image 3 de ago. de 2026, 17\_44\_32-20260803-204608.png](images/ChatGPT%20Image%203%20de%20ago.%20de%202026,%2017_44_32-20260803-204608.png)

Definição das semanas de um mês de referência:

-   **Maio**: semana 1 (25/04 a 01/05), semana 2 (02/05 a 08/05), semana 3 (09/05 a 15/05), semana 4 (16/05 a 22/05) e semana 5 (23/05 a 29/05).
    
-   **Junho**: semana 1 (30/05 a 05/06), semana 2 (06/06 a 12/06), semana 3 (13/06 a 19/06) e semana 4 (20/06 a 26/06).
    
-   Demais dias de Junho (27-30) entram para a referência de **Julho** 

## **5.2. Denominador: Quantidade de solicitações de pagamento válidas**

O denominador da taxa de efetivação de pagamento parte do total de solicitações de pagamento e aplica filtros obrigatórios de exclusão para todos os produtos, **com exceção** do Item 6 “Referência de pagamento nula ou inválida”, cuja regra atua estritamente para Pix Automático.

Esses critérios garantem que somente as jornadas válidas sejam computadas no cálculo.

Critérios de Exclusão do Denominador (Solicitações Válidas)4000

**Regra**

**Descrição**

1.  **StatusCode diferente de 2xx**
    

Somente são computadas as solicitações cujo _statuscode HTTP_ pertence à família 2xx (200, 201, 204 e demais), indicando que a requisição foi processada com sucesso pela instituição.

Requisições cujo _statuscode_ pertence às famílias 4xx (erros de cliente), 5xx (erros de servidor) ou demais respostas fora da faixa de sucesso são excluídas do denominador, pois indicam falhas técnicas, autorizações inválidas ou indisponibilidade que não representam uma jornada efetiva do cliente.

2.  **Identificadores (ID’s) nulos**
    

Para garantir a rastreabilidade da jornada, são removidos do denominador os registros sem identificação de consentimento. A exclusão da chave do consentimento varia conforme o produto:

-   -   **Pix Automático e Transferência Inteligente:** É efetuada a busca prioritária no parâmetro `ADDITIONALINFO_RECURRINGCONSENTID`, utilizando o `ADDITIONALINFO_CONSENTID` como alternativa secundária (equivalente a `coalesce(ADDITIONALINFO_RECURRINGCONSENTID,ADDITIONALINFO_CONSENTID)`). O registro é descartado somente se ambos resultarem em valor nulo.
        
    -   **Pagamento com Redirecionamento e Sem Redirecionamento:** O registro é desconsiderado caso `ADDITIONALINFO_CONSENTID` não esteja preenchida.
        

3.  **Ausência de Chamada na API de Consulta** (`GET`)
    

Retiramos as chamadas em que a requisição `POST` inicial teve sucesso (`2xx`), mas não houve registro de consultas posteriores via `GET` ou atualizações via `PATCH` na API.

4.  **Usuário com Saldo Insuficiente ou Limite excedido**
    

Excluímos tentativas de pagamento em que a transação foi rejeitada pela instituição detentora por razões de saldo insuficiente por parte do usuário ou estouro de limites preestabelecidos. Esses casos são identificados a partir da `ADDITIONALINFO_REJECTIONREASONCODE` com preenchimento “SALDO\_INSUFICIENTE” ou “VALOR\_ACIMA\_LIMITE”.

5.  **Pagamentos cancelados**
    

Excluímos tentativas de pagamento que foram canceladas antes da sua efetiva liquidação. Esses casos são identificados a partir da `ADDITIONALINFO_STATUS` com preenchimento “CANC”.

6.  **Referência de pagamento nula ou inválida**
    

**Esta regra é exclusiva para o Pix Automático**, produto que depende do atributo `ADDITIONALINFO_PAYMENTREFERENCE` para identificar a periodicidade e enquadrar a transação no ciclo correto. São desconsideradas do cálculo todas as requisições em que esse campo está ausente (`NULL`) ou preenchido fora dos padrões normativos.

Para ser considerado válido, o campo deve conter o valor `'zero'` (indicando cobrança avulsa) ou seguir a estrutura ISO de data e intervalo temporal `YYYY-MM-DDP{N}{T}` (ex: `2026-05-01P1M` para cobrança mensal), onde a data representa o início do ciclo, `P` o indicador de período, `{N}` a quantidade e `{T}` a unidade de tempo (`M` para mês, `W` para semana, `D` para dia e `Y` para ano). Qualquer preenchimento fora desse formato é classificado como inválido e removido do indicador.

## **5.3. Numerador - Quantidade de pagamentos liquidados**

O numerador da taxa de efetivação de pagamento contabiliza o total de transações liquidadas com sucesso a partir das solicitações válidas (descritas no [**item 5.2**](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#5.2.-Denominador%3A-Quantidade-de-solicita%C3%A7%C3%B5es-de-pagamento-v%C3%A1lidas) deste documento). Considera-se um pagamento efetivamente liquidado quando o campo`ADDITIONALINFO_STATUS` apresenta “`ACSC`" em seu preenchimento.

# 6\. Interpretação dos Resultados

Tendo estabelecido a metodologia de apuração da taxa de efetivação de pagamento, torna-se necessário definir os parâmetros que determinam se o desempenho do participante está adequado aos padrões do ecossistema. Esse acompanhamento é estruturado a partir de três métricas de referência: a **Meta (ou Top 3)**, a **Taxa de Tolerância** e a **Taxa de Diagnóstico**, detalhadas a seguir.

## 6.1. Cálculo das Metas (TOP 3)

Essa métrica define o benchmark de excelência do mercado e é calculado da seguinte forma:

1.  Calcula-se a taxa de efetivação em uma janela de 3 meses, incluindo o mês de referência, para cada conglomerado;
    
2.  Dentre os 19 maiores conglomerados, identificam-se as instituições com as três maiores taxas de efetivação;
    
3.  Calcula-se a taxa ponderada dessas três maiores taxas, definindo-se a meta Top 3;
    
4.  Esse valor serve de referência para a definição dos demais limiares
    

## 6.2. Taxa de Tolerância

A Taxa de Tolerância é o piso de conformidade. Instituições cuja taxa de efetivação se mantiver acima dela são consideradas conformes. Ela é obtida tomando-se 80% da Taxa Top 3 e subtraindo-se 3 pontos percentuais, para acomodar pequenas variações operacionais.

#F4F5F7wide1800

**TAXA DE TOLERÂNCIA = (80% × TAXA TOP 3) − 3 p.p**

## 6.3 Taxa de Diagnóstico

A Taxa de Diagnóstico é o limiar inferior de severidade. Se a taxa de efetivação de uma instituição cair abaixo dela, será necessária uma avaliação independente por empresa especializada para diagnosticar e corrigir os problemas subjacentes da jornada.

#F4F5F7wide1800

**TAXA DE DIAGNÓSTICO= 60% × (80% × TAXA TOP 3) = 48% × TAXA TOP 3**

## 6.4. Limiares Estabelecidos

Com base nas taxas calculadas acima, a instituição participante pode se enquadrar em um de três estados de conformidade apresentados abaixo.

**Estado**

**Condição**

**Tratamento**

**Conforme**

Taxa da instituição ≥ Taxa de Tolerância

Nenhuma ação regulatória é disparada

**Desconforme**

Taxa de Diagnóstico ≤ Taxa da instituição < Taxa de Tolerância

A instituição deve justificar porque se encontra nessa situação

**Diagnóstico**

Taxa da instituição < Taxa de Diagnóstico

A instituição deve adotar ações corretivas para retornar ao patamar de conformidade

# 7\. Cálculo das Notas

A nota (0 a 10) traduz a taxa de efetivação — _numerador ÷ solicitações válidas_ — em escala de conformidade, ancorada em duas metas: **Taxa de Diagnóstico** (piso) e **Taxa de Tolerância** (nota 7).

-   **Taxa da instituição < Diagnóstico → nota 0** (Falha Total)
    

-   **Taxa Diagnóstico ≤ Taxa da instituição < Taxa Tolerância → nota 0 a 7:** (Taxa − Tx. Diagnóstico) × 7 ÷ (Tx. Tolerância − Diagnóstico)
    

-   **Tolerância ≤ Taxa da instituição** **< 100% → nota 7 a 10:** 7 + (Taxa − Tx. Tolerância) × 3 ÷ (1 − Tx. Tolerância)
    

-   **Taxa da instituição ≥ 100% → nota 10**
    
-   **Sem solicitações válidas → sem nota**
    

**A nota é truncada** em 1 casa decimal (não arredondada) — por isso a média do sistema não cai exatamente sobre as linhas inteiras.

**Faixas:** **Conforme** (7–10)**Não Conforme** (0–7) **Diagnóstico**(0)

Abaixo temos um gráfico que mostra esse comportamento.

![image-20260805-165955.png](images/image-20260805-165955.png)

# 8\. Outras métricas do painel

## 8.1. Percentual de solicitações de pagamento válidas

Esta métrica mensura a proporção de requisições de pagamento consideradas válidas em relação ao volume total de solicitações recebidas. Indica a qualidade das chamadas iniciais no ecossistema antes da aplicação de filtros do funil.

#F4F5F7wide1800

**% DE SOLICITAÇÕES VÁLIDAS = (QTD DE SOLICITAÇÕES VÁLIDAS ) / (TOTAL DE SOLICITAÇÕES DE PAGAMENTO)**

wide1540

O percentual de solicitações de pagamento válidas também pode ser obtido por meio da análise do _funil de efetivação (detalhado na_ [_seção 9.5._](data/references/guides/Efetiva.md)_)_ disponível no painel de produtos, utilizando as etapas do funil na relação a seguir.

**% PERCENTUAL DE SOLICITAÇÕES VÁLIDAS = (Pagamento Rejeitado + Pagamento Pendente + Pagamento Liquidado) / Total**

## 8.2. Coeficiente de Impacto

Esta métrica quantifica a perda total de solicitações ao longo do funil de efetivação. Corresponde ao volume de solicitações de pagamento que, embora tenham sido consideradas válidas na entrada, não atingiram o status final de autorização. O Coeficiente tem como objetivo mensurar o quanto a Taxa de Efetivação da instituição analisada foi prejudicada por um conjunto de solicitações com um _client_ específico. Dessa forma, na visão **“Detalhamento dos clients”** ([**Seção 9.4**](data/references/guides/Efetiva.md)**)** no painel de produtos, os _clients_ são exibidos em ordem decrescente de acordo com o Coeficiente de Impacto.

#F4F5F7wide1800

**COEFICIENTE DE IMPACTO = (QTD DE SOLICITAÇÕES VÁLIDAS) - (QTD DE PAGAMENTOS LIQUIDADOS)**

# 9\. Interpretação dos Dados no Painel

## 9.1. Controles

wide1800

O painel é **interativo.** Seleções realizadas sobre linhas de tabelas interferem nos filtros aplicados nas visões posteriores. Para retornar a visão sem filtros basta selecionar “Redefinir para original”.

![image-20260818-173803.png](images/image-20260818-173803.png)

Desta forma, têm-se em “**Controles**”:

![image-20260818-173915.png](images/image-20260818-173915.png)wide1800

Ao clicar nos três pontos ao lado de um filtro, é possível **Atualizar** as opções de filtragem disponíveis de acordo com os dados mais recentes ou **Redefinir** o filtro, retornando às opções originalmente carregadas.

**Campos**

**Descrição**

**Visão**

Informar a visão para a exibição dos dados

**Referência**

Seleciona o mês de referência truncado no primeiro dia do mês (`YYYY-MM-01`), considerando a janela de datas resultante da regra do período de apuração (descrita na [seção 5.1](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#5.1.-Per%C3%ADodo-de-apura%C3%A7%C3%A3o) deste documento).

**Produto**

Seleciona o produto desejado, podendo ser pagamento com redirecionamento, pagamento sem redirecionamento, pix automático ou transferências inteligentes.

**Referência do Pagamento**

Quando o produto é Pix Automático, seleciona se o pix é avulso ou recorrente. Para os demais produtos, não há abertura.

**Papel do Conglomerado**

Seleciona se o conglomerado desejado será _server ou client_

**Conglomerado**

Seleciona o conglomerado desejado com o papel definido no controle “Papel do Conglomerado”

**Contraparte**

Seleciona o conglomerado que atua como contraparte do conglomerado selecionado.  
_Ex.: se o papel do conglomerado selecionado é server, sua contraparte será um conglomerado que atua como client._

## 9.2. Visão de Notas e taxas mensais

O painel inicia apresentando o **resultado consolidado da apuração mensal**, que é atualizado conforme os filtros selecionados em **“Controles”**.

A visão apresentada considera o **papel do conglomerado selecionado**: se o filtro **“Papel do Conglomerado”** estiver definido como **server**, os cards apresentarão o diagnóstico dos _servers_. Da mesma forma, se o papel selecionado for **client**, todos os cards apresentarão o diagnóstico dos _clients_.

Essa visão está organizada em _cards_ informativos que cobrem três frentes: o desempenho individual do conglomerado (Nota e Taxa de Efetivação), os parâmetros de referência e governança da Open Finance (TOP 3, Taxa de Tolerância e Taxa de Diagnóstico) e a volumetria de solicitações de pagamentos registradas da PCM (Total de Solicitações e % Solicitações Válidas).

![image-20260805-010651.png](images/image-20260805-010651.png)

## 9.3. Visão de detalhamento semanal

A seção apresenta o acompanhamento da evolução temporal (considerando o papel do conglomerado selecionado) subdividido em duas visões analíticas:

**a) Volumetria de Solicitações de Pagamento (Fonte PCM):** Alimentado exclusivamente por dados da PCM, essa visão contempla um gráfico de barras empilhadas combinado a uma linha de tendência. As barras representam o volume total de solicitações ([**seção 4**](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#4.-Total-de-Solicita%C3%A7%C3%B5es-de-Pagamento)) segregados em chamadas válidas (em verde, detalhadas na [**seção 5.2**](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#5.2.-Denominador%3A-Quantidade-de-solicita%C3%A7%C3%B5es-de-pagamento-v%C3%A1lidas)) e inválidas (em cinza), enquanto a linha indica o percentual de solicitações válidas (solicitações válidas/total de solicitações de pagamento)

![image-20260805-011015.png](images/image-20260805-011015.png)

**b) Comparativo da Taxa de Efetivação:** Exibe a evolução histórica da Taxa de Efetivação via PCM.

Além disso, as linhas pontilhadas de referência indicam os limiares de governança (**TOP 3**, **Taxa de Tolerância** e **Taxa de Diagnóstico**), viabilizando a verificação imediata da conformidade da instituição, conforme detalhado na [seção 6.1](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#6.1.-C%C3%A1lculo-das-Metas-\(TOP-3\)).

![image-20260805-011336.png](images/image-20260805-011336.png)

## 9.4. Visão Geral das Contrapartes

Esta visão apresenta o desdobramento da Taxa de Conversão e da Quantidade de Solicitações de Consentimento por contraparte, conforme o filtro selecionado.

A contraparte apresentada será definida de acordo com o papel do conglomerado selecionado: se o papel for client, serão apresentados os resultados das suas contrapartes server. Da mesma forma, se o papel selecionado for server, a visão apresentará os resultados das contrapartes client.

Vale ressaltar que a exibição dos _clients_ ocorre em ordem decrescente com base no Coeficiente de Impacto, conforme especificado na [seção 8.2](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#8.2.-Coeficiente-de-Impacto)

![image-20260818-180834.png](images/image-20260818-180834.png)

## 9.5. Funil de Taxa de Efetivação

Esta seção apresenta a jornada de efetivação de pagamentos em formato de funil, mapeando o fluxo desde o volume total de solicitações iniciais até a efetivação do pagamento. O objetivo é evidenciar os pontos de quebra ao longo do processo, identificando em quais etapas específicas os pagamentos foram classificadas como **inválidos** (nível 1 ao nível 5), **não liquidados** (nível 6 e 7) ou **liquidados** (nível 99).

A seguir, são detalhadas as etapas que compõem este funil:

**Nível**

**Descrição**

0.  Total
    

Representa o total de solicitações de pagamento, sendo a soma de todos os outros níveis do funil.

Detalhado na [seção 4.0](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#4.-Total-de-Solicita%C3%A7%C3%B5es-de-Pagamento) deste documento.

1.  StatusCode sem Sucesso
    

Todas as solicitações com StatusCode que **NÃO** pertence à família 2xx (200, 201, 204 e demais).

Para mais detalhes, consulte a [seção 5.2](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#5.2.-Denominador%3A-Quantidade-de-solicita%C3%A7%C3%B5es-de-pagamento-v%C3%A1lidas) deste documento.

2.  Consentid Nulo
    

Quantidade de identificadores nulos.

Para mais detalhes, consulte a [seção 5.2](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#5.2.-Denominador%3A-Quantidade-de-solicita%C3%A7%C3%B5es-de-pagamento-v%C3%A1lidas) deste documento.

3.  Não solicitou a API no Get
    

Quantidade de solicitações que teve POST, mas a Instituição não realizou a chamada de consulta de status GET para validar a elegibilidade do pagamento ou prosseguir com a efetivação.

4.  Saldo insuficiente/ valor acima do limite
    

Quantidade de rejeições de pagamento porque o usuário não possui saldo disponível na conta corrente/poupança no momento da liquidação ou que o valor da transação excede os limites operacionais estabelecidos.

5.  Pagamento Cancelado
    

Quantidade de pagamentos cancelados.

6.  Pagamento Rejeitado
    

Quantidade de pagamentos rejeitados.

7.  Pagamento Pendente
    

Quantidade de pagamentos que foi devidamente recebido e validado pela Detentora, mas cuja liquidação financeira final ainda está em processamento.

99.  Pagamento Liquidado
     

Representa a etapa final do funil. Após a filtragem sequencial de todas as invalidades e pagamentos não liquidados, resta o volume exclusivamente de liquidados com sucesso.

Vale ressaltar que através do funil, se pode chegar a **taxa de efetivação**, cujo numerador corresponde ao último nível e o denominador, à soma dos dois últimos níveis, conforme ilustrado na imagem abaixo.

![Rascunho - Quadro 3-20260805-140111.jpg](images/Rascunho%20-%20Quadro%203-20260805-140111.jpg)

Além da taxa de efetivação, também é possível chegar ao **percentual de solicitações válidas** cujo numerador corresponde a soma dos três últimos níveis e o denominador o primeiro nível, conforme ilustrado na imagem abaixo.

![Rascunho - Quadro 3 (1)-20260805-195720.jpg](images/Rascunho%20-%20Quadro%203%20-1--20260805-195720.jpg)

A segunda visão desta seção apresenta a distribuição percentual das etapas do funil ao longo das semanas, estruturada em um gráfico de barras empilhadas normalizado a 100%.

Essa abordagem exibe a representatividade relativa de cada etapa em relação ao total de solicitações recebidas, viabilizando o acompanhamento da tendência temporal de cada categoria e a identificação de variações no comportamento do fluxo semana a semana.

![image-20260805-014832.png](images/image-20260805-014832.png)

wide1800

As datas exibidas no eixo horizontal do gráfico representam o fechamento de cada ciclo semanal, truncadas na sexta-feira da respectiva semana, em conformidade com a regra de período de apuração detalhada na [seção 5.1](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2025685070#5.1.-Per%C3%ADodo-de-apura%C3%A7%C3%A3o)

## 9.6. Distribuição de erros para a etapa de “Pagamento Rejeitado”

As visões desta seção do painel têm como objetivo diagnosticar as causas que impediram a liquidação de um pagamento, bem como a volumetria de solicitações de pagamento por erro e sua representatividade percentual. Por essa razão, a análise abrange exclusivamente as solicitações de pagamento classificadas na etapa **“Pagamento Rejeitado”** do funil. O mapeamento desses motivos é realizado por meio do campo `additionalinfo_rejectionreasoncode`.**Dis**

![image-20260805-015351.png](images/image-20260805-015351.png)wide1800

Para verificar os requisitos de obrigatoriedade dos campos para cada produto, acesse: Regras de Obrigatoriedade (additionalInfo) - SV - Área do Desenvolvedor - Open Finance Brasil - Área do Desenvolvedor

## 9.7. Evidências

Neste visual estão dispostas informações sobre chamadas identificadas (_xfapi_) que tiveram influência negativa sobre a métrica. A aba apresenta amostras de evidências na granularidade de **dia, conglomerado (podendo ser server ou client),** _**contraparte, xfapi**_ **e etapa do funil.**

wide1800

Para consultar os _**xfapis**_ referentes a um conglomerado e uma contraparte específica, considerando um determinado **produto** e **etapa do funil**, siga a sequência abaixo:

1.  Em **Controles**, selecione (clique) o **Item Monitorado, referência e produto** desejado.
    
2.  Na visão **“Visão Geral das Contrapartes”**, selecione (clique) na contraparte desejada.
    
3.  Na visão **“Funil de Conversão”**, selecione (clique) a **etapa do funil** que deseja analisar.
    

![image-20260818-180805.png](images/image-20260818-180805.png)

wide1800

As colunas **“ConsentID”, “Motivo de Erro”** e **“Additionalinfo\_paymentreference”** são preenchidas apenas nas etapas do funil em que essas informações são aplicáveis. Nos demais casos, o valor exibido é **“Não se Aplica”**.

**Campos**

**Descrição**

**Dia**

Data da ocorrência da chamada

**Conglomerado**

Instituição analisada podendo ser server ou client, de acordo com filtro “Papel do Conglomerado”

**Contraparte**

Instituição com a qual a casa se comunicou

**xfapi**

Código de identificação da chamada

**Método**

Método avaliado

**Endpoint**

_endpoint_ avaliado

**StatusCode**

Status retornado pelo servidor

**Funil**

Pontos de quebra ao longo do processo de cálculo da Taxa de Efetivação de Pagamento

**ConsentId**

ID que identifica um consentimento

**Motivo de Erro**

Indica o erro que levou um pagamento a ser rejeitado

**Additionalinfo\_paymentreference**

Indica a referência do pagamento para pix automático

# 10\. Referências Normativas

-   Instrução Normativa BCB nº 706, de 29 de janeiro de 2026 – Manual de Monitoramento do Open Finance, versão 3.0
    

-   Resolução Conjunta nº 1, de 4 de maio de 2020 – Disposições gerais sobre implementação do Open Finance
    

-   Resolução BCB nº 32, de 29 de outubro de 2020 – Requisitos técnicos e procedimentos operacionais do Open Finance
    

-   Guia de Itens Monitorados – Taxa de Conversão (Área do Desenvolvedor do Open Finance Brasil, item 2.6.2)
