# v.23.00.00 Pagamentos com Múltiplos Aprovadores via JSR

Esta página reúne os requisitos e recomendações aplicáveis à jornada de pagamento sem redirecionamento com Pix via Open Finance com múltiplos aprovadores (múltipla alçada) via JSR.

## Etapas da jornada

2.   Confirmação
    
3.   Efetivação
    

wide760

**Nota**

Além dos requisitos e recomendações previstos nesta página, aplicam-se a esta jornada aqueles descritos em:

-   Pix via hybrid flow;
    
-   Pix com vencimento através de QR Code dinâmico via hybrid flow;
    
-   Pix Agendado via hybrid flow;
    
-   Pix Automático via hybrid flow;
    
-   Pix Saque e Pix Troco via hybrid flow;
    
-   Transferências Inteligentes via hybrid flow;
    

-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

wide760

**Atenção**

A jornada de **Pix Saque e Pix Troco** não suporta pagamentos com múltiplos aprovadores.

Consulte a página **Casos de erro de Pix Saque e Pix Troco** para mais informações sobre os possíveis erros e como comunicá-los ao usuário durante a jornada.

* * *

# Etapa 2: Confirmação

760Resumo

Nesta etapa, o usuário solicitante:

-   Confirma a solicitação utilizando as credenciais geradas na etapa de **Efetivação** da Vinculação de Conta**.**
    

A ID deve:

-   Comunicar a ITP sobre a necessidade de múltiplas aprovações da solicitação .
    
-   Comunicar os demais aprovadores sobre a pendência de aprovação.
    

wide760#F4F5F7

## Requisitos - ID

**Cenário: Dinâmica de aprovação**

REQ.PG-13700 a 13800true

REQ.PG-14400 a 14900true

![image-20260624-163818.png](images/image-20260624-163818.png)

REC.PG-04500 a 04600true

![image-20260624-163839.png](images/image-20260624-163839.png)

* * *

# Etapa 3: Efetivação

760Resumo

Nesta etapa final da jornada, A ITP deve:

-   Exibir o resultado da solicitação com a pendência de aprovação.
    
-   Possibilitar que o usuário solicitante cancele a solicitação enquanto ainda estiver pendente de aprovações.
    

REQ.PG-15100 a 15200true

![image-20260624-163247.png](images/image-20260624-163247.png)wide760#F4F5F7

## Requisitos - ID

**Cenário: Interrupção da jornada**

REQ.PG-07999

-   `REQ.PG-07999` Se o usuário solicitante cancelar a solicitação antes de todas as aprovações, informar aos usuários envolvidos sobre o cancelamento.
    

REQ.PG-08000true

![image-20260624-164500.png](images/image-20260624-164500.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático e Transferências Inteligentes

**Jornada**

Múltiplos Aprovadores (JSR)

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.PG-07999`

**Texto**

Se o usuário solicitante cancelar a solicitação antes de todas as aprovações, informar os usuários envolvidos sobre o cancelamento.
