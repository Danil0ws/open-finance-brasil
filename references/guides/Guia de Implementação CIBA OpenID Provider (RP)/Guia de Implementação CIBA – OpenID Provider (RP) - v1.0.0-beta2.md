# Guia de Implementação CIBA – OpenID Provider (RP) - v1.0.0-beta2

12falsenonelisttrue

# 1\. Introdução

## 1.1. Objetivo

Este documento tem por objetivo consolidar orientações práticas de implementação do protocolo **Client Initiated Backchannel Authentication (CIBA)** no perfil brasileiro (**CIBA-BR**) para instituições participantes do **Open Finance Brasil** que atuam como **Relying Party (RP)** – isto é, receptoras de dados e iniciadoras de transação de pagamento.

O público-alvo são instituições que **já possuem aplicações cliente certificadas em conformidade com OFB-FAPI-BR** e desejam habilitar o fluxo de autenticação desacoplada (backchannel) definido em CIBA, mantendo total aderência ao perfil de segurança financeiro exigido pelo ecossistema brasileiro.

## 1.2. Escopo

Este documento concentra-se exclusivamente nos aspectos técnicos e normativos adicionados ou modificados pela adoção de CIBA em relação a uma implementação OFB-FAPI-BR já certificada. Não são repetidos requisitos gerais de FAPI ou de segurança do Open Finance Brasil já contemplados em outras especificações e guias do ecossistema.

## 1.3. Premissas

-   O RP já implementou e certificou sua aplicação cliente conforme OFB-FAPI-BR (incluindo autenticação de cliente via private\_key\_jwt, uso de mTLS com certificados BRCAC, Dynamic Client Registration – DCR/DCM, descoberta de Authorization Servers, e demais requisitos de segurança).
    
-   O RP conhece e aplica as práticas de governança do **Diretório de Participantes** do Open Finance Brasil (obtenção e uso de Software Statement Assertion – SSA, gestão de certificados, etc.).
    
-   O RP está familiarizado com os conceitos de **consentimento explícito** e **autorização do usuário** no contexto do Open Finance Brasil.
    

## 1.4. Modalidade CIBA adotada

O perfil brasileiro (CIBA-BR) define como padrão único o modo PING para entrega de notificações ao Relying Party (RP). Este guia reflete essa decisão, cobrindo o modo PING e o uso de polling apenas como mecanismo de fallback em cenários de exceção onde o RP não consegue receber a notificação PING.

## 1.5. Relação com as especificações oficiais

Este documento **não substitui e não modifica** as especificações técnicas oficiais:

-   **CIBA-BR** (Open Finance Brasil Client Initiated Backchannel Authentication Profile)
    
-   **CIBA-Core** (OpenID Connect Client-Initiated Backchannel Authentication Core)
    
-   **FAPI-CIBA** (Financial-grade API CIBA Profile)
    
-   **OFB-FAPI-BR** (Open Finance Brasil Financial-grade API Security Profile)
    

Em caso de dúvida ou divergência, **prevalecem sempre as especificações oficiais** publicadas pelo Open Finance Brasil e pelos grupos de trabalho OpenID Foundation e IETF. Este guia visa apenas facilitar a compreensão e a aplicação prática dessas especificações no contexto do ecossistema brasileiro.

# 2\. Discovery (well-known)

A etapa de Discovery é o ponto de partida para que o Relying Party (RP) descubra as capacidades de um Authorization Server (OP). No contexto do CIBA-BR, parte-se do pressuposto de que o RP já consome discovery e opera fluxos OFB-FAPI-BR de forma plena (incluindo descoberta de endpoints, validação de metadados e seleção de algoritmos). Assim, o objetivo deste capítulo é destacar apenas os elementos adicionais que o RP deve extrair e validar no documento de descoberta do OP para determinar se aquele Authorization Server suporta o fluxo CIBA, qual é o endpoint de backchannel authentication, se o modo de entrega é PING conforme exigido pelo perfil brasileiro, e quais algoritmos e parâmetros são suportados para este fluxo.

Padrões de referência:

-   OpenID Connect Discovery 1.0
    
-   OAuth 2.0 Authorization Server Metadata (RFC 8414)
    
-   OpenID Connect Client‑Initiated Backchannel Authentication (CIBA-Core)
    
-   FAPI-CIBA (perfil financeiro para CIBA)
    
-   CIBA-BR (perfil brasileiro para CIBA no Open Finance Brasil)
    

