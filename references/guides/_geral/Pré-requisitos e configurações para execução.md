# Pré-requisitos e configurações para execução

Esta seção apresenta os pré-requisitos, configurações e orientações necessárias para acesso e utilização da FVP Manual, incluindo a criação de planos de teste e as particularidades das execuções para Pessoa Física (PF) e Pessoa Jurídica (PJ).

## **A. Criando uma conta no Diretório de Produção**

Para acessar a FVP Manual, é necessário possuir uma conta no Ambiente de Produção do [Diretório dos Participantes](https://auth.directory.openbankingbrasil.org.br/interaction/FXZw8_7JyIZUL7ZYCTO6Vbo0xe6G1rv8X5MRg2O7doQ).

As instruções para criação da conta estão disponíveis no Guia Operacional do Diretório de Participantes.

Durante esse processo será necessário:

-   Assinar os Termos e Condições de uso;
    
-   Configurar um dispositivo TOTP para autenticação.
    

Caso ocorra algum problema que não esteja contemplado na documentação do Diretório, recomenda-se abrir um chamado no Service Desk.

## **B. Escopo de acesso ao Diretório**

Para acessar a FVP, o usuário deverá possuir o papel "PFVPC" no Ambiente de Produção do Diretório, vinculado à organização que será testada.

Caso o usuário não possua essa permissão, ao realizar o login será apresentada a mensagem:

"403 – FORBIDDEN"

Além da permissão “PFVPC”, o CPF utilizado deverá possuir acesso aos recursos que serão utilizados durante a execução dos testes, uma vez que será responsável pela autorização dos consentimentos necessários durante o fluxo.

## **C. Acessando a plataforma**

Após receber a permissão "PFVPC", o acesso à FVP deverá ser realizado por meio do login no Diretório dos Participantes.

Após a autenticação, será apresentada a tela de aceite dos Termos e Condições da FVP, que deverá ser confirmada para prosseguir com a utilização da ferramenta.

## **D. Criando um plano de testes**

Após aceitar os Termos e Condições, o usuário será direcionado para a tela de criação dos planos de teste.

![att\_0\_for\_2065039588.png](images/att_0_for_2065039588.png)![att\_1\_for\_2065039588.png](images/att_1_for_2065039588.png)wide760

Os campos obrigatórios variam conforme o tipo de execução Pessoa Física ou Pessoa Jurídica. (Para mais detalhes de preenchimento acesse Planos e suas configurações)

**Testes de Pessoa Física (PF)**

Campo

Descrição

Authorisation Server ID

Servidor que será testado. Deve estar cadastrado para o orgId informado

BrazilCpf

CPF do usuário autenticado, com permissão PFVPC para a organização

**Testes de Pessoa Jurídica (PJ)**

Campo

Descrição

Authorisation Server ID

Servidor que será testado. Deve estar cadastrado para o orgId informado

BrazilCpf

CPF do usuário autenticado, com permissão PFVPC para a organização

BrazilCnpj

CNPJ ao qual o CPF informado possui acesso na instituição participante

Dependendo do plano de teste selecionado, poderão ser solicitadas informações adicionais, como debtorAccount ou creditorAccount.

Caso o CPF informado ou o Authorisation Server ID não estejam vinculados à organização configurada no Diretório, a criação do plano não será permitida.

## **Boas práticas**

Antes de iniciar uma execução, recomenda-se observar os seguintes pontos:

-   Certifique-se de que a conta utilizada possui saldo suficiente para cenários de pagamento (Pix e Pagamentos Automáticos), evitando falhas decorrentes de insuficiência de saldo.
    
-   Utilize a mesma conta (PF ou PJ) durante toda a execução do teste. Alterações de titularidade podem ocasionar rejeições.
    
-   Antes de iniciar um novo teste, verifique se a execução anterior foi finalizada. Caso o status esteja como Running, aguarde sua conclusão ou utilize o botão Stop.
    
-   Confirme que a instituição está autenticada com a conta correspondente ao segmento que será testado (PF ou PJ).
    
-   Sempre que possível, realize logout da aplicação bancária antes do início do teste e efetue o login apenas durante o redirecionamento.
    
-   Nas execuções via QR Code, mantenha o navegador mobile autenticado na FVP para garantir o retorno correto após a autorização do consentimento.
    

### **Entendendo o Redirecionamento**

Durante a execução do teste, a autorização do consentimento ocorre por meio do redirecionamento para a aplicação da instituição.

A FVP disponibiliza duas formas de redirecionamento:

-   QR Code (aplicação mobile);
    
-   Botão de redirecionamento (aplicação web).
    

**Redirecionamento mobile (QR Code)**

1.  1\. Inicie a execução normalmente pelo navegador desktop;
    
2.  2\. Leia o QR Code utilizando a câmera do dispositivo móvel;
    
3.  3\. Abra o link apresentado;
    
4.  4\. Autorize o consentimento ou pagamento no aplicativo da instituição;
    
5.  5\. Após a conclusão, o fluxo retornará automaticamente para a FVP.
    

Importante: para esse fluxo funcionar corretamente, o usuário deverá estar autenticado na FVP também no navegador do dispositivo móvel utilizado para leitura do QR Code.

![att\_2\_for\_2065039588.png](images/att_2_for_2065039588.png)

**Redirecionamento web**

1.  1\. Inicie a execução pelo navegador desktop;
    
2.  2\. Clique em Proceed with test;
    
3.  3\. Realize a autenticação na aplicação web da instituição;
    
4.  4\. Conclua a autorização do consentimento.
    

Caso a instituição não possua aplicação web, deverá disponibilizar um QR Code para continuidade do fluxo no aplicativo mobile.

Após a conclusão da autorização, o usuário será redirecionado novamente para a FVP.

![att\_3\_for\_2065039588.png](images/att_3_for_2065039588.png)

## Suporte e Dúvidas Adicionais

Caso a instituição tenha dúvidas ou apontamentos de irregularidades, aconselhamos que realizem a abertura de um ticket de Solicitação de Informações via Service Desk: Solicitação de Serviço → Solicitação de Informações → Conformidade → Ferramenta de Validação em Produção (FVP).
