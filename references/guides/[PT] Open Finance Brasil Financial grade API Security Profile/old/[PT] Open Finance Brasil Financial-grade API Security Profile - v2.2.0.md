# [PT] Open Finance Brasil Financial-grade API Security Profile - v2.2.0

13falsedefaultlisttrue

## Prefácio

This document is also avaiable in [English](file:///C:/wiki/spaces/DraftOF/pages/76283925)

A Associação Open Finance é responsável por criar padrões e especificações necessárias para atender aos requisitos e obrigações da Legislação do Open Finance do Brasil, conforme originalmente delineado pelo [Banco Central do Brasil](https://www.bcb.gov.br/content/config/Documents/BCB_Open_Banking_Communique-April-2019.pdf) e Conselho Monetário Nacional. É possível que alguns dos elementos deste documento estejam sujeitos a direitos autorais ou patenteados. A Associação Open Finance não se responsabiliza pela identificação de qualquer ou todos esses direitos.

O Perfil de Segurança do Open Finance Brasil (FAPI-BR) consiste nas seguintes partes:

-   Open Finance Brasil Financial-grade API Security Profile 2.2.0
    
-   Open Finance Brasil Dynamic Client Registration Profile 2.1.0
    

## 1\. Introdução

O Perfil de Segurança do Open Finance Brasil é uma implementação do perfil [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) que fornece diretrizes de implementação específicas para segurança e interoperabilidade que devem ser aplicadas as APIs expostas no ecossistema do Open Finance Brasil. O Perfil de Segurança do Open Finance Brasil é um subconjunto do perfil [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html), no entanto esse subconjunto não se refere a retirada de mecanismos de segurança do perfil original e sim a obrigatoriedade de utilização de determinadas características do mesmo visando a facilitação da interoperabilidade entre as instituições financeiras.

Este perfil descreve as capacidades e os recursos de segurança que devem ser oferecidos por servidores e clientes que são necessários para o ecossistema do Open Finance Brasil, definindo as medidas para mitigar ou endereçar:

-   ataques que abordam considerações de privacidade identificadas na cláusula 9.1 de [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html).
    
-   o requisito de concessão de acesso granular a recursos, com vistas à minimização de dados;
    
-   o requisito de informar sobre o contexto da autenticação do usuário (claim Authentication Context Request - acr) que foi realizada por um Provedor OpenID, com vistas a favorecer o adequado gerenciamento do risco decorrente do acesso do usuário;
    

Este perfil também especifica o método para os aplicativos:

-   obterem de maneira segura os tokens OAuth necessários para acesso a dados críticos de acordo com os requisitos do [Open Finance Brasil](data/references/Resolução_Conjunta_1.md);
    
-   utilizarem o OpenID Connect para identificação do usuário do Open Finance; e
    
-   utilizarem o OpenID Connect para afirmar a identidade do cliente.
    

Embora seja possível codificar do início um servidor de autorização que atenda ao Perfil de Segurança do Open Finance Brasil, o público alvo desta especificação são os provedores que já possuem uma implementação certificada do [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) e desejam realizar as adequações necessárias para obter a certificação para o Perfil de Segurança do Open Finance Brasil.

Estas partes são destinados a serem usados com [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [OIDC](https://openid.net/specs/openid-connect-core-1_0.html), [FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) e [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html).

## 2\. Convenções Notacionais

As palavras-chave "deve" (shall), "não deve" (shall not), "deveria" (should), "não deveria" (should not) e "pode" (may) presentes nesse documento devem ser interpretadas conforme as diretrizes descritas em [ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) observando seguinte equivalência:

-   "deve" => equivalente ao termo "shall" e expressa um requerimento definido no documento (nas traduções é similar ao termo "must", que pode denotar um requerimento externo ao documento);
    
-   "não deve" => equivalente ao termo "shall not" e também expressa um requerimento definido no documento;
    
-   "deveria" e "não deveria"=> equivalente ao termo "should" e "should not" e expressa uma recomendação
    
-   "pode" => equivalente ao termo "may" indica uma permissão
    

Estas palavras-chave não são usadas como termos de dicionário, de modo que qualquer ocorrência deles deve ser interpretada como palavras-chave e não devem ser interpretados com seus significados de linguagem natural.

## 3\. Referências normativas

Os seguintes documentos referenciados são indispensáveis para a adoção das especificações deste documento. Para referências datadas, apenas a edição citada se aplica. Para referências não datadas, deve-se aplicar a última edição do documento referenciado (incluindo quaisquer emendas).

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md) - OIDF FAPI WG Lodging Intent Working Paper

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

[JAR](https://tools.ietf.org/html/draft-ietf-oauth-jwsreq) - OAuth 2.0 JWT Secured Authorization Request

[OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0

[OIDC-Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0

[OIDC-Registration](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0

[PAR](https://tools.ietf.org/html/draft-ietf-oauth-par) - OAuth 2.0 Pushed Authorization Requests

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

## 4\. Símbolos e termos abreviados

-   **API** \- Application Programming Interface (Interface de programação de aplicativo)
    
-   **DCR** \- Registro de cliente dinâmico
    
-   **FAPI** \- Financial-grade API
    
-   **HTTP** \- Protocolo de transferência de hipertexto
    
-   **MFA** \- Multi-Factor Authentication (Autenticação por Múltiplos Fatores)
    
-   **OIDF** \- OpenID Foundation
    
-   **REST** \- Representational State Transfer (Transferência de Estado Representacional)
    
-   **TLS** \- Transport Layer Security (Segurança da Camada de Transporte)
    

## 5\. Perfil de Segurança para o Open Finance Brasil

### 5.1. Servidor de Autorização

Para atender às considerações de privacidade identificadas no Open Finance Brasil, que não foram totalmente abordadas na especificação final [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html), e para suportar o gerenciamento de clientes no ecossistema Open Finance Brasil, o Perfil de Segurança do Open Finance Brasil estabelece que o Servidor de Autorização deve suportar as disposições especificadas na cláusula 5.2.2 de [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html).

Além disso, ele deve:

1.  deve realizar a autenticação do cliente utilizando private\_key\_jwt;
    
2.  deve exigir requisições do tipo Pushed Authorization Requests (PAR);
    
3.  deve publicar metadados de descoberta (incluindo a do endpoint de autorização) por meio do documento de metadado especificado em [OIDC-Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) e [RFC8414](https://tools.ietf.org/html/rfc8414) (".well-known");
    
4.  deve suportar os parâmetros claims como definido no item 5.5 do [OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html);
    
5.  deve suportar o atributo acr "`urn:brasil:openbanking:loa2`" como definido no item 5.1.1.1;
    
6.  deveria suportar o atributo acr "`urn:brasil:openbanking:loa3`" como definido no item 5.1.1.1;
    
7.  deve implementar o endpoint _userinfo_ como definido no item 5.3 do [OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html);
    
8.  deve suportar o escopo parametrizável ("parameterized scope") como definido no item 6.3.1 de [FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
9.  pode suportar [FAPI-CIBA](https://bitbucket.org/openid/fapi/src/master/Financial_API_WD_CIBA.md);
    
10.  deve suportar _refresh tokens_;
     
11.  deve emitir _access tokens_ com o tempo de expiração entre 300 (mínimo) e 900 (máximo) segundos;
     
12.  deve suportar o valor “_code id\_token_” para o atributo _response\_type_;
     
13.  não deve permitir o recurso de rotação de _refresh tokens_;
     
14.  deve garantir que em caso de compartilhamento do Servidor de Autorização para outros serviços, além do Open Finance, não divulgue e/ou possibilite o uso de métodos não certificados no ambiente do Open Finance;
     
15.  deve garantir que as configurações divulgadas aos demais participantes através do OpenID Discovery (indicado pelo arquivo de Well-Known cadastrado no Diretório) sejam restritos aos modos de operação aos quais a instituição se certificou;
     
16.  deve recusar requisições, para o ambiente do Open Finance, que estejam fora dos modos de operação ao qual a instituição certificou seu Servidor de Autorização;
     
17.  o tempo mínimo de expiração do `request_uri` deve ser de 120 segundos;
     
18.  deve recusar requisições que não apresentem o cabeçalho `x-fapi-interaction-id` em endpoints de recursos protegidos;
     
19.  deve exigir a utilização de Proof Key for Code Exchange (PKCE);
     
20.  deve exigir a utilização do _subject\_type_ “public”;
     
21.  deve exigir a utilização do _response\_mode_ “fragment”;
     
22.  _Deve emitir refresh\_tokens_ (JWT ou opaco) sem prazo de validade nos cenários onde o mesmo é necessário;
     
23.  deve garantir o uso único dos valores de `request_uri`no ponto de autorização.
     

**Nota 1:** consideram-se endpoints de recursos protegidos aqueles pertencentes às APIs de produtos que exigem autenticação, como, por exemplo, /consents, /resources, /accounts e /payments, entre outros. Não se enquadram nessa categoria os endpoints de segurança (como /authorize, /token, /introspect, /revocation e /register), nem os endpoints das APIs de dados abertos.

**Nota 2:** o servidor de autorização deve garantir o uso único dos valores de `request_uri` no ponto de autorização, não no ponto de carregamento de uma página de autorização. Essa exigência evita que comportamentos como pré-carregamento de URLs por agentes do usuário ou chamadas duplicadas (por exemplo, simultâneas para navegador e aplicativo da OP) resultem na invalidação indevida do `request_uri`.

#### **5.1.1. ID Token**

O Servidor de Autorização deve suportar as disposições especificadas na cláusula 5.2.2.1 de [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) e além disso, para atender a requisitos específicos do Perfil de Segurança do Open Finance Brasil, ele deve:

1.  deve obrigatoriamente criptografar o _id token_ nos momentos de callback e chamada do endpoint de token;
    
2.  para a criptografia do _id token_ deve ser utilizada chave do tipo _enc_ disponível no JWKS informado no parâmetro _jwks\_uri_ do registro do cliente (DCR). O _kid_ da chave utilizada para a criptografia do _id token_ deve ser indicada no atributo _kid_ do cabeçalho do documento JWT;
    
3.  deve sempre incluir a claim acr no _id token_. O valor do claim acr deve ser um dos valores permitidos conforme definido na sessão Contextos de autenticação (acr);
    
4.  O uso de outros cabeçalhos para indicação da chave utilizada, como x5u, x5c, jku ou jkw é vetado conforme definido na cláusula 2 [OIDC-Core](https://openid.net/specs/openid-connect-core-1_0.html).
    

##### 5.1.1.1. Contextos de autenticação (acr) - "urn:brasil:openbanking:loa2" ou "urn:brasil:openbanking:loa3"

Esse perfil define _urn:brasil:openbanking:loa2 (LoA2)_ e _urn:brasil:openbanking:loa3_ (LoA3) como novas classes de "Authentication Context Request" (ACR)

-   LoA2: mecanismo de autenticação com a adoção de um único fator
    
-   LoA3: mecanismo de autenticação com múltiplos fatores de autenticação
    

A seguinte orientação deve ser observada para o mecanismo de autenticação das APIs do Open Finance Brasil:

-   De acordo com o Art. 17 da Resolução Conjunta nº 01, as instituições devem adotar procedimentos e controles para autenticação de cliente compatíveis com os aplicáveis ao acesso a seus canais de atendimento eletrônicos.
    
-   Em observância à regulação em vigor, sugere-se que:
    
    -   Para a autenticação do usuário em autorizações de acessos às APIs de compartilhamento de dados, os servidores de autorização deveriam adotar, no mínimo, método compatível com LoA2; e
        
    -   Para a autenticação do usuário em autorizações de acessos às API's de iniciação de transação de pagamento ou contratação de serviço/produto, os servidores de autorização deveriam adotar método de autenticação compatível com LoA3 ou superior.
        

Em todos os casos, a adoção de mecanismo de autenticação mais rigoroso (LoA3 ou superior) fica a critério da instituição transmissora/detentora de conta, de acordo com sua avaliação de riscos e de forma compatível com os mecanismos habitualmente utilizados.

Esclarecimentos adicionais sobre fatores de autenticação

São fatores de autenticação:

-   Aquilo que você conhece, como uma senha ou frase secreta
    
-   Aquilo que você tem, como um token, smartcard ou dispositivo
    
-   Aquilo que "você é", ou seja, autenticação condicionada a apresentação de uma característica física exclusivamente sua, como a validação por biometria
    

Para realizar autenticação por múltiplos fatores (MFA) é necessário que o usuário apresente, ao menos, dois diferentes fatores dos listados acima. Um mesmo fator usado mais de uma vez - por exemplo, a apresentação de suas senhas que ele conhece - não pode ser aceito como MFA.

#### **5.1.2. Clarificações sobre a "sub" Claim**

Este perfil usa a definição oficial encontrada em: Analise requisitos de criptografia ID\_TOKEN. Isso significa que o sub é um identificador nunca transferido ou alterado para o usuário final dentro da emissora (detentora/transmissora).

#### 5.1.3 Escopos obrigatórios no endpoint de descoberta (well-known)

O servidor de autorização, contidos em organizações que possuem a role DADOS, deve obrigatoriamente declarar os escopos abaixo em seu endpoint de descoberta (well-known), independentemente se a instituição forneça ou não os produtos referentes aos escopos abaixo listados:

-   invoice-financings
    
-   financings
    
-   loans
    
-   unarranged-accounts-overdraft
    
-   bank-fixed-incomes
    
-   credit-fixed-incomes
    
-   variable-incomes
    
-   treasure-titles
    
-   funds
    
-   exchanges
    

Os escopos não listados acima devem ser declarados caso a instituição forneça produtos referentes aos mesmos (ex: accounts, payments, etc…).

### 5.2. Cliente confidencial

Cliente confidencial é todo cliente criado através de um método seguro e que possua credenciais específicas de acesso. No ecossistema do Open Finance Brasil, clientes confidenciais são cliente que foram criados através do DCR (Dynamic Client Registration). Um cliente confidencial deve atender as disposições especificadas na cláusula 5.2.3 de [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) e além disso, para atender a requisitos específicos do Perfil de Segurança do Open Finance Brasil, ele deve:

1.  deve suportar objetos de solicitação criptografados;
    
2.  deve suportar solicitações de autorização _PAR_ (pushed authorization requests);
    
3.  deve suportar o escopo parametrizável ("parameterized scope") como definido no item 6.3.1 de [FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md);
    
4.  deve suportar _refresh tokens_;
    
5.  não deve incluir um valor específico na claim _acr_;
    
6.  deve definir a claim _acr_ como _essential_;
    
7.  deve suportar o método de autenticação _private\_key\_jwt_;
    
8.  não deve permitir o recurso de rotação de _refresh tokens_;
    
9.  deve enviar o cabeçalho `x-fapi-interaction-id` em endpoints de recursos protegidos.
    

## 6\. Considerações de segurança

Os participantes devem apoiar todas as considerações de segurança especificadas na cláusula 8 [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) e o [Manual de Segurança de Banco Central do Brasil](data/references/Instrução_Normativa_BCB_305.md).

O ICP Brasil emite certificados RSA x509 somente, portanto, para simplificar, a seção remove o suporte para algoritmos EC e exige que apenas algoritmos de criptografia recomendados pela IANA sejam usados.

### 6.1. Considerações sobre assinatura do conteúdo de mensagens (JWS)

Para garantir a integridade e o não-repúdio das informações tramitadas em API's sensíveis e que indicam essa necessidade na sua documentação, deve ser adotado a estrutura no padrão JWS definida na [RFC7515](https://tools.ietf.org/html/rfc7515) e que inclui:

-   Cabeçalho (JSON Object Signing and Encryption - JOSE Header), onde se define o algoritmo utilizado e inclui informações sobre a chave pública ou certificado que podem ser utilizadas para validar a assinatura;
    
-   Payload (JWS Payload): conteúdo propriamente dito e detalhado na especificação da API;
    
-   Assinatura digital (JWS Signature): assinatura digital, realizada conforme parâmetros do cabeçalho.
    

1.  Cada elemento acima deve ser codificado utilizando o padrão Base64url [RFC4648](https://tools.ietf.org/html/rfc4648#section-5) e, feito isso, os elementos devem ser concatenados com "." (método JWS Compact Serialization, conforme definido na [RFC7515](https://tools.ietf.org/html/rfc7515)).
    
2.  O payload das mensagens (requisição JWT e resposta JWT) assinadas devem incluir as seguintes claims presentes na [RFC7519](https://openbanking-brasil.github.io/specs-seguranca/JWT):
    

-   aud (na requisição JWT): o Provedor do Recurso (p. ex. a instituição detentora da conta) deverá validar se o valor do campo aud coincide com o endpoint sendo acionado;
    
-   aud (na resposta JWT): o cliente da API (p. e. instituição iniciadora) deverá validar se o valor do campo aud coincide com o seu próprio organisationId listado no diretório;
    
-   iss (na requisição JWT e na resposta JWT): o receptor da mensagem deverá validar se o valor do campo iss coincide com o organisationId do emissor;
    
-   jti (na requisição JWT e na resposta JWT): o valor do campo jti deverá ser preenchido com o UUID definido pela instituição de acordo com a \[RFC4122\] usando o versão 4;
    
-   iat (na requisição JWT e na resposta JWT): o valor do campo iat deverá ser preenchido com horário da geração da mensagem e de acordo com o padrão estabelecido na [RFC7519](#) para o formato NumericDate.
    
-   cty (na requisição JWT e na resposta JWT): o valor do campo cty deverá ser preenchido caso as operações de assinatura ou criptografia aninhadas não sejam empregadas, o uso desse parâmetro de cabeçalho não é recomendado. No caso de assinatura aninhada ou criptografia ser empregada, este parâmetro de cabeçalho deve estar presente; neste caso, o valor deve ser "JWT", para indicar que um JWT aninhado é transportado neste JWT. Embora os nomes dos tipos de mídia não diferenciem maiúsculas de minúsculas, é recomendável que "JWT" sempre seja escrito com caracteres maiúsculos para compatibilidade com implementações herdadas.
    

1.  O content-type HTTP das requisições e respostas com mensagens JWS deve ser definido como: "application/jwt".
    
2.  No cabeçalho JOSE deve constar os seguintes atributos:
    

-   alg - deve ser preenchido com o valor PS256";
    
-   kid - deve ser obrigatoriamente preenchido com o valor do identificador da chave utilizado para a assinatura;
    
-   typ - deve ser preenchido com o valor JWT;
    
-   Em caso de erro na validação da assinatura pelo Provedor do Recurso a API deve retornar mensagem de erro HTTP com status code 400 e a resposta deve incluir na propriedade code do objeto de resposta de erro especificado na API (ResponseError) a indicação da falha com o conteúdo BAD\_SIGNATURE.
    
-   Erros na validação da mensagem recebida pela aplicação cliente (p. ex. iniciador de pagamento) devem ser registrados e o Provedor do Recurso (p. ex. instituição detentora de conta) deve ser notificado.
    

1.  O receptor deve validar a consistência da assinatura digital da mensagem JWS exclusivamente com base nas informações obtidas do diretório, ou seja, com base nas chaves publicadas no JWKS da instituição no diretório.
    
2.  As assinaturas devem ser realizadas com uso do certificado digital de assinatura especificado no Padrão de Certificados Open Finance Brasil;
    
3.  A claim iat deve ser numérica no formato Unix Time GMT+0 com tolerância de +/- 60 segundos;
    
4.  A claim do jti deve ser única para um clientId dentro de um intervalo de tempo de 86.400 segundos (24h), não podendo ser reutilizada neste período. Em caso de reutilização, deverá ser retornado o código de erro HTTP 403. Demais casos seguir instrução da RFC 6749, item 5.2;
    

### 6.2. Considerações sobre algoritmos de assinatura

Para JWS, clientes e servidores de autorização devem usar o algoritmo PS256;

### 6.3. Considerações de algoritmo de criptografia

Para JWE, clientes e servidores de autorização devem usar RSA-OAEP com A256GCM

### 6.4. Considerações sobre o uso seguro do Transport Layer Security

Para TLS, endpoints do Servidor de Autenticação e endpoints do Servidor de Recursos usados diretamente pelo cliente:

1.  devem suportar TLS\_ECDHE\_RSA\_WITH\_AES\_128\_GCM\_SHA256
    
2.  devem suportar TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384
    
3.  As funcionalidades "TLS Session Resumption" e "TLS Renegotiation" devem ser desabilitadas
    

## 7\. Considerações sobre o escopo parametrizável

Os mecanismos existentes para gerenciar adequadamente o acesso aos recursos definidos em [RFC6749](https://tools.ietf.org/html/rfc6749) são insuficientes para atender aos requisitos de um ecossistema de compartilhamento de dados moderno. Utilizar strings de escopo estático não fornece aos consumidores controle de granularidade suficiente para controlar o compartilhamento de dados ou gerenciamento de recursos com terceiros. O Open Finance Brasil optou por implementar o escopo parametrizável ([FAPI-LIP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md)) associado a APIs de consentimento/vínculo para gerenciar o acesso granular aos recursos.

### 7.1. Definição de Escopo de Consentimento Dinâmico

Este perfil define o escopo dinâmico do OAuth 2.0 da seguinte maneira:

-   string “_consent_”, “_recurring-consent_” ou “enrollment”; e
    
-   delimitador de dois pontos “:”; e
    
-   Consent Resource Id retornado por uma criação bem-sucedida do recurso a ser concedido (ex: consent, recurring-consent, enrollment)
    

O Consent Resource Id:

-   deve incluir caracteres seguros para url;
    
-   deve ser “namespaced”;
    
-   deve ter propriedades de um [Nonce](https://openid.net/specs/openid-connect-core-1_0.html#NonceNotes);
    

Devido as características do Consent Resource ID e por facilidade de implementação, muitas instituições optam por utilizar uma chave UUIDv4 como Consent Resource ID, no entanto isso não é uma regra e cada instituição pode optar por outros métodos desde que sejam respeitadas as regras acima apresentadas e também definidas nas especificações de cada API.

#### 7.1.1. Exemplo de escopo de consentimento dinâmico

Considerando que a instituição transmissora/detentora seja o Banco Exemplo e que a mesma esteja utilizando UUIDv4 como Consent Resource ID, os consentimentos/consentimentos recorrentes/vínculos de dispositivo criados contra esta instituição teriam o seguinte formato, respectivamente:

-   consent:urn:bancoexemplo:830ce3c6-e9e7-4800-ae93-3e9b29b470f1
    
-   recurring-consent:urn:bancoexemplo:c9a8a741-39a6-4014-bb75-e05934f9d711
    
-   enrollment:urn:bancoexemplo:eb093d20-ccc5-4242-a271-6658f6663712
    

## 8\. Ciclo de vida do consentimento

O consentimento é um objeto de negócio fundamental, fortemente vinculado aos artefatos de segurança (refresh e access tokens). No entanto, seu ciclo de vida deve ser gerenciado de forma independente, através de sua própria máquina de estados. As especificações funcionais da API publicadas pelo Open Finance Brasil definem as transições de estado, os comportamentos esperados e as condições de erro dos recursos REST protegidos por este perfil, garantindo o controle adequado sobre o ciclo de vida do consentimento.

Os requisitos a seguir visam instruir sobre o comportamento do Servidor de Autorização (AS) em relação ao ciclo de vida do consentimento, assegurando que as práticas de autorização estejam alinhadas com as expectativas normativas e a segurança de todo o ecossistema.

### 8.1. Servidor de autorização

Além dos requisitos descritos nas disposições de segurança do Open Finance Brasil, o Servidor de Autorização

1.  deve apenas emitir refresh\_tokens quando vinculados a um consentimento ativo e válido;
    
    1.  Não deve emitir refresh\_token quando o consentimento estiver no status “CONSUMED” (para serviços de pagamentos);
        
    2.  Deve emitir um access\_token por meio de um grant\_type do tipo client credentials no status “CONSUMED” (para serviços de pagamentos).
        
    3.  Em uma jornada otimizada, deve emitir refresh\_tokens enquanto ao menos um dos consentimentos vinculados estiver ativo e válido.
        
2.  só deve compartilhar o acesso aos recursos quando apresentado access\_token vinculado a um consentimento ativo e com o status "AUTHORISED“. Para tokens gerados com o scope: payments ou recurring-payments_, o_ status do consentimento não será validado;
    
    1.  No cenário de recebimento de token inválido, deve ser retornado status code 401.
        
3.  deve revogar os refresh tokens e, quando aplicável, os access tokens quando o Consentimento (Consent Resource) relacionado for apagado;
    
    1.  Em uma jornada otimizada, deve realizar a revogação dos refresh\_tokens e access\_tokens apenas se ambos os consentimentos vinculados forem revogados.
        
4.  deve garantir que os access tokens são emitidos com os scopes necessários para permitir acesso aos dados especificados em elemento Permission do Consentimento (Consent Resource Object) relacionado;
    
5.  não deve rejeitar pedido de autorização com scopes além do necessário para permitir acesso a dados definidos em elemento Permission do Consentimento (Consent Resource Object) relacionado;
    
6.  pode reduzir o escopo solicitado para um nível que seja suficiente para permitir o acesso aos dados definidos em elemento Permission do Consentimento (Consent Resource Object) relacionado;
    
7.  deve manter registros sobre o histórico dos consentimento para permitir a adequada formação de trilhas de auditoria em conformidade com a regulação em vigor;
    
8.  deve retornar falha na autenticação e o código de retorno access\_denied no parâmetro erro (como especificado na seção 4.1.2.1 da [RFC6749](https://tools.ietf.org/html/rfc6749)) caso o CPF do usuário autenticado não seja o mesmo indicado no elemento loggedUser do Consentimento (Consent Resource Object);
    
9.  deve retornar falha na autenticação e o código de retorno access\_denied no parâmetro erro (como especificado na seção 4.1.2.1 da [RFC6749](https://tools.ietf.org/html/rfc6749)) caso o elemento businessEntity não tenha sido preenchido no Consentimento (Consent Resource Object) relacionado e o usuário tenha selecionado ou se autenticado por meio de credencial relacionada à conta do tipo Pessoa Jurídica (PJ);
    
10.  deve condicionar a autenticação ou seleção de contas do tipo PJ à consistência entre o CNPJ relacionado à(s) conta(s) e o valor presente no elemento businessEntity do Consentimento (Consent Resource Object). Em caso de divergência deve retornar falha na autenticação e o código de retorno _access\_denied_ no parâmetro erro (como especificado na seção 4.1.2.1 da [RFC6749](https://tools.ietf.org/html/rfc6749));
     
11.  deve emitir _refresh\_token_ com validade não inferior à validade do consentimento ao qual está relacionado, respeitado os demais critérios acima.
     

### 8.2. Cliente confidencial

Além dos requisitos descritos nas disposições de segurança do Open Finance Brasil, o Cliente Confidencial

1.  deve, sempre que possível, revogar e cessar o uso de refresh e de access tokens vinculados a um consentimento (Consent Resource Object) que foi excluído;
    
2.  deve excluir consentimentos (Consent Resource Objects) que estão expirados.
    

## Appendix A. Avisos

Copyright (c) 2025 Associação Open Finance Brasil

A Associação Open Finance concede a qualquer Colaborador, desenvolvedor, implementador ou outra parte interessada uma licença de direitos autorais mundial não exclusiva, livre de royalties para reproduzir, preparar trabalhos derivados, distribuir, executar e exibir, estes Implementadores Rascunho ou Especificação Final exclusivamente para fins de (i) desenvolver especificações e (ii) implementar Rascunhos de Implementadores e Especificações Finais com base em tais documentos, desde que a atribuição seja feita à Associação Open Finance como a fonte do material, mas que tal atribuição o faça não indica endosso da Associação Open Finance.

A tecnologia descrita nesta especificação foi disponibilizada a partir de contribuições de várias fontes, incluindo membros da OpenID Foundation, do Grupo de Trabalho de Segurança do Open Finance Brasil e outros. Embora a Associação Open Finance tenha tomado medidas para ajudar a garantir que a tecnologia esteja disponível para distribuição, ela não toma posição quanto à validade ou escopo de qualquer propriedade intelectual ou outros direitos que possam ser reivindicados como pertencentes à implementação ou uso do tecnologia descrita nesta especificação ou até que ponto qualquer licença sob tais direitos pode ou não estar disponível; nem representa que fez qualquer esforço independente para identificar tais direitos. A Associação Open Finance e os contribuidores desta especificação não oferecem (e por meio deste expressamente se isentam de quaisquer) garantias (expressas, implícitas ou de outra forma), incluindo garantias implícitas de comercialização, não violação, adequação a uma finalidade específica ou título, relacionados a esta especificação, e todo o risco quanto à implementação desta especificação é assumido pelo implementador. A política de Direitos de Propriedade Intelectual do Open Finance Brasil exige que os contribuidores ofereçam uma promessa de patente de não fazer valer certas reivindicações de patentes contra outros contribuidores e implementadores. A Associação Open Finance convida qualquer parte interessada a trazer à sua atenção quaisquer direitos autorais, patentes, pedidos de patentes ou outros direitos de propriedade que possam abranger a tecnologia que possa ser necessária para praticar esta especificação.

## Author's Address

Associação Open Finance - GT Segurança

Email: [gt-seguranca@openfinancebrasil.org.br](mailto:gt-seguranca@openfinancebrasil.org.br)

URI: [https://openfinancebrasil.org.br](https://openfinancebrasil.org.br/)
