# v.23.00.00 Pix Automático via JSR

# Visão geral

A Jornada de Iniciação de **Pagamento Sem Redirecionamento (JSR)** ou Pix por Biometria ou Pix por Aproximação ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento utilizando um vínculo de conta previamente criado através da jornada de Vinculação de Conta via Open Finance.
    
2.  Após revisar os dados, o usuário confirma a transação na ITP através da chave de segurança.
    
3.  Por fim, a ITP informa o resultado da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-181558.png](images/image-20260112-181558.png)

* * *

# Telas de exemplo 

wide760

**Nota**

Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%600

## Fluxo de telas

![image-20260521-175605.png](images/image-20260521-175605.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamentos recorrentes com Pix Automático sem redirecionamento via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Confirmação
    
3.  Efetivação
    

## Cenário de referência

-   Autorização de pagamentos recorrentes com Pix Automático sem redirecionamento.
    
-   Alçada simples.
    

Variações da jornadatrue

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a Jornada de pagamento Sem Redirecionamento (JSR), como um **Pix por Biometria** ou **Pix por Aproximação**, via Open Finance.
    
-   Escolhe o vínculo de conta previamente criado para realizar o pagamento.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada. 
    

A ITP deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente do vínculo de conta.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

![image-20260527-190430.png](images/image-20260527-190430.png)

REQ.PG-00100 a 00200true

REQ.PG-00201 a 00202true

![image-20260624-192020.png](images/image-20260624-192020.png)

REQ.PG-00701 a 00707true

![image-20260624-192056.png](images/image-20260624-192056.png)

REQ.PG-00800true

REQ.PG-01000true

Ex.: Transações de valor fixo como serviços de streaming.

REQ.PG-01001 a 01004true

REQ.PG-01005true

REQ.PG-01006true

REQ.PG-01007true

REQ.PG-01008 a 01010true

REQ.PG-01011true

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01900true

REQ.PG-02000true

![image-20260625-130012.png](images/image-20260625-130012.png)

REQ.PG-02101 a 02102true

REQ.PG-02200 a 02400true

![image-20260625-130432.png](images/image-20260625-130432.png)

REQ.PG-00999true

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

REQ.PG-01401 a 01402true

![image-20260624-194235.png](images/image-20260624-194235.png)

REC.PG-00100true

![image-20260624-194313.png](images/image-20260624-194313.png)

**Cenário: Onboarding**

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260623-204411.png](images/image-20260623-204411.png)

REC.PG-00800 a 00900true

REC.PG-01000true

![image-20260623-205008.png](images/image-20260623-205008.png)

REC.PG-01300true

![image-20260625-130605.png](images/image-20260625-130605.png)

* * *

# Etapa 2: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Confirma a solicitação utilizando as credenciais geradas na etapa de **Efetivação** da Vinculação de Conta.
    

A ITP deve:

-   Garantir um ambiente seguro para confirmação através da biometria.
    
-   Viabilizar a confirmação com o mínimo de fricção.  
    

REQ.PG-05899true

![image-20260624-194743.png](images/image-20260624-194743.png)

REQ.PG-05900 a 06000true

![image-20260624-194916.png](images/image-20260624-194916.png)

* * *

# Etapa 3: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   Visualiza o resultado da solicitação.     
    

A ITP deve:

-   Apresentar com clareza o resultado da solicitação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da solicitação.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

REQ.PG-06900true

REQ.PG-06901true

REQ.PG-06904true

REQ.PG-07200true

Ex.: Transações de valor fixo.

REQ.PG-07401true

REQ.PG-07202true

REQ.PG-07203true

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-07403true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

REQ.PG-07801true

REQ.PG-07802true

REQ.PG-07803true

REQ.PG-07812true

REQ.PG-07810true

REQ.PG-06999true

REQ.PG-07000true

wide760

**Nota**

Para pagamento agendado, consulte a página **Pix Agendado**.

REQ.PG-07100true

REQ.PG-07500true

REQ.PG-07600true

wide760

**Atenção!**

Conforme definido pelo arranjo de pagamento, o pagamento inicial avulso deve ser identificado como **Pix**.

REQ.PG-07700true

![image-20260826-134718.png](images/image-20260826-134718.png)

REQ.PG-08100true

![image-20260624-174843.png](images/image-20260624-174843.png)

REC.PG-02100true

REC.PG-02102true

Ex.: Você pode cancelar o pagamento até às 23:59 do dia anterior à data agendada.

![image-20260826-134813.png](images/image-20260826-134813.png)
