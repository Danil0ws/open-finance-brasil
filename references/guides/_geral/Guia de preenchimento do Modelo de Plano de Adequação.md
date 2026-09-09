# Guia de preenchimento do Modelo de Plano de Adequação

# Controle de versão

**Versão**

**Data**

**Resumo das alterações**

001

Versão inicial

# 1\. Introdução e Objetivos

Orientar as instituições participantes a preencherem o Plano de Adequação, estruturando-o de forma prática, com informações objetivas, rastreáveis e verificáveis, conforme determinações da Instrução normativa BCB nº 706 de 29/01/2026, que divulga a versão 3.0 do Manual de Monitoramento do _Open Finance_.

# 2\. Aplicação

Aplica-se às instituições participantes do _Open Finance_, que necessitam apresentar e executar, de acordo com as normas vigentes, um Plano de Adequação.

# 3\. Documentos de referência

-   [Instrução Normativa BCB nº 588, de 31/01/2025 - Manual de Serviços](data/references/Instrução_Normativa_BCB_588.md)
    
-   [Instrução Normativa BCB n° 615 de 06/05/2025 - Manual de APIs do Open Finance](data/references/Instrução_Normativa_BCB_615.md) 
    
-   [Instrução Normativa BCB n° 637 de 13/06/2025 - Manual de Experiencia do Cliente Open Finance](data/references/Instrução_Normativa_BCB_637.md) 
    
-   [Instrução Normativa BCB n° 706 de 29/01/2026 - Manual de Monitoramento do Open Finance](data/references/Instrução_Normativa_BCB_706.md)
    

# 4\. Finalidade da resposta

Este documento tem como finalidade apoiar as instituições na elaboração e no desenvolvimento do modelo de resposta para estruturação do Plano de Adequação, quando da desconformidade dos indicadores de monitoramento. Toda desconformidade deve ser respondida como uma cadeia única em que as seções se sustentem, desde o diagnóstico aos controles mitigatórios propostos.

A resposta deve ser detalhada de forma clara e objetiva, sendo que resposta declaratória/genérica não será aceita, considerando que afirmações como: o problema foi corrigido, a área técnica está avaliando, a instituição segue monitorando e similares, não a constituem. Em sua completude, a resposta deve atender à estrutura descrita no documento “Modelo padrão do Plano de Adequação” e conter:

 **Contexto do Problema** >> **Causa Identificada** >> **Soluções Aplicadas** >> **Controles Mitigatórios**

O Plano de Adequação deve ser elaborado para cada item monitorado apontado em desconformidade, apresentar cronograma individualizado por item (sendo que os itens podem ser consolidados em um único documento para formalização) e estar assinado pelo diretor responsável pelo compartilhamento de dados e serviços no âmbito do _Open Finance_.

-   **Importante:** conforme determina o [Manual de Monitoramento do Open Finance](data/references/Instrução_Normativa_BCB_706.md), o Plano de Adequação deve entrar em execução assim que for apresentado, sendo que não serão aceitos Planos com início futuro para as ações corretivas.
    

# 5\. Cadeia de adequação: etapas que sustentam a resposta

O Plano de Adequação é avaliado em cadeia e não como campos isolados. Abaixo a definição operacional de cada seção, sendo que as exigências para cada item monitorado estão exemplificadas e descritas no item “7. Aplicação por item monitorado” deste documento.

**Seção**

**Definição operacional**

**Contexto do Problema**

Explicação da situação garantindo a identificação de: o que, onde, quando e quanto do item monitorado bem como período de apuração; o que está envolvido (painel, _endpoint_, produto, canal, marca, ambiente, _ticket_, volume e nível de severidade do impacto); e se a desconformidade é pontual, recorrente ou estrutural.

**Causas Identificadas**

Detalhamento da(s) causa(s) raiz(es) em sua origem, indicando o motivo fundamental (técnico, processual, de governança, dados ou dependência externa), sem descrever apenas o contexto do problema. Indica o onde, o estado atual dos componentes que atendem o serviço (capacidade, configuração etc.) e a razão de como o estado contribuiu para o problema.

**Soluções Aplicadas**

Descrição das soluções aplicadas/em aplicação para correção das causas, detalhando a(s) ação(ões) adotada(s) e o resultado esperado, componentes corrigidos, datas marco de início e de conclusão.

**Controles Mitigatórios**