## 2.1. Endpoints

Em relação ao discovery já exigido por OFB‑FAPI‑BR, CIBA introduz essencialmente um novo endpoint a ser publicado no documento de metadados do Authorization Server (issuer):

-   **backchannel\_authentication\_endpoint**
    
    -   Endpoint em que o RP envia a requisição CIBA (backchannel authentication request);
        
    -   Deve ser publicado no documento de discovery do OP, conforme CIBA-Core / RFC 8414.
        

Todos os demais endpoints relevantes (`authorization_endpoint`, `token_endpoint`, `jwks_uri`, `registration_endpoint`, etc.) já são exigidos pela certificação OFB‑FAPI‑BR e não sofrem alteração estrutural por causa de CIBA.

## 2.1. Obtenção de metadados do OP para CIBA

Ao configurar uma relação com um novo OP (detentora/transmissora), o RP deve:

1.  **Localizar o issuer e o endpoint de discovery do OP** a partir do Diretório de Participantes do Open Finance Brasil;
    
2.  **Consumir o documento de metadados** (OIDC Discovery / RFC 8414) e, além dos pontos já utilizados para OFB‑FAPI‑BR, extrair especificamente os seguintes itens relacionados a CIBA:
    
    **backchannel\_authentication\_endpoint**
    
    -   Endpoint a ser utilizado pelo RP para envio das requisições CIBA;
        
    -   Deve ser armazenado e utilizado para todas as chamadas de backchannel authentication junto a este OP.
        
    
    **grant\_types\_supported**
    
    -   Verificar que o OP anuncia o grant\_type: `"urn:openid:params:grant-type:ciba"`;
        
    -   Se este grant\_type não estiver presente, o RP não deve tentar utilizar CIBA com aquele OP.
        
    
    **backchannel\_token\_delivery\_modes\_supported**
    
    -   O RP deve verificar que o OP anuncia `["ping"]`;
        
    -   O RP não deve tentar operar com modos não anunciados ou não permitidos (`"push"` ou `"poll"`).
        
    
    **backchannel\_authentication\_request\_signing\_alg\_values\_supported**
    
    -   Conjunto de algoritmos aceitos pelo OP para assinatura do request object CIBA;
        
    -   O RP deve selecionar um algoritmo compatível com essa lista e com as exigências de FAPI‑BR (ex.: PS256, ES256).
        
    
    **backchannel\_user\_code\_parameter\_supported**
    
    -   No perfil brasileiro, espera‑se `false`; mas caso venha `true`, o RP não deve se registrar para utilizar `user_code`.
        

Todos os demais metadados relevantes (`authorization_endpoint`, `token_endpoint`, `jwks_uri`, `registration_endpoint`, etc.) já são consumidos pelo RP conforme exigido pela certificação OFB‑FAPI‑BR e não sofrem alteração estrutural por causa de CIBA.

## 2.2. Alinhamento com autenticação de cliente (OFB‑FAPI‑BR)

Do ponto de vista do RP, CIBA não altera o modelo de autenticação de cliente já exigido pelo Open Finance Brasil:

-   O RP deve continuar se autenticando junto ao OP usando `private_key_jwt`, tanto no `token_endpoint` quanto no `backchannel_authentication_endpoint`, conforme OFB‑FAPI‑BR;
    
-   Ao consumir discovery, o RP deve apenas confirmar que os metadados de `token_endpoint_auth_methods_supported` e algoritmos de assinatura continuam consistentes com esse modelo e com sua própria configuração.
    

Ou seja:

-   Não há introdução de novos métodos de autenticação de cliente por causa de CIBA;
    
-   O discovery deve apenas confirmar que o RP, autenticando‑se via `private_key_jwt` conforme OFB‑FAPI‑BR, está autorizado a usar o grant\_type `urn:openid:params:grant-type:ciba` e o `backchannel_authentication_endpoint` anunciado pelo OP.
    

# 3\. Registro (DCR/DCM)

O processo de registro dinâmico de clientes (Dynamic Client Registration – DCR e Dynamic Client Management – DCM), já implementado e certificado conforme OFB-FAPI-BR-DCR, permite que o RP se registre automaticamente junto ao OP utilizando um Software Statement Assertion (SSA) emitido pelo Diretório de Participantes. No contexto do CIBA-BR, esse mecanismo permanece inalterado em sua estrutura, mas o RP deve incluir parâmetros adicionais no payload de registro para declarar sua capacidade e intenção de operar no modo CIBA. Este capítulo descreve exclusivamente os novos parâmetros que o RP deve enviar ao OP durante o registro (ou atualização via DCM) para habilitar o fluxo CIBA, as validações que o RP deve realizar sobre a resposta do OP, e as configurações específicas relacionadas ao modo PING, sem repetir as exigências gerais de DCR/DCM já estabelecidas pelo perfil brasileiro.

