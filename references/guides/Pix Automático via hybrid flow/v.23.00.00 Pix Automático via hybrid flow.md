# v.23.00.00 Pix Automático via hybrid flow

# Visão geral

A jornada de **Pix Automático** ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração de uma autorização de pagamentos automáticos com Pix via Open Finance.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida, com clareza sobre as próximas etapas.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, visualiza os dados da solicitação configurada na ITP e confirma.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Por fim, a ITP informa o status da solicitação de pagamento, concluindo a jornada.
    

![image-20260118-141144.png](images/image-20260118-141144.png)

* * *

# Telas de exemplo 

wide760

**Nota**

Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%100%600600

## Fluxo de telas

![image-20260518-175345.png](images/image-20260518-175345.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamentos recorrentes com Pix Automático via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação
    

## Cenário de referência

-   Autorização de pagamentos recorrentes com Pix Automático.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

Variações da jornadatrue

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento com Pix Automático via Open Finance.
    
-   Escolhe a Instituição Detentora de Conta (ID) que será usada para realizar o pagamento.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada. 
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

![image-20260623-194138.png](images/image-20260623-194138.png)

REQ.PG-00100 a 00200true

REQ.PG-00300 a 00700true

![image-20260623-201100.png](images/image-20260623-201100.png)

REQ.PG-00701 a 00707

**Cenário: Onboarding de Pix Automático**

-   `REQ.PG-00701` A partir do início da oferta do serviço de Pix Automático, no primeiro acesso do usuário, informar sobre a disponibilidade do serviço (onboarding).
    
-   `REQ.PG-00702` No onboarding, informar o que é o Pix Automático e suas vantagens.
    
-   `REQ.PG-00703` No onboarding, informar sobre a autorização, agendamento, possibilidade de cancelamento dos pagamentos agendados e da autorização.
    
-   `REQ.PG-00704` No onboarding, informar sobre a possibilidade de configuração do valor máximo por transação, em caso de cobranças com valores variáveis.
    
-   `REQ.PG-00705` No onboarding, informar sobre a possibilidade de configuração do recebimento de notificações de agendamento, caso a ITP as envie.
    
-   `REQ.PG-00706` No onboarding, informar sobre as regras de retentativas de liquidação em caso de saldo insuficiente, a critério do recebedor.
    
-   `REQ.PG-00707` No onboarding, informar que o uso de limite de crédito pré-aprovado é habilitado automaticamente e pode ser desabilitado na instituição de débito do usuário.
    

**Nota**  
Se a ITP também atuar como Instituição Detentora de Conta (ID) e já oferecer o Pix Automático nesse papel, não é necessário reapresentar onboarding do serviço quando disponibilizá-lo como ITP.

![image-20260623-201217.png](images/image-20260623-201217.png)

REQ.PG-00800true

REQ.PG-01000true  
Ex.: Transações de valor fixo.

REQ.PG-01001 a 01004

-   `REQ.PG-01001` Para solicitações de valores variáveis, permitir que o usuário defina o valor máximo de cada pagamento recorrente, podendo inclusive ser um valor indeterminado.
    
-   `REQ.PG-01002` Se o recebedor definir um valor mínimo por transação, exibir mensagem informando o usuário que o valor máximo não pode ser inferior ao valor mínimo estabelecido pelo recebedor.
    
    Ex.: O valor máximo não pode ser inferior a R$ 300,00.
    
-   `REQ.PG-01003` Exibir aviso claro ao usuário de que pagamentos com valor superior ao valor máximo configurado não serão efetivados e que ele poderá ser notificado para ajustar o limite ou buscar outras formas de pagamento.
    
    Ex.: Caso o valor da mensalidade ultrapasse este valor, o agendamento não será realizado e você será avisado para ajustar o limite ou buscar outra forma de pagamento.
    
-   `REQ.PG-01004` Se houver pagamento inicial avulso, por se tratar de um pagamento imediato com Pix, informar que o valor deste pagamento não está sujeito ao valor máximo definido e sim ao limite transacional do arranjo Pix.
    
    Ex.: O valor pagamento inicial não está sujeito ao valor máximo definido.
    

![image-20260623-195402.png](images/image-20260623-195402.png)

REQ.PG-01005

-   `REQ.PG-01005` Permitir preenchimento opcional da descrição da autorização.    
    Ex.: Introdução à Música Clássica, Conta de Energia etc.
    

REQ.PG-01006

-   `REQ.PG-01006` Exibir nome e CPF (mascarado)/CNPJ do usuário pagador.
    

REQ.PG-01007

-   `REQ.PG-01007` Exibir CNPJ e Nome Fantasia da empresa recebedora. Se a empresa não possui Nome Fantasia, exibir o Nome Empresarial/Razão Social.
    

REQ.PG-01008 a 01010

-   `REQ.PG-01008` Exibir o identificador do objeto da cobrança.  
    Ex.: Número do contrato, código do usuário etc.
    
-   `REQ.PG-01009` Exibir a data prevista do primeiro pagamento da recorrência.
    
-   `REQ.PG-01010` Exibir a periodicidade dos pagamentos futuros conforme estabelecido pelo recebedor (Semanal, Mensal, Trimestral, Semestral ou Anual).
    

REQ.PG-01011

-   `REQ.PG-01011` Exibir a data de início da autorização e a data de validade da autorização, inclusive quando for indeterminada.
    

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01900true

REQ.PG-02000true

![image-20260625-125048.png](images/image-20260625-125048.png)

REQ.PG-02101 a 02102

-   `REQ.PG-02101` Exibir as regras de retentativas de efetivação de pagamento após a data de vencimento conforme definido pelo recebedor e de acordo com as regras do arranjo de pagamento.
    
-   `REQ.PG-02102` Informar sobre a possibilidade de incidência de juros e multas em caso de falha na efetivação do pagamento na data de vencimento, a critério do recebedor, no próximo pagamento da recorrência.
    

REQ.PG-02200 a 02400true

REQ.PG-02500true

![image-20260625-125205.png](images/image-20260625-125205.png)

REQ.PG-00999

**Cenário: Pagamento inicial avulso**

-   `REQ.PG-00999` Para pagamento inicial avulso, exibir todas as informações mínimas aplicáveis à solicitação de um pagamento imediato com Pix, conforme as regras do arranjo.
    

REQ.PG-01000true

REQ.PG-01200true

wide760

**Atenção!**

Conforme definido pelo arranjo de pagamento, o pagamento inicial avulso deve ser identificado como **Pix**.

REQ.PG-01300true

wide760

**Nota**

Para permitir o agendamento do pagamento, consulte a página **Pix Agendado**.

REQ.PG-01400true

REQ.PG-01401 a 01402

-   `REQ.PG-01401` Não exibir o número da agência, número da conta e a instituição bancária do recebedor.
    
-   `REQ.PG-01402` Se o pagamento inicial avulso for imediato, informar sobre a necessidade de saldo e limite Pix para efetivação do pagamento.
    

![image-20260623-202354.png](images/image-20260623-202354.png)

REC.PG-00100true

![image-20260623-203813.png](images/image-20260623-203813.png)

**Cenário: Onboarding**

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260623-204411.png](images/image-20260623-204411.png)

