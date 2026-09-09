# MQD - Especificação Técnica

## Introdução

No contexto do Open Finance Brasil, o Motor de Qualidade de Dados (MQD) desempenha um papel fundamental, assegurando a qualidade dos dados presentes nas APIs dos participantes. Esta plataforma, desenvolvida sob o modelo de código aberto, concentra-se na avaliação da qualidade dos dados compartilhados entre os participantes, assegurando a integridade das informações.

## Especificações de Referência

O MQD valida respostas de APIs contra JSON Schemas derivados das especificações OpenAPI oficiais do Open Finance Brasil. Os endpoints aceitos podem ser encontrados em Tabela de endpoints validados pelo Motor de Qualidade de Dados (MQD)

## Repositórios de Código

Os JSON Schemas e especificações OpenAPI usados pelo MQD como source of truth estão nos repositórios:

Repositório

Descrição

[mqd-client](https://github.com/OpenBanking-Brasil/mqd-client)

Código do MQD Client (instalado nas IFs)

[mqd-schema\_generator](https://github.com/OpenBanking-Brasil/mqd-schema_generator)

Gerador de JSON Schemas a partir das specs OpenAPI

## Motivação

A motivação subjacente ao desenvolvimento do Motor de Qualidade de Dados é a promoção da transparência e confiabilidade no âmbito do Open Finance. Facilitando o acesso direto aos dados das APIs dos participantes, a plataforma elimina obstáculos na comunicação e agiliza a análise de qualidade dos dados. Além disso, ao utilizar dados dos clientes, a plataforma garante que o controle sobre informações sensíveis permanece com a instituição, reduzindo os riscos de segurança.

Outro ponto essencial de motivação reside na filosofia do código aberto. Ao desenvolver a plataforma com base nesse modelo, estamos fomentando a inovação colaborativa e a transparência. Isso permite que os próprios participantes do Open Finance contribuam para o aprimoramento contínuo da plataforma, impulsionando, assim, a melhoria geral da qualidade das APIs em todo o ecossistema. Por fim, essa abordagem possibilita que a estrutura do OFB avalie a qualidade do ecossistema, contribuindo para a construção de um ambiente seguro e confiável.

## O que o Motor de Qualidade de Dados não é

-   **Não viola a privacidade** — Apesar de utilizar dados dos clientes, a plataforma adere rigorosamente às diretrizes de segurança e privacidade. Os dados permanecem seguros nas instituições participantes.
    
-   **Não é solução universal** — Não resolve automaticamente todas as questões de qualidade. Depende da colaboração dos participantes e das diretrizes específicas de cada API.
    
-   **Não é ferramenta de monitoramento de usuários** — Atua como tecnologia que promove a integridade dos dados dentro do contexto do Open Finance.
    

## Arquivo Histórico

As páginas filhas desta seção contêm cópias históricas das especificações que foram usadas como referência durante o desenvolvimento inicial do MQD (2022-2023). **Estas cópias não são mantidas atualizadas.** Para especificações atualizadas, consulte sempre os links das tabelas acima ou o repositório `mqd-schema_generator`.
