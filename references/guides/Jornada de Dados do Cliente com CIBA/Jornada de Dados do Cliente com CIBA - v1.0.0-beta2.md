# Jornada de Dados do Cliente com CIBA - v1.0.0-beta2

12falsenonelisttrue

# 1\. Introdução

## 1.1. Objetivo

Este documento tem por objetivo ilustrar, de forma prática e detalhada, uma jornada completa de autenticação desacoplada (backchannel) utilizando o perfil CIBA-BR **aplicado à autorização de um consentimento de Dados Cadastrais e Transacionais** no contexto do Open Finance Brasil, incluindo exemplos de requisições e respostas HTTP trafegadas entre os participantes.

O foco é mostrar, ponta a ponta, como o CIBA é usado para o cliente autenticar-se e autorizar um consentimento de compartilhamento de dados cadastrais e transacionais junto à detentora (OP), permitindo que a receptora (RP) obtenha tokens e passe a consumir as APIs de dados.

O público-alvo são desenvolvedores, arquitetos de solução e equipes de integração que já conhecem as especificações CIBA-BR, OFB-FAPI-BR, FAPI-CIBA e as APIs de Dados Cadastrais e Transacionais, e desejam visualizar, passo a passo, como os fluxos se concretizam na prática.

## 1.2. Escopo

Este documento cobre, especificamente para a **jornada de Dados Cadastrais e Transacionais:**

-   **Discovery (OpenID Connect Discovery)**: como o receptor (RP) descobre as capacidades CIBA do transmissor (OP);
    
-   **Registro Dinâmico de Cliente (DCR)**: como o receptor (RP) se registra para habilitar CIBA;
    
-   **Jornada CIBA completa** (modo PING): desde a criação do consentimento até a obtenção de tokens e consumo de APIs de recursos.
    

Este documento não substitui as especificações técnicas oficiais (CIBA-BR, OFB-FAPI-BR, FAPI-CIBA, CIBA-Core) nem os guias de implementação para OP e RP. Ele serve como material complementar ilustrativo.

## 1.3. Convenções

-   Todos os exemplos utilizam dados fictícios (URLs, client\_id, tokens, certificados).
    
-   As requisições e respostas são ilustrativas, podendo divergir do que realmente precisa ser executado e recebido de um servidor produtivo real.
    
-   As requisições e respostas estão formatadas para legibilidade (indentação JSON, quebras de linha).
    
-   Cabeçalhos HTTP não essenciais ao entendimento do fluxo podem ser omitidos.
    
-   Assinaturas JWS e certificados mTLS são representados de forma simplificada (indicados por `<base64url>` ou `<PEM>`).
    

## **1.4. Premissas**

-   O RP já possui um Software Statement Assertion (SSA) válido emitido pelo Diretório de Participantes do Open Finance Brasil.
    
-   O OP já publicou um Authorization Server certificado em OFB-FAPI-BR com suporte a CIBA-BR.
    
-   O RP e o OP possuem certificados BRCAC válidos para autenticação mútua (mTLS).
    

# 2\. Participantes da Jornada

## 2.1. Instituições envolvidas

Papel

Instituição (fictícia)

URL base

**Transmissora (OP)**

Banco Exemplo S.A.

`https://auth.bancoexemplo.com.br`

**Receptora (RP)**

Fintech Inovadora Ltda.

`https://api.fintechinova.com.br`

**Diretório de Participantes**

Open Finance Brasil

`https://matls-auth.directory.openbankingbrasil.org.br`

## 2.2. Identificadores e credenciais (fictícios)

**Item**

**organisationId da Transmissora (OP)**

`2d79a9f3-c679-457e-9651-3441fa686df1`

**organisationId da Receptora (RP)**

`a1b2c3d4-e5f6-7890-abcd-ef1234567890`

**softwareStatmentId da Receptora (RP)**

`s1w2a3r4-e5d6-7890-ijkl-mn1234567890`

**clientId pós-registro na Transmissora**

`rp_fintech_inovadora_prod_001`

**SSA (JWT assinado pelo Diretório)**

