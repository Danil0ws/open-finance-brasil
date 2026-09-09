# v.23.00.00 Casos de erro de Pix

Esta página reúne os requisitos e recomendações aplicáveis ao tratamento e a **comunicação de erros na** **jornada de pagamento com Pix imediato com e sem redirecionamento** via Open Finance. 

* * *

Introdução - Mensagem de erro# Mensagem de erro

A mensagem de erro deve **comunicar** o erro **com clareza**, **explicar** o que ocasionou o erro com **linguagem simples** e **fornecer orientação** e **opções de ação** para que o usuário consiga continuar.

Boas práticas de experiência considerando os pilares:

-   O que houve?
    
-   O que ocasionou o erro?
    
-   Orientações ao usuário.
    
-   Ação necessária para prosseguir.
    

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

REQ.PG-09100#F4F5F7

## Requisitos - ITP

**Cenário: Erros na ITP**

-   `REQ.PG-09100` Informar ao usuário sobre erros na ITP e orientá-lo sobre como prosseguir.
    

![image-20260615-210814.png](images/image-20260615-210814.png)

* * *

# Etapa 1: Solicitação

REQ.PG-09200#F4F5F7

## Requisitos - ITP

**Cenário: Erros na solicitação**

-   `REQ.PG-09200` Informar ao usuário sobre a invalidade do QR Code e impedir a confirmação da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente com outro QR Code ou usar outra forma de pagamento. 
        
    -   **Exemplo de mensagem: QR Code inválido.** O QR Code informado é inválido ou não pôde ser lido corretamente.
        

![image-20260615-211003.png](images/image-20260615-211003.png)

* * *

# Etapa 2: Direcionamento

REQ.PG-09300#F4F5F7

## Requisitos - ITP

**Cenário: Erros no direcionamento ITP > ID**

-   `REQ.PG-09300` Informar ao usuário sobre a impossibilidade de redirecioná-lo para a ID.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde. 
        
    -   **Exemplo de mensagem:** Não foi possível te direcionar para a \[Detentora\] para confirmar a transação**.** Você pode tentar novamente.
        

![image-20260615-211322.png](images/image-20260615-211322.png)

* * *

# Etapa 3: Confirmação

REQ.PG-09400#F4F5F7

## Requisitos - ID

**Cenário: Erro genérico na ID**

-   `REQ.PG-09400` Informar ao usuário sobre erros na ID e orientá-lo sobre como prosseguir.
    

![image-20251120-183955.png](images/image-20251120-183955.png)REQ.PG-09500

**Cenário: Erros na autenticação/confirmação**

-   `REQ.PG-09500` Se houver falha de infraestrutura, informar ao usuário sobre a impossibilidade de concluir a autenticação ou confirmação.
    
    -   **Ações para prosseguir:** tentar novamente mais tarde.  
        
    -   **Exemplo de mensagem:  Tivemos um problema com sua autenticação.** Tente novamente mais tarde.
        

![image-20260615-211542.png](images/image-20260615-211542.png)

REQ.PG-09600

-   `REQ.PG-09600` Se os dados do usuário informados na ID forem diferentes dos dados informados na ITP, informar ao usuário sobre a impossibilidade de concluir a autenticação.
    
    -   **Ações para prosseguir:** tentar novamente com os dados corrigidos. / Alterar a conta de origem, se necessário.
        
    -   **Exemplo de mensagem:** Não foi possível prosseguir com a solicitação. Os dados informados não coincidem com os registrados na sua instituição. Verifique e tente novamente com as informações corretas. 
        

![image-20260615-211639.png](images/image-20260615-211639.png)REQ.PG-09700-   `REQ.PG-09700` Se a conta do usuário estiver indisponível, impedir que a conta seja selecionada para a solicitação. Ex.: desabilitar a seleção da conta.
    
    -   **Ações para prosseguir:** tentar novamente com outra conta de origem ou outra ID. 
        
    -   **Exemplo de mensagem:** Conta indisponível. (Ex.: tag) ![image-20260615-211748.png](images/image-20260615-211748.png)

REQ.PG-09800

-   `REQ.PG-09800` Informar ao usuário se a conta selecionada não possuir saldo nem limite de crédito pré-aprovado suficientes para a solicitação e impedir a confirmação da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente com outra conta ou outra ID. 
        
    -   **Exemplo de mensagem:** **Saldo insuficiente!** Não foi possívei concluir o pagamento via Pix, pois a conta selecionada não possui saldo suficiente. Tente escolher outra conta ou transfira recursos para esta conta antes de continuar.
        

