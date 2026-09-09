# v.23.00.00 Casos de erro na Jornada Otimizada em Transferências Inteligentes

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a comunicação de erros na **Jornada Otimizada em Transferências Inteligentes** via Open Finance. 

* * *

# Introdução - Mensagem de errotrue

* * *

# Etapa 5: Efetivação

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-10704-   `REQ.PG-10704` Informar ao usuário se a solicitação de Transferências Inteligentes for efetivada e o compartilhamento de saldo e limite via Jornada Otimizada falhar.
    
    -   **Ações para prosseguir:** orientar o usuário conforme estratégia da instituição. 
        
    -   **Exemplo de mensagem: Falha no compartilhamento de saldo e limite.** A autorização de Transferências Inteligentes foi criada, mas o compartilhamento de saldo e limite falhou**.** ![image-20251125-221213.png](images/image-20251125-221213.png)

# Gestão na ITP

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-11003

**Cenário: Erros na gestão do compartilhamento de saldo e limite via Jornada Otimizada**

-   `REQ.PG-11003` Informar ao usuário sobre falha no cancelamento do compartilhamento de saldo e limite.
    
-   **Ações para prosseguir:** tentar novamente. 
    
-   **Exemplo de mensagem: Falha no cancelamento.** Tivemos um problema com o cancelamento do compartilhamento de saldo e limite. Tente novamente.
    

![image-20260624-143204.png](images/image-20260624-143204.png)

# Gestão na ID

wide760#F4F5F7

## Requisitos - ID

REQ.PG-11003true

![image-20260624-143134.png](images/image-20260624-143134.png)

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Transferências Inteligentes

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP

**Justificativa**

Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-10704`

**Texto**

Informar ao usuário se a solicitação de Transferências Inteligentes for efetivada e o compartilhamento de saldo e limite via Jornada Otimizada falhar.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Jornada Otimizada em Transferências Inteligentes

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-11003`

**Texto**

Informar ao usuário sobre falha no cancelamento do compartilhamento de saldo e limite.
