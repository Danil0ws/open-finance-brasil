## Guia de recomendações para Participantes do Open Finance Brasil

# **Prevenção a Fraudes &** **Prevenção à lavagem de dinheiro e ao** **financiamento do terrorismo (PLD-FT)**

Corporativo | Interno



1




Versão 5.0. 11.03.2025



2



Corporativo | Interno




# **Sumário**

1. **Histórico de revisão** 3
2 **Apresentação** 4
3 **Escopo** 5
4 **Referências** 6
5 **Introdução** 8
6 **Dicionário** 10
**7** **Proposta de prevenção a fraudes** 12
7.1 Framework de prevenção a fraudes 12
7.1.1 Prevenção 13
7.1.2 Detecção 14
7.1.3 Remediação 15
7.1.4 Repressão 16
**8** **Detalhamento das capacidades** 17
8.1 Prevenção 17
8.1.1 Campanha de educação de clientes 17
8.1.2 Autenticação de múltiplos fatores (MFA) 19
8.1.3 _Redirect/Hybrid Flow – OpenID_ 20
8.1.4 Autorizações sem Redirecionamento 21
8.1.5 Validação de identidade no receptor e transmissor 22
8.1.6 Segurança de device 24
8.1.7 Segurança de Informação 25
8.1.8 Segurança Interna e Contenção de Ataques 28
8.2 Detecção 29
8.2.1 Ferramenta de monitoria transacional paramétrica real-time 30
8.2.2 Marcações e Reportes de infração – DICT e Resolução 6 31
8.2.2 Monitoramento de transações financeiras e não-financeiras 32
8.2.3 Modelos de _machine learning_ transacional 33
8.3 Remediação 34
8.3.1 Operação Contínua e Integral (24x7x365) 35
8.3.2   Ressarcimento em confiança 36
8.4 Repressão 37
8.4.1 Colaboração para derrubada de _Phishing_ entre Participantes 38
**9** **Prevenção à lavagem de dinheiro** 39
9.1 Políticas, Procedimentos e Controles Internos das Participantes 40
9.2 Avaliação interna de risco 43
9.3 KYC ( _know your customer_ ) 45
9.4 Monitoramento, da seleção e da análise de operações
e situações suspeitas 47
9.5 Comunicação ao COAF 48


Corporativo | Interno



3




9.6 Procedimentos destinados a conhecer funcionários, parceiros
e prestadores de serviços terceirizados 49
9.7 Acompanhamento e controle 50
9.8 Avaliação de efetividade 51


Corporativo | Interno



4




# 1. Histórico de Revisão

|Data|Versão|Descrição das alterações|
|---|---|---|
|30/03/2021|0.1|Criação do documento|
|30/04/2021|1.0|Revisão do documento – Febraban (1.1)|
|30/05/2021|2.0|Revisão do documento – Convenção (1.1/1.2/1.3/2.1/2.2/2.3)|
|30/07/2021|3.0|Revisão fnal do documento pela convenção|
|23/08/2021|4.0|Revisão fnal do GT de Prevenção a Fraudes|
|11/03/2025|5.0|Revisão fnal do GT Prevenção a Fraudes|



5


Corporativo | Interno




# 2. Apresentação

Este manual descreve as principais ameaças e recomendações de Prevenção a Fraude,
Lavagem de Dinheiro e Financiamento ao Terrorismo para os participantes do Open
Finance no Brasil.


Tem como objetivo descrever como devem ser implementadas as estratégias de
mitigação dos riscos identificados na análise feita pelo GT de Prevenção a Fraudes da
convenção OFB, do escopo de serviços de pagamentos e compartilhamento de dados.


6


Corporativo | Interno




# 3. Escopo

Estas especificações e recomendações fazem parte de um trabalho em desenvolvimento

contínuo, não tendo a pretensão de exaurir o tema; novos conceitos e definições serão

abordados em versões futuras deste documento.


Nenhuma informação aqui apresentada deve ser considerada final para qualquer

propósito.


Este documento **não** altera nenhum tipo de norma ou legislação a respeito do tema, e,

sim, recomenda boas práticas para criarmos um ecossistema seguro.


7


Corporativo | Interno




# 4. Referências

Estas especificações baseiam-se, referenciam, e complementam, onde aplicável, os
seguintes documentos:









|Referência¹|Considerações|
|---|---|
|Especifcação OAuth|Protocolos Open Source utilizados no Open Finance<br>Brasil|
|Protocolo OpenId|Protocolos Open Source utilizados no Open Finance<br>Brasil – importante atenção ao protocolo de Redirect|
|Protocolo FAPI|Protocolos Open Source utilizados no Open Finance<br>Brasil|
|Protocolo CIBA|Protocolos Open Source utilizados no Open Finance<br>Brasil|
|Protocolo PSD2|Protocolos Open Source utilizados no Open Finance<br>Brasil|
|Protocolo FIDO2|Protocolos Open Source utilizados no Open Finance<br>Brasil|
|Lei 9.613/98e 12.683/12|Lei federal referentes à prevenção a lavagem de<br>dinheiro|
|Lei 13810/19, Resolução 44e <br>Instrução Normativa BCB nº.<br>262/2022;|Leis e normas de atendimento à CSNU|
|Lei 13260/16|Lei federal referentes à prevenção de atos terroristas|
|Circulares BCB nº 3.978/20e <br>4.001/20|Norma referentes à prevenção a lavagem de dinheiro|
|Resolução Conjunta nº 1, de 4 de<br>maio de 2020, conforme em<br>vigor (“Resolução Conjunta”)|Resolução Open Finance Brasil – dispõe sobre a<br>implementação do Sistema Financeiro Aberto|


Corporativo | Interno





8




|Resolução BCB nº 1, de 12 de<br>agosto de 2020|Institui o arranjo de pagamentos Pix e aprova o seu<br>Regulamento|
|---|---|
|Resolução BCB n° 406, de 02 de<br>agosto de 2024|Dispõe sobre o compartilhamento do serviço de<br>iniciação de transação de pagamento sem o<br>redirecionamento para outros ambientes ou sistemas<br>eletrônicos|
|Resolução BCB n° 407, de 02 de<br>agosto de 2024|Altera a Resolução BCB nº 80, de 25 de março de 2021,<br>que disciplina a constituição e o funcionamento de<br>instituições de pagamento|
|Instruções Normativas BCB<br>para o Open Finance|Regras gerais do Open Finance|
|FAQ e Base normativa|FAQ do Banco Central|
|Instrução Normativa BCB n°<br>509 de 30/8/2024|Estabelece as orientações, as condições e os prazos<br>para a realização de testes em produção pelas<br>instituições participantes, o cronograma de pontos de<br>controle do processo de publicação em produção da<br>versão 2.0.0 (ou posterior) da_application programming_<br>_interface_ (API), e o prazo de validade do consentimento<br>relativos ao compartilhamento do serviço de iniciação<br>de transação de pagamento sem redirecionamento no<br>Open Finance.|



1: Ou qualquer norma ou lei que venha a substituí-las


Corporativo | Interno



9




# 4. Referências

Os itens abaixo são leituras indispensáveis para o entendimento do funcionamento do

Open Finance e dos mecanismos propostos nesse Guia.



|Referência|Considerações|
|---|---|
|Portal do Cidadão|Site do Open Finance voltado para o cidadão|
|Área do Desenvolvedor|Site do Open Finance voltado para o desenvolvedor, com<br>defnições técnicas e especifcações|
|Guia de UX|Guia de Experiência do Usuário – importante atenção ao fuxo de<br>autenticação e de validação de CPF|
|Processo sistêmico de <br>devolução de fundos (PIX)|Defnição do Banco Central para Processo de Devolução<br>Sistêmica em Fraudes envolvendo PIX|
|Temporizador<br>transacional PIX|Defnição do Banco Central para processo de temporização das<br>transações em casos com suspeitas de fraudes envolvendo PIX|
|Processo de resolução de <br>disputas|Regulamento de Resolução de Disputas no âmbito do Open<br>Finance – importante atenção ao_liability_ da instituição detentora<br>em casos de suspeita de fraude|
|LGPD - Lei Geral de <br>Proteção aos Dados|Importante atenção ao Artigo 11, II, g|
|Resolução Conjunta nº<br>6/2023|Dispõe sobre requisitos para compartilhamento de dados e<br>informações sobre indícios de fraudes.|


Corporativo | Interno



10




