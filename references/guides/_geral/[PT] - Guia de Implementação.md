# [PT] - Guia de Implementação

-   **Opção 1: Iniciação de pagamento usando um Token de Identificação (id\_token) na Iniciadora**
    
    -   Adesão
        
    -   Liquidação
        
    -   Diretrizes para essa opção:
        
    -   Informações e validações de um id\_token
        
    -   Passo a passo para salvar um id\_token
        
    -   Passo a passo de uma Iniciação de Pagamento com o id\_token salvo
        
    -   Tabela de erros “HTTP 400 Bad Request”:
        
    -   Lista de possíveis erros:
        
    -   Diagrama de sequência fluxo CIBA
        
-   **Opção 2: Iniciação de pagamento CIBA sem redirecionamento** 
    
    -   Diretrizes para essa opção
        
    -   Paso a Passo
        
    -   Diagrama de sequência fluxo CIBA Sem Redirecionamento
        

## Opção 1: Iniciação de pagamento usando um Token de Identificação (id\_token) na Iniciadora

O serviço de Iniciação de Pagamentos do Open Finance Brasil implementa o fluxo de consentimento com redirecionamento para a autorização de pagamentos. Esse redirecionamento pode ser realizado via redirect entre aplicativos ou sites <> aplicativos. O CIBA fornece uma alternativa para esse fluxo onde ocorre um desacoplamento do processo e o canal para a autorização poderá ser um push-notification, SMS, email, WhatsApp etc.

### Adesão

Após um redirecionamento comum, o usuário, em um detentor de conta com CIBA habilitado, poderá aderir a essa forma de autorização no aceite de um consentimento.

### Liquidação

No ambiente do iniciador de pagamentos o usuário poderá selecionar a conta salva e receber o pedido de autorização via push-notification, SMS, email, WhatsApp etc. O usuário ainda deverá autorizar o consentimento para que o pagamento seja efetuado com sucesso.

### Diretrizes para essa opção:

1.  Iniciadores de pagamento e detentores de conta devem considerar o id\_token, obtido no fluxo de FAPI Hybrid Flow como identificação de usuário e conta a ser utilizado em endpoint para recuperar token de autenticação do pagamento;
    
2.  O id\_token deverá ter no mínimo 180 dias de expiração;
    
3.  Os iniciadores de pagamento deverão mostrar no fluxo de pagamento os dados do usuário e conta para ser selecionado, essa consulta poderá ser feita buscando os dados do endpoint de Consentimento de Pagamentos (GET /payments/v2/consents/{consentId}, dado /data/debtorAccount/number);
    
4.  Utilizar como base de experiência o guia de UX onde existirá um checkbox para “salvar conta para transações futuras” (link do guia de UX e figma);
    
5.  O id\_token deve ser utilizado na chamada de autorização através do parâmetro “id\_token\_hint”;
    
6.  Apenas o “poll mode” será utilizado para obter token para o envio do pagamento via endpoint Backchannel Authentication Endpoint do CIBA descrito no well-known da Detentora de Contas;
    
7.  O cancelamento do id\_token poderá ser realizado pela detentora de conta em casos de fraude ou por motivos de segurança;
    
8.  O cancelamento do id\_token poderá ser realizado pela iniciadora de pagamentos em caso de fraude ou por motivos de segurança, através da remoção do id\_token do cliente em sua base de dados. Com base nos protocolos FAPI e OIDF, apenas a remoção do id\_token é suficiente para interromper o uso do fluxo CIBA, uma vez que, após a remoção, a iniciadora de pagamentos não será capaz de referenciar o cliente.
    

### Informações e validações de um id\_token

Informação contidas em uma id\_token

**Parâmetros**

**Validações**

iss

·       Authorization Server deve estabelecer identificador, ou conjunto de identificadores "iss" padrão para uso em transações CIBA.- Authorization Server não deve aceitar "iss" diferente de seu próprio identificador, ou conjunto de identificadores, padrão.

