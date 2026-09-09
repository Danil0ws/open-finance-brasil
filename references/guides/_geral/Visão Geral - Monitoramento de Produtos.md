# Visão Geral - Monitoramento de Produtos

:info:atlassian-info#F4F5F7wide180016falsenonelisttrue

# 1\. Controle de Versão

**Versão**

**Data**

**Resumo das Alterações**

1

29 de jul. de 2026

Versão inicial

# 2\. Introdução e Objetivos

Esta aba do painel tem como objetivo apresentar uma visão geral do sistema e dos conglomerados, com foco em volume, performance e conformidade, apoiando as análises relacionadas ao monitoramento dos cinco produtos Open Finance: Dados de Clientes, Pagamento sem Redirecionamento, Pagamento com Redirecionamento, Pix Automático e Transferências Inteligentes.

# 3\. Interpretação dos Dados no Painel

As informações contidas neste item têm como objetivo ajudar o usuário a compreender cada um dos visuais e campos exibidos na aba **“Visão Geral”** do painel **\[BSC\] Produtos.**

## 3.1. Controles

wide1800

O painel é **interativo.** Seleções realizadas sobre linhas de tabelas interferem nos filtros aplicados nas visões posteriores. Para retornar a visão sem filtros basta selecionar “Redefinir para original”.

![img1.png](images/img1.png)

Desta forma, têm-se em “**Controles**”:

![Captura de tela 2026-08-03 152620-20260803-182639.png](images/Captura%20de%20tela%202026-08-03%20152620-20260803-182639.png)wide1800

Ao clicar nos três pontos ao lado de um filtro, é possível **Atualizar** as opções de filtragem disponíveis de acordo com os dados mais recentes ou **Redefinir** o filtro, retornando às opções originalmente carregadas.

**Campos**

**Descrição**

**Visão**

Selecionar a visão para a exibição dos dados

**Referência**

Seleciona o mês de referência truncado no primeiro dia do mês (`YYYY-MM-01`)

**Server**

Selecionar o Conglomerado desejado como _server_

## 3.2. Notas e Volumes por Produto

Neste visual é apresentada a nota consolidada e o total de solicitações de consentimento da apuração mensal, por conglomerado e por produto, conforme os filtros selecionados na seção **“Controles”**.

A nota exibida corresponde à média simples, por produto, dos seguintes indicadores: [**Conversão**](https://openfinancebrasil.atlassian.net/wiki/pages/resumedraft.action?draftId=2024931348&draftShareId=2279d172-b134-4b34-a65b-b21cdfda9fbe&atlOrigin=eyJpIjoiMjUxZDEyZGJlMzI5NDBjOTlhNzczYjIwOTkyOWJhOTciLCJwIjoiYyJ9)**,** [**Efetivação**](https://openfinancebrasil.atlassian.net/wiki/pages/resumedraft.action?draftId=2025685070&draftShareId=84cd85ac-0502-4141-8871-0b2f75a36b3c&atlOrigin=eyJpIjoiOGMxNjhiYmEzMWY3NGE3NmI3MDI4MjMwOTY1ZGFhN2UiLCJwIjoiYyJ9)**,** **Tempo de Resposta****,** **Disponibilidade****,** **Reporte****, UX e FVP**.

O volume de solicitações exibido para cada produto é calculado conforme a metodologia descrita na seção [**Total de Solicitações de Criação de Consentimento**](data/references/guides/2.md) (disponível na documentação de Taxa de Conversão)

![image-20260803-190521.png](images/image-20260803-190521.png)

## 3.3. Monitoramento de Produtos | Notas por Indicador

Este visual detalha a nota consolidada apresentada na visão anterior, exibindo, por produto, as notas de cada indicador que compõe a média geral.

![image-20260803-190725.png](images/image-20260803-190725.png)

## 3.4. Média Geral por Produtos

Esta visão consolida as notas por conglomerado e produto, oferecendo uma perspectiva geral de monitoramento do desempenho e facilitando a identificação de pontos de atenção e oportunidades de melhoria.

![image-20260803-194708.png](images/image-20260803-194708.png)

# 4\. Referências Normativas

-   Instrução Normativa BCB nº 706, de 29 de janeiro de 2026 – Manual de Monitoramento do Open Finance, versão 3.0
    

-   Resolução Conjunta nº 1, de 4 de maio de 2020 – Disposições gerais sobre implementação do Open Finance
    

-   Resolução BCB nº 32, de 29 de outubro de 2020 – Requisitos técnicos e procedimentos operacionais do Open Finance
    

-   Guia de Itens Monitorados – Taxa de Conversão (Área do Desenvolvedor do Open Finance Brasil, item 2.6.2)