Informação sobre o que impedirá a recorrência, incluindo controles preventivos e detectivos, alertas, rotinas de monitoramento, esteiras de validação, aumento de capacidade e melhorias de governança interna.

**Importante:** a insuficiência descritiva ou fragilidade técnica de qualquer seção ou não encadeamento lógico entre as seções invalida o Plano para o item em desconformidade.

# 6\. Critérios de rejeição - Exemplos

A resposta será considerada insuficiente pela Estrutura de Governança do _Open Finance_ quando apresentar qualquer das situações ou similares listadas abaixo, independentemente do restante do conteúdo:

-   Descrever o sintoma e não a causa raiz;
    
-   Declarar causa não apoiada pelo contexto fornecido ou conhecido;
    
-   Não nomear o responsável pela execução ou acompanhamento;
    
-   Não trazer data de início e de conclusão por ação;
    
-   Não apresentar controle que mitigue a recorrência;
    
-   Utilizar descrição genérica, sem fundamento técnico/arquitetural;
    
-   Não oferecer ligação lógica entre causa, ação corretiva e o resultado esperado;
    
-   Consolidar várias desconformidades em uma única resposta, sem cronograma individual;
    
-   Atribuir causa ou parte dela a terceiros sem demonstrar a ação da própria instituição ou não informar o prazo de solução negociado.
    

# 7\. Aplicação por item monitorado

Cada tópico abaixo representa a cadeia de adequação de um item monitorado, definindo os **requisitos de resposta** em cada etapa e exemplos de **causa raiz aceitável versus rótulos genéricos.**

**Itens monitorados contemplados:**

**Código**

**Item monitorado**

2.1 I

Tempo de resposta das APIs (Desempenho)

2.1 II

Disponibilidade das APIs

2.1 III

Requisições com _status code_ HTTP 529 (sobrecarga do servidor)

2.2 I

Versões iniciais e novas versões de APIs

2.2 II

Implementação de APIs e artefatos associados

2.2 III

Modalidades de participação

2.2 IV

Retirada de versões antigas de APIs

2.3

Metas de prazo máximo para atendimento de _tickets_ (SLA)

2.4

Reporte de informações (PCM e planilhas autorreportadas)

2.5

Qualidade de dados

2.6.1

Jornada do cliente

2.6.2

Taxa de conversão

##  **2.1 I Tempo de resposta das APIs (Desempenho)**

Refere-se ao desempenho das APIs quanto ao tempo de atendimento das requisições, medindo se as respostas são entregues dentro dos limites estabelecidos pelo SLA. Avalia a capacidade da instituição de garantir rapidez, estabilidade e consistência no retorno das chamadas, conforme os padrões exigidos pelo _Open Finance_.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição objetiva do cenário em que a desconformidade ocorreu, incluindo, por exemplo: APIs afetadas, período de ocorrência, magnitude da degradação (ex.: percentis de latência acima do limite regulatório – quanto), componentes impactados, volume de chamadas (volume é contexto e não a causa) e impacto no negócio (ex.: indisponibilidade, lentidão para consumidores – especificar quais e quando).

**Causas identificadas**

Identificação clara da causa (e causas contribuintes), com nexo causal técnico com o contexto explicitamente declarado.

Deve conter: componente(s) ofensor(es), sua capacidade instalada, dependência da API para com o serviço ofertado pelo componente e demais contextos necessários à análise.

A causa deve ser demonstrável, se solicitado, evitando suposições (se baixa capacidade de processamento, por exemplo, deve-se possuir a possibilidade de demonstrar consumo de CPU próximo do limite provisionado, ou outro indicador em sistema corporativo que o prove).

**Soluções aplicadas**

Descrição das ações corretivas implementadas para eliminar cada causa, incluindo, por exemplo: ajustes de arquitetura (quais), otimização de código (onde, razão), escalabilidade de infraestrutura (onde, quanto), banco de dados (o quê), correções de integração ou filas (o quê).

As soluções devem ser específicas às causas relatadas, com indicação de quando serão aplicadas, em quais componentes e qual é o resultado esperado.

**Controles mitigatórios**

Medidas implementadas para prevenção de novas ocorrências, como por exemplo: implantação de monitoramento em tempo real para ação manual imediata (qual melhoria), definição de _thresholds_ de latência para APIs, alertas automáticos antes da degradação crítica, dashboards operacionais visíveis para times técnicos e gestão. As medidas devem ser vinculadas ao indicador afetado. 

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