sub

·       Authorization Server deve verificar se o identificador "sub" em questão já foi emitido para um cliente/conta, e se está válido dentro de seus requisitos.

aud

·       Authorization Server não deve aceitar "aud" diferente do client\_id de onde se origina a solicitação de autorização para o fluxo CIBA.

exp

·       "exp" deve ser estabelecido conforme políticas de risco da instituição Detentora de Conta.- Authorization Server não deve aceitar solicitações de autorização cuja data/hora é maior que "exp".

iat

·       Sem validações específicas.

auth\_time

·       Sem validações específicas.

nonce

·       Sem validações específicas para o AS.

acr

·       Se presente, o AS deverá aceitar apenas valores iguais ou acima dos requisitos de autenticação da Detentora para autorizar transações de pagamento.

amr

·       Se presente, o AS deverá aceitar apenas valores iguais ou melhores que os requisitos de autenticação da Detentora para autorizar transações de pagamento.

azp

·       Authorization Server não deve aceitar "azp" diferente do client\_id de onde se origina a solicitação de autorização para o fluxo CIBA.

Parâmetros para validação de um id\_token

Todos os parâmetros devem estar presentes no cabeçalho (header) do JWT.

**Parâmetros**

**Descrição**

**Valores recomendados**

alg

O parâmetro "alg" (algoritmo) identifica o algoritmo criptográfico usado para proteger o JWS/JWE. O valor de Assinatura JWS não é válido se o valor "alg" não representar um algoritmo suportado ou se não houver uma chave compatível para uso do algoritmo associado à entidade que assinou digitalmente o conteúdo.

PS256 ou PS512

jku

O parâmetro "jku" (JWK Set URL) é um URI (RFC3986) que se refere a um recurso para um conjunto de chaves públicas codificadas em JSON, uma das quais corresponde à chave usada para assinar digitalmente o JWS. As chaves DEVEM ser codificadas como um JWK Set.

O protocolo usado para adquirir o recurso DEVE fornecer proteção de integridade; uma solicitação HTTP GET para recuperar o JWK Set DEVE usar o Transport Layer Security (TLS); e a identidade do servidor DEVE ser validada, de acordo com a Seção 6 da RFC6125. (OPCIONAL)

jwk

O parâmetro "jwk" (JSON Web Key) é a chave pública que corresponde à chave usada para assinar digitalmente o JWS. Essa chave é representada como uma chave JWK. (OPCIONAL)

kid

O parâmetro "kid" (Key ID) é uma indica qual chave foi usada para proteger o JWS/JWE. Este parâmetro permite que os remetentes sinalizem explicitamente uma mudança de chave para os destinatários. O valor "kid" DEVE ser uma string com distinção entre maiúsculas e minúsculas. Quando usado com um JWK, o valor "kid" é usado para corresponder a um valor de parâmetro "kid" do JWK. (OPCIONAL)

x5u

O parâmetro "x5u" (X.509 URL) é um URI (RFC3986) referente a um recurso para o certificado de chave pública X.509 ou cadeia de certificados (RFC5280) correspondente à chave usada para assinar digitalmente o JWS. (OPCIONAL)

x5c

O parâmetro "x5c" (X.509 Certificate Chain) contém o certificado de chave pública X.509 ou cadeia de certificados (RFC5280) correspondente à chave usada para assinar digitalmente o JWS. (OPCIONAL)

x5t

O parâmetro "x5t" (X.509 Certificate SHA-1 Thumbprint) é uma impressão digital SHA-1 codificada em base64url (hash) da codificação DER do certificado X.509 (RFC5280) correspondente à chave usada para assinar digitalmente o JWS. (OPCIONAL)

x5t#S256

O parâmetro "x5t#S256" (X.509 Certificate SHA-256 Thumbprint) é uma impressão digital SHA-256 codificada em base64url (hash) da codificação DER do certificado X.509 (RFC5280) correspondente à chave usada para assinar digitalmente o JWS. Pode ser utilizado alternativamente ao "x5t". (OPCIONAL)