Padrões de referência:

-   RFC 7591 (OAuth 2.0 Dynamic Client Registration – DCR)
    
-   RFC 7592 (OAuth 2.0 Dynamic Client Registration Management – DCM)
    
-   OFB-FAPI-BR-DCR (perfil brasileiro para DCR/DCM)
    
-   CIBA-Core / FAPI-CIBA / CIBA-BR
    

## 3.1. Parâmetros novos ou estendidos no registro de cliente CIBA

Quando o RP deseja se registrar com capacidade CIBA junto a um OP, ele deve incluir no payload de DCR ou DCM os seguintes parâmetros adicionais (ou estender valores de parâmetros já existentes):

**grant\_types**

-   O RP deve incluir obrigatoriamente: `"urn:openid:params:grant-type:ciba"`;
    
-   O RP deve manter também os demais grant\_types já utilizados em fluxos OFB-FAPI-BR (por exemplo, `"authorization_code"`, `"refresh_token"`, `"client_credentials"` conforme aplicável ao contexto do RP);
    
-   Exemplo: `["authorization_code", "refresh_token", "client_credentials", "urn:openid:params:grant-type:ciba"]`.
    

**backchannel\_token\_delivery\_mode**

-   No contexto brasileiro (CIBA‑BR), o RP deve declarar: `"ping"`;
    
-   O RP não deve solicitar registro com delivery\_mode `"push"` ou `"poll"`;
    
-   Observação: o modo `"poll"` pode ser utilizado pelo RP como fallback implícito (conforme descrito no capítulo 4), mas o modo registrado deve ser `"ping"`.
    

**backchannel\_client\_notification\_endpoint**

-   **Obrigatório** para modo `"ping"`.
    
-   URL do endpoint do RP que receberá a notificação CIBA (ping) do OP ao final da jornada de autenticação do usuário;
    
-   O RP deve garantir que este endpoint:
    
    -   Utilize HTTPS;
        
    -   Aceite conexões TLS conforme BCP195;
        
    -   Suporte mTLS conforme exigido pelo ecossistema Open Finance Brasil (ou seja, aceite conexões autenticadas via certificado BRCAC do OP);
        
    -   Esteja disponível e acessível pelos OPs com os quais o RP pretende operar CIBA.
        

**backchannel\_authentication\_request\_signing\_alg**

-   Algoritmo de assinatura que o RP utilizará para assinar o request object CIBA (uso de request object assinado é obrigatório conforme OFB-FAPI-BR);
    
-   Deve estar alinhado com os algoritmos permitidos por FAPI‑BR (ex.: `PS256`, `ES256`) e com a lista anunciada pelo OP em `backchannel_authentication_request_signing_alg_values_supported` (conforme obtido no discovery);
    
-   O RP deve selecionar um algoritmo que:
    
    -   Esteja presente na lista do OP;
        
    -   Seja compatível com as chaves do RP (publicadas via `jwks_uri` ou `jwks`).
        

**backchannel\_user\_code\_parameter**

-   Se enviado, deve ser `false` (ou omitido, caso o OP aceite omissão como padrão `false`);
    
-   No perfil brasileiro (CIBA-BR), o uso de `user_code` não é permitido; portanto, o RP deve declarar explicitamente `false` ou não enviar este parâmetro (dependendo da política de validação do OP).
    

Todos os demais parâmetros de DCR já exigidos por OFB‑FAPI‑BR (`jwks_uri` ou `jwks`, `token_endpoint_auth_method = private_key_jwt`, `redirect_uris` – quando aplicável a fluxos front-channel, `client_name`, `logo_uri`, `policy_uri`, `tos_uri`, etc.) permanecem obrigatórios e inalterados. CIBA apenas adiciona os itens acima.

Após enviar a requisição de DCR (ou atualização via DCM) ao OP, o RP deve validar a resposta recebida para garantir que o registro CIBA foi aceito e armazenado conforme esperado, e que o cliente está apto a operar no perfil CIBA-BR.

