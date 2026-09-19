# Discovery of the Mock Bank (PT)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank-(PT)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank-(PT))
**Slug:** `Discovery-of-the-Mock-Bank-(PT)`

---

# Pré-requisitos: Criando uma declaração de software no Sandbox

[Versão em inglês disponível aqui](https://gitlab.com/obb1/certification/-/wikis/Discovery-of-the-Mock-Bank)

## O Diretório dos Participantes - Sandbox

Para se conectar com o Mock Bank, um TPP precisará primeiro ter uma Declaração de Software válida emitida da Sandbox do diretório de participantes do Open Banking.

Para acessar o [Sandbox do diretório de participantes](https://web.sandbox.directory.openbankingbrasil.org.br/organisations) o usuário precisa pertencer a uma organização que seja um participante autorizado do Open Banking e também ser adicionado como um membro de uma das organizações presentes no diretório. Este acesso pode ser concedido por administradores já existentes desta organização.

Para criar uma declaração de software no diretório, o usuário deve consultar o [Guia do Diretório de Participantes](https://openbanking-brasil.github.io/areadesenvolvedor/#diretrizes-tecnicas-do-diretorio), que é atualmente mantido pela estrutura central do Open Banking

A criação de uma declaração de software também pode ser vista no vídeo [Mock Bank - Create S.S.](https://www.youtube.com/watch?v=03R2jtrZPuU&ab_channel=OpenBankingBrasil)

## Atribuir as funções regulatórias à Declaração de Software (S.S)

Para se comunicar com outros servidores, que incluem o Mock Bank, as instituições credenciadas devem garantir que suas Declarações de Software possam obter os escopos necessários vinculados aos papéis regulatórios. Esses papéis refletem a autorização das instituições do Banco Central e, consequentemente, as APIs que elas estão autorizadas a utilizar.

No ambiente de Sandbox, a atribuição de um papel à sua organização e à sua declaração de software é feita de forma totalmente self-service. Para ver como atribuir essas funções, consulte o [Guia do Diretório de Participantes](https://openbanking-brasil.github.io/areadesenvolvedor/#diretrizes-tecnicas-do-diretorio)

O mapeamento entre escopos e papéis regulatórios está especificado na [Documentação de Segurança do DCR](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2.md#regulatory-roles-to-openid-and-oauth-20-mappings). Isto significa que o usuário deve certificar-se de que seu cliente detém todas as funções reguladoras necessárias antes de interagir com o Mock Bank

## Emitindo certificados usando o PKI do Diretório no Sandbox

O Diretório do Open Banking contém um PKI que pode ser usado para criar certificados para as Aplicações que estão sendo registradas. O Sandbox também usa [certificados estilo ICP-Brasil](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-certificate-standards-1_ID1.md), semelhantes aos que são emitidos pelas diferentes autoridades certificadoras para serem usados no ambiente de produção.

Há dois tipos de certificados que devem ser emitidos para serem usados com o cliente criado, BRCAC e BRSEAL. O primeiro é usado para transporte ou criptografia, enquanto o segundo é o certificado de assinatura. Observe que enquanto o BRCAC é criado no nível de Declaração de Software, no menu de Declaração de Software, o BRSEAL é criado no nível de organização, no menu Certificado de Organização. Para emitir os certificados, será necessária uma biblioteca para gerar os Certificate Signing Requests (CSR) que precisam ser carregadas no diretório.

A geração dos certificados pode ser vista no item **"11.Criando certificados de transporte e assinatura em Sandbox "** do [Guia do Diretório dos Participantes](https://openbanking-brasil.github.io/areadesenvolvedor/#diretrizes-tecnicas-do-diretorio)

Uma vez terminado, o participante deve ter dois conjuntos de chaves públicas e privadas, ambos em formato PEM. Para perguntas relativas aos arquivos de certificados, consulte [TPP User Guide - Creating Certificates Session](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/tpp-user-guide.md#14-creating-and-uploading-certificates)

O processo de emissão dos certificados também pode ser visto no vídeo [Mock Bank - Issue Certficates](https://www.youtube.com/watch?v=0GSMsVtjw2c&t=1s&ab_channel=OpenBankingBrasil)

# Descobrindo as APIs do Mock Bank

## APIs do Diretório

As informações do Diretório de Participantes podem ser acessadas em um nível API utilizando duas abordagens diferentes:

- Acesso à API "Data", que fornece um dump de todos os Servidores de Autorização registrados no diretório - 15 minutos em cache. Para maiores informações sobre os detalhes que podem ser acessados através desta API, favor consultar a [data api swagger](https://openbanking-brasil.github.io/areadesenvolvedor/swagger/swagger_participants.yaml)
- O acesso ao mTLS protegido "matls-api", que fornece dados granulares em tempo real de tudo o que foi registrado dentro do diretório. Para mais detalhes sobre os recursos que podem ser acessados, consulte o [matls-api swagger](https://raw.githubusercontent.com/OpenBanking-Brasil/specs-directory/main/openapi.yaml)

> Favor observar que embora ambos os swaggers sejam para o Diretório de Participantes, eles podem ser usados para o ambiente sandbox com a única diferença de que se deve adicionar sandbox antes do ".directory" no URI. Por exemplo:
>
> - Sandbox: https://data.sandbox.directory.openbankingbrasil.org.br/participants
> - Produção: https://data.directory.openbankingbrasil.org.br/participants

Ambos os métodos podem ser usados para recuperar os detalhes do Mock Bank, porém o uso da API de dados prova ser um método mais simples, pois não somente é uma API que pode ser acessado sem qualquer tipo de autenticação, mas todas as informações necessárias podem ser obtidas com um único pedido.

## Obtendo as URIs do Mock Bank

O Mock Bank está atualmente registrado sob a organização Open Banking Brasil, que tem a seguinte identificação de organização:

```
MOCK BANK
"OrganisationId": "b961c4eb-509d-4edf-afeb-35642b38185d",
"OrganisationName": "Open Banking Brasil - Raidiam"
```

Ela pode ser encontrada procurando por seu Brand Name (CustomerFriendlyName) ou sua id (AuthorisationServerId):

```
MOCK BANK
"CustomerFriendlyName": "Mock Bank Sandbox"
"AuthorisationServerId": "7844e311-aa1f-4f67-9475-cbd989310b3e"
"OpenIDDiscoveryDocument": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
```

Sob o Servidor de Autorização, é possível obter o well-known endpoint, registrado como "OpenIDDiscoveryDocument" e todos os recursos que o Mock Bank suporta atualmente, incluindo todos as APIs da Fase 2 - Customer Data APIs e a Fase 3 - PIX Payments API

Abaixo está um exemplo de código em Python que permite a recuperação do well-known end point do Mock Bank e de todos os seus recursos API:

```
import requests

response = requests.get("https://data.sandbox.directory.openbankingbrasil.org.br/participants")
response = response.json()

for Organisation in response:
  for AuthServer in Organisation['AuthorisationServers']:
    if AuthServer['AuthorisationServerId']=='7844e311-aa1f-4f67-9475-cbd989310b3e':
      AS_WellKnown=AuthServer['OpenIDDiscoveryDocument']
      AS_Resources=AuthServer['ApiResources']
```

---

*Conteúdo baixado em 16/09/2026, 15:37:26*
