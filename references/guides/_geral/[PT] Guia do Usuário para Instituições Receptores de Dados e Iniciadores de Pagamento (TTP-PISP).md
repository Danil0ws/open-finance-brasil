# [PT] Guia do Usuário para Instituições Receptores de Dados e Iniciadores de Pagamento (TTP/PISP)

TPP - Third Party Provider PISP - Payment Initiation Service Provider

## 1\. Registrando um Aplicativo

Em um alto nível, as seguintes etapas principais são necessárias para integrar um novo aplicativo no ecossistema Open Finance Brasil.

1.  Cadastre sua organização no Diretório de Participantes (Interface do Usuário)
    
2.  Cadastre seu aplicativo no Diretório de Participantes (Interface do Usuário)
    
3.  Obtenha credenciais para sua aplicação junto à uma autoridade certificadora ICP-Brasi)(fora do escopo deste documento)
    
4.  Registre suas credenciais para o seu aplicativo no Diretório de Participantes (Interface do Usuário)
    
5.  Identifique provedores de informações de conta ou serviços de pagamento de interesse dos clientes de seu aplicativo, pesquisando o Diretório de Participantes (API)
    
6.  Registre seu aplicativo com cada provedor (API)
    

### 1.1. Diagrama de Sequência

![att\_4\_for\_157384798.png](images/att_4_for_157384798.png)

### 1.2. Visão Geral do Diretório

O framework de confiança do Open Finance Brasil fornece todos os serviços de descoberta necessários para que instituições participantes (receptoras e transmissoras de dados, iniciadoras de pagamento ou detentoras de contas) interajam entre si sem serem obrigadas a validarem a autenticidade de identidades, autorizações, Apps, APIs ou credenciais para acessos por aplicativos uns dos outros. Além disso, fornece um único registro de todas propostas ao consumidor sendo oferecidas no mercado e um único ambiente de controle para as autoridades regulatórias que concedem permissões para gerenciar participantes dentro do ecossistema.

O framework de confiança não tem visibilidade ou visão das interações que ocorrem entre instituições participantes receptoras (TPP) ou transmissoras (ASPSP) de dados. Ele é projetado para fornecer confiança e garantia de identidade e autorização apenas. Ele não se enquadra no fluxo de comunicação entre um consumidor e um provedor e não tem conhecimento ou visibilidade de quaisquer dados do cliente. Este modelo de framework de confiança é conhecido como confiança transitiva onde duas partes, um TPP e um ASPSP, concordam em confiar nas declarações e atestados de legitimidade uns dos outros emitidos por um provedor de confiança comum e, em seguida, prossigam comunicando o que quiserem, sem qualquer validação adicional onerosa ou outro tipo de verificação

### 1.3. Acessando o Diretório

Este guia do usuário assume que as organizações participantes já passaram pelo processo de iniciação com a Estrutura Inicial do Open Finance Brasil e já concluíram todas as integrações necessárias, processos de assinatura de contrato e inclusão de administrador individual.

![att\_2\_for\_157384798.png](images/att_2_for_157384798.png)

### 1.4. Criação de uma Nova Declaração de Software (SSA)

Uma declaração de software descreve um aplicativo inserido naquilo que pode ser considerado a ‘App Store’ do Open Finance Brasil. Este registro de aplicativo contém todas as informações necessárias para que um banco identifique tecnicamente e interaja com o aplicativo, além de conter todas as informações que auxiliam os clientes que estejam utilizando-o a confirmar sua legitimidade.

Um novo aplicativo ou declaração de software pode ser registrado fazendo logon no Diretório, navegando até ‘Software Statements’, clicando em ‘Criar Novo’ e preenchendo o formulário. O texto de ajuda é fornecido para cada campo da tela. Lembre-se de que a maioria dessas informações será exibida aos clientes pelos Bancos como parte do processo de redirecionamento ou autorização. Como tal, é importante que todas as URIs e descrições sejam relevantes para o público.

![att\_1\_for\_157384798.png](images/att_1_for_157384798.png)

#### 1.4.1. Atribuição de Funções Regulatórias de Software

Em um ecossistema de compartilhamento de dados complexo e diversificado, as funções regulatórias de uma organização podem mudar. Eles podem ser adicionados e revogados. Isso significa que o software adicionado ao Diretório pode receber permissão de ter zero (0) ou mais funções regulatórias. Um administrador pode atribuir a um determinado software todo e qualquer permissões que a organização proprietária do software pode ter.

