# v.23.00.00 Casos de erro de Pix Agendado

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a comunicação de erros na **jornada de pagamento com Pix Agendado com e sem redirecionamento** via Open Finance. 

* * *

# Mensagem de erro

**A mensagem de erro deve comunicar** o erro **com clareza**, **explicar** o que ocasionou o erro com **linguagem simples** e **fornecer orientação** e **opções de ação** para que o usuário consiga continuar.

Boas práticas de experiência considerando ospilares:

-   O que houve?
    
-   O que ocasionou o erro?
    
-   Orientações ao usuário.
    
-   Ação necessária para prosseguir.  
    

wide760

**Exemplo de erro:**  
**QR Code inválido.** O QR Code informado é inválido ou não pôde ser lido corretamente.

-   **O que houve?**
    
    -   A solicitação de pagamento não pode ser iniciada.  
        
-   **O que ocasionou o erro?**
    
    -   O QR Code informado é inválido.  
        
-   **Orientações ao usuário**
    
    -   Tentar novamente com outro QR Code ou usar outra forma de pagamento.   
        
-   **Ações para prosseguir**
    
    -   Tentar novamente.  
        
-   **Mensagem de erro**
    
    -   **QR Code inválido.** O QR Code informado é inválido ou não pôde ser lido corretamente.
        

  
Sempre que possível, identificar se o problema ocorreu na Instituição Iniciadora de Transação de Pagamento (ITP) ou na Instituição Detentora de Conta (ID), além do tipo de erro.  
Quando o erro acontecer em ambiente da ID, esta deverá redirecionar o usuário ao ambiente da ITP junto com o código do erro específico, conforme as possibilidades descritas no **Diagrama de Sequência — Momento 3 - Etapa de Autorização do Cliente**, disponível no Portal do Desenvolvedor, onde deverá ocorrer a tratativa.  
A tratativa na ITP deverá ser o mais específica possível a fim de evitar erros genéricos.  
Os casos de erros devem ser tratados conforme previsto nos regulamentos dos arranjos.

Os requisitos estão organizados por **cenário,** **ações necessárias** **para resolver o erro** e **exemplos de mensagem para comunicar o erro** de forma clara. 

Para casos que não estejam cobertos nesta página, as instituições devem garantir que, diante de qualquer erro, o usuário seja sempre informado com clareza, sobre o que ocorreu e o que pode fazer a seguir. 

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

![07c27401-3170-4d65-8669-cfd5519af92b.png](images/07c27401-3170-4d65-8669-cfd5519af92b.png)

REQ.PG-09800true

![image-20251120-193343.png](images/image-20251120-193343.png)![image-20260416-130054.png](images/image-20260416-130054.png)

REQ.PG-09900true

![image-20251121-191400.png](images/image-20251121-191400.png)

REQ.PG-10000true

![image-20251121-191632.png](images/image-20251121-191632.png)

REQ.PG-10100true

![image-20251121-141915.png](images/image-20251121-141915.png)

REQ.PG-10200true

![image-20251121-144823.png](images/image-20251121-144823.png)

REQ.PG-10300true

![image-20251124-171202.png](images/image-20251124-171202.png)

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

![image-20251120-185316.png](images/image-20251120-185316.png)

REC.PG-02600true

![image-20251125-215521.png](images/image-20251125-215521.png)

* * *

# Gestão na ITP

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-10900

**Cenário: Erros na gestão**

-   `REQ.PG-10900` Se o usuário tentar cancelar uma solicitação que já está cancelada ou liquidada na ID, informar o usuário sobre a impossibilidade de cancelar a solicitação e o motivo.
    
    -   **Ações para prosseguir:** verificar na ID o estado atual do pagamento. 
        
    -   **Exemplo de mensagem: Cancelamento não permitido.** Este pagamento já foi processado/cancelado. Verifique o status na sua instituição para confirmar a situação da transação.
        

![image-20251121-192636.png](images/image-20251121-192636.png)REQ.PG-11000

-   `REQ.PG-11000` Informar ao usuário se houver erro no cancelamento da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde. 
        
    -   **Exemplo de mensagem:  Falha no cancelamento.** Não foi possível cancelar \[a solicitação\]. Tente novamente mais tarde.
        

![image-20251126-201508.png](images/image-20251126-201508.png)

* * *

# Gestão na ID

wide760#F4F5F7

## Requisitos - ID

**Cenário: Erros na gestão**

REQ.PG-11000true

![image-20251126-201508.png](images/image-20251126-201508.png)

* * *

# Casos de erro de Pix Agendado Sem Redirecionamento (JSR)

Esta seção descreve os requisitos e recomendações para tratar erros que ocorrem somente na jornada de Pix Agendado Sem Redirecionamento (JSR)

# Etapa 3: Efetivação

REC.PG-02700true

![image-20251125-221528.png](images/image-20251125-221528.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Segurança e privacidade, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-10900`

**Texto**

Se o usuário tentar cancelar uma solicitação que já está cancelada ou liquidada na ID, informar o usuário sobre a impossibilidade de cancelar a solicitação e o motivo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Segurança e privacidade, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-11000`

**Texto**

Informar ao usuário se houver erro no cancelamento da solicitação.
