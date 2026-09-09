# Orientações - [DC] Consentimento

## Consentimento

No compartilhamento de dados cadastrais e transacionais, o "consentimento" denota a autorização concedida por um cliente de uma instituição participante do Open Finance para que outra instituição possa acessar informações sobre os produtos (recursos) detidos pelo cliente. Essa autorização é dada de forma explícita e detalhada.  
O cliente, que é o principal interessado no compartilhamento de suas informações, detém o poder de determinar quais produtos a instituição terá acesso. Além disso, dependendo do tipo de produto, ele pode especificar a origem precisa dos dados. Por exemplo, no caso de produtos do tipo "conta", o cliente tem a capacidade de escolher quais contas específicas terão seus dados compartilhados. Para outras categorias de produtos, como operações de crédito, o cliente pode indicar as modalidades de compartilhamento. Isso inclui autorizar a consulta de dados relativos a produtos que estejam atualmente contratados, bem como produtos que possam ser adquiridos no futuro, durante o período de validade do consentimento.

-   **Criação de consentimento para menores de idade**​
    
    -   É de responsabilidade das instituições participantes (Transmissora e Receptora) conceder o grau de autonomia para os clientes menores de idade, conforme parametrização dos responsáveis nos canais de atendimento da instituição.
        

## Máquina de Estados

O consentimento é uma entidade que possui estados indicando a sua situação da permissão de compartilhamento de dados do cliente. Existem 3 estados possíveis para um consentimento:

-   **AWAITING\_AUTHORISATION:** estado inicial quando um consentimento é criado. Neste estado, o consentimento representa apenas uma intenção de compartilhamento, indicando quem é o cliente que irá realizar o compartilhamento, quais permissões estão sendo solicitadas e a sua data de validade. Neste momento ainda não estão definidos os recursos a serem compartilhados.
    
-   **AUTHORISED:** estado que indica que o consentimento foi aprovado pelo cliente e que é possível realizar o consumo de dados. Neste estado os recursos ao qual o consentimento dá acesso já foram selecionados, seja através dos seus identificadores ou através da sua modalidade. Apesar do consentimento estar aprovado, ainda poderão existir recursos cujo acesso dependa de uma aprovação de múltipla alçada.
    
-   **REJECTED:** estado que indica que o consentimento foi revogado. A revogação pode se dar por diferentes motivos, como expiração do tempo máximo para autorização e aprovação do consentimento, vencimento da data de validade do consentimento após a sua aprovação ou ainda uma revogação explicita solicitada pelo cliente. 
    

![image-20260116-122924.png](images/image-20260116-122924.png)

### Regras de transição de estados

-   **AWAITING\_AUTHORISATION** pode transicionar para:
    
    -   **AUTHORIZED:**
        
        -   Quando o consentimento for aprovado através da jornada de autorização, onde os recursos são selecionados;
            
    -   **REJECTED:**
        
        -   Quando o consentimento não for aprovado dentro de 60 minutos após a sua criação;
            
        -   Quando o cliente rejeitar o consentimento na jornada de autorização.
            
-   **AUTHORISED** pode transicionar para:
    
    -   **REJECTED:**
        
        -   Quando o consentimento atingir a sua data de validade;
            
        -   Quando o cliente solicitar a revogação no portal de gerenciamento de consentimentos na receptora de dados ou na transmissora de dados;
            
        -   Quando a receptora ou transmissora de dados suspeitarem de alguma fraude.
            
-   **REJECTED** é um estado final e não pode ser alterado.
    

## Controle de acesso a uma API – Escopos e Permissões

Open Finance Brasil adotou o FAPI como o padrão de segurança. Este padrão, fundamentado no modelo OAuth2, emprega o conceito de "escopos" para definir o nível de autorização associado a um token de acesso. De maneira simplificada, depois de concluídos os procedimentos de autenticação e autorização para um consentimento, é gerado um token de acesso. Este token é vinculado a uma lista de escopos que representam a permissão para acessar determinada API e seus endpoints.

No entanto, a utilização dos escopos por si só não proporciona granularidade adequada para um controle preciso das operações, grupo de dados, recursos e modalidade de recursos que foram autorizados a serem compartilhados. Desta forma, estas informações são vinculadas ao consentimento.