|Manual Operacional do<br>Diretório de<br>Identifci adores de Contas<br>Transacionais (DICT)|Disponível em:<br>https://www.bcb.gov.br/content/estabilidadefni anceira/pix/Regul<br>amento_Pix/X_ManualOperacionaldoDICT.pdf|
|---|---|
|Mecanismo Especial de<br>Devolução (MED)|Mecanismo exclusivo do Pix criado para facilitar as devoluções em<br>caso de fraudes, aumentando as possibilidades da vítima reaver os<br>recursos.|
|Guia de implementação <br>dos procedimentos de <br>devolução no Pix, com <br>ênfase no Mecanismo<br>Especial de Devolução|Disponível em:<br>https://www.bcb.gov.br/content/estabilidadefnanceira/pix/Guia<br>%20MED%20-%20vers%C3%A3o%202.0.pdf|
|Canal no Youtube|Página do Open Finance com vídeos explicativos sobre<br>infraestruturas e processos|


Corporativo | Interno



11




# 5. Introdução

**A segurança e a correta infraestrutura, com o objetivo de prevenir as fraudes e a**

**PLD/FT são elementos primordiais a serem observados pelas Participantes.**


A questão de combate a fraudes mostra-se tão relevante no OFB que (i) demandas de

clientes decorrentes de fraudes devem ser identificadas e reportadas pelas Participantes

nos relatórios semestrais de compartilhamento de dados (cf. art. 33, §1º, I, da Resolução

Conjunta) e (ii) casos de sua suspeita justificada podem levar à proposta ao cliente de

revogação do consentimento pelas Participantes transmissoras de dados ou detentoras

de contas (cf. art. 15, §2º, da Resolução Conjunta).


Ademais, as próprias Participantes comprometem-se com procedimentos e controles

internos no compartilhamento, os quais se somam a políticas, procedimentos e controles

internos já adotados pelas próprias Participantes, inclusive para prevenção à utilização do

Sistema Financeiro para prática de crimes de lavagem de dinheiro e financiamento ao

terrorismo.


Inclusive para prevenção à utilização do Sistema Financeiro para prática de crimes de

lavagem de dinheiro e financiamento ao terrorismo, os Participantes devem garantir

atendimento a Lei nº 9.613/1998, que impõe obrigações para a prevenção e combate ao

crime de lavagem de dinheiro e financiamento ao terrorismo, tais quais as obrigações,

estabelecidas pelos artigos 10 e 11 da referida Lei, que estabelece o dever de identificar

clientes, manter registros e comunicar operações financeiras e ainda o envio das

comunicações de operações financeiras e o envio de comunicações de não ocorrência de

propostas, transações ou operações passíveis de serem comunicadas. A Lei 13.260/2016

relativa a atos terroristas, tratando de disposições investigatórias e processuais e

reformulando o conceito de organização terrorista e Lei 13.810/2019 dispõe sobre o

cumprimento de sanções impostas por resoluções do Conselho de Segurança das Nações

Unidas, incluída a indisponibilidade de ativos de pessoas naturais e jurídicas e de

entidades, e a designação nacional de pessoas investigadas ou acusadas de terrorismo,

de seu financiamento ou de atos a ele correlacionados.


12


Corporativo | Interno




Tendo em vista a rápida evolução do Ecossistema, bem como os produtos que vêm sendo

lançados, estratégias de prevenção à Fraudes bem como PLD/FT devem ser consideradas

na modelagem de negócios de todos os participantes do OFB.


**Este Guia, portanto, é composto de recomendações que poderão ser observadas**

**diretamente pelas Participantes. Apresenta detalhes técnicos associados a requisitos**

**de segurança a serem adotados nas diferentes estratégias de prevenção a fraudes e a**

**tecnologias que compõem a infraestrutura do OFB, com foco no escopo da Estrutura,**

**sem prejuízo da consequente supervisão do BCB.**


Todos os conteúdos deste Guia são de natureza sugestiva e devem ser considerados

como recomendações. Nenhum dos itens descritos neste documento deve ser

interpretado como de implementação mandatória, independentemente da maneira que

são descritos, a menos que sejam amparados por Normativas do Banco Central ou regras

do Open Finance.


13


Corporativo | Interno




# 6. Dicionário

**Conta fria**


Conta aberta por um Fraudador em nome de um titular/cliente.


A abertura da conta fria é possível quando o Fraudador tem posse dos dados cadastrais

do titular/cliente, se passando pelo mesmo e abrindo contas em nome deste com o

objetivo de movimentar valores provenientes de golpes financeiros e/ou outros crimes de

natureza diversa.


Usualmente, essa abertura indevida se dá por exploração de falhas ou fragilidades nos

procedimentos de identificação e autenticação da instituição responsável pela conta.


**Engenharia social**


Ato pelo qual um fraudador utiliza a combinação de texto e contexto para colocar sua

vítima em um golpe com o objetivo de causar danos financeiros ou de imagem. Os

criminosos utilizam uma variedade enorme de contextos, tais como informações obtidas

pelas redes sociais, com a finalidade de induzir o cliente a lhe passar as credenciais de

pagamento e/ou para que o cliente acredite no que ele está dizendo e concorde em

passar as credenciais de pagamento e/ou de acesso a contas financeiras.


A engenharia social é um meio pelo qual os Fraudadores obtêm informações para

executar golpes, subtrair valores ou obter vantagens ilícitas.


Exemplos: Golpe do motoboy, golpe do WhatsApp, golpe da URA falsa etc.


**Conta Laranja**


O fraudador usa conta de terceiros, pessoas que fornecem seu nome, CPF e dados e

credenciais bancários, para movimentar valores e adquirir bens, para prática de atos e

atividades ilícitas.


14


Corporativo | Interno




Usualmente essas contas são autênticas, abertas por usuários reais com suas

verdadeiras credenciais e aplicação válida de fatores de autenticação, diferentemente da

“Conta Fria” definida anteriormente.


Esses terceiros podem ou não ter conhecimento de que a conta será usada para fins

ilícitos (podem ter sido induzidos ao fornecimento das credenciais por alguma forma de

engenharia social e remuneração financeira).


_**Phishing**_


Mensagens e e-mails falsos que induzem o usuário a clicar em links falsos, acessar

interfaces digitais falsas e informar dados e credenciais de acesso ou pagamento, ou

instalar _malware_ para ataques posteriores.


**Golpe do falso funcionário**


O fraudador entra em contato com a vítima se passando por funcionário de central do

banco ou instituição de pagamento e induz a vítima a fornecer credenciais de acesso ou

autenticação, a cadastrar novos fatores de autenticação ou dispositivos de acesso, ou a

executar transações indevidas, sob a falsa justificativa de se tratar de um teste, estorno,

procedimento de segurança, entre outras razões.


**Invasão de conta**


Ato pelo qual o fraudador em posse das credenciais de acesso do cliente (obtidas

mediantes diferentes técnicas mencionadas nesta seção), acessa a conta com o objetivo

de obter ganhos financeiros ou vantagens ilícitas, por meio de transferências,

pagamentos, contratação de empréstimos ou outras ações.


_**Pushing**_


Ato de engenharia social no qual, após realizar uma invasão de conta ou abertura de uma

Conta Fria nas instituições Receptoras ou Iniciadoras, o fraudador inicia a solicitação de

múltiplos processos de consentimento ou iniciação de pagamentos indevidos, usando

fluxos que permitem o envio de notificações às Transmissoras e Detentoras mediante


15


Corporativo | Interno




uma identificação simples (ex. CPF, CNPJ, email, número de telefone). Ao se

acostumarem com esse processo, os usuários podem se tornar mais vulneráveis a golpes,

aprovando transações que não foram solicitadas.


***As modalidades de fraude acima descritas podem ser praticadas de maneira**

**independente ou também combinadas entre si, possibilitando diferentes tipos de**

**ataques.**


**Roubo de device**


Prática de roubo ou furto de dispositivo eletrônico (computador ou especialmente

dispositivo móvel) habilitado a realizar transações e operações bancárias, mediante a

utilização do mesmo para a invasão da conta bancária do cliente.


Exemplo: Após realizado o roubo ou furto, o fraudador acessa o dispositivo já

desbloqueado durante o crime, ou tenta descobrir a senha de desbloqueio usando dados

cadastrais do cliente ou testando combinações comuns (ex. 123456 ou 111111). O fraudador

desabilita a função de encontrar o celular para evitar que o dono rastreie ou apague as

informações do aparelho. Em seguida, tenta descobrir qual a senha do aplicativo do banco

ou de instituições de pagamento procurando por “senha” no campo de busca do celular ou

tenta acessar o recurso de “senhas” em “ajustes”. Com essa informação, entra no

aplicativo do banco ou da instituição de pagamento e utiliza a função de recuperação de

senha.


**PLD/FT**


Prevenção à Lavagem de Dinheiro e ao Financiamento do Terrorismo.


16


Corporativo | Interno




# 7. Proposta de prevenção a fraudes

