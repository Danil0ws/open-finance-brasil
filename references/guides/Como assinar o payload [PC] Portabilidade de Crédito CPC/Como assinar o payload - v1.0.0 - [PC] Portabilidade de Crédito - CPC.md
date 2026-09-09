# Como assinar o payload - v1.0.0 - [PC] Portabilidade de Crédito - CPC

none

### Orientações detalhadas para assinatura do _payload_ dos _endpoints_ de Portabilidade de crédito

-   No contexto da API de Portabilidade de Crédito, os payloads dos endpoints, trafegados tanto pela instituição credora quanto pela instituição proponente, devem estar devidamente assinados. Abaixo, seguem as orientações para a assinatura das mensagens JWS.
    
-   Informações complementares de segurança estão disponíveis no link.
    

**– Passo 1** - Identifique a chave privada e o certificado de assinatura correspondente a serem usados para assinatura  
As assinaturas devem ser realizadas com uso do certificado digital de assinatura especificado no Padrão de Certificados Open Finance Brasil  
O certificado de assinatura deve ser válido no momento da criação do JWS

**– Passo 2** - Geração do JOSE (JSON Object Signing and Encryption) Header

_**▫**_ O JOSE Header deve conter os seguintes campos:

**Nome**

**Tipo**

**Obrigatório**

**Descrição**

alg

string

true

O algoritmo que será usado para assinar o JWS. Deve ser preenchido com o valor PS256.

kid

string

true

Deve ser obrigatoriamente preenchido com o valor do identificador da chave utilizado para a assinatura.

typ

string

true

É o tipo de conteúdo usado para trafegar mensagens na API. Deve ser preenchido com o valor `JWT`.

**– Passo 3** \- Montando a mensagem JWS  
Para garantir a integridade e o não-repúdio das informações tramitadas em APIs sensíveis e que indicam essa necessidade na sua documentação, deve ser adotado a estrutura no padrão JWS definida na \[[RFC7515](https://datatracker.ietf.org/doc/html/rfc7515)\], e que inclui:

**\-Cabeçalho** (JSON Object Signing and Encryption – JOSE Header), onde se define o algoritmo utilizado e inclui informações sobre a chave pública ou certificado que podem ser utilizadas para validar a assinatura

_**\-Payload**_ (JWS Payload): conteúdo propriamente dito e detalhado na especificação da API, além de informações sobre claims JWT

**\-Assinatura digital** (JWS Signature): assinatura digital, realizada conforme parâmetros do cabeçalho

O payload das mensagens (requisição e resposta JWT) assinadas devem incluir as seguintes claims presentes na [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519#section-4.1):

**Nome**

**Tipo**

**Obrigatório**

**Descrição**

aud

string

true

(_**Requisição JWT**_): o Provedor do Recurso (p. ex. a instituição proponente) deverá validar se o valor do campo **aud** coincide com o endpoint sendo acionado.

(_**Resposta JWT**_): o cliente da API (p. ex. instituição credora) deverá validar se o valor do campo **aud** coincide com o seu próprio organisationId listado no diretório.

iss

string

true

(_**Requisição JWT**_ e _**Resposta JWT**_): o receptor da mensagem deverá validar se o valor do campo **iss** coincide com o organisationId da outra parte, listado no diretório.

jti

string

true

(_**Requisição JWT**_ e _**Resposta JWT**_): o valor do campo **jti** deverá ser preenchido com o UUID definido pela instituição de acordo com a [RFC4122](https://datatracker.ietf.org/doc/html/rfc4122) usando o versão 4.

iat

string

true

(_**Requisição JWT**_ e _**Resposta JWT**_): o valor do campo **iat** deverá ser preenchido com o horário da geração da mensagem e de acordo com o padrão estabelecido na [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519#section-2) para o formato _NumericDate_. A claim iat deverá ser gerada no Unix Time GMT+0 e sua verificação deverá possuir uma tolerância de +/- 60 segundos para cobrir pequenas diferenças nos relógios dos servidores dos participantes.

-   **A claim do “jti” deve ser única para um clientId dentro de um intervalo de tempo de 86.400 segundos, não podendo ser reutilizada neste período. Em caso de reutilização, deverá ser retornado o código de erro HTTP 403**
    
-   **As validações referentes as claims do JWT devem preceder a validação de idempotência (e.g. “jti”, “iat” e “iss”)**
    
    -   Cada elemento acima deve ser codificado utilizando o padrão Base64url \[[RFC4648](https://datatracker.ietf.org/doc/html/rfc4648#section-5)\] e, feito isso, os elementos devem ser concatenados com “.” (método JWS Compact Serialization, conforme definido na \[[RFC7515](https://datatracker.ietf.org/doc/html/rfc7515#section-3.1)\])
        

Formato da mensagem JWS:

_**▫ payload**_ = Base64url(**JOSE** _**Header**_) + "." + Base64url(_**payload**_ **JWT**) + "." + Base64url(_**digital signature**_)

Veja ao lado exemplo de mensagem JWS assinada e codificada e um exemplo de mensagem JWS decodificada

▫ <<Necessária uma outra proposta em complemento após a aprovação de um _endpoint_ da API de Portabilidade de Crédito para exemplificar o funcionamento>>

-   **Em caso de erro**
    
    -   Na validação da assinatura pelo Provedor do Recurso a API deve retornar mensagem de erro HTTP com status code 400 e a resposta deve incluir na propriedade _code_ do objeto de resposta de erro especificado na API (ResponseError) a indicação da falha com o conteúdo BAD\_SIGNATURE
        
    -   Erros na validação da mensagem recebida pela aplicação cliente (p. ex. instituição proponente) devem ser registrados e o Provedor do Recurso (p. ex. instituição credora) deve ser notificada