typ

O parâmetro "typ" (Type) é usado pelos aplicativos JWS para declarar o media type (IANA.MediaTypes) deste JWS completo. Destina-se ao uso pelo aplicativo quando mais de um tipo de objeto pode estar presente em uma estrutura de dados do aplicativo que pode conter um JWS; o aplicativo pode usar esse valor para eliminar a ambiguidade entre os diferentes tipos de objetos que podem estar presentes. (OPCIONAL)

JWT

cty

O parâmetro "cty" (Content Type) é usado por aplicativos JWS para declarar o media type (IANA.MediaTypes) do conteúdo protegido (payload). Destina-se ao uso pelo aplicativo quando mais de um tipo de objeto pode estar presente no JWS Payload; o aplicativo pode usar esse valor para eliminar a ambiguidade entre os diferentes tipos de objetos que podem estar presentes.

ao invés de usar “application/example” usar “example”

crit

O parâmetro "crit" (Critical) indica que extensões para esta especificação e/ou \[JWA\] estão sendo usadas e DEVEM ser compreendidas e processadas. Seu valor é um array com os nomes dos Parâmetros do Cabeçalho presentes no Cabeçalho do JOSE que usam essas extensões.

### Passo a passo para salvar um id\_token

Lembre-se, o fluxo para a geração de um id\_token é um fluxo de consentimento FAPI Hybrid-Flow comum! A Iniciadora de Pagamentos deverá salvar o id\_token que vem no redirecionamento de volta da detentora via query parameters.

1.  Siga os passos do Diagrama de Sequência de uma Iniciação de Pagamento via Hybrid-Flow;
    
2.  Na etapa de recebimento do **code, state, id\_token** no redirectURL (redirecionamento de volta da detentora para a iniciadora) a iniciadora deve salvar o id\_token que também vem nos parâmetros da url de redirect. Atentar-se ao item 4 do diagrama de sequência do link acima;
    
3.  Realizar o pagamento normalmente, pois apenas no próximo pagamento será possível a utilização do canal CIBA para a comunicação com o cliente para autorizar um consentimento.
    

### Passo a passo de uma Iniciação de Pagamento com o id\_token salvo

1.  Criar um consentimento fase 3 para Iniciação de Pagamentos padrão;
    
2.  Receber resposta da criação do consentimento com status **AWAITING\_AUTHORISATION**;
    
3.  Requisitar Backchannel Authentication Endpoint do CIBA para autorização do consentimento, verificar payload abaixo:
    

Os campos devem ser codificados para url (URL Encoded). No exemplo foi deixado como plain text para facilitar o entendimento.

O BackchannelAuthenticationEndpoint deve ser encontrado no _**.well-known**_ da detentora.

A iniciadora deve enviar o id do consentimento no campo scope junto com o scope _**openid**_.

A detentora deverá validar o id\_token de acordo com as tabelas referenciadas acima dos itens.

### Tabela de erros “HTTP 400 Bad Request”:

1.  **invalid\_request**: The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, contains more than one of the hints, or is otherwise malformed.
    
2.  **invalid\_scope**: The requested scope is invalid, unknown, or malformed.
    
3.  **expired\_id\_token\_hint**: The id\_token hint provided in the authentication request is not valid because it has expired.
    
4.  **unknown\_user\_id**: The OpenID Provider is not able to identify which end-user the Client wishes to be authenticated by means of the hint provided in the request (id\_token\_hint).
    
5.  **unauthorized\_client**: The Client is not authorized to use this authentication flow.
    
6.  **invalid\_id\_token\_hint**: The id\_token is invalid and can’t be used in the flow.
    

4.  Resposta do Backchannel Authentication Endpoint:
    

**auth\_req\_id**: identificador da requisição de autenticação;

**expires\_in**: tempo de expiração do auth\_req\_id em segundos, tempo máximo que a iniciadora poderá fazer o polling do `/token`;