Com isso, para o acessar os dados de um recurso é necessário possuir um token associado ao escopo exigido para consumo de uma API/endpoint e um consentimento que de a permissão de acesso a operação e ao recurso desejado.

### Regras para a criação do consentimento

1.  A receptora de dados deve enviar as permissões desejadas em grupo mínimo de permissões definidos para cada tipo de produto;
    
2.  A receptora de dados pode solicitar mais de um grupo de permissões ao mesmo tempo, respeitando a intenção do cliente durante a criação do consentimento;
    
3.  Para produtos com seleção por agrupamento de recursos ou agrupamento de produtos, a transmissora deve manter as permissões do agrupamento solicitado,  
    mesmo quando não os comercialize;
    
4.  Para produtos que exigem a seleção individual de recurso na aprovação do consentimento, caso a transmissora ofereça o produto (contas e/ou cartões), a transmissora deve retornar as permissions no pedido de criação do consentimento independente se o cliente possui ou não este produto;
    
5.  Se após a remoção de um agrupamento de produtos não restarem permissões funcionais, a transmissora deve rejeitar o pedido de criação do consentimento dando um retorno HTTP Status Code 422, com a mensagem "SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES";
    
6.  Nas situações abaixo, a transmissora deve rejeitar o pedido de criação de consentimento, dando retorno HTTP Status Code 422 com as mensagens especificadas abaixo:
    

a. Caso, no pedido da criação do consentimento, a transmissora valide a ausência de parâmetros PJ e presença de permissions CUSTOMERS BUSINESS deve retornar HTTP Status Code 422 com a mensagem “INFORMACOES\_PJ\_NAO\_INFORMADAS”;  
b. Caso, no pedido da criação do consentimento, a transmissora valide a presença de parâmetros PJ e presença de permissions CUSTOMERS PERSONAL deve retornar HTTP Status Code 422 com a mensagem “PERMISSOES\_PJ\_INCORRETAS”;  
c. Caso recebam uma solicitação de consentimento com permissões de dados cadastrais PF e PJ em conjunto, retornar HTTP Status Code 422 com a mensagem “PERMISSAO\_PF\_PJ\_EM\_CONJUNTO”;  
d. Caso a Instituição Receptora envie permissões divergentes ao agrupamento especificado na tabela abaixo, retornar HTTP Status Code 422 com a mensagem “COMBINACAO\_PERMISSOES\_INCORRETA”.  
e. Caso a Instituição Receptora envie data de expiração maior que um ano ou uma data referente ao passado, deve-se retornar HTTP Status Code 422.

7.  Caso seja identificado um cliente PJ na jornada de criação de consentimento, deve-se exibir apenas marcas que suportem públicos PJ ou ambos (PF e PJ) para escolha. As marcas que contemplam público PJ podem ser selecionadas no diretório nos casos em que a flag de seleção de público está preenchida com a opção “Suporta Contas PJ”​;
    
8.  Caso seja identificado um cliente PF na jornada de criação de consentimento, deve-se exibir apenas marcas que suportem públicos PF ou ambos (PF e PJ) para escolha. As marcas que contemplam público PF podem ser selecionadas no diretório nos casos em que a flag de seleção de público está preenchida com a opção “Suporta Contas PF”.
    

A tabela abaixo indica, para cada produto, os agrupamentos de permissões válidos e como é realizado a seleção de recursos, por identificador ou por modalidade. Produtos cuja seleção de recurso seja por identificador devem ter o agrupamento de permissões removidos quando a instituição transmissora não oferecer o produto. Já produtos cuja seleção de recurso seja por agrupamento de recurso ou agrupamento de produtos deve ter as permissões mantidas mesmo quando a instituição transmissora não comercializar o produto solicitado.

**CATEGORIA DE DADOS**

**AGRUPAMENTO**

**PERMISSIONS**

**SELEÇÃO DE RECURSO**

**Cadastro**

Dados Cadastrais PF

CUSTOMERS\_PERSONAL\_IDENTIFICATIONS\_READ

Por recurso

RESOURCES\_READ

**Cadastro**

Informações complementares PF

CUSTOMERS\_PERSONAL\_ADITTIONALINFO\_READ

Por recurso

RESOURCES\_READ

**Cadastro**

Dados Cadastrais PJ

CUSTOMERS\_BUSINESS\_IDENTIFICATIONS\_READ

Por recurso

RESOURCES\_READ

**Cadastro**

Informações complementares PJ

