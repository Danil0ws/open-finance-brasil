# Orientações - [DC] Dados Cadastrais

none

## Comportamento da API de Dados Cadastrais com relação a Recursos

### Regras de negócio para implementação pela transmissora

-   RN001 - Dados Cadastrais não geram recursos listáveis na API de Recursos (Resources). Eventuais fluxos de múltiplas alçadas terão os seus status reportados diretamente ao consultar os dados da API de Dados Cadastrais (Customers).
    
-   RN002 - Ao consultar a API de Recursos (Resources) em que, no consentimento, se tenham somente permissões de compartilhamento de Dados Cadastrais, deve ser retornado o código 200 com lista vazia da API de Recursos (Resources)
    
-   RN003 - Caso a Transmissora ainda esteja preparando a listagem dos recursos autorizados da API de Recursos (Resources), deve ser retornado o código HTTP Status Code 202 - ACCEPTED com o body vazio e a Receptora deverá seguir as recomendações de polling.
    
-   RN004 – Caso a Transmissora não possua cadastro unificado, ela poderá entregar mais de um registro no _endpoint_ de Identificação PN e PJ. No caso de PJ, deve-se indicar, no atributo “companiesCnpj”, a referência do CNPJ das empresas que fazem uso do respectivo cadastro.
    

Considerando o cenário abaixo: Marca 1, com as empresas CNPJ 1, CNPJ 2 e CNPJ 3.

Cadastro Não Unificado para PN.  

-   RN005 - Caso a Transmissora possua cadastro unificado das empresas de sua respectiva marca, ela poderá entregar apenas um registro na lista do endpoint de Identificação PN e PJ, devendo esta indicar, no atributo “companiesCnpj”, a referência do CNPJ das empresas que fazem uso do respectivo cadastro.
    

Considerando o cenário abaixo: Marca 1, com as empresas CNPJ 1, CNPJ 2 e CNPJ 3.

Cenário: Cadastro Unificado para PN.

-   RN006 – Se, a critério do transmissor, for aplicado fluxo de múltipla alçada para acesso aos Dados Cadastrais, deverá ser aplicado os status apresentados a seguir.
    

### Códigos de uso para o erro 403 na API de Dados Cadastrais (Customers)

A Transmissora deve preencher do retorno do código HTTP Status Code 403 - Forbidden, conforme segue:

-   PENDING\_AUTHORISATION: code=’STATUS\_RESOURCE\_PENDING\_AUTHORISATION’, title=’Aguardando autorização de múltiplas alçadas’, detail=(uso a critério do Transmissor)
    
-   UNAVAILABLE: code= ‘STATUS\_RESOURCE\_UNAVAILABLE’,title=’Recurso indisponível’, detail=(uso a critério do transmissor)
    

-   TEMPORARILY\_UNAVAILABLE: code= ’STATUS\_RESOURCE\_TEMPORARILY\_UNAVAILABLE’, title=’Recurso temporariamente indisponível’, detail=(uso a critério do transmissor)
    

## Orientações sobre dados do empregador (endpoint /personal/financial-relations)

Na versão 2.1.0 da API houve a adição de dois objetos ao endpoint ‘/personal/financial-relations’, para possibilitar o compartilhamento de informações de dados do empregador. Dessa forma, os campos portabilitiesReceived e paychecksBankLink estão relacionados com Portabilidade Salarial. Nesse sentido, as informações compartilhadas nesses campos podem ser úteis para portabilidade salarial da conta salário do banco-folha para outras instituições:

-   O objeto paychecksBankLink será utilizado para exposição de informações de conta salário ativas mantidas pelo cliente com a instituição transmissora de dados. Sua implementação é obrigatória por instituições transmissoras que atuam como instituição financeira contratada para a prestação de serviços de pagamento de salário (banco folha). O conteúdo deve ser enviado sempre que existente para o cliente que compartilhou seus dados cadastrais.
    