REC.PG-00700true

![image-20260518-193320.png](images/image-20260518-193320.png)

REC.PG-00800 a 00900true

REC.PG-01000true

![image-20260623-205008.png](images/image-20260623-205008.png)

REC.PG-01200true

![image-20260623-205143.png](images/image-20260623-205143.png)

REC.PG-01300true

![image-20260623-205255.png](images/image-20260623-205255.png)

* * *

# Etapa 2: Direcionamento

760Resumo

Nesta etapa, o usuário:

-   É direcionado da Iniciadora (ITP) para a sua Detentora de Conta (ID).
    

A ITP deve:

-   Orientar o usuário sobre o direcionamento.
    
-   Assegurar que a navegação ocorra de forma transparente, conforme o dispositivo utilizado.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-02600 a 03100true

REQ.PG-03200 a 03400true

REQ.PG-03401

-   `REQ.PG-03401` Informar que o usuário possui até 60 minutos para confirmar a autorização de pagamento na ID.       
    Ex.: Você tem até 60 minutos para confirmar a operação.
    

REQ.PG-03600true

![image-20260624-140649.png](images/image-20260624-140649.png)

wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01400true

* * *

# Etapa 3: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Pode escolher a conta que deseja usar para fazer o pagamento se ele possuir mais de uma conta na ID.
    