## 3.2. Preparação do endpoint de notificação (backchannel\_client\_notification\_endpoint)

Antes de concluir o registro CIBA, o RP deve garantir que o endpoint declarado em `backchannel_client_notification_endpoint` está:

**Implementado e acessível:**

-   O endpoint deve estar ativo e acessível pelos OPs do ecossistema Open Finance Brasil.
    

**Configurado para mTLS:**

-   Deve aceitar conexões mTLS usando certificados BRCAC válidos do OP;
    
-   O RP deve validar o certificado do OP (cadeia, revogação, binding ao `client_id` ou `organisation_id` conforme política de segurança do ecossistema).
    

**Preparado para processar notificações PING:**

-   O endpoint deve ser capaz de receber e processar a notificação conforme CIBA-Core / FAPI-CIBA / CIBA-BR (detalhes do processamento serão abordados no capítulo 4 – Jornada CIBA).
    

**Monitorado e resiliente:**

-   O RP deve implementar logging, alertas e controles de disponibilidade para garantir que notificações PING não sejam perdidas por indisponibilidade do endpoint;
    
-   Em caso de indisponibilidade temporária, o RP deve estar preparado para utilizar polling como fallback (conforme descrito no [capítulo 4](data/references/guides/Guia.md)).
    

# 4\. Jornada CIBA

Este capítulo descreve a implementação do CIBA no modo PING do ponto de vista do RP, cobrindo apenas os comportamentos e regras necessários para operar o fluxo de autenticação desacoplada (backchannel). Não descreve jornadas específicas de produto (por exemplo, dados cadastrais/transacionais ou pagamentos) e não substitui regras de negócio e contratos técnicos das APIs de produto. A premissa é que o RP já opera uma implementação certificada em OFB-FAPI-BR; aqui são listados somente os pontos “delta CIBA”, incluindo o uso de login\_hint como identificador opaco, a criação e gestão do `auth_req_id`, a recepção de notificação PING, o uso de polling como fallback e a troca de `auth_req_id` por tokens no `token_endpoint`.

Para uma visão completa e detalhada da jornada fim a fim envolvendo CIBA aplicada ao compartilhamento de **Dados Cadastrais e Transacionais** – incluindo criação de consentimento, autenticação do usuário no OP, emissão de tokens e consumo das APIs de recursos e dados – recomenda-se a consulta ao documento complementar Jornada de Dados Cadastrais e Transacionais com CIBA, que aplica, de forma concreta, as orientações genéricas deste guia ao caso específico de dados do cliente no Open Finance Brasil.

## 4.1. Visão geral e papéis

-   **OP (Authorization Server):** recebe a requisição CIBA, conduz a autenticação do usuário em canal desacoplado e emite tokens quando aplicável;
    
-   **RP (Client):** inicia a autenticação via backchannel\_authentication\_endpoint, recebe notificação PING e obtém tokens via token\_endpoint;
    
-   **Usuário:** autentica-se e decide (aprova/nega) no canal do OP.
    

### **4.1.1 Fluxo resumido (visão do RP)**

1.  RP cria consentimento na API de produto e obtém consentId (contexto).
    
2.  RP chama `POST /bc-authorise` (`backchannel_authentication_endpoint`) com `login_hint`igual ao consentId e recebe `auth_req_id`.
    
3.  RP aguarda notificação PING no seu callback endpoint.
    
4.  OP conduz autenticação do usuário (assíncrono, fora do controle do RP).
    
5.  OP envia PING ao RP (callback).
    
6.  RP valida PING e chama `POST /token` com `auth_req_id`.
    
7.  RP recebe tokens (access\_token, refresh\_token, id\_token) e consome APIs de recursos.
    

## 4.2. Pré-condição: contexto autorizável e identificador opaco (login\_hint)

Para iniciar CIBA, o RP deve possuir um “contexto autorizável” previamente estabelecido, que será referenciado no CIBA por um `login_hint`. No âmbito do Open Finance Brasil, esse contexto tipicamente é criado por uma etapa anterior de consentimento (conforme o produto/serviço), em que existe, permitindo ao OP recuperar o titular, o RP solicitante e o escopo autorizado. Podendo ser:

1.  um identificador de consentimento de dados (consentId);
    
2.  um identificador de consentimento de serviços de pagamento (consentId) - futuro;
    
3.  um identificador de vínculo de dispositivo (enrollmentId) - futuro.
    

