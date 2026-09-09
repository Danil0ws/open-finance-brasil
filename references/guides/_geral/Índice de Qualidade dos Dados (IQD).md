# Índice de Qualidade dos Dados (IQD)

## item 2.5Purple

## Controle de versão

**Versão**

**Data**

**Resumo das alterações**

1

Versão inicial

2

Implementado o Fator de Consistência no cálculo do IQA para mensurar a regularidade do reporte de dados de cada família de API

3

Revisão geral do documento

Alteração do Tópico “Classificação de conformidade do IQD”

Inclusão do tópico “Interpretação dos Dados no Painel”

4

Revisão geral do documento

Alteração do tópico “Cálculo do Índice de Qualidade de Dados”

Inclusão das “Perguntas frequentes”

## Introdução e Objetivos

Para garantir transparência quanto à qualidade dos dados no ecossistema do Open Finance, a Estrutura Responsável pela Governança do Open Finance disponibiliza o Índice de Qualidade dos Dados (IQD), juntamente com seus indicadores e metodologias de cálculo. Esses dados serão divulgados mensalmente, permitindo que o público acompanhe o nível de qualidade dos dados fornecidos pelas instituições participantes. Essa transparência proporciona informações confiáveis para a tomada de decisões relacionadas a riscos e resultados de negócios.

O Índice de Qualidade de Dados (IQD) foi desenvolvido para fornecer informações detalhadas sobre a qualidade dos dados oferecidos pelas instituições participantes aos cidadãos, associações e demais participantes do ecossistema do Open Finance. Com maior transparência, esses grupos têm acesso a um conjunto abrangente de informações para decidir qual instituição desejam utilizar para o compartilhamento de dados e/ou serviços financeiros por meio do Open Finance.

# **Glossário** 

**Termo** 

**Significado** 

**Family Type** 

Grupo de APIs por domínio (ex: accounts, credit-cards, payments) 

**Report** 

Arquivo JSON enviado diariamente pela instituição com métricas de qualidade 

**Snapshot** 

Foto semanal das métricas de uma organização por family type 

**Ticket** 

Chamado aberto no Service Desk quando há não-conformidade 

**SLA** 

Prazo para resolução do ticket 

**Conglomerado** 

Grupo econômico (ex: todas as empresas do Itaú) 

**OFB** 

Open Finance Brasil — o ecossistema inteiro 

**IR** 

Índice de Resolução — tickets resolvidos vs total 

**IC** 

Índice de Confiabilidade — requisições sem erro vs total 

**FC** 

Fator de Consistência — reports enviados vs esperados 

**IA** 

Índice de Disponibilidade — peso do family type no total 

**IQF** 

Índice de Qualidade do Family Type — nota composta 

**IQA** 

Índice de Qualidade Ajustado — IQF × peso 

**IQD** 

Índice de Qualidade dos Dados — nota final da organização 

## Sobre o Índice

O Índice de Qualidade dos Dados (IQD) corresponde à nota mensal que avalia a qualidade dos dados disponibilizados por cada instituição no Open Finance Brasil. O cálculo é realizado automaticamente pelo sistema MQD, sendo o resultado disponibilizado mensalmente, a partir do dia 15, com base nos dados do mês anterior.

O IQD é composto por três índices principais: Índice de Resolução (IR), Índice de Confiabilidade (IC) e Fator de Consistência (FC), cada um com seu respectivo peso. Esses índices, quando combinados, fornecem uma visão abrangente da qualidade dos dados fornecidos pelas instituições participantes do Open Finance.

**Dimensão** 

**Peso** 

**Confiabilidade** 

75% 

**Resolução** 

25% 

**Consistência** 

Multiplicador 

# Processo IQD

## **Processamento dos dados**

O IQD **não analisa dados brutos**. Ele consome informações já processadas por etapas anteriores: 

Instituição envia reports diários (JSON)   
        **↓**  
\[mqd-report\_process\] — Ingere e persiste os reports   
        **↓**  
\[mqd-aggregator\_day\] — Agrega dados por dia   
        **↓**  
