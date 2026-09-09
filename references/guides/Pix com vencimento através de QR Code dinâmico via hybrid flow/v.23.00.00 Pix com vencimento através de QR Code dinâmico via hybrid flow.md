# v.23.00.00 Pix com vencimento através de QR Code dinâmico via hybrid flow

# Visão geral

A Jornada de Iniciação de Pagamento Com Redirecionamento com **Pix com vencimento através de QR Code dinâmico** ocorre quando:

1.  O usuário lê o QR Code com as informações da cobrança com vencimento e a Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento com Pix com vencimento através de QR Code dinâmico via Open Finance.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida, com clareza sobre as próximas etapas.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, revisa os dados da transação configurada na ITP e confirma o pagamento.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Por fim, a ITP informa o status da solicitação de pagamento, concluindo a jornada.
    

* * *

# Telas de exemplo

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pelas marca **Wiscredi** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%1000

## Fluxo de telas

![image-20260331-203615.png](images/image-20260331-203615.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamento com vencimento através de QR Code dinâmico com Pix via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação
    

## Cenário de referência

-   Pagamento com vencimento através de QR Code dinâmico com Pix.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

Variações da jornadatrue

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

![image-20260331-203832.png](images/image-20260331-203832.png)1011Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento com Pix via Open Finance.
    
-   Escolhe a Instituição Detentora de Conta (ID) que será usada para realizar o pagamento.
    
-   Insere e revisa os dados da transação conforme as regras da forma de iniciação selecionada. 
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-00100 a 00200true

![image-20260616-202307.png](images/image-20260616-202307.png)

REQ.PG-00300 a 00700true

![image-20260616-202525.png](images/image-20260616-202525.png)

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

REQ.PG-01901

-   `REQ.PG-01901` Impedir que o usuário altere os dados do QR Code, à exceção de:
    
    -   Valor (caso permitido pelo recebedor);
        
    -   Data pretendida do pagamento (conforme permitido pelo recebedor e disponibilizado pela ITP);
        
    -   Campo de solicitação de informações ao pagador (se houver).
        

REQ.PG-02000true

REQ.PG-02100true

REQ.PG-02200 a 02400true

REQ.PG-02500true

![image-20260625-123224.png](images/image-20260625-123224.png)

REC.PG-00100true

![image-20260616-203412.png](images/image-20260616-203412.png)

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260616-204145.png](images/image-20260616-204145.png)

REC.PG-00700true

![image-20260616-204328.png](images/image-20260616-204328.png)

REC.PG-00800 a 00900true

REC.PG-01000true

REc.PG-01100true

REC.PG-01200true

REC.PG-01300true

![image-20260617-185903.png](images/image-20260617-185903.png)

* * *

# Etapa 2: Direcionamento

1011Resumo

Nesta etapa, o usuário:

-   É direcionado da Iniciadora (ITP) para a sua Detentora de Conta (ID).
    

A ITP deve:

-   Orientar o usuário sobre o direcionamento.
    
-   Assegurar que a navegação ocorra de forma transparente, conforme o dispositivo utilizado.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-02600 a 03100true

REQ.PG-03200 a 03400true

REQ.PG-03500true

REQ.PG-03600true

![image-20260616-205143.png](images/image-20260616-205143.png)

wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01400true

REC.PG-01500true

![image-20260616-205333.png](images/image-20260616-205333.png)

* * *

# Etapa 3: Confirmação

1011Resumo

Nesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Pode escolher a que deseja usar para fazer o pagamento se ele possuir mais de uma conta na ID.
    
-   Revisa as informações da solicitação enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma a solicitação.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo da solicitação.
    
-   Permitir a edição da conta de débito, se o usuário possuir múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    
-   Comunicar o resultado da autorização à ITP.
    
-   Enviar notificações ao usuário e aos demais aprovadores nos cenários de múltiplos aprovadores.
    

REQ.PG-03700 a 03900true

![image-20260617-134519.png](images/image-20260617-134519.png)

REQ.PG-04000 a 04500true

![image-20260617-134645.png](images/image-20260617-134645.png)

Fluxograma ITP > IDtrue

REQ.PG-04600true

REQ.PG-04700true

REQ.PG-04800true

REQ.PG-04900true

REQ.PG-05000true

Nota.Recebedortrue

REQ.PG-05100true

REQ.PG-05200true

REQ.PG-05300 a 05800true

![image-20260625-123630.png](images/image-20260625-123630.png)

REQ.PG-05900 a 06000true

REQ.PG-06100 a 06200true

![image-20260617-140504.png](images/image-20260617-140504.png)

REC.PG-01600true

![image-20260617-140912.png](images/image-20260617-140912.png)

REC.PG-01700true

![image-20260617-141036.png](images/image-20260617-141036.png)

REC.PG-01800 a 01900true

![image-20260617-141219.png](images/image-20260617-141219.png)

* * *

# Etapa 4: Redirecionamento

760Resumo

Nesta etapa, o usuário:

-   É redirecionado da Instituição Detentora de Conta (ID) para o ambiente da Iniciadora de Transação de Pagamento (ITP).
    

A ID deve:

-   Garantir um redirecionamento seguro, automático e sem fricções.
    
-   Redirecionar o usuário para o mesmo ambiente (app ou browser) em que iniciou a jornada.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

wide760#F4F5F7

## Requisitos - ID

**Cenário: Tela de transição**

REQ.PG-06300 a 06600true

REQ.PG-06700true

REQ.PG-06800true

![image-20260617-141317.png](images/image-20260617-141317.png)

REC.PG-02000true

![image-20260617-141352.png](images/image-20260617-141352.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da transação.   
    

A ITP deve:

-   Apresentar com clareza o resultado da transação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da transação.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

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

![image-20260617-141704.png](images/image-20260617-141704.png)

**Cenário: Interrupção da jornada**

REQ.PG-07900true

REQ.PG-08000true

![image-20260617-142103.png](images/image-20260617-142103.png)

REC.PG-02100true

![image-20260625-123759.png](images/image-20260625-123759.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix com vencimento através de QR Code dinâmico

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

PUX - 279

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 637

**ID**

`REQ.PG-01901`

**Texto**

Impedir que o usuário altere os dados do QR Code, à exceção de:

-   Valor (caso permitido pelo recebedor);
    
-   Data pretendida do pagamento (conforme permitido pelo recebedor e disponibilizado pela ITP);
    
-   Campo de solicitação de informações ao pagador (se houver).