**7.1 Framework de prevenção a fraudes**


Este framework de prevenção a fraudes é aplicável às Participantes, a partir de 4 (quatro)
pilares orientadores:


i. Prevenção a Fraudes;
ii. Detecção de Fraudes;
iii. Remediação de Fraudes, e;
iv. Repressão a Fraudes.


Para cada um dos pilares orientadores, foram mapeados:


i. Orientações/recomendações a serem observadas pelas Participantes; e
ii. Possíveis riscos ao OFB.


Cada uma das orientações que compõem cada um dos pilares estão a seguir detalhados,
conforme níveis de recomendação baseados no seu potencial de mitigação ao risco de
exposição a fraudes e golpes:


i. Alto: Orientação de implementação altamente recomendada para os
Participantes;
ii. Médio: Orientação de implementação recomendada para os Participantes;
iii. Baixo: Orientação opcional ou informativa para os Participantes.


**7.1.1** **Prevenção**


**I. Recomendações de Nível Alto**


1. Campanha de educação de clientes pelas Participantes
2. Autenticação de múltiplos fatores (MFA)
3. Redirect/Hybrid Flow - OpenID
4. Autorizações sem Redirecionamento
5. Validação de identidade do cliente
6. Disseminação para o público em geral da existência do MED e da importância de
sua utilização. (relato de infração)


**Riscos**


17


Corporativo | Interno




1. Abertura de Conta Fria e uso de Conta Laranja em detentora de conta pagadora ou
recebedora ou cadastro indevido em iniciadoras de transação de pagamento.
Consentimentos indevidos para Compartilhamento de Dados e Iniciação de
Pagamentos
2. Invasão de contas
3. Engenharia social
4. _Phishing_
5. _Pushing_
6. Participantes iniciadoras de transação de pagamento, detentoras de conta
pagadoras ou recebedoras criadas para prática de fraudes
7. Fragilidade no processo de segurança na adesão ao diretório centralizado do Open
Finance
8. Aumento de desacordo comercial


**7.1.2** **Detecção**


I. **Recomendações de nível alto**


1. Ferramenta de monitoria transacional paramétrica real-time
2. Monitoramento de transações financeiras e não-financeiras


3. Modelos de _machine learning_ transacional
4. Temporizador transacional


**Riscos**


1. Ataques de alta velocidade, com transferência e saques em sequência
2. Ataques de força bruta
3. Ausência de capacidade de detecção analítica, modelos de _machine learning_ e
sistemas de detecção real time
4. Falta de tempo hábil para treino de algoritmos _de machine learning_


5. _Falta de tempo hábil para a ativação do MED;_


**7.1.3** **Remediação**


I. **Recomendações de nível alto (conforme normas próprias aplicáveis** )


1. Operação contínua e integral


**Riscos**


1. Auto fraude


18


Corporativo | Interno




2. Obrigação de manter os limites transacionais de meios de pagamento similares,
mas que tenham nível de risco diferentes
3. Ausência de padronização do processo de interferência nas transações de
instituições iniciadoras de transação de pagamento
4. Ausência de política de responsabilidade para Participante que abriu a Conta Fria,
em inobservância à regulamentação aplicável


**7.1.4** **Repressão**


I. **Recomendações de nível alto**


1. Colaboração para identificação de _Phishing_ entre os Participantes.


19


Corporativo | Interno




# 8. Detalhamento das **capacidades**

**8.1 Prevenção**


**8.1.1 Campanha de educação de clientes – nível alto**


I.O QUE É?


As campanhas de educação de clientes serão promovidas diretamente pelas
Participantes para orientação de clientes na proteção dos seus dados cadastrais e
transacionais no OFB. Incluem recomendações de seguranças, alertas nas interfaces das
Participantes, informações detalhadas sobre os golpes e fraudes mais praticados e
formas de prevenção adequada


II.COMO FUNCIONA?


As Participantes prepararão, de acordo com suas políticas de comunicação e de
segurança, campanhas contínuas de educação direcionadas aos clientes, por meio de
canais digitais, com objetivo de conscientizar os clientes sobre o uso atento e correto das
funcionalidades disponíveis no âmbito do OFB e sobre o dever de cada cliente de manter
seus dados em segurança.


As campanhas de educação poderão conter as seguintes formas de comunicação:


         - Mensagens de esclarecimento sobre o uso das funções do OFB por meio de mídias
sociais e canais de alto engajamento;


         - Mensagens de esclarecimento sobre o uso das funções do OFB por meio de canais
digitais (APP, Portal, Internet Banking)


O conteúdo dessas campanhas de educação abordará os seguintes temas:


         - Funcionalidades habilitadas pelo OFB (compartilhamento de dados, iniciação de
pagamentos, etc.);


         - Dados compartilhados pelo cliente;


         - Finalidades de uso desses dados compartilhados pelas Participantes;


         - Dicas de segurança ao cliente, incluindo descrições de modalidades de fraude,
como ataques de phishing, roubo de identidade, engenharia social;


         - Deveres e responsabilidades dos clientes quanto à auto fraude.


1


Corporativo | Interno




As mensagens dessa campanha de educação poderão ser encaminhadas pelos canais de
comunicação de cada Participante, incluindo e-mails, redes sociais e notificações nos
aplicativos, diretamente aos seus clientes.


Recomendação de Recorrência: O GT de Prevenção à Fraudes Recomenda que, ao menos,
1 (uma) ativação educacional sobre prevenção à Fraudes seja realizada pela participante
junto aos seus clientes em ciclos determinados, por meios diversos, a fim de que não
sejam direcionados para Spams e afins.


III. MITIGAÇÃO DE RISCOS


As campanhas de educação pretendem mitigar o uso incorreto das funções habilitadas no

OFB pelos clientes, por meio dos canais digitais oficiais, além de evitar golpes, fraudes,

vazamento de dados, perdas financeiras, entre outros riscos.


Os clientes deverão ser orientados pelas Participantes para se atentar a comunicações

não oficiais das Participantes, por e-mails, SMS ou ligações, especialmente

comunicações contendo links suspeitos.


IV. EXPERIÊNCIA DO USUÁRIO


Os clientes podem receber as comunicações por meio de: SMS, notificação nos canais

digitais ( _push_ ), e-mails, redes sociais (Instagram, Facebook, Twitter, etc.) e demais

veículos de comunicação (TV, rádio, jornais, etc.), a critério de cada participante.


**8.1.2 Autenticação de múltiplos fatores (MFA) – nível alto**


I. O QUE É?


A utilização de ferramentas de segurança de Autenticação de Múltiplos Fatores (“MFA”),

que consiste em associar mais de uma forma de autenticação para adicionar camadas de

proteção aos processos transacionais para autenticar a identidade do usuário.


Os fatores de autenticação são itens ligados ao usuário, inclusive, sem limitação:


            - Algo que o usuário possui (uma chave segura ou um smartphone)


            - Algo que o usuário sabe (uma senha ou um PIN)


            - Algo que o usuário é (uma impressão digital ou reconhecimento facial)


2


Corporativo | Interno




II. COMO FUNCIONA?


As Participantes detentoras de conta e as iniciadoras de pagamento poderão utilizar MFA

na jornada de confirmação e autenticação em todas as transações.


A MFA adiciona novas camadas de verificação da identidade, trazendo maior segurança

em todo o processo. Quando o cliente inserir seu login e senha, o Portal poderá validar e

solicitar, por exemplo, um código randômico, uma biometria ou um dispositivo

habitualmente vinculado ao cliente.


O uso de MFA poderá ocorrer de acordo com o nível de risco (score) observado em cada

processo executado pelo cliente, seguindo as políticas de segurança específicas das

Participantes, conforme as orientações e padrões de segurança recomendados no OFB.


Figura 1 - Exemplo de processo com autenticação com múltiplos fatores


III. MITIGAÇÃO DE RISCOS


A solicitação de MFA traz maior confiabilidade e dificulta a violação de segurança e o

comprometimento de dados, minimizando danos graves ou ataques de identidades dos

clientes, das Participantes e da Estrutura.


As principais ações a serem evitadas e os principais riscos a serem mitigados com a

utilização do MFA no OFB são:


i. consulta indevida de dados,

ii. uso de Engenharia Social e

iii. Invasão de Conta.


3


Corporativo | Interno




IV. EXPERIÊNCIA DO USUÁRIO


Na jornada do cliente no OFB, a aplicação do MFA poderá ser solicitada para maior

segurança e confiabilidade nas identificações e transações realizadas.


**8.1.3 Redirect/Hybrid Flow - OpenID – nível alto**


I.O QUE É?


O REDIRECT entre aplicativo (APP) e/ou Browser no Desktop é o fluxo que permite que a