\[mqd-ticket\_generator\] — Analisa semana a semana (7 dias)   
                          Gera "snapshots" com métricas consolidadas   
                          Abre tickets de não-conformidade   
        **↓**  
\[mqd-iqd\_generator\] — Soma os snapshots do mês ← ESTE DOCUMENTO   
                    Consulta tickets no Service Desk   
                         Calcula o IQD

**O que é um "snapshot"?** 

É uma foto semanal da situação de cada instituição por family type. Contém: 

-   Quantas requisições foram feitas 
    
-   Quantas tiveram erros 
    
-   Quantos dias a instituição enviou reports 
    
-   Quantos dias eram esperados 
    
-   Se houve ticket aberto 
    

## **Período de Cálculo** 

O cálculo do IQD é realizado mensalmente, a partir do dia 15 de cada mês, contemplando integralmente os dados referentes ao mês anterior.

**Exemplo** 

Execução em 15 de fevereiro de 2025: 

-   Período analisado: 1º de janeiro a 31 de janeiro de 2025 
    
-   Busca todos os snapshots semanais cujo fim cai em janeiro
    

## **Componentes do IQD**

### **Índice de Resolução (IR)**

Esse índice mede a eficiência na resolução de problemas e no atendimento ao suporte relacionado a uma determinada família de APIs. Esse índice é calculado com base na quantidade de tickets encerrados dentro do prazo de SLA em relação ao total de tickets abertos para a família de APIs em questão. Um valor alto de IR indica que a instituição é eficiente na resolução de problemas e no atendimento às demandas dos usuários. A eficiência é avaliada com base na fórmula a seguir, proporcionando uma medida quantitativa da eficiência na resolução de problemas:

![image-20240606-162030.png](images/image-20240606-162030.png)

#### Se não houver tickets o IR é considerado 1,0 (nota máxima - 100%)

### **Índice de Confiabilidade (IC)**

Esse índice avalia a qualidade e a integridade dos dados fornecidos por uma determinada API. Esse índice indica a proporção de requisições bem-sucedidas em relação ao total de requisições. Um valor alto indica que os dados fornecidos pela API são confiáveis e podem ser utilizados com segurança pelas aplicações e serviços que dependem dessas informações.

![image-20260710-184750.png](images/image-20260710-184750.png)

### **Fator de Consistência (FC)**

Incorpora a regularidade do fornecimento de dados ao cálculo do IQA, complementando as métricas de qualidade ao considerar a relação entre a quantidade de reports enviados e a quantidade de reports esperados para cada família de API.

![image-20260710-184851.png](images/image-20260710-184851.png)

### **Índice de Abrangência (IA)**

Esse índice mede o quão abrangente é uma determinada API em relação ao total de APIs analisadas na organização. Esse índice leva em consideração a quantidade de requisições realizadas para uma determinada família de API, comparando-a com todas as famílias de APIs analisadas naquela organização. Um valor alto de IA indica que a API em questão possui uma grande relevância e abrangência dentro da organização.

![image-20260710-184910.png](images/image-20260710-184910.png)

### **Cálculo do Índice de Qualidade de Dados (IQD)**

O Índice de Qualidade de Dados (IQD) é calculado em várias etapas, considerando diferentes aspectos da qualidade e consistência dos dados fornecidos.

O IQD é calculado em três níveis:

IQD OFB (ecossistema inteiro)  
└── IQD por Conglomerado (grupo econômico)  
     └── IQD por Organização (instituição)  
          └── IQF por Family Type (ex: accounts)

-   **Organização**: nota individual de cada instituição 
    
-   **Conglomerado**: nota do grupo (ex: Itaú + Itaú Unibanco + Rede) 
    
-   **OFB**: nota geral do ecossistema Open Finance Brasil 
    

**Agregação Conglomerado e OFB**

**Conglomerado** 

**a)** Agrupa todas as organizações do mesmo grupo econômico 

**b)** Soma as métricas por family type (requests, errors, tickets, reports) 

**c)** Aplica as mesmas fórmulas como se fosse uma "super-organização" 

**OFB (Ecossistema)** 

**a)** Agrupa **todas** as organizações em um único grupo 

**b)** Soma tudo 

**c)** Aplica as mesmas fórmulas 

