# MQD Manual de Instalação

O presente documento fornece orientações para instalação do Motor de Qualidade de Dados nas Instituições Financeiras participantes do Open Finance Brasil.

11falsenonelistfalse

# Instalação

O primeiro passo é clonar o código do repositório (disponível no Github) para a sua pasta local.

wide760![image-20230918-141824.png](images/image-20230918-141824.png)

Em seguida, valide se o clone foi realizado corretamente em sua pasta local.

wide760![image-20230918-142001.png](images/image-20230918-142001.png)

Acesse a pasta do código criada localmente.

wide760![image-20230918-142020.png](images/image-20230918-142020.png)

Após acessar a pasta, é necessário compilar e criar a imagem que será utilizada pelo Docker para o container onde o Motor de Qualidade de Dados estará alocado.

wide760![image-20230918-142218.png](images/image-20230918-142218.png)

A seguir, valide se a imagem foi criada corretamente.

wide760![image-20230918-142228.png](images/image-20230918-142228.png)

Modifique as variáveis ​​de ambiente de acordo com as necessidades no arquivo:

wide760

wide760

### Variáveis de ambiente

**Nome**

**Descrição**

**Valores**

API\_PORT

Porta que será usada para expor os endpoints da API

":" + porta

SERVER\_ORG\_ID

ID da organização da instituição financeira

Existem 2 parâmetros de configuração, um enviado no cabeçalho e outro como parte da configuração da aplicação (variável de ambiente).  A configuração como variável de ambiente deve indicar o ID da organização do IF onde o motor está sendo instalado (ex.: ID da Instituição Financeira no Diretório Central)

Organisation Id Válido

REPORT\_EXECUTION\_WINDOW

Indica a janela de execução para envio de relatórios,  
**é um campo opcional, caso não esteja definido seu valor será carregado automaticamente**

\> 0, < 60

REPORT\_EXECUTION\_NUMBER

Indica a quantidade de relatórios que devem ser processados ​​antes do envio, caso a quantidade de relatórios atinja o limite, o relatório é enviado automaticamente e o timer da janela de tempo é reiniciado  
**é um campo opcional, caso não esteja definido seu valor será carregado automaticamente**

\>0, < 2000000

ENVIRONMENT

Indica o ambiente em que o aplicativo está sendo instalado

PROD  
SANDBOX  
DEV

LOGGING\_LEVEL

Indica o nível de rastreio que será utilizado na aplicação

DEBUG  
INFO  
WARNING  
ERROR  
FATAL

APPLICATION\_MODE

Indica a forma como será executada a aplicação, isso dependerá se se trata de uma instituição do tipo transmissora ou receptora.

A obrigação apenas define a instalação como TRANSMISSOR, mas se desejar instalar em ambos os modos (RECEPTORA / TRANSMISSORA) será necessário ter 2 instalações.

TRANSMITTER  
RECEIVER

PROXY\_URL

Indica a url onde será encontrado o Proxy que estabelece conexão segura com o servidor.

URL válida

### Volumes

**Volume**

**Descrição**

/etc/nginx/conf.d/default.conf

Volume do arquivo de configuração NGINX deve ser modificado para utilizar a configuração necessária de acordo com o ambiente onde será instalado  
./proxy/default.prd.conf  
./proxy/default.sandbox.conf  
./proxy/default.dev.conf

/etc/ssl

Volume que indica a pasta contendo os arquivos de certificados de acordo com o arquivo de configuração  
/etc/ssl/client.crt  
/etc/ssl/client.crt  
**Caso os nomes sejam diferentes do configurado, esses nomes podem ser modificados no arquivo/caminho específico**

Por fim, use o Docker Compose para iniciar a aplicação do Motor de Qualidade de Dados.

wide760

![image-20240220-182424.png](images/image-20240220-182424.png)

Em seguida, execute o comando para enviar um request de teste a API do Motor de Qualidade de Dados.

wide760

![image-20240220-182526.png](images/image-20240220-182526.png)wide760

**Importante!**

Hoje não há limite para o MQD, tanto no tamanho quanto na quantidade de mensagens. Mas ainda recomendamos o monitoramento constante do contêiner da aplicação, pois dependendo da carga entregue será necessário aumentar os recursos (RAM e CPU) para processar adequadamente todas as mensagens.

# **Configuração**

Para integrar a validação de dados ao Motor de Qualidade de Dados, é necessário atualizar os serviços que deseja validar conforme fluxo mostrado abaixo.

![receptora\_fluxo\_API.png](images/receptora_fluxo_API.png)

