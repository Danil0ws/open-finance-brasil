# Registering an Application and Retrieving a Software Statement (PT)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-an-Application-and-Retrieving-a-Software-Statement-(PT)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-an-Application-and-Retrieving-a-Software-Statement-(PT))
**Slug:** `Registering-an-Application-and-Retrieving-a-Software-Statement-(PT)`

---

# Registro de um aplicativo na 'App Store'.

[Versão em inglês disponível](https://gitlab.com/obb1/certification/-/wikis/Registering-an-Application-and-Retrieving-a-Software-Statement)

Vamos partir do princípio de que um TPP já passou pelos processos necessários de onboarding tanto de si mesma como organização quanto como indivíduo e se registrou com sucesso no Diretório.

### Criação de um novo aplicativo ou registro de software

![image](uploads/a6b63dce51e402510485d6defd4db7ed/image.png)

Navegue até Declarações de Software - Clique em '+ Nova Declaração de Software' e preencha o formulário com os Softwares Metadados

### Upload ou gerar os certificados

![image](uploads/1f7f8045a9fe028e3e5dce2559e617ac/image.png)

Este passo deve ser bem autoexplicativo. Ou usar o embutido production grade PKI e a Autoridade Certificadora para criar certificados ou use o seu.


### Interacting with the App Store

Quando uma Declaração de Software é registrada, um cliente OAuth é provisionado para este Registro de Software que permite aos participantes interagir com a API. Os próximos passos mostrarão como, com menos de 50 linhas de NodeJs, é possível interagir com o OpenID FAPI Protected Resources usando as credenciais concedidas pelo cliente alavancando o [node-openid-client](https://github.com/panva/node-openid-client) que é uma OpenID Certified Relying Party.


#### Setup Key Material
```
const { Issuer, custom  } = require('openid-client');
const fs = require('fs');
const { default: fromKeyLike } = require('jose/jwk/from_key_like');
const crypto = require('crypto');
const { X509Certificate } = require('crypto');
    const {
        jwtVerify
        } = require('jose/jwt/verify');
    const {
        parseJwk
        } = require('jose/jwk/parse');
        
    const certsPath = path.join(__dirname, './certs/',ENVIRONMENT, SSID );


    const key = crypto.createPrivateKey(fs.readFileSync(certsPath + '/signing.key'));
    const signingCert = new X509Certificate(fs.readFileSync(certsPath + '/signing.pem'));

```
#### Como falar com o OpenID Server


Alavancando [OpenID Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html), basta criar uma classe emissora e depois criar um cliente associado com o emissor. A maior parte do código abaixo é o registro, comentários ou a configuração das opções HTTP corretas para garantir que a autenticação do certificado do cliente seja usada ao fazer chamadas HTTP.

```
 //Connect the FAPI client to the directory 
   const directoryIssuer = await Issuer.discover('https://auth.sandbox.directory.openbankingbrasil.org.br');


    console.log('Discovered directory issuer %s %O', directoryIssuer.issuer, directoryIssuer.metadata);
    const { FAPIClient } = directoryIssuer;


    const directoryClientMetdata = JSON.parse(fs.readFileSync(certsPath + '/directory_client.json'));
    const directoryClient = new FAPIClient(directoryClientMetdata, keyset );


    console.log('Discovered client %O', directoryClient);
    directoryClient[custom.http_options] = function (options) {
        
        options.https = {};

        options.https.certificate          = fs.readFileSync(certsPath + '/transport.pem'); // <string> | <string[]> | <Buffer> | <Buffer[]>
        options.https.key                  = fs.readFileSync(certsPath + '/transport.key');
        options.https.certificateAuthority = fs.readFileSync(certsPath + '/ca.pem');// <string> | <string[]> | <Buffer> | <Buffer[]> | <Object[]>
        return options;
    };
```

#### Obter um token e chamar um recurso

```
 //Get Software Statement From Directory
const ccTokenSet = await directoryClient.grant({ scope: 'directory:software', grant_type: 'client_credentials' });

const softwareAssertionResponse = await directoryClient.requestResource(`https://matls-api.sandbox.directory.openbankingbrasil.org.br/organisations/${ORGID}/softwarestatements/${SSID}/assertion`, ccTokenSet);
```

---

*Conteúdo baixado em 16/09/2026, 15:38:28*
