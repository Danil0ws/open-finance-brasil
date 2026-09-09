# Acompanhamento de implementação de versões iniciais e de novas versões de APIs

## ITEM 2.2 - IPurple

## Controle de versão

**Versão**

**Data**

**Resumo das alterações**

1

Versão inicial

2

Inclusão do ciclo completo de vida das APIs, incluindo certificação, publicação e operação

## Introdução e Objetivos

Esta métrica tem como objetivo assegurar que as instituições participantes cumpram os requisitos de implementação, certificação e publicação de APIs, em conformidade com as diretrizes regulatórias e de governança do ecossistema.

A métrica abrange o ciclo de vida completo das APIs, compreendendo as etapas de desenvolvimento, maturidade, certificação, entrada em produção (go-live) e operação, garantindo sua execução de forma consistente, rastreável e aderente aos padrões de segurança, interoperabilidade e conformidade estabelecidos.

## Calendário de Certificação

As datas de certificação e entrada em produção das APIs são definidas no calendário oficial do Open Finance Brasil, disponível em: [Calendário oficial do Open Finance Brasil](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/calendars).

## Sobre a Métrica

A métrica avalia a conformidade das APIs com base em quatro dimensões:

-   Maturidade: Evolução das implementações e cumprimento dos marcos intermediários de desenvolvimento;
    
-   Certificação: Existência de certificação funcional e de segurança válida e aderente à versão disponibilizada em produção;
    
-   Publicação (go-live): Registro das APIs no Diretório de Participantes e disponibilização em ambiente produtivo conforme o calendário oficial;
    
-   Operação: Consistência entre o Diretório e o ambiente produtivo, incluindo versionamento e coexistência de versões (Current e Deprecated).
    

## Metodologia de Cálculo e Verificação

#### **A.** Cálculo de Cumprimento de Marcos (Maturidade)

Para validação do progresso técnico das implementações, utiliza-se a seguinte fórmula:

![image-20260529-034446.png](images/image-20260529-034446.png)

-   Total de testes esperados: Contempla os testes obrigatórios das APIs ofertadas, acrescidos dos testes condicionais aplicáveis (ex.: pessoa jurídica, múltiplas alçadas);
    
-   Regra de arredondamento: O quantitativo mínimo exigido para atingimento do marco deve ser arredondado para baixo;
    
    -   _Exemplo:_ para um marco de 25% com resultado de 9,25 testes, exige-se o mínimo de 9 testes com sucesso;
        
-   Critério de validade: São considerados apenas os testes executados após a data da última breaking change aplicável.
    

#### **B. Verificação de Publicação e Operação**

-   Consistência: Verificação da aderência entre os registros do Diretório de Participantes e a implementação em ambiente produtivo;
    
-   Disponibilidade (regra 404): Endpoints que apresentarem resposta com status HTTP 404 por período superior a 8 horas são considerados indisponíveis;
    
-   Convivência de versões: Verificação da disponibilidade das versões Current e Deprecated, quando exigido.
    

## Interpretação dos Resultados

Os resultados da métrica são utilizados para identificar instituições que não atendem aos requisitos de implementação, certificação e publicação de APIs.

A análise considera os seguintes aspectos:

-   Consistência entre Diretório e ambiente produtivo: Verificação se todas as APIs registradas estão disponíveis em produção; 
    
-   Disponibilidade de versões: Confirmação de que as versões “current” e “deprecated” estão disponíveis durante o período de convivência, quando aplicável; 
    
-   Disponibilidade dos endpoints: Identificação de endpoints com indisponibilidade, caracterizada por resposta HTTP 404 por período superior a 8 horas.
    

A ocorrência de falha em qualquer um dos aspectos avaliados caracteriza situação de desconformidade.

## Tratamento das Desconformidades

-   Marcos regulatórios (exceto go-live): Caso a instituição participante regularize a desconformidade dentro do prazo máximo estabelecido no ticket aberto pela Estrutura no âmbito da esteira operacional, a situação deve ser registrada para fins de gestão e acompanhamento, não sendo considerada para aplicação de medidas; 
    
