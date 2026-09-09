# v.23.00.00 Casos de erro da Jornada Otimizada na Vinculação de Conta

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a comunicação de erros na **jornada de Vinculação de Conta para pagamentos sem redirecionamento (JSR)** via Open Finance. 

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
**Falha no cancelamento.** Não foi possível cancelar a autorização de pagamento. Tente novamente mais tarde.

-   **O que houve?**
    
    -   A solicitação não pôde ser cancelada.
        
-   **O que ocasionou o erro?**
    
    -   Uma indisponibilidade do sistema.
        
-   **Orientações ao usuário**
    
    -   Tentar novamente mais tarde.
        
-   **Ações para prosseguir**
    
    -   Tentar novamente.
        
-   **Mensagem de erro**
    
    -   **Falha no cancelamento.** Não foi possível cancelar o vínculo de conta. Tente novamente mais tarde.
        

Sempre que possível, identificar se o problema ocorreu na Instituição Iniciadora de Transação de Pagamento (ITP) ou na Instituição Detentora de Conta (ID), além do tipo de erro.  
Quando o erro acontecer em ambiente da ID, esta deverá redirecionar o usuário ao ambiente da ITP junto com o código do erro específico, conforme as possibilidades descritas no **Diagrama de Sequência — Momento 3 - Etapa de Autorização do Cliente**, disponível no Portal do Desenvolvedor, onde deverá ocorrer a tratativa.  
A tratativa na ITP deverá ser o mais específica possível a fim de evitar erros genéricos.  
Os casos de erros devem ser tratados conforme previsto nos regulamentos dos arranjos.

Os requisitos estão organizados por **cenário,** **ações necessárias** **para resolver o erro** e **exemplos de mensagem para comunicar o erro** de forma clara. 

Para casos que não estejam cobertos nesta página, as instituições devem garantir que, diante de qualquer erro, o usuário seja sempre informado com clareza, sobre o que ocorreu e o que pode fazer a seguir. 

# Etapa 5: Efetivação

REQ.VC-10600#F4F5F7

## Requisitos - ITP

-   `REQ.VC-10600` Informar ao usuário se a solicitação de Vinculação de Conta for efetivada e o compartilhamento de saldo e limite via Jornada Otimizada falhar.
    
    -   **Ações para prosseguir:** orientar o usuário conforme estratégia da instituição. 
        
    -   **Exemplo de mensagem: Falha no compartilhamento de saldo e limite.** O vínculo de conta com a \[Instituição\] foi criado, mas o compartilhamento de saldo e limite falhou**.**  ![image-20260615-171038.png](images/image-20260615-171038.png)

# Gestão na ITP

wide760#F4F5F7

## Requisitos - ITP

REQ.VC-10800

**Cenário: Erros na gestão - Jornada Otimizada**

-   `REQ.VC-10800` Informar ao usuário sobre falha no cancelamento do compartilhamento de saldo e limite.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde. 
        
    -   **Exemplo de mensagem:** Tivemos um problema com o cancelamento do compartilhamento de saldo e limite. Tente novamente.
        

![image-20260615-173724.png](images/image-20260615-173724.png)

* * *

# Gestão na ID

wide760#F4F5F7

## Requisitos - ID

REQ.VC-10800true

![image-20260624-172348.png](images/image-20260624-172348.png)true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-10600`

**Texto**

Informar ao usuário se a solicitação de Vinculação de Conta for efetivada e o compartilhamento de saldo e limite via Jornada Otimizada falhar.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

**ID**

`REQ.VC-10800`

**Texto**

Informar ao usuário sobre falha no cancelamento do compartilhamento de saldo e limite.