**d)** Resultado: uma nota única que representa a saúde do Open Finance Brasil

Após o cálculo, o indicador recebe uma classificação de acordo com o valor obtido.

**IQD** 

**Qualificação** 

≥ 0,95 (95%) 

**CONFORME** 

< 0,95 (95%) 

**NÃO CONFORME** 

#### a) Cálculo do Índice de Qualidade do Family Type (IQF)

O IQF é obtido através da combinação ponderada dos índices IR e IC, multiplicada pelo Fator de Consistência (FC).

**IQF = ((𝐼𝑅 × Peso IR) + (𝐼𝐶 × Peso IC)) × FC**

#### b) Cálculo do Índice de Qualidade Ajustado (IQA)

O IQA é obtido através da multiplicadção do IQF pelo Índice de Abrangência (IA)

**IQA = IQF x IA**

#### c) Calculo do IQD

O Índice de Qualidade de Dados (IQD) é a somatória de todos os Índices de Qualidade ajustados (IQA) finais.

**IQD = Σ IQA**

### **Exemplo ilustrativo**

**Cenário** 

Banco XYZ em janeiro/2025, com 2 family types: accounts e credit-cards. 

**Métrica** 

**accounts** 

**credit-cards** 

Requisições totais 

10.000 

5.000 

Requisições com erro 

200 

50 

Tickets abertos 

2 

1 

Tickets fechados 

2 

0 

Reports enviados 

35 

35 

Reports esperados 

35 

35 

 **Cálculo** 

**a) Total de requisições da organização** = 10.000 + 5.000 = 15.000 

**b) accounts:** 

-   IR = 2/2 = **1,00** (todos os tickets foram resolvidos) 
    
-   IC = 9.800/10.000 = **0,98** (98% das requisições sem erro) 
    
-   FC = 35/35 = **1,00** (enviou todos os reports) 
    
-   IA = 10.000/15.000 = **0,667** (67% do tráfego) 
    
-   IQF = (1,00 × 0,25 + 0,98 × 0,75) × 1,00 = **0,985** 
    
-   IQA = 0,985 × 0,667 = **0,657** 
    

**c) credit-cards:** 

-   IR = 0/1 = **0,00** (ticket não foi resolvido!) 
    
-   IC = 4.950/5.000 = **0,99** 
    
-   FC = 35/35 = **1,00** 
    
-   IA = 5.000/15.000 = **0,333** (33% do tráfego) 
    
-   IQF = (0,00 × 0,25 + 0,99 × 0,75) × 1,00 = **0,743** 
    
-   IQA = 0,743 × 0,333 = **0,247**
    

**d) IQD do Banco XYZ** = 0,657 + 0,247 = **0,904** → **NÃO CONFORME** 

O banco ficou não conforme porque não resolveu o ticket de credit-cards dentro do SLA. 

# **Regras Especiais** 

**1\. Family types não obrigatórios ou com exceção** 

Se um family type tem IgnoreAvailabilityRules = true ou não é obrigatório (Required = false): 

-   O FC é automaticamente **1,0** (não penaliza por falta de reports) 
    
-   O ExpectedReports é igualado ao TotalReports 
    

**2\. Family types sem requisições** 

Se um family type não recebeu nenhuma requisição no mês: 

-   **IQA = 0** (não contribui positivamente para o IQD) 
    
-   O IA usa o MaxRequests da organização como referência para manter o peso proporcional 
    

**3\. Tickets — quando é considerado "fechado"?** 

Um ticket do Service Desk é considerado resolvido se: 

-   Status = **"Sem SLA"** (não tinha prazo), OU 
    
-   Status = **"ATENDIMENTO ENCERRADO"** E prazo = **"Dentro do SLA"** 
    

Tickets com status **"CANCELADO"** são ignorados (não contam para nada). 

**4\. Conglomerados** 

-   Organizações são agrupadas pelo ConglomerateID 
    
-   Se uma organização não pertence a nenhum conglomerado, ela é tratada como conglomerado individual 
    
-   As métricas de todas as organizações do grupo são somadas e as mesmas fórmulas são aplicadas 
    

# Interpretação dos Dados no Painel

