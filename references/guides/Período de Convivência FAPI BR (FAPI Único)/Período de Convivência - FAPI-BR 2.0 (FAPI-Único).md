# Período de Convivência - FAPI-BR 2.0 (FAPI-Único)

13falsenonelistfalse

## 1\. Objetivo

Apoiar as instituições participantes do Open Finance com orientações para a implementação do perfil FAPI único de segurança, especialmente no período de convivência entre os perfis antigos e o novo que ocorrerá entre 25/03/2024 e 14/04/2024.

## 2\. Contexto

As especificações de segurança do Open Finance são baseadas no FAPI, da OpenID Foundation, e permitiam que as autenticações fossem realizadas através de oito métodos diferentes, com variantes de Private Key e mTLS, com ou sem PAR, com ou sem JARM. A fim de simplificar a comunicação entre as instituições e melhorar a interoperabilidade, a documentação foi atualizada para criação de um perfil FAPI único que deverá ser implementado por todas as instituições do ecossistema.

O cronograma de adequação das instituições prevê um período de três semanas de convivência entre os perfis, para que as iniciadoras de pagamento e receptoras de dados façam os devidos DCMs e ajustes bilaterais com as detentoras de conta e transmissoras de dados, antes da descontinuação dos perfis anteriores. A realização dos DCMs a tempo é necessária para a devida implementação das novas APIs de Consentimento e de Pagamentos.

**Resumo de compatibilidade a ser garantida no período de convivência**

-   **Processo DCR/DCM**
    
    -   Atualizações nos registros de _clients_ (software statments), independente da finalidade (troca de certificado, aumento de escopo de produtos, rollbacks pós tentativa de migração para o FAPI-Único)
        
-   **Processo FAPI**
    
    -   Geração de novo access-token, habilitanto a obtenção de novos consentimentos
        
    -   Renovação de um access-token (refresh-token) para o consumo de dados de consentimentos já existentes
        

## 3\. Cronograma

**Data**

**Iniciadora de pagamento e Receptora de dados**

**Detentora de conta e transmissora de dados**

Até 24/03/2024

Obter certificação RP da OIDF

Obter certificações OP DCR/DCR e OP FAPI da OIDF

Até 24/03/2024 (23:59)

Publicar o link da certificação de segurança do novo perfil

A partir do momento de recebimento da certificação:

-   Atualizar o well-known e suas implementações com o novo perfil de segurança
    
-   Publicar o link das certificações de segurança do novo perfil
    

Entre 25/03/2024 e 14/04/2024

Realizar DCR ou DCM com todas as instituições para atualizar para o novo perfil

Atentar-se aos SLAs diferenciados acerca do atendimento de tickets relacionados aos processos de DCR/DCM, conforme IN BCB 443

Após 15/04/2024

Parar de fazer chamadas, DCR e DCM com os perfis antigos

Remover o suporte aos perfis antigos

## 4\. Principais mudanças no perfil FAPI-Único (FAPI-BR 2.0)

1.  Adoção do perfil único _private\_key_ \+ PAR​
    
2.  Criptografar o _id\_token_ por padrão, sem a necessidade de validação de PII em seu conteúdo​
    
3.  Tornar o _proof key for code exchange_ (PKCE) obrigatório​
    
4.  Remover _claims_ CPF e CNPJ​
    
5.  Proibir a rotação de _registration\_access\_token_ no processo de DCR/DCM​
    
6.  Restringir os parâmetros do atributo _response\_type_​
    
7.  Restringir os parâmetros do atributo _response\_mode_​
    
8.  Restringir os parâmetros do atributo _subject\_type_​
    

### 4.1. Métodos de Autenticação

A principal mudança do FAPI-Único é a adoção de um único método de autenticação, o private-key-jwt. Durante o período de convivência é imprescindível que os participantes mantenham disponíveis todos os métodos de autenticação que ofereciam na primeira versão do FAPI-BR.

Na primeira versão do FAPI, os servidores de autenticação eram obrigados a oferecer ao menos uma das seguintes opções de métodos de autenticação private-key-jwt ou mtls que poderiam, ainda, ser combinadas com o uso de PAR.

#### well-know