-   Revisa as informações do agendamento enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma o agendamento.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo do agendamento.
    
-   Permitir a edição da conta de débito, em caso de múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Quando aplicável, exibir mensagens de erro claras ao usuário.
    
-   Comunicar o resultado da autorização à ITP.
    
-   Enviar notificações ao usuário e aos demais aprovadores nos cenários de múltiplos aprovadores.
    

![image-20260518-181854.png](images/image-20260518-181854.png)

REQ.PG-03700 a 03900true

![image-20260624-140841.png](images/image-20260624-140841.png)

REQ.PG-04000 a 04500true

![image-20260624-141631.png](images/image-20260624-141631.png)

Fluxograma ITP > IDtrue

REQ.PG-04600true

REQ.PG-04700true

Ex.: Transações de valor fixo.

REQ.PG-04701

-   `REQ.PG-04701` Para transações de valor variável, exibir o valor máximo a ser transacionado, inclusive se o valor for indeterminado, conforme informado pela ITP.
    

REQ.PG-04702

-   `REQ.PG-04702` Exibir nome e CPF (mascarado)/CNPJ do usuário pagador.
    

REQ.PG-04800true

REQ.PG-04801

-   `REQ.PG-04801` Exibir a descrição da autorização quando informada pela ITP.
    

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-04802

-   `REQ.PG-04802` Exibir CNPJ e Nome Fantasia da empresa recebedora. Se a empresa não possuir Nome Fantasia, exibir o Nome Empresarial/Razão Social.
    

REQ.PG-04803

-   `REQ.PG-04803` Exibir o identificador do objeto da cobrança conforme informado pela ITP.  
    Ex.: Número do contrato, código do usuário etc.
    

REQ.PG-04804

-   `REQ.PG-04804` Exibir a periodicidade dos pagamentos futuros conforme informado pela ITP (Semanal, Mensal, Trimestral, Semestral ou Anual).
    

REQ.PG-04805

-   `REQ.PG-04805` Exibir a data prevista do primeiro pagamento da recorrência conforme informado pela ITP.
    

REQ.PG-04806

-   `REQ.PG-04806` Exibir a data de início e a data de validade da autorização, inclusive se a data de validade for indeterminada, conforme informado pela ITP.
    

REQ.PG-04807 a 04808

-   `REQ.PG-04807` Exibir informação sobre a existência de retentativas de efetivação de pagamento conforme informado pela ITP.
    
-   `REQ.PG-04808` Exibir informação sobre a possibilidade de incidência de juros e multas em caso de falha na efetivação do pagamento na data de vencimento, a critério do recebedor, no próximo pagamento da recorrência conforme informado pela ITP.
    

REQ.PG-04699

**Cenário: Pagamento inicial avulso**

-   `REQ.PG-04699` Para pagamento inicial avulso, exibir todas as informações mínimas aplicáveis à confirmação de um pagamento imediato com Pix, conforme as regras do arranjo.
    

REQ.PG-04700true

REQ.PG-04900true

Ex.: Taxa de adesão, Matrícula, Taxa de instalação etc.

REQ.PG-05100true

REQ.PG-05200true

wide760

**Atenção!**

