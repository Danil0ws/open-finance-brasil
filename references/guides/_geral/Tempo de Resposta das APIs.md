# Tempo de Resposta das APIs

## Controle de versão

**Versão**

**Data**

**Resumo das alterações**

1

Versão inicial

2

Segregação da métrica de desempenho de APIs da métrica de disponibilidade de APIs.

Maior detalhamento do cálculo da métrica.

3

Revisão geral do documento

Inclusão do tópico “Interpretação dos Dados no Painel”

## Introdução e Objetivos

Esta métrica visa monitorar se os _endpoints_ das APIs das instituições participantes estão cumprindo os SLAs de tempo de resposta, estabelecidos no Manual de APIs do Open Finance.

Considerando que, o tempo de resposta de cada requisição é o tempo transcorrido entre o recebimento de uma requisição que não ultrapassa os limites de tráfego e o momento em que a requisição é completamente respondida.

## Sobre a Métrica

A métrica de Tempo de Resposta das APIs considera o valor do percentil 95 e o número de requisições ocorridas no dia.

As medições devem ser realizadas de maneira independente para cada versão "_major_" dos _endpoints_ em produção e devem ser consideradas as requisições com todos os códigos de retorno possíveis, **com exceção dos associados a limites de tráfego e limites operacionais**.

**O valor do tempo de resposta a ser considerado para uma requisição é o valor reportado pelo consumidor da API,** ou seja, o valor reportado pela instituição iniciadora de pagamentos nas APIs de “Serviços de Iniciação de Pagamentos” e o valor reportado pela receptora de dados no caso de APIs de "Dados Cadastrais e Transacionais".  

**Na falta de informações dos consumidores, serão utilizadas as informações dos provedores** para o cálculo do SLA de desempenho, ou seja, o valor reportado pela instituição detentora de contas nas APIs de "Serviços de Iniciação de Pagamentos", e o valor reportado pela instituição transmissora de dados no caso de APIs de "Dados Cadastrais e Transacionais".

Os _endpoints_ das APIs deverão manter, diariamente, o SLA do percentil 95 do tempo de resposta em no máximo:

I - 1.500ms, em _endpoints_ classificados como de alta e média-alta frequências;

II - 2.000ms, em _endpoints_ classificados como de média frequência; e

III - 4.000ms, em _endpoints_ classificados como de baixa frequência.

A conformidade é avaliada mensalmente, verificando se os _endpoints_ das APIs das instituições participantes atenderam aos SLAs do desempenho.

## Metodologia Simplificada

A metodologia adotada para o monitoramento do tempo de resposta das APIs avalia se, diariamente, o percentil 95 dos endpoints cumpre o seu SLA, ou seja, se em um dia que o endpoint avaliado receba 100 requisições, o tempo de resposta de pelo menos 95 requisições é inferior ao SLA.  

## Aspectos Técnicos

O monitoramento inclui várias etapas:

**Filtro inicial dos dados provenientes da Plataforma de Coleta de Métricas (PCM)**

Serão consideradas apenas as chamadas com tempo de processamento maior que zero, ou seja, _**processtimespan**_ \> 0

Serão excluídas as requisições com status ‘PAIRED\_INCONSISTENT’ e ‘DISCARDED’ para todos os _endpoints_

Serão excluídas as chamadas com _status code_ 423, 429 e 529

**Agrupamento dos dados (serão agrupados para facilitar o cálculo do percentil 95 (P95))**

_**Timestamp**:_ data da chamada da API (yyyy-mm-dd)

_**Serverorgid**_: identificador da organização consumidora da API utilizada pelo cliente para a solicitação do dado 

_**Endpoint**_: _endpoint_ da API com o método e recurso

**Cálculo do percentil**

**Coleta dos dados**: Seja R o conjunto de todos os tempos de resposta de um dia, onde “ri” é o tempo de resposta da i-ésima requisição. Ou seja, R={r1, r2, ..., rn}. Nessa coleta é utilizado o _processtimespan_ quando _clientorgid_\=_organisationid_ ou _serverorgid_\=_organisationid_ e _status_ ‘UNPAIRED’

**Cálculo do índice do percentil 95**: o índice para o percentil 95, denotado por i95, é calculado pela fórmula i95 = 0.95 ∗ n, arredondado para o número inteiro mais próximo, e onde “n” representa número de requisições

**Ordenação dos dados**: O conjunto R em ordem crescente para obter o conjunto ordenado Rord={r(1), r(2), ..., r(n)}, onde r(1) é o menor tempo de resposta e r(n) é o maior

**Obtenção do valor do percentil 95**: o valor do percentil 95, denotado por P95, é o valor no índice i95 no conjunto ordenado Rord. Ou seja, P95 = r(i95)

## Interpretação dos Resultados

Para fins do processo de monitoramento, o período de apuração referente a este item é mensal e a análise de desconformidade é feita por conglomerado. A título de exceção, no caso de conglomerados que possuam equipes N2 por CNPJ, a desconformidade será gerada para a instituição.

Considera-se que um _endpoint_ está em conformidade caso tenha respeitado o SLA do desempenho em pelo menos 90% dos dias do mês de referência, arredondando-se para o número inteiro mais próximo, desde que o valor do percentil 95 (P95) dos demais dias não tenha sido superior ao SLA do desempenho aumentado em 20%. Os dias do mês de referência são os dias do mês em que houve requisições para o _endpoint_ avaliado.

Assim, consideramos cada conformidade diária:

**CONFORME**