No JSON retornado pela endpoint de well-know dos servidores de autenticação, os métodos de autenticação aceitos são definidos no parâmetro _token\_endpoint\_auth\_methods\_supported_, utilizado para comunicar a url do endpoint que o cliente deve utilizar para obter/renovar um _access-token_.

**Método de Autenticação**

**well-know**  
(_token\_endpoint\_auth\_methods\_supported_)

**FABI-BR 1.0**

**FAPI-Único**

private-key-jwt

private\_key\_jwt

Suporta

Obrigatório

mtls

tls\_client\_auth

Suporta

Não suporta

Além do parâmetro _token\_endpoint\_auth\_methods\_supported_, alguns participantes declaram os métodos de autenticação aceitos nos parâmetros _revocation\_endpoint\_auth\_methods\_supported_ e _introspection\_endpoint\_auth\_methods\_supported_ que comunicam as urls dos endpoints de revogação de um access-token e de introspecção de um token. Caso o faça o participante deve garantir que todos os parâmetros sejam atualizados conforme a política do FAPI-Único.

#### Cenários

##### **Cenário 1: A implementação do FAPI 1.0 da instituição suporta apenas um dos métodos de autenticação**

![image-20240301-023531.png](images/image-20240301-023531.png)

#####   
**Cenário 2: A implementação do FAPI 1.0 da instituição suporta ambos os métodos de autenticação**

![image-20240306-130205.png](images/image-20240306-130205.png)

### 4.2. Pushed Authorization Requests (PAR)

Além de estabelecer como único método de autenticação o private-key-jwt, o perfil de segurança FAPI-Único exige a adoção do PAR para que os parâmetros da requisição de autorização sejam enviados diretamente ao servidor de autorização, sem o intermédio do navegador.

O uso do PAR altera o fluxo de chamadas realizados durante o processo de autenticação FAPI, sendo necessário garantir que, durante o período de convivência, instituições transmissoras/detentoras que não exigiam a adoção obrigatória do PAR mantenham a compatibilidade aceitando requisições sem o uso de PAR para os _clients_ previamente registrados. Após o término do período de convivência o uso do PAR deverá se tornar obrigatória a todos os _clients_.

#### well-know

No JSON retornado pela endpoint de well-know dos servidores de autenticação, existem dois parâmetros relacionados ao uso do PAR, _pushed\_authorization\_request\_endpoint_ que indica a url do endpoint para envio dos parâmetros de autenticação e _require\_pushed\_authorization\_requests_ indicando se o uso PAR é opcional ou obrigatório. O não envio destes parâmetros significa que a instituição não suporta o uso de PAR.

**Parâmetro**

**well-know**

**FABI-BR 1.0**

**FAPI-Único**

Endpoint PAR

_pushed\_authorization\_request\_endpoint_

Opcional

Obrigatório

Obrigatoriedade do PAR

_require\_pushed\_authorization\_requests_

Opcional

Obrigatório com valor _**true**_

#### Cenários

##### **Cenário 1: A implementação do FAPI 1.0 da instituição não suportava PAR**

Neste cenário, no período de convivência, o transmissor/detentor precisa garantir que clientes existentes, registrados sem o uso do PAR, continuem funcionando da mesma maneira. Posteriormente, ao término deste período, nenhuma autenticação sem o uso de PAR deverá ser aceita.

![image-20240301-035903.png](images/image-20240301-035903.png)

##### **Cenário 2: A implementação do FAPI 1.0 da instituição suportava PAR de maneira opcional**

Neste cenário, no período de convivência, o transmissor/detentor precisa garantir que clientes existentes, registrados, continuem funcionando da mesma maneira podendo escolher se utilizam ou não o PAR. Posteriormente, ao término deste período, nenhuma autenticação sem o uso de PAR deverá ser aceita.

![image-20240301-035947.png](images/image-20240301-035947.png)

##### **Cenário 3: A implementação do FAPI 1.0 da instituição exigia o uso do PAR**

Neste cenário não existe distinção entre o FAPI-BR 1.0 e FAPI-Único, sendo exigido que todos os clientes sempre façam a autenticação utilizando o PAR.

![image-20240301-040052.png](images/image-20240301-040052.png)

