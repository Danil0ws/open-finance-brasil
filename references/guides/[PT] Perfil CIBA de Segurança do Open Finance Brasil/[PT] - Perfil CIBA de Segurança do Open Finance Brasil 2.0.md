# [PT] - Perfil CIBA de Segurança do Open Finance Brasil 2.0

## Introdução

O padrão de API de nível financeiro fornece um perfil para OAuth 2.0 adequado para uso em serviços financeiros. O método OAuth é um padrão utilizado pelo cliente para validar o dono do recurso em um servidor de autorização usando um redirecionamento HTTP. As partes 1 e 2 desta especificação oferecem suporte a esse modelo de interação e são adequadas para casos de uso em que o proprietário do recurso está interagindo com o cliente em um dispositivo que ele controla que tem um navegador da Web. No entanto, há muitos casos de uso para iniciar pagamentos em que o proprietário do recurso não está interagindo com o cliente dessa maneira. Por exemplo, o proprietário do recurso pode querer autorizar um pagamento em um terminal de "ponto de venda" em uma loja ou posto de combustível.

Este documento aborda o perfil [CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) (Client Initiated Backchannel Authentication) ou Fluxo de Autenticação de Backchannel Iniciado pelo Cliente OpenID Connect que oferece suporte a esse método de interação desacoplada. A especificação CIBA permite que um cliente que obtenha conhecimento de um identificador para o usuário obtenha tokens do servidor de autorização. O consentimento do usuário é dado no Dispositivo de Autenticação do usuário mediado pelo servidor de autorização. Este documento traça o perfil da especificação CIBA para alinhá-lo com as outras partes do FAPI e fornecer recomendações de segurança para seu uso com APIs que exigem segurança de nível financeiro.