![image-20260615-211917.png](images/image-20260615-211917.png)REQ.PG-09900

-   `REQ.PG-09900` Informar ao usuário se o valor da solicitação ultrapassar o limite transacional disponível da conta selecionada e impedir a confirmação da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente com outra conta de origem ou outra Detentora. / Ajustar o valor e tentar novamente. 
        
    -   **Exemplo de mensagem:** **Limite excedido.** Ajuste o valor da transação e tente novamente.
        

![image-20260615-212038.png](images/image-20260615-212038.png)REQ.PG-10000

-   `REQ.PG-10000` Informar ao usuário se o valor exibido na ID for diferente do valor informado na ITP e impedir a confirmação da solicitação.
    
    -   **Ações para prosseguir:** iniciar nova solicitação. 
        
    -   **Exemplo de mensagem: Valor divergente.** Não podemos prosseguir com a solicitação pois o valor informado na \[Iniciadora\] está divergente. Tente novamente.
        

![image-20260615-212145.png](images/image-20260615-212145.png)

REQ.PG-10100

-   `REQ.PG-10100` Informar ao usuário se o prazo para confirmação da solicitação expirar.
    
    -   **Ações para prosseguir:** iniciar nova solicitação. 
        
    -   **Exemplo de mensagem: Sessão expirada.** A solicitação não foi realizada pois o tempo expirou. Tente novamente. 
        

![image-20260616-140642.png](images/image-20260616-140642.png)

REQ.PG-10200

-   `REQ.PG-10200` Informar ao usuário se ele não possuir poderes de representação (PJ) suficientes para confirmar a solicitação e impedir a confirmação da solicitação.
    
    -   **Ações para prosseguir:** contatar a ID. / Contatar o titular principal da conta. 
        
    -   **Exemplo de mensagem: Você não tem autorização para concluir essa ação.** Entre em contato conosco ou com o titular principal da conta para mais informações.
        

![image-20260616-140752.png](images/image-20260616-140752.png)

REQ.PG-10300

-   `REQ.PG-10300` Informar ao usuário se as contas de origem e destino forem iguais e impedir a confirmação da solicitação.
    
    -   **Ações para prosseguir:** tentar novamente com outra conta. 
        
    -   **Exemplo de mensagem: Não foi possível confirmar sua transação**  
        A conta de débito do pagamento não pode ser a mesma que a conta destino. Escolha outra conta para prosseguir.
        

![image-20260616-141015.png](images/image-20260616-141015.png)REQ.PG-10400

**Cenário: Tratativa de erro pós-cancelamento por parte do usuário** 

-   `REQ.PG-10400` Redirecionar o usuário para a ITP se ele cancelar a solicitação mesmo após a identificação de um erro (ex.: conta indisponível).
    
    -   **Ações para prosseguir:** \-
        
    -   **Exemplo de mensagem:** \-
        

![image-20260616-141346.png](images/image-20260616-141346.png)

REQ.PG-10500

**Cenário: Erros na tentativa de confirmação**

-   `REQ.PG-10500` Informar ao usuário que a solicitação não foi concluída devido à expiração do prazo para confirmação da ITP.
    
    -   **Ações para prosseguir:** iniciar nova solicitação. 
        
    -   **Exemplo de mensagem: Falha na solicitação.** Sua solicitação falhou devido a problemas internos na \[Iniciadora\]. Tente novamente.
        

![image-20260616-142011.png](images/image-20260616-142011.png)

* * *

# Etapa 4: Redirecionamento

REQ.PG-10600#F4F5F7

## Requisitos - ID

**Cenário: Erros no redirecionamento ID > ITP**

-   `REQ.PG-10600` Redirecionar o usuário para a ITP se houver erro na confirmação da solicitação decorrente de indisponibilidade da conta, saldo insuficiente, falha de infraestrutura ou outros impedimentos.
    
    -   **Ações para prosseguir:** \-
        
    -   **Exemplo de mensagem:** \-
        

![image-20260323-165706.png](images/image-20260323-165706.png)

* * *

# Etapa 5: Efetivação

REQ.PG-10700#F4F5F7

## Requisitos - ITP

**Cenário: Erros na efetivação**

