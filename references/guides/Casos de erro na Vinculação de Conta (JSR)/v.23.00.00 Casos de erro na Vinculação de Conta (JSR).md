# v.23.00.00 Casos de erro na Vinculação de Conta (JSR)

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a comunicação de erros na **jornada de Vinculação de Conta para pagamentos sem redirecionamento (JSR)** via Open Finance. 

* * *

# Mensagem de erro

**A mensagem de erro deve comunicar** o erro **com clareza**, **explicar** o que ocasionou o erro com **linguagem simples** e **fornecer orientação** e **opções de ação** para que o usuário consiga continuar.

Boas práticas de experiência considerando os pilares:

-   O que houve?
    
-   O que ocasionou o erro?
    
-   Orientações ao usuário.
    
-   Ação necessária para prosseguir.  
    

wide760

**Exemplo de erro:**  
**Falha no cancelamento.** Não foi possível cancelar o vínculo de conta. Tente novamente mais tarde.

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

* * *

# Geral

REQ.VC-09500#F4F5F7

## Requisitos - ITP

**Cenário: Erro genérico na ITP**

-   `REQ.VC-09500` Informar ao usuário sobre erros na ITP e orientá-lo sobre como prosseguir.
    

![image-20260615-150318.png](images/image-20260615-150318.png)

* * *

# Etapa 2: Direcionamento

REQ.VC-09600#F4F5F7

## Requisitos - ITP

-   `REQ.VC-09600` Informar ao usuário sobre a impossibilidade de redirecioná-lo para a ID.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde. 
        
    -   **Exemplo de mensagem:** não foi possível te direcionar para a \[Detentora\] para confirmar a transação**.** Tente novamente mais tarde. ![image-20260615-150634.png](images/image-20260615-150634.png)

* * *

# Etapa 3: Confirmação

REQ.VC-09700#F4F5F7

## Requisitos - ID

**Cenário: Erro genérico na ID**

-   `REQ.VC-09700` Informar ao usuário sobre erros na ID e orientá-lo sobre como prosseguir.
    

![image-20260615-170210.png](images/image-20260615-170210.png)

REQ.VC-09800

**Cenário: Erros na autenticação/confirmação**

-   `REQ.VC-09800` Se houver falha de infraestrutura, informar ao usuário sobre a impossibilidade de concluir a autenticação ou confirmação.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde.  
        
    -   **Exemplo de mensagem:  Tivemos um problema com sua autenticação.** Tente novamente mais tarde.
        

![image-20260729-200017.png](images/image-20260729-200017.png)

REQ.VC-09900

-   `REQ.PG-09900` Se os dados do usuário informados na ID forem diferentes dos dados informados na ITP, informar ao usuário sobre a impossibilidade de concluir a autenticação.
    
    -   **Ações para prosseguir:** tentar novamente com os dados corrigidos. / Alterar a conta de origem, se necessário.
        
    -   **Exemplo de mensagem:** Não foi possível prosseguir com a solicitação. Os dados informados não coincidem com os registrados na sua instituição. Verifique e tente novamente com as informações corretas. 
        

![image-20260615-151034.png](images/image-20260615-151034.png)

  
 

REQ.VC-10000-   `REQ.VC-10000` Se a conta do usuário estiver indisponível, impedir que a conta seja selecionada para a solicitação. Ex.: desabilitar a seleção da conta.
    
    -   **Ações para prosseguir:** tentar novamente com outra conta de origem ou outra ID. 
        
    -   **Exemplo de mensagem:** Conta indisponível. (Ex.: tag) ![image-20260615-151539.png](images/image-20260615-151539.png)

REQ.VC-10100

-   `REQ.VC-10100` Informar ao usuário se o prazo para confirmação da solicitação expirar.
    
    -   **Ações para prosseguir:** iniciar nova solicitação. 
        
    -   **Exemplo de mensagem: Sessão expirada.** A solicitação não foi realizada pois o tempo expirou. Tente novamente. 
        

![image-20260615-151631.png](images/image-20260615-151631.png)

REQ.VC-10200

**Cenário: Tratativa de erro pós-cancelamento por parte do usuário** 

-   `REQ.VC-10200` Redirecionar o usuário para a ITP se ele cancelar a solicitação mesmo após a identificação de um erro (ex.: conta indisponível).
    
    -   **Ações para prosseguir:** \-
        
    -   **Exemplo de mensagem:** \-
        

![image-20260624-175141.png](images/image-20260624-175141.png)

REQ.VC-10300

**Cenário: Erros na tentativa de confirmação**

-   `REQ.VC-10300` Informar ao usuário que a solicitação não foi concluída devido à expiração do prazo para confirmação da ITP.
    
    -   **Ações para prosseguir:** iniciar nova solicitação. 
        
    -   **Exemplo de mensagem: Falha na solicitação.** Sua solicitação falhou devido a problemas internos na \[Iniciadora\]. Tente novamente.
        