`eyJhbGc...` (simplificado nos exemplos)

# 3\. Discovery e Registro

## 3.1. Discovery (OpenID Connect Discovery)

### 3.1.1 Objetivo

Antes de qualquer interação técnica com o Authorization Server da transmissora (OP), a receptora (RP) precisa descobrir as capacidades e endpoints disponíveis. Isso é feito consultando o documento de metadados OpenID Connect Discovery (well-known), que publica informações essenciais como:

-   Endpoints de autorização, token, registro dinâmico e CIBA;
    
-   Algoritmos de assinatura e criptografia suportados;
    
-   Grant types disponíveis (incluindo CIBA);
    
-   Modos de entrega de notificação CIBA (no caso do OFB, apenas "ping");
    
-   Requisitos de segurança (mTLS, private\_key\_jwt, PAR obrigatório, etc.).
    

Essa etapa é fundamental para que o receptor (RP) valide que o transmissor (OP) suporta CIBA-BR antes de prosseguir com o registro e a jornada de autenticação.

### 3.1.2. Requisição HTTP

wide1800

### 3.1.3. Resposta HTTP

jsonwide1800

### 3.1.4. Validações do RP

Após obter o documento de discovery, o RP deve verificar as seguintes condições para confirmar que o OP suporta CIBA-BR conforme esperado:

**Capacidades CIBA obrigatórias:**

-   `grant_types_supported` contém `"urn:openid:params:grant-type:ciba"`.
    
-   `backchannel_token_delivery_modes_supported` contém `"ping"`.
    
-   `backchannel_user_code_parameter_supported` é `false`.
    
-   `backchannel_authentication_request_signing_alg_values_supported` inclui ao menos um algoritmo suportado pelo receptor (RP).
    

## 3.2. Registro Dinâmico de Cliente (DCR)

### **3.2.1. Objetivo**

Para que o receptor (RP) possa iniciar jornadas CIBA com o transmissor (OP), ele precisa se registrar dinamicamente junto ao Authorization Server, utilizando seu Software Statement Assertion (SSA) emitido pelo Diretório de Participantes. Esse registro cria um `client_id` e estabelece os parâmetros de segurança e capacidades do cliente, incluindo:

-   Grant types suportados (incluindo CIBA);
    
-   Modo de entrega de notificação CIBA (ping);
    
-   Endpoint de callback para receber notificações PING;
    
-   Algoritmos de assinatura para request objects CIBA;
    
-   Métodos de autenticação de cliente (private\_key\_jwt);
    
-   Scopes desejados para operar APIs de Dados Cadastrais e Transacionais.
    

O registro é feito via POST no `registration_endpoint` do transmissor (OP).

### **3.2.**2\. Requisição HTTP (POST /reg)

jsonwide1800" }\]\]>

### **3.2**.3. Resposta HTTP (registro bem-sucedido)

jsonwide1800

### **3.2.4 Validações do RP**

Após receber a resposta de registro bem-sucedido, o RP deve validar que os parâmetros retornados estão coerentes com o que foi solicitado:

-   `grant_types` inclui `"urn:openid:params:grant-type:ciba"`;
    
-   `backchannel_token_delivery_mode` é `"ping"`;
    
-   `backchannel_client_notification_endpoint` corresponde ao que foi enviado;
    
-   `backchannel_authentication_request_signing_alg` é o algoritmo solicitado;
    
-   `backchannel_user_code_parameter` é `false`.
    

Se todas as validações passarem, o receptor (RP) está pronto para iniciar jornadas CIBA com este transmissor (OP).

# 4\. Jornada CIBA do Consentimento de Dados Cadastrais e Transacionais

![image-20260219-183819.png](images/image-20260219-183819.png)

## **4.1. Cliente inicia jornada (etapa não-técnica)**

Antes de qualquer chamada técnica às APIs do Open Finance Brasil, o usuário interage com o aplicativo ou site da receptora (RP) para expressar sua intenção de compartilhar dados cadastrais e transacionais de sua conta na instituição detentora (OP). Essa etapa é puramente de experiência do usuário (UX/UI) e não envolve requisições HTTP ao ecossistema.