CUSTOMERS\_BUSINESS\_ADITTIONALINFO\_READ

Por recurso

RESOURCES\_READ

**Contas**

Saldos

ACCOUNTS\_READ

Por recurso

ACCOUNTS\_BALANCES\_READ

RESOURCES\_READ

**Contas**

Limites

ACCOUNTS\_READ

Por recurso

ACCOUNTS\_OVERDRAFT\_LIMITS\_READ

RESOURCES\_READ

**Contas**

Extratos

ACCOUNTS\_READ

Por recurso

ACCOUNTS\_TRANSACTIONS\_READ

RESOURCES\_READ

**Cartão de Crédito**

Limites

CREDIT\_CARDS\_ACCOUNTS\_READ

Por recurso

CREDIT\_CARDS\_ACCOUNTS\_LIMITS\_READ

RESOURCES\_READ

**Cartão de Crédito**

Transações

CREDIT\_CARDS\_ACCOUNTS\_READ

Por recurso

CREDIT\_CARDS\_ACCOUNTS\_TRANSACTIONS\_READ

RESOURCES\_READ

**Cartão de Crédito**

Faturas

CREDIT\_CARDS\_ACCOUNTS\_READ

Por recurso

CREDIT\_CARDS\_ACCOUNTS\_BILLS\_READ

CREDIT\_CARDS\_ACCOUNTS\_BILLS\_TRANSACTIONS\_READ

RESOURCES\_READ

**Operações de Crédito**

Dados do Contrato

LOANS\_READ

Por agrupamento de produtos

LOANS\_WARRANTIES\_READ

LOANS\_SCHEDULED\_INSTALMENTS\_READ

LOANS\_PAYMENTS\_READ

FINANCINGS\_READ

FINANCINGS\_WARRANTIES\_READ

FINANCINGS\_SCHEDULED\_INSTALMENTS\_READ

FINANCINGS\_PAYMENTS\_READ

UNARRANGED\_ACCOUNTS\_OVERDRAFT\_READ

UNARRANGED\_ACCOUNTS\_OVERDRAFT\_WARRANTIES\_READ

UNARRANGED\_ACCOUNTS\_OVERDRAFT\_SCHEDULED\_INSTALMENTS\_RE

UNARRANGED\_ACCOUNTS\_OVERDRAFT\_PAYMENTS\_READ

INVOICE\_FINANCINGS\_READ

INVOICE\_FINANCINGS\_WARRANTIES\_READ

INVOICE\_FINANCINGS\_SCHEDULED\_INSTALMENTS\_READ

INVOICE\_FINANCINGS\_PAYMENTS\_READ

RESOURCES\_READ

**Investimento**

Dados da Operação

BANK\_FIXED\_INCOMES\_READ

Por agrupamento de produtos

CREDIT\_FIXED\_INCOMES\_READ

FUNDS\_READ

VARIABLE\_INCOMES\_READ

TREASURE\_TITLES\_READ

RESOURCES\_READ

**Câmbio**

Listar

EXCHANGES\_READ

Por agrupamento de recursos

RESOURCES\_READ

Detalhes da Operação

EXCHANGES\_READ

RESOURCES\_READ

Eventos

EXCHANGES\_READ

RESOURCES\_READ

### Cenários de caso de erro

Foram mapeados alguns erros esperados durante o fluxo do usuário no ecossistema. Existem orientações específicas já tratadas no Guia de Experiência do Usuário. Aqui, trataremos a visão mais técnica do que pode ser feito em caso de erro:

-   Durante o redirecionamento do Consentimento, não se encontrou o browser no dispositivo do usuário: Além da orientação ao usuário, deve-se perceber que o fluxo de Consentimento continua pendente. Como a intenção de Consentimento segue válida por 60 minutos, deve-se tentar utilizar o mesmo Consentimento para tentar novamente a autorização do usuário.
    
-   Durante o redirecionamento do Consentimento, houve um problema inesperado no servidor do Transmissor (HTTP Code 4xx ou 5xx): Além da orientação ao usuário, deve-se perceber que o fluxo de Consentimento continua pendente. Como a intenção de Consentimento segue válida por 60 minutos, deve-se tentar utilizar o mesmo Consentimento para tentar novamente a autorização do usuário.
    
