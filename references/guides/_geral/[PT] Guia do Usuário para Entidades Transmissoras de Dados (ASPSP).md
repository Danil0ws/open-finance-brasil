# [PT] Guia do Usuário para Entidades Transmissoras de Dados (ASPSP)

ASPSP - _Account Servicing Payment Service Provider_

## 1\. Registrando um Banco

### 1.1. Visão Geral do Diretório

Os serviços do framework de confiança providos pelo Open Finance Brasil fornecem todos os serviços de descoberta necessários para que instituiçoes transmissores e receptoras interajam entre si, sem que seja preciso validar individualmente a autenticidade de cada participante.

Um _Authorization Server_ ou AS, conforme definido por [RFC 6749 - The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749), executa várias funções em um ecossistema de compartilhamento de dados como o Open Finance Brasil. Antes de prosseguir, certifique-se de que os conceitos de funções e responsabilidades definidos na RFC original sejam bem compreendidos. Além disso, certifique-se de que os conceitos, funções e responsabilidades definidos no [OpenID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html) e como eles estendem os conceitos definidos no RFC 6749 são igualmente bem compreendidos.

### 1.2. Registrando um Authorization Server e OpenID Provider

Os bancos, geralmente grandes bancos, não serão uma entidade única do ponto de vista das operações de tecnologia. Eles podem ter marcas, segurança e infraestrutura de TI diferentes para diferentes segmentos de clientes, ou podem ter alguma infraestrutura de TI que ofereça suporte a várias marcas ou segmentos de clientes. Isso significa que o ecossistema técnico precisa ser flexível o suficiente para suportar uma ampla variedade de implantações de infraestrutura de bancos, garantindo que os serviços necessários possam ser descobertos por clientes de instituições receptoras que precisam interagir com ele.

Um modelo flexível para anunciar serviços de autenticação / autorização e os recursos protegidos pelo AuthN e AuthZ é suportado pelo Diretório.

-   **Customer Friendly Name** - Será exibido aos clientes pelas instituições receptoras, e já deve ser reconhecido pelos clientes do banco.
    
-   **Customer Friendly Logo** - Será exibido aos clientes pelas instituições receptoras para auxiliar no reconhecimento da marca.
    
-   **Description** - Isso pode ser exibido aos clientes pelas instituições receptoras para auxiliar no reconhecimento da marca.
    
-   **Terms of Service** - Este é um link para os Termos de Serviço do banco, que podem ser incluídos pelas instituições receptoras.
    
-   **Notification WebHook** - _Authorization Servers_ podem registrar um WebHook que receberá atualizações por push sobre as alterações dos participantes, seus softwares ou certificados.
    
-   **OpenID Well Known Document Uri** - Link para o documento de descoberta do Authorization Server.
    

Um banco pode optar por ter um _Authorization Server_ ou muitos, desde que satisfaça os seguintes requisitos.

-   Um cliente pode reconhecer o _Authorization Server_ como um local com o qual normalmente faria interação com o seu banco.
    
-   O _Authorization Server_ pode emitir tokens para os recursos e serviços que um cliente ou insituição receptora está procurando.
    
-   O _Authorization Server_ das instituições transmissoras/detentoras de contas que atenda mais de uma marca deve aceitar mais de um cadastro (criação de client\_ids) para um mesmo _software statement_. Caso a solução de _Authorization Server_ não suporte este comportamento, deverá ser adequado para suportar múltiplas marcas e o cadastramento das marcas no diretório deverá sofrer apontamento de acordo com cada marca.
    

### 1.3. Registrando Recursos

Depois que um banco registra um _Authorization Server_, ele precisa anunciar para quais recursos, APIs ou serviços ele pode fornecer autorização.

\[Authorization Resources management image\]

Auth Id

Auth Customer Friendly Name

Well Known

Resource

Version

1

Amazing Business Banking

