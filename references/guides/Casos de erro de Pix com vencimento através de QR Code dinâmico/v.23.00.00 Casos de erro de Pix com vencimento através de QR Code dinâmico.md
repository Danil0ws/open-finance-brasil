# v.23.00.00 Casos de erro de Pix com vencimento através de QR Code dinâmico

Esta seção reúne os requisitos e recomendações aplicáveis ao tratamento e a comunicação de erros na **jornada de pagamento com Pix com vencimento através de QR Code dinâmico com e sem redirecionamento** via Open Finance. 

* * *

Introdução - Mensagem de errotrue

* * *

# Geral

REQ.PG-09100true

![image-20260618-181703.png](images/image-20260618-181703.png)

* * *

# Etapa 1: Solicitação

REQ.PG-09200true

![image-20260618-181727.png](images/image-20260618-181727.png)

REQ.PG-09201

-   `REQ.PG-09201` Caso o QR Code não aceite pagamento após o vencimento, informar o usuário sobre o motivo da não conclusão do pagamento.
    
    -   **Ações para prosseguir:** contatar o recebedor para mais informações.   
        
    -   **Exemplo de mensagem:** Esse QR Code não aceita pagamento após o vencimento. Contate o recebedor para mais informações.
        

![image-20260618-182227.png](images/image-20260618-182227.png)

REQ.PG-09202

-   `REQ.PG-09202` Em caso de erro na leitura de QR Code com chave vinculada a uma conta ou usuário com restrição para recebimento de transação Pix por envolvimento em fraude, informar o usuário que a conta de destino ou o usuário recebedor esteve envolvido em transação com fundada suspeita de fraude e que não é possível concluir a transação.
    
    -   **Ações para prosseguir:** \-  
        
    -   **Exemplo de mensagem: Pix não realizado.** Conta de destino envolvida em transação com suspeita de fraude.
        

![image-20260619-204323.png](images/image-20260619-204323.png)

* * *

# Etapa 2: Direcionamento

REQ.PG-09300true

![image-20260618-182630.png](images/image-20260618-182630.png)

* * *

# Etapa 3: Confirmação

REQ.PG-09400true

![image-20260618-183152.png](images/image-20260618-183152.png)

REQ.PG-09500true

![image-20260618-183238.png](images/image-20260618-183238.png)

REQ.PG-09600true

![image-20260618-183323.png](images/image-20260618-183323.png)

REQ.PG-09700true

![image-20260618-183457.png](images/image-20260618-183457.png)

REQ.PG-09800true

![image-20260618-183822.png](images/image-20260618-183822.png)

REQ.PG-09900true

![image-20260618-183857.png](images/image-20260618-183857.png)

REQ.PG-10000true

![image-20260618-184052.png](images/image-20260618-184052.png)

REQ.PG-10100true

![image-20260618-184117.png](images/image-20260618-184117.png)

REQ.PG-10200true

![image-20260618-184147.png](images/image-20260618-184147.png)

REQ.PG-10400true

![image-20260618-184408.png](images/image-20260618-184408.png)

  

REQ.PG-10500true

![image-20260618-184441.png](images/image-20260618-184441.png)

* * *

# Etapa 4: Redirecionamento

REQ.PG-10600true

![image-20260323-165706.png](images/image-20260323-165706.png)

* * *

# Etapa 5: Efetivação

REQ.PG-10700true

![image-20260618-184534.png](images/image-20260618-184534.png)

REC.PG-02600true

* * *

# Casos de erro de Pix com vencimento através de QR Code dinâmico Sem Redirecionamento (JSR)

Esta seção descreve os requisitos e recomendações para tratar erros que ocorrem somente nas jornada de Pix com vencimento através de QR Code dinâmico Sem Redirecionamento (JSR)

# Etapa 3: Efetivação

REC.PG-02700true

![image-20260618-184607.png](images/image-20260618-184607.png)

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

`REQ.PG-09201`

**Texto**

Caso o QR Code não aceite pagamento após o vencimento, informar o usuário sobre o motivo da não conclusão do pagamento.

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

`REQ.PG-09202`

**Texto**

Em caso de erro na leitura de QR Code com chave vinculada a uma conta ou usuário com restrição para recebimento de transação Pix por envolvimento em fraude, informar o usuário que a conta de destino ou o usuário recebedor esteve envolvido em transação com fundada suspeita de fraude e que não é possível concluir a transação.
