# v.23.00.00 Casos de erro de Pix Automático

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a comunicação de erros na **jornada de pagamento com Pix Automático com e sem redirecionamento** via Open Finance. 

* * *

Introdução - Mensagem de errotrue

* * *

# Geral

REQ.PG-09100true

![image-20251120-185401.png](images/image-20251120-185401.png)

* * *

# Etapa 1: Solicitação

REQ.PG-09200true

![image-20251120-185748.png](images/image-20251120-185748.png)REQ.PG-09203

-   `REQ.PG-09203` Se o usuário tentar fazer a leitura de um QR Code de Pix Automático em uma ITP que também não seja uma ID, informá-lo que o tipo de QR Code informado não pode ser lido na ITP.
    
    -   **Ações para prosseguir:** utilizar os canais disponíveis para pagamento com Pix Automático acessando a opção diretamente na Detentora.   
        
    -   **Exemplo de mensagem: Esse tipo de QR Code não pode ser lido neste canal.** Faça a leitura do QR Code na sua instituição bancária para realizar o pagamento.
        

![image-20251124-182440.png](images/image-20251124-182440.png)

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

![image-20251120-183955.png](images/image-20251120-183955.png)

REQ.PG-09700true

![image-20251120-193343.png](images/image-20251120-193343.png)

REQ.PG-09900true

![image-20251121-191400.png](images/image-20251121-191400.png)

REQ.PG-10000true

![image-20251121-191632.png](images/image-20251121-191632.png)

REQ.PG-10100true

![image-20251121-141915.png](images/image-20251121-141915.png)

REQ.PG-10200true

![image-20251121-144823.png](images/image-20251121-144823.png)

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

![image-20251120-185316.png](images/image-20251120-185316.png)REQ.PG-10701

-   `REQ.PG-10701` Informar ao usuário sobre a falha do pagamento inicial avulso e a necessidade de contatar o recebedor ou ITP para regularizar a situação, sobre a manutenção da autorização de Pix Automático e sobre a possibilidade, a critério do recebedor, de cancelamento posterior da autorização.
    
    -   **Ações para prosseguir:** contatar o recebedor ou ITP para regularizar o pagamento pendente.  
        
    -   **Exemplo de mensagem: Saldo insuficiente!** Não foi possível concluir o pagamento de adesão com Pix, por falta de saldo na sua conta. A autorização de Pix Automático para \[Empresa X\] foi criada e poderá, a critério do recebedor, ser encerrada posteriormente. Entre em contato com o recebedor para regularizar o pagamento de adesão.
        

![image-20251120-194355.png](images/image-20251120-194355.png)

REC.PG-02600true

* * *

# Gestão na ITP

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-10900true

![image-20251121-192636.png](images/image-20251121-192636.png)

REQ.PG-11000true

![image-20251126-201508.png](images/image-20251126-201508.png)REQ.PG-11001-   `REQ.PG-11001` Informar ao usuário se houver erro na alteração de algum parâmetro da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde. 
        
    -   **Exemplo de mensagem: Falha na alteração.** Não foi possível realizar essa alteração. Tente novamente mais tarde. 

![image-20251126-201853.png](images/image-20251126-201853.png)

* * *

# Gestão na ID

wide760#F4F5F7

## Requisitos - ID

REQ.PG-11000true

![image-20260625-132528.png](images/image-20260625-132528.png)

REQ.PG-11001true

![image-20260625-132619.png](images/image-20260625-132619.png)

REQ.PG-11002

**Cenário: Erros na liquidação do pagamento**

-   `REQ.PG-11002` Se após a última tentativa de liquidação, um pagamento da recorrência falhar, informar ao usuário sobre a falha sem oferecer outros meios de pagamento.
    
    -   **Ações para prosseguir:** contatar o recebedor ou ITP para regularizar a situação. 
        
    -   **Exemplo de mensagem: Pagamento não realizado.** Não foi possível realizar o pagamento com Pix Automático para **Telefonia S/A** por falha de comunicação. Contate o recebedor para regularizar. 
        

![image-20251120-194639.png](images/image-20251120-194639.png)

* * *

# Casos de erro de Pix Automático Sem Redirecionamento (JSR)

Esta seção descreve os requisitos e recomendações para tratar erros que ocorrem somente na jornada de Pix Automático Sem Redirecionamento (JSR)

# Etapa 3: Efetivação

REC.PG-02700true

![image-20251125-221528.png](images/image-20251125-221528.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-09203`

**Texto**

Se o usuário tentar fazer a leitura de um QR Code de Pix Automático em uma ITP que também não seja uma ID, informá-lo que o tipo de QR Code informado não pode ser lido na ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-10701`

**Texto**

Informar ao usuário sobre a falha do pagamento inicial avulso e a necessidade de contatar o recebedor ou ITP para regularizar a situação, sobre a manutenção da autorização de Pix Automático e sobre a possibilidade, a critério do recebedor, de cancelamento posterior da autorização.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-11001`

**Texto**

Informar ao usuário se houver erro na alteração de algum parâmetro da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-11002`

**Texto**

Se após a última tentativa de liquidação, um pagamento da recorrência falhar, informar ao usuário sobre a falha sem oferecer outros meios de pagamento.
