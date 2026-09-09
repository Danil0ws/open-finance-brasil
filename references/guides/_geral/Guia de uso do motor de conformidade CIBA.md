# Guia de uso do motor de conformidade CIBA

## 1\. Objetivo

Este guia orienta os participantes do ecossistema Open Finance Brasil na configuração e na execução dos testes CIBA disponíveis no motor de conformidade da OpenID Foundation.

Nesta etapa, o motor contempla testes para:

-   **Relying Parties (RP)** — Receptores/clientes;
    
-   **OpenID Providers (OP)** — Transmissores/servidores, com **cliente estático**.
    

> **Importante:** os testes de OP com cliente dinâmico serão disponibilizados posteriormente.

## 2\. Ambientes e materiais de apoio

-   **Motor de conformidade — ambiente de desenvolvimento:**  
    [https://review-app-dev-branch-26.certification.openid.net](https://review-app-dev-branch-26.certification.openid.net)
    
-   **Ambiente oficial de certificação:**  
    [https://www.certification.openid.net](https://www.certification.openid.net)
    

O ambiente de desenvolvimento é o ambiente de referência para a etapa atual de testes. Ele deverá ser utilizado até que sejam divulgadas novas orientações para a transição ao ambiente definitivo de certificação.

Os testes realizados nesta etapa têm caráter preparatório e destinam-se à evolução e à maturação dos cenários. A certificação será conduzida posteriormente na versão estável do motor, de acordo com as orientações e o cronograma CIBA que serão comunicados ao ecossistema.

## 3\. Antes de iniciar

Antes de criar um plano de teste, reúna as informações e os artefatos técnicos aplicáveis ao perfil que será testado.

### Para testes de OP

-   URL de descoberta OpenID (`discoveryUrl`);
    
-   identificadores dos clientes estáticos (`client_id` - obtidos após DCM);
    
-   certificados BRSeal - chaves JWKS de assinatura e de criptografia dos clientes
    
-   certificados BRCAC - utilizados em mTLS;
    
-   URL da API de consentimentos (`consentUrl`);
    
-   URL da API de recursos (`resourceUrl`);
    
-   CPF ou CNPJ válido para o cenário de teste;
    
-   `organizationId` da instituição.
    

### Para testes de RP

-   identificador do cliente (`client_id`);
    
-   endpoint de notificação do cliente CIBA (`backchannel_client_notification_endpoint`);
    
-   certificados BRCAC do client;
    
-   certificados BRSEAL - chaves JWKS aplicáveis;
    
-   informações do diretório necessárias ao cenário;
    
-   `organizationId` da instituição.
    

> **Segurança:** devem ser utilizadas chaves geradas pelo PKI do diretório de sandbox

## 4\. Acesso e criação de um teste

1.  Acesse o [ambiente de desenvolvimento do motor](https://review-app-dev-branch-26.certification.openid.net).
    
2.  Selecione **Create a new test**, no canto superior direito.
    
3.  Escolha **Open Finance Brazil**.
    
4.  Selecione o perfil que será testado:
    
    -   **OP (Authorization Server)**, para Transmissores/servidores; ou
        
    -   **Relying Party**, para Receptores/clientes.
        
5.  Selecione **CIBA**.
    
6.  Confira as opções escolhidas e selecione **Configure this plan**
    

![image-20260813-125820.png](images/image-20260813-125820.png)

7.  Selecione o ecossistema **BR - Open Finance Brazil** (modo Guided)
    

![image-20260813-130137.png](images/image-20260813-130137.png)

8.  Selecione o **Papel** a ser testado
    

![04.Selecao\_Papel-20260813-130235.png](images/04.Selecao_Papel-20260813-130235.png)

## 5\. Configuração do teste de OP

### 5.1 Seleção do plano

Ao criar o teste, selecione o plano **CIBA**

![image-20260813-131112.png](images/image-20260813-131112.png)

Revise o plano clique em **Configure this plan**. Por enquanto, somente o cenário com cliente estático está disponível para OP.  

![image-20260813-131559.png](images/image-20260813-131559.png)

### 5.2 Preenchimento da configuração

A configuração pode ser informada diretamente pela aba **Form** ou inserida como JSON na aba **JSON**. Caso a instituição já possua uma configuração utilizada nos testes do perfil FAPI1 Advanced do Open Finance Brasil, ela poderá ser utilizada como ponto de partida, com os ajustes específicos do CIBA.

No inicio de configuração do plano será exibido um resumo conforme abaixo:

![image-20260813-141001.png](images/image-20260813-141001.png)

#### Campos obrigatórios vs. opcionais

Campo

Obrigatório

Descrição

`alias`

✓

Alias do plano

`description`

✓

Identificação do plano no padrão `OFB-<organizationId>`

`publish`

✓

Indica se o plano deverá ser visivel a terceiros

`server.discoveryUrl`

✓

Endpoint de descoberta do servidor (.well-know)

`client1.client_id`

✓

Identificador do cliente estático 1

`client1.scope`

✓

Deve incluir `openid consents resources`

`client1.jwks`

✓

JWKS com chaves privadas BRSEAL e criptografia do client

`client1.organization_jwks`

✓

JWKS com chaves privadas BRSEAL e criptografia da organização

`client1.mtls_cert`  

✓

Chave pública do certificado de transporte BRCAC

`client1.mtls_key`

✓

Chave privada do certificado de transporte BRCAC

`client1.mtls_ca`

Cadeia de Certificados do BRCAC

`client2.client_id`

✓

Identificador do cliente estático 2

`client2.scope`

✓

Deve incluir `openid consents resources`

`client2.jwks`

✓

JWKS com chaves privadas BRSEAL e criptografia do client

`client1.organization_jwks`

✓

JWKS com chaves privadas BRSEAL e criptografia da organização

`client2.organization_jwks`

✓

JWKS com chaves privadas BRSEAL e criptografia da organização

`client2.acr_value`

✓

urn:brasil:openbanking:loa2 ou urn:brasil:openbanking:loa3

`client2.mtls_cert`

✓

Chave pública do certificado de transporte BRCAC

`client2.mtls_key`

✓

Chave privada do certificado de transporte BRCAC

`client2.mtls_ca`

Cadeia de Certificados do BRCAC

`resourceUrl`

✓

Endpoint da API de recursos

`consentUrl`

✓

Endpoint da API de consentimentos

`brazilCpf`

✓

Documento válido para teste do cliente PF ou operador PJ

`brazilCnpj`

✓

Preechido se o teste for realizado para cliente PJ

`directory.keystore_base`

✓

[https://keystore.sandbox.directory.openbankingbrasil.org.br](https://keystore.sandbox.directory.openbankingbrasil.org.br)

**Instruções detalhadas por campo:**

`alias` **(Obrigatório)**

-   Deve ser uma string **única** - não é possível ter dois planos com o mesmo alias executando simultaneamente
    
-   É utilizado para compor o path do endpoint de notificação
    
-   O DCR/DCM deve ser realizado prevendo este alias
    
-   A URL de notificação usada pelo teste segue o padrão: `https://review-app-dev-branch-26.certification.openid.net/test/a/CIBA-Conformance-Test/<alias>`
    
-   Exemplo: `test-ciba-op-001`
    

`description` **(Obrigatório)**

-   Deve obrigatoriamente seguir o padrão: `OFB-<organizationId>-<Descrição>`
    
-   Exemplo: `OFB-14c057d6-17bb-11ec-9621-0242ac130002 Testes CIBA`
    
-   Isso é necessário para habilitar o controle das organizações que estão executando testes
    
-   Caso o padrão não seja adotado, não será possível determinar se a organização está cumprindo com os marcos estabelecidos
    

`publish` **(Obrigatório)**

-   Indica se o plano deverá ser visível a terceiros
    

`server.discoveryUrl` **(Obrigatório)**

-   Informe a URL completa do endpoint de descoberta OpenID (URL .well-know) do OP que será testado
    
-   Padrão: `https://seu-op.exemplo.com/.well-known/openid-configuration`
    
-   Deve retornar um documento JSON com a configuração de descoberta contendo os atributos do CIBA
    
-   O motor utilizará este endpoint para auto-descobrir os demais endpoints do OP
    

`client1.client_id` **e** `client2.client_id` **(Obrigatório)**

-   Serão utilizados 2 clientes para o teste: 2 Software Statements com 2 registros DCR distintos
    
-   Eles podem ter sido gerados na mesma organização
    
-   Informe os identificadores dos clientes estáticos fornecidos após o processo de Onboarding (DCM)
    
-   Cada cliente deve ter um `client_id` único
    
-   Estes identificadores devem estar pré-registrados no OP
    

`client1.scope` **e** `client2.scope` **(Obrigatório)**

-   Configure com no mínimo os valores:
    

wide760true

-   Este scope é essencial para testes CIBA e inclui:
    
    -   `openid`: autorização de identidade
        
    -   `consents`: acesso à API de consentimentos
        
    -   `resources`: acesso à API de recursos
        
-   Podem ser adicionados escopos adicionais conforme necessário
    

`client1.jwks` **e** `client2.jwks` **(Obrigatório)**

-   Informe as chaves JWKS (JSON Web Key Set) com chaves privadas BRSEAL e criptografia do client
    
-   Deve conter as chaves de assinatura e criptografia específicas de cada cliente
    
-   **Origem:** devem ser geradas pelo PKI do diretório de sandbox do Open Finance Brasil
    
-   Inclua o `kid` (Key ID) em cada chave para identificação
    
-   Nunca utilize chaves de produção em ambiente de teste
    

`client1.organization_jwks` **e** `client2.organization_jwks` **(Obrigatório)**

-   Informe o JWKS com chaves privadas BRSEAL e criptografia **da organização**
    
-   Deve conter as chaves de assinatura e criptografia da instituição
    
-   **Origem:** devem ser geradas pelo PKI do diretório de sandbox do Open Finance Brasil
    
-   Diferente das chaves do cliente individual
    

`client1.mtls_cert` **e** `client2.mtls_cert` **(Obrigatório)**

-   Informe a chave **pública** do certificado de transporte BRCAC para cada cliente
    

`client1.mtls_key` **e** `client2.mtls_key` **(Obrigatório)**

-   Informe a chave **privada** do certificado de transporte BRCAC para cada cliente
    

`client1.mtls_ca` **e** `client2.mtls_ca` **(Opcional)**

-   Cadeia de Certificados do BRCAC
    
-   Fornece o caminho de confiança do certificado de transporte
    
-   Deixe em branco se não for necessário ou se o OP aceitar apenas o certificado raiz
    

`client2.acr_value` **(Obrigatório)**

-   Informe um dos valores de nível de autenticação (ACR):
    
    -   `urn:brasil:openbanking:loa2` (nível 2)
        
    -   `urn:brasil:openbanking:loa3` (nível 3)
        
-   Define o nível de autenticação exigido para o cliente 2
    
-   Deve estar alinhado com requisitos do OP
    

`resourceUrl` **(Obrigatório)**

-   Endpoint completo da API de recursos, incluindo o caminho específico
    
-   Exemplo: `https://seu-op.exemplo.com/open-banking/resources/v3/resources`
    
-   Deve ser um endpoint válido que retorne informações de recursos
    

`consentUrl` **(Obrigatório)**

-   Endpoint completo da API de consentimentos, incluindo o caminho específico
    
-   Exemplo: `https://seu-op.exemplo.com/open-banking/consents/v3/consents`
    
-   Deve ser um endpoint válido que suporte operações de consentimento CIBA
    

`brazilCpf` **(Obrigatório)**

-   Documento válido para teste do cliente Pessoa Física (PF) ou operador PJ
    
-   Formato: `00000000000` (11 dígitos)
    
-   O motor utilizará este documento em testes de consentimento e acesso a recursos
    

`brazilCnpj` **(Obrigatório)**

-   Preenchido se o teste for realizado para cliente Pessoa Jurídica (PJ)
    
-   Formato: `00000000000000` (14 dígitos)
    
-   Pode coexistir com `brazilCpf` para testes abrangentes
    

`directory.keystore_base` **(Obrigatório)**

-   Informe a URL base do diretório de chaves:
    
    -   Para sandbox: `https://keystore.sandbox.directory.openbankingbrasil.org.br`
        
-   O motor utilizará este endereço para validar certificados e chaves da organização
    

### 5.3 Exemplo com MockBank

Um exemplo completo de preenchimento do teste OP apontando para o MockBank está disponível em:

## 6\. Configuração do teste de RP

### 6.1 Seleção do plano

Ao criar o teste, selecione:

-   **FAPI-CIBA**.
    

### 6.2 Preenchimento da configuração

Caso a instituição já possua uma configuração utilizada nos testes do perfil FAPI1 Advanced RP do Open Finance Brasil, ela poderá ser utilizada como ponto de partida, com os ajustes específicos do CIBA.

No inicio de configuração do plano será exibido um resumo conforme abaixo:

![image-20260813-145414.png](images/image-20260813-145414.png)

#### Campos obrigatórios vs. opcionais

Campo

Obrigatório

Descrição

`alias`

✓

Alias do plano

`description`

✓

Identificação do plano no padrão `OFB-<organizationId>`

`publish`

✓

Indica se o plano deverá ser visivel a terceiros

`server.jwks`

✓

JWKS com chaves privadas BRSEAL e criptografia da organização

`client.client_id`

✓

Identificador do cliente estático 1

`client.backchannel_client_notification_endpoint`

✓

URL de callback do client

`client.jwks`

✓

JWKS com chaves publicas BRSEAL e criptografia do client

`client.mtls_cert`

✓

Chave pública do certificado de transporte BRCAC

`directory.keystore_base`

✓

[https://keystore.sandbox.directory.openbankingbrasil.org.br](https://keystore.sandbox.directory.openbankingbrasil.org.br)

#### Instruções detalhadas por campo:

`alias` **(Obrigatório)**

-   Deve ser uma string **única** - não é possível ter dois planos com o mesmo alias executando simultaneamente
    
-   Exemplo: `test-ciba-rp-001`
    

`description` **(Obrigatório)**

-   Deve obrigatoriamente seguir o padrão: `OFB-<organizationId>-CIBA-RP-<Descrição>`
    
-   Exemplo: `OFB-14c057d6-17bb-11ec-9621-0242ac130002 Testes CIBA RP`
    
-   Isso é necessário para habilitar o controle das organizações que estão executando testes
    
-   Se necessário, acrescente uma identificação do cenário para distinguir múltiplos testes
    
-   Caso o padrão não seja adotado, não será possível determinar se a organização está cumprindo com os marcos estabelecidos
    

`publish` **(Obrigatório)**

-   Indica se o plano deverá ser visível a terceiros
    

`server.jwks` **(Obrigatório)**

-   Informe o JWKS com chaves publicas BRSEAL e criptografia **da organização**
    
-   Deve conter as chaves de assinatura e criptografia da instituição RP
    
-   **Origem:** devem ser geradas pelo PKI do diretório de sandbox do Open Finance Brasil
    
-   Este JWKS é utilizado para validar tokens e certificados do OP
    
-   Inclua o `kid` (Key ID) em cada chave para identificação
    
-   Diferente das chaves do cliente individual
    

`client.client_id` **(Obrigatório)**

-   Informe o identificador único do cliente RP registrado no diretório OpenID
    
-   Este `client_id` deve estar previamente registrado/onboarded no OP que será testado
    
-   Exemplo: `um-identificador-unico-da-rp`
    

`client.backchannel_client_notification_endpoint` **(Obrigatório)**

-   **Este é o campo mais importante para testes de RP**
    
-   Informe a URL completa do endpoint que receberá as notificações CIBA do OP
    
-   Exemplo: `https://seu-rp.exemplo.com/ciba/notification`
    
-   O OP enviará notificações para este endpoint quando a autenticação estiver pronta
    

`client.jwks` **(Obrigatório)**

-   Informe as chaves JWKS (JSON Web Key Set) com chaves **públicas** BRSEAL e criptografia do client
    
-   Deve conter as chaves de assinatura e criptografia específicas do cliente RP
    
-   **Origem:** devem ser geradas pelo PKI do diretório de sandbox do Open Finance Brasil
    
-   **Assinatura:** chave pública usada pelo OP para validar JWTs assinados pelo cliente
    
-   **Criptografia:** chave pública usada pelo OP para criptografar dados destinados ao cliente
    
-   Inclua o `kid` (Key ID) em cada chave para identificação
    
-   Nunca utilize chaves de produção em ambiente de teste
    
-   O OP recuperará estas chaves via JWKS URI ou configuração direta
    

`client.mtls_cert` **(Obrigatório)**

-   Informe a chave **pública** do certificado de transporte BRCAC do cliente
    
-   Utilizado para autenticação mTLS com o OP
    
-   Pode incluir a cadeia de certificados conforme necessário
    

`directory.keystore_base` **(Obrigatório)**

-   Informe a URL base do diretório de chaves:
    
    -   Para sandbox: `https://keystore.sandbox.directory.openbankingbrasil.org.br`
        
-   O motor utilizará este endereço para validar certificados e chaves da organização
    
-   Deve ser consistente entre OP e RP para testes com sucesso
    

## 7\. Execução e acompanhamento dos testes

1.  Revise todos os campos da configuração.
    
2.  Salve ou inicie o plano conforme as opções apresentadas pelo motor.
    
3.  Execute os testes indicados no plano.
    
4.  Acompanhe o status de cada teste e consulte os logs para identificar as etapas executadas.
    
5.  Em caso de falha, analise a mensagem exibida e o log técnico antes de executar novamente.
    
6.  Após os ajustes necessários, repita o teste e registre o resultado.
    

## 8\. Registro de dúvidas e comportamentos identificados

Ao comunicar uma dúvida, falha ou comportamento inesperado pelos canais de suporte do Open Finance Brasil, informe, sempre que possível:

-   instituição e `organizationId`;
    
-   perfil testado: RP ou OP;
    
-   nome do plano e do teste;
    
-   data e horário aproximados da execução;
    
-   identificador ou URL pública do log, quando aplicável;
    
-   resultado esperado;
    
-   resultado observado;
    

## 9\. Próximas etapas

Os participantes deverão iniciar os testes no ambiente indicado e compartilhar eventuais dúvidas, dificuldades ou comportamentos inesperados pelos canais de suporte do Open Finance Brasil.

As orientações sobre a disponibilização da versão estável do motor, a transição ao ambiente definitivo, os prazos e o processo de certificação serão comunicadas oportunamente, em conjunto com o cronograma CIBA.