-   Durante o redirecionamento do Consentimento, houve um problema inesperado no servidor do Transmissor (Timeout, queda de Internet, etc.): Além da orientação do usuário, deve-se perceber que o fluxo de Consentimento continua pendente. Como a intenção de Consentimento segue válida por 60 minutos, deve-se tentar utilizar o mesmo Consentimento para tentar novamente a autorização do usuário.
    
-   Durante o redirecionamento do Consentimento, houve um problema com o Login do usuário (erro de credenciais): Além da orientação ao usuário, deve-se perceber que o fluxo de Consentimento continua pendente. Como a intenção de Consentimento segue válida por 60 minutos, deve-se tentar utilizar o mesmo Consentimento para tentar novamente a autorização do usuário.
    
-   Após o Consentimento do lado do Receptor, o usuário não finaliza o fluxo de compartilhamento deixando o fluxo pendente. Como a intenção de Consentimento segue válida por 60 minutos, deve-se tentar utilizar o mesmo Consentimento para tentar novamente a autorização do usuário.
    
-   Após o Consentimento do lado do Receptor, o usuário rejeita o compartilhamento. O consentimento é alterado para o status REJECTED e não pode mais ser utilizado para compartilhamento de dados.
    
-   Após o Consentimento completo, o app do Receptor não consegue acessar os dados por indisponibilidade: Deve-se tentar novamente. Access Token ainda é válido, portanto deve-se tentar novamente sem maiores prejuízos técnicos.
    
-   Após o Consentimento completo, o app do Receptor não consegue acessar os dados por pendência de autorização de um terceiro (ex.: Dupla alçada): Deve-se consultar a API de Recursos (Resources) para verificar as pendências e saber como proceder.
    

### Orientações para uso do token de consentimentos:

-   O estado e a validação do consentimento devem ser considerados antes do acionamento do token. ​
    
-   Após a identificação de que um consentimento está vencido/inativo, é indicado que não haja recorrência de acionamentos do token, que está inválido, para realização de consulta de informações e acesso aos serviços a fim de evitar comportamentos de consumo inadequado das APIs.
    

## Renovação simplificada do consentimento

A renovação de consentimento possibilita que o cliente estenda a data de expiração de um consentimento já existente. Ao contrário da criação de um novo consentimento, no qual há o redirecionamento e confirmação pelo cliente na transmissora, a renovação é feita via backend, sem redirecionamento.  
Importante salientar que na renovação apenas a validade do consentimento (expirationDateTime ) e a finalidade podem ser alteradas.  
Por não haver redirecionamento, nem todo consentimento é passível de renovação. A renovação aplica-se:

-   A consentimentos de Cliente Pessoa Física
    
-   A consentimentos de Cliente Pessoa Jurídica no qual não haja necessidade de múltiplas alçadas de confirmação.
    