-   Exceção – go-live: Falhas relacionadas ao cumprimento da publicação na data estabelecida no calendário oficial (go-live), incluindo a não publicação no Diretório de Participantes ou a não disponibilização em ambiente produtivo, são passíveis de aplicação de medidas independentemente de regularização posterior.
    

note9f744b40-e961-41df-9d15-198712b9f093

Exemplo Ilustrativo

Exemplo Ilustrativo

1.  Considere uma instituição que tenha registrado no Diretório de Participantes a API Canais de Atendimento (_channels_). A métrica estará em desconformidade se a API estiver presente no Diretório, mas não tiver sido disponibilizada no ambiente produtivo da instituição.Além disso, considere que essa API esteja na sua versão atual (_current_) 2.0.0 e que sua versão anterior esteja marcada como em desuso (_deprecated_) na versão 1.0.2. Durante o período de convivência, ambas as versões devem estar disponíveis tanto no Diretório quanto no ambiente produtivo. Se alguma dessas versões não estiver publicada, a instituição estará em desconformidade em relação ao item monitorado.
    
    ![image-20240520-185011.png](images/image-20240520-185011.png)

2.  Considere uma instituição que disponha das APIs de _Consents_, _Resources_ e Câmbio. Suponha que o total de testes esperados para um marco seja 37. Se o marco de 25% exigir 9,25 testes, será esperado o sucesso em 9 testes para alcançar o marco. Se a instituição não conseguir atingir esse número, ela será considerada em desconformidade.
    
3.  Considerando uma instituição em que a URI da certificação de segurança não esteja registrada corretamente no cadastro do servidor de autorização do Diretório. Mesmo que todos os outros critérios estejam em conformidade, a métrica consideraria a instituição em desconformidade devido a esse único item não atendido.
    

Em caso de desconformidade com algum dos critérios, o item monitorado é considerado NÃO CONFORME.

## Dados e Fontes

A avaliação da métrica é realizada a partir da integração de dados provenientes de fontes oficiais e sistemas de apoio ao monitoramento do Open Finance, assegurando rastreabilidade e consistência das análises.

São consideradas, no mínimo, as seguintes fontes:

-   Diretório de Participantes: Base oficial de registro das APIs, contendo informações de endpoints, versões e URIs de certificação; 
    
-   Motor de Conformidade Funcional: Resultados de execução dos testes de conformidade, incluindo evidências de sucesso e falha; 
    
-   Sistemas de certificação de segurança: Registros e evidências de certificação associados aos servidores de autorização das instituições participantes; 
    
-   Plataforma Analítica de Dados (PAD): Repositório centralizado que serve como base para a análise e avaliação da métrica;
    
-   Gerenciador de Configuração (GDC): Parâmetros relacionados a APIs, versões, cronogramas e marcos regulatórios. Consolidando detalhes adicionais das APIs, incluindo endpoints, famílias de APIs, versões e as respectivas datas de início e término de vigência. Essas informações são mantidas e atualizadas pelos grupos de produtos responsáveis.
    
-   Ferramentas de monitoramento de APIs: Dados de disponibilidade, incluindo respostas de endpoints e status de operação em ambiente produtivo.
    

A combinação dessas fontes de dados — Diretório de Participantes, monitoramento sintético, dados consolidados na PAD e informações do GDC, cria um ecossistema de informações, permitindo avaliação da métrica e monitoramento efetivo das APIs no contexto do Open Finance.

## Limitações e Considerações

Atualmente, não há visibilidade ou conhecimento de limitações ou considerações adicionais para esta métrica. A análise será continuamente revisada e aprimorada conforme novos dados e informações se tornem disponíveis.

## Responsável pela Aprovação AOF

Gerência de Arquitetura e Plataforma (Diretoria de Eficiência Operacional)

Gerência de Produto e Experiência (Diretoria de Tecnologia)