Participante iniciadora de pagamento redirecione o usuário de uma aplicação (APP) ou

navegador de uma Participante para outro aplicativo (APP) ou navegador instalados no

mesmo device, recomendando-se o uso de aplicativo (APP) da Participante Detentora de

conta. Esse redirecionamento é realizado através do fluxo conhecido como Hybrid Flow,

especificado pela OpenID Foundation, um dos fluxos padrões de autenticação e

autorização para o OFB. Para mais detalhes, clique aqui. Se houver divergência nas duas

fontes, por favor, considere como a fonte da verdade aquela referenciada no link


Esse fluxo permite que o cliente realize sua autenticação na Participante Detentora de

conta, com a possibilidade de usar os mesmos métodos de autenticação que são

utilizados para acessar seu canal digital, o que confere o mesmo grau de segurança que

seria adotado em um acesso à Detentora.


II. COMO FUNCIONA?


A execução com sucesso do Hybrid Flow concede à Participante Receptora/Iniciadora

credenciais de autorização, nomeadas access_token e refresh_token, para o consumo de

dados ou execução de transações de pagamento. Associados aos certificados emitidos

para as Participantes Receptoras/Iniciadoras, esses tokens autorizam a chamada às APIs

de serviços. Esses tokens têm duração estipulada pelo próprio usuário, e podem ter

validade indeterminada. Por essas razões, o armazenamento seguro desses certificados e

credenciais, seja em aplicações de front ou back-end, e o controle adequado de acesso

dos usuários é fundamental para a segurança do OFB e dos dados e fundos dos usuários

finais.


4


Corporativo | Interno




III. MITIGAÇÃO DE RISCOS


Abaixo, elencamos cenários, riscos e boas práticas que podem ser praticadas pelas

instituições participantes do Open Finance, referentes ao fluxo FAPI _Hybrid Flow_ :


Cenário 1


        - Contexto: Após o redirecionamento, a iniciadora detém credenciais com validade

indeterminada e que representam a autenticação do usuário.

        - Risco: O vazamento dessa credencial poderá fazer com que um usuário se passe

por outro.

        - Mitigação/Boa prática: É recomendado que a iniciadora mantenha essas

credenciais apenas em seu _back-end_, não expondo para o cliente final.


Cenário 2


        - Contexto: Roubo de url no fluxo FAPI _Hybrid Flow_

        - Risco: Engenharia Social - Fraudador começa uma iniciação de pagamentos via

app do ITP, compartilha urls de redirecionamento via rede social, usuário autoriza

no app do Banco e manda a url de volta e o Fraudador conclui no app do ITP.

        - Mitigação/Boa prática: As instituições participantes do Open Finance podem

realizar campanhas educativas aos usuários alertando sobre engenharia social e

ensinando que urls não devem ser compartilhadas.”

`o` Roubo de Device e invasão de conta.


**8.1.4 Autorizações sem Redirecionamento – nível Alto**


I. O QUE É?


Desde 2023, após a implantação das jornadas de compartilhamento de dados e iniciação

de pagamentos, o OFB prosseguiu com melhorias e novas propostas e adaptações aos

fluxos e protocolos originais. Entre essas propostas, estão algumas jornadas que não

exigem o redirecionamento do usuário ao ambiente das Participantes

Receptoras/Detentoras em todas as solicitações de autorização, visando melhorias de

experiência e menor atrito ao usuário. Essas jornadas podem ser funcionalmente


5


Corporativo | Interno




classificadas, para o ponto de vista de Prevenção, como “Autorizações sem

Redirecionamento”.


COMO FUNCIONA A JORNADA SEM REDIRECIONAMENTO?


O serviço de iniciação de pagamentos sem redirecionamento (ou Jornada Sem

Redirecionamento) é aquele em que o cliente inicia e conclui a solicitação de transação

sem sair do ambiente da ITP – ou seja, sem ser redirecionado ao ambiente da detentora

de conta.


O desenvolvimento da Jornada Sem Redirecionamento foi sugerido pelo Banco Central do

Brasil com o objetivo de melhorar a experiência do usuário, preservando a segurança de

pagamento e ser uma alternativa à jornada de iniciação de pagamento com

redirecionamento.


Para habilitar a Jornada Sem Redirecionamento, o BCB delineou as seguintes Diretrizes:


O processo deve ser constituído de duas etapas: (i) Vínculo de Conta e (ii) Pagamento;


Vínculo de conta: Processo em que o cliente vincula sua conta a ITP, com autenticação

usual (FAPI Hybrid Flow) no detentor de contas;


Pagamento: Processo em que o cliente solicita a iniciação de pagamento e não é

redirecionado ao ambiente da detentora de conta;


Por último, a Estrutura de Governança responsável pelo desenvolvimento da Jornada Sem

Redirecionamento elegeu o FIDO2 como protocolo de autenticação que irá habilitar o

serviço de acordo com as Diretrizes do Banco Central do Brasil.


III. MITIGAÇÃO DE RISCOS PARA JORNADA SEM REDIRECIONAMENTO


Para o lançamento da Jornada sem Redirecionamento, o Banco Central do Brasil lançou a

Instrução Normativa BCB n° 512 de 30/8/2024, onde fica estabelecido no Art.16 § 1º que

para iniciação de transações por meio do compartilhamento do serviço de iniciação de

transação de pagamento sem redirecionamento o limite máximo é de R$500,00 por

transação. Obs.: Esta informação é a oficial no momento em que este documento está


6


Corporativo | Interno




sendo atualizado. Solicitamos que, no momento da leitura, o Participante revise a

Normativa para verificar se a regra ainda está em vigor.


Adicional a isso, a Estrutura de Governança deliberou pelo compartilhamento dos sinais

de ricos nos momentos de vínculo de conta e de pagamento sem redirecionamento, desta

forma a instituição Detentora de Conta será capaz de avaliar os respectivos sinais e tomar

suas devidas ações, conforme Regulamentações vigentes e regras do Open Finance.


O Participante poderá consultar mais detalhes sobre os sinais de riscos na Jornada sem

Redirecionamento no seguinte link:

https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/141557761/SV+API+
+Pagamentos+sem+Redirecionamento


VI. COMO FUNCIONAM AS TRANSFERÊNCIAS INTELIGENTES?


No fluxo de Transferências Inteligentes (Sweeping Accounts), o usuário seleciona no

ambiente da Participante Iniciadora parâmetros transacionais com um dos seus casos de

uso sendo saldar uma conta que fique sem fundos, e é redirecionado para a Detentora

para autorizar essas transações. Uma vez autorizadas, essas transferências ocorrem sem

a ação do usuário na Detentora quando cumpridos os requisitos para sua efetivação.


VII. MITIGAÇÃO DE RISCOS PARA AS TRANSFERÊNCIAS INTELIGENTES


As principais ações a serem evitadas e os principais riscos a serem mitigados nestas

jornadas são:


i. Roubo de Device;

ii. Invasão de Conta, e;

iii. _Pushing_ .


Como estas jornadas não permitem uma autenticação customizada ao risco, seguindo os

critérios padrão das Detentoras e a detecção de sinais de risco em seu próprio ambiente,

fazem-se necessários alguns controles adicionais, como o uso de limites específicos para

esses tipos de pagamento, que devem ser configurados e confirmados pelo usuário.


7


Corporativo | Interno




Adicionalmente, as Iniciadoras deverão compartilhar alguns sinais de risco nas chamadas

de cadastro e transação, que deverão ser interpretados e tratados pelas Detentoras para

adicionar às suas capacidades de Detecção nessas jornadas.


Reforça-se a segurança do armazenamento de certificados e credenciais nestes fluxos.


**8.1.5 Validação de identidade do cliente – nível alto**


I. O QUE É?


Na iniciação de pagamentos no canal Open Finance, é obrigatório que as Participantes

garantam que a pessoa natural que iniciou a jornada de pagamento seja a mesma pessoa

que irá autenticar e concluir a transação na instituição receptora.


Os métodos de autenticação e identificação das pessoas ficam sob a responsabilidade de

cada Participante detentora de conta, que deverá validar as credenciais e informações

disponibilizadas pelas instituições iniciadoras de pagamentos.


II. COMO FUNCIONA?


Maiores orientações estão no Guia de Experiência do Usuário.


[Disponível em:](data/references/guides/Guia.md)