Embora seja possível codificar um OpenID Provider e um Relying Party a partir dos primeiros princípios usando essa especificação, o principal público dessa especificação são as partes que já possuem uma implementação certificada [de API de nível financeiro: Client Initiated Backchannel Authentication Profile](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e desejam obter a certificação para o programa Brasil Open Finance.

**Convenções Notacionais**

As palavras-chave "deve", "não deve", "deveria", "não deveria", "pode" e "opcional" neste documento devem ser interpretadas como descrito na [Parte 2 da Diretiva ISO](https://www.iso.org/sites/directives/current/part2/index.xhtml). Essas palavras-chave não são usadas como termos do dicionário, de modo que qualquer ocorrência delas deve ser interpretada como palavras-chave e não deve ser interpretada com seus significados de linguagem natural.

1.  **Escopo**
    

Este documento especifica o método de:

1.  aplicações para obter tokens OAuth por meio de um fluxo de autenticação backchannel de forma apropriadamente segura para acesso de maior risco aos dados de uma maneira que atenda aos requisitos do [Open Finance Brasil](https://www.in.gov.br/en/web/dou/-/resolucao-conjunta-n-1-de-4-de-maio-de-2020-255165055);
    
2.  aplicativos que usam o OpenID Connect CIBA para sugerir a identidade do cliente.
    

Este documento é aplicável a todos os participantes do Open Finance no Brasil.

2.  **Referências normativas**
    

Os seguintes documentos referenciados são indispensáveis para a aplicação deste documento. Para referências datadas, aplica-se apenas a edição citada. Para referências não datadas, aplica-se a última edição do documento referenciado (incluindo quaisquer alterações).

[ISODIR2](https://www.iso.org/sites/directives/current/part2/index.xhtml) - ISO/IEC Directives Part 2

[RFC6749](https://tools.ietf.org/html/rfc6749) - The OAuth 2.0 Authorization Framework

[RFC6750](https://tools.ietf.org/html/rfc6750) - The OAuth 2.0 Authorization Framework: Bearer Token Usage

[RFC7636](https://tools.ietf.org/html/rfc7636) - Proof Key for Code Exchange by OAuth Public Clients

[RFC6819](https://tools.ietf.org/html/rfc6819) - OAuth 2.0 Threat Model and Security Considerations

[RFC7515](https://tools.ietf.org/html/rfc7515) - JSON Web Signature (JWS)

[RFC7519](https://tools.ietf.org/html/rfc7519) - JSON Web Token (JWT)

[RFC7591](https://tools.ietf.org/html/rfc7591) - OAuth 2.0 Dynamic Client Registration Protocol

[RFC7592](https://tools.ietf.org/html/rfc7592) - OAuth 2.0 Dynamic Client Registration Management Protocol

[BCP195](https://tools.ietf.org/html/bcp195) - Recommendations for Secure Use of Transport Layer Security (TLS) and Datagram Transport Layer Security (DTLS)

[OIDC](https://openid.net/specs/openid-connect-core-1_0.html) - OpenID Connect Core 1.0 incorporating errata set 1

[FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[OIDD](https://openid.net/specs/openid-connect-discovery-1_0.html) - OpenID Connect Discovery 1.0 incorporating errata set 1

[OIDR](https://openid.net/specs/openid-connect-registration-1_0.html) - OpenID Connect Registration 1.0 incorporating errata set 1

[RFC8705](https://tools.ietf.org/html/rfc8705) - OAuth 2.0 Mutual TLS Client Authentication and Certificate Bound Access Tokens

[JARM](https://bitbucket.org/openid/fapi/src/master/Financial_API_JWT_Secured_Authorization_Response_Mode.md) - Financial-grade API: JWT Secured Authorization Response Mode for OAuth 2.0 (JARM)

[PAR](https://tools.ietf.org/html/draft-ietf-oauth-par) - OAuth 2.0 Pushed Authorization Requests

[JAR](https://tools.ietf.org/html/draft-ietf-oauth-jwsreq) - OAuth 2.0 JWT Secured Authorization Request

[FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html) - Financial-grade API Security Profile 1.0 - Part 1: Baseline

[FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html) - Financial-grade API Security Profile 1.0 - Part 2: Advanced

[FAPI-2-Baseline](https://bitbucket.org/openid/fapi/src/master/FAPI_2_0_Baseline_Profile.md) - Financial-grade API Security Profile 2.0 - Part 1: Baseline

[FAPI-2-Advanced](https://bitbucket.org/openid/fapi/src/master/FAPI_2_0_Advanced_Profile.md) - Financial-grade API Security Profile 2.0 - Part 2: Advanced

[FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) - Financial-grade API: Client Initiated Backchannel Authentication Profile

[FAPI-BR](data/references/guides/PT.md) – Open Finance Brasil Financial-grade API Security Profile 1.0

[CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) - OpenID Connect Client Initiated Backchannel Authentication Core

[LIWP](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md) - OIDF FAPI WG Lodging Intent Working Paper

[OBB-FAPI-DCR](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID3.html) - Open Finance Brasil Financial-grade API Dynamic Client Registration Profile 1.0

[RFC4648](https://tools.ietf.org/html/rfc4648) - The Base16, Base32, and Base64 Data Encodings

3.  **Termos e definições**
    

Para os fins deste documento, os termos definidos em [RFC6749,](https://tools.ietf.org/html/rfc6749) [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc6750), [OpenID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html), [CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e ISO29100 se aplicam.

4.  **Símbolos e termos abreviados**
    

**API** \- Application Programming Interface

**OFBIS** \- Open Finance Brasil Initial Structure

**CSRF** \- Cross Site Request Forgery

**DCR** \- Dynamic Client Registration

**FAPI** \- Financial-grade API

**HTTP** \- Hyper Text Transfer Protocol

**OIDF** \- OpenID Foundation

**REST** \- Representational State Transfer

**TLS** \- Transport Layer Security

**MFA** \- Multi-Factor Authentication

5.  **Perfil de Segurança do Brasil Open Banking**
    

**5.1. Introdução**

O perfil de segurança Open Finance Brasil especifica requisitos adicionais de segurança e identidade para recursos de API de alto risco protegidos pelo OAuth 2.0 Authorization Framework que consiste em [RFC6749](https://tools.ietf.org/html/rfc6749), [RFC6750](https://tools.ietf.org/html/rfc6750), [RFC7636](https://tools.ietf.org/html/rfc7636), [FAPI-1-Baseline](https://openid.net/specs/openid-financial-api-part-1-1_0.html), [FAPI-1-Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html), [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html) e outras especificações.

Este perfil descreve as provisões de segurança e recursos para um servidor e cliente que são necessárias para o programa Open Finance Brasil, definindo as medidas a serem abordadas:

-   o requisito de transmitir a Solicitação de Contexto de Autenticação que foi executada por um OpenID Provider a um Cliente para permitir o gerenciamento apropriado do risco de conduta do usuário pelo client.
    
-   a exigência de que os clientes afirmem um relacionamento de cliente pré-existente afirmando uma declaração de identidade do cliente como parte do fluxo CIBA.
    

**5.2. Open Banking Brasil CIBA Provisões de segurança**

**5.2.1. Introdução**

Open Finance Brasil tem requisito para adotar Cliente [Initiated Back Channel Authentication](https://openid.net/specs/openid-financial-api-ciba-ID1.html) como um meio de habilitar fluxos de trabalho de autenticação desacoplada. Além disso, esse perfil descreve o escopo específico, os requisitos de gerenciamento de clientes necessários para apoiar o ecossistema mais amplo do Open Finance Brasil.

Como um perfil do OAuth 2.0 Authorization Framework, este documento exige o seguinte para o perfil do Brasil Open Finance Security.

**5.2.2. Servidor de autorização**

O Servidor de Autorização deverá suportar as disposições especificadas na cláusula 5.2.2 do [Financial-grade API CIBA Security Profile 1.0](https://openid.net/specs/openid-financial-api-ciba-ID1.html)

Além disso, o Servidor de Autorização

1.  O tempo de aceitação do consentimento na solicitação de Autorização recebida via CIBA permanecerá o mesmo definido para o fluxo via Fluxo Híbrido, respeitando as configurações do produto utilizado;
    
2.  Deve assegurar que o ‘exp’ em todos os id\_tokens gerados têm pelo menos 180 dias de duração;
    
3.  O id\_token pode ser utilizado no pedido de autorização através do parâmetro “id\_token\_hint";
    
4.  Deve suportar CIBA poll mode;
    
5.  Não deve suportar CIBA push mode;
    
6.  Não deve suportar CIBA ping mode;
    
7.  O cancelamento do id\_token será realizado pela instituição titular da conta em casos de fraude ou por razões de segurança;
    
8.  Novos pedidos de autenticação poderão ser negados pela instituição titular da conta em casos de fraude ou por razões de segurança;
    
9.  Tabela de erro "HTTP 400 Bad Request":
    

-   invalid\_request: A solicitação indica que está faltando um parâmetro necessário, foi incluído um valor de parâmetro inválido, foi inclui um parâmetro mais de uma vez, contém mais de um parâmetro invalido ou está malformada.;
    
-   invalid\_scope: O escopo solicitado é inválido, desconhecido ou malformado;
    
-   expired\_id\_token\_hint: Caso enviado, o “hint” do id\_token fornecido na solicitação de autenticação não é válido porque já expirou;
    
-   unknown\_user\_id: O OpenID Provider não é capaz de identificar qual usuário final o Cliente deseja ser autenticado. Tanto por meio do “hint” fornecido na solicitação (id\_token\_hint) como pelos dados do consentimento;
    
-   unauthorized\_client: O Cliente não está autorizado a usar esse fluxo de autenticação.
    
-   invalid\_id\_token\_hint: Caso enviado, o id\_token é inválido e não pode ser usado no fluxo.
    

10\. Deve emitir ciba auth request acknowledgements (a resposta da consulta do auth\_req\_id) com prazo máximo respeitando  as configurações do produto utilizado, como definido para o fluxo via Hybrid Flow;

11\. Validação,  Payload Id\_token, pode ser validado, quando enviado, pelos parâmetros abaixo.

**Parâmetros**

**Validação**

Iss

O Servidor de Autorização deve estabelecer um identificador, ou conjunto de identificadores "iss" padrão para uso em transações CIBA. - O Servidor de Autorização não deve aceitar "iss" diferente de seu próprio identificador, ou conjunto de identificadores, padrão.

Sub

O Servidor de Autorização deve verificar se o identificador "sub" em questão já foi emitido para um cliente/conta, e se é válido dentro de seus requisitos.

Aud

O Servidor de Autorização não deve aceitar "aud" diferente do client\_id de onde se origina a solicitação de autorização para o fluxo CIBA.

exp

"exp" deve ser estabelecido de acordo com as políticas de risco da instituição Titular da Conta. O Servidor de Autorização não deve aceitar solicitações de autorização cuja data/hora seja maior que "exp".

iat

Sem validações específicas

auth\_time

Sem validações específicas

nonce

Sem validações específicas no Servidor de Autorização (AS)

acr

Se presente, o AS só deverá aceitar valores iguais ou superiores aos requisitos de autenticação do Titular para autorizar operações de pagamento.

amr

Se presente, o AS só deverá aceitar valores iguais ou superiores aos requisitos de autenticação do Titular para autorizar operações de pagamento.

azp

O Servidor de Autorização não deve aceitar "azp" diferente do client\_id de onde se origina a solicitação de autorização para o fluxo CIBA.

12\. Parâmetros para validação de assinatura

**Parâmetros**

**Descrição**

**Condição**

**Valores recomendados**

alg

O parâmetro "alg" (algoritmo) identifica o algoritmo criptográfico usado para proteger o JWS/JWE. O valor de Assinatura JWS será inválido se o valor "alg" não representar um algoritmo suportado ou se não houver nenhuma chave compatível para o uso do algoritmo associado à entidade que assinou digitalmente o conteúdo.

Obrigatório

PS256 ou PS512

kid

O parâmetro "kid" (Key ID) indica qual chave foi usada para proteger o JWS/JWE. Esse parâmetro permite que os remetentes sinalizem explicitamente uma alteração de chave para os destinatários. O valor "kid" DEVE ser uma cadeia de caracteres que diferencia maiúsculas de minúsculas. Quando usado com um JWK, o valor "kid" é usado para corresponder a um valor de parâmetro "kid" do JWK.

Obrigatório

x5t | x5t#S256

O parâmetro "x5t" ou "x5t#S256” (X.509 Certificate SHA-1/SHA-256 Thumbprint) é uma impressão digital SHA-1/SHA-256 codificada em base64url (hash) da codificação DER do certificado X.509 (RFC5280) correspondente à chave usada para assinar digitalmente o JWS.

Obrigatório

typ

O parâmetro "typ" (Type) é usado por aplicativos JWS para declarar o tipo de mídia (IANA. MediaTypes) deste JWS completo. Destina-se ao uso pelo aplicativo quando mais de um tipo de objeto pode estar presente em uma estrutura de dados de aplicativo que pode conter um JWS; O aplicativo pode usar esse valor para eliminar a ambiguidade entre os diferentes tipos de objetos que podem estar presentes.

Opcional

JWT

**5.2.3. Cliente confidencial**

Além disso, o cliente confidencial

1.  deve suportar o consentimento parametrizado do escopo de recursos do OAuth 2.0, conforme definido na cláusula 6.3.1 [OIDF FAPI WG Lodging Intent Pattern](https://bitbucket.org/openid/fapi/src/master/Financial_API_Lodging_Intent.md)
    
2.  deve suportar tokens de atualização.
    

6.  **Considerações de segurança**
    

Os participantes devem apoiar todas as considerações de segurança especificadas em todas as cláusulas e subcláusulas do \[FAPI-BR\] e [FAPI-CIBA](https://openid.net/specs/openid-financial-api-ciba-ID1.html).

7.  Considerações sobre compartilhamento de dados
    

Os participantes devem apoiar todas as considerações de compartilhamento de dados especificadas em \[FAPI-BR\].
