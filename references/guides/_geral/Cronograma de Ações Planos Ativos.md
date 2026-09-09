# Cronograma de Ações Planos Ativos

:info:atlassian-info#F4F5F7none

# 1\. Controle de Versão

**Versão**

**Data**

**Resumo das Alterações**

1

30 de ago. de 2026

Versão inicial da documentação

# 2\. Introdução e Objetivos

Esta aba tem como objetivo detalhar, em nível granular (ação a ação), o cronograma de ações que compõe cada Plano de Adequação, permitindo acompanhar o andamento das entregas dentro dos prazos estabelecidos.

Ela apoia o acompanhamento operacional do dia a dia da equipe de monitoramento, possibilitando identificar rapidamente ações vencidas ou próximas do vencimento, além de visualizar a carga de trabalho e o desempenho de cada especialista responsável, direcionando a priorização das cobranças e do acompanhamento junto às instituições.

O cronograma detalhado é um conteúdo obrigatório de todo Plano de Adequação apresentado pela instituição (Art. 7º, inciso XIII, alínea "a", da Política de Monitoramento). Após a aprovação do plano, o SLA do ticket passa a observar os prazos e marcos estabelecidos nesse cronograma vigente (Art. 7º, inciso XVII) — ou seja, os campos "Início" e "Vencimento" desta aba refletem os marcos formalmente definidos no cronograma aprovado do plano, e não datas arbitrárias.

# 3\. Interpretação dos Dados no Painel

As informações contidas nesse item têm como objetivo ajudar o usuário a compreender cada um dos visuais e campos exibidos no painel.

## 3.1. Controles

O painel é **interativo.** Seleções realizadas sobre linhas de tabelas interferem nos filtros aplicados nas visões posteriores. Para retornar a visão sem filtros basta selecionar “Redefinir para original”.

![image-20260901-220614.png](images/image-20260901-220614.png)

Ao clicar nos três pontos ao lado de um filtro, é possível **Atualizar** as opções de filtragem disponíveis de acordo com os dados mais recentes ou **Redefinir** o filtro, retornando às opções originalmente carregadas.

**Especificação dos filtros:**

**Campo**

**Descrição**

**Conglomerado**

Filtra as ações pelo conglomerado ao qual a instituição pertence.

**Instituição**

Filtra as ações por instituição participante.

**Especialista**

Filtra as ações pelo especialista de monitoramento responsável pelo acompanhamento.

**Status das Entregas**

Filtra as ações pelo status de entregas (ex.: Atrasado, Concluído, Em Andamento, Não Iniciado.)

**Vencimento**

Filtra as ações pela data de vencimento prevista no cronograma.

## 3.2. Volume das Ações

Indicadores consolidados sobre o cronograma de ações dos Planos de Adequação, considerando o recorte aplicado nos Controles:

![image-20260901-210231.png](images/image-20260901-210231.png)

## Indicadores (KPIs)

**Indicador**

**Descrição**

**Quantidade de Ações**

Total de ações de cronograma cadastradas nos Planos de Adequação, no grão ação (uma linha por ação, podendo haver múltiplas ações por ticket).

**Planos com Ações**

Quantidade de Planos de Adequação (tickets) que possuem ao menos uma ação de cronograma preenchida.

**Vence Hoje**

Quantidade de ações cuja data de vencimento é a data corrente.

**Em Atraso**

Quantidade de ações com data de vencimento ultrapassada e ainda não concluídas.

**Necessita Acompanhamento**

Quantidade de ações marcadas como "Em andamento" pelo especialista, mas que já estão em atraso pela data de vencimento — ou seja, o status não foi atualizado a tempo.

**Instituições com Atraso**

Quantidade de instituições distintas que possuem ao menos uma ação em atraso.

# 4\. Visão Geral do Acompanhamento dos Analistas

![imagem (4)-20260901-192253.png](images/imagem%20-4--20260901-192253.png)

Visual composto pelo um gráfico e uma tabela, ambos com a distribuição das ações de cronograma por especialista de monitoramento responsável.

## **4.1. Distribuição das Ações por Especialista**

Mostra a participação de cada especialista no total de ações de cronograma (1.575 ações, no exemplo), permitindo identificar rapidamente a distribuição de carga entre a equipe.

## **4.2. Tabela de Desempenho por Especialista**

Para cada especialista, são exibidas três colunas: Ações (quantidade total de ações sob sua responsabilidade), % Ações (participação percentual sobre o total) e Méd. Dias Atraso (média de dias de atraso das ações em aberto e atrasadas desse especialista). A linha "Total" consolida os valores da equipe.

Cada especialista pode ser expandido (ícone "+") para visualizar a quantidade de ações em cada status de entrega — Atrasado, Concluído, Dentro do Prazo, Não Iniciado e Vencendo Hoje — detalhando como a carga daquele especialista está distribuída ao longo do fluxo de trabalho.

## 4.3. Detalhamento

Tabela de detalhes (uma linha por ação do cronograma), utilizada para investigação detalhada do andamento de cada Plano de Adequação. Principais campos:

**Campo**

**Descrição**

**Conglomerado**

Conglomerado ao qual a instituição pertence.

**Instituição**

Instituição participante à qual o ticket e a ação estão associados.

**Ticket ID**

Identificador do ticket (Plano de Adequação) no ServiceDesk.

**Item Monitorado**

Item em desconformidade associado ao ticket. Quando o ticket possui múltiplos itens (caso de tickets consolidadores), todos são exibidos concatenados.

**Plano de Adequação**

Classificação do ticket quanto à origem/ocorrência do plano — ex.: "Plano de Adequação - Consolidado" (originado de ticket consolidador, sem resposta prévia da instituição) ou "Plano de Adequação - 2ª Ocorrência" (reincidência).

**Especialista**

Especialista de monitoramento responsável pelo acompanhamento da ação.

**Título**

Título da ação de cronograma, geralmente iniciado pelo código do item monitorado ao qual se refere (ex.: "2.1. I. Correções ...").

**Descrição**

Descrição detalhada do que deve ser entregue naquela ação do cronograma.

**Status Ticket**

Status atual do ticket no ServiceDesk (ex.: AGUARDANDO IMPLEMENTAÇÃO N2).

**Status Ação**

Status da ação informado pelo especialista/instituição (ex.: Concluído, Em andamento).

**Início**

Data de início prevista para a ação.

**Vencimento**

Data de vencimento prevista para a ação.

**Status Entrega**

Status macro da ação dentro do fluxo de tratamento (ex.: Pendente, Concluído, Não Iniciado), indicando em que fase ela se encontra.

**Fila Prioridade**

Classificação de urgência das ações ainda não concluídas, calculada pela proximidade do vencimento, para orientar a priorização do atendimento pelo especialista.

**Observação:** uma ação com Status Ação = "Em andamento" e vencimento já ultrapassado é classificada como "Necessita Acompanhamento" no KPI da seção 4.2, sinalizando que o especialista ainda não atualizou a entrega apesar do prazo vencido.

# 5\. Referências Normativas

●      Política de Monitoramento do Open Finance Brasil, São Paulo, 15 de janeiro de 2026 — Versão 3, aprovada em 15/05/2026 pelo Banco Central do Brasil — especialmente o Capítulo IV, Art. 7º, incisos I a XXIII (fluxo de gestão do monitoramento e de aplicação de medidas: Ticket Consolidador, Relatório de Situação de Desconformidade, Plano de Adequação, cronograma e ocorrência reiterada).
