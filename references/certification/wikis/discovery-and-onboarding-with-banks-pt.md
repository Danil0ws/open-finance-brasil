# Discovery and Onboarding with Banks (PT)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-and-Onboarding-with-Banks-(PT)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-and-Onboarding-with-Banks-(PT))
**Slug:** `Discovery-and-Onboarding-with-Banks-(PT)`

---

## Encontrar Provedores de Recursos de Interesse para nossos clientes

[Versão em inglês disponível]([Portuguese version available](https://gitlab.com/obb1/certification/-/wikis/Discovery-and-Onboarding-with-Banks)

Uma das características do Diretório é a capacidade dos Bancos Participantes de anunciarem seus Servidores de Autorização e de listarem e anunciarem quais APIs, Versões e Locais desses Recursos que esses servidores de autorização irão emitir tokens de acesso. Isto permite que os Bancos gerenciem os ciclos de vida das versões das APIs de uma maneira centralizada e consistente, depreciem as versões antigas ou comecem a anunciar as APIs mais recentes à medida que e quando esses recursos se tornarem disponíveis. Isto permite aos TPPs gerenciarem dinamicamente as conexões que eles têm com os bancos com base nas propostas que podem ser habilitadas como resultado da disponibilização de dados.

Neste exemplo, o Raidiam Mock Bank está anunciando que apoia as APIs de 'financiamento' e os locais em que essas APIs podem ser encontradas. Na maioria das situações você esperaria em um único ponto final para uma localização de recurso, entretanto, alguns bancos do Reino Unido, usam hosts físicos separados para suas localizações de failover/locais alternativos em vez de confiar no failover do DNS.


```
{
        "PayloadSigningCertLocationUri": "https://mockbank.com/payload.pem",
        "ParentAuthorisationServerId": null,
        "OpenIDDiscoveryDocument": "https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration",
        "CustomerFriendlyName": "Mock Bank",
        "CustomerFriendlyDescription": null,
        "TermsOfServiceUri": "https://mockbank.com/tos",
        "ApiResources": [
            {
                "ApiFamilyType": "financings",
                "ApiVersion": 1,
                "ApiResourceId": "b67768ec-a0aa-4445-ae96-e00f28145146",
                "ApiDiscoveryEndpoints": [
                    {
                        "ApiDiscoveryId": "13aad598-12c6-4f75-92f4-dc754756b222",
                        "ApiEndpoint": "https://api.personal.bank.com/v1/personal-accounts"
                    }
                ]
            }
        ],
        "AutoRegistrationSupported": true,
        "CustomerFriendlyLogoUri": "https://mockbank.com/logo.png",
        "DeveloperPortalUri": "https://mockbank.com/dev",
        "AuthorisationServerId": "c8f0bf49-4744-4933-8960-7add6e590841"
    
},

```

Identificar fornecedores apropriados para tipos específicos de recursos é tão simples quanto obter um token de acesso, solicitar os recursos e depois filtrar.

```
{ //Query the participants API
        const cctokenset = await directoryClient.grant({ scope: 'directory:software', grant_type: 'client_credentials' });
        const availableBanks = JSON.parse((await directoryClient.requestResource('https://data.sandbox.directory.openbankingbrasil.org.br/participants', cctokenset)).body.toString('utf-8'));
        console.log(availableBanks);
        
        const foundBanks = availableBanks.flatMap(org => org.AuthorisationServers)
            .filter(auth => auth.ApiResources && auth.ApiResources.length > 0)
            .filter(auth => (auth.ApiResources
                .some(res => (res.ApiFamilyType = req.query.apiType))
            ));


        return res.json(foundBanks);
```

## Registro junto a um Provedor


No ecossistema Brazil Open Banking, todos os Bancos são obrigados a implementar o RFC7951 - OAuth 2.0 Dynamic Client Registration e, além disso, eles são obrigados a implementar o RFC7592 - OAuth 2.0 Client Management.

Alavancar as APIs de Registro Dinâmico de Cliente para o Onboard para um Banco é simples.

#### Descubra qual configuração OpenID um servidor suporta

Usando o OpenID Discovery Document Uri que foi fornecido pelo Diretório no exemplo acima, crie um Emissor.

```
const bankIssuer = await Issuer.discover(foundBank[0].OpenIDDiscoveryDocument);


console.log('Discovered bank issuer %s %O', bankIssuer.issuer, bankIssuer.metadata);
```

O Emissor e os metadados do Emissor são construídos usando OpenID Discovery para recuperar a configuração anunciada do Servidor de Autorização Bancária / Provedor OpenID que é um simples [JSON payload](https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration) que inclui todos os pontos finais necessários, assinatura e padrões de criptografia que o Provedor OpenID suporta.

#### Recuperando uma declaração de software do diretório

Uma declaração de software é uma coleção de metadados que descreve a aplicação. Os ecossistemas que estão alavancando um diretório central (Brasil, UK OBIE, Austrália CDR) poderão obter esses metadados que são assinados pelo serviço central que eles podem apresentar aos Provedores como parte de seu processo de registro. Os Provedores validarão a assinatura das Declarações de Software como parte do processo de garantia de registro para confirmar a legitimidade da aplicação e do participante que desejar fazer onboard.

```
const cctokenset = await directoryClient.grant({ scope: 'directory:software', grant_type: 'client_credentials' });

const softwareAssertionResponse = await directoryClient.requestResource(`https://matls-api.sandbox.directory.openbankingbrasil.org.br/organisations/${ORGID}/softwarestatements/${SSID}/assertion`, cctokenset);
            
```

#### Criação de um Pedido Dinâmico de Registro de Cliente (Dynamic Client Registration Request)

Há muitas configurações diferentes em conformidade com a FAPI que um provedor OpenID pode escolher adotar e decidir o que é melhor para cada provedor dependerá de uma série de fatores diferentes que estão fora do escopo deste artigo.

Devido à grande variedade de opções que os Bancos podem escolher adotar, os TPPs devem ser capazes de processar e selecionar a partir das capacidades de propaganda a combinação do que eles gostariam de usar. A seguir, um exemplo de como um TPP poderia usar uma Declaração de Software e um OpenID Metadata dos Bancos para determinar se ele pode usar OAuth 2 Pushed Authorisation Requests (PAR) ou se precisa usar Signed and Encrypted Request Objects.

```
function generateDcrPayload(issuer, softwareStatementAssertion, directoryClient, softwareStatement) {
    
        const dcr = {};
        dcr.application_type = 'web';
        dcr.grant_types = [
            'client_credentials',
            'authorization_code',
            'implicit',
            'refresh_token'
        ];
        dcr.response_types = ['code id_token'];
        dcr.require_auth_time = true;
        dcr.request_object_signing_alg = 'PS256';
        dcr.jwks_uri = directoryClient.jwks_uri;
        dcr.tls_client_auth_subject_dn = directoryClient.tls_client_auth_subject_dn;
        dcr.redirect_uris = directoryClient.redirect_uris;
        dcr.token_endpoint_auth_method = issuer.token_endpoint_auth_methods_supported.includes('tls_client_auth') ? 'tls_client_auth' : 'private_key_jwt';
        dcr.client_name = softwareStatementAssertion.software_client_name;
        dcr.tos_uri = softwareStatementAssertion.software_tos_uri;
        dcr.software_id = softwareStatementAssertion.software_id;
        if (issuer.response_modes_supported.includes('jwt')) dcr.response_mode = 'jwt';
        dcr.client_uri = softwareStatementAssertion.software_client_uri;
        dcr.logo_uri = softwareStatementAssertion.software_logo_uri;
        dcr.scope = issuer.scope;
        dcr.require_signed_request_object = true;
        if (issuer.pushed_authorization_request_endpoint) {
            dcr.require_pushed_authorization_requests = true;
        }
        else {
            dcr.request_object_encryption_enc = 'A256GCM';
            dcr.request_object_encryption_alg = 'RSA-OAEP';
        }
        dcr.software_statement = softwareStatement;
        return dcr;
    }
```

#### Registro junto ao Provedor

E para o passo final de registrar de fato é bem simples. O FAPIClient contém um método de registro que fará todo o trabalho pesado para você.

```
const bankIssuer = await Issuer.discover(foundBank[0].OpenIDDiscoveryDocument);


console.log('Discovered bank issuer %s %O', bankIssuer.issuer, bankIssuer.metadata);

const { FAPIClient } = bankIssuer;


const dcrRequest = generateDcrPayload(bankIssuer.metadata, ssa.payload, directoryClient.metadata, softwareAssertionResponse.body.toString('utf-8'), );


const bankClient =  await FAPIClient.register({ ...dcrRequest, keyset });
```

Com os metadados do cliente e os tokens de gerenciamento de registro resultantes sendo devolvidos para o novo cliente onboarded, um TPP está agora totalmente funcional e pronta para solicitar acesso aos dados do consumidor.

```
{
  "grant_types": [
    "client_credentials",
    "authorization_code",
    "refresh_token",
    "implicit"
  ],
  "id_token_signed_response_alg": "PS256",
  "authorization_signed_response_alg": "RS256",
  "response_types": [
    "code id_token",
    "code"
  ],
  "token_endpoint_auth_method": "tls_client_auth",
  "application_type": "web",
  "post_logout_redirect_uris": [],
  "require_auth_time": true,
  "subject_type": "public",
  "introspection_endpoint_auth_method": "tls_client_auth",
  "revocation_endpoint_auth_method": "tls_client_auth",
  "request_object_signing_alg": "PS256",
  "require_signed_request_object": true,
  "require_pushed_authorization_requests": true,
  "tls_client_certificate_bound_access_tokens": true,
  "client_id_issued_at": 1622806390,
  "client_id": "tO3Vo3ckUJclyWAxM8pZT",
  "client_name": "Mock Bank Client 1",
  "client_uri": "https://www.raidiam.com",
  "default_max_age": 0,
  "jwks_uri": "https://keystore.sandbox.directory.openbankingbrasil.org.br/74e929d9-33b6-4d85-8ba7-c146c867a817/b8986a43-e730-460f-97f9-9ad90f4e31d3/application.jwks",
  "logo_uri": "https://www.raidiam.com",
  "policy_uri": "https://www.raidiam.com",
  "redirect_uris": [
    "https://oauth.pstmn.io/v1/callback",
    "https://tpp.localhost/cb"
  ],
  "tos_uri": "https://www.raidiam.com",
  "tls_client_auth_subject_dn": "CN=b8986a43-e730-460f-97f9-9ad90f4e31d3,OU=74e929d9-33b6-4d85-8ba7-c146c867a817,O=Open Banking,C=BR",
  "request_object_encryption_alg": "RSA-OAEP",
  "request_object_encryption_enc": "A256GCM",
  "registration_client_uri": "https://matls-auth.mockbank.poc.raidiam.io/reg/tO3Vo3ckUJclyWAxM8pZT",
  "registration_access_token": "2b1JkScyN7R9kne49r-7KnduwVFb84O55GiVu8S6Ksa"
}
```

---

*Conteúdo baixado em 16/09/2026, 15:37:25*