Foi detectado que durante o pico diário das H às H ocorre saturação do pool de conexões de integração provisionado na configuração do Nginx, hoje limitado a X, o que leva ao não atendimento imediato de requisições solicitadas pelo API _gateway_ ao sistema de contas-correntes, deflagrando reconexões, com consequente lentidão para os consumidores do _endpoint_ X do _Open Finance_.

Instabilidade pontual de performance.

Reconstrução durante o período sob análise, do índice de ID de recurso no banco de dados Oracle. Esse índice é necessário ao _endpoint_ de recursos Z, ocasionando lentidão de resposta aos _requests_.

Lentidão momentânea no banco de dados.

Incapacidade de _autoscaling_ da memória necessária ao cache durante o pico de X a Y, ocasionada por limitação Z.

Pico de acesso não previsto.

## 2.1 II Disponibilidade das APIs

Define que as instituições devem garantir que suas APIs permaneçam acessíveis e operantes de forma contínua, com monitoramento baseado em requisições válidas e em intervalos regulares. Para fins de conformidade, são estabelecidos níveis mínimos de disponibilidade, sendo 95% de disponibilidade diária e 99,5% de disponibilidade longa (média móvel de 90 dias), assegurando não apenas a operação pontual, mas principalmente a estabilidade sustentada ao longo do tempo das APIs disponibilizadas no _Open Finance_.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Detalhamento do incidente (data, duração, APIs afetadas), impacto no serviço/cliente, nível de indisponibilidade (total ou parcial) e indicadores de disponibilidade antes/durante o evento.

**Causas identificadas**

Descrição da causa raiz (ex.: falha de infraestrutura, indisponibilidade de fornecedor, erro de _deploy_, falha de rede), com explicação técnica clara e validação pela equipe responsável.

**Soluções aplicadas**

Medidas adotadas para normalização (_rollback_, correção técnica, ajuste de configuração, acionamento de contingência), com registro da execução e validação da restauração do serviço.

**Controles mitigatórios**

Implementação de monitoramento de disponibilidade, definição de SLA, planos de contingência e redundância, gestão de mudanças, testes de resiliência e processos formais de gestão de incidentes.

 **Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

Indisponibilidade causada por falha no _cluster_ de banco de dados primário, devido ao esgotamento de conexões simultâneas, sem acionamento automático do _failover_ configurado.

Falha de infraestrutura.

Interrupção da API ocasionada por erro em _deploy_ de versão (v2.3.1), que introduziu _loop_ de requisições e sobrecarga no serviço.

Problema de _deploy_.

Queda devido à indisponibilidade do provedor externo de autenticação utilizado na API x (timeout superior a 30s), sem mecanismo de _fallback_ implementado. 

Falha no provedor de terceiro.

##  2.1 III Requisições com status code HTTP 529

Monitora se a instituição mantém sua infraestrutura de APIs dimensionada adequadamente, controlando o percentual de requisições que falham por sobrecarga (HTTP 529), com limites regulatórios rígidos para garantir disponibilidade e estabilidade no _Open Finance_. 

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição detalhada do evento: quando ocorreu (datas/horários), duração e sistemas afetados; identificação das APIs, serviços ou canais impactados;  
volume de requisições e comportamento observado (picos, anomalias de tráfego); impacto ao cliente e ao negócio (ex.: indisponibilidade de serviços críticos, falha em transações); classificação do incidente conforme (ex.: severidade, criticidade).

**Causas identificadas**

Análise de causa raiz (RCA), com evidências técnicas e indicação se o problema decorreu de: capacidade insuficiente (infraestrutura), falha em balanceamento de carga, ataque ou comportamento anômalo (ex.: DDoS), erro de configuração ou _deploy_, dependência de terceiro (_cloud,_ API externa).  
Registros de logs, métricas e traces que comprovem a origem do problema.  
Avaliação de falha de controles preventivos existentes.

**Soluções aplicadas**