**O que acontece nesta etapa:**

1.  O usuário acessa o aplicativo/site da receptora (Fintech Inovadora).
    
2.  O usuário seleciona a funcionalidade desejada (ex.: "Conectar minha conta bancária", "Importar minhas transações").
    
3.  O sistema da receptora apresenta ao usuário:
    
    -   Com qual instituição detentora (ex.: Banco Exemplo S.A.);
        
    -   Quais dados serão compartilhados (ex.: dados cadastrais, saldo, transações);
        
    -   Prazo de validade do consentimento.
        
4.  O usuário confirma a intenção de compartilhamento.
    

**Resultado desta etapa:**

-   A receptora armazena internamente a intenção do usuário e os parâmetros de compartilhamento (escopos desejados, instituição detentora, etc.);
    
-   A receptora está pronta para iniciar o fluxo técnico: obter token client\_credentials, criar consentimento formal e iniciar CIBA.
    

## **4.2. Criar token de acesso sistêmico**

### **4.2.1. Objetivo**

Antes de criar um consentimento de dados junto à detentora, a receptora precisa autenticar-se como aplicação (client-to-server) para ter acesso às APIs de consentimento. Isso é feito obtendo um `access_token` do tipo **client\_credentials** junto ao Authorization Server da detentora.

Esse token não representa um usuário específico; ele representa a aplicação cliente do receptor (RP) e é usado para:

-   Criar consentimentos (POST /consents);
    
-   Consultar status de consentimentos (GET /consents/{consentId});
    
-   Outras operações de API que não exigem contexto de usuário autenticado.
    

O token `client_credentials` é de curta duração e deve ser renovado conforme necessário.

### **4.2.2. Requisição HTTP (POST /token)**

wide1800\]\]>

### **4.2.**3\. Resposta HTTP (sucesso)

jsonwide1800", "token\_type": "Bearer", "expires\_in": 600, "scope": "consents" }\]\]>

## **4.3. Criar Consentimento de Dados Cadastrais e Transacionais**

### **4.3.1. Objetivo**

Agora que a receptora possui um token client\_credentials válido, ela pode criar formalmente um consentimento junto à detentora, especificando:

-   Qual usuário será titular do consentimento (CPF/CNPJ do loggedUser);
    
-   Quais permissões estão sendo solicitadas (ex.: ACCOUNTS\_READ, ACCOUNTS\_BALANCES\_READ, ACCOUNTS\_TRANSACTIONS\_READ);
    
-   Prazo de validade do consentimento (expirationDateTime).
    

Ao criar o consentimento, a detentora:

1.  Valida o token client\_credentials (scope `consents`);
    
2.  Valida os parâmetros de negócio (permissões, usuário, prazo);
    
3.  Cria o consentimento no estado `AWAITING_AUTHORISATION` (aguardando autorização do usuário);
    
4.  Retorna um `consentId` único, que será usado como `login_hint` no fluxo CIBA.
    

### **4.3.2. Requisição HTTP (POST /consents)**

jsonwide1800 Content-Type: application/json x-fapi-interaction-id: 92cac523-d3ae-2289-b106-330a6218710d \[mTLS com certificado BRCAC do RP\] { "data": { "loggedUser": { "document": { "identification": "11111111111", "rel": "CPF" } }, "businessEntity": { "document": { "identification": "11111111111111", "rel": "CNPJ" } }, "permissions": \[ "ACCOUNTS\_READ", "ACCOUNTS\_BALANCES\_READ", "ACCOUNTS\_TRANSACTIONS\_READ" \], "expirationDateTime": "2025-12-31T23:59:59Z" } }\]\]>

### **4.3.3.** Resposta HTTP (consentimento criado, aguardando autorização)

jsonwide1800

## **4.4. Solicitar autenticação CIBA (POST /bc-authorize)**

### **4.4.1. Objetivo**

Com o consentimento criado (estado `AWAITING_AUTHORISATION`), a receptora agora inicia o fluxo de autenticação desacoplada (CIBA) para que o usuário, no canal da detentora (app ou internet banking), possa avaliar e aprovar o consentimento. Para isso, a receptora envia uma requisição ao `backchannel_authentication_endpoint` do OP, incluindo:

-   `login_hint`: o `consentId` criado no passo anterior (identificador opaco que permite ao OP localizar o consentimento e o usuário titular);
    
-   `scope`: escopos parametrizados (ex.: `openid consents:urn:...`);
    
-   `client_notification_token`: token gerado pela receptora para correlacionar a notificação PING que virá do OP;
    
-   `request` (JWT assinado): request object contendo todos os parâmetros, assinado pela receptora.
    

Se a requisição for válida, o OP retorna um `auth_req_id` e um `expires_in`, indicando que a autenticação foi iniciada e o usuário tem até `expires_in` segundos para aprovar/negar.

Nesta jornada de Dados Cadastrais e Transacionais, o RP não deve enviar `binding_message` na requisição CIBA. O contexto apresentado ao usuário pela transmissora deve ser derivado do consentimento previamente criado, identificado pelo consentId informado no `login_hint`, e das informações obrigatórias da própria jornada de consentimento.

### **4.4.2. Construção do Request Object (JWT assinado pelo RP)**

**Claims do request object:**

jsonwide1800

**Assinado com PS256:**

wide1800\]\]>

### **4.4.**3\. Requisição HTTP

wide1800 &client\_assertion\_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer &client\_assertion=eyJhbGciOiJQUzI1NiIsImtpZCI6InJwLWtleS0wMDEifQ.eyJpc3MiOiJycF9maW50ZWNoX2lub3ZhZG9yYV9wcm9kXzAwMSIsInN1YiI6InJwX2ZpbnRlY2hfaW5vdmFkb3JhX3Byb2RfMDAxIiwiYXVkIjoiaHR0cHM6Ly9hdXRoLmJhbmNvZXhlbXBsby5jb20uYnIvYmMtYXV0aG9yaXplIiwiaWF0IjoxNzA5MjM4MTAwLCJleHAiOjE3MDkyMzg0MDAsImp0aSI6ImF1dGhfYWJjMTIzIn0.\]\]>

### **4.4.**4\. Resposta HTTP (sucesso)

jsonwide1800

### **4.4.5. Armazenamento pelo RP**

O RP deve armazenar:

-   `auth_req_id`: `auth_req_A1B2C3D4E5F6G7H8` (identificador único da transação CIBA)
    
-   `expires_in`: 86400 segundos (24 horas) — prazo máximo para o usuário aprovar/negar
    
-   `interval`: 600 segundos (10 minutos) — intervalo mínimo para polling (se necessário usar fallback)
    
-   `client_notification_token` enviado: `notif_xyz789uvw012` (para validar a notificação PING quando ela chegar)
    

Neste ponto, o RP aguarda:

1.  Notificação PING do OP (fluxo normal); ou
    
2.  Polling no token\_endpoint, caso o PING não seja recebido (fallback). (apenas em cenários de excessão)
    

## **4.**5\. Notificar aprovadores do consentimento

### **4.**5.1. Objetivo

Após receber a requisição CIBA e localizar o consentimento associado ao `login_hint` (o `consentId`), a transmissora (OP) precisa acionar os aprovadores responsáveis por aquele consentimento para que eles possam:

-   Ser informados de que existe um consentimento pendente de autorização;
    
-   Autenticar-se com segurança (ex.: biometria, senha, token);
    
-   Selecionar recursos (contas e cartões) - quando aplicável;
    
-   Revisar o que está sendo solicitado (dados, permissões, prazo);
    
-   Autorizar ou negar o consentimento.
    

Essa etapa é interna à transmissora e pode envolver regras de negócio específicas, especialmente para clientes PJ. Não há novas chamadas RP → OP nesse momento; todo o processamento é iniciado a partir do auth\_req\_id recebido em /bc-authorize.

### **4.**5.2. O que acontece do lado da OP (visão conceitual)

Internamente, a OP:

-   Localiza o consentimento a partir do `login_hint`/`consentId`.
    