Regra prática para o RP:

-   O RP deve enviar no `login_hint` o identificador do contexto criado na etapa de consentimento do produto;
    
-   O RP não deve tratar `login_hint` como credencial do usuário nem como identificador legível; é apenas uma referência opaca a um contexto já criado;
    
-   O RP deve estar preparado para receber erro `invalid_login_hint` caso o OP não consiga resolver/validar o contexto informado (por exemplo: consentId inexistente, expirado, revogado, ou não vinculado ao client\_id do RP).
    

Observação operacional: como no Open Finance Brasil existem vários produtos (compartilhamento de dados e serviços de pagamento via iniciadoras), a forma exata de obter o consentId varia por API de produto, mas o uso do consentId como `login_hint` no CIBA permanece o mesmo.

## 4.3. Construção e envio da requisição CIBA (backchannel\_authentication\_endpoint)

### 4.3.1. Seleção do OP e preparação

Antes de chamar CIBA com um OP, o RP deve:

-   consumir o discovery do OP e validar os metadados CIBA ([capítulo 2](data/references/guides/Guia.md)));
    
-   garantir que o client\_id está registrado com CIBA habilitado via DCR/DCM ([capítulo 3](data/references/guides/Guia.md)));
    
-   obter o `backchannel_authentication_endpoint` do OP via discovery;
    
-   garantir que consegue receber PING no `backchannel_client_notification_endpoint` registrado.
    

### 4.3.2. Autenticação do cliente e segurança de transporte

O RP deve aplicar os mesmos requisitos de segurança já exigidos em OFB-FAPI-BR:

-   mTLS conforme exigido no ecossistema (certificados BRCAC e políticas de validação aplicáveis);
    
-   autenticação de cliente via `private_key_jwt` tanto no `backchannel_authentication_endpoint` e `token_endpoinn`.
    

### 4.3.3. Request object assinado (obrigatório) e parâmetros relevantes

O RP deve enviar a requisição CIBA conforme CIBA-Core/FAPI-CIBA/CIBA-BR, utilizando request object assinado (JWT) com algoritmo compatível com:

-   o que o OP anuncia em `backchannel_authentication_request_signing_alg_values_supported`;
    
-   o que foi registrado no cliente (`backchannel_authentication_request_signing_alg`);
    
-   as exigências do perfil de segurança do Open Finance Brasil.
    

Parâmetros que o RP deve considerar (no request object e/ou conforme o método de envio adotado pelo OP):

**login\_hint**

-   conter o contexto de autorização conforme especificado no [capítulo 4.2](data/references/guides/Guia.md)).
    

**scope**

-   deve ser coerente com o contexto referenciado e com a finalidade do fluxo;
    
-   o RP não deve solicitar scopes fora do que está autorizado no consentimento (isso pode resultar em `invalid_scope` ou falha de autorização).
    

**client\_notification\_token**

-   token opaco definido pelo RP para correlação e segurança no recebimento do PING;
    
-   o RP deve gerar valor imprevisível e associá-lo internamente ao estado da transação (`auth_req_id` quando recebido);
    
-   o RP deve validar esse token quando receber a notificação (ver [capítulo 4.6](data/references/guides/Guia.md))), para evitar confusão de transações e ataques de injeção.
    

**requested\_expiry**

-   -   pode ser enviado pelo RP para solicitar o prazo de validade da requisição de autenticação CIBA;
        
    -   quando enviado, deve conter um número inteiro positivo e não deve ser superior ao prazo máximo estabelecido pela regra específica do produto ou serviço;
        
    -   quando o valor solicitado for inferior ou igual ao prazo máximo aplicável, o OP utilizará esse valor como prazo de validade do `auth_req_id`;
        
    -   quando o parâmetro não for enviado ou o valor solicitado for superior ao prazo máximo aplicável, o OP aplicará o prazo máximo estabelecido para o produto ou serviço;
        
    -   o RP deve sempre utilizar o valor de `expires_in` retornado pelo OP como referência efetiva para a validade do `auth_req_id`.
        

**binding\_message (opcional)**

-   o RP pode enviar o parâmetro opcional `binding_message` para fornecer informação auxiliar de contexto ao OP, observadas as regras específicas aplicáveis ao produto, serviço ou jornada em questão.
    
-   quando utilizado, o binding\_message deve ser uma mensagem curta, neutra e descritiva do contexto da solicitação
    