Ações corretivas imediatas adotadas (ex.: aumento de capacidade, _rollback_ de versão, bloqueio de tráfego, ajuste de _rate limit_); correções estruturais implementadas (ex.: _auto scaling_, melhoria de arquitetura (qual), otimização de código – onde e por qual razão; ajustes em monitoramento e alertas; implementação de planos de continuidade ou contingência.

**Controles mitigatórios**

Controles preventivos implementados ou reforçados, como por exemplo: mecanismos de _auto_ _scaling_, _rate limiting_ e _throttling_, balanceamento e distribuição de carga, e redundância e alta disponibilidade; monitoramento contínuo (APM, observabilidade, alertas proativos); planos de resposta a incidentes (_runbooks_, _playbooks_); governança e revisão periódica de capacidade; treinamento de equipes e revisão de processos de _change_ _management_; indicadores (KPIs/KRIs) definidos para evitar recorrência.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

Durante o pico identificou-se saturação do _cluster_ de APIs devido à ausência de _auto scaling_, resultando em rejeição de requisições com status HTTP 529. 

Ocorreu instabilidade no sistema durante o período.

Verificou-se falha no balanceador de carga, que direcionou volume excessivo de requisições para um único nó degradado, ocasionando sobrecarga e respostas HTTP 529. 

Houve indisponibilidade momentânea do serviço.

Não houve redirecionamento do tráfego ao provedor anti-DDOS devido a falha humana, levando à exaustão de recursos e geração de respostas HTTP 529.

Ataque impactou a aplicação. 

## 2.2 I Versões iniciais e novas versões de APIs

Estabelece que as instituições devem garantir gestão adequada do ciclo de vida das APIs, incluindo tanto o lançamento de versões iniciais quanto a publicação de novas versões. Isso envolve assegurar que essas liberações ocorram de forma controlada e documentada.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição detalhada do evento relacionado à publicação inicial ou à alteração de versão da API, incluindo datas, ambientes, e identificação das APIs impactadas.

**Causas identificadas**

Apresentação da análise de causa raiz indicando falhas no processo de gestão de mudanças, versionamento ou governança de APIs. Isso pode incluir ausência de controle sobre versionamento, mudanças não documentadas ou falhas em _pipelines_ de _deploy_. 

**Soluções aplicadas**

Descrição das ações corretivas adotadas, melhorias implementadas no processo, como reforço em testes automatizados, ajustes em _pipelines_ de CI/CD, revisão de procedimentos.

**Controles mitigatórios**

Demonstrar os controles implementados ou aprimorados para evitar recorrência, incluindo mudanças nos processos formais de versionamento, processos estruturados de gestão de mudanças e releases, e obrigatoriedade de testes abrangentes antes da publicação. Também são esperados monitoramento contínuo, indicadores de qualidade de APIs e revisão periódica dos processos de desenvolvimento e publicação. 

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

Apesar de ter sido registrado erro no provisionamento da nova API no GW, o processo automatizado prosseguiu com sua publicação no balanceador de carga, colocando em produção uma atualização parcial e mantendo simultaneamente o serviço antigo em produção.

Houve problema na atualização da API.

O processo de gestão de mudanças não previa o redirecionamento da ação em caso de restruturação organizacional, o que deixou o pedido de mudanças atribuído a uma equipe inexistente.. 

A API não foi publicada em produção na data prevista por erro humano.

##  **2.2 II Implementação de APIs e artefatos associados**

Valida se a instituição implementou e disponibilizou corretamente as APIs do _Open Finance_, com todos os artefatos técnicos exigidos, em conformidade com os padrões, segurança e requisitos operacionais definidos pelo Manual de APIs. 

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição clara da desconformidade identificada, indicando, por exemplo, se há API não aderente ao padrão do _Open Finance_ ou divergente das especificações técnicas, além das APIs afetadas, incluindo nome, versão e _endpoints_ impactados.

**Causas identificadas**

Apresentação de causa raiz detalhada, apontando se o problema decorre de erro de implementação, falha em deploy ou divergência entre documentação e código. Identificar se a causa está relacionada a especificações técnicas incorretas, erro de versionamento, falhas em artefatos (como _Swagger/OpenAPI_, certificados ou metadados) ou problemas de segurança/autenticação. 

**Soluções aplicadas**

Descrição das correções, incluindo ajustes em _endpoints_ e APIs, serviços de negócio (_backend_), correção de certificados ou configurações de segurança. Devem ser informadas as datas da implementação das correções e caso aplicável, também deve ser indicada a atualização no Diretório de Participantes.

**Controles mitigatórios**

Descrição das ações adotadas para prevenção de novas ocorrências, monitoramento contínuo de APIs (incluindo _health checks_ e métricas de erro) e revisão dos processos de governança de APIs, incluindo _deploy_, versionamento e publicação. 

Detalhamento dos controles preventivos, como validações antes da publicação e revisão de artefatos, e os controles detectivos, como alertas, l_ogs_ e monitoramento contínuo.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A falha foi causada por divergência entre o contrato publicado na especificação e a implementação em produção, devido à ausência de validação automatizada no _pipeline_ de _deploy_.

Erro sistêmico e de publicação de API.

O problema ocorreu por configuração incorreta do certificado de segurança (mTLS), incompatível com os requisitos definidos, após atualização de infraestrutura sem testes de regressão completos. 

Falha de configuração do certificado de segurança.

A desconformidade foi originada por versionamento inadequado da API, em que a versão “_deprecated_” foi removida antes do prazo de convivência, devido à ausência de controle formal de ciclo de vida de APIs. 

Problema técnico de versionamento.

## **2.2 III Modalidades de participação**

Monitora se a instituição está corretamente enquadrada, cadastrada e atuando nas modalidades de participação declaradas, garantindo aderência regulatória e coerência entre autorização, papel exercido e serviços disponibilizados no _Open Finance_.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Detalhamento da natureza da inconsistência, como classificação incorreta, ausência de documentação comprobatória ou enquadramento inadequado. Deve incluir o período de ocorrência, as áreas ou processos impactados.

**Causas identificadas**

Descrição da causa raiz do problema, indicando se a origem decorre de falhas sistêmicas, erros operacionais, interpretação inadequada da norma ou ausência de atualização de sistemas e procedimentos, bem como indicar se a causa é pontual ou estrutural.

**Soluções aplicadas**

Apresentação das ações corretivas adotadas para sanar o problema, como reclassificação de participações, ajustes em bases de dados e revisão de critérios. Descrever as melhorias em processos, incluindo atualização de políticas, normas e fluxos, bem como eventuais ajustes sistêmicos ou automações, além de informar os treinamentos realizados e os prazos e status das ações (concluídas ou em andamento).

**Controles mitigatórios**

Detalhamento dos controles implementados para prevenção de nova ocorrência, incluindo validações automáticas, conciliações periódicas e revisões independentes.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A classificação incorreta das modalidades de participação ocorreu devido à ausência de parametrização adequada no Diretório após atualização da normativa regulatória, resultando em enquadramento indevido.

A inconsistência foi causada por um erro sistêmico não especificado.

O apontamento foi causado pela inexistência de controle de validação independente no processo de cadastro, permitindo divergências entre a documentação suporte e o registro da modalidade de participação.

Houve um problema manual no processo de provisionamento.

A inconsistência identificada decorreu da interpretação inadequada do item pela equipe operacional, em razão de falta de treinamento específico e ausência de orientação formal atualizada.

O problema ocorreu devido a falha humana.

## **2.2 IV Retirada de versões antigas de APIs**

Assegurar a descontinuação controlada de versões antigas de APIs, garantindo a atualização tecnológica, a segurança dos serviços e a continuidade adequada para os consumidores. 

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição clara do cenário, evidenciando que versões antigas de APIs permaneceram ativas além do período permitido pelas normas, informando qual API e qual versão estavam em desacordo, detalhando a data prevista para descontinuação em comparação com a data real de retirada, bem como descrever os impactos no ecossistema, como a eventual utilização continuada por consumidores.

**Causas identificadas**

Demonstração da análise de causa raiz, descrevendo de forma detalhada os fatores que levaram ao descumprimento, que pode incluir falhas no processo de governança de APIs, como ausência de demanda interna de descontinuação, problemas técnicos que impediram a remoção da versão antiga, dependência de terceiros que não migraram no prazo.

**Soluções aplicadas**

Descrição das ações corretivas adotadas para sanar o problema, incluindo a desativação das versões antigas fora de conformidade, a implementação ou melhoria do processo de gestão do ciclo de vida das APIs.

**Controles mitigatórios**

Apresentação das medidas preventivas implementadas para prevenção de nova ocorrência, como a formalização de uma política de versionamento e descontinuação alinhada às normas, a implantação de monitoramento contínuo do uso das APIs por meio de telemetria, a configuração de alertas automáticos para versões próximas do vencimento, e o estabelecimento de processos de governança com pontos de controle obrigatórios.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A descontinuação da versão da API não ocorreu no prazo devido à ausência de um processo formalizado de gestão de ciclo de vida, o que resultou na falta de acompanhamento estruturado das datas de _sunset_ previamente definidas.

Falha operacional no processo de APIs.

O atraso na retirada da versão foi causado por dependência de participantes externos que não concluíram a migração no prazo, somado à ausência de um plano de contingência para encerramento forçado conforme exigido.

Houve um desalinhamento interno.

## 2.3 Metas de prazo máximo para atendimento de tickets (SLA)

Monitorar se a instituição respondeu, tratou ou concluiu tickets dentro do prazo aplicável, considerando tickets do mês de referência ou do estoque na data de apuração, garantindo eficiência no atendimento e evitando atrasos excessivos. 

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição objetiva do cenário identificado, com apresentação dos dados quantitativos (percentuais de SLA não atendido, volume de _tickets_ impactados, períodos afetados).

**Causas identificadas**

Análise detalhada da causa raiz, demonstrando que houve investigação estruturada. As causas podem incluir fatores como inadequação no dimensionamento da equipe, falhas em processos de priorização, ineficiências nos fluxos operacionais, indisponibilidade ou limitação de sistemas, ausência de automação ou falhas na capacitação dos colaboradores.

**Soluções aplicadas**

Descrição das ações corretivas implementadas para tratar o problema, incluindo ajustes de capacidade operacional (contratação ou realocação de equipe), revisão de SLAs e critérios de priorização, otimização dos fluxos de atendimento, melhorias sistêmicas (automação, ferramentas de monitoramento) e ações de capacitação. Deve-se demonstrar que as soluções estão alinhadas à eliminação das causas.

**Controles mitigatórios**

Apresentação dos mecanismos implementados para prevenção de nova ocorrência, como monitoramento contínuo dos indicadores de SLA, definição de alertas preventivos para tickets próximos do vencimento, rotinas de acompanhamento gerencial, indicadores de desempenho acompanhados pela governança, auditorias internas periódicas e planos de contingência para picos de demanda.

**Cronograma de regularização dos tickets em aberto**

Apresentação de cronograma detalhado para solução de cada ticket atrasado em aberto na data de apuração, com identificação do ticket, situação atual e data prevista de conclusão, permitindo o acompanhamento objetivo do cumprimento dos prazos assumidos.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

O volume de tickets aumentou 35% no período analisado sem ajuste proporcional no dimensionamento da equipe, gerando fila superior à capacidade de atendimento e impactando diretamente o cumprimento dos SLAs.

Alto volume de demandas.

A ausência de critérios automatizados de priorização resultou no tratamento inadequado de _tickets_ críticos, causando atrasos no atendimento de solicitações com maior urgência.

Problemas no processo de atendimento.

A ferramenta de gestão de _tickets_ apresentou indisponibilidades recorrentes e lentidão, comprometendo o registro, a triagem e o acompanhamento das demandas dentro dos prazos estabelecidos.

Falha sistêmica.

## **2.4 Reporte de informações (PCM e planilhas autorreportadas)**

Avaliar se a instituição reportou todas as informações exigidas, sem divergência, incompletude ou inconsistência nos dados enviados à camada de monitoramento, incluindo as planilhas autorreportadas.  

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição clara da inconsistência ou falha identificada, incluindo o descumprimento de prazos, divergências de dados, ausência de envio ou inadequação no formato exigido. Deve incluir ainda o período afetado, os tipos de informações não reportadas ou reportadas incorretamente.

**Causas identificadas**

Análise detalhada da causa raiz, demonstrando metodologia estruturada. As causas podem envolver falhas na integração de sistemas, ausência de validações automatizadas, erros manuais na consolidação de dados, lacunas nos processos de governança da informação, falhas na definição de responsabilidades ou deficiência na interpretação de requisitos regulatórios.

**Soluções aplicadas**

Descrição das ações corretivas implementadas para sanar as falhas de reporte, incluindo ajustes em sistemas (integrações, automações, validações), revisão de processos de consolidação e envio de informações, redefinição de responsabilidades entre áreas, atualização de normativos internos e realização de treinamentos. Deve-se apresentar o plano de ação com prazos, responsáveis e status, além de evidenciar que as soluções atuam diretamente sobre as causas identificadas.

**Controles mitigatórios**

Detalhamento dos mecanismos implementados para prevenção de nova ocorrência, incluindo rotinas de validação prévia dos dados antes do envio, controles de dupla checagem, monitoramento contínuo de prazos de reporte, alertas automáticos para envio regulatório, revisões periódicas de qualidade de dados, auditorias internas e governança formal sobre o processo de reporte.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A integração entre o sistema de origem e o repositório de reporte apresentou falhas de mapeamento de campos, resultando na transmissão incompleta de dados obrigatórios dentro do prazo regulatório.

Identificação de erros sistêmicos.

A ausência de validações automatizadas na etapa de consolidação permitiu o envio de informações inconsistentes, sem identificação prévia de divergências nos dados.

Falha no processo de validação.

A definição inadequada de responsabilidades entre as áreas envolvidas no reporte gerou atraso na consolidação e submissão das informações, impactando o cumprimento dos prazos estabelecidos.

Problema operacional.

## **2.5 Qualidade de dados**

Exige que a instituição garanta que os dados sejam corretos, completos, consistentes, tempestivos e rastreáveis, além de manter controles e monitoramento contínuo para assegurar a confiabilidade das informações utilizadas e reportadas.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição clara da inconsistência identificada, evidenciando falhas como dados incompletos, inconsistentes, incorretos ou fora do prazo. É necessário indicar quais bases ou sistemas foram impactados, o período de ocorrência, o volume de registros.

**Causas identificadas**

Análise estruturada da causa raiz, podendo incluir falhas em integrações sistêmicas, ausência de validações automáticas, erros manuais na entrada ou transformação de dados, inconsistências em regras de negócio, deficiência na governança de dados ou ausência de responsabilidades claramente definidas. É importante evidenciar o nexo entre a causa identificada e o problema observado.

**Soluções aplicadas**

Detalhamento das ações corretivas implementadas para restabelecimento do item, como ajustes em sistemas (correção de integrações e regras), implementação de validações automáticas, saneamento e reconciliação de bases, revisão de processos de captura e tratamento de dados e atualização de normativos internos. Deve apresentar plano de ação com responsáveis, prazos e status, evidenciando que as medidas atacam diretamente a causa raiz.

**Controles mitigatórios**

Apresentação de controles para garantir a manutenção contínua do item, como validações automáticas na origem e no processamento, reconciliações periódicas entre bases, monitoramento contínuo de indicadores de qualidade (completude, consistência, tempestividade), alertas para desvios, governança formal de dados (políticas, papéis e responsabilidades definidos), auditorias internas e revisões periódicas.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A ausência de validações automáticas na entrada de dados permitiu o registro de informações incompletas e inconsistentes, impactando diretamente a confiabilidade das bases utilizadas em reportes.

Erro de dados nas bases de reporte.

A falha na integração entre sistemas gerou divergência de informações entre bases distintas, devido à inconsistência no mapeamento de campos e regras de transformação.

Falha na integração entre sistemas.

A inexistência de governança formal de dados, com papéis e responsabilidades não definidos, resultou em falhas recorrentes na atualização, revisão e validação das informações.

Falha no processo de governança de dados.

## **2.6.1 Jornada do cliente**

Exige que a instituição mapeie, documente e monitore toda a jornada do cliente, garantindo processos claros, consistentes e sem falhas, com acompanhamento contínuo para corrigir problemas e assegurar conformidade. O foco é assegurar uma experiência fluida, eficiente e em conformidade regulatória, reduzindo riscos operacionais e impactos ao cliente.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição clara da falha identificada, indicando em quais etapas ocorreram rupturas, inconsistências ou fricções (ex.: _onboarding_, atendimento, resolução). Deve informar o período afetado, os pontos de contato impactados e os efeitos na experiência do cliente, como atrasos, retrabalho, insatisfação ou não conformidade regulatória.

**Causas identificadas**

Análise estruturada da causa raiz, que pode envolver ausência de mapeamento completo da jornada, falhas de integração entre canais, inconsistência de informações entre etapas, processos não padronizados, lacunas em treinamentos ou ausência de governança clara. Deve ser demonstrada a relação direta entre a causa identificada e o ponto de ruptura na experiência do cliente.

**Soluções aplicadas**

Descrição das ações corretivas implementadas para sanar as falhas identificadas, como revisão e redesenho da jornada do cliente, padronização de processos entre canais, melhorias em integrações sistêmicas e atualização de procedimentos internos.

**Controles mitigatórios**

Apresentação dos mecanismos implementados para prevenção de nova ocorrência, incluindo monitoramento contínuo da jornada (com indicadores de desempenho e experiência), revisões periódicas do mapeamento da jornada, testes de fluxos (ex.: cliente oculto), controles de qualidade nos pontos de contato e governança formal com definição de papéis e responsabilidades.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A inexistência de um mapeamento completo e atualizado da jornada do cliente resultou em lacunas entre etapas, gerando desconexão no fluxo de atendimento entre canais.

Problema no fluxo de jornada do cliente.

A falta de integração entre sistemas e canais de atendimento ocasionou perda de informações ao longo da jornada, exigindo retrabalho e impactando a experiência do cliente.

Falha operacional.

A ausência de padronização nos procedimentos entre áreas e canais levou a orientações inconsistentes ao cliente, causando fricções e atrasos na conclusão do atendimento.

Identificado problema de processo.

##  **2.6.2 Taxa de conversão (Compartilhamento de dados, Iniciação de Pagamento e Vínculo)**

Estabelece que a instituição deve monitorar, analisar e garantir a efetividade dos processos ao longo da jornada do cliente, assegurando que as etapas de conversão (ex.: proposta > contratação) ocorram de forma eficiente, fluida e sem barreiras desnecessárias.

**Requisitos da resposta:**

**Seção**

**Definição operacional**

**Contexto do problema**

Descrição da falha identificada, evidenciando redução ou desempenho abaixo do esperado nos processos comerciais ou de relacionamento com o cliente. Deve indicar o período impactado, os canais ou etapas da jornada afetadas (ex.: propostas não concluídas, abandono em _onboarding_), e os impactos associados, como perda de negócios ou ineficiência operacional.

**Causas identificadas**

Apresentação da análise estruturada da causa raiz que levaram à baixa taxa de conversão, podendo incluir falhas na jornada do cliente, processos pouco eficientes, etapas excessivamente complexas, inconsistência de informações entre canais, indisponibilidade de sistemas ou falta de alinhamento comercial. A instituição deve demonstrar a relação direta entre as causas identificadas e o desempenho insatisfatório do indicador.

**Soluções aplicadas**

Ações corretivas implementadas para melhoria da taxa de conversão, como simplificação de fluxos, revisão de etapas da jornada, melhorias na usabilidade de canais digitais, correção de falhas sistêmicas, padronização de abordagens comerciais e capacitação das equipes.

**Controles mitigatórios**

Apresentação dos mecanismos para prevenção de nova ocorrência e acompanhamento contínuo da taxa de conversão, incluindo indicadores monitorados periodicamente, dashboards gerenciais, alertas para queda de desempenho, testes contínuos de jornada (ex.: A/B _testing_), governança sobre processos comerciais e revisões periódicas das etapas do funil de conversão.

**Exemplos fictícios de causas corretamente formuladas X rótulos genéricos:**

**Causas aceitáveis**

**Rótulos genéricos (não aceitáveis)**

A etapa de _onboarding_ digital apresentava 5 telas adicionais obrigatórias sem justificativa regulatória, aumentando a taxa de abandono antes da finalização da proposta.

Baixa conversão no processo.

A inconsistência de informações entre os canais de atendimento gerou dúvidas no cliente, resultando em desistência durante a jornada de contratação.

Problema na jornada.

A indisponibilidade intermitente do sistema de simulação de propostas impediu a continuidade do fluxo em horários de pico, impactando diretamente a taxa de conversão.

Identificação de falha sistêmica.

# **7\. Critérios de efetividade e encerramento do Plano**

O Plano de Adequação é considerado efetivo apenas quando atende aos critérios abaixo:

-   Corrige a causa raiz, não apenas o sintoma;
    
-   Elimina a desconformidade no indicador afetado;
    
-   Implementa controle para prevenção de nova ocorrência.
    

**Importante:**

A autodeclaração de conclusão deve ser registrada no ticket correspondente, observar as datas marco do plano e conter a ciência e a concordância das áreas internas de Governança, Risco e Compliance, ou equivalentes. A ação somente é considerada concluída após o registro da autodeclaração via Service Desk, no mesmo ticket. A Associação _Open Finance_ pode revogar essa conclusão se identificar indícios de que a ação não foi executada.
