# Visão Geral Plano de Adequação

:info:atlassian-info#F4F5F7none

# 1\. Controle de Versão

**Versão**

**Data**

**Resumo das Alterações**

1

30 de ago. de 2026

Versão inicial da documentação

# 2\. Introdução e Objetivos

O Painel Gestão de Consequências tem como objetivo apresentar uma visão consolidada dos Planos de Adequação em aberto, mediante as desconformidades identificadas nos itens monitorados das instituições participantes, permitindo o acompanhamento do ciclo de monitoramento e gestão de consequências previsto na Política de Monitoramento do Open Finance.

O painel apoia tanto a leitura executiva (quantas instituições estão em situação regular, quais precisam de atenção e onde estão os maiores riscos) quanto a investigação operacional (detalhamento de tickets, itens monitorados em desconformidade e prazos de SLA), possibilitando a priorização das ações de acompanhamento pelo analista responsável.

# 3\. Interpretação dos Dados no Painel

As informações contidas nesse item têm como objetivo ajudar o usuário a compreender cada um dos visuais e campos exibidos no painel.

## 3.1. Controles

O painel é **interativo.** Seleções realizadas sobre linhas de tabelas interferem nos filtros aplicados nas visões posteriores. Para retornar a visão sem filtros basta selecionar “Redefinir para original”.

![image-20260901-181848.png](images/image-20260901-181848.png)

Desta forma, têm-se em **“Controles”**:

![image-20260901-182301.png](images/image-20260901-182301.png)

Ao clicar nos três pontos ao lado de um filtro, é possível **Atualizar** as opções de filtragem disponíveis de acordo com os dados mais recentes ou **Redefinir** o filtro, retornando às opções originalmente carregadas.

**Especificação dos filtros:**

**Campos**

**Descrição**

**Conglomerado**

Seleciona o Conglomerado desejado.

**Instituição**

Seleciona a Instituição desejada.

**Especialista**

Seleciona o especialista de monitoramento atribuído ao plano.

**Status do Plano**

Seleciona a categoria de distribuição do plano.

**Status do Atendimento**

Seleciona o status do atendimento.

**Mês de Referência**

Seleciona do mês de referência na qual foi feita a abertura do plano.

**Amplitude do Cronograma**

Seleciona a duração do cronograma do plano, do início ao fim das ações previstas.

##  3.2. Visão Geral dos Planos de Adequação

Esta seção apresenta os indicadores consolidados (KPIs) e a distribuição geral dos Planos de Adequação em aberto.

![image-20260901-183124.png](images/image-20260901-183124.png)

## Indicadores (KPIs)

**Indicador**

**Descrição**

**Instituições com Planos Abertos**

Número de instituições distintas com ao menos um Plano de Adequação em aberto (ticket não encerrado ou cancelado).

**Total de Planos**

Quantidade total de Planos de Adequação considerados no recorte atual do painel, somando todos os status (Recusado, Não Classificado, Envio pendente, Em análise técnica, Em análise e Aprovado).

**Planos com Primeira Ocorrência**

Quantidade de planos cujo campo de ocorrência reiterada está classificado como "Primeira", mediante a recorrência de desconformidade em algum item monitorado.

**Planos com Segunda Ocorrência**

Quantidade de planos cujo campo de ocorrência reiterada está classificado como "Segunda" (reincidência), informando que mesmo após o término do plano de adequação de primeira ocorrência a instituição continuou com desconformidade nos itens monitorados.

**Tickets Consolidadores em Plano**

Quantidade de tickets consolidadores que se converteram em Plano de Adequação (ocorrência reiterada em branco), geralmente por ausência de resposta da instituição ao relatório de desconformidade.

**Planos com Amplitude ≥ 180 dias**

Quantidade de planos cujo cronograma de ações (da data de vencimento da primeira à da última ação) tem amplitude igual ou superior a 180 dias.

### Gráfico "Distribuição dos Planos"

Gráfico do tipo waterfall (cascata) que decompõe o Total de Planos por status atual: Recusado, Não Classificado, Envio pendente, Em análise técnica, Em análise e Aprovado, somando à barra de Total ao final. Permite visualizar de forma rápida a proporção de planos em cada etapa do fluxo de tratamento.

**Cada status tem a finalidade de classificar a real situação do ticket dentro do fluxo de tratamento do plano:**

●      **Recusado e Envio Pendente:** existe alguma pendência da instituição.

●      **Em Análise Técnica e Em Análise**: o plano está sendo verificado pelo time de monitoramento.

●      **Não Classificado:** planos que acabaram de entrar no sistema por meio da integração com o ServiceDesk e ainda não foram analisados.

●      **Aprovado:** planos já validados pelo time de monitoramento, aguardando a implementação das correções pela instituição.

##  3.3. Classificação dos Status e Distribuição por Planos

O painel classifica cada Plano de Adequação em um dos três níveis de status executivo, exibidos por cor:

●      🔴Crítico: planos em segunda ocorrência em aberto, ou planos com algum prazo de SLA vencido.

●      🟡Atenção: planos em tratamento (em análise, envio pendente, recusado), ou que estejam com o prazo de SLA próximo do vencimento (até 7 dias).

●      🟢Regular: planos aprovados e dentro do prazo, sem pendências.

![image-20260901-183559.png](images/image-20260901-183559.png)

A tabela "Distribuição dos Status por Planos" cruza esses três níveis (Crítico/Atenção/Regular) com o status do plano (Recusado, Não Classificado, Envio pendente, Em análise técnica, Em análise, Aprovado), permitindo identificar em qual etapa do fluxo se concentram os planos críticos e os planos que demandam atenção.

# 4\. Itens Monitorados

Esta seção detalha como as desconformidades identificadas se distribuem dentro de cada Plano de Adequação. Como um mesmo plano pode reunir mais de um item monitorado, o total de itens pode ser maior que o total de planos.

![image-20260901-185256.png](images/image-20260901-185256.png)

## 4.1. Gráfico de evolução mensal

Gráfico de barras empilhadas que mostra a evolução mês a mês (2026-01 a 2026-08, no exemplo) da quantidade de tickets por grupo de item monitorado: Governança de APIs, Jornada, Qualidade de Dados, Resiliência de APIs e Taxa de Conversão.

## 4.2. Tabela Distribuição dos Itens Monitorados

Lista, para cada item monitorado (ex.: "2.3. Metas de prazo máximo para atendimento de tickets", "2.1. I. Tempo de resposta das APIs"), o grupo ao qual pertence, o número de tickets (Nº Ticket) e o percentual sobre o total geral de ocorrências de itens monitorados.

# 5\. Tabelas de Detalhamento

## 5.1. Detalhamento por Conglomerado

Tabela que consolida, por conglomerado, a quantidade de planos em cada status (Recusados, Não Classificados, Envio Pendente, Em Análise Técnica, Em Análise, Aprovados), além da quantidade de planos em Primeira Ocorrência, Segunda Ocorrência e Tickets Consolidador em Plano. A linha "Total" reflete a soma de todos os conglomerados e deve bater com os KPIs da seção 3.2. Cada conglomerado pode ser expandido (ícone "+") para detalhamento por instituição.

A tabela conta com **drill down**: ao clicar em uma instituição, o painel passa a exibir apenas os planos daquela instituição, e esse filtro é refletido em todos os demais visuais da aba.

![imagem (2)-20260901-192131.png](images/imagem%20-2--20260901-192131.png)

## 5.2. Tabela de Detalhamento Operacional

Tabela de detalhamento que reúne, todos os planos e as principais informações necessárias para a análise de cada um. Ao clicar em um plano, o usuário é direcionado automaticamente ao portal do ServiceDesk, onde pode visualizar o ticket completo do Plano de Adequação.

![imagem (2)-20260901-200538.png](images/imagem%20-2--20260901-200538.png)

**Especificação dos campos:**

**Campo**

**Descrição**

**Instituição**

Instituição participante à qual o ticket está associado.

**Ticket ID**

Identificador do ticket no ServiceDesk.

**Prazo de SLA**

Data-limite do SLA para atendimento do ticket.

**SLA Estimado**

Classificação calculada do SLA: Dentro do SLA, Fora do SLA, Encerrado Dentro do SLA, Encerrado Fora do SLA ou Cancelado.

**Data de Solicitação**

Data de abertura do ticket.

**Data de Atualização**

Data da última atualização do ticket.

**Item Monitorado**

Item em desconformidade associado ao ticket.

**Categoria de Terceiro Nível**

Categoria do ticket no ServiceDesk (ex.: Apresentação do Plano de Adequação, Correção do Plano de Adequação).

**Ocorrência Reiterada**

Indica se o plano é de Primeira ou Segunda ocorrência (reincidência); em branco para tickets consolidadores.

**Status Plano**

Status do Plano de Adequação (ex.: Aprovado).

**Status**

Status atual do ticket no ServiceDesk (ex.: AGUARDANDO IMPLEMENTAÇÃO N2).

**Especialista**

Especialista de monitoramento responsável pelo acompanhamento do ticket.

**Ações Preenchidas**

Indica se o cronograma de ações do plano foi preenchido (Sim/Não).

**Prazo Cronograma**

Prazo, em dias, associado ao cronograma de ações do plano.

# 6\. Referência Normativa

●      Política de Monitoramento do Open Finance Brasil, São Paulo, 15 de janeiro de 2026 — Versão 3, aprovada em 15/05/2026 pelo Banco Central do Brasil — especialmente o Capítulo IV, Art. 7º, incisos I a XXIII (fluxo de gestão do monitoramento e de aplicação de medidas: Ticket Consolidador, Relatório de Situação de Desconformidade, Plano de Adequação, cronograma e ocorrência reiterada).