[https://auth.business.amazingbank.org.br/.well-known/openid-configuration](https://auth.business.amazingbank.org.br/.well-known/openid-configuration)

consents

1

1

Amazing Business Banking

[https://auth.business.amazingbank.org.br/.well-known/openid-configuration](https://auth.business.amazingbank.org.br/.well-known/openid-configuration)

business account information

1

1

Amazing Business Banking

[https://auth.business.amazingbank.org.br/.well-known/openid-configuration](https://auth.business.amazingbank.org.br/.well-known/openid-configuration)

payments

1

2

Amazing Banking

[https://auth.amazingbank.org.br/.well-known/openid-configuration](https://auth.amazingbank.org.br/.well-known/openid-configuration)

consents

1

2

Amazing Banking

[https://auth.amazingbank.org.br/.well-known/openid-configuration](https://auth.amazingbank.org.br/.well-known/openid-configuration)

account information

1

2

Amazing Banking

[https://auth.amazingbank.org.br/.well-known/openid-configuration](https://auth.amazingbank.org.br/.well-known/openid-configuration)

account information

2

3

Amazing Banking

[https://auth.payments.amazingbank.org.br/.well-known/openid-configuration](https://auth.payments.amazingbank.org.br/.well-known/openid-configuration)

payments consents

1

3

Amazing Banking

[https://auth.payments.amazingbank.org.br/.well-known/openid-configuration](https://auth.payments.amazingbank.org.br/.well-known/openid-configuration)

payments

1

No exemplo acima, o Amazing Banking está anunciando dois serviços que devem ser reconhecidos pelos clientes. “Amazing Business Banking” e “Amazing Banking”. Estes **podem ou não estar** diretamente relacionados a “Marcas”, pois bancos diferentes podem precisar anunciar serviços de autenticação diferentes, mesmo dentro de uma submarca.

Além disso, o banco anuncia quais recursos cada um dos servidores de autorização está protegendo ou oferecendo. No exemplo acima, o Amazing Banking é compatível com a versão 1 e a versão 2 da API de informações da conta, e o “Amazing Banking” tem dois sistemas separados de autenticação e autorização para Pagamentos e Informações da conta.

Anunciar corretamente quais recursos são oferecidos por cada servidor é importante para atingir a escala prevista pelo Open Finance Brasil, além de ser fundamental para garantir que os clientes possam identificar seu serviço bancário facilmente e que as instituições receptoras possam encaminhar os clientes para o _Authorization Server_ correto com base nos recursos protegidos por cada serviço.

## 2\. Validando uma Solicitação de Registro de Cliente

Usando o OpenID Connect Discovery e a especificação de Dynamic Client Registration (DCR) do Open Finance Brasil. Uma instituição receptora pode registrar seu aplicativo em cada um dos _Authorization Servers_ disponíveis no ecossistema.

### 2.1. Registro OpenID Connect e OAuth 2.0 Dynamic Client Registration

Consulte a Especificação de Dynamic Client Registration (DCR) do Open Finance Brasil para obter mais detalhes:

[https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251331/PT+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3#Provisionamentos-do-OpenID-Connect-Discovery-do-Open-Finance-Brasil](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251331/PT+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3#Provisionamentos-do-OpenID-Connect-Discovery-do-Open-Finance-Brasil) .

### 2.2. Processamento de declaração de software (Software Statement Assertion)

Consulte a Especificação de Dynamic Client Registration (DCR) do Open Finance Brasil para obter mais detalhes:

[https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251331/PT+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3#Declara%C3%A7%C3%A3o-de-Software](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251331/PT+Open+Finance+Brasil+Financial-grade+API+Dynamic+Client+Registration+1.0+Implementers+Draft+3#Declara%C3%A7%C3%A3o-de-Software)

## 3\. Validando um Pedido de Autorização

Consulte o Perfil de Segurança do Open Finance Brasil (Financial-grade API Security Profile) para obter mais detalhes:

[https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251182/PT+Open+Finance+Brasil+Financial-grade+API+Security+Profile+1.0+Implementers+Draft+3#Profile-de-Seguran%C3%A7a-para-o-Open-Finance-Brasil](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/76251182/PT+Open+Finance+Brasil+Financial-grade+API+Security+Profile+1.0+Implementers+Draft+3#Profile-de-Seguran%C3%A7a-para-o-Open-Finance-Brasil)