Para isso é necessário consumir a API conforme especificação disponível em [mqd-client/docs/specification/mqd-client-openapi.yml at main · OpenBanking-Brasil/mqd-client (github.com)](https://github.com/OpenBanking-Brasil/mqd-client/blob/main/docs/specification/mqd-client-openapi.yml), gerando assim uma nova solicitação ao obter a resposta da TRANSMISSORA.

Para a tratativa de erros no processamento do MQD ou para envio do request para ele, espera-se conseguir enviar 100% das transações para processamento, porém, podem ocorrer pequenas perdas que não afetariam os resultados. Por esta razão recomendamos uma abordagem padrão incluindo 3 tentativas no momento da integração.

O relatório pode ser enviado minutos ou horas depois de acontecer, porém deve-se levar em consideração o seguinte:

1.  O mecanismo enviará os resultados da validação a cada 15 minutos, portanto o melhor cenário é que o envio da transação não ultrapasse esta janela de tempo.
    
2.  Evite acumular transações a serem enviadas ao MQD, o que pode sobrecarregar os requisitos de processamento e, em última análise, causar a ocorrência de mais erros.
    

Uma política que pode funcionar seria de 3 tentativas:

-   10 segundos
    
-   30 segundos
    
-   1 minuto
    

Jitter: insira um valor aleatório (+/-) em segundos, evitando que todas as novas tentativas aconteçam ao mesmo tempo.

Se a % de solicitações que necessitam de nova tentativa for muito alta, será necessário analisar os tipos de problemas e iniciar um cenário de melhoria.

É necessário incluir as informações do cabeçalho nesta nova solicitação: 

**Variável**

**Descrição**

**Exemplo**

serverOrgId

Para Instituições Receptoras: Identificador da TRANSMISSORA onde a informação foi solicitada

Para Instituições Transmissoras: Identificador da RECEPTORA que solicitou a informação

Para eliminar a necessidade de criar diferentes endpoints para RECEPTORA e TRANSMISSORA e incluir parâmetros diferentes, existe um único parâmetro geral **serverOrgId**, que no caso de instalação como TRANSMISORA, será o id da organização que está solicitando o informações (clientOrgID)

c73bcdcc-2669-4bf6-81d3-e4ae73fb11fd

endpointName

Nome do endpoint que foi solicitado, como descrito na documentação, sem incluir as informações dos parâmetros dentro da URI

/accounts/v2/accounts/{accountId}

versionHeader

Validar diferentes versões da API em períodos de convivência

Esta variável é opcional

2.0.0

# Atualização

Para atualizar o Motor de Qualidade de Dados para uma nova versão, siga os passos abaixo.

### 1\. Consultar o Changelog

Antes de atualizar, verifique as alterações da nova versão no repositório:

wide1800true

Verifique se há breaking changes ou novas variáveis de ambiente necessárias.

### 2\. Atualizar a imagem

Faça pull do código atualizado e reconstrua a imagem Docker:

wide1800true

### 3\. Reiniciar o container

Pare o container existente e inicie com a nova imagem:

wide1800true

### 4\. Validar o funcionamento

Execute uma requisição de teste para confirmar que o MQD está operacional:

wide1800true

Um retorno HTTP 200 com body `{}` confirma que o serviço está recebendo as mensagens corretamente.

### Atualização automática de schemas

O MQD baixa automaticamente a configuração de APIs e versões suportadas do servidor central (endpoint `GET /settings`). **Não é necessário atualizar manualmente os JSON Schemas** — o sistema faz isso periodicamente.

Quando uma nova versão de API entra em vigência no ecossistema, o servidor central atualiza a configuração e os clientes MQD recebem os novos schemas automaticamente no próximo ciclo de sincronização.

### Verificação de versão

Para verificar qual versão de configuração o MQD está utilizando, consulte os logs do container com `LOGGING_LEVEL=INFO` ou superior. O log de inicialização indicará a versão de configuração carregada.

### Rollback

Se a nova versão apresentar problemas:

1.  Pare o container com a versão nova
    
2.  Rebuild a imagem a partir da tag/commit anterior:
    
    true docker build --no-cache -f infra/dockerfile/dockerfile-minimal -t mqd-client . \]\]>
3.  Reinicie com a imagem anterior:
    
    true

O MQD não persiste estado local — todas as mensagens não enviadas serão perdidas no restart. Por isso, recomenda-se realizar a atualização em janelas de menor tráfego para minimizar a perda de validações não reportadas.

* * *

> **Importante:** Caso a nova versão do MQD inclua suporte a novas APIs que ainda não estejam configuradas no servidor central, a validação dessas APIs só estará disponível após a atualização da configuração server-side. Consulte o Squad Qualidade de Dados para verificar o calendário de ativação.