-   Identifica o(s) aprovador(es) para aquele tipo de consentimento.
    
-   Gera uma ou mais tarefas de aprovação (“work items”) para os aprovadores:
    
-   Por exemplo, notificação push no app, alerta no internet banking corporativo ou outra fila interna.
    

## **4.**6\. Cliente/aprovadores aprovam o consentimento

### **4.**6.1. Objetivo

Nesta etapa, o(s) aprovador(es) efetivamente acessam o canal da OP (app, internet banking, canal PJ, etc.), autenticam-se e aprovam (ou negam) o consentimento. Essa jornada acontece totalmente fora do controle técnico da receptora (RP) e do canal CIBA — do ponto de vista de CIBA, é um processo assíncrono que ocorre “no meio” entre o `/bc-authorize` e a futura chamada ao `/token`.

### **4.**6.2. O que acontece do lado da OP (visão conceitual)

Do ponto de vista do CIBA-BR:

1.  O usuário/aprovador acessa o canal da transmissora (OP).
    
2.  O usuário é autenticado com um dos níveis de `acr` suportados (por exemplo, `urn:brasil:openbanking:loa2` ou `loa3`).
    
3.  A transmissora (OP) apresenta os detalhes do consentimento:
    
    -   quem é a receptora (Fintech Inovadora);
        
    -   quais dados serão compartilhados;
        
    -   por quanto tempo;
        
    -   eventual contexto adicional (ex.: mensagem de binding\_message).
        
4.  O usuário/aprovador aprova ou nega o consentimento.
    
5.  A transmisora (OP):
    
    -   atualiza o estado do consentimento na API de produto (por exemplo, `AUTHORISED` ou `REJECTED`);
        
    -   atualiza o estado interno da transação CIBA associada ao `auth_req_id` (aprovada, negada, expirada, etc.).
        

Somente após essa decisão é que a transmissora (OP) irá enviar o PING ao (RP) (próximo passo).

Para esta jornada, o OP não deve utilizar `binding_message` como elemento de contexto adicional. As informações apresentadas ao usuário devem ser derivadas do consentimento criado e das regras de experiência aplicáveis ao compartilhamento de dados.

## **4.**7\. Transmissor notifica aprovação (backchannel\_client\_notification\_endpoint)

### **4.**7.1. Objetivo

Assim que a OP tiver um resultado para a transação CIBA (aprovação, negação ou expiração), ela notifica a receptora (RP) através do endpoint de callback registrado no DCR (`backchannel_client_notification_endpoint`), utilizando o modo PING definido em CIBA-BR.

Essa notificação serve para que o RP saiba que já pode tentar trocar o `auth_req_id` por tokens no `/token`.

### **4.**7.2. Requisição HTTP (PING da OP → RP)

jsonwide1800

Notas importantes:

-   O cabeçalho `Authorization: Bearer ...` utiliza exatamente o `client_notification_token` que foi enviado pelo RP no request object do `/bc-authorize`:
    
    -   aqui: `notif_xyz789uvw012`;
        
-   O corpo inclui pelo menos o `auth_req_id`; o modo PING não carrega o resultado em si (aprovado/negado) — esse resultado será conhecido quando o RP chamar o `/token`.
    

### **4.**7.3. Validações do RP ao receber o PING

Ao receber essa requisição, o RP deve:

1.  Validar a conexão mTLS (certificado BRCAC da OP).
    
2.  Validar o token de autorização:
    
    -   `Authorization: Bearer notif_xyz789uvw012` deve bater com o `client_notification_token` que o RP gerou e associou àquele `auth_req_id`.
        
3.  Validar o corpo:
    
    -   `auth_req_id` presente;
        
    -   `auth_req_id` conhecido e em estado “pendente” na base da receptora (RP).
        

Se tudo estiver correto, o RP:

-   registra internamente que o PING foi recebido para aquele `auth_req_id`;
    
-   agenda imediatamente (ou enfileira) a chamada ao `/token` (próximo passo).
    

A resposta HTTP da receptora (RP) para o PING pode ser simplesmente um 204 com corpo vazio.