As informações contidas neste item têm como objetivo ajudar o usuário a compreender cada um dos campos exibidos no painel de “Índice de Qualidade de Dados (IQD)”. Desta forma, têm-se:

Em “**Controles**”:

![image-20250416-114221.png](images/image-20250416-114221.png)

**Campos**

**Descrição**

**Data início**

informar a data de início ou período desejado, podendo ser uma data relativa ou intervalo de datas absoluto

**Data fim**

informar a data de fim ou período desejado, podendo ser uma data relativa ou intervalo de datas absoluto

**Conglomerado**

selecionar o conglomerado desejado

**Visualizar por conglomerado ou instituição**

selecionar a opção “instituição” para exibir os detalhes da organização pertencentes ao conglomerado ou a opção “conglomerado” para exibir o resultado por conglomerado

Em “**Desconformidade mensal do IDQ por Conglomerado**” (**Figura 1**) é apresentado o resultado consolidado da apuração mensal por conglomerado, de acordo com o filtro selecionado em “**Controles**”.

O painel é interativo. Por exemplo, ao clicar na célula “**NÃO CONFORME**” do conglomerado, serão exibidos os detalhamentos do mês de apuração.

![image-20250416-164316.png](images/image-20250416-164316.png)

Em “**Desconformidade mensal do IDQ por Instituição Participante**” (**Figura 2**) é apresentado o resultado consolidado da apuração mensal por **Instituição Participante**, de acordo com o filtro selecionado em “**Controles**”.

O painel é interativo. Por exemplo, ao clicar na célula “**NÃO CONFORME**” da Instituição, serão exibidos os detalhamentos do mês de apuração.

![image-20250416-164551.png](images/image-20250416-164551.png)

Em “**Desconformidade mensal - Instituição Participante**”, têm-se:

![image-20250416-164807.png](images/image-20250416-164807.png)

**Campos**

**Descrição**

**Mês apuração**

mês referente a apuração

**IQD**

percentual referente ao Índice de Qualidade dos Dados (IQD) no mês de apuração

**Status**

não conforme

Em “**Detalhamento do cálculo do IQD por Instituição Participante**”, têm-se:

note666869b4e764

É possível ampliar a visualização do painel e exportar os dados para CSV ou Excel por meio da opção 'Opções de menu', localizada no canto superior direito”.

É possível ampliar a visualização do painel e exportar os dados para CSV ou Excel por meio da opção 'Opções de menu', localizada no canto superior direito”.

![image-20250416-144843.png](images/image-20250416-144843.png)

**Campos**

**Descrição**

**Mês/Ano**

mês e ano referente a apuração

**Conglomerado Participante**

conglomerado/instituição selecionado(a)

**Família de APIs**

família de APIs correspondentes

**Quantidade de Requisições**

total de requisições reportadas no mês de apuração de determinada família de APIs

**Quantidade de Requisições com erros**

total de requisições com erros reportadas no mês de apuração de determinada família de APIs

**Tickets abertos**

total de tickets abertos quando contém erro em requisições de determinada família de APIs no mês de apuração

**Tickets encerrados**

total de tickets encerrados de determinada família de APIs no mês de apuração

**Dia do mês**

dia do mês em que houve reporte de dados para determinada família de API

**Dias reportados**

total de dias do mês de apuração em que houve reporte de dados para determinada família de API

**Índice de Resolução (IR)**

resultado do percentual do índice de resolução

**Índice de Confiabilidade (IC)**

resultado do percentual do índice de confiabilidade

**Índice de Abrangência (IA)**

resultado do percentual do índice de abrangência

**Fator de Consistência (FC)**

percentual do fator de consistência

**Índice de Qualidade da API (IQA)**

percentual do índice de qualidade da API

**Índice de Qualidade de Família (IQF)**

percentual do índice de qualidade de família

## Dados e Fontes

Para o cálculo do índice, utilizam-se os dados provenientes do Motor de Qualidade de Dados (MQD). Esses dados são posteriormente consolidados na Plataforma Analítica de Dados (PAD), que é um repositório centralizado e serve como base para a análise e avaliação dos dados para o índice.