Após a renovação de consentimento (\`POST /consents/{consentId}/extends\`) a transmissora deve garantir que o refresh token opaco, ao qual o consentimento está associado, continue válido, obedecendo às definições do Perfil de Segurança do Open Finance Brasil.

### Regras para a renovação simplificada do consentimento

-   Somente consentimentos ativos, no status AUTHORISED, podem ser renovados;
    
-   A nova data de expiração do consentimento não pode estar no passado, deve minimamente ser maior que a data de expiração atual;
    
-   Para situações na qual o cliente escolha o prazo indeterminado, a receptora não deve enviar o campo expirationDateTime no pedido de renovação à transmissora, de forma que o consentimento fique, de fato, sem um prazo determinado;
    
-   A renovação de consentimento ativo do cliente somente poderá ser aceita pela transmissora para um usuário logado na receptora, identificado por seu documento (\`loggedUser\`; \`businessEntity\` quando aplicável) e permitido a partir de token de acesso (informado no cabeçalho \`Authorization\`) conseguido anteriormente durante a criação e confirmação do consentimento vigente. A transmissora deve validar documento fornecido e token de acesso para executar a renovação de consentimento. Isso implica que qualquer usuário (\`loggedUser\`) com permissão para o consentimento associado deve ser capaz de finalizar o fluxo de renovação sem redirecionamento. No caso de pessoa jurídica o \`businessEntity\` deve ser igual ao do consentimento original.
    

Abaixo uma ilustração do fluxo esperado para o processo de renovação simplificado.

![image-20231110-204950.png](images/image-20231110-204950.png)

### Casos de erro para a renovação simplificada do consentimento

-   A transmissora deve validar documento fornecido (\`loggedUser\`; \`businessEntity\` quando aplicável) e token de acesso para executar a renovação de consentimento. Caso a transmissora detecte que se trata de acesso inválido por questões de segurança, é esperado status de erro 401 ou 403. Tipicamente, erros de segurança tem precedência, pois são avaliados primeiro, ao invés de erros de negócio. Por exemplo, status de erro 401 ocorrerá, mesmo que exista algum outro erro funcional (status 422) na requisição;
    
-   Na tentativa de renovação de consentimentos no status REJECTED a transmissora deve retornar status de erro 422 (\`ESTADO\_CONSENTIMENTO\_INVALIDO\`);
    
-   Na tentativa de renovação de consentimentos que exijam aprovações por múltiplas alçadas a transmissora deve retornar status de erro 422 (\`DEPENDE\_MULTIPLA\_ALCADA\`) ;
    
-   A transmissora deve retornar status de erro 422 (\`DATA\_EXPIRACAO\_INVALIDA\`) na tentativa de renovação de consentimentos em que o novo expirationDateTime seja:
    
    -   Menor que a data de requisição (currentDateTime ) do pedido de renovação, ou menor ou igual que a data de expiração atual.
        

## Mudanças entre as versões 2.2.0 e 3.0.0

As regras de manutenção das permissões durante a criação do consentimento foram modificadas entre as versões 2.1.0 e 3.0.0. Na versão 2.1.0, os agrupamentos de permissões de produtos não oferecidos por uma instituição transmissora eram sempre removidos do consentimento. No entanto, na versão 3.0.0, os produtos cuja seleção de recurso seja por agrupamento de produtos ou agrupamento de recursos devem ter as permissões correspondentes sempre mantidas, mesmo quando a instituição transmissora não ofereça o respectivo produto.

Esta mudança tem como objetivo aumentar a abrangência dos consentimentos para diminuir a necessidade de emissão de novos consentimentos. Desta forma, para suportar esta mudança tanto transmissora e receptora de dados precisarão realizar ajustes no processo de criação de consentimento e no processo de geração de tokens de acesso.

### Mudanças para as transmissoras de dados somente para produtos cuja seleção é agrupada por produtos (Operações de Crédito e Investimentos) ou por recursos (Câmbio)

**Regra**

**Como é**

**Como fica**

URL de _well-know_

Deve incluir apenas os escopos dos produtos trabalha

Deve incluir todos os escopos válidos do Open Finance

Criação do Consentimento

Deve remover as permissões correspondentes aos produtos que não trabalha

Deve manter todas as permissões dos agrupamentos solicitados, mesmo dos produtos que não trabalha

Criação do _access-token_

Deve remover os escopos dos produtos que não trabalha

Deve manter os escopos solicitados, mesmo dos produtos que não trabalha

APIs e endpoints

Deve implementar apenas as APIs e _endpoints_ dos produtos que trabalha¹

Deve implementar apenas as APIs e _endpoints_ dos produtos que trabalha¹

Comunicação

Deixar claro que novos recursos serão compartilhados quando contratados

Deixar claro que novos recursos e produtos poderão serão compartilhados quando contratados

1 Válido para todos os produtos, e não somente Operações de Crédito, Investimentos e Câmbio.

### Mudanças para as receptoras de dados somente para produtos cuja seleção é agrupada por produtos (Operações de Crédito e Investimentos) ou por recursos (Câmbio)

**Regra**

**Como é**

**Como fica**

Comunicação

Deixar claro que novos recursos serão compartilhados quando contratados

Deixar claro que novos recursos e produtos poderão serão compartilhados quando contratados

Consumo de APIs e _Endpoints_

Pode se basear nas permissões do consentimento para saber quais _endpoints_ consumir

Deve se basear na API Recursos

### Impactos e regras de transição

-   Consentimentos anteriores a mudança não serão alterados, mantendo o permissionamento correspondente a devolução de _permissions_ na criação do mesmo;
    
-   Quando uma instituição acrescentar um novo produto ao seu portifólio ela deverá atualizar a lista de recursos de recursos para clientes que tenham consentimentos válidos, com permissões para o agrupamento correspondente, e que contratarem o novo produto. A atualização não é necessária no caso de produtos cuja seleção se dá por recurso individual;
    
-   Todas as políticas de abrangência e vigência são aplicáveis a novos recursos que venham a ser expostos na listagem – conforme item anterior. A transmissora fica sujeita as mesmas regras de tempestividade de atualização de dados vigentes;
    
-   Os receptores deverão consultar a API Recursos ou de listagem para obter os identificadores dos produtos que forem contratados pelos clientes;
    
-   Os novos produtos poderão estar sujeitos a avaliação de múltiplas alçadas. Caberá aos transmissores e/ou receptores notificar os clientes da nova pendência.
    

### Mudanças na renovação simplificada e período de convivência

#### Mudanças na renovação simplificada

Na versão 2.2.0 dos endpoints de renovação simplificada foi necessária a utilização de valor dummy na representação técnica de consentimentos com prazo de expiração indeterminado. Por isso o campo expirationDateTime era obrigatório no post do pedido de renovação pelo receptor. A entrada do novo perfil FAPI 1.0 possibilitou que o campo expirationDateTime, e consequentemente, o prazo de validade do token, pudessem não ser obrigatoriamente preenchidos com uma data. Dessa forma, o comportamento esperado nos casos de renovação com prazo indeterminado é o não envio do campo expirationDateTime.

#### Período de convivência entre v2.2.0 e v3.0.0 da API Consents

Para adequada convivência entre versões da API Consents de Dados do Cliente é preciso que o prazo de expiração indeterminado seja reconhecido de duas formas:

-   v2.2.0: preenchimento de dummy (\`2300-01-01T00:00:00Z´) no campo expirationDateTime
    
-   v3.0.0: campo expirationDateTime não é enviado na requisição
    

Dessa forma, as instituições precisam tratar ambas as representações na experiência do usuário e exibir prazo indeterminado, de acordo com Guia UX, quando aplicável.

## **Mapeamento de mensagens retornadas pela API Consentimento**

**Endpoint**

**Método**

**HTTP Status**

**Cenário**

**Código de Mensagem**

/consents

POST

201

Criação do consentimento efetuada com sucesso (payload de retorno conforme a especificação)

422

Se após a remoção de um agrupamento de produtos não restarem permissões funcionais

SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES

A transmissora valide a ausência de parâmetros PJ e presença de permissions CUSTOMERS BUSSINESS

INFORMACOES\_PJ\_NAO\_INFORMADAS

A transmissora valide a presença de parâmetros PJ e presença de permissions CUSTOMERS PERSONAL

PERMISSOES\_PJ\_INCORRETAS

Solicitação de consentimento com permissões de dados cadastrais PF e PJ em conjunto

PERMISSAO\_PF\_PJ\_EM\_CONJUNTO

Instituição Receptora envie permissões divergentes ao agrupamento de especificado na tabela

COMBINACAO\_PERMISSOES\_INCORRETA

Data de expiração maior que um ano, diferente de prazo indeterminado (data vazia) ou data referente ao passado.

DATA\_EXPIRACAO\_INVALIDA

Utilizado para cenários de erros ainda não mapeados em outros status.

ERRO\_NAO\_MAPEADO

DELETE

422

Consentimento já se encontra no status REJECTED

CONSENTIMENTO\_EM\_STATUS\_REJEITADO

/consents/{consentID}/extends

POST

201

Renovação do consentimento finalizada com sucesso (payload de retorno conforme a especificação)

422

Necessário a aprovação de múltipla alçada

DEPENDE\_MULTIPLA\_ALCADA

Estado inválido do consentimento

ESTADO\_CONSENTIMENTO\_INVALIDO

Nova data para expiração de consentimento é inválida

DATA\_EXPIRACAO\_INVALIDA

Utilizado para cenários de erros ainda não mapeados em outros status.

ERRO\_NAO\_MAPEADO

## **Consentimentos para empresas com sócio único pessoa natural**

É vedado a exigência de poderes ou criação de etapas adicionais para aprovação de consentimentos em empresas (clientes PJ) com apenas um sócio pessoa natural (exemplo: MEI, EI, SLU e afins). Isto é, o usuário administrador pessoa natural deve ser capaz de iniciar e finalizar as jornadas de compartilhamento de dados e serviços do OFB sem a necessidade de configuração de poderes adicionais. Para casos em que haja delegação de poderes para terceiros, as regras de configuração de alçadas já existentes devem ser seguidas.