**DENTRO DA TOLERÂNCIA**

**NÃO CONFORME**

P95 < SLA

SLA < P95 < SLA \* 1,2

P95 > SLA \* 1,2

E fazemos a apuração mensal:

**CONFORME**

**NÃO CONFORME**

Se a quantidade de dias conforme ≥ 90% de dias de acionamento

Se a quantidade de dias não conforme > 0

Se a quantidade de dias não conforme < 90% de dias de acionamento

**Importante**: A métrica não se aplica às APIs de "_Webhook_".

note

#### Exemplo Ilustrativo

#### Exemplo Ilustrativo

I - Em um mês de 30 dias, em que um _endpoint_ de alta frequência tenha apresentado valor de P95 inferior a 1.500ms em 27 dias e, nos demais dias, tenha apresentado valor de P95 entre 1.500ms e 1.800ms (1.500ms \* 1,2 = 1.800ms), o _endpoint_ está em **conformidade** para fins do processo de monitoramento naquele mês.

II - Em um mês de 31 dias, em que um _endpoint_ de alta frequência tenha apresentado valor de P95 inferior a 1.500ms em 28 dias e, nos demais dias, tenha apresentado, em pelo menos um dos dias, valor de P95 superior a 1.800ms (1.500ms \* 1,2 = 1.800ms), o _endpoint_ está **não conforme** para fins do processo de monitoramento naquele mês.

## Interpretação dos Dados no Painel

As informações contidas neste item têm como objetivo ajudar o usuário a compreender cada um dos campos exibidos no painel de “Tempo de Respostas das APIs”. Desta forma, têm-se:

Em “**Controles**”:

![Controles.png](images/Controles.png)

**Campos**

**Descrição**

**Mês análise**

informar a data ou período desejado, podendo ser uma data relativa ou intervalo de datas absoluto

**Conglomerado**

selecionar o conglomerado desejado

_**Endpoint**_

selecionar o _endpoint_ desejado ou selecionar todos os _endpoint_s

**Visualizar organização**

selecionar a opção “sim” para exibir os detalhes da organização pertencentes ao conglomerado ou a opção “não” para exibir o resultado por conglomerado

Em “**Desconformidade mensal**” é apresentado o resultado consolidado da apuração mensal por conglomerado e/ou organização, de acordo com o filtro selecionado em “**Controles**”.

O painel é interativo. Por exemplo, ao clicar na célula “**NÃO CONFORME**” do conglomerado ou da organização, serão exibidos os detalhamentos do mês de apuração. Além disso, é possível maximizar a visualização do painel e exportar os dados para CSV ou Excel.

![painel 2.png](images/painel%202.png)

Nos detalhes do mês de apuração:

![image-20250325-133054.png](images/image-20250325-133054.png)

**Campos**

**Descrição**

**Mês da apuração**

mês referente a apuração

**Método HTTP**

método da requisição

_**Endpoint**_

_endpoint_ da requisição

**Dias acionamentos**

total de dias do mês de apuração que o _endpoint_ foi acionado

**Dias P95 < frequência**

total de dias do mês de apuração em que o P95 (percentil 95) encontra-se inferior a frequência do _endpoint_

**Dias P95 entre a frequência**

total de dias em que o P95 (percentil 95) encontra-se no intervalo de tempo da frequência do _endpoint_

**Dias P95 \> tolerância**

total de dias do mês de apuração em que o P95 (percentil 95) encontra-se superior a tolerância de 20%

_**Status**_

não conforme (P95>SLA\*1,2)

No detalhamento, é possível visualizar:

![detalhamento 2.png](images/detalhamento%202.png)

**Campos**

**Descrição**

**Dias acionamento**

dia do mês de apuração em que o _endpoint_ foi acionado

**Método HTTP**

método da requisição

_**Endpoint**_

_endpoint_ da requisição

**Frequência API (ms)**

SLA da frequência de classificação do _endpoint_

**Quantidade de requisições**

total de requisições utilizadas para o cálculo de um determinado dia do mês de apuração

**P95 (ms)**

percentil 95 do tempo de requisição por milissegundo

_**Status**_

dentro da tolerância (SLA<P95<SLA\*1,2) ou

não conforme (P95 > SLA\*1,2)

**Importante**: para que o detalhamento seja exibido, deve-se sempre clicar na célula “NÃO CONFORME”.

![detalhamento 3.png](images/detalhamento%203.png)

**Campos**

**Descrição**

**x-fapi-interaction-id**

identificador único do reporte

_**Server**_

servidor reportado na requisição

_**Client**_

cliente reportado na requisição

**Método HTTP**

método da requisição

_**Endpoint**_

_endpoint_ da requisição

**Requisição (ms)**

tempo de resposta da requisição

**Importante:** serão exibidos no máximo cinco evidências de reporte.

## Dados e Fontes

Para o cálculo desta métrica, a fonte informacional é a Plataforma de Coleta de Métricas (PCM), que consolida os dados a partir dos reportes enviados pelas instituições participantes.  Todos os métodos e recursos dos _endpoints_ serão avaliados. Esses dados são consolidados na Plataforma Analítica de Dados (PAD), um repositório centralizado que serve como base para a análise e avaliação da métrica.

## Limitações e Considerações

Atualmente, não há visibilidade ou conhecimento de limitações ou considerações adicionais para esta métrica. A análise será continuamente revisada e aprimorada conforme novos dados e informações se tornem disponíveis.

## Responsável pela Aprovação

GT Arquitetura