Conforme definido pelo arranjo de pagamento, o pagamento inicial avulso deve ser identificado como **Pix**.

REQ.PG-05201

-   `REQ.PG-05201` Não exibir o número da agência, número da conta e a instituição bancária do recebedor.
    

![image-20260624-144141.png](images/image-20260624-144141.png)

REQ.PG-05300 a 05800true

REQ.PG-05900 a 06000true

REQ.PG-06100 a 06200true

![image-20260624-150810.png](images/image-20260624-150810.png)

REC.PG-01600true

![image-20260624-145200.png](images/image-20260624-145200.png)

REC.PG-01700true

![image-20260624-145121.png](images/image-20260624-145121.png)

REC.PG-01701 a 01702

**Cenário: Revisão e confirmação da transação de pagamento**

-   `REC.PG-01701` Informar ao usuário, na tela de confirmação, de que notificações serão enviadas quando os próximos pagamentos forem agendados.
    
-   `REC.PG-01702` Informar ao usuário que as notificações de agendamento podem ser desabilitadas na área de gestão.
    

![image-20260625-125411.png](images/image-20260625-125411.png)

REC.PG-01800 a 01900true

![image-20260624-150737.png](images/image-20260624-150737.png)

* * *

# Etapa 4: Redirecionamento

760Resumo

Nesta etapa, o usuário:

-   É redirecionado da Instituição Detentora de Conta (ID) para o ambiente da Iniciadora de Transação de Pagamento (ITP).
    

A ID deve:

-   Garantir um redirecionamento seguro, automático e sem fricções.
    
-   Redirecionar o usuário para o mesmo ambiente (app ou browser) em que iniciou a jornada.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientat
    

REQ.PG-06300 a 06600true

REQ.PG-06700true

REQ.PG-06800true

![image-20260624-151041.png](images/image-20260624-151041.png)

REC.PG-02000true