-   `REQ.PG-10700` Informar ao usuário sobre a indisponibilidade do sistema e sobre a possibilidade de a solicitação ter sido processada (no backend), mesmo sem confirmação do resultado.
    
    -   **Ações para prosseguir:** verificar se a solicitação foi efetivada na ID./Tentar novamente mais tarde caso a solicitação não tenha sido efetivada. 
        
    -   **Exemplo de mensagem: Sistema indisponível.** Verifique na sua instituição se a solicitação foi concluída. Caso não tenha sido, tente novamente mais tarde.
        

![image-20260616-142127.png](images/image-20260616-142127.png)REC.PG-02600#F4F5F7

## Recomendações - ITP

**Cenário: Otimização da solicitação em caso de erro** 

-   `REC.PG-02600` Ao receber o usuário de volta após a identificação do erro, otimizar a nova solicitação, mantendo os dados corretos já preenchidos e indicando a alteração apenas da informação que causou o erro.
    

![image-20260616-142234.png](images/image-20260616-142234.png)

* * *

# Casos de erro de Pix Sem Redirecionamento (JSR)

Esta seção descreve os requisitos e recomendações para tratar erros que ocorrem somente nas jornada de Pix imediato Sem Redirecionamento (JSR)

# Etapa 3: Efetivação

REC.PG-02700#F4F5F7

## Recomendações - ITP

**Cenário: Erros na liquidação do pagamento** 

-   `REC.PG-02700` Informar ao usuário se o valor do pagamento realizado por meio de um vínculo de conta ultrapassar o limite definido para o vínculo e impedir a confirmação do pagamento.
    
    -   **Ações para prosseguir:** ajustar o valor do pagamento e tentar novamente. / Tentar novamente com outro vínculo de conta que possua limite disponível. 
        
    -   **Exemplo de mensagem: Limite do vínculo excedido.** O valor da transação excede o limite diário/por transação definido para este vínculo de conta. Altere o valor da transação ou use outra conta para concluir o pagamento. ![image-20260616-142418.png](images/image-20260616-142418.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR)

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-09100`

**Texto**

Informar ao usuário sobre erros na ITP e orientá-lo sobre como prosseguir.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR)

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-09200`

**Texto**

Informar ao usuário sobre a invalidade do QR Code e impedir a confirmação da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off)

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-09300`

**Texto**

Informar ao usuário sobre a impossibilidade de redirecioná-lo para a ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-09400`

**Texto**

Informar ao usuário sobre erros na ID e orientá-lo sobre como prosseguir.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-09500`

**Texto**

Se houver falha de infraestrutura, informar ao usuário sobre a impossibilidade de concluir a autenticação ou confirmação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-09600`

**Texto**

Se os dados do usuário informados na ID forem diferentes dos dados informados na ITP, informar ao usuário sobre a impossibilidade de concluir a autenticação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-09700`

**Texto**

Se a conta do usuário estiver indisponível, impedir que a conta seja selecionada para a solicitação. Ex.: desabilitar a seleção da conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-09800`

**Texto**

Informar ao usuário se a conta selecionada não possuir saldo nem limite de crédito pré-aprovado suficientes para a solicitação e impedir a confirmação da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-09900`

**Texto**

Informar ao usuário se o valor da solicitação ultrapassar o limite transacional disponível da conta selecionada e impedir a confirmação da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-10000`

**Texto**

Informar ao usuário se o prazo para confirmação da solicitação expirar.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-10100`

**Texto**

Quando o prazo para confirmação da solicitação expirar, informar essa condição ao usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-10200`

**Texto**

Informar ao usuário se ele não possuir poderes de representação (PJ) suficientes para confirmar a solicitação e impedir a confirmação da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix Agendado, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-10300`

**Texto**

Informar ao usuário se as contas de origem e destino forem iguais e impedir a confirmação da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-10400`

**Texto**

Redirecionar o usuário para a ITP se ele cancelar a solicitação mesmo após a identificação de um erro (ex.: conta indisponível).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-10500`

**Texto**

Informar ao usuário que a solicitação não foi concluída devido à expiração do prazo para confirmação da ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA)

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-10600`

**Texto**

Redirecionar o usuário para a ITP se houver erro na confirmação da solicitação decorrente de indisponibilidade da conta, saldo insuficiente, falha de infraestrutura ou outros impedimentos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix Agendado, Transferências Inteligentes

**Jornada**

Casos de erro (Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR)

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-10700`

**Texto**

Informar ao usuário sobre a indisponibilidade do sistema e sobre a possibilidade de a solicitação ter sido processada (no backend), mesmo sem confirmação do resultado.
