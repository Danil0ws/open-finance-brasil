# Como Assinar o Payload - v4.0.0-beta.1 - Pagamentos

No contexto da API Payment Initiation, os payloads de mensagem de consentimento e de pagamento que trafegam tanto por parte da instituição iniciadora de transação de pagamento quanto por parte da instituição detentora de conta devem estar assinados. Abaixo temos as orientações para assinatura das mensagens JWS.

Informações complementares de segurança podem ser consultadas em [https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-financial-api-1\_ID3-ptbr.md](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-financial-api-1_ID3-ptbr.md) .

-   **Passo 1** - Identifique a chave privada e o certificado de assinatura correspondente a serem usados para assinatura:
    

As assinaturas devem ser realizadas com uso do certificado digital de assinatura especificado no [Padrão de Certificados Open Finance Brasil](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-certificate-standards-1_ID1-ptbr.md#certificado-de-assinatura-certificadoassinatura).

O certificado de assinatura deve ser válido no momento da criação do JWS.

-   **Passo 2** - Geração do JOSE Header
    

O JOSE Header deve conter os seguintes campos:

Nome

Tipo

Obrigatório

Descrição

alg

string

true

O algoritmo que será usado para assinar o JWS. Deve ser preenchido com o valor `PS256`.

kid

string

true

Deve ser obrigatoriamente preenchido com o valor do identificador da chave utilizado para a assinatura.

typ

string

true

É o tipo de conteúdo usado para trafegar mensagens na API. Deve ser preenchido com o valor `JWT`.

-   **Passo 3** - Montando a mensagem JWS
    

Para garantir a integridade e o não-repúdio das informações tramitadas em _API´s sensíveis e que indicam essa necessidade na sua documentação_, deve ser adotado a estrutura no padrão JWS definida na \[[RFC7515](https://datatracker.ietf.org/doc/html/rfc7515)\] e que inclui:

**Cabeçalho** (_JSON Object Signing and Encryption – JOSE Header_), onde se define o algoritmo utilizado e inclui informações sobre a chave pública ou certificado que podem ser utilizadas para validar a assinatura;

**Payload** (_JWS Payload_): conteúdo propriamente dito e detalhado na especificação da API além de informações sobre `claims` JWT ;

**Assinatura digital** (_JWS Signature_): assinatura digital, realizada conforme parâmetros do cabeçalho.

O payload das mensagens (requisição e resposta _JWT_) assinadas devem incluir as seguintes `claims` presentes na [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519#section-4.1):

Nome

Tipo

Obrigatório

Descrição

aud

string

true

(_**requisição JWT**_): o Provedor do Recurso (p. ex. a instituição Detentora da Conta) deverá validar se o valor do campo **aud** coincide com o endpoint sendo acionado.  
(_**resposta JWT**_): o cliente da API (p. ex. instituição Iniciadora) deverá validar se o valor do campo **aud** coincide com o seu próprio `organisationId` listado no diretório.

iss

string

true

(_**requisição JWT**_ e _**resposta JWT**_): o receptor da mensagem deverá validar se o valor do campo **iss** coincide com o `organisationId` da outra parte listado no diretório.

jti

string

true

(_**requisição JWT**_ e _**resposta JWT**_): o valor do campo **jti** deverá ser preenchido com o UUID definido pela instituição de acordo com a [RFC 4122](https://datatracker.ietf.org/doc/html/rfc4122) usando o versão 4.

iat

string

true

(_**requisição JWT**_ e _**resposta JWT**_): o valor do campo **iat** deverá ser preenchido com o horário da geração da mensagem e de acordo com o padrão estabelecido na [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519#section-2) para o formato _NumericDate_. A claim iat deverá ser gerada no Unix Time GMT +0 e sua verificação deverá possuir uma tolerância de +/- 60 segundos para cobrir pequenas diferenças nos relógios dos servidores dos participantes.

-   **A claim do “jti” deve ser única para um clientId dentro de um intervalo de tempo de 86.400 segundos, não podendo ser reutilizada neste período. Em caso de reutilização, deverá ser retornado o código de erro HTTP 403.**
    
-   **As validações referentes as claims do JWT devem preceder a validação de idempotência (e.g. “jti”, “iat” e “iss”)**
    

Cada elemento acima deve ser codificado utilizando o padrão Base64url \[[RFC4648](https://datatracker.ietf.org/doc/html/rfc4648#section-5)\] e, feito isso, os elementos devem ser concatenados com “.” (método JWS Compact Serialization, conforme definido na \[[RFC7515](https://datatracker.ietf.org/doc/html/rfc7515#section-3.1)\]).

Formato da mensagem JWS:

**payload** = Base64url(**JOSEHeader**) + "." + Base64url(**payload JWT**) + "." + Base64url(**digital signature**)

Veja ao lado exemplo de mensagem JWS assinada e codificada e um exemplo de mensagem JWS decodificada.

> Exemplo de requisição - JWS assinada e codificada

> Exemplo de requisição - JWS decodificada

> Exemplo de resposta - JWS assinada e codificada

> Exemplo de resposta - JWS decodificada

**Em caso de erro**

-   Na validação da assinatura pelo Provedor do Recurso a API deve retornar mensagem de erro `HTTP` com status code `400` e a resposta deve incluir na propriedade code do objeto de resposta de erro especificado na API (_ResponseError_) a indicação da falha com o conteúdo `BAD_SIGNATURE`.
    
-   Erros na validação da mensagem recebida pela aplicação cliente (p. ex. iniciador de pagamento) devem ser registrados e o `Provedor do Recurso` (p. ex. instituição detentora de conta) deve ser notificado.
