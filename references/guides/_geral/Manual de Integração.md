# Manual de Integração

O presente documento demonstra o uso das APIs da Plataforma de Coleta de Métricas. 

## Referências 

### Documentação da API

A documentação oficial da API se encontra em Documentação da API - PCM

### Documentação funcional

A documentação funcional pode ser encontrada em Plataforma de Coleta de Métricas

## Procedimento de integração

### Visão geral

O diagrama abaixo ilustra os principais componentes da plataforma

![5f891e18-a348-4ee8-b32c-50cb49c32ff6.png](images/5f891e18-a348-4ee8-b32c-50cb49c32ff6.png)

Para que reportes sejam enviados para a PCM é necessário que o participante obtenha um token de acesso, o que é feito através de um endpoint de autenticação que é acessível através de uma conexão mTLS. De posse do token, o participante pode efetuar os envios para os endpoints da API descritas na documentação. É necessário o uso de certificados válidos para a recuperação do token, em contrapartida os envios de reportes são feitos sem a necessidade de uma conexão mTLS.

### Endereços base

Os endereços base em cada ambiente, bem como suas respectivas datas de validade são os abaixo:

**Ambiente**

**Endereço**

**Tipo**

**Validade**

Sandbox

[https://api.pcm.sandbox.openfinancebrasil.org.br](https://api.pcm.sandbox.openfinancebrasil.org.br)

API

Indeterminada

[https://auth.pcm.sandbox.openfinancebrasil.org.br](https://api.pcm.sandbox.openfinancebrasil.org.br)

Autenticação

Piloto

[https://api.pcm.piloto.openfinancebrasil.org.br](https://api.pcm.piloto.openfinancebrasil.org.br)

API

Disponível até 31/01/2023

[https://auth.pcm.piloto.openfinancebrasil.org.br](https://api.pcm.piloto.openfinancebrasil.org.br)

Autenticação

Produção

[https://api.pcm.openfinancebrasil.org.br](https://api.pcm.openfinancebrasil.org.br)

API

Disponível a partir de 01/02/2023

[https://auth.pcm.openfinancebrasil.org.br](https://api.pcm.openfinancebrasil.org.br)

Autenticação

## Autenticação

O procedimento segue o fluxo de `client_credentials` da especificação oauth2, sendo que o acesso ao endpoint precisa ser feito usando uma conexão mTLS. As credenciais, bem como os certificados aceitos em cada um dos ambientes estão descritos abaixo:

**Ambiente**

**Credenciais**

**Certificados**

Sandbox/Piloto

client\_id do Software Statement do diretório de sandbox

Certificado emitido pelo diretório central de sandbox

Produção

client\_id do Software Statement do diretório de produção

Certificado emitido por autoridade certificadora aceita pelo ecossistema \[1\]

O endpoint de recuperação de token é: 

`<endereço de autenticação conforme ambiente>/token/`

**Importante**: manter a última barra ("/") depois de _token_. 

Para se recuperar um token, é necessário estabelecer uma comunicação mTLS entre o cliente que está fazendo a chamada e o authorization server, utilizando um certificado de cliente. Os passos para configuração de certificados cliente no Postman podem ser encontrados em [https://learning.postman.com/docs/sending-requests/certificates/](https://learning.postman.com/docs/sending-requests/certificates/).

Os tokens gerados estão configurados com duração de 21600 segundos (6 horas). Não há limitação para a quantidade de tokens gerados muito embora seja importante que eles sejam reaproveitados no período de validade. É possível fazer a introspecção do token para se determinar até quando ele é válido, uma vez que ele não é criptografado.

Para recuperar um token é necessário fazer uma chamada POST usando um payload com os seguintes campos:

client\_id 

`client_id` do software statement ligado ao certificado usado no acesso

grant\_type 

Fixo: `client_credentials`

Não há a necessidade do envio do `client_secret`, uma vez que a camada de transporte via certificado cliente já assegura a autenticidade do chamador. 

Os campos relevantes devolvidos por esse endpoint são: 

access\_token 

Token no padrão jwt para acesso às APIs 

expires\_in 

Número de segundos em que o token é válido ![5f891e18-a348-4ee8-b32c-50cb49c32ff6.png](images/5f891e18-a348-4ee8-b32c-50cb49c32ff6.png)

token\_type 

O tipo do token fornecido (nesse caso, Bearer) 

### Exemplo

Envio de um request para o endereço de autenticação em sandbox: 

nonewide1800

Resposta: 

wide1800

Alternativamente, é possível utilizar o fluxo fresh, ficando a cargo das instituições o comportamento mais adequado a cada situação.

`<endereço de autenticação conforme ambiente>/token-fresh/`

O fluxo fresh sempre gera um token novo, ignorando qualquer token em cache para leitura. Após a leitura, salva esse token em cache.

O comportamento desse endpoint é:

-   Ao chamar o endpoint fresh, o sistema **não reutiliza** token de cache existente.
    
-   O sistema chama o provedor de autenticação e obtém **um token novo**.
    
-   Em seguida, esse token novo **também é gravado no cache**.
    
-   Depois disso, uma chamada ao endpoint `/token` pode retornar esse token recém-gerado, desde que ele ainda esteja válido.
    

Em resumo: **fresh ignora cache na entrada, mas alimenta cache na saída**.

Para a maioria das requisições, o uso de **token em cache continua sendo o comportamento padrão**, trazendo:

-   menor latência
    
-   menos chamadas externas
    
-   melhor escalabilidade do sistema
    

Isso mantém o sistema **rápido e eficiente para uso cotidiano**.

Cenário

Endpoint recomendado

Uso geral

`/token`

Garantir token novo na chamada atual

`/token-fresh`

Reutilizar token válido para performance

`/token`

## Interação com a API 

Para realizar chamadas localmente, realize a importação da documentação OpenAPI no seu cliente HTTP (Postman: [https://learning.postman.com/docs/integrations/available-integrations/working-with-openAPI/](https://learning.postman.com/docs/integrations/available-integrations/working-with-openAPI/) , Insomnia: [https://docs.insomnia.rest/insomnia/import-export-data#import-data](https://docs.insomnia.rest/insomnia/import-export-data#import-data) ). Esse procedimento irá criar as collections nos formatos descritos pela documentação. 

O token gerado deverá ser enviado nas chamadas da API do PCM dentro do header Authorization, identificando o tipo do token conforme abaixo: 

`Authorization: <token type> <token>` 

Onde `<token type>` pode ser Bearer, Basic, etc (no caso das APIs da PCM, será aceito apenas tokens do tipo Bearer), e o token recuperado no processo de autenticação. 

Usando o exemplo da chamada da sessão anterior, o header deverá ser mandado com o seguinte conteúdo: 

`Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IkFiT` 

### Exemplo

Para o envio de um reporte como server, o request tem que ser como o exemplo abaixo:

wide1800

Resposta

wide1800

## Exemplos de chamadas

Os exemplos abaixo utilizam as instituições que participaram do Piloto da PCM. São elas (em ordem alfabética): Banrisul, BV, Caixa e Gerencianet.

Os cenários de teste foram montados a fim de demonstrar o uso da API. A escolha de qual instituição faz qual chamada foi aleatória, e tem o único objetivo de exemplificar os tipos de chamadas em seus cenários.

### Cenário 1: PAIRED

BV faz chamada para Caixa, ambos enviam reportes sem erros. O status esperado para os dois reportes finais é **PAIRED**. 

BV:

wide1800

Caixa:

wide1800

### Cenário 2: PAIRED\_INCONSISTENT

Caixa reporta transação feita com Banrisul, mas os dados de consistência não estão iguais. O status esperado para os dois reportes finais é **PAIRED\_INCONSISTENT.** 

Caixa:

wide1800

Banrisul:

wide1800

### Cenário 3: SINGLE

Banrisul reporta timeout em uma transação com BV, sendo que a geração do fapiInteractionId seria feita pelo server. O status desse reporte será `SINGLE`.

wide1800

### Cenário 4: DISCARDED

Gerencianet envia um reporte sem o campo httpMethod, que é um campo obrigatório. O status do reporte será registrado como DISCARDED, e o status retorno da chamada será 400. 

wide1800

Resposta

wide1800

### Cenário 5: DISCARDED

Caixa envia reporte com dado inconsistente no campo endpoint (veja lista dos endpoints válidos na Documentação da API - PCM e na documentação funcional). Status do reporte tem que ser DISCARDED com a devida justificativa, e o status da resposta 400. 

wide1800

Resposta

wide1800

### Cenário 6: DISCARDED 

Banrisul envia reporte sem os identificadores de receptor e transmissor. Status do reporte deverá ser DISCARDED com a devida justificativa e o status de retorno, 400. No entanto, apenas o Banrisul poderá consultar esse reporte. 

wide1800

* * *

\[1\] Padrão de certificação do Open Finance Brasil v2.1