[https://openfnancebrasil.atlassian.net/wiki/spaces/OF/pages/17378535/Guia+de+Experi](data/references/guides/Guia.md)

+ncia+do+Usu+rio


III. MITIGAÇÃO DE RISCOS


Ao implementar esse controle, é possível mitigar o risco de um fraudador, em posse de

uma conta iniciadora de pagamento, iniciar inúmeras transações em contas de diferentes

Participantes.


É altamente recomendado que seja usada uma abordagem em camadas para a

verificação de identidade que combine validação de dados, autenticação biométrica e

prova de identidade durante o processo de onboarding de clientes. Isso pode incluir

verificações de documentos de identidade, selfies e validação cruzada de informações.


8


Corporativo | Interno




Adicionalmente, é necessário que Participantes Receptoras/Iniciadoras e

Transmissoras/Detentoras identifiquem em contratos, termos de uso, e nas mensagerias

do protocolo do OFB a situação em que oferecerem os serviços de consumo de dados e

iniciação de pagamentos, e contas transacionais, para outras instituições (modelo _as-a-_

_service_ ), para que seja possível a identificação correta dos usuários finais, que não têm

vínculo com esses Participantes fornecedores dos serviços.


IV. EXPERIÊNCIA DO USUÁRIO


Na situação em que um cliente idôneo tentar iniciar uma transação em nome de outra

pessoa natural, o cliente receberá uma mensagem de negativa devido ao fato de o seu

CPF ser diferente da conta da iniciadora, como por exemplo, um marido tentando realizar

um pagamento em nome da esposa.


**8.1.6 Segurança de device – nível crítico**


I. O QUE É?


Segurança de device consiste em todas as ferramentas que podem ser usadas por

Participantes nas jornadas de consentimento e na iniciação de pagamentos no OFB, a fim

de tornar mais robustas as camadas de proteções e criar uma jornada mais segura para

os clientes.


II. COMO FUNCIONA?


Para o cliente, os processos de segurança do device são praticamente imperceptíveis

durante as interações. As variáveis digitais e as validações dos componentes irão mapear

       - perfil seguro do cliente autenticado, tornando-o elegível à jornada requerida e

garantindo vias de segurança durante suas solicitações e transações.


As proteções ofertadas, tanto nativas quanto de bordas e de processos, podem ser

adicionadas a variáveis digitais e _machine learning_ de análises de risco, reforçando o

processo naquele device.


9


Corporativo | Interno




Alguns exemplos de funcionalidades que podem diminuir as fragilidades do canal OFB, a

serem adotadas pelas Participantes, são:


      - Aplicação Anti-automação

      - Certificado Digital

      - Criptografia end-to-end

      - Geolocalização

      - Habitualidade do device

      - Identificação do dispositivo (ID Sessão, Device ID, IP, UserAgent)

      - _Machine learning_

      - Múltiplos Fatores de Autenticações (MFA)

      - Ofuscação de Código (técnicas de desenvolvimento de código para dificultar o
entendimento e evitar ataques)

      - _Firewall_ de borda

      - Componentes de verificação comportamental do device e usuários

      - Variáveis digitais


III. MITIGAÇÃO DE RISCOS


Os protocolos de segurança que envolvam o _device_ têm o objetivo de assegurar melhor
jornada e experiência, além de garantir:


       - Confiabilidade do usuário

       - Inibição de _hacking_

       - Melhor perfilamento do cliente durante as transações

       - Aperfeiçoamento da experiência do cliente

       - Maior proteção dos dados do cliente

       - Aumento da robustez da aplicação (APP)


IV. EXPERIÊNCIA DO USUÁRIO


O cliente poderá ter uma jornada mais completa e satisfatória se seus dados estiverem
sendo protegidos com uma segurança robusta em cada etapa da interação. Dessa
maneira, ele mantém um relacionamento de confiança durante o uso da aplicação (APP),
compartilhamento de seus dados e realização de transações.


10


Corporativo | Interno




**8.1.7 Segurança de informação – nível alto**


I. O QUE É?


A segurança da informação tem por objetivo impedir/dificultar que dados das transações

sejam alterados.


II. COMO FUNCIONA?


Na jornada de pagamento recorrente os pagamentos serão realizados de forma

assíncrona da criação dos mesmos, de forma que as validações previstas já foram

realizadas e aprovadas.


III. MITIGAÇÃO DE RISCOS


É necessário criptografar as informações referentes a valores e dados da conta de
crédito/chave pix, bem como recomenda-se o envio de uma notificação prévia ao débito
para impedir:


       - Subtração de valores com prejuízo a quem estava previsto de ser realizado o
crédito;


II. EXPERIÊNCIA DO USUÁRIO


Por ser um processo assíncrono o usuário eventualmente não perceberá o débito dos

recursos e poderá ter eventuais prejuízos, impactando assim negativamente a

experiência do usuário.


**8.1.8 Segurança Interna e Contenção de** **Ataques – nível alto**


I. O QUE É?


Quando determinadas fragilidades em jornadas ou sistemas são descobertas, elas podem

ser rapidamente exploradas por fraudadores ocasionando perdas e impactos

significativos em um curto espaço de tempo. É fundamental que os participantes tenham

planos de ação e times preparados para agir de forma preventiva e reativa nesses

contextos.


11


Corporativo | Interno




II. COMO FUNCIONA?


Recomenda-se que participantes realizem auditorias internas regulares e fornecer

treinamento contínuo aos funcionários para reconhecer e reportar atividades suspeitas.

Recomenda-se implementar medidas para monitorar e mitigar fraudes internas, incluindo

       - uso de ferramentas de auditoria e monitoramento de atividades.


É recomendado também desenvolver planos claros de resposta a incidentes que incluam

procedimentos de contenção, comunicação e relato em caso de ataques bem-sucedidos.

Recomenda-se garantir que todos os funcionários estejam cientes desses planos e

saibam como agir rapidamente.


**8.2 Detecção**


**8.2.1 Ferramenta de monitoria transacional paramétrica real-time – nível alto**


I. O QUE É?


Trata-se de uma ferramenta com capacidade técnica de receber e processar em tempo
real dados inerentes às transações e às interações efetuadas no OFB.


O objetivo é monitorá-las de forma automatizada, sob a ótica de prevenção e detecção de
fraudes e PLD/FT, baseada em parâmetros pré-estabelecidos e regras de monitoramento
de cada Participante.


II.COMO FUNCIONA?


Recomenda-se que as participantes implementem, em até 12 (doze) meses, uma
ferramenta que funcionará como filtro de operações fraudulentas e suspeitas de PLD/FT.


É recomendado que as Participantes que já possuem tal ferramenta implementem na
rotina de monitoramento e de regras de prevenção e detecção de fraudes e PDL-FT para
todas as transações do OFB. Também é recomendado que tal ferramenta permita a
criação e manutenção dessas rotinas de monitoramento, com respeito a avaliações
internas de risco das Participantes, em tempo real, objetivando o monitoramento das
transações financeiras e não financeiras efetuadas no ecossistema do OFB.


III. MITIGAÇÃO DE RISCOS


Com os dados das transações financeiras e não financeiras recebidos e processados pela
ferramenta em tempo real, as Participantes terão a capacidade de elaborar regras


12


Corporativo | Interno




baseadas em parâmetros de suspeitos anteriormente conhecidos, filtrando transações
regulares de transações irregulares. Dessa forma, será possível monitorar e dar
tratamento a situações suspeitas, reduzindo o risco de perdas financeiras e aumentando

       - nível de segurança e a credibilidade do OFB para clientes e Participantes.


IV. EXPERIÊNCIA DO USUÁRIO


A implementação e manutenção de uma ferramenta de monitoramento em tempo real
agregará positivamente para a experiência do usuário, uma vez que possa ajudar as
Participantes a diferenciarem de maneira mais fácil e rápida operações fraudulentas de
operações não fraudulentas, contribuindo, inclusive, para manter taxas mais altas de
conversão e aprovação das transações com maior segurança e sustentabilidade.


Recomenda-se que a ferramenta possa inclusive suspender temporariamente as
operações fraudulentas, que poderão ser retomadas ou canceladas de forma definitiva.


**8.2.2 Marcações e Reportes de infração – DICT e Resolução 6 – nível alto**


I. O QUE É?


O advento do ecossistema do Pix incentivou a adoção de bases compartilhadas entre
instituições de marcações de infrações e fraudes cometidas em pagamentos e
transferências. Essas bases são definidas por normativos e resoluções, e devem ser
alimentadas e consumidas por todos os participantes dos arranjos de pagamentos
usados no OFB.


II. COMO FUNCIONA?


O Art. 1º da Resolução Conjunta nº 6/2023 determina que instituições financeiras,
instituições de pagamento e demais instituições autorizadas (com exceção às
administradoras de consórcio) devem reportar e compartilhar dados e informações sobre
indícios de fraudes nestas bases.


A forma de compartilhamento está prevista nos Art.2º da Resolução Conjunta nº 6/2023,
definindo os “indícios de fraude”, que englobam as informações transacionais, de
identificação e de canal que a instituição participante tenha a possibilidade de obter. O
compartilhamento se dá por sistema eletrônico que obedeça aos requisitos do Art. 3º e 5º
da referida resolução, inclusive com a possibilidade de contratação de empresa
terceirizada para a implantação dos serviços. Art. 1º, ou seja, (Art.1º §1º); destaque ainda
para o §3º, do Art.2º, o qual prevê a necessidade de consentimento específico para o
compartilhamento de dados.


13


Corporativo | Interno




As demandas da Res. Conj. nº 6 se aplicam para diferentes métodos de pagamento, mas
especificamente para o Pix, marcações de fraudes reportadas e confirmadas são
previstas no próprio DICT, quando são abertas contestações pelos PSPs Pagadores
através do MED (Mecanismo Especial de Devolução).


III. MITIGAÇÃO DE RISCOS


Como mencionado, instituições autorizadas devem realizar os reportes de indícios de
fraudes, mas também é fundamental que todos os Participantes que executem
autorizações de pagamentos consumam estas informações para reforçar suas
estratégias de detecção. O uso destas informações permite identificar contas
recebedoras suspeitas, e aplicar alertas, temporização ou mensagens contextualizadas
ao usuário.


**8.2.3 Monitoramento de transações financeiras e não- financeiras – nível alto**


I. O QUE É?


O monitoramento é a capacidade de as Participantes coletarem e analisarem informações
de forma massiva, com o objetivo de prever e identificar possíveis irregularidades nas
transações efetuadas pelo OFB.


As transações não-financeiras podem ser configuradas por algumas interações dentro do
ecossistema do OFB, tais como criação de cadastro ou conta, alteração de dados
cadastrais, uso de credenciais, alteração de senhas de acesso a sistemas e aplicativos
(APP).


As transações financeiras são aquelas que envolvem movimentações financeiras, como,
por exemplo, pagamentos, liberação de crédito, entre outras.


II. COMO FUNCIONA?


Recomenda-se que as Participantes elaborem e mantenham atualizadas as políticas e
processos internos de monitoramento e resposta a transações suspeitas de
irregularidades no âmbito de fraudes e PLD/FT em observância à regulamentação e à
legislação vigentes. As Participantes também deverão implementar controles internos
por meio de relatórios, indicadores, regras e parâmetros de monitoramento préestabelecidos por essas políticas, a fim de monitorar as transações efetuadas no OFB. O
monitoramento das transações deve ser construído conforme uma abordagem baseada
em riscos de cada Participante. Esse monitoramento deverá se basear principalmente no
perfil das transações efetuadas, com avaliação de parâmetros, inclusive, horário das
transações, valor, localização, finalidade da transação, histórico e perfil de utilização do
cliente. Caso se identifiquem irregularidades, a Participante poderá gerar alertas ou


14


Corporativo | Interno




interromper transações, a seu critério, observada a regulamentação e legislação
vigentes.


III. MITIGAÇÃO DE RISCOS


O monitoramento de fraude e a PLD/FT permitem a identificação e o tratamento de
transações suspeitas de irregularidade, fatores essenciais para a segurança,
confiabilidade e manutenção do OFB.


Ainda, esse monitoramento colabora com a manutenção de baixos índices de fraudes no
ecossistema do OFB, com potencial redução do nível de reclamações e insatisfações de
clientes. Mitiga também o risco de perdas financeiras para Participantes e clientes, em
decorrência da possibilidade de intervenção rápida para tratamento de transações
irregulares.


IV. EXPERIÊNCIA DO USUÁRIO


O monitoramento de transações melhora a experiência do cliente no que se refere à
segurança, à sustentabilidade e à confiabilidade do OFB, ao maximizar a prevenção a
fraudes e a PLD/FT.


Esse monitoramento pode gerar maior tempo de espera na aprovação da transação para
um pequeno percentual de transações que necessitem de análise mais aprofundada,
devido a uma suspeita de fraude ou lavagem de dinheiro e financiamento a terrorismo. De
todo modo, esse é um procedimento comum já aplicável a outros produtos e serviços no
mercado financeiro, com o qual os clientes já têm familiaridade.


**8.2.4 Modelos de** _**machine learning**_ **transacional – nível alto**


I. O QUE É?


O _Machine Learning_, ou aprendizado de máquina, é uma das principais aplicações
conhecidas no campo da inteligência artificial e se utiliza de um ou mais algoritmos
matemáticos para resolver problemas anteriormente estabelecidos. É altamente
aplicável ao processo de prevenção, detecção e investigação de fraudes e PLD/FT.


II. COMO FUNCIONA?


Os modelos de machine learning baseados em algoritmos matemáticos têm capacidade
de interpretar, avaliar e correlacionar diversos dados e eventos nas transações efetuadas,
de forma veloz, precisa e automatizada, e apoiarão significativamente a identificação de
eventuais desvios na utilização do OFB para aplicação de fraudes.


15


Corporativo | Interno




Recomenda-se que esses modelos sejam aplicados no processo transacional, a fim de
antever e detectar eventuais tentativas de fraudes e de atividades ilícitas.


III. MITIGAÇÃO DE RISCOS


O uso de modelos de _machine learning_ aumenta significativamente a capacidade de as
Participantes identificarem desvios comportamentais no padrão comum dos clientes e no
ecossistema do OFB.


Tal tecnologia, quando aplicada na prevenção a fraudes em transações financeiras ou não
financeiras, pode apoiar as Participantes na prevenção, detecção e remediação de um
maior número de fraudes em menor tempo e de forma automatizada, com redução do
falso-positivo na identificação de situações suspeitas.


Esses modelos minimizam a chance de sucesso do fraudador, uma vez que são capazes
de interpretar e processar grande quantidade de dados.


IV. EXPERIÊNCIA DO USUÁRIO


Não há impacto significativo perceptível na experiência dos usuários. Trata-se de uma
camada extra de segurança nas transações, normalmente aplicada antes ou em conjunto
do processo de autorização.


**8.3 Remediação**


**8.3.1 Operação Contínua e Integral (24x7x365) – nível alto**


I. O QUE É?


Trata-se de um serviço de atendimento e suporte ao cliente para tratamento das
demandas e de remediação com foco em fraudes ou suspeitas de fraude, com
disponibilidade de 24h por dia, todos os dias da semana e do ano. Essa operação pode ser
totalmente sistêmica, híbrida (sistêmica mais humana) ou totalmente humana.


II.COMO FUNCIONA?


Às Participantes, sugere-se manter um serviço de atendimento ao cliente seguindo os
padrões de atendimento da legislação vigente, com o objetivo de dar ao cliente o primeiro
atendimento e dar o suporte para eventuais queixas.


Recomenda-se que esse serviço de atendimento suporte processos decorrentes de
fraude confirmada ou casos de suspeita de fraudes, conforme reportados pelos clientes
e/ou por outras Participantes; quando necessário, as solicitações devem seguir para


16


Corporativo | Interno




tratativa interna das Participantes ou, se for o caso, a Participante poderá se valer da
resolução de disputas do OFB.


III. MITIGAÇÃO DE RISCOS


A disponibilização desse serviço de atendimento mitiga eventuais reclamações do
cliente, melhorando a experiência do cliente e colabora para identificação e mitigação
mais ágil de fraudes.


IV. EXPERIÊNCIA DO USUÁRIO


Os serviços de atendimento contribuem para que clientes sanem eventuais dúvidas sobre
transações, com suporte necessário nos casos de reporte de fraude ou de suspeitas de
fraudes no momento de sua constatação. Em sua experiência, é importante comunicar os
clientes para que tenham clareza da existência e do funcionamento desse serviço.


**8.3.2 Ressarcimento em confiança – nível alto**


I. O QUE É?


O processo de ressarcimento em confiança (crédito em confiança) é um procedimento
que depende da discricionariedade de cada participante do OFB e tem por objetivo
efetuar a restituição imediata ao cliente nos casos de transação não reconhecida
proveniente de uma ação de fraude. Caberá a cada instituição definir se implementará e
sua estratégia para aplicação.


II.COMO FUNCIONA?


A partir do início das operações via Open Finance, os usuários poderão relatar o não
reconhecimento de uma transação, iniciando um processo de contestação na instituição.


Em casos em que seja necessário reestabelecer imediatamente o saldo do cliente, poderá
haver o lançamento de crédito em confiança na conta do usuário, enquanto a análise do
caso está em andamento. Nessas situações, cada instituição deve estabelecer as
premissas para a aplicação do crédito em confiança, assumindo os riscos da decisão.


É necessário observar que, nos casos em que seja necessário realizar a reversão do
crédito em confiança, a conta deve possuir saldo suficiente.


III. MITIGAÇÃO DE RISCOS


O processo de ressarcimento em confiança viabiliza que as instituições regularizem a
conta de um usuário de forma ágil e evitando maiores atritos. Além disso, ele minimiza


17


Corporativo | Interno




possíveis ações judiciais, reclamações em mídias sociais e em órgãos regulados por
usuários que foram vítimas de ações de fraudadores.


IV. EXPERIÊNCIA DO USUÁRIO


Na percepção do usuário, entender que a instituição possui uma forma ágil de resolver e
devolver recursos traz maior confiança e colabora para que relacionamento se mantenha.
É importante que o cliente tenha clareza dos processos internos do ressarcimento em
confiança, quando aplicado.


**8.4 Repressão**


**8.4.1 Colaboração para derrubada de** _**Phishing**_ **entre os Participantes – nível alto**


I. O QUE É?


_Phishing_ é um termo originado do idioma inglês, relacionado a palavra fishing, que
significa pescaria.


Tal termo ilustra de forma clara uma técnica empregada por meios digitais para coleta e
obtenção de dados de pessoas físicas e jurídicas, incluindo senhas, credenciais e dados
pessoais que possam permitir a criação de uma identidade ou credencial falsa.


A melhor identificação do Phishing pode ser feita a partir do aumento da capacidade das
Participantes de monitorar, identificar e inutilizar os canais utilizados para a coleta e
utilização indevida dos dados na aplicação de fraudes e lavagem de dinheiro ou
financiamento ao terrorismo.


II.COMO FUNCIONA?


O objetivo da iniciativa é promover a cultura de monitoramento, pelas Participantes, de
canais utilizados por fraudadores para esta coleta indevida de dados.


Os fraudadores normalmente se aproveitam de desconhecimento ou falso vínculo de
confiança para obtenção desses dados.


Dessa forma, sugere-se a atuação em 3 frentes no combate e identificação do _Phishing:_


1. Monitoramento próprio: Cada Participante deve buscar monitorar sua própria marca e
seus canais de comunicação, buscando identificar, de forma mais célere, eventuais
canais usados para o Phishing, e manter canais de denúncias para reporte dessas
situações ou suspeitas. Ainda, deve divulgar e participar de campanhas de orientação a
clientes.


18


Corporativo | Interno




2. Monitoramento conjunto entre Participantes: As Participantes podem manter um canal
de comunicação para fiscalização conjunta de eventuais suspeitas de utilização da marca
de outras Participantes em ações de _Phishing_, visto que, muitas vezes, os fraudadores
utilizam-se de diversas marcas simultaneamente para maximizar seus resultados. Ainda,
podem manter grupos de discussão ativos, com periodicidade razoável, para troca de
melhores práticas no combate ao Phishing.


3. Monitoramento conjunto da marca Open Finance: contempla o monitoramento
vinculado à marca Open Finance e compreende o alerta e reporte de situações suspeitas
por todas as Participantes, somada à colaboração na averiguação e nas ações conjuntas e
efetivas para identificação e derrubada de Phishing que envolvam o Open Finance.


A estruturação da colaboração para averiguação, constatação, identificação e derrubada
de Phishing, pode ser feita por meio da utilização da ferramenta MISP ( _Malware_
_Information Sharing Platform_ ), já empregada no PIX, com criação, na ferramenta, de uma
instância para colaboração na identificação e derrubada de Phishing envolvendo Open
Finance.


Outra sugestão é a criação de uma nova categoria destinada ao Open Finance na
ferramenta e no fluxo adotado para o Pix, a fim de reportar, receber e dar a devida
tratativa, com acompanhamento do BCB.


III. MITIGAÇÃO DE RISCOS


A iniciativa mantém as Participantes atentas e reduz significativamente o risco de perdas
financeiras, pois impacta diretamente na obtenção indevida de dados pelo fraudador, o
que minimiza o potencial de aplicação de fraudes e protege os dados de clientes e a
credibilidade do OFB.


IV. EXPERIÊNCIA DO USUÁRIO


A iniciativa não tem impacto negativo na experiência do cliente, mas tem um caráter
preventivo, visando minimizar os meios disponíveis para obtenção indevida de dados por
meio de _Phishing._


19


Corporativo | Interno




# 9. Prevenção à lavagem de dinheiro

A implementação do OFB traz como premissa a não criação de nenhum novo arranjo de

pagamento ou nova dinâmica de transferência de recursos entre instituições, com

relação às atualmente existentes, o que mantém as transações do OFB sujeitas a

responsabilidades já existentes de PLD/FT.


Dessa forma, é recomendado que, para as transações executadas via OFB, as

Participantes, já reguladas pelo BCB, devem se manter aderentes aos requisitos e

diretrizes definidos na legislação e regulamentação em vigor para PLD/FT. Essa

regulamentação já fornece o respaldo mínimo necessário para uma atuação aderente das

Participantes no OFB quanto à PLD/FT, conforme políticas, procedimentos, controles

internos, avaliações internas de risco, registros e monitoramentos de operações

suspeitas, comunicações ao COAF.


A Circular do Banco Central que apresenta tais requisitos e diretrizes é ilustrada nas

subseções abaixo.


**9.1 Políticas, Procedimentos e Controles Internos das Participantes**


A Circular BCB nº 3.978, conforme em vigor, dispõe sobre a política, os procedimentos e
os controles internos a serem adotados pelas instituições autorizadas a funcionar pelo
BCB para assegurar a PLD/FT, levando em consideração o conceito da abordagem
baseada em risco.


20


Corporativo | Interno




A política de PLD/FT, devidamente documentada e aprovada pelo Conselho de
Administração ou pela Diretoria, conforme o caso, deve ser mantida atualizada e
compatível com os perfis de risco dos clientes, das Participantes, das operações, dos
produtos e serviços e dos empregados, parceiros e prestadores de serviços
terceirizados, com o comprometimento da alta Administração da Participante com a
efetividade e a melhoria contínua da política, dos procedimentos e dos controles internos
relacionados com a PLD/FT. Esses são elementos essenciais para a mitigação de riscos
aos quais as Participantes estão expostas.


Essa política deve ser formulada com base em princípios e diretrizes de PLD/FT e

recomenda-se que contenha, no mínimo:


i. a definição de papéis e responsabilidades para o cumprimento das obrigações de

que trata a Circular BCB nº 3.978;

ii. a definição de procedimentos voltados à avaliação e à análise prévia de novos

produtos e serviços, bem como da utilização de novas tecnologias;

iii. a avaliação interna de risco e a avaliação de efetividade;

iv. a verificação do cumprimento da política, dos procedimentos e dos controles

internos, bem como a identificação e a correção das deficiências verificadas;

v. a promoção de cultura organizacional de prevenção à lavagem de dinheiro e ao

financiamento do terrorismo, contemplando, inclusive, os funcionários, os

parceiros e os prestadores de serviços terceirizados;


vi. a seleção e a contratação de empregados, parceiros e de prestadores de serviços

terceirizados;

vii. a capacitação dos empregados sobre o tema da PLD/FT, incluindo os empregados

dos correspondentes no País que prestem atendimento em nome das

Participantes, sempre compatível com as atividades por ele exercidas;

viii. a coleta, verificação, validação e atualização de informações cadastrais, visando a

conhecer os clientes, os funcionários, os parceiros e os prestadores de serviços

terceirizados;

ix.          - registro de operações e de serviços financeiros;


x.          - monitoramento, seleção e análise de operações e situações suspeitas; e

xi. A comunicação de operações ao COAF.


21


Corporativo | Interno




Recomenda-se que as Participantes implementem uma estrutura de governança
compatível com o porte, volume e complexidade das suas operações, com indicação de
um diretor responsável pela PLD/FT, e instituir, ainda, mecanismos de acompanhamento
e de controle de modo a assegurar a implementação e a adequação dessa política, dos
procedimentos e dos controles internos adequados PLD/FT, de acordo com a legislação e
regulamentação aplicáveis.


**9.2 Avaliação interna de risco (“AIR”)**


Recomenda-se que as Participantes realizem AIR com adoção da abordagem baseada em

risco; ou seja, com aplicação de medidas e controles proporcionais ao risco e a alocação

de esforços de maneira mais eficiente. O objetivo é identificar e mensurar o risco de

utilização de seus produtos e serviços nas práticas de lavagem de dinheiro e

financiamento do terrorismo.


O risco deve ser avaliado quanto à sua probabilidade de ocorrência e à magnitude dos

efeitos financeiro, jurídico, reputacional e socioambiental para as Participantes.


Recomenda-se que essa AIR considere, no mínimo, os perfis de risco de:


i. clientes;

ii. Participantes, inclusive o modelo de negócio e a área geográfica de atuação;

iii. operações, transações, produtos e serviços, abrangendo todos os canais de

distribuição e a utilização de novas tecnologias; e

iv. atividades exercidas pelos empregados, empregados de correspondentes,

parceiros e prestadores de serviços terceirizados.


Recomenda-se definir categorias de risco e adotados os respectivos controles de

gerenciamento e de mitigação, reforçados para as situações de maior risco e

simplificados nas situações de menor risco. Além disso, devem ser utilizadas, quando

disponíveis, avaliações realizadas por entidades públicas do país relativas à PLD/FT, por

exemplo, a Avaliação Setorial de Riscos e a Avaliação Nacional de Riscos.


Recomenda-se que a AIR seja formalizada e aprovada, com revisão periódica ou

alterações significativas em perfis de risco pré-definidos, pelo diretor responsável pela

PLD/FT, bem como encaminhada internamente para ciência de comitês de risco e de


22


Corporativo | Interno




auditoria, conforme aplicável, e para o Conselho de Administração e/ou Diretoria das

Participantes.


**9.3 KYC (know your customer)**


As Participantes devem implementar procedimentos destinados a conhecer seus

clientes, formalizados em manual específico aprovado e atualizado pela diretoria das

Participantes, de acordo com a legislação e regulamentação vigentes.


Recomenda-se que os procedimentos contemplem, inclusive:


i. Identificação dos clientes;

ii. Qualificação dos clientes, inclusive qualificação como PEP (Pessoa Exposta

Politicamente); e

iii. Classificação dos clientes.


Recomenda-se que os procedimentos de identificação permitam verificar e validar a

identidade do cliente, incluir a obtenção, a verificação e a validação da autenticidade de

informações de identificação, inclusive mediante confrontação de informações com

aquelas disponíveis em bancos de dados e a manutenção de informações atualizadas.


A qualificação de clientes verifica-se por meio da coleta, verificação e validação de

informações, inclusive a avaliação da capacidade financeira do cliente e verificação e

validação de acordo com o perfil de risco do cliente e com a natureza da relação de

negócio, além de coleta de informações adicionais compatíveis com o risco de utilização

de produtos e serviços, a verificação da condição de PEP, de seu representante, familiar

ou estreito colaborador.


Recomenda-se que os procedimentos de qualificação sejam compatíveis com o perfil de

risco do cliente, contemplando medidas reforçadas para clientes classificados em

categorias de maior risco, de acordo com a avaliação interna de risco referida e com a

política de PLD/FT, e com a natureza da relação de negócio, bem como prever a análise da

cadeia de participação societária até a identificação da pessoa natural caracterizada

como seu beneficiário final, no caso de pessoa jurídica.


23


Corporativo | Interno




I. Registro de Operações


Recomenda-se que as Participantes possuam infraestrutura e procedimentos adequados

de forma a manter registro de todas as operações realizadas e produtos e serviços

contratados, inclusive saques, depósitos, aportes, pagamentos, recebimentos e

transferência de recursos, a fim de possibilitar a identificação da origem e o destino de

recursos, seus remetentes e destinatários.


Recomenda-se que os registros sejam segmentados em:


i. Registro de operações de pagamento, recebimento e transferência de recursos

independentemente do valor ou espécie de produto ou valor;

ii. Registro de operações em espécie: operações com utilização de recursos em

espécie de valor individual superior a R$2.000,00 (dois mil reais) e operações de

depósito ou aporte em espécie de valor individual igual ou superior a R$50.000,00

(cinquenta mil reais).


**9.4 Monitoramento, Seleção, Análise e Comunicação (MASC)**


Recomenda-se que os participantes implementem procedimentos de monitoramento,

seleção, análise e comunicação de operações e situações, conforme parâmetros, regras e

cenários descritos em manual específico, aprovado pela Diretoria das Participantes, com

       - objetivo de identificar suspeitas de lavagem de dinheiro e do financiamento do

terrorismo, compatíveis com políticas de PLD/FT e com as Avaliações Internas de Risco

(AIR).


Recomenda-se que os procedimentos contemplem:


i. Monitoramento e seleção de operações e situações suspeitas: as operações

realizadas e os produtos e serviços contratados que considerem as partes

envolvidas, os valores, as formas de realização, os instrumentos utilizados ou a

falta de fundamento econômico ou legal e possam configurar indícios de lavagem

de dinheiro ou de financiamento do terrorismo;


24


Corporativo | Interno




ii. Análise de operações e situações suspeitas selecionadas por meio dos

procedimentos de monitoramento e seleção, com o objetivo de caracterizá-las ou

não como suspeitas de lavagem de dinheiro ou financiamento do terrorismo.


Recomenda-se que essa análise seja formalizada pelas Participantes em um dossiê,

independentemente da comunicação ao COAF, com procedimentos prévios e de apoio na

análise, inclusas consultas a bases de dados, serviços tecnológicos e de inteligência

artificial, algoritmos, etc.


**9.5 Comunicação ao COAF**


Recomenda-se que as Participantes comuniquem ao COAF as operações ou situações

suspeitas de lavagem de dinheiro e de financiamento do terrorismo, de acordo com a

legislação e regulamentação aplicáveis, sem dar ciência aos envolvidos ou a terceiros

( _tipping-off_ ).


Recomenda-se que essas comunicações sejam feitas de forma clara, consistente e

detalhada, com razões fundamentadas para tanto, por meio do Sistema de Controle de

Atividades Financeiras (SISCOAF), do COAF.


A tomada de decisão de comunicação não pode exceder o prazo de quarenta e cinco dias,

contados a partir da data da seleção da operação ou situação e a comunicação deverá ser

feita até o dia útil seguinte da decisão da comunicação (cf. art. 43, § 1° c/c art. 48, § 2° da

Circular 3.978).


**9.6 Procedimentos destinados a conhecer empregados, parceiros e prestadores de**

**serviços terceirizados (Know your Partner e Know your Supplier)**


Recomenda-se que as Participantes implementem procedimentos destinados a conhecer

seus empregados, parceiros e prestadores de serviços terceirizados, que prestem

serviços de atendimento em seu nome, inclusive procedimentos e controles internos

relacionados à PLD/FT.


Recomenda-se que estes procedimentos contemplem a identificação e a qualificação

dos empregados, parceiros de negócio e prestadores de serviço terceirizados. Além


25


Corporativo | Interno




disso, devem prever a classificação das atividades por eles exercidas em categorias de

risco definidas na AIR.


Recomenda-se que os procedimentos sejam compatíveis com a política de PLD/FT e com

a avaliação interna de risco. As informações relativas aos empregados, parceiros e

prestadores de serviços terceirizados devem ser mantidas atualizadas, considerando,

inclusive, eventuais alterações que impliquem mudança de classificação nas categorias

de risco.


**9.7 Acompanhamento e controle**


Recomenda-se que as Participantes instituam mecanismos de acompanhamento e de

controle de modo a assegurar a implementação e a adequação da política, dos

procedimentos e dos controles internos relacionados à PLD/FT, submetidos a testes

periódicos pela auditoria interna, quando aplicáveis, compatíveis com os procedimentos

e controles internos das Participantes.


**9.8 Avaliação de efetividade**


Recomenda-se que as Participantes avaliem anualmente a efetividade da política, dos

procedimentos e dos controles internos relativos à PLD/FT, em relatório especial,

inclusos, no mínimo:


i. procedimentos destinados a conhecer clientes (KYC), inclusive a verificação e a

validação das informações dos clientes e a adequação dos dados cadastrais;

ii. procedimentos de monitoramento, seleção, análise e comunicação ao Coaf,

incluindo a avaliação de efetividade dos parâmetros de seleção de operações e de

situações suspeitas;

iii. governança da política de PLD/FT;

iv. medidas de desenvolvimento da cultura organizacional voltadas à prevenção da

lavagem de dinheiro e ao financiamento do terrorismo;

v. programas de capacitação periódica de pessoal;

vi. procedimentos destinados a conhecer os funcionários, parceiros e prestadores

de serviços terceirizados; e


26


Corporativo | Interno




vii. ações de regularização dos apontamentos oriundos da auditoria interna e da

supervisão do BCB.


Recomenda-se que o relatório da avaliação de efetividade descreva a forma como foi

realizada a avaliação efetiva, os testes aplicados e os resultados obtidos e sirvam de base

para elaboração de um plano de ação destinado a solucionar as deficiências identificadas

por meio da avaliação de efetividade, de modo a buscar o constante aperfeiçoamento das

práticas relativas à PLD/FT.


27


Corporativo | Interno


