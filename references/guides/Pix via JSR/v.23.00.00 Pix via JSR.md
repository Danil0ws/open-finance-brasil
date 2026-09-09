# v.23.00.00 Pix via JSR

# Visão geral

A Jornada de Iniciação de Pagamento Sem Redirecionamento (JSR) ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento utilizando um vínculo de conta previamente criado através da jornada de Vinculação de Conta via Open Finance.
    
2.  Após revisar os dados, o usuário confirma a transação na ITP através da chave de segurança.
    
3.  Por fim, a ITP informa o resultado da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-181558.png](images/image-20260112-181558.png)

* * *

# Telas de exemplo

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pelas marcas **Wiscredi** e **Cloud Finance**, sendo esta última utilizada como **solução whitelabel pelo recebedor Seu Lar**.  
A Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%600

## Fluxo de telas

![image-20260417-135810.png](images/image-20260417-135810.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamento imediato com Pix sem redirecionamento via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Confirmação
    
3.  Efetivação  
    

## Cenário de referência

-   Pagamento imediato com Pix sem redirecionamento.
    
-   Alçada simples.
    

Variações da jornada

> Jornadas que envolvam múltiplos aprovadores e transações temporizadas para JSR devem observar as regras específicas previstas nos subcapítulos correspondentes.

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a Jornada de pagamento Sem Redirecionamento (JSR), como um **Pix por Biometria** ou **Pix por Aproximação**, via Open Finance.
    
-   Escolhe o vínculo de conta previamente criado para realizar o pagamento.
    
-   Insere e revisa os dados da transação conforme as regras da forma de iniciação selecionada. 
    

A ITP deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente do vínculo de conta.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

![image-20260417-135827.png](images/image-20260417-135827.png)

REQ.PG-00100 a 00200true

![image-20260615-183300.png](images/image-20260615-183300.png)

REQ.PG-00201 a 00202

**Cenário: Busca e seleção do vínculo**

-   `REQ.PG-00201` Permitir que o usuário selecione, com agilidade e precisão, a instituição com a qual possui vínculo de conta.
    
-   `REQ.PG-00202` Exibir todas as instituições com as quais o usuário tenha efetuado a vinculação de conta no dispositivo utilizado.
    

![image-20260615-183417.png](images/image-20260615-183417.png)

REQ.PG-00800true

REQ.PG-00900true

REQ.PG-01000true

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01300true

wide760

**Nota**

Para permitir o agendamento do pagamento, consulte a página **Pix Agendado**.

REQ.PG-01400true

Ex.: Pix via chave Pix ou inserção manual de dados transacionais.

REQ.PG-01500true

Ex.: Pix via QR Code.

REQ.PG-01600true

REQ.PG-01700true

REQ.PG-01800true

Nota.Recebedortrue

REQ.PG-01900true

REQ.PG-02000true

REQ.PG-02100true

REQ.PG-02200 a 02400true

![image-20260616-185719.png](images/image-20260616-185719.png)

REC.PG-00100true

![image-20260615-184224.png](images/image-20260615-184224.png)

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260615-184603.png](images/image-20260615-184603.png)

REC.PG-00800 a 00900true

REc.PG-01100true

REC.PG-01300true

![image-20260615-184743.png](images/image-20260615-184743.png)

* * *

# Etapa 2: Confirmação

760ResumoNesta etapa, o usuário:

-   Confirma a transação utilizando as credenciais geradas na etapa de **Efetivação** da Vinculação de Conta**.**
    

A ITP deve:

-   Garantir um ambiente seguro para confirmação através das credenciais.
    
-   Viabilizar a confirmação com o mínimo de fricção.  

REQ.PG-05899#F4F5F7

## Requisitos - ITP

**Cenário: Confirmação via validação das chaves (FIDO)**

-   `REQ.PG-05899` Solicitar que o usuário confirme a solicitação através da inserção das credenciais criadas na **Efetivação** da Vinculação de Conta.
    

![image-20260616-185813.png](images/image-20260616-185813.png)

REQ.PG-05900 a 06000true

![image-20260615-184945.png](images/image-20260615-184945.png)

* * *

# Etapa 3: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   Visualiza o resultado da transação.     
    

A ITP deve:

-   Apresentar com clareza o resultado da transação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da transação.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

REQ.PG-06900trueREQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

![image-20260615-194121.png](images/image-20260615-194121.png)REQ.PG-08100

**Cenário: Interrupção da jornada**

-   `REQ.PG-08100` Se a ITP disponibilizar interrupção da jornada através de cancelamento ativo como um botão "Cancelar", exibir mensagem confirmando o cancelamento da solicitação.
    

![image-20260615-194842.png](images/image-20260615-194842.png)

REC.PG-02100true

![image-20260615-195530.png](images/image-20260615-195530.png)

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 637

**ID**

`REQ.PG-00201`

**Texto**

Permitir que o usuário selecione, com agilidade e precisão, a instituição com a qual possui vínculo de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 637

**ID**

`REQ.PG-00202`

**Texto**

Exibir todas as instituições com as quais o usuário tenha efetuado a vinculação de conta no dispositivo utilizado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 637

**ID**

`REQ.PG-05899`

**Texto**

Solicitar que o usuário confirme a solicitação através da inserção das credenciais criadas na **Efetivação** da Vinculação de Conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza - IN BCB 637

**ID**

`REQ.PG-08100`

**Texto**

Se a ITP disponibilizar interrupção da jornada através de cancelamento ativo como um botão "Cancelar", exibir mensagem confirmando o cancelamento da solicitação.