**interval**: intervalo mínimo do polling no `/token` que deve ser maior que 2 segundo;

5.  Ao receber a chamada do Backchannel Authentication Endpoint, a detentora deve informar o usuário sobre a solicitação de pagamento, utilizando o canal desacoplado (SMS, push notification, etc) de sua escolha para autenticar o cliente de acordo com suas políticas e autorizar o pagamento.
    
6.  Com o pagamento reconhecido pelo usuário a detentora muda o status do consentimento para AUTHORISED.
    
7.  Em posse do auth\_req\_id a iniciadora deve chamar o endpoint `/token` em um intervalo de tempo determinado pelo campo `interval` da resposta da chamada do Backchannel Authentication Endpoint para receber o `access_token` , `id_token` e o `refresh_token` do consentimento autorizado até um tempo limite determinado pelo campo `expires_in` da resposta. Esse é o modo poll.
    

Os campos devem ser codificado para url (URL Encoded). No exemplo foi deixado como plaintext para facilitar o entendimento.

**grant\_type**: deve ser urn:openid:params:grant-type:ciba

**auth\_req\_id**: identificador da requisição de autenticação recebido na resposta da chamada do Backchannel Authentication Endpoint.

8.  Realizar polling para obter o status da autorização da solicitação de consentimento, uma vez autorizada a solicitação de pagamento a detentora deve retornar uma resposta de sucesso com statusCode 200. Para os casos onde o consentimento ainda não foi aceito ou foi rejeitado a detentora deverá retornar 403 com os error codes listados abaixo.
    

Exemplo de resposta de sucesso conforme CIBA.Core1 10.1.1:

Exemplo de resposta de erro conforme CIBA.Core1 11:

### Lista de possíveis erros:

**Error Code**

**Error Description**

authorization\_pending

The user has not yet been authenticated, and the authorization request is still pending

slow\_down

The authorization request is still pending, and the client must increase the interval for polling requests by at least x seconds

expired\_token

The transaction (auth\_req\_id) has expired. The client must start over with a new Authentication Request

access\_denied

The user did not consent to the authorization request

9.  Seguir com o processo de uma iniciação de pagamento e realizar as chamadas na API de pagamento, caso o acesso for concedido com sucesso.
    

### Diagrama de sequência fluxo CIBA

![Diagrama\_CIBA\_PT.png](images/Diagrama_CIBA_PT.png)

**Opção 2: Iniciação de pagamento CIBA sem redirecionamento** 

O serviço de Iniciação de Pagamentos do Open Finance Brasil implementa o fluxo de consentimento com redirecionamento para a autorização de pagamentos. Esse redirecionamento pode ser realizado via redirect entre aplicativos ou sites <> aplicativos conhecido como fluxo Hybrid-Flow. O CIBA fornece uma alternativa para esse fluxo onde ocorre um desacoplamento do processo e o canal para a autorização poderá ser um push-notification, SMS, email, WhatsApp etc. 

Nesta opção não existe nenhum vínculo e validação de id\_token, os dados do próprio consentimento são utilizados para realizar todo o processo de autorização de um consentimento.

**Diretrizes para essa opção:**

1.  Apenas o “poll mode” será utilizado para obter token para o envio do pagamento via endpoint Backchannel Authentication Endpoint do CIBA descrito no well-known da Detentora de Contas;
    
2.  A  Detentora de Contas  pode a qualquer momento bloquear novas chamadas de um iniciador por suspeita de fraude ou validação interna, obrigando este a entrar em contato via Service Desk para regularizar o cpf/cnpj específico.
    
3.  O consentimento contém a identificação do usuário loggedUser e o businessEntity que permite que o Detentor de Contas saiba quem sensibilizar via push notitication/email etc para a autorização do consentimento. 
    

**Passo a passo** 

1.  Com mais fatores de autenticação fluxo de pagamento, o usuário final requisita um pagamento ou autorização dos produtos Open Finance.
    
