# v.23.00.00 Gestão de Pix Automático

Esta página reúne os requisitos e recomendações para gestão de **autorizações e transações de pagamentos com Pix Automático com ou sem redirecionamento (JSR)**, via Open Finance.

Nota.Regulamentação e Arranjotrue

* * *

# Gestão na ITP

Esta seção reúne os requisitos e recomendações para gestão de Pix Automático na Instituição Iniciadora de Transação de Pagamento (ITP).

* * *

## Gestão das autorizações na ITP

![image-20260625-132634.png](images/image-20260625-132634.png)wide760#F4F5F7

## Requisitos - ITP

![image-20260624-195607.png](images/image-20260624-195607.png)

REQ.PG-08300 a 08500true

![image-20260622-125637.png](images/image-20260622-125637.png)

REQ.PG-08601true

![image-20260625-132841.png](images/image-20260625-132841.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

![image-20260625-132913.png](images/image-20260625-132913.png)

REQ.PG-08603

**Cenário: Gestão das autorizações de pagamento**

-   `REQ.PG-08603` Disponibilizar funcionalidade de consulta, alteração e cancelamento das autorizações de pagamento ativas.
    

![image-20260625-133202.png](images/image-20260625-133202.png)

REQ.PG-08605true

REQ.PG-06901true

REQ.PG-06904true

REQ.PG-07200true

Ex.: Transações de valor fixo.

REQ.PG-07401true

REQ.PG-07202true

REQ.PG-07203true

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-07403true

REQ.PG-07300 true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07803true

![image-20260625-133246.png](images/image-20260625-133246.png)

REQ.PG-08900true

Ex.:

-   Cancelado em DD/MM/AA às HH/MM/SS pelo pagador/recebedor.
    
-   Expirado em DD/MM/AA.
    

![image-20260625-135935.png](images/image-20260625-135935.png)

REQ.PG-08901 a 08906

**Cenário: Alteração da autorização de pagamento**

-   `REQ.PG-08901` Para autorizações ativas de cobranças com valor variável, manter o valor máximo não preenchido por padrão.
    
-   `REQ.PG-08902` Permitir que o usuário insira ou altere o valor máximo.
    
-   `REQ.PG-08903` Se o recebedor definir um valor mínimo por transação, informar o usuário que o valor máximo não pode ser inferior ao valor mínimo estabelecido pelo recebedor.
    
-   `REQ.PG-08904` Informar ao usuário, antes da confirmação, que se o valor máximo configurado for inferior ao valor de um pagamento agendado, o pagamento não será efetivado e o usuário poderá ser notificado para buscar outras formas de pagamento.
    
-   `REQ.PG-08905` Informar ao usuário, antes da confirmação, que o novo valor máximo se aplica apenas aos pagamentos ainda não agendados da recorrência.
    
-   `REQ.PG-08906` Seguir a regulação vigente para efetivação da alteração.
    

![image-20260625-133403.png](images/image-20260625-133403.png)

**Cenário: Experiência de alteração da autorização de pagamento**

Na área de gestão de pagamento da ITP, o usuário pode ter a experiência de alteração de parâmetros como a ID, embora, no backend, esteja cancelando a autorização vigente e criando uma nova autorização de pagamento.

Nesses casos, o usuário deverá passar pelo fluxo completo, envolvendo o direcionamento para a ID, confirmação e redirecionamento para ITP para efetivação da solicitação.

REQ.PG-08907true  
Ex.: **Tudo certo!** A autorização anterior foi cancelada e uma nova foi criada com a sua nova instituição.

![image-20260624-202300.png](images/image-20260624-202300.png)

REQ.PG-08908true

REQ.PG-08909true

REQ.PG-08910true

![image-20260625-133523.png](images/image-20260625-133523.png)

wide760#F4F5F7

## Recomendações - ITP

REC.PG-02200 a 02300true

![image-20260616-190415.png](images/image-20260616-190415.png)

REC.PG-02301true

![image-20260624-215716.png](images/image-20260624-215716.png)

REC.PG-02400true

![image-20260624-202734.png](images/image-20260624-202734.png)

REC.PG-02401true

![image-20260625-133622.png](images/image-20260625-133622.png)

REC.PG-02402

**Cenário: Alteração das autorizações de pagamento**

-   `REC.PG-02402` Permitir a gestão de recebimento de notificações para cada autorização ativa em uma única jornada.
    

![image-20260624-202941.png](images/image-20260624-202941.png)

REC.PG-02403

-   `REC.PG-02403` Permitir a gestão de valor máximo para cada autorização ativa de valor variável em uma única jornada.
    

![image-20260624-203043.png](images/image-20260624-203043.png)

REC.PG-02406

**Cenário: Cancelamento da autorização de pagamento**

-   `REC.PG-02406` Se o usuário tentar cancelar uma autorização de pagamento, exibir uma mensagem de confirmação da ação. 
    

REC.PG-02900true  
Ex.: Essa ação não pode ser desfeita e resultará no cancelamento de todos os pagamentos futuros vinculados. 

![image-20260625-133726.png](images/image-20260625-133726.png)

* * *

## Gestão dos pagamentos na ITP

![image-20260625-134053.png](images/image-20260625-134053.png)wide760#F4F5F7

## Requisitos - ITP

  
REQ.PG-08700true

![image-20260625-134107.png](images/image-20260625-134107.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

![image-20260625-134133.png](images/image-20260625-134133.png)

REQ.PG-08800true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07202true

REQ.PG-07203true

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-07403true

REQ.PG-07300 true

REQ.PG-07600true

REQ.PG-07700true

wide760

**Atenção!**

Conforme definido pelo arranjo de pagamento, o comprovante do pagamento inicial avulso deve ser exibido na área de **Gestão de Pix**.

![image-20260625-141115.png](images/image-20260625-141115.png)

REQ.PG-08900true  
Ex.:

-   Agendado para DD/MM/AA
    
-   Cancelado em DD/MM/AA às HH/MM/SS pelo pagador/recebedor
    

![image-20260625-134531.png](images/image-20260625-134531.png)

**Cenário: Cancelamento dos pagamentos agendados**

REQ.PG-08913

-   `REQ.PG-08913` Permitir que o usuário cancele os pagamentos agendados da recorrência.
    

REQ.PG-08909trueREQ.PG-08910true

REQ.PG-08914

-   `REQ.PG-08914` Informar que o cancelamento de um pagamento agendado não impede que os pagamentos futuros da recorrência sejam agendados e efetivados.
    

![image-20260625-135030.png](images/image-20260625-135030.png)

wide760#F4F5F7

## Recomendações - ITP

REC.PG-02500true

![image-20260625-143024.png](images/image-20260625-143024.png)

f

REC.PG-03000true

REC.PG-03001

-   `REC.PG-03001` Combinar a mensagem de confirmação com a informação obrigatória de que o cancelamento do pagamento atual não impede o agendamento dos pagamentos futuros, conforme os parâmetros da autorização ativa.
    

![image-20260625-134824.png](images/image-20260625-134824.png)

* * *

# Gestão na ID

Esta seção reúne os requisitos e recomendações para gestão de Pix Automático na Instituição Detentora de Conta (ID).

* * *

## Gestão das autorizações na ID

![image-20260625-135225.png](images/image-20260625-135225.png)

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08200true

![image-20260624-205657.png](images/image-20260624-205657.png)

REQ.PG-08201 a 08202true

![image-20260624-205802.png](images/image-20260624-205802.png)

REQ.PG-08601true

![image-20260625-135308.png](images/image-20260625-135308.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704true

![image-20260625-135325.png](images/image-20260625-135325.png)

REQ.PG-08603true

![image-20260625-135432.png](images/image-20260625-135432.png)

REQ.PG-08605true

REQ.PG-06901true

REQ.PG-06904true

REQ.PG-07200true

Ex.: Transações de valor fixo.

REQ.PG-07401true

REQ.PG-07202true

REQ.PG-07203true

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-07403true

REQ.PG-07300 true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

REQ.PG-07801

-   `REQ.PG-07801` Informar que o uso do limite de crédito, quando disponível, em caso de transações com valor superior ao saldo disponível é habilitado por padrão
    

![image-20260625-135507.png](images/image-20260625-135507.png)

REQ.PG-08900true

Ex.:

-   Cancelado em DD/MM/AA às HH/MM/SS pelo pagador/recebedor.
    
-   Expirado em DD/MM/AA.
    

![image-20260625-135906.png](images/image-20260625-135906.png)

REQ.PG-08901 a 08906true

REQ.PG-08915

-   `REQ.PG-08915` Para cada autorização ativa, caso o usuário possua limite de crédito contratado, manter seu uso ativado por padrão e permitir que o usuário desative seu uso.
    

REQ.PG-08916

-   `REQ.PG-08916` Para cada autorização ativa, manter o envio de notificações sobre a autorização ativado por padrão e permitir que o usuário desative.
    

![image-20260625-135531.png](images/image-20260625-135531.png)

REQ.PG-08908true

REQ.PG-08909true

REQ.PG-08910true

![image-20260625-143328.png](images/image-20260625-143328.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-02200 a 02300true

![image-20260615-204630.png](images/image-20260615-204630.png)

REC.PG-02301true

![image-20260624-215939.png](images/image-20260624-215939.png)

REC.PG-02400true

![image-20260624-212011.png](images/image-20260624-212011.png)

REC.PG-02401true

![image-20260625-140417.png](images/image-20260625-140417.png)

REC.PG-02402true

![image-20260624-212208.png](images/image-20260624-212208.png)

REC.PG-02403true

![image-20260624-212252.png](images/image-20260624-212252.png)

REC.PG-02404

-   `REC.PG-02404` Se o usuário possuir limite de crédito contratado, permitir a gestão de seu uso para cada autorização ativa em uma única jornada. 
    

![image-20260624-212401.png](images/image-20260624-212401.png)

REC.PG-02406true

REC.PG-02900true  
Ex.: Essa ação não pode ser desfeita e resultará no cancelamento de todos os pagamentos futuros vinculados.

![image-20260625-143437.png](images/image-20260625-143437.png)

* * *

## Gestão dos pagamentos na ID

![image-20260625-140646.png](images/image-20260625-140646.png)

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08700true

![image-20260625-140730.png](images/image-20260625-140730.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704true

![image-20260625-140752.png](images/image-20260625-140752.png)

REQ.PG-08800true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07202true

REQ.PG-07203true

Ex.: Introdução à Música Clássica, Conta de Energia.

REQ.PG-07403true

REQ.PG-07300 true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

wide760

**Atenção!**

Conforme definido pelo arranjo de pagamento, o comprovante do pagamento inicial avulso, quando aplicável, deve ser exibido na área de **Gestão de Pix**.

![image-20260625-140953.png](images/image-20260625-140953.png)

REQ.PG-08900true

Ex.:

-   Agendado para DD/MM/AA
    
-   Cancelado em DD/MM/AA às HH/MM/SS pelo pagador/recebedor
    

![image-20260625-141314.png](images/image-20260625-141314.png)

**Cenário: Cancelamento dos pagamentos agendados**

REQ.PG-08913true

REQ.PG-08909true

REQ.PG-08910true

REQ.PG-08914true

![image-20260625-143618.png](images/image-20260625-143618.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-02500true

![image-20260625-141808.png](images/image-20260625-141808.png)

REC.PG-03000true  
REC.PG-03100true

Ex.: Tem certeza que quer cancelar este pagamento para Telefonia S/A? Esta ação é irreversível e não impede o agendamento dos pagamentos futuros.

![image-20260625-141930.png](images/image-20260625-141930.png)

* * *

Matriz de status de pagamentostrue

* * *

true

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático e Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08603`

**Texto**

Disponibilizar funcionalidade de consulta, alteração e cancelamento das autorizações de pagamento ativas.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08901`

**Texto**

Para autorizações ativas de cobranças com valor variável, manter o valor máximo não preenchido por padrão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08902`

**Texto**

Permitir que o usuário insira ou altere o valor máximo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08903`

**Texto**

Se o recebedor definir um valor mínimo por transação, informar o usuário que o valor máximo não pode ser inferior ao valor mínimo estabelecido pelo recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08904`

**Texto**

Informar ao usuário, antes da confirmação, que se o valor máximo configurado for inferior ao valor de um pagamento agendado, o pagamento não será efetivado e o usuário poderá ser notificado para buscar outras formas de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08905`

**Texto**

Informar ao usuário, antes da confirmação, que o novo valor máximo se aplica apenas aos pagamentos ainda não agendados da recorrência.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08906`

**Texto**

Seguir a regulação vigente para efetivação da alteração.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08913`

**Texto**

Permitir que o usuário cancele os pagamentos agendados da recorrência.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08914`

**Texto**

Informar que o cancelamento de um pagamento agendado não impede que os pagamentos futuros da recorrência sejam agendados e efetivados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08915`

**Texto**

Para cada autorização ativa, caso o usuário possua limite de crédito contratado, manter seu uso ativado por padrão e permitir que o usuário desative seu uso.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Automático

**Jornada**

Gestão

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08916`

**Texto**

Para cada autorização ativa, manter o envio de notificações sobre a autorização ativado por padrão e permitir que o usuário desative.