-   o `binding_message` deve observar os limites, formatos, charset permitido, políticas de sanitização e demais restrições definidos para o produto, serviço ou jornada correspondente.
    
-   não deve conter dados sensíveis (CPF, e-mail, telefone, códigos, links, valores confidenciais)​;
    
-   não deve ser usada para marketing ou conteúdo promocional​.
    

O RP deve ainda cumprir os requisitos gerais de integridade do request object: claims obrigatórias (por exemplo, iss, aud, iat, exp, jti quando aplicável), consistência de audience e vinculação ao OP.

### 4.3.4. Respostas e erros relevantes no backchannel\_authentication\_endpoint

Em caso de sucesso, o RP receberá tipicamente:

-   **auth\_req\_id:** identificador da transação CIBA;
    
-   **expires\_in:** validade do `auth_req_id` (referência obrigatória para o RP);
    
-   **interval**: quando aplicável, intervalo mínimo recomendado para polling no `token_endpoint` (fallback).
    

Erros relevantes que o RP deve tratar:

-   **invalid\_login\_hint**: contexto inválido/não resolúvel/estado incompatível;
    
-   **unauthorized\_client**: falha de autenticação/autorização;
    
-   **invalid\_request**: request object malformado, assinatura inválida, parâmetros inconsistentes;
    
-   **invalid\_scope**: scope incompatível com o consentimento/contexto.
    

## 4.4. Gestão de estado do lado do RP (auth\_req\_id lifecycle)

Ao receber um `auth_req_id` válido, o RP deve persistir estado transacional vinculando no mínimo:

-   auth\_req\_id ↔ OP (issuer) ↔ client\_id usado ↔ login\_hint (consentId) ↔ scope solicitado;
    
-   client\_notification\_token (o mesmo enviado);
    
-   timestamps (criação, expiração efetiva calculada por expires\_in);
    
-   status (pendente, notificado, tokenizado, negado, expirado, erro);
    
-   correlação com a operação/produto (ex.: qual consentimento/proposta/origem interna).
    

## 4.5. Condução da autenticação do usuário (fluxo desacoplado) – visão do RP

Após iniciar CIBA, o RP não conduz a autenticação do usuário: ela ocorre no canal do OP (app, internet banking, etc.). Do ponto de vista do RP, isso implica:

-   o RP deve projetar UX/fluxo de negócio assumindo que a decisão do usuário é assíncrona;
    
-   o RP deve respeitar o `expires_in`: se expirar sem decisão, a transação deve ser encerrada e tratada como consentimento rejeitado do ponto de vista de negócio;
    
-   o RP não deve assumir que receberá PING imediatamente; deve tratar “pendente” como estado normal.
    

## 4.6. Recebimento da notificação PING (backchannel\_client\_notification\_endpoint)

No modo PING (obrigatório no CIBA-BR), o OP fará uma chamada ao endpoint do RP registrado em `backchannel_client_notification_endpoint` quando houver mudança de estado relevante (tipicamente após decisão do usuário).

Responsabilidades do RP ao receber o PING:

**a) Segurança do endpoint**

-   exigir HTTPS e aplicar validações TLS, mTLS;
    
-   validar o certificado BRCAC do OP (cadeia, política e critérios operacionais do RP).
    

**b) Correlação e validação**

-   extrair do payload o `auth_req_id` para correlação com o contexto;
    
-   validar o `client_notification_token` recebido/associado (conforme a forma definida no perfil/especificação), garantindo que a notificação corresponde à transação iniciada pelo RP;
    
-   tratar notificações duplicadas como idempotentes (não disparar dupla tokenização, não duplicar efeitos de negócio).
    

**c) Comportamento após o PING**

-   o PING não entrega tokens. Ele sinaliza ao RP que deve buscar o resultado no `token_endpoint` usando o `auth_req_id`.
    
-   ao receber um PING válido, o RP deve preparar (ou agendar) a chamada ao `token_endpoint` para concluir a jornada.
    

**d) Resposta do endpoint do RP**

-   o RP deve responder de forma previsível e rápida, minimizando timeouts do lado do OP.
    
-   se houver indisponibilidade temporária, isso aumentará a chance de retries do OP e/ou acionará polling como fallback do lado do RP.
    

### 4.6.1. Considerações sobre a implementação do endpoint de callback

Além do especificado nas normas CIBA-BR e FAPI-CIBA, a implementação do endpoint de notificação PING pelo RP deve observar os seguintes aspectos técnicos e operacionais:

**a) Processamento síncrono mínimo (aceitação segura)**

-   O RP deve implementar o endpoint de notificação PING de forma a receber a requisição e realizar todas as validações de segurança especificadas em FAPI-CIBA de forma síncrona, antes de retornar a resposta HTTP (por exemplo: validações de TLS/mTLS, validação de integridade/autenticidade conforme mecanismo aplicável no perfil, validações de correlação como `client_notification_token` quando aplicável e checagens básicas de formato).
    

**b) Processamento assíncrono (pós-aceitação)**

-   O RP deve executar validações de negócio adicionais e processamentos subsequentes de forma assíncrona, após responder ao Authorization Server, com o objetivo de não manter a conexão HTTP da notificação PING aguardando processamentos que não sejam essenciais para a aceitação da notificação. Exemplos típicos de processamento assíncrono:
    
    -   disparo da chamada ao `token_endpoint` para troca do `auth_req_id`;
        
    -   atualização de estado interno do fluxo de negócio;
        
    -   notificações internas, auditoria e enriquecimento de dados.
        

**c) Idempotência e notificações duplicadas**

-   O RP deve estar preparado para receber notificações duplicadas referentes ao mesmo auth\_req\_id (por retentativas do OP e/ou comportamento de rede) e deve tratar o processamento de forma idempotente, evitando efeitos duplicados e processamentos desnecessários (por exemplo, evitar chamar novamente o /token se a transação já estiver concluída, ou garantir que chamadas repetidas não alterem o estado final).
    

**d) Capacidade e dimensionamento**

-   O RP deve dimensionar a sua infraestrutura para atender ao volume de notificações recebidas, considerando:
    
    -   o volume normal de operações CIBA;
        
    -   a possibilidade de retentativas de entrega por parte dos Authorization Servers;
        
    -   janelas de pico de tráfego.
        

**e) Parâmetros técnicos**

-   **Timeout:** OP e RP devem configurar timeout de conexão HTTP em 10 segundos.
    
-   **SLA de resposta do endpoint do RP:** 1000 ms (tempo para retornar HTTP ao OP, considerando apenas validações síncronas essenciais).
    
-   **Limites de tráfego e operacional:** não se aplicam (observação: isso não elimina a necessidade de o RP ter proteção de infraestrutura contra overload/DoS; significa apenas que não há um limite normativo do perfil para o callback).
    

**f) Tratamento de status HTTP na resposta do endpoint de callback**

O RP deve utilizar códigos HTTP de forma consistente, de modo a orientar corretamente o comportamento do Authorization Server em relação a retentativas:

-   **Responder 2xx** apenas quando aceitar a notificação e conseguir enfileirar com segurança o processamento assíncrono do evento (incluindo posterior chamada ao /token, se aplicável).
    
-   **Responder 4xx** quando a notificação não for aceita por violação de contrato, segurança ou validações definitivas (sem expectativa de sucesso em retentativas), por exemplo:
    
    -   falha de validação de autenticação/autorização do OP;
        
    -   payload inválido de forma permanente;
        
    -   correlação inválida (`client_notification_token` não reconhecido ou `auth_req_id` desconhecido/expirado de forma definitiva).
        
-   **Responder 429** quando estiver sob pressão de volume e desejar que o OP retente em outro momento (sinalizando bloqueio temporário por excesso de requisições). O RP pode opcionalmente incluir o cabeçalho `Retry-After` para orientar o OP.
    
-   **Responder 5xx** (por exemplo 500, 503) ou **408** quando houver indisponibilidade transitória ou falhas internas que impeçam o processamento da notificação naquele momento, mas que possam ser resolvidas em uma tentativa futura.
    
-   **Não utilizar 3xx** (redirecionamento): o RP não deve redirecionar notificações PING; caso seja necessário alterar o endpoint de callback, isso deve ser feito via atualização de registro (DCM).
    

## **4.7. Suporte a polling como fallback (exceção)**

Embora o modo PING seja o padrão, o RP deve suportar mecanismo de fallback via polling quando:

-   houver suspeita de falha de entrega (instabilidade do endpoint do RP, rede, etc.);
    
-   o OP estiver indisponível para enviar a notificação mas mantém o estado;
    
-   o RP não receber o PING esperado dentro de uma janela operacional;
    