2.  Criação do consentimento de qualquer produto Open Finance (as-is no Hybrid Flow)
    
3.  Consentimento criado e retornado com status awaiting\_authorization (as-is no Hybrid Flow)
    
4.  Resposta da criação do consentimento (as-is no hybrid flow)
    
5.  Chamada ao Backchannel Authentication Endpoint do CIBA para autorização do consentimento
    

6.  Os campos dever ser codificado para url (URL Encoded). No exemplo foi deixado como plain text para facilitar o entendimento.  
    O BackchannelAuthenticationEndpoint deve ser encontrado no _**.well-known**_ da detentora.  
    A iniciadora deve enviar o id do consentimento no campo scope junto com _**openid.**_
    

7.  Resposta do Backchannel Authentication Endpoint
    

-   auth\_req\_id: identificador da requisição de autenticação;
    
-   expires\_in: tempo de expiração do auth\_req\_id em segundos, tempo máximo que a iniciadora podera fazer o polling do /token;
    
-   interval: intervalo minimo do polling no /token que deve ser maior que 2 segundos.
    

8.  A Detentora notifica o usuário (via push, SMS ou e-mail) para autorizar o pagamento.
    
9.  O usuário acessa o app/site da Detentora.
    

10\. O usuário se autentica e autoriza o consentimento.

11\. O status do consentimento é atualizado para AUTHORISED.

12\. Com o auth\_req\_id , a Iniciadora deve chamar o endpoint /token em intervalos definidos pelo campo interval da resposta do _Backchannel Authentication Endpoint_. O objetivo é obter o access\_token, id\_token e refresh\_token do consentimento autorizado. Esse processo de polling deve continuar até o limite de tempo especificado pelo campo expires\_in, também fornecido na resposta do _Backchannel Authentication Endpoint_.  
O polling deve começar apenas depois do status do consentimento ser atualizado por uma notificação de evento via webhook e GET consequente do consentimento com status AUTHORISED

-   Os campos devem ser codificado para url (URL Encoded). no exemplo foi deixado como plain text para facilitar o entendimento
    
-   grant\_type: deve ser urn:openid:params:grant-type:ciba
    
-   auth\_req\_id: identificador da requisição de autenticação recebido na resposta da chamada do Backchannel Authentication Endpoint
    

13\. Enquanto a solicitação de pagamento não for autorizada pelo cliente, a detentora deve retornar uma resposta de erro com statusCode 403, E uma vez autorizada a solicitação de pagamento a detentora deve retornar uma resposta de sucesso com statusCode 200.

 Exemplo de resposta de sucesso conforme CIBA.Core1 10.1.1:

14\. Exemplo de resposta de erro conforme CIBA.Core1 11:

15\. Possíveis erros:

**Error Code**

**Error Description**

authorization\_pending

The user has not yet been authenticated, and the authorization request is still pending

slow\_down

The authorization request is still pending, and the client must increase the interval for polling requests by at least x seconds

expired\_token

The transaction (auth\_req\_id) has expired. The client must start over with a new Authentication Request

access\_denied

The user did not consent to the authorization request

16\. Após a Iniciadora receber o access\_token e refresh\_token do consentimento autorizado, ela deve iniciar o pagamento de acordo com o fluxo padrão já conhecido.

17.  Ao receber a solicitação de pagamento, a Detentora processa a transação e, com o status 201 (sucesso) ou 422 (erro de validação), o consentimento é marcado como "consumido".
     
18.  A Detentora responde à Iniciadora com o resultado do processamento do pagamento, seguindo o mesmo fluxo do _Hybrid Flow_.
     
19.  A Iniciadora continua a consultar o status do pagamento usando _polling_ no endpoint de consulta ou aguarda evento de webhook para fazer polling
     
20.  A Detentora atualiza a Iniciadora com o status final do pagamento
     

**Diagrama de sequência fluxo CIBA sem Redirecionamento**

![image-20241203-161042.png](images/image-20241203-161042.png)