![image-20260624-151119.png](images/image-20260624-151119.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da solicitação e, quando aplicável, do pagamento inicial avulso.   
    

A ITP deve:

-   Apresentar com clareza o resultado da solicitação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da solicitação.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

REQ.PG-06900true

REQ.PG-06901true

REQ.PG-06904

-   `REQ.PG-06904` Exibir o Id (código de identificação) da autorização (número final do `consentId`, excluindo o prefixo `urn:instituicao:`).
    

REQ.PG-07200true

Ex.: Transações de valor fixo.

REQ.PG-07401

-   `REQ.PG-07201` Para transações de valor variável, exibir o valor máximo a ser transacionado, inclusive se o valor for indeterminado.
    

REQ.PG-07202

-   `REQ.PG-07202` Exibir CNPJ e Nome Fantasia da empresa recebedora. Se a empresa não possuir Nome Fantasia, exibir o Nome Empresarial/Razão Social.
    

REQ.PG-07203

-   `REQ.PG-07203` Exibir a descrição da autorização, quando preenchida.
    

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-07403

-   `REQ.PG-07204` Exibir o identificador do objeto da cobrança.  
    Ex.: Número do contrato, código do usuário etc.
    

REQ.PG-07300 true  
REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

REQ.PG-07801

-   `REQ.PG-07801` Para transações de valor váriavel, informar ao usuário que o valor máximo pode ser alterado.
    

REQ.PG-07802

-   `REQ.PG-07802` Informar ao usuário sobre a necessidade de saldo e limites transacionais da conta no momento da efetivação do pagamento.
    

REQ.PG-07803

-   `REQ.PG-07803` Informar que o uso do limite de crédito, quando contratado e disponível, é habilitado por padrão e que pode ser desabilitado na instituição de débito do usuário.
    

REQ.PG-07812

-   `REQ.PG-07812` Informar, com destaque, o caminho para acessar e gerenciar a autorização de pagamento na ITP.
    

REQ.PG-07810true

REQ.PG-06999

**Cenário: Pagamento inicial avulso**

-   `REQ.PG-06999` Para pagamento inicial avulso, exibir todas as informações mínimas aplicáveis à efetivação de um pagamento imediato com Pix, conforme as regras do arranjo.
    

REQ.PG-07000true

wide760

**Nota**

Para pagamento agendado, consulte a página **Pix Agendado**.

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07500true

REQ.PG-07600true

wide760

**Atenção!**

Conforme definido pelo arranjo de pagamento, o pagamento inicial avulso deve ser identificado como **Pix**.

REQ.PG-07700true

![image-20260826-134508.png](images/image-20260826-134508.png)

**Cenário: Interrupção da jornada**

REQ.PG-07900true

REQ.PG-08000true

![image-20260624-174843.png](images/image-20260624-174843.png)

REC.PG-02100true

REC.PG-02102true

Ex.: Você pode cancelar o pagamento até às 23:59 do dia anterior à data agendada.

![image-20260826-134556.png](images/image-20260826-134556.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00701`

**Texto**

A partir do início da oferta do serviço de Pix Automático, no primeiro acesso do usuário, informar sobre a disponibilidade do serviço (onboarding).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00702`

**Texto**

No onboarding, informar o que é o Pix Automático e suas vantagens.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00703`

**Texto**

No onboarding, informar sobre a autorização, agendamento, possibilidade de cancelamento dos pagamentos agendados e da autorização.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00704`

**Texto**

No onboarding, informar sobre a possibilidade de configuração do valor máximo por transação, em caso de cobranças com valores variáveis.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00705`

**Texto**

No onboarding, informar sobre a possibilidade de configuração do recebimento de notificações de agendamento, caso a ITP as envie.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00706`

**Texto**

No onboarding, informar sobre as regras de retentativas de liquidação em caso de saldo insuficiente, a critério do recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00707`

**Texto**

No onboarding, informar que o uso de limite de crédito pré-aprovado é habilitado automaticamente e pode ser desabilitado na instituição de débito do usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01001`

**Texto**

Para solicitações de valores variáveis, permitir que o usuário defina o valor máximo de cada pagamento recorrente, podendo inclusive ser um valor indeterminado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01002`

**Texto**

Se o recebedor definir um valor mínimo por transação, exibir mensagem informando o usuário que o valor máximo não pode ser inferior ao valor mínimo estabelecido pelo recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01003`

**Texto**

Exibir aviso claro ao usuário de que pagamentos com valor superior ao valor máximo configurado não serão efetivados e que ele poderá ser notificado para ajustar o limite ou buscar outras formas de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01004`

**Texto**

Se houver pagamento inicial avulso, por se tratar de um pagamento imediato com Pix, informar que o valor deste pagamento não está sujeito ao valor máximo definido e sim ao limite transacional do arranjo Pix.  
Ex.: O pagamento inicial está sujeito ao limite do arranjo Pix.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Especificação técnica

**ID**

`REQ.PG-01005`

**Texto**

Permitir preenchimento opcional da descrição da autorização.  

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01006`

**Texto**

Exibir nome e CPF (mascarado)/CNPJ do usuário pagador.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01007`

**Texto**

Exibir CNPJ e Nome Fantasia da empresa recebedora. Se a empresa não possuir Nome Fantasia, exibir o Nome Empresarial/Razão Social.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01008`

**Texto**

Exibir o identificador do objeto da cobrança.  
Ex.: Número do contrato, código do usuário etc.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01009`

**Texto**

Exibir a data prevista do primeiro pagamento da recorrência.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01010`

**Texto**

Exibir a periodicidade dos pagamentos futuros conforme estabelecido pelo recebedor (Semanal, Mensal, Trimestral, Semestral ou Anual).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01011`

**Texto**

Exibir a data de início da autorização e a data de validade da autorização, inclusive quando for indeterminada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-02101`

**Texto**

Exibir as regras de retentativas de efetivação de pagamento após a data de vencimento conforme definido pelo recebedor e de acordo com as regras do arranjo de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-02102`

**Texto**

Informar sobre a possibilidade de incidência de juros e multas em caso de falha na efetivação do pagamento na data de vencimento, a critério do recebedor, no próximo pagamento da recorrência.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00999`

**Texto**

Para pagamento inicial avulso, exibir todas as informações mínimas aplicáveis à solicitação de um pagamento imediato com Pix, conforme as regras do arranjo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01401`

**Texto**

Não exibir o número da agência, número da conta e a instituição bancária do recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-01402`

**Texto**

Se o pagamento inicial avulso for imediato, informar sobre a necessidade de saldo e limite Pix para efetivação do pagamento.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-03401`

**Texto**

Informar que o usuário possui até 60 minutos para confirmar a autorização de pagamento na ID.     true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04701`

**Texto**

Para transações de valor variável, exibir o valor máximo a ser transacionado, inclusive se o valor for indeterminado, conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04702`

**Texto**

Exibir nome e CPF (mascarado)/CNPJ do usuário pagador.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04801`

**Texto**

Exibir a descrição da autorização quando informado pela ITP.  
Ex.: Introdução à Música Clássica, Conta de Energia.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04802`

**Texto**

Exibir CNPJ e Nome Fantasia da empresa recebedora. Se a empresa não possuir Nome Fantasia, exibir o Nome Empresarial/Razão Social.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04803`

**Texto**

Exibir o identificador do objeto da cobrança conforme informado pela ITP.  
Ex.: Número do contrato, código do usuário etc.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04804`

**Texto**

Exibir a periodicidade dos pagamentos futuros conforme informado pela ITP (Semanal, Mensal, Trimestral, Semestral ou Anual).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04805`

**Texto**

Exibir a data prevista do primeiro pagamento da recorrência conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04806`

**Texto**

Exibir a data de início e a data de validade da autorização, inclusive quando for indeterminada, conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04807`

**Texto**

Exibir informação sobre a existência de retentativas de efetivação de pagamento conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04808`

**Texto**

Exibir informação sobre a possibilidade de incidência de juros e multas em caso de falha na efetivação do pagamento na data de vencimento, a critério do recebedor, no próximo pagamento da recorrência conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04699`

**Texto**

Para pagamento inicial avulso, exibir todas as informações mínimas aplicáveis à solicitação de um pagamento imediato com Pix, conforme as regras do arranjo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05201`

**Texto**

Não exibir o número da agência, número da conta e a instituição bancária do recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-06904`

**Texto**

Exibir o Id (código de identificação) da autorização (número final do `consentId`, excluindo o prefixo `urn:instituicao:`).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07201`

**Texto**

Para transações de valor variável, exibir o valor máximo a ser transacionado, inclusive se o valor for indeterminado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07202`

**Texto**

Exibir CNPJ e Nome Fantasia da empresa recebedora. Se a empresa não possuir Nome Fantasia, exibir o Nome Empresarial/Razão Social.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07203`

**Texto**

Exibir a descrição da autorização, se o usuário tiver preenchido.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07204`

**Texto**

Exibir o identificador do objeto da cobrança.  
Ex.: Número do contrato, código do usuário etc.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07801`

**Texto**

Para transações de valor váriavel, informar ao usuário que o valor máximo pode ser alterado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07802`

**Texto**

Informar sobre a necessidade de saldo e limites transacionais da conta no momento da efetivação do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07803`

**Texto**

Informar que o uso do limite de crédito, quando contratado e disponível, é habilitado por padrão e que pode ser desabilitado na instituição de débito do usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07812`

**Texto**

Informar, com destaque, o caminho para acessar e gerenciar a autorização de pagamento na ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-06999`

**Texto**

Para pagamento inicial avulso, exibir todas as informações mínimas aplicáveis à efetivação de um pagamento imediato com Pix, conforme as regras do arranjo.