Se uma organização perder uma função regulatória, todo software com essa função regulatória será revogado do ecossistema, portanto, é muito importante que um aplicativo receba apenas as funções de que realmente precisa para funcionar.

Um exemplo do mundo real disso poderia ser a Amazon. Ela possui dois aplicativos, ‘Amazon Accounting’ e ‘Amazon Prime’. A Amazon como organização é um DADOS e PISP autorizados e tem permissão para lidar com dados de clientes bem como fazer pagamentos via Open Finance Brasil. A ‘Amazon Accounting’ dever receber a função de domínio de DADOS e a ‘Amazon Prime’ deve receber uma função de domínio de PISP.

No futuro, se a Amazon perder a permissão regulatória para ser um iniciador de pagamento, apenas a aplicação ‘Amazon Prime’ seria removida do ecossistema. O App ‘Amazon Accounting’ do exemplo continuaria a funcionar sem problemas.

### 1.5. Criação e Upload de Certificados

#### 1.5.1. Sandbox

O serviço de Diretório do Open Finance Brasil inclui uma infraestrutura de chave pública que pode ser usada para criar certificados para os aplicativos sendo registrados no ambiente Sandbox. Basta selecionar certificados no menu e seguir as instruções.

O Diretório suporta vários certificados, tipos de chave e um comando e configuração openssl será disponibilizado como um exemplo. Depois de criar a solicitação de assinatura de certificado (Certificate Signing Request - CSR) para um certificado de “Transporte” e “Assinatura”, você pode enviá-los ao diretório para serem validados e transformados em certificados.

Lembre-se de seguir as práticas de gerenciamento de chaves de sua organização para a geração de certificados. Essas credenciais e chaves precisam ser manuseadas com cuidado. Um evento significativo de comprometimento de chave pode levar ao comprometimento dos dados do cliente.

#### 1.5.2. Produção

Os certificados para acesso e assinatura em ambiente de produção devem ser fornecidos pelo ICP Brasil. Os detalhes sobre os certificados e os requisitos para os certificados estão detalhados no [Padrão de Certificados Open Finance Brasil](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-certificate-standards-1_ID1.md).

#### 1.5.3. O que é um JWT, JWE, JWS e JWK {#JWT\_JWE\_JWS\_JWK)