## **4.**8\. Obter token de acesso de cliente (troca de auth\_req\_id por tokens)

### **4.**8.1. Objetivo

Após receber o PING (ou, em fallback, após algum tempo de espera utilizando o `interval`), a receptora (RP) tenta trocar o `auth_req_id` por tokens no `token_endpoint` do OP, utilizando o grant type CIBA (`urn:openid:params:grant-type:ciba`).

Se o usuário tiver aprovado o consentimento, o transmissor (OP) emitirá:

-   um `access_token` de usuário;
    
-   um `refresh_token`;
    
-   um `id_token` com contexto de autenticação;
    

### **4.**8.2. Requisição HTTP (POST /token com grant CIBA)

wide1800\]\]>

### **4.**8.3. Resposta HTTP (sucesso – consentimento aprovado)

jsonwide1800", "token\_type": "Bearer", "expires\_in": 600, "scope": "openid accounts accounts:read", "id\_token": "eyJhbGciOiJQUzI1NiIsImtpZCI6Im9wLWtleS0wMDEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2F1dGguYmFuY29leGVtcGxvLmNvbS5iciIsImF1ZCI6InJwX2ZpbnRlY2hfaW5vdmFkb3JhX3Byb2RfMDAxIiwic3ViIjoidXJuOmJhbmNvZXhlbXBsbzphY2NvdW50OjEyMzQ1Njc4OTAiLCJhdF9oYXNoIjoiYWJjMTIzX2hhc2giLCJzaWQiOiJzZXNzaW9uXzEyMzQ1NiIsImF1dGhfdGltZSI6MTcwOTIzODE1MCwiYWNyIjoidXJuOmJyYXNpbDpvcGVuYmFua2luZzpsb2EyIiwiaWF0IjoxNzA5MjM4MTUwLCJleHAiOjE3MDkyMzg3NTB9.", "refresh\_token": "eyJhbGciOiJQUzI1NiIsImtpZCI6Im9wLWtleS0wMDEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2F1dGguYmFuY29leGVtcGxvLmNvbS5iciIsInN1YiI6InVybjpiYW5jb2V4ZW1wbG86YWNjb3VudDoxMjM0NTY3ODkwIiwic2NvcGUiOiJvcGVuaWQgYWNjb3VudHMiLCJhdWQiOiJodHRwczovL2F1dGguYmFuY29leGVtcGxvLmNvbS5iciIsImlhdCI6MTcwOTIzODE1MCwiZXhwIjoxNzEwODQyOTUwLCJ0b2tlbl90eXBlIjoicmVmcmVzaF90b2tlbiIsImNvbnNlbnRJZCI6InVybjpiYW5jb2V4ZW1wbG86Y29uc2VudDpDMUQyRTNGNC1HNUg2LTc4OTAtSUpLTC1NTjEyMzQ1Njc4OTAifQ." }\]\]>

### **4.**8.4. Atualização interna no RP

O receptor (RP) deve:

1.  Associar o `access_token` e o `refresh_token` ao `consentId` e ao usuário interno.
    
2.  Marcar que o consentimento foi autorizado (pode opcionalmente consultar o consentimento na API da OP para confirmar o status `AUTHORISED`).
    
3.  Usar o `access_token` para consumir as APIs de recursos, respeitando:
    
    -   escopos autorizados;
        
    -   prazo de expiração dos tokens;
        

# **5\. Considerações Finais**

## **5.1. Resumo da jornada completa**

Este documento ilustrou, passo a passo, uma jornada completa de autenticação desacoplada (backchannel) utilizando o perfil CIBA-BR para autorização de consentimento de Dados Cadastrais e Transacionais no Open Finance Brasil. A jornada cobriu:

1.  **Discovery**: como a receptora descobre as capacidades CIBA do Authorization Server da detentora;
    
2.  **Registro Dinâmico (DCR)**: como a receptora se registra para habilitar fluxos CIBA em modo PING;
    
3.  **Configuração do usuário**: a intenção de compartilhamento expressa pelo usuário no canal da receptora (etapa não-técnica);
    
4.  **Token client\_credentials**: autenticação server-to-server para acesso às APIs de consentimento;
    