### 4.3. Proof Key for Code Exchange (PKCE)

PKCE é um método de segurança utilizado para proteger contra ataques de interceptação de código. Ele funciona gerando uma chave dinâmica que é utilizada para verificar a identidade do aplicativo cliente durante o processo de autorização. Essa chave é temporária e é usada para criar um código de autorização único, o qual é trocado por um token de acesso. O PKCE é utilizado para prevenir ataques de interceptação de código em aplicativos de autenticação que utilizam o fluxo de autorização baseado em código, garantindo uma camada adicional de segurança ao processo de autenticação. No novo perfil FAPI-Único o uso de PKCE se torna obrigatório, dado que no FAPI, quando se utiliza PAR, o uso de PKCE se torna obrigatório.

#### Cenários

**Cenário 1: A implementação do FAPI 1.0 da instituição não suportava PAR ou em que o uso do PAR não era obrigatório**

Neste cenário, durante o período de convivência, o servidor de autenticação deve garantir que clientes registrados, sem a obrigatoriedade do uso de PAR, possam continuar realizando o fluxo FAPI sem o uso de PKCE. Já clientes que foram registrados com uso de PAR obrigatório devem ser cobrados do uso do PKCE.

**Cenário 2: A implementação do FAPI 1.0 da instituição que obrigava o uso PAR (consequentemente de PKCE)**

Neste cenário, todos os clientes previamente registrados exigem o uso do PAR e consequentemente todos já são obrigados a utilizar o PKCE, não havendo impacto durante o processo de migração do FABI-BR 1.0 para o FAPI-Único.

### 4.4. Criptografia do idToken

No contexto do FAPI (Financial-grade API), a encriptação do ID Token é uma prática importante para proteger informações sensíveis transmitidas durante o processo de autenticação e autorização. O ID Token é um token de autenticação que contém informações sobre o usuário autenticado, como seu identificador, tipo de autenticação e outros atributos de perfil. Ao encriptar o ID Token, as informações contidas nele são tornadas ilegíveis para qualquer parte que não possua a chave de desencriptação adequada.

No FAPI-BR 1.0 a encriptação do ID Token só era exigida caso informações PII, como CPF e CNPJ, estivessem presentes, sendo opcionais nos demais casos. Já no FAPI-Único a encriptação do ID Token sempre dever ser realizada.

Durante o processo de registro do _client,_ o servidor de autenticação informa o cliente os algoritmos e tipos de criptografia que poderão ser aplicados e caso não realizasse a encriptação, a informação não era fornecida. Desta forma, os transmissores/detentores devem adotar uma política de convivência para este aspecto.

#### well-know

No JSON retornado pela endpoint de well-know dos servidores de autenticação, existem dois parâmetros relacionados a criptografia do ID Token, _id\_token\_encryption\_alg\_values\_supported_ que lista os algorítimos válidos para a criptografia e id\_token\_encryption\_enc\_values\_supported que lista os métodos de criptografia suportados.

Como no FAPI 1.0 os authorizations servers já deveriam suportar a criptografia para alguns cenários, não deveria haver impactos para a URL de well-know, devendo ambos os atributos estar presentes. Entretanto, existe uma quebra de comportamento, e os clients devem se preparar para sempre receberem os dados criptografados.

### 4.5. Claims CPF e CNPJ

No FAPI-BR 1.0 era obrigatório que os servidores de autorização suportassem as claims CPF e CNPJ durante o pedido de autenticação. No FAPI-Único esta exigência deixa de existir, e de forma contrária, eles devem ignorar o pedido destas claims.

#### well-know

No JSON retornado pela endpoint de well-know dos servidores de autenticação, o parâmetro _claims\_supported_ indica quais claims podem ser solicitadas durante o processo de autenticação FAPI. Este parametro traz uma lista de todas as claims suportadas para diferentes propósitos.

![image-20240306-011634.png](images/image-20240306-011634.png)

### 4.6. Rotação de _registration\_access\_token_ no processo de DCR/DCM​

No novo perfil FAPI-Único foi proibida a rotação do registration\_access\_token o processo de DCR/DCM. Esta mudança não gera problemas de convivência.

### 4.7. Atributo _response\_type_

