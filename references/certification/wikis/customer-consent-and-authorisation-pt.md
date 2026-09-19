# Customer Consent and Authorisation (PT)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Consent-and-Authorisation-(PT)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Consent-and-Authorisation-(PT))
**Slug:** `Customer-Consent-and-Authorisation-(PT)`

---

[Versão em inglês disponível](https://gitlab.com/obb1/certification/-/wikis/Customer-Consent-and-Authorisation)

Vamos seguir os passos para obter acesso aos dados dos clientes usando as Brazil Open Banking Standards para Redirecionamento usando tanto objetos de solicitação criptografados quanto solicitações de autorização empurradas. Ambas as modalidades que são suportadas para o Open Banking Brazil.

### Passo 0. Simplificando nossos esforços de desenvolvimento

Criar um cliente API strongly typed pode ser tão simples quanto executar um único comando de cliente (cli). Um exemplo de como gerar um cliente API usando a [Consents OpenAPI definition](https://github.com/OpenBanking-Brasil/areadesenvolvedor/blob/master/documentation/source/swagger/swagger_consents.yaml) está abaixo.

```
openapi-generator generate -i swagger.yaml -g typescript-axios --additional-properties=npmName=@raidiam/api_consents_open_banking_brasil --additional-properties=supportsES6=true  -o ./tmp
```

### Passo 1. Criar um Recurso de Consentimento

Usando uma API criada em typescript

```
  using creating a new consent resource is as simple as
// Obtain Tokens for a client credentials grant with scope of consents
const tokens = await fapiClient.grant({ scope: 'consents', grant_type: 'client_credentials' });

// Craft Post Request
var oneYearFromNow ​= new Date();
oneYearFromNow.setFullYear(oneYearFromNow.getFullYear() + 1);


var now = new Date();


const createPost = await consentsApi.consentsPostConsents(`${tokens.token_type} ${tokens.access_token}`,
                {
                    data: {
                        permissions: [CreateConsentDataPermissionsEnum.AccountsRead, CreateConsentDataPermissionsEnum.AccountsBalancesRead],
                        expirationDateTime: oneYearFromNow.toISOString(), transactionFromDateTime: now.toISOString(), transactionToDateTime: oneYearFromNow.toISOString(),
                        loggedUser: {
                            document: {
                                identification: '12345123451',
                                rel: 'CPF'
                           } 
                        },
                        businessEntity: {
                            document: {
                                identification: '11111111111111',
                                rel: 'CNPJ'
                            }
                        }
                    }
                }).catch(err => {
                    console.log(err);
                });

```

Pronto, uma requisição de consentimento foi criada


```
{
   "data":{
      "consentId":"mock-ccfe895c-b4cf-4685-b744-2c8fb997c795",
      "creationDateTime":"2021-06-08T16:30:39.399Z",
      "status":"AWAITING_AUTHORISATION",
      "statusUpdateDateTime":"2021-06-08T16:30:39.199Z",,
      "permissions":[
         "ACCOUNTS_READ",
         "ACCOUNTS_BALANCES_READ"
      ],
      "expirationDateTime":"2022-06-08T16:30:39.199Z",
      "transactionFromDateTime":"2021-06-08T16:30:39.199Z",
      "transactionToDateTime":"2022-06-08T16:30:39.199Z",
   },
   "links":{
      "self":"https://matls-api.mockbank.poc.raidiam.io/consents/mock-ccfe895c-b4cf-4685-b744-2c8fb997c795"
   },
   "meta":{
      "totalRecords":1,
      "totalPages":1,
      "requestDateTime":"2021-06-08T16:30:39.399Z"
   }
}
```

### Passo 2. Criação de um objeto de solicitação

#### 2.1 Criando um PKCE Code Challenge para o pedido

```
  const state = crypto.randomBytes(32).toString('hex');
        const nonce = crypto.randomBytes(32).toString('hex');
        const code_verifier = generators.codeVerifier();



        const code_challenge = generators.codeChallenge(code_verifier);
```

#### 2.2 Opcional: Criar um objeto de reivindicação contendo as reivindicações padrões OIDF Brasil desejadas ou o nível de autenticação que você deseja que um Banco realize com o usuário final

O perfil de segurança do Brasil define duas novas alegações do OIDC de que Third Parties podem solicitar que sejam fornecidos por seu Banco: CPF e CNPJ. Os detalhes destas reivindicações estão no Perfil de Segurança da FAPI Brasil.

```
 const claims = {
            id_token: {
                auth_time: {
                    essential: true,
                },
                cpf: {
                    essential: true,
                },
                given_name: {
                    essential: true,
                },
                acr: {
                    values: ['urn:brasil:openbanking:loa2'],
                    essential: true
                }
            },
            user_info: {
                auth_time: {
                    essential: true,
                },
                cpf: {
                    essential: true,
                },
                given_name: {
                    essential: true,
                },
                acr: {
                    values: ['urn:brasil:openbanking:loa2'],
                    essential: true
                }
            }
        };
```

#### 2.3 Preparar um objeto de solicitação e assiná-lo (usando o oidc-client)

A biblioteca que é gratuita cuida de todo o levantamento pesado para os desenvolvedores, tanto que criar um JWT que atenda ao requisito de um Objeto de Solicitação FAPI é tão simples quanto:

```
const requestObject = await fapiClient.requestObject({
            `openid consent:${consentId}`,
            response_type: 'code id_token',
            redirect_uri: 'https://tpp.localhost/cb',
            code_challenge,
            code_challenge_method: 'S256',
            response_mode: 'form_post',
            state,
            nonce,
            claims,
            max_age: 300
        
});

```

#### 2.4 To PAR or Not to PAR

Os prós (muitos) e contras (não muitos) do uso de Pushed Authorisation Requests (PAR) são um tópico para outro artigo, entretanto, para os desenvolvedores não há nenhuma desvantagem em usar o PAR com esta biblioteca e há benefícios significativos de privacidade que podem ser obtidos ao comunicar pedidos de informação. Mais informações sobre o PAR podem ser encontradas no vídeo de introdução recente que [o CTO do Raidiam deu ao Ecossistema do Brasil em nome da Fundação OpenID](https://www.youtube.com/watch?v=v8ks7C-f9Yg).

**2.4.1 Criar Url de Autorização usando o PAR**

```
reference = await fapiClient.pushedAuthorizationRequest({
            request: requestObject
          
});
authUrl = await fapiClient.authorizationUrl({ request_uri: reference.request_uri });
```

**2.4.2 Create Authorization Url not using PAR **

```
authUrl = await fapiClient.authorizationUrl({ request: requestObject });
```

### 3.0 Enviar usuário para autorização

```
const { authUrl, code_verifier, state, nonce } = await generateRequest(createPost.data.data.consentId, USE_PAR);

//save state
//save nonce
//save code_verifier

return res.redirect(authUrl);
```

### 4.0 Autenticação do usuário e autorização

As etapas de validação e as informações que precisam ser apresentadas ao cliente

![image](uploads/6fd71e5a2acaeae5040446a6a8f82602/image.png)

### 5.0 Validar o Redirecionamento e obter tokens de acesso

```
const state = retrieveState();
res.cookie('bank.state', null, { path });


const nonce = retrieveNonce();
res.cookie('bank.nonce', null, { path });


const code_verifier = retrieveCodeVerifer();
res.cookie('bank.code_verifier', null, { path });


tokens = await fapiClient.callback('https://tpp.localhost/cb',
               callbackParams,
               { code_verifier, state, nonce, response_type: 'code id_token' },
           );
```

Pronto! End-to-end com apenas algumas centenas de linhas de NodeJS e o uso de bibliotecas gratuitas de código aberto uma TPP pode descobrir, registrar, configurar consentimento, obter autorização do cliente para acesso e depois acessar recursos.

---

*Conteúdo baixado em 16/09/2026, 15:37:22*
