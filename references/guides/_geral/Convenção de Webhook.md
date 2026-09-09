# Convenção de Webhook

Webhook é uma funcionalidade de retorno assíncrono de chamadas baseadas no protocolo HTTP que permite comunicação leve e orientada a eventos entre 2 interfaces de programação de aplicativos (APIs). O Webhook pode ser usado para diminuir custos operacionais entre as instituições participantes possibilitando um pooling otimizado para obter informações dos recursos e podem ser usados para acionar fluxos de trabalho de automações internas das instituições.

A instituição (detentora de contas e/ou transmissora de dados) envia uma notificação à iniciadora de pagamento e/ou receptora de dados informando que ocorreu uma mudança no estado do recurso e ela deverá consultar o recurso para obter mais informações.

**Endpoints que possuem a funcionalidade de Webhook:**

/payments/v2:

1.  POST /consents
    
2.  POST /pix/payments
    

**Orientações:**

Todos os endpoints do Webhook utilizam-se de mTLS para autenticação, não possuem scopes e permissions específicos de segurança. Toda a segurança é feita via certificado(mTLS – BRCAC).

Dado que as URLs do ecossistema são formadas com a configuração abaixo:  
<host> / <string> / <api> / <versão> / <recurso>

Para a utilização desse recurso é necessário que:

-   Iniciadoras de pagamentos e/ou Receptora de dados: Precisam cadastrar a sua URI base (<host>) no diretório de participantes no campo “**API Webhook**”;
    
-   Detentoras de contas e/ou Transmissora de dados: Precisam construir a URI de notificação da seguinte forma:
    

**Exemplo de URI do consentimento**

![webhook\_consent.png](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/105021661/child/attachment/att118784039/download)

**Exemplo de URI do pagamento**

![webhook\_payment.png](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/105021661/child/attachment/att118784045/download)

-   Quando habilitar a funcionalidade de Webhook para a API de Pagamentos, a iniciadora de pagamentos deverá estar apta a receber notificações nos seguintes endereços:
    
    -   `https://itp.com/kong3/open-banking/webhook/[Versão do Webhook]/payments/[Versão da API]/consents/{consentId}`
        
    -   `https://itp.com/kong3/open-banking/webhook/[Versão do Webhook]/payments/[Versão da API]/pix/payments/{paymentId}`
        

**Versionamento do Webhook:** Ocorrerá de forma desacoplada de qualquer API presente no ecossistema. Tal decisão tem por objetivo possibilitar o reaproveitamento da especificação quando o Webhook for adotado para outras APIs no ecossistema do Open Finance Brasil, sendo assim:

-   `A versão do Webhook não fará parte da URL base do serviço, a URL base representa apenas o <host> da iniciadora que receberá as notificações;`
    
-   `O restante da URL será formada da seguinte maneira: uma string "/open-banking/webhook", versão do Webhook, nome da API, sua versão e qual endpoint dentro da API que este Webhook notificará, por exemplo:`
    
    -   `/open-banking/webhook/[Versão do Webhook]/[nome_da_API]/[Versão_da_API]/[endpoint_da_API]`
        
-   Utilizando a API de Iniciação de Pagamentos como exemplo, ficaria da seguinte forma:
    
    -   `/open-banking/webhook/[Versão do Webhook]/payments/[Versão_da_API]/consents/{consentId}`
        
    -   `/open-banking/webhook/[Versão do Webhook]/payments/[Versão_da_API]/pix/payments/{paymentId}`
        

**Prazo para sincronização:** As detentoras de conta e transmissoras de dados devem sincronizar o seu mecanismo de notificações por Webhook com o fluxo DCR/DCM de modo que as notificações para as iniciadoras de pagamento e receptoras de dados se iniciem em até 10 minutos após a execução do DCR/DCM.

**Comportamento durante o período de convivência entre versões de API:**  
Durante este período, iniciadoras de pagamento ou transmissoras de dados que estiverem com a funcionalidade de notificações via Webhook ativa no diretório de participantes PRECISAM também estar habilitadas a receber as notificações de Webhook para o endpoint que possuir esta capacidade na nova versão da API, por exemplo, supondo que a versão 3 da API de iniciação de pagamentos ( `/payments/v3` ) tenha sido lançada em produção (atualmente só há a versão 2), durante o período de convivência entre a `/payments/v2` e a `/payments/v3` , a iniciadora precisaria ter os seguintes endereços habilitados para receber as notificações:

-   `https://itp.com/kong3/open-banking/webhook/[Versão do Webhook]/payments/v2/pix/payments/{paymentId}`
    
-   `https://itp.com/kong3/open-banking/webhook/[Versão do Webhook]/payments/v3/pix/payments/{paymentId}`
    

Como pode ser visto no exemplo acima, iniciadoras de pagamentos e transmissoras de dados, assim como detentoras de contas e receptoras de dados, precisam manter a gestão entre as versões que iniciaram a troca de informações entre elas. Uma alteração feita a um recurso utilizando uma versão “x” de uma API qualquer, que possua endpoints passíveis de notificação via Webhook, notificará sempre utilizando essa versão “x”, como parâmetro para construção de sua URI de notificação. Por exemplo, se durante o período de convivência citado anteriormente, tivermos um pagamento sendo enviado via API da `/payments/v2` , então a resposta deverá ser obrigatoriamente via Webhook `/payments/v2`