![image-20260615-170317.png](images/image-20260615-170317.png)

* * *

# Etapa 4: Redirecionamento

REQ.VC-10400#F4F5F7

## Requisitos - ID

**Cenário: Erros no redirecionamento ID > ITP**

-   `REQ.VC-10400` Redirecionar o usuário para a ITP se houver erro na confirmação da solicitação decorrente de indisponibilidade da conta, saldo insuficiente, falha de infraestrutura ou outros impedimentos.
    
    -   **Ações para prosseguir:** \-
        
    -   **Exemplo de mensagem:** \-
        

![image-20260323-165706.png](images/image-20260323-165706.png)

* * *

# Etapa 5: Efetivação

REQ.VC-10500#F4F5F7

## Requisitos - ITP

**Cenário: Erros na efetivação**

-   `REQ.VC-10500` Informar ao usuário sobre a indisponibilidade do sistema e sobre a possibilidade de a solicitação ter sido processada (no backend), mesmo sem confirmação do resultado.
    
    -   **Ações para prosseguir:** Verificar se a solicitação foi efetivada na ID./Tentar novamente mais tarde caso a solicitação não tenha sido efetivada. 
        
    -   **Exemplo de mensagem: Sistema indisponível.** Verifique na sua instituição se a solicitação foi concluída. Caso não tenha sido, tente novamente mais tarde.
        

![image-20260615-170858.png](images/image-20260615-170858.png)

REC.VC-02700#F4F5F7

## Recomendações - ITP

**Cenário: Otimização da solicitação em caso de erro** 

-   `REC.VC-02700` Ao receber o usuário de volta após a identificação do erro, otimizar a nova solicitação, mantendo os dados corretos já preenchidos e indicando a alteração apenas da informação que causou o erro.
    

![image-20260624-175338.png](images/image-20260624-175338.png)

* * *

# Gestão na ITP

wide760#F4F5F7

## Requisitos - ITP

REQ.VC-10700

**Cenário: Erros na gestão**

-   `REQ.VC-10700` Informar ao usuário se houver erro no cancelamento da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde. 
        
    -   **Exemplo de mensagem:  Falha no cancelamento.** Não foi possível cancelar o vínculo de conta. Tente novamente mais tarde.
        

![image-20260615-173528.png](images/image-20260615-173528.png)

* * *

# Gestão na ID

wide760#F4F5F7

## Requisitos - ID

REQ.VC-10700true

![image-20260615-173352.png](images/image-20260615-173352.png)

REQ.VC-10900

-   `REQ.VC-10900` Informar ao usuário se houver erro na alteração de algum parâmetro da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente. 
        
    -   **Exemplo de mensagem: Atenção!** O valor máximo por transação não pode ser maior que o valor máximo por dia.
        

![image-20260624-175520.png](images/image-20260624-175520.png)true

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

`REQ.VC-09500`

**Texto**

Informar ao usuário sobre erros na ITP e orientá-lo sobre como prosseguir.

true

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

`REQ.VC-09600`

**Texto**

Informar ao usuário sobre a impossibilidade de redirecioná-lo para a ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-09700`

**Texto**

Para erros genéricos na ID, comunicar o erro com clareza, orientando o usuário sobre como prosseguir.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-09800`

**Texto**

Se houver falha de infraestrutura, informar ao usuário sobre a impossibilidade de concluir a autenticação ou confirmação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-09900`

**Texto**

Se os dados do usuário informados na ID forem diferentes dos dados informados na ITP, informar ao usuário sobre a impossibilidade de concluir a autenticação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-10000`

**Texto**

Se a conta do usuário estiver indisponível, impedir que a conta seja selecionada para a solicitação. Ex.: desabilitar a seleção da conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-10100`

**Texto**

Informar ao usuário se o prazo para confirmação da solicitação expirar.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-10200`

**Texto**

Redirecionar o usuário para a ITP se ele cancelar a solicitação mesmo após a identificação de um erro (ex.: conta indisponível).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-10300`

**Texto**

Informar ao usuário que a solicitação não foi concluída devido à expiração do prazo para confirmação da ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-10400`

**Texto**

Redirecionar o usuário para a ITP se houver erro na confirmação da solicitação decorrente de indisponibilidade da conta, saldo insuficiente, falha de infraestrutura ou outros impedimentos.

true

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

`REQ.VC-10500`

**Texto**

Informar ao usuário sobre a indisponibilidade do sistema e sobre a possibilidade de a solicitação ter sido processada (no backend), mesmo sem confirmação do resultado.

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

`REQ.VC-10700`

**Texto**

Informar ao usuário se houver erro no cancelamento da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Casos de erro

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-10900`

**Texto**

Informar ao usuário se houver erro na alteração de algum parâmetro da solicitação.
