Informe #30 — 30 de julho de 2021


Buscando padronizar o retorno do status de consentimento da Fase 2, fica definido que serão
aceitos dois status _code_ para consentimento revogado: status _code_ 404 ou 200.


- Instituições que implementaram com status _code_ 404 terão testes aprovados no motor de
conformidade automaticamente


- Instituições que implementaram com status _code_ 200 receberão este erro no motor de conformidade. Porém, orientamos que continuem com o processo de certificação, e indiquem que
houve este erro no pedido de certificação Para essas, solicitamos também que informem à
Estrutura de Governança através do e-mail abaixo para que possamos mapear a necessidade de revisão do teste na sua certificação.


Essa orientação será adicionada à seção de Problemas conhecidos das Especificações da Fase 2
do Portal na próxima semana.


**[ENVIE UM E-MAIL PARA ADMINISTRATIVO@OPENBANKINGBR.ORG](mailto:administrativo@openbankingbr.org?subject=Fase%202%20-%20Retorno%20do%20status%20de%20consentimento)**


**[ACESSE A SEÇÃO PROBLEMAS CONHECIDOS](https://openbanking-brasil.github.io/areadesenvolvedor/#problemas-conhecidos-da-especificacao)**


Informamos que foi identificado na API da Fase 2 de Dados Cadastrais Pessoa Jurídica uma
inconsistência na expressão regular do campo _code_ do EconomicActivity. Portanto, para passar na
certificação da identificação de pessoa jurídica, é preciso utilizar uma massa de dados onde o
CNAE do cliente não se inicie com zero, ou seja, possua 7 dígitos numéricos.


Para os casos em que a instituição não possua o CNAE do cliente, orientamos que as Instituições
utilizem o valor 9999999, uma vez que não é possível compartilhar “NA” pois o campo é do tipo
numérico.


Essa orientação será adicionada à seção de Problemas conhecidos das Especificações da Fase 2
do Portal na próxima semana.


**[ACESSE AS APIs FASE 2](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-2-apis-do-open-banking-brasil)**


**[ACESSE A SEÇÃO PROBLEMAS CONHECIDOS](https://openbanking-brasil.github.io/areadesenvolvedor/#problemas-conhecidos-da-especificacao)**


Foi identificada ambiguidade na documentação relacionada à validade do access token e refresh
token da API Fase 3: a informação do campo description sobre o período do access token está incoerente com a especificação de segurança.


As instituições devem considerar o seguinte texto para o campo description do expirationDateTime
do schema ResponsePaymentConsentData:


Data e hora em que o consentimento da iniciação de pagamento expira, devendo ser sempre o creationDateTime mais 5 minutos. Uma string com data e hora conforme especificação RFC-3339, sempre com a utilização de timezone UTC (UTC time format). O consentimento é criado com o status AWAITING_AUTHORISATION, e deve assumir o status AUTHORIZED ou REJECTED antes do tempo de expiração - 5 minutos. Caso o tempo seja
expirado, o status deve assumir REJECTED. Para o cenário em que o status assumiu AUTHORISED, o tempo máximo do expirationDateTime do consentimento deve assumir "now
+ 60 minutos". Este é o tempo para consumir o consentimento autorizado, mudando seu
status para CONSUMED. Não é possível prorrogar este tempo e a criação de um novo consentimento será necessária para os cenários de insucesso.


Esse ajuste será atualizado no swagger na segunda-feira (02/08).


**[ACESSE A API FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


Foi realizado o seguinte ajuste na Área do Desenvolvedor para a Fase 3:


- Remoção do header x-jws-signature da tabela de parâmetros que especifica os headers da
API Fase 3.


Este ajuste não traz modificações no Swagger e o torna coerente com a tabela.


**[ACESSE A API FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


Conforme o Informe #29, foi realizado uma atualização Patch para as APIs da Fase 1 hoje. A atualização contempla:


- Retorno dos itens do menu Schemas em ordem alfabética


- Definição de quantidade máxima de itens para a lista de services em sharedAutomatedTellerMachines


- Remoção do atributo de e-mail nos Swaggers, deixando apenas a URL para contato do
Service Desk


- Atualização da descrição do item AverageMetrics no Swagger, afirmando a unidade do
campo em milissegundos


Estes ajustes foram disponibilizados nesta sexta-feira (30/07), colocando o portal na versão v1.0.0rc8.1 e as APIs Fase 1 na versão v1.0.2.

Para mais detalhes, verifique o changelog na Área do Desenvolvedor.


**[ACESSE AS APIs FASE 1](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-1-apis-do-open-banking-brasil)**


Com o intuito de auxiliar as Instituições Financeiras a utilizarem o Model Bank,
foi disponibilizada no canal oficial do Open Banking no Youtube uma série de vídeos tutoriais sobre
a sua utilização:


1) Walkthrough - Create Software Statement


2) Walkthrough - Create Transport Cert


3) Walkthrough - Dynamic Client Registration


Os vídeos, desenvolvidos em conjunto com fornecedores, são sessões guiadas em inglês no Model
Bank. Informamos que, futuramente, também será disponibilizado um tutorial em português para as
Instituições Financeiras.


Em caso de dúvidas, acesse a plataforma do Service Desk por meio de login ou como convidado.


**[ACESSE OS VÍDEOS NO YOUTUBE](https://www.youtube.com/watch?v=03R2jtrZPuU&list=PLB4KVrA_iiEHiTHd0ZGLcPUkEuslABfdJ)**


Foi disponibilizado em 15/07, a nova versão do Portal Open Banking. Seguindo as diretrizes das
[Instrução Normativa n°133, o site conta com três áreas:](data/references/Instrução_Normativa_BCB_133.md)


- Área do Cidadão


- Área do Participante


- Área do Desenvolvedor


O objetivo do Portal é organizar e transmitir informações específicas e úteis aos diversos stakeholders do ecossistema Open Banking, em um ambiente seguro para navegação.


**[ACESSE O PORTAL OPEN BANKING](https://openbankingbrasil.org.br/)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