O response type no FAPI refere-se aos tipos de resposta permitidos durante o processo de autorização de um software cliente para acessar recursos protegidos por um servidor de autorização. Na especificação FAPI-BR 1.0, os tipos de resposta aceitos eram "code id\_token" ou "code" em conjunto com o response\_mode jwt (JARM). O primeiro combina o fluxo de autorização com a obtenção de um token de identificação (ID token), fornecendo informações sobre a identidade do usuário autenticado. O segundo envolve a obtenção dos tokens de acesso em uma resposta encapsulada em um JWT assinado. No FAPI-Único, apenas o tipo "code id\_token" é permitido. Isso significa que o fluxo de autorização deve obrigatoriamente fornecer tanto um código de autorização quanto um token de identificação.

A mudança nas opções de response type impacta os softwares clientes ao exigir ajustes nos fluxos de autorização e possíveis reavaliações nas estratégias de autenticação e segurança, garantindo a conformidade com as novas especificações e uma interação segura e eficaz com os servidores de autorização em transações financeiras. É importante destacar que essa mudança pode exigir a realização de um DCM.

#### **well-know**

**Cenário 1: A implementação do FAPI 1.0 da instituição suportava os response types “code idtoken” e “code”**

Neste cenário, durante o período de convivência, o servidor de autorização deve garantir a compatibilidade mantendo os dois formatos de _response\_type_ disponíveis. AO término deste período apenas o _response\_type_ “code id\_token” deve ser mantido.

![image-20240306-014708.png](images/image-20240306-014708.png)

**Cenário 2: A implementação do FAPI 1.0 da instituição suportava apenas o response type “code id\_token”**

Neste cenário, não existe problema de compatibilidade e o servidor de autorização pode manter o suporte apenas do response\_type “code id\_token” durante o período de convivência.

![image-20240306-014718.png](images/image-20240306-014718.png)

### 4.8. Atributo _response\_mode_

O atributo "response\_mode" é um parâmetro em solicitações de autorização OAuth 2.0 que especifica o formato e o método de entrega da resposta de autorização do servidor de autorização ao cliente após o consentimento do usuário. Os valores possíveis incluem "query" para retornar a resposta como parâmetros de consulta na URL de redirecionamento, "fragment" para retorná-la como um fragmento na URL e "form\_post" para enviá-la em um corpo de mensagem HTML POST, sendo escolhido de acordo com as necessidades de segurança e o contexto de uso do cliente.

O uso do "response\_mode" jwt em conjunto com o "response\_type" "code" permite que a resposta de autorização seja encapsulada em um token JWT (JSON Web Token), fornecendo segurança adicional para as transações OAuth 2.0. Esse método é especialmente útil quando combinado com a técnica JARM (JSON-based Algorithm for Resilient Metrics), onde as características da resposta TLS são utilizadas para calcular uma impressão digital única, fornecendo uma camada adicional de segurança contra ataques como falsificação de resposta de autorização (authorization response spoofing) e manipulação dos parâmetros de resposta.​

No FAPI-BR 1.0 era permitido o uso de qualquer um dos response\_mode definidos na RFC, ou exigido o uso do response\_mode jwt quando se utilizando o response\_type code. No perfil FAPI-Único apenas o response\_mode fragment é aceito, gerando a necessidade de alterações no processo de autenticação por parte dos softwares clientes. Esta mudança pode exigir a realização do DCM.

#### **well-know**

**Cenário 1: A implementação do FAPI 1.0 da instituição suportava apenas o response type “code” e consequentemente apenas o response mode “jwt”**

Neste cenário, é necessário que durante o período de convivência, o servidor de autorização mantenha a compatibilidade com o modo jwt para caso algum cliente ainda utilize o response type code e adicione suporte ao modo fragment para os softwares clientes que migrarem para o uso do response type “code id\_token”.

![image-20240306-023644.png](images/image-20240306-023644.png)

**Cenário 2: A implementação do FAPI 1.0 da instituição não definia os responses modes no well-know**

Neste cenário, a omissão no well-know do atributo “response\_modes\_supported” indica que o servidor de autorização aceita os modos “query” e “fragment”. Desta forma, é necessário que seja garantida a compatibilidade durante o período de convivência.

