# v.23.00.00 Pix Agendado via JSR

# Visão geral

A Jornada de Iniciação de **Pagamento Sem Redirecionamento (JSR)** ou Pix por Biometria ou Pix por Aproximação ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento utilizando um vínculo de conta previamente criado através da jornada de Vinculação de Conta via Open Finance.
    
2.  Após revisar os dados, o usuário confirma a transação na ITP através da chave de segurança.
    
3.  Por fim, a ITP informa o resultado da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-181558.png](images/image-20260112-181558.png)

* * *

## Protótipo navegável

100%600

## Fluxo de telas

![image-20260619-195817.png](images/image-20260619-195817.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamento agendado (único ou recorrente) com Pix sem redirecionamento via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Confirmação
    
3.  Efetivação
    

## Cenário de referência

-   Agendamento (único ou recorrente) com Pix sem redirecionamento.
    
-   Alçada simples.
    

Variações da jornadatrue

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a Jornada de Pagamento Sem Redirecionamento (JSR), como um **Pix por Biometria** ou **Pix por Aproximação**, via Open Finance.
    
-   Escolhe o vínculo de conta previamente criado que será utilizado.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada. 
    

A ITP deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente do vínculo de conta.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

###   
Métodos de iniciação com Pix

![image-20260319-194816.png](images/image-20260319-194816.png)

REQ.PG-00100 a 00200true

![image-20260619-195942.png](images/image-20260619-195942.png)

REQ.PG-00201 a 00202true

![image-20260619-200118.png](images/image-20260619-200118.png)

REQ.PG-00800true

REQ.PG-00900true

REQ.PG-01000true

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01201 a 01202true

![image-20260619-200421.png](images/image-20260619-200421.png)

REQ.PG-01203 a 01204true

![image-20260619-200556.png](images/image-20260619-200556.png)

REQ.PG-01205 a 01209true

![image-20260827-123609.png](images/image-20260827-123609.png)

REQ.PG-01210trueREQ.PG-01211true

REQ.PG-01400true

REQ.PG-01500true

REQ.PG-01600true

REQ.PG-01700true

REQ.PG-01800true

Nota.Recebedortrue

REQ.PG-01900true

REQ.PG-02000true

REQ.PG-02100true

REQ.PG-02200 a 02400true

![image-20260827-124007.png](images/image-20260827-124007.png)

REC.PG-00100true

![image-20260619-201838.png](images/image-20260619-201838.png)

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260619-201901.png](images/image-20260619-201901.png)

REC.PG-00800 a 00900true

REC.PG-01000true

REc.PG-01100true

REC.PG-01300true

![image-20260827-124107.png](images/image-20260827-124107.png)

* * *

# Etapa 2: Confirmação

760ResumoNesta etapa, o usuário:

-   Confirma a solicitação utilizando as credenciais geradas na etapa de **Efetivação** da Vinculação de Conta**.**
    

A ITP deve:

-   Garantir um ambiente seguro para confirmação através das credenciais.
    
-   Viabilizar a confirmação com o mínimo de fricção.  

REQ.PG-05899true

![image-20260619-202226.png](images/image-20260619-202226.png)

REQ.PG-05900 a 06000true

![image-20260619-202433.png](images/image-20260619-202433.png)

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

REQ.PG-06902 a 06903true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07501true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

REQ.PG-07801true

REQ.PG-07809true

REQ.PG-07810true

REQ.PG-07811true

wide760

**Nota**

A experiência de alteração permite que o usuário altere parâmetros como data, recebedor ou ID, embora, no backend, esteja cancelando o agendamento vigente e criando uma nova autorização de agendamento.

Consulte a página **Gestão de Pix Agendado** para mais informações.

![image-20260826-135544.png](images/image-20260826-135544.png)

REQ.PG-08100true

![image-20260619-203021.png](images/image-20260619-203021.png)

REC.PG-02100true

REC.PG-02101true

REC.PG-02102true

![image-20260826-135448.png](images/image-20260826-135448.png)