-   o fallback deve prioritariamente verificar mudanças de estado na API de consentimento do produto/serviço (por exemplo, `GET /consents/{consentId}`). Ao detectar que o consentimento mudou para AUTHORISED, o RP deve então chamar o token\_endpoint com o auth\_req\_id para obter os tokens. Essa abordagem reduz a carga no `token_endpoint` e melhora a eficiência operacional.
    

Regras práticas de polling pelo RP:

-   respeitar o `interval` informado pelo OP (quando presente) para evitar rate limiting e erros;
    
-   interromper polling quando `expires_in` expirar;
    
-   monitorar evidências operacionais (quantidade de polls, erros, tempo até conclusão), pois alta incidência pode indicar falhas de infraestrutura.
    

## 4.8. Token endpoint: troca de auth\_req\_id por tokens (grant CIBA)

O RP obterá tokens via token\_endpoint usando grant\_type CIBA e auth\_req\_id.

### 4.8.1. Requisição ao token\_endpoint

O RP deve:

-   autenticar-se via `private_key_jwt` conforme OFB-FAPI-BR;
    
-   usar mTLS conforme exigido;
    
-   enviar grant\_type = `"urn:openid:params:grant-type:ciba"`;
    
-   enviar `auth_req_id` recebido do OP.
    

### 4.8.2. Respostas e estados que o RP deve tratar

O RP deve tratar os estados definidos por CIBA-Core/FAPI-CIBA/CIBA-BR, em especial:

**Pendente:**

-   `authorization_pending`: significa que o usuário ainda não decidiu;
    
-   o RP deve continuar aguardando PING ou fazer polling respeitando interval e expires\_in.
    

**Negado:**

-   `access_denied`: o usuário negou ou o OP negou por decisão de segurança/risco;
    
-   o RP deve encerrar a transação e seguir o tratamento de negócio (sem tentar “forçar” nova tokenização com o mesmo `auth_req_id`).
    

**Expirado:**

-   `expired_token` (ou erro equivalente conforme perfil): o `auth_req_id` expirou;
    
-   o RP deve encerrar a transação e, se necessário, reiniciar todo o processo criando novo contexto/consentimento e nova requisição CIBA (não reutilizar `auth_req_id` expirado).
    

**Aprovado:**

-   o OP retornará tokens (tipicamente):
    
    -   access\_token;
        
    -   refresh\_token (quando aplicável);
        
    -   id\_token (quando aplicável ao perfil e ao conjunto de scopes)
        

O RP deve armazenar tokens conforme sua política de segurança, respeitar expiração e escopos, e utilizar esses tokens para acessar as APIs do ecossistema (fora do escopo deste capítulo).

## 4.9. Considerações de segurança, abuso e fraude (específicas de CIBA) – visão do RP

Sem repetir controles gerais de FAPI já existentes, o RP deve observar riscos particulares do CIBA:

**a) Proteção de identificadores e anti-fraude**

-   consentId (`login_hint`) é identificador opaco: proteger contra vazamento em logs/telemetria.
    
-   `client_notification_token` deve ser imprevisível e validado rigorosamente no callback PING.
    

**b) Controle de jornada assíncrona**

-   implementar timeouts coerentes com `expires_in` e com regras de negócio;
    
-   prevenir “pendências eternas” e filas acumuladas.
    

**c) Resiliência e idempotência**

-   PING pode repetir (retries do OP): endpoint do RP deve ser idempotente.
    
-   tokenização pode ser chamada mais de uma vez (polling): o RP deve tratar respostas repetidas sem causar efeitos duplicados.
    

**d) Contenção de abuso**

-   evitar polling agressivo (respeitar interval/backoff);
    
-   monitorar falhas sistemáticas de PING e elevar para correção de infraestrutura (do RP e/ou do OP).
    

# 5\. Diretório de Participantes

No Diretório de Participantes, o RP deverá registrar, para cada um de seus softwares clientes, as suas certificações de segurança e funcionais, conforme especificado no Guia de Operação do Diretório.

# 6\. Monitoramento

O RP deverá incluir no reporte à PCM:

-   O resultado da chamada a API de segurança POST /token na criação de tokens do tipo `cliente_credentials` e CIBA;
    
-   O resultado da chamada ao endpoint POST /bc-authorise na solicitação de uma autenticação CIBA;
    
-   O resultado do recebimento da notificação PING no `backchannel_client_notification_endpoint;`
    
-   O resultado da chamada das APIs de negócio (por exemplo: Consentimentos e Resources).