5.  **Criação de consentimento**: formalização do pedido de compartilhamento junto à detentora, gerando um `consentId`;
    
6.  **Requisição CIBA**: início do fluxo de autenticação desacoplada, com envio do `login_hint` (consentId) e obtenção de `auth_req_id`;
    
7.  **Aprovação do consentimento**: autenticação e decisão do usuário/aprovadores no canal da detentora;
    
8.  **Notificação PING**: comunicação assíncrona da detentora para a receptora, sinalizando que a transação foi concluída;
    
9.  **Troca de tokens**: obtenção de `access_token` (certificate-bound), `id_token` e `refresh_token` no `/token`;
    

## **5.2. Diferenças em relação ao fluxo front-channel (hybrid)**

Enquanto o fluxo híbrido tradicional (authorization\_code + id\_token) exige redirecionamento do navegador e interação síncrona do usuário no momento da autorização, o CIBA-BR oferece uma experiência desacoplada, na qual:

-   O usuário não precisa estar presente no dispositivo/sessão da receptora no momento da autenticação;
    
-   A autenticação ocorre de forma assíncrona no canal da detentora (app, internet banking);
    
-   A receptora é notificada via PING quando a decisão é tomada;
    
-   O fluxo é especialmente útil para:
    
    -   Aplicações server-side sem front-end web;
        
    -   Cenários B2B/PJ com múltiplos aprovadores;
        
    -   Jornadas de onboarding com menor atrito (ex.: solicitação de compartilhamento iniciada via link, SMS, etc.).
        

## **5.3. Gestão de tokens e ciclo de vida de consentimentos**

Após a obtenção dos tokens via CIBA, a receptora deve observar:

-   **Renovação de access\_token**: utilizar o `refresh_token` antes da expiração do `access_token`;
    
-   **Validade do consentimento**: respeitar o `expirationDateTime` do consentimento; tokens emitidos não estendem automaticamente a validade do consentimento;
    
-   **Revogação**: o usuário pode revogar o consentimento a qualquer momento via canal da detentora; nesse caso, novos acessos com o `access_token` serão bloqueados;
    

## **5.4. Tratamento de erros e cenários de fallback**

Embora este documento tenha ilustrado um fluxo de sucesso (happy path), em produção a receptora deve estar preparada para:

-   **Timeout do PING**: se a notificação PING não for recebida dentro do prazo esperado, o RP deve fazer polling no `/token` respeitando o `interval` retornado no `/bc-authorize`;
    
-   **Negação do consentimento**: o `/token` pode retornar erro `access_denied` se o usuário negar a autorização;
    
-   **Expiração do auth\_req\_id**: se o usuário não responder dentro do `expires_in`, o `/token` retornará `expired_token`;
    
-   **Erros de validação no** `/bc-authorize`: por exemplo, `invalid_request`, `invalid_client`, `unauthorized_client`, conforme CIBA Core e CIBA-BR;
    
-   **Indisponibilidade temporária**: erros HTTP 5xx devem ser tratados com retry (respeitando backoff exponencial).
    

## **5.5. Recursos adicionais**

Para aprofundamento técnico e implementação, recomenda-se consultar:

-   **Especificações oficiais**:
    
    -   CIBA Core (OpenID Connect Client-Initiated Backchannel Authentication);
        
    -   FAPI-CIBA (Financial-grade API CIBA Profile);
        
    -   CIBA-BR (perfil brasileiro);
        
    -   OFB-FAPI-BR (perfil de segurança do Open Finance Brasil);
        
    -   APIs de Dados Cadastrais e Transacionais (Open Finance Brasil).
        
-   **Guias de implementação**:
    
    -   Guia de Implementação para Receptoras (RP);
        
    -   Guia de Implementação para Transmissoras (OP);
        
    -   Guia de Segurança e Certificados mTLS.
        
-   **Ferramentas e ambientes de testes**:
    
    -   Diretório de Participantes do Open Finance Brasil;
        
    -   Sandbox de APIs;
        
    -   Conformance Suite (OpenID Foundation).
