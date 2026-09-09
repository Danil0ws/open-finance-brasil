# CIBA-BR v2.0.0 - Open Finance Brasil Client Initiated Backchannel Authentication

true

# Introdução

O CIBA (Client Initiated Backchannel Authentication) é um protocolo de autenticação desacoplado em que Instituições Iniciadoras de Pagamento ou Receptoras de Dados recebem consentimentos dos usuários SEM realizar o fluxo FAPI Hybrid Flow (redirecionamento) em todas as interações.

Existem diversas formas para realizar esse fluxo e algumas delas estão listadas abaixo:

**Opção 1:**

O usuário é redirecionado via fluxo FAPI Hybrid Flow apenas uma única vez, onde o CIBA é ativado e por consequência os próximos pedidos de autorização serão por meio de um canal secundário - o backchannel - em que as Instituições Iniciadoras de Pagamento ou Receptoras de Dados se comunicam com o Servidor de Autorização da Instituição Detentora da Conta ou Transmissora de Dados para receber a autorização o consentimento do usuário.

O uso do FAPI Hybrid Flow para o vínculo inicial dessa opção 1 foi escolhido porque já é um processo conhecido pelo usuário e permite uma identificação via id\_token em que os Servidores de Autorização já implementam nas Instituições Detentoras de Conta ou Transmissora de Dados.

Após o vínculo, nos próximos pedidos de consentimento, o usuário receberá um push notification, SMS, mensagem via WhatsApp, etc como canal de redirecionamento para o aceite do consentimento.

**Opção 2:**

O usuário **não** é redirecionado via fluxo FAPI Hybrid Flow e as informações do próprio consentimento são utilizadas para iniciar uma autorização por meio de um canal secundário - o backchannel - em que as Instituições Iniciadoras de Pagamento ou Receptoras de Dados se comunicam com o Servidor de Autorização da Instituição Detentora da Conta ou Transmissora de Dados para receber a autorização do consentimento do usuário.

Não existe vínculo, e nesse primeiro pedido de autorização de consentimento, o usuário receberá um push notification, SMS, mensagem via WhatsApp, etc como canal de redirecionamento para o aceite do consentimento.

Ao habilitar o fluxo CIBA os participantes devem implementar algumas diretrizes:

1.  O id\_token é único e representa um cliente e conta;
    
2.  O tempo de aceite do consentimento sobre o pedido de Autorização recebido via CIBA deverá se manter o mesmo definido para o fluxo via Hybrid Flow, respeitando as configurações do produto utilizado. 
    
3.  O payload de pagamento deve conter identificação que foi realizado via CIBA ou FAPI Hybrid Flow.
    

O fluxo CIBA está descrito em quatro documentos técnicos que se complementam mutuamente, e fazem referências a outras especificações. Recomenda-se a consulta na seguinte ordem:

-    [OpenID Connect Client-Initiated Backchannel Authentication Flow - Core 1.0](https://openid.net/specs/openid-client-initiated-backchannel-authentication-core-1_0.html)
    

o   Esta é a principal especificação do fluxo CIBA divulgada pela OpenID Foundation, contendo detalhes de implementação, requisitos e recomendações, e referências a outras especificações basais.

-   [Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3](data/references/guides/PT.md)  
    

o   Este é o perfil de regras e recomendações de autenticação e segurança proposto pelo GT de Segurança do Open Finance Brasil.

-   [Draft-02: Financial-grade API: Client Initiated Backchannel Authentication Profile](https://openid.net/specs/openid-financial-api-ciba-ID1.html)
    

o   Este é o perfil de regras e recomendações de autenticação e segurança proposto pela OpenID Foundation para implementações genéricas do fluxo CIBA.

-   Open Banking Brasil Financial-grade CIBA API Security Profile 1.0 Implementers Draft 3  
    

o   Este é o perfil de regras e recomendações de autenticação e segurança proposto pela Squad CIBA do Open Finance Brasil para implementação do fluxo CIBA para Iniciação de Pagamentos no cenário brasileiro.

O protocolo CIBA é abrangente e permite diversos casos de uso. Nas próximas seções estão definidas as opções permitidas e seus detalhes. 

**\[EN\] \[SV\] CIBA – Decoupled Flow**

**Introduction**

CIBA (Client-Initiated Backchannel Authentication) is a decoupled authentication protocol where Payment Initiators or Data Receivers obtain user consent **without** performing the FAPI Hybrid Flow (redirection) for every interaction.

There are several ways to implement this flow, and some of them are listed below:

**Option 1:**  
 The user is redirected via the FAPI Hybrid Flow only once, during which CIBA is activated. As a result, subsequent authorization requests will occur through a secondary channel—the backchannel—where Payment Initiators or Data Receivers communicate with the Authorization Server of the Account Holding or Data Transmitting Institution to receive user consent.

The use of FAPI Hybrid Flow for the initial linkage in this option was chosen because it is already a familiar process for users and allows identification via an id\_token implemented by the Authorization Servers of Account Holding or Data Transmitting Institutions.

After the linkage, subsequent consent requests will notify the user through push notifications, SMS, WhatsApp messages, etc., as the redirection channel for consent approval.

**Option 2:**  
 The user is **not** redirected via the FAPI Hybrid Flow. Instead, the consent information itself is used to initiate authorization via a secondary channel—the backchannel—where Payment Initiators or Data Receivers communicate with the Authorization Server of the Account Holding or Data Transmitting Institution to obtain user consent.

In this scenario, there is no linkage, and during the first authorization request, the user will receive notifications through push notifications, SMS, WhatsApp messages, etc., as the redirection channel for consent approval.

**Requirements for Enabling the CIBA Flow:**

Participants must implement the following guidelines:

1.  The id\_token must be unique and represent both a client and an account.
    
2.  The consent acceptance time for the authorization request via CIBA must remain the same as that defined for the Hybrid Flow, respecting the configurations of the utilized product.
    
3.  The payment payload must indicate whether it was processed via CIBA or FAPI Hybrid Flow.
    

The CIBA flow is outlined in four mutually complementary technical documents, which reference additional specifications. The recommended reading order is as follows:

-   [OpenID Connect Client-Initiated Backchannel Authentication Flow - Core 1.0](https://openid.net/specs/openid-client-initiated-backchannel-authentication-core-1_0.html)
    

o   This is the primary specification for the CIBA flow published by the OpenID Foundation, containing implementation details, requirements, recommendations, and references to foundational specifications.          

-   [Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3](data/references/guides/PT.md)  
    

o   This profile provides authentication and security rules and recommendations proposed by the Open Finance Brasil Security Working Group.

-   [Draft-02: Financial-grade API: Client Initiated Backchannel Authentication Profile](https://openid.net/specs/openid-financial-api-ciba-ID1.html)
    

o   This profile outlines authentication and security rules and recommendations proposed by the OpenID Foundation for generic CIBA flow implementations.

-   Open Banking Brasil Financial-grade CIBA API Security Profile 1.0 Implementers Draft 3  
    

o   This profile provides authentication and security rules and recommendations proposed by the Open Finance Brasil CIBA Squad for implementing the CIBA flow for Payment Initiation in the Brazilian scenario.

The CIBA protocol is comprehensive and supports various use cases. The next sections define the permitted options and their details.
