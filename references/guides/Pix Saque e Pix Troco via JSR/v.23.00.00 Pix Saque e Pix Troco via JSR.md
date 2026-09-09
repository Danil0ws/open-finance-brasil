# v.23.00.00 Pix Saque e Pix Troco via JSR

# Visão geral

A Jornada de Iniciação de **Pagamento Sem Redirecionamento (JSR)** ou Pix por Biometria ou Pix por Aproximação ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento utilizando um vínculo de conta previamente criado através da jornada de Vinculação de Conta via Open Finance.
    
2.  Após revisar os dados, o usuário confirma a transação na ITP através da chave de segurança.
    
3.  Por fim, a ITP informa o resultado da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-181558.png](images/image-20260112-181558.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de Pagamento imediato Sem Redirecionamento com Pix com finalidade de saque e troco via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Confirmação
    
3.  Efetivação
    

## Cenário de referência

-   Pagamento imediato sem redirecionamento com Pix Saque ou Pix Troco.
    
-   Alçada simples.
    

> Transações temporizadas para JSR devem observar as regras específicas previstas na página correspondente.

wide760

**Atenção!**

A jornada de **Pix Saque e Pix Troco** não suporta pagamentos com múltiplos aprovadores.

Consulte a página **Casos de erro de Pix Saque e Pix Troco** para mais informações sobre os possíveis erros e como comunicá-los ao usuário durante a jornada.

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a Jornada de Pagamento Sem Redirecionamento (JSR), como um **Pix por Biometria** ou **Pix por Aproximação**, via Open Finance.
    
-   Escolhe o vínculo de conta previamente criado para realizar o pagamento.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada. 
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente do vínculo de conta.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

![image-20260623-142727.png](images/image-20260623-142727.png)

REQ.PG-00100 a 00200true

![image-20260622-204554.png](images/image-20260622-204554.png)

REQ.PG-00201 a 00202true

![image-20260622-201431.png](images/image-20260622-201431.png)

REQ.PG-00708 a 00710true

![image-20260622-181612.png](images/image-20260622-181612.png)

REQ.PG-00711true

![image-20260622-181833.png](images/image-20260622-181833.png)

REQ.PG-00800true

REQ.PG-00900true

REQ.PG-01000true

![image-20260622-181700.png](images/image-20260622-181700.png)

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01300true

![image-20260622-182733.png](images/image-20260622-182733.png)

REQ.PG-01500true

REQ.PG-01700true

REQ.PG-01800true

Nota.Recebedortrue

![image-20260622-182951.png](images/image-20260622-182951.png)

REQ.PG-01900true

REQ.PG-02000true

![image-20260622-183032.png](images/image-20260622-183032.png)

REQ.PG-02100true

REQ.PG-02101 a 02102true

REQ.PG-02200 a 02400true

![image-20260622-201753.png](images/image-20260622-201753.png)

REC.PG-00100true

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00501 a 00504true

![image-20260622-183829.png](images/image-20260622-183829.png)

REC.PG-00600true

![image-20260622-184017.png](images/image-20260622-184017.png)

REC.PG-00601true

![image-20260306-175413.png](images/image-20260306-175413.png)

REC.PG-00602 a 00606true

![image-20260622-184855.png](images/image-20260622-184855.png)

REC.PG-00800 a 00900true

REC.PG-01000true

REc.PG-01100true

REC.PG-01300true

![image-20260622-202328.png](images/image-20260622-202328.png)

* * *

# Etapa 2: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Confirma a solicitação utilizando as credenciais geradas (biometria) na etapa de **Efetivação** da Vinculação de Conta.
    

A ITP deve:

-   Garantir um ambiente seguro para confirmação através da biometria.
    
-   Viabilizar a confirmação com o mínimo de fricção.
    

REQ.PG-05899true

![image-20260622-202708.png](images/image-20260622-202708.png)

REQ.PG-05900 a 06000true

![image-20260622-202834.png](images/image-20260622-202834.png)

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

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07301 a 07302true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

![image-20260623-142008.png](images/image-20260623-142008.png)

REQ.PG-08100true

![image-20260622-202946.png](images/image-20260622-202946.png)

REC.PG-02100true

REC.PG-02103 a 02104true

![image-20260622-201144.png](images/image-20260622-201144.png)

* * *
