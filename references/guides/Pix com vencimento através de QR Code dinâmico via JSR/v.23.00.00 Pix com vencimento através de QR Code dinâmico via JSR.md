# v.23.00.00 Pix com vencimento através de QR Code dinâmico via JSR

# Visão geral

A Jornada de Iniciação de **Pagamento Sem Redirecionamento (JSR)** ou Pix por Biometria ou Pix por Aproximação ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento utilizando um vínculo de conta previamente criado através da jornada de Vinculação de Conta via Open Finance.
    
2.  Após revisar os dados, o usuário confirma a transação na ITP através da chave de segurança.
    
3.  Por fim, a ITP informa o resultado da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-181558.png](images/image-20260112-181558.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de Pagamento Sem Redirecionamento com vencimento através de QR Code dinâmico com Pix via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Confirmação
    
3.  Efetivação
    

## Cenário de referência

-   Pagamento imediato ou agendado de cobrança com vencimento através de QR Code dinâmico com Pix.
    
-   Alçada simples.
    

Variações da jornadatrue

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1 : Solicitação

![image-20260427-144149.png](images/image-20260427-144149.png)760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento Sem Redirecionamento (JSR), como um **Pix por Biometria** ou **Pix por Aproximação**, com vencimento através da leitura de QR Code dinâmico, via Open Finance.
    
-   Escolhe o vínculo de conta previamente criado para realizar a solicitação.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada.
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente do vínculo de conta.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-00100 a 00200true

![image-20260617-175832.png](images/image-20260617-175832.png)

REQ.PG-00201 a 00202true

![image-20260617-180031.png](images/image-20260617-180031.png)

REQ.PG-00800true

REQ.PG-00900true

REQ.PG-01000true

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01300true

wide760

**Nota**

Para permitir o agendamento do pagamento, consulte a página **Pix Agendado**.

REQ.PG-01500true

REQ.PG-01700true

REQ.PG-01800true

Nota.Recebedortrue

REQ.PG-01900true

REQ.PG-01901true

REQ.PG-02000true

REQ.PG-02100true

REQ.PG-02200 a 02400true

![image-20260617-185508.png](images/image-20260617-185508.png)

REC.PG-00100true

![image-20260617-185601.png](images/image-20260617-185601.png)

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260617-185701.png](images/image-20260617-185701.png)

REC.PG-00800 a 00900true

REC.PG-01000true

REc.PG-01100true

REC.PG-01200true

REC.PG-01300true

![image-20260617-190028.png](images/image-20260617-190028.png)

* * *

# Etapa 2: Confirmação

760ResumoNesta etapa, o usuário:

-   Confirma a solicitaçãoutilizando as credenciais geradas na etapa de **Efetivação** da Vinculação de Conta**.**
    

A ITP deve:

-   Garantir um ambiente seguro para confirmação através das credenciais.
    
-   Viabilizar a confirmação com o mínimo de fricção.  

REQ.PG-05899true

![image-20260617-190212.png](images/image-20260617-190212.png)

REQ.PG-05900 a 06000true

![image-20260617-190354.png](images/image-20260617-190354.png)

* * *

# Etapa 3: Efetivação

760ResumoNesta etapa final da jornada, o usuário:

-   Visualiza o resultado da solicitação.     
    

A ITP deve:

-   Apresentar com clareza o resultado da solicitação.
    
-   Disponibilizar um comprovante com os principais dados da solicitação.  
    
-   Quando aplicável, exibir mensagens de erro ou pendências, como autorizações em múltiplas alçadas, transações temporizadas ou indisponibilidade momentânea dos sistemas. 

REQ.PG-06900true

REQ.PG-07000true

wide760

**Nota**

Para pagamento agendado, consulte a página **Pix Agendado**.

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

![image-20260617-190714.png](images/image-20260617-190714.png)

REQ.PG-08100true

![image-20260625-123941.png](images/image-20260625-123941.png)

REC.PG-02100true

![image-20260617-191002.png](images/image-20260617-191002.png)

* * *
