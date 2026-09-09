# Guia de Boas Práticas

### **OCSP e cache**

As respostas OCSP das ACs podem ser cacheadas pelo participante provedor do serviço de forma a permitir melhor performance na checagem necessária à conexão mTLS oriunda do consumidor do serviço, de acordo com a política de risco de cada instituição provedora.

**JWKS e cache**

As respostas JWKS do diretório obtidas pelos participantes podem ser cacheadas pelo participante de forma a evitar consultas recorrentes à Infraestrutura do diretório e permitir maior celeridade nas checagens de assinatura dos _payloads_ melhorando, assim, o tempo de resposta a qual o participante está sujeito.

O participante pode utilizar duas estratégias para definir quando solicitar a atualização (_refresh)_ de um objeto JWKS cacheado localmente:

-   _Update on error_: Consulta o objeto JWKS vigente quando a checagem com o objeto JWKS cacheado não obtém êxito
    
-   _Update on Webhook_: Consulta o objeto JWKS vigente quando recebe uma notificação de _Webhook_ do diretório informando da mudança, conforme consta na documentação que pode ser acessada através do link 16\. Configurando eventos de notificação no Diretório
    

**Captura do authorization code na receptora/iniciadora**

As implementações responsáveis pela captura do _authorization code_ nas URLs de _call back_ devem ser as mais simples possíveis, de forma a minimizar o risco de quebra de dependência e não execução da funcionalidade pelo _user-agent_ do usuário. Entre outras, deve-se evitar (em ordem decrescente de criticidade):

-   Dependências externas ao domínio da URL (exemplo: _captcha, analytics_);
    
-   Que o conteúdo da página seja cacheado no lado do usuário;
    
-   Dependências externas ao _host_ da URL;
    
-   Páginas com várias imagens;
    
-   Demais implementações que possam não funcionar por alguma indisponibilidade de rede ou dependência a partir da máquina do usuário.
    

Após a captura do _authorization code_, realize as demais operações de UX necessárias.

_**Payload**_ **de resposta e cache**

Nas APIs de negócio, as respostas dos sistemas de negócio podem ser cacheadas no API _Gateway_, desde que a arquitetura do sistema invalide dinamicamente os registros em cache que não espelhem mais a realidade.