Quando os certificados são carregados para o Diretório, o framework de confiança os anuncia em [JSON Web Key Sets](https://tools.ietf.org/html/rfc7517) com cada JSON Web Key (JWK) tendo um ‘KID’ ou um Key ID. Os JWKs, além de ter propriedades específicas que descrevem o algoritmo e os conjuntos de criptografia que eles suportam, também anunciam seu “uso”, que pode ser do tipo ‘enc’ para criptografia ou ‘sig’ para assinatura.

Essas chaves ‘sig’ e pares de chaves ‘enc’ são usadas em muitos lugares dentro do ecossistema do Open Finance Brasil para criptografar ou assinar dados usando os padrões definidos em [RFC 7519 JSON Web Token](https://tools.ietf.org/html/rfc7519), que deve ser lido em detalhes pelos desenvolvedores.

Tipos de JWT incluem

-   OpenID Connect Request Objects definidos em [Open ID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html)
    
-   OpenID Connect `id_token` definido em [Open ID Connect Core](https://openid.net/specs/openid-connect-core-1_0.html)
    

Entre muitos outros.

Esses JWTs podem ser criptografados também usando o JSON Web Encryption (JWE). Na maioria dos casos, as chaves que devem ser usadas para validar uma assinatura da Web JSON (JWS) ou a chave que foi usada para criptografar um JWE são geralmente publicadas como uma JSON Web Key em um JSON Web Key Set com a referência à chave que está sendo carregada no campo de cabeçalho ‘kid’ (Key ID).

**Exemplo de Request Object JWT assinado**

O exemplo acima é apresentado decodificado logo abaixo. No cabeçalho está incluso o atributo ‘kid’ (id da chave) com o valor `PWAi5ruQcHfzPzq2JFdpY7nAUh6LzTTQtDBUpOM37JQ`, que pode ser localizado no JSON Web KeySet para este cliente [aqui](https://keystore.sandbox.directory.openbankingbrasil.org.br/74e929d9-33b6-4d85-8ba7-c146c867a817/1509a662-6b3a-4cb8-b7c0-ffb6e596eb0d/application.jwks)

O JWK público do JWKS retirado da uri fornecido anteriormente

A chave privada que foi usada para criar o JWS

Se quiser conhecer um pouco mais e exercitar, visite o site [JWT-IO](https://jwt.io/) e conheça um pouco mais.

## 2\. Interagindo com as APIs de Serviços de Confiança

Quando um aplicativo é registrado no Diretório, o serviço central usa os metadados e certificados fornecidos para criar para o software um cliente OAuth 2.0 que tem um `grant type` do tipo `client credentials`, conforme definido em [RFC6749](https://tools.ietf.org/html/rfc6749) e com um mecanismo de autenticação de cliente definido como `tls_client_auth`, conforme definido em [RFC 8705](https://tools.ietf.org/html/rfc8705).

Usando o ClientID listado na declaração do software (software statement) no Diretório, [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) e a configuração do OpenID Provider Issuer abaixo, um participante tem todos das informações necessárias para descobrir, autenticar e interagir com as APIs do Diretório.

### 2.1. Emissores do Framework de Confiança do Diretório

Produção: [https://auth.directory.openbankingbrasil.org.br/](https://auth.directory.openbankingbrasil.org.br/)

Sandbox: [https://auth.sandbox.directory.openbankingbrasil.org.br/](https://auth.sandbox.directory.openbankingbrasil.org.br/)

Os certificados para acesso às API´s publicadas pelas instituições participantes devem ser obrigatoriamente certificados emitidos no âmbito da ICP-Brasil.

### 2.2. Como se Comunicar com o Authorization Server do Diretório

Use o OpenID Issuer e a Cláusula 4 da especificação [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) para obter o documento ‘openid-configuration’.

Obtenha o ‘alias’ do endpoint do Mutual TLS Token, conforme definido por [RFC8705 - OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://tools.ietf.org/html/rfc8705)

Estabeleça uma conexão TLS mútua usando o certificado de transporte registrado anteriormente e solicite um token de acesso com o escopo `directory:software`

### 2.3. Como se Comunicar com as APIs do Diretório

As APIs do Diretório são recursos RESTful protegidos usando o Perfil de Segurança do Open Finance Brasil. Isso significa que eles têm a mesma postura de segurança das APIs publicadas pelos Bancos. Todas as APIs de Diretório requerem o escopo do recurso OAuth 2.0 de `directory:software` e são protegidos usando Mutual TLS (mTLS).

Consulte a especificação do Diretório OpenAPI v3 para o conjunto completo de endpoints disponíveis.

### 2.4. Descobrindo Authorization Servers de Bancos

Faça uma busca pelo recurso de participantes (informações públicas) e obtenha uma lista de todos os participantes e seus Authorization Servers.

Filtre os participantes por aqueles que possuem Authorization Servers protegendo os recursos que você está interessado em acessar para o seu produto. No exemplo acima, existem dois Authorization Server para ‘Amazing Bank’, um para o negócio de varejo e um para o banco corporativo.

O aplicativo agora descobriu a lista de bancos que estão oferecendo APIs que podem ser úteis para os usuários do aplicativo e pode gerar uma lista de ‘customer friendly names’ de bancos e logotipos para exibir aos clientes para permitir que eles selecionem o banco a partir do qual desejam compartilhar dados.

## 3\. Registrando o Aplicativo com um Provedor

![att\_3\_for\_157384798.png](images/att_3_for_157384798.png)

A partir do exemplo dado acima, podemos ver que a localização do “OpenIDDiscoveryDocument” é anunciada por cada um dos Authorization Server.

### 3.1. Criação de uma Declaração de Software (SSA)

Uma afirmação de declaração de software (software statement assertion - SSA) é um JWT assinado pelo Diretório que contém todas as informações sobre um aplicativo que existe em um determinado momento no Diretório. Inclui a localização de todas as chaves públicas vinculadas à esta declaração de software e todos os outros metadados de que um banco precisa para validar a legitimidade do aplicativo.

Um SSA não tem período de validade, é simplesmente um registro pontual do que existia como atributos válidos no momento em que foi criado. Os bancos devem aceitar um SSA com menos de alguns minutos, mas a janela exata pode ser diferente entre os provedores.

Obtenha um token de acesso e, em seguida, carregue a declaração do software para um aplicativo no Diretório.

### 3.2. Enviando uma Solicitação de Dynamic Client Registration (RFC7591)

Consulte o [Dynamic Client Registration do Open Finance Brasil](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID3-ptbr.html)

### 3.3. Salvando o Token de Dynamic Registration Management (RFC7592)

Consulte o [Dynamic Client Registration do Open Finance Brasil](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID3-ptbr.html)

### 3.4. Modificando um cliente usando Dynamic Client Management Token (RFC7592)

Consulte o [Dynamic Client Registration do Open Finance Brasil](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-dynamic-client-registration-1_ID3-ptbr.html)

## 4\. Obtendo Acesso aos Recursos dos Clientes

![att\_5\_for\_157384798.png](images/att_5_for_157384798.png)

Para todas as opções, incluindo todos os códigos de permissão, consulte o [Consent API](https://openbanking-brasil.github.io/areadesenvolvedor/swagger/swagger_consents_apis.yaml). Os exemplos a seguir são exemplos mínimos, mas funcionais para demonstrar o fluxo de ponta a ponta. Esses exemplos pressupõem que o cliente está se comunicando com um provedor de OpenID, aproveitando o mecanismo de autenticação de endpoint do token ‘tls\_client\_auth’. Exemplos alternativos estão disponíveis no apêndice.

### 4.1. Pré-requisitos

Esses exemplos **não normativos** presumem que o cliente OAuth descobriu os locais de todos os ‘endpoints’ necessários para se comunicar com os recursos dos bancos do Diretório, incluindo o recurso de consentimento, os recursos de dados e o documento de descoberta de autorização OpenID do Diretório.

### 4.2. Criando Consentimento

btendo um Token de Acesso com escopo ‘consents’

Criando um recurso de consentimento

### 4.3. Autorizando Consentimento - Redirecionar

#### 4.3.1. Criar OpenID Connect Request Object

Diferentes métodos de autenticação (private\_key\_jwt e tls\_client\_auth) e de encaminhamento do Request Object (com e sem uso de PAR) podem ser suportados pelos Authorization Servers de acordo com a especificação [FAPI-1.0 Part 2 - Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html).

Portanto, como reforça o perfil de segurança para o Open Finance Brasil (item 8 da seção 5.2.3 dos [requisitos de segurança para o cliente confidencial](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-financial-api-1_ID3-ptbr.html#section-5.2.3)), todas as 4 combinações de métodos devem ser suportados pelos clientes de API.

A tabela abaixo reflete os diferentes profiles de segurança e combinações que devem ser suportados por todos os clientes de API (conforme os [profiles certificados pela OIDF para o Open Finance Brasil](https://openid.net/certification/#FAPI_OPs)).

**Perfil da certificação OIDF**

BR-OB Adv. OP w/ Private Key, PAR

Todos os requisitos para o OpenID Request Object estão incluídos no [Perfil de Segurança do Open Finance Brasil](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-financial-api-1_ID3-ptbr.html). Veja o exemplo com JWS a seguir:

#### 4.3.2. Redirecionar o Usuário ao Authorization Server para Autorização

De acordo com o OpenID Connect Core.

#### 4.3.3. Obtenção de Token de Acesso por Meio de Troca de Código de Autorização

Conforme [RFC 7636 Proof Key for Code Exchange](https://tools.ietf.org/html/rfc7636)

### 4.3.4. Verificação do Status do Recurso de Consentimento

Neste ponto, um TPP pode, opcionalmente, verificar o status da solicitação de consentimento para ver se mudou para totalmente autorizado. Esta etapa não deverá ser necessária para recursos que não requerem consentimento de múltiplos indivíduos, entretanto, para contas comerciais ou contas conjuntas com requisitos de acesso especiais, então pode demorar um pouco para o banco obter as autorizações adicionais necessárias para que esse consentimento seja totalmente autorizado. Os TPPs não devem abusar da verificação do status de consentimento API.

#### 4.3.5. Acesso aos Recursos

Com o token de acesso que foi retornado em 4.3.3, o TPP agora tem a capacidade de chamar os recursos dos clientes.

## Apêndice

### A.1 Concessão de Credenciais de private\_key\_jwt client

### A.2 Exemplo de Corpo de Objeto de Solicitação Decodificado

### A.3 Exemplo de Decodificação do Corpo de uma Solicitação com Valores de Reivindicação Específicos Sendo Solicitados

Neste exemplo, um cliente está solicitando que o Authorization Server autentique o cliente apenas se a declaração cpf corresponder ao valor fornecido. Os requisitos de processamento para solicitações com um valor ‘cpf’ específico são definidos no Perfil de Segurança do Open Finance Brasil.

### A.4 Exemplo de Decodificação do Corpo de Solicitação de Autenticação CIBA

Neste exemplo, uma solicitação CIBA está sendo feita para solicitar autorização de consentimento usando um id\_token emitido como a indicação do proprietário do recurso que o banco deve entrar em contato para obter autorização.