Essa estrutura permite uma avaliação precisa do índice e um monitoramento efetivo da qualidade dos dados no contexto do Open Finance.

## **Perguntas Frequentes** 

**P1: Se minha instituição não recebeu requisições em um family type, isso prejudica o IQD?**   
R: Não diretamente. O IQA desse family type será 0, mas o peso (IA) é redistribuído. O impacto depende de quantos family types a instituição possui. 

**P2: O que acontece se eu não enviar reports em alguns dias?**   
R: O FC (Fator de Consistência) será menor que 1,0, reduzindo proporcionalmente o IQF de todos os family types afetados. 

**P3: Por que o "mês" pode ter 28 ou 35 dias?**   
R: Porque o sistema opera em semanas de 7 dias. Dependendo de como os sábados caem no calendário, 4 ou 5 semanas são capturadas. A proporção é mantida, então não há prejuízo. 

**1\. O problema em linguagem simples** 

O IQD calcula a nota de um **mês** (ex: janeiro = 31 dias). Mas os dados de entrada vêm de **análises semanais** que sempre cobrem exatamente **7 dias**. 

**2\. Como funciona na prática** 

O processo de qualidade (ticket\_generator) roda toda semana, sempre de sábado a sábado: 

Janeiro 2025:

**Semana**

**1º dia**

**Último dia**

**Resultado**

1

28/12

04/01

end\_date = 04/01 ✓ cai em janeiro

2

04/01

11/01

end\_date = 11/01 ✓

3

11/01

18/01

end\_date = 18/01 ✓

4

18/01

25/01

end\_date = 25/01 ✓

5

25/01

01/02

end\_date = 01/02 ✗ cai em fevereiro!

O IQD de janeiro captura as semanas cujo **fim** cai em janeiro: semanas 1 a 4. 

Cada semana tem expected\_reports = 7. Com 4 semanas: **28 reports esperados**. 

Mas em outro mês, dependendo de como os sábados caem: 

Março 2025: 

**Semana**

**1º dia**

**Último dia**

**Resultado**

1

22/02

01/03

end\_date = 01/03 ✓

2

01/03

08/03

end\_date = 08/03 ✓

3

08/03

15/03

end\_date = 15/03 ✓

4

1503

22/03

end\_date = 22/03 ✓

5

22/03

29/03

end\_date = 29/03 ✓

Com 5 semanas capturadas: **35 reports esperados** — o "mês de 35 dias". 

**3\. Isso prejudica alguma instituição?** 

**Não.** O cálculo é proporcional. O que importa é a **razão** entre reports enviados e esperados: 

**Cenário** 

**Reports enviados** 

**Reports esperados** 

**FC** 

Mês com 4 semanas, tudo OK 

28 

28 

1,00 

Mês com 5 semanas, tudo OK 

35 

35 

1,00 

Mês com 4 semanas, faltou 1 dia/semana 

24 

28 

0,86 

Mês com 5 semanas, faltou 1 dia/semana 

30 

35 

0,86 

A proporção é sempre a mesma. Nenhuma instituição é beneficiada ou prejudicada pelo número de semanas do mês. 

**4\. Efeito nas bordas do mês** 

-   A Semana 1 de janeiro pode incluir dias de **dezembro** (ex: 28-31/12) 
    
-   Os últimos dias de janeiro (26-31) podem cair numa semana cujo fim é em **fevereiro** 
    

Isso significa que alguns dias são contabilizados no mês "vizinho". É um trade-off aceito: o sistema prioriza **semanas completas** sobre limites exatos do mês calendário. 

**P4: Se eu resolver um ticket fora do SLA, conta como resolvido?**   
R: Não. Apenas tickets com status "ATENDIMENTO ENCERRADO" + "Dentro do SLA" ou "Sem SLA" contam como fechados. 

**P5: Tickets cancelados prejudicam meu IQD?**   
R: Não. Tickets com status "CANCELADO" são completamente ignorados no cálculo. 

**P6: Como funciona o cálculo do conglomerado?**   
R: As métricas de todas as organizações do grupo são somadas e as mesmas fórmulas são aplicadas sobre o total. É como se o conglomerado fosse uma única organização grande.
