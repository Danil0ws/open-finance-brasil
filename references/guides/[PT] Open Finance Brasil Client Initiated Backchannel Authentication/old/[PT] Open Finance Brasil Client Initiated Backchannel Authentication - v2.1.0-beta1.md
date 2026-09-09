# [PT] Open Finance Brasil Client Initiated Backchannel Authentication - v2.1.0-beta1

13falsenonelisttrue

## **1\. Introdução**

O Open Finance Brasil adota o padrão Financial-grade API (FAPI) para garantir segurança adequada aos serviços financeiros oferecidos no ecossistema. Este documento especifica o perfil de implementação do Client Initiated Backchannel Authentication (CIBA) - ou Fluxo de Autenticação de Backchannel Iniciado pelo Cliente - como parte integrante da arquitetura de segurança do Open Finance Brasil.

Embora seja possível codificar um OpenID Provider e um Relying Party a partir dos primeiros princípios usando essa especificação, o principal público deste documento são as partes que já possuem uma implementação certificada no perfil [Financial-grade API: Client Initiated Backchannel Authentication Profile (FAPI-CIBA)](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e desejam obter a certificação para o programa Open Finance Brasil.

## **2\. Convenções Notacionais**

As palavras-chave "deve" (shall), "não deve" (shall not), "deveria" (should), "não deveria" (should not) e "pode" (may) presentes nesse documento devem ser interpretadas conforme as diretrizes descritas em [ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) observando a fseguinte equivalência:

-   "deve" => equivalente ao termo "shall" e expressa um requisito definido no documento (nas traduções é similar ao termo "must", que pode denotar um requisito externo ao documento);
    
-   "não deve" => equivalente ao termo "shall not" e também expressa um requisito definido no documento;
    
-   "deveria" e "não deveria"=> equivalente ao termo "should" e "should not" e expressa uma recomendação
    
-   "pode" => equivalente ao termo "may" indica uma permissão
    

Estas palavras-chave não são usadas como termos de dicionário, de modo que qualquer ocorrência delas deve ser interpretada como palavra‑chave normativa e não deve ser interpretada com seus significados de linguagem natural.

## **3\. Escopo**

Este documento especifica o método de:

1.  aplicações (softwares clientes) obterem tokens OAuth por meio de um fluxo de autenticação backchannel de forma apropriadamente segura para acesso aos dados de uma maneira que atenda aos requisitos do [Open Finance Brasil](https://www.in.gov.br/en/web/dou/-/resolucao-conjunta-n-1-de-4-de-maio-de-2020-255165055);
    
2.  aplicações (softwares clientes) que usam o OpenID Connect CIBA sugerirem a identidade do cliente em jornada.
    

Este documento é aplicável a todos os participantes do Open Finance Brasil que implementem fluxos CIBA no âmbito do ecossistema.

## **4\. Referências normativas**

Os seguintes documentos referenciados são indispensáveis para a adoção das especificações deste documento. Para referências datadas, apenas a edição citada se aplica. Para referências não datadas, deve-se aplicar a última edição do documento referenciado (incluindo quaisquer emendas).

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) - OpenID Connect Client Initiated Backchannel Authentication Core

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md) - OIDF FAPI WG Lodging Intent Working Paper

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

OFB-FAPI-BR – Open Finance Brasil Financial-grade API Security Profile

OFB-FAPI-BR-DCR - Open Finance Brasil Financial-grade API Dynamic Client Registration Profile

[OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0

[OIDC-Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0

[OIDC-Registration](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0

[RFC4648](https://tools.ietf.org/html/rfc4648) - The Base16, Base32, and Base64 Data Encodings

[RFC6749](https://tools.ietf.org/html/rfc6749) - The OAuth 2.0 Authorization Framework

[RFC6750](https://tools.ietf.org/html/rfc6750) - The OAuth 2.0 Authorization Framework: Bearer Token Usage

[RFC6819](https://tools.ietf.org/html/rfc6819) - OAuth 2.0 Threat Model and Security Considerations

[RFC7515](https://tools.ietf.org/html/rfc7515) - JSON Web Signature (JWS)

[RFC7519](https://tools.ietf.org/html/rfc7519) - JSON Web Token (JWT)

[RFC7591](https://tools.ietf.org/html/rfc7591) - OAuth 2.0 Dynamic Client Registration Protocol

[RFC7592](https://tools.ietf.org/html/rfc7592) - OAuth 2.0 Dynamic Client Registration Management Protocol

[RFC7636](https://tools.ietf.org/html/rfc7636) - Proof Key for Code Exchange by OAuth Public Clients

[RFC8414](https://tools.ietf.org/html/rfc8414) - OAuth 2.0 Authorization Server Metadata

[RFC8705](https://tools.ietf.org/html/rfc8705) - OAuth 2.0 Mutual TLS Client Authentication and Certificate Bound Access Tokens

## **5\. Símbolos e termos abreviados**

-   **API** \- Application Programming Interface (Interface de programação de aplicativo)
    
-   **DCR** \- Registro de cliente dinâmico
    
-   **FAPI** \- Financial-grade API
    
-   **HTTP** \- Protocolo de transferência de hipertexto
    
-   **JSR** \- Jornada Sem Redirecionamento
    
-   **MFA** \- Multi-Factor Authentication (Autenticação por Múltiplos Fatores)
    
-   **OIDF** \- OpenID Foundation
    
-   **REST** \- Representational State Transfer (Transferência de Estado Representacional)
    
-   **TLS** \- Transport Layer Security (Segurança da Camada de Transporte)
    

## **6\. Perfil de Segurança CIBA para o Open Finance Brasil**

### **6.1. Visão Geral**

O perfil de segurança do Open Finance Brasil especifica requisitos adicionais de segurança e identidade para recursos de API de alto risco protegidos pelo OAuth 2.0 Authorization Framework ([RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636)), pelos perfis Financial-grade API ([FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html), [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html)), pelo [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e por outras especificações relacionadas.

Este perfil descreve as provisões de segurança e requisitos funcionais para servidores de autorização e clientes que implementam CIBA no contexto do Open Finance Brasil, definindo, em especial:

-   o requisito de transmitir ao Cliente, de forma padronizada, o contexto de autenticação que foi executado por um OpenID Provider, permitindo o gerenciamento apropriado do risco de conduta do usuário pelo cliente;
    
-   a exigência de que os clientes indiquem, por meio de um identificador de consentimento ou de vínculo de dispositivo, o recurso que será utilizado para identificar o usuário em jornada como parte do fluxo CIBA.
    

Os requisitos deste perfil são adicionais e restritivos em relação às especificações [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html), e devem ser observados conjuntamente com OFB-FAPI-BR.

### **6.2. Servidor de Autorização**

#### **6.2.1. Conformidade básica**

O Servidor de Autorização CIBA:

-   Deve atender às disposições especificadas na cláusula 5.2.2 do [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html);
    
-   Deve estar em conformidade com os requisitos de segurança aplicáveis de OFB-FAPI-BR para servidores de autorização.
    

#### 6.2.2. **Modos de entrega CIBA**

O Servidor de Autorização CIBA:

-   Deve suportar o CIBA ping mode;
    
-   Deve exigir que os clientes se registrem, por meio de DCR/DCM, apenas para utilização do CIBA ping mode, conforme [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592) e OFB-FAPI-BR-DCR.
    
-   Não deve aceitar nem anunciar, em seu processo de registro dinâmico ou em sua configuração, outros modos de entrega de tokens ou notificações CIBA além do ping mode.
    

NOTA: Conforme estabelecido em [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html), clientes registrados para o ping mode estão implicitamente habilitados a utilizar o poll mode como mecanismo complementar. No contexto do Open Finance Brasil, o uso do poll mode é reservado exclusivamente como mecanismo de fallback para situações em que:

-   Houver suspeita ou evidência de falha na entrega da notificação de ping ao endpoint do Cliente;
    
-   O Cliente não tenha recebido a notificação dentro do prazo esperado, considerando as características da rede e os requisitos de disponibilidade estabelecidos em OFB-FAPI-BR;
    
-   Seja necessário garantir a continuidade da experiência do usuário em cenários de degradação técnica temporária.
    

O Cliente deve implementar mecanismos adequados de timeout e detecção de falhas na notificação antes de recorrer ao poll mode como fallback.

#### 6.2.3. Parâmetro login\_hint e identificação do usuário

O Servidor de Autorização CIBA:

-   Deve suportar o recebimento do parâmetro `login_hint` contendo o identificador de consentimento ou o identificador de vínculo de dispositivo, para identificar o usuário que precisa realizar a autenticação;
    
-   Deve utilizar o valor de `login_hint` para localizar, em seus registros internos, os dados necessários à identificação e autenticação do usuário associados ao consentimento ou vínculo informado;
    
-   Não deve exigir que o `login_hint` contenha dados pessoais diretamente identificáveis do usuário (como CPF, e‑mail ou número de telefone). O identificador deve ser opaco do ponto de vista do Cliente e representar apenas o consentimento ou o vínculo de dispositivo (JSR) estabelecido entre as partes.
    
-   Adicionalmente aos códigos de erro para o HTTP status 400 previstos em [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html), seção 13, o Servidor de Autorização CIBA no Open Finance Brasil deve adotar o seguinte código adicional:
    
    -   `invalid_login_hint`: deve ser retornado quando o valor enviado em `login_hint` for inválido, não puder ser interpretado pelo Servidor de Autorização ou não puder ser associado a um consentimento ou vínculo de dispositivo válido e ativo no contexto daquele Cliente.
        

O formato e as características do identificador de consentimento ou do identificador de vínculo de dispositivo devem ser definidos pelas regras de negócio e de segurança de cada instituição titular da conta, respeitadas as políticas do Open Finance Brasil.

#### 6.2.4. Parâmetro user\_code e registro de clientes

O Servidor de Autorização CIBA:

-   Não deve anunciar suporte ao parâmetro `user_code` em seus metadados de configuração (discovery).
    
-   Não deve aceitar requisições de registro ou de gerenciamento dinâmico de cliente (DCR/DCM) que incluam o parâmetro `backchannel_user_code_parameter` com valor `true`. Nesses casos, o Servidor de Autorização CIBA deve rejeitar a requisição de DCR/DCM com código de status HTTP 400 e erro `invalid_client_metadata`, conforme RFC7591, RFC7592 e OFB-FAPI-BR-DCR.
    
-   Não deve aceitar requisições de autorização CIBA que utilizem o parâmetro `user_code`. Caso o parâmetro `user_code`seja recebido em uma requisição CIBA, o Servidor de Autorização CIBA deve rejeitar a requisição com erro `invalid_request`, conforme CIBA-Core.
    

#### 6.2.5. Parâmetro binding\_message

O Servidor de Autorização CIBA:

-   Pode aceitar o parâmetro opcional `binding_message`, conforme definido em CIBA-Core e observadas as regras específicas aplicáveis ao produto, serviço ou jornada em questão.
    
-   A aceitação, validação, tratamento e eventual exibição do `binding_message` ao usuário devem ser definidos de forma específica nas regras aplicáveis a cada produto, serviço ou jornada do Open Finance Brasil.
    
-   `binding_message` não deve ser utilizada para transmitir dados pessoais diretamente identificáveis do usuário (por exemplo, CPF, e‑mail, número de telefone), dados sigilosos (incluindo senhas, códigos de autenticação, OTP), URLs ou informações de marketing e publicidade.
    
-   Quando aceita, `binding_message` deve ser tratada pelo Servidor de Autorização CIBA como informação auxiliar de contexto, com exibição opcional ao usuário, de acordo com as regras de experiência, segurança e negócio aplicáveis ao produto, serviço ou jornada correspondente.
    

#### 6.2.6. Parâmetro requested\_expiry e o prazo de validade da requisição de autenticação (expires\_in)

O Servidor de Autorização CIBA:

-   Não deve considerar o valor de `requested_expiry` eventualmente enviado pelo Cliente na requisição CIBA. Caso o parâmetro seja recebido, o Servidor de Autorização CIBA deve ignorá-lo.
    
-   Deve determinar o tempo de validade da requisição de autorização CIBA (`expires_in`) com base no prazo definido para a aprovação do consentimento ou do vínculo de dispositivo, conforme a regra específica do produto ou serviço.
    
-   Deve recusar tentativas de uso de `auth_req_id` fora desse intervalo de validade, retornando erro conforme definido em [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md).
    

#### 6.2.7. Tratamento de pedidos em casos de fraude ou segurança

A instituição titular da conta, atuando como Servidor de Autorização CIBA:

-   Pode negar novos pedidos de autenticação em casos de suspeita de fraude ou por razões de segurança, de acordo com suas políticas internas e com OFB-FAPI-BR;
    
-   Nesses casos, deve retornar ao Cliente um código de erro apropriado, conforme [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) (por exemplo, access\_denied ou outro erro permitido pelas especificações), evitando a exposição de informações sensíveis sobre os motivos da recusa.
    

**6.2.8. Notificações PING e idempotência**

O Servidor de Autorização CIBA:

-   Deve implementar mecanismos de retentativa de entrega da notificação PING ao Cliente, nos casos em que ocorram falhas temporárias de comunicação ou erros transitórios na chamada ao endpoint de notificação do Cliente.
    
-   Pode, em decorrência dessas retentativas, produzir múltiplas notificações PING referentes a um mesmo `auth_req_id`.
    

### **6.3. Cliente confidencial**

O Cliente confidencial que participa de fluxos CIBA no Open Finance Brasil deve atender aos seguintes requisitos adicionais aos estabelecidos em [OFB-FAPI-BR](data/references/guides/PT.md) e [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md).

#### 6.3.1. Escopo parametrizado (Lodging Intent)

O Cliente confidencial:

-   Deve suportar o escopo parametrizável ("parameterized scope") como definido no item 6.3.1 de [FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
-   Deve ser capaz de associar o identificador de consentimento emitido com escopo parametrizável ao parâmetro `login_hint` utilizado nas requisições CIBA subsequentes.
    

#### 6.3.2. Uso do login\_hint

O Cliente confidencial:

-   Deve enviar, nas requisições CIBA ao Servidor de Autorização, o parâmetro `login_hint` contendo o identificador de consentimento ou o identificador de vínculo de dispositivo acordado com a instituição titular da conta;
    
-   Deve tratar o valor de `login_hint` como um identificador opaco, não devendo inferir ou reconstruir a identidade civil do usuário a partir desse valor;
    
-   Não deve incluir, em `login_hint`, dados pessoais diretamente identificáveis do usuário, salvo disposição expressa em regulamento ou especificação complementar do Open Finance Brasil.
    

#### 6.3.3. Suporte a tokens de atualização

O Cliente confidencial:

-   Deve suportar o uso de tokens de atualização (refresh tokens), em conformidade com OFB-FAPI-BR e [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md).
    

#### 6.3.4. Suporte ao ping mode

O Cliente confidencial:

-   Deve ser capaz de operar no CIBA ping mode, em alinhamento com os requisitos do Servidor de Autorização descritos na seção 6.2.2;
    
-   Deve expor um endpoint de notificação compatível com o ping mode, devidamente protegido, de acordo com OFB-FAPI-BR, incluindo o uso de TLS conforme [BCP195](https://tools.ietf.org/html/bcp195) e autenticação mútua via certificado, conforme [RFC8705](https://tools.ietf.org/html/rfc8705);
    
-   Deve validar as notificações recebidas do Servidor de Autorização CIBA, incluindo a autenticidade da origem, a integridade da mensagem e a associação correta ao `auth_req_id` previamente emitido;
    
-   Deve, após o recebimento da notificação de ping, seguir o fluxo de token endpoint conforme [CIBA-Core](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) para obtenção dos tokens associados ao `auth_req_id`.
    
-   Deve ser capaz de receber múltiplas notificações PING referentes a um mesmo `auth_req_id` e tratá-las de forma idempotente, de modo que a execução repetida de processamento associado à mesma requisição de autenticação não produza efeitos de negócio duplicados ou inconsistentes.
    

#### 6.3.4.1 Fallback para o poll mode

O Cliente confidencial:

-   Não deve utilizar o poll mode como fluxo principal de obtenção de tokens no contexto do Open Finance Brasil.
    
-   Deve restringir o uso do poll mode a situações em que:
    
    -   houver suspeita ou evidência de falha na entrega da notificação de ping ao endpoint do client; ou
        
    -   a notificação de ping não tenha sido recebida dentro de um prazo operacionalmente adequado em relação ao valor de `expires_in` retornado pelo Servidor de Autorização CIBA.
        

Em todos os casos, o Cliente confidencial deve observar as regras de intervalo mínimo (interval) e demais requisitos definidos em CIBA-Core e FAPI-CIBA.

#### 6.3.5. Parâmetro user\_code e registro de clientes

O Cliente confidencial:

-   Não deve incluir o parâmetro `backchannel_user_code_parameter` com valor `true` em requisições de registro ou de gerenciamento dinâmico de cliente (DCR/DCM) encaminhadas ao Servidor de Autorização CIBA no contexto do Open Finance Brasil.
    
-   Não deve enviar o parâmetro `user_code` em requisições CIBA no contexto do Open Finance Brasil.
    

#### 6.3.6. Parâmetro binding\_message

O Cliente confidencial:

-   Pode enviar o parâmetro opcional `binding_message` para auxiliar na identificação do contexto da operação pelo usuário, observadas as regras específicas aplicáveis ao produto, serviço ou jornada em questão.
    
-   O envio do `binding_message` não implica sua aceitação, processamento ou exibição pelo Servidor de Autorização CIBA. A aceitação, validação, tratamento e eventual exibição do `binding_message` ao usuário devem observar as regras aplicáveis a cada produto, serviço ou jornada do Open Finance Brasil.
    
-   O `binding_message` não deve conter dados pessoais diretamente identificáveis do usuário (por exemplo, CPF, e‑mail, número de telefone), dados sigilosos (incluindo senhas, códigos de autenticação, OTP), URLs ou conteúdo de marketing e publicidade.
    
-   O `binding_message` deve observar os limites, políticas, formatos e restrições eventualmente estabelecidos para o produto, serviço ou jornada correspondente.
    

#### 6.3.7. Parâmetro requested\_expiry

O Cliente confidencial:

-   Não deve enviar o parâmetro `requested_expiry` em requisições CIBA no contexto do Open Finance Brasil.
    
-   Deve considerar o valor de `expires_in` retornado pelo Servidor de Autorização CIBA como a fonte de verdade para a validade da requisição CIBA e para o planejamento de qualquer fallback (incluindo uso eventual do poll mode).
    

#### **6.3.8. Registro dinâmico de clientes (DCR/DCM)**

O Cliente confidencial:

-   Deve se registrar junto ao Servidor de Autorização por meio de DCR/DCM, conforme [RFC7591](https://tools.ietf.org/html/rfc7591), [RFC7592](https://tools.ietf.org/html/rfc7592) e OFB-FAPI-BR-DCR;
    
-   Deve declarar, no processo de registro, suporte ao CIBA ping mode, em alinhamento com os requisitos estabelecidos na seção 6.2.2 deste documento;
    
-   Deve manter atualizados seus metadados de registro, incluindo os endpoints necessários para o ping mode e qualquer outra informação exigida por OFB-FAPI-BR-DCR e OFB-FAPI-BR.
    

## **7\. Considerações de segurança**

Os participantes devem apoiar todas as considerações de segurança especificadas em todas as cláusulas e subcláusulas de OFB-FAPI-BR e [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md), bem como as recomendações de segurança relacionadas ao OAuth 2.0 ([RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC6819](https://tools.ietf.org/html/rfc6819)), ao uso de JWS/JWT ([RFC7515](https://tools.ietf.org/html/rfc7515), [RFC7519](https://tools.ietf.org/html/rfc7519)) e ao uso seguro de TLS ([BCP195](https://tools.ietf.org/html/bcp195), [RFC8705](https://tools.ietf.org/html/rfc8705)).

## 8\. Considerações sobre compartilhamento de dados

Os participantes devem apoiar todas as considerações de compartilhamento de dados especificadas em OFB-FAPI-BR.