-   O objeto portabilitiesReceived deverá conter informações de empregador recebidas pela transmissora na ocorrência de uma portabilidade de salário. Devem ser compartilhadas as informações de portabilidade aprovadas, mesmo que de forma compulsória, considerando prazo histórico de 5 anos. Caso o pedido seja posteriormente regularizado (negado) pela instituição detentora da conta salário, tal pedido deve deixar de ser compartilhado. A implementação do objeto portabilitiesReceived é obrigatória para instituições transmissoras que também são detentoras de conta, e seu conteúdo deve ser compartilhado quando já houver portabilidade de salário realizada pelo cliente para a instituição transmissora de seus dados no OPF. A transmissora terá tais informações apenas quando o pedido da portabilidade tiver sido solicitado em seu canais.
    

## Orientações para instituições receptoras de dados

No objeto paychecksBankLink serão compartilhadas informações de conta salário que se encontram abertas, entretanto, pelo fato de haver uma conta salário aberta, não é possível afirmar que há um vínculo empregatício ativo para o cliente. Recomenda-se o cruzamento das informações obtidas desse objeto com as transações expostas na API Contas, para melhor compreensão dos dados.

No objeto portabilitiesReceived serão compartilhadas informações do empregador de portabilidade(s) recebida(s) pela transmissora, porém apenas por tais informações não é possível afirmar que tal portabilidade se encontre ativa ou que ainda exista o vínculo do cliente com o empregador ou com a instituição banco folha. Recomenda-se a análise das transações compartilhadas na API Contas para melhor compreensão dos dados.

**Opções Iniciais**

**Instituição A**

**Instituição B**

**Instituição C**

**Contexto geral**

Banco Folha - Detém a conta salário e outra conta (conta de depósito à vista, contas de poupança ou conta pré-paga)

É detentora de conta de  
depósito à vista, contas de  
poupança ou conta pré-paga

Banco Folha - Detém a conta salário e outra conta (conta de depósito à vista, contas de poupança ou conta pré-paga)

**Cenário 1:**  
Cliente realiza portabilidade da Instituição A para Instituição B, sendo que o pedido foi feito através de um canal da Instituição B

Deve enviar dados do empregador

-   Objeto **paychecksBankLink** (Dados Cadastrais)
    

Obs: Não compartilha transação Folha de Pagamento na API Contas, pois não houve "portabilidade interna”

Deve enviar dados do empregador

-   Objeto **portabilitiesReceived** (Dados Cadastrais)
    

\-

**Cenário 2:**  
Cliente realiza portabilidade da Instituição A para Instituição B, sendo que o pedido foi feito através de um canal da Instituição A

Deve enviar dados do empregador

-   Objeto **paychecksBankLink** (Dados Cadastrais)
    

Obs: Não compartilha transação Folha de Pagamento na API Contas, pois não houve "portabilidade interna”

Não deve enviar os dados do empregador

\-

**Cenário 3:**  
Cliente possui conta salário e portabilidade interna na Instituição A

Deve enviar dados do empregador

-   API de Contas (CNPJ do empregador na transação Folha de Pagamento)
    
-   Objeto **paychecksBankLink** (Dados Cadastrais)
    

\-

\-

**Cenário 4:**  
Cliente possui conta salário na Instituição A, conta salário na Instituição C e realizou portabilidade salarial apenas da Instituição C para Instituição A, sendo que o pedido foi feito através de um canal da Instituição A

Deve enviar dados do empregador

-   Objeto **paychecksBankLink** (Dados Cadastrais)
    

-   Objeto **portabilitiesReceived** (Dados Cadastrais)
    

Obs: Não compartilha transação Folha de Pagamento na API Contas, pois não houve "portabilidade interna”

\-

Deve enviar dados do empregador

-   Objeto **paychecksBankLink** (Dados Cadastrais)
    

**Cenário 5:**  
Cliente possui conta de depósito à vista e conta salário na Instituição A sem portabilidade interna ou externa

Deve enviar dados do empregador

-   Objeto **paychecksBankLink** (Dados Cadastrais)
    

\-

\-

**Cenário 6:**  
Cliente possui apenas conta salário na Instituição A

Não há compartilhamento de dados do empregador

\-

\-