![image-20240306-024058.png](images/image-20240306-024058.png)

**Cenário 3: A implementação do FAPI 1.0 da instituição suportava múltiplos response modes**

Neste cenário, é necessário que durante o período de convivência, o servidor de autorização mantenha a compatibilidade com todos os modos previamente suportados, além de incluir caso ainda não o suportasse, o modo fragment.

![image-20240306-025818.png](images/image-20240306-025818.png)

### 4.9. Atributo _subject\_type_​

No contexto do FAPI (Financial-grade API), os "subject types" "public" e "pairwise" são utilizados para identificar o usuário sobre o qual uma ação está sendo realizada durante o processo de autorização. No FAPI, apenas esses dois tipos de "subject" são aceitos, com o objetivo de garantir um nível adequado de segurança e privacidade nas transações financeiras.

O "subject type" "public" permite que o "subject" seja um identificador público e único, como um nome de usuário ou endereço de e-mail, sendo mais simples e direto. Já o "pairwise" cria identificadores únicos para cada cliente, garantindo que o mesmo usuário receba um identificador diferente para cada cliente, protegendo sua privacidade. Essa restrição aos "subject types" "public" e "pairwise" no FAPI visa garantir uma abordagem consistente e segura para a identificação de usuários em transações financeiras, atendendo aos rigorosos requisitos de segurança e privacidade nesse contexto.

No FAPI-BR 1.0, ambos os tipos de "subject" eram suportados, porém, no FAPI-Único, apenas o tipo "public" é aceito. Essa diferença pode potencialmente causar problemas de compatibilidade entre as versões, o que deve ser cuidadosamente considerado durante o período de convivência entre elas. Essa mudança requer a execução de um DCM. Além disso, os receptores de dados devem se atentar que o subject utilizado previamente para identificar o usuário pode ser alterado.

#### **well-know**

Durante o período de convivência é necessário que o servidor de autorização garanta o funcionamento de ambos os modelos.

![image-20240306-031212.png](images/image-20240306-031212.png)

## 5\. FAQ

1.  **Durante o período de convivência devo aceitar requisições de registro (DCR) para novos clientes que forem solicitadas utilizando FAPI-BR 1.0, por exemplo , utilizando o método de autenticação mtls ou sem o uso de PAR?**
    

Sim. Para garantir o funcionamento durante o período de convivência, todos os transmissores/detentores deverão continuar suportando a realização de novos registros (DCR) utilizando o FABI-BR 1.0. Após o período de convivência apenas requisições que utilizem os padrões do FAPI-Único deverão ser aceitas.

2.  **Durante o período de convivência devo aceitar requisições de modificações de clientes existentes (DCM) que forem solicitadas utilizando FAPI-BR 1.0, por exemplo, utilizando o método de autenticação mtls ou sem o uso de PAR?**
    

Sim, manter a compatibilidade com solicitações que utilizam o FAPI-BR 1.0 é importante para garantir a manutenção de clientes existentes e para possibilitar o processo de rollback de uma migração para o FAPI-Único mal sucedida.

3.  **Após o período de convivência, é obrigatório a remoção do suporte ao método de autenticação mtls?**
    

Sim, após o período de convivência o Open Finance Brasil não suportará nenhum outro método de autenticação além do private-key-jwt, devendo ser recusada a criação de novos clientes ou alteração de clientes existentes utilizando parâmetros incompatíveis com o definido no FAPI-Único.

4.  **Sou obrigado a declarar os parâmetros** _**revocation\_endpoint\_auth\_methods\_supported**_ **e** _**introspection\_endpoint\_auth\_methods\_supported no JSON retornado no meu endpoint de well-know?**_
    

Não. A escolha de determinar um método de autenticação para estes endpoints não é definida no FAPI-Único, ficando a cargo do transmissor/detentor escolher utilizar os valores padrões (quando os parâmetros não são comunicados) ou adotar o formato private-key-jwt definido no FAPI-Único.

Entretanto, independentemente da escolha do transmissor/dententor, deve-se garantir que no período de convivência o formato previamente utilizado na sua implementação do FAPI-BR 1.0 seja suportado.
