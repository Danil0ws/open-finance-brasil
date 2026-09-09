# v.23.00.00 Casos de erro de Pix Saque e Pix Troco

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a **comunicação de erros na** **jornada de pagamento com Pix Saque e Pix Troco com e sem redirecionamento** via Open Finance. 

* * *

Introdução - Mensagem de errotrue

* * *

# Geral

REQ.PG-09100true

![image-20251120-185401.png](images/image-20251120-185401.png)

* * *

# Etapa 1: Solicitação

REQ.PG-09200true

![image-20251120-185748.png](images/image-20251120-185748.png)

* * *

# Etapa 2: Direcionamento

REQ.PG-09300true

![image-20251123-175537.png](images/image-20251123-175537.png)

* * *

# Etapa 3: Confirmação

REQ.PG-09400true

![image-20251120-183955.png](images/image-20251120-183955.png)

REQ.PG-09500true

![image-20251123-175846.png](images/image-20251123-175846.png)

REQ.PG-09600true  
 

![image-20251121-195418.png](images/image-20251121-195418.png)

REQ.PG-09700true

![image-20251120-193343.png](images/image-20251120-193343.png)

REQ.PG-09800true

![image-20251124-175319.png](images/image-20251124-175319.png)![image-20251120-193636.png](images/image-20251120-193636.png)

REQ.PG-09900true

![image-20251121-191400.png](images/image-20251121-191400.png)

REQ.PG-10000true

![image-20251121-191632.png](images/image-20251121-191632.png)

REQ.PG-10100true

![image-20251121-141915.png](images/image-20251121-141915.png)

REQ.PG-10200true

![image-20251121-144823.png](images/image-20251121-144823.png)

REQ.PG-10201

-   `REQ.PG-10201` Ao identificar tentativa de iniciação de Pix Saque ou Pix Troco em conta que exija múltiplas aprovações, informar ao usuário que a operação não pode ser realizada nesse contexto.
    
    -   **Ações para prosseguir:** \- 
        
    -   **Exemplo de mensagem:** **Não foi possível concluir a transação**
        
        Esta operação não é permitida porque sua conta requer múltiplas aprovações.
        

REQ.PG-10400true

![image-20260323-170003.png](images/image-20260323-170003.png)

  

REQ.PG-10500true

![image-20251124-184027.png](images/image-20251124-184027.png)

* * *

# Etapa 4: Redirecionamento

REQ.PG-10600true

![image-20260323-165706.png](images/image-20260323-165706.png)

* * *

# Etapa 5: Efetivação

REQ.PG-10700true

![image-20251120-185316.png](images/image-20251120-185316.png)REQ.PG-10702

-   `REQ.PG-10702` Ao receber o usuário da ID após erro decorrente de uma solicitação que exija múltiplas aprovações, informar que a transação não foi concluída.
    
    -   **Exemplo de mensagem detalhada:** **Não foi possível concluir a transação**  
        Esta operação não é permitida porque sua conta requer múltiplas aprovações.
        
    -   **Exemplo de mensagem genérica: Transação não concluída.**  
        Não conseguimos processar seu pagamento.
        

**Nota**

Na Jornada Com Redirecionamento, como o usuário já foi informado do erro de forma detalhada na ID, fica a critério da ITP exibir uma mensagem de erro de forma detalhada ou uma mensagem genérica de falha da transação.

![image-20260622-203458.png](images/image-20260622-203458.png)

REC.PG-02600true

![image-20251125-215521.png](images/image-20251125-215521.png)REC.PG-02601

**Cenário: Erros na efetivação**

-   `REC.PG-02601` Ao receber o usuário da ID após erro decorrente de uma solicitação que exija múltiplas aprovações, caso a ITP exiba uma mensagem genérica de falha da transação, orientar o usuário a entrar em contato com a ID para obter mais detalhes.
    
    -   **Ações para prosseguir:** \- 
        
    -   **Exemplo de mensagem genérica: Transação não concluída.**  
        Não conseguimos processar seu pagamento. Entre em contato com seu banco para mais detalhes.
        

![image-20260622-203927.png](images/image-20260622-203927.png)

* * *

# Casos de erro - Pix Saque e Pix Troco Sem Redirecionamento (JSR)

Esta seção descreve os requisitos e recomendações para tratar erros que ocorrem somente nas jornada de Pix Saque e Pix Troco Sem Redirecionamento (JSR)

# Etapa 3: Efetivação

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-10703

**Cenário: Erros na efetivação**

-   `REQ.PG-10703` Ao ser informada pela ID sobre a impossibilidade de iniciação de Pix Saque ou Pix Troco em conta que exija múltiplas aprovações, informar ao usuário que a operação não pode ser realizada nesse contexto.
    
    -   **Ações para prosseguir:** \- 
        
    -   **Exemplo de mensagem detalhada:** **Transação não concluída.**  
        Esta operação não é permitida porque sua conta requer múltiplas aprovações.
        

**Nota**

Na Jornada Sem Redirecionamento, como o usuário não foi informado do erro na ID, a ITP deve exibir uma mensagem de erro de forma detalhada.

![image-20260622-203607.png](images/image-20260622-203607.png)

wide760#F4F5F7

## Recomendações - ITP

REC.PG-02602

**Cenário: Erros na efetivação**

-   `REC.PG-02602` Na mensagem de erro sobre a impossibilidade de iniciação de Pix Saque ou Pix Troco em conta que exija múltiplas aprovações, orientar o usuário a entrar em contato com a ID para obter mais detalhes.
    
    -   **Ações para prosseguir:** \- 
        
    -   **Exemplo de mensagem genérica: Transação não concluída.**  
        Esta operação não é permitida porque sua conta requer múltiplas aprovações. Entre em contato com seu banco para mais detalhes.
        

![image-20260622-203703.png](images/image-20260622-203703.png)

REC.PG-02700true

![image-20251125-221528.png](images/image-20251125-221528.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Casos de erro (Hybrid Flow)

**Proposta**

**Instituição**

ID

**Justificativa**

Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 637

**ID**

`REQ.PG-10201`

**Texto**

Ao identificar tentativa de iniciação de Pix Saque ou Pix Troco em conta que exija múltiplas aprovações, informar ao usuário que a operação não pode ser realizada nesse contexto.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Casos de erro (Hybrid Flow)

**Proposta**

**Instituição**

ITP

**Justificativa**

Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 637

**ID**

`REQ.PG-10702`

**Texto**

Ao receber o usuário da ID após erro decorrente de uma solicitação que exija múltiplas aprovações, informar que a transação não foi concluída.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Casos de erro (JSR)

**Proposta**

**Instituição**

ITP

**Justificativa**

Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 637

**ID**

`REQ.PG-10703`

**Texto**

Ao ser informada pela ID sobre a impossibilidade de iniciação de Pix Saque ou Pix Troco em conta que exija múltiplas aprovações, informar ao usuário que a operação não pode ser realizada nesse contexto.
