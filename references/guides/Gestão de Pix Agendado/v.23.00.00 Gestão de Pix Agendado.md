# v.23.00.00 Gestão de Pix Agendado

Esta página reúne requisitos e recomendações para gestão **de autorizações e transações de pagamentos com** **Pix Agendado** **com ou sem redirecionamento** **(JSR)** via Open Finance.  

Nota.Regulamentação e Arranjotrue

* * *

# Gestão na ITP

Esta seção reúne os requisitos e recomendações para gestão de Pix Agendado na Instituição Iniciadora de Transação de Pagamento (ITP).

* * *

## Gestão das autorizações na ITP

![image-20260622-191510.png](images/image-20260622-191510.png)

REQ.PG-08200true

![image-20260622-133223.png](images/image-20260622-133223.png)

REQ.PG-08300 a 08500true

![image-20260622-125637.png](images/image-20260622-125637.png)

REQ.PG-08601

**Cenário: Histórico das autorizações de pagamento**

-   `REQ.PG-08601` Disponibilizar funcionalidade de consulta ao histórico das autorizações de pagamento e seus respectivos status.
    

![image-20260623-131331.png](images/image-20260623-131331.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

![image-20260622-133441.png](images/image-20260622-133441.png)

REQ.PG-08604

**Cenário: Gestão das autorizações de pagamento**

-   `REQ.PG-08604` Disponibilizar funcionalidade de consulta e cancelamento das autorizações de pagamento ativas.
    

![image-20260622-170359.png](images/image-20260622-170359.png)

REQ.PG-08605

**Cenário: Comprovante das autorizações de pagamento**

-   `REQ.PG-08605` Para o comprovante de cada autorização de pagamento, além das informações descritas neste cenário, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para comprovante de pagamento.
    

![image-20260622-170451.png](images/image-20260622-170451.png)

REQ.PG-06901true

REQ.PG-06902 a 06903true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07501true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07801true

![image-20260622-170603.png](images/image-20260622-170603.png)

REQ.PG-08900true

![image-20260623-131533.png](images/image-20260623-131533.png)

**Cenário: Experiência de alteração da autorização de pagamento**  
Na área de gestão de pagamento da ITP, para evitar o reinício do processo de criação de uma autorização de pagamento, o usuário pode ter a experiência de alteração de parâmetros como data, recebedor ou ID, embora, no backend, esteja cancelando o agendamento vigente e criando uma nova autorização de agendamento.

Nesses casos, o usuário deverá passar pelo fluxo completo, envolvendo o direcionamento para a ID, confirmação e redirecionamento para ITP para efetivação da solicitação.

REQ.PG-08907

-   `REQ.PG-08907` Se a ITP disponibilizar a experiência de alteração da autorização de pagamento, exibir, na etapa de efetivação, mensagem informando que a autorização de pagamento anterior foi cancelada e substituída por um nova.
    

Ex.: **Tudo certo!** Sua autorização anterior foi encerrado e uma novo foi criada com o novo valor.

![image-20260622-170734.png](images/image-20260622-170734.png)

REQ.PG-08908

**Cenário: Cancelamento da autorização de pagamento**

-   `REQ.PG-08908` Permitir que o usuário cancele a autorização de pagamento.
    

REQ.PG-08909-   `REQ.PG-08909` Informar ao usuário sobre as regras para cancelamento, conforme definido pelo arranjo de pagamento. 

Ex.: Você pode cancelar o pagamento até às 23:59 do dia anterior à data agendada.

REQ.PG-08910

-   `REQ.PG-08910` Informar ao usuário sobre a irreversibilidade do cancelamento e outras possíveis consequências.
    

![image-20260622-171032.png](images/image-20260622-171032.png)

wide760#F4F5F7

## Recomendações - ITP

REC.PG-02200 a 02300true

![image-20260622-171302.png](images/image-20260622-171302.png)

REC.PG-02301true

![image-20260624-215716.png](images/image-20260624-215716.png)

REC.PG-02400true

![image-20260622-171427.png](images/image-20260622-171427.png)

REC.PG-02401

**Cenário: Histórico das autorizações de pagamento**

-   `REC.PG-02401` Permitir a ordenação (por data, recebedor, status) e o filtro de status na consulta ao histórico dos pagamentos.
    

![image-20260622-171747.png](images/image-20260622-171747.png)

REC.PG-02800

**Cenário: Comprovante da autorização de pagamento**

-   `REC.PG-02800` Informar ao usuário de que a transação estará sujeita à disponibilidade de saldo e limites transacionais na conta de débito no momento da efetivação do pagamento.
    

![image-20260622-171949.png](images/image-20260622-171949.png)

**Cenário: Cancelamento da autorização de pagamento**

REC.PG-02900-   `REC.PG-02900` Se o usuário tentar cancelar uma autorização de pagamento, combinar a mensagem de confirmação com a informação obrigatória sobre a irreversibilidade do cancelamento.   

Ex.: Deseja cancelar esse agendamento para João Rodrigues? Esta ação é irreversível e resultará no cancelamento de todos os pagamentos futuros vinculados.

![image-20260622-172136.png](images/image-20260622-172136.png)

* * *

## Gestão dos pagamentos na ITP

![image-20260623-132130.png](images/image-20260623-132130.png)

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-08700true

![image-20260623-132508.png](images/image-20260623-132508.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

![image-20260623-132700.png](images/image-20260623-132700.png)

REQ.PG-08800true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

![image-20260623-132908.png](images/image-20260623-132908.png)

REQ.PG-08900true

![image-20260622-174548.png](images/image-20260622-174548.png)

**Cenário: Cancelamento dos pagamentos agendados**

REQ.PG-08912

-   `REQ.PG-08912` Informar que o cancelamento de um pagamento da recorrência não impede a efetivação dos pagamentos futuros.
    

![image-20260622-174940.png](images/image-20260622-174940.png)

wide760#F4F5F7

## Recomendações - ITP

REC.PG-02500true

![image-20260623-133011.png](images/image-20260623-133011.png)

REC.PG-03000

**Cenário: Cancelamento dos pagamentos**

-   `REC.PG-03000` Se o usuário tentar cancelar um pagamento da recorrência, exibir uma mensagem de confirmação da ação.   
    

REC.PG-03100

-   `REC.PG-03100` Combinar a mensagem de confirmação com a informação obrigatória de que o cancelamento do pagamento não impede a efetivação dos pagamentos futuros, conforme os parâmetros da autorização ativa.
    

Ex.: Deseja cancelar este pagamento para João Rodrigues? Essa ação não pode ser desfeita e não impede o pagamento dos agendamentos futuros.

![image-20260622-175750.png](images/image-20260622-175750.png)

* * *

# Gestão na ID

Esta seção reúne os requisitos e recomendações para gestão de Pix Agendado na Instituição Detentora de Conta (ID).

* * *

## Gestão das autorizações na ID

![image-20260622-191801.png](images/image-20260622-191801.png)

REQ.PG-08200true

![image-20260622-191949.png](images/image-20260622-191949.png)

REQ.PG-08201 a 08202true

![image-20260622-192220.png](images/image-20260622-192220.png)

REQ.PG-08601true

![image-20260622-192610.png](images/image-20260622-192610.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704true

![image-20260622-192853.png](images/image-20260622-192853.png)

REQ.PG-08604true

![image-20260623-133258.png](images/image-20260623-133258.png)

REQ.PG-08605true

![image-20260623-133414.png](images/image-20260623-133414.png)

REQ.PG-06901true

REQ.PG-06902 a 06903true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

REQ.PG-07801true

![image-20260623-133541.png](images/image-20260623-133541.png)

REQ.PG-08900true

![image-20260623-133745.png](images/image-20260623-133745.png)

REQ.PG-08908true

REQ.PG-08909true

Ex.: Você pode cancelar o pagamento até às 23:59 do dia anterior à data agendada.

REQ.PG-08910true

![image-20260623-133831.png](images/image-20260623-133831.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-02200 a 02300true

![image-20260622-200942.png](images/image-20260622-200942.png)

REC.PG-02301true

![image-20260624-215939.png](images/image-20260624-215939.png)

REC.PG-02400true

![image-20260622-201037.png](images/image-20260622-201037.png)

REC.PG-02401true

![image-20260622-201137.png](images/image-20260622-201137.png)

REQ.PG-07801true

![image-20260622-201256.png](images/image-20260622-201256.png)

**Cenário: Cancelamento da autorização de pagamento**

REC.PG-02900true Ex.: Deseja cancelar esse agendamento para João Rodrigues? Esta ação é irreversível e resultará no cancelamento de todos os pagamentos futuros vinculados.

![image-20260623-133919.png](images/image-20260623-133919.png)

* * *

## Gestão dos pagamentos na ID

![image-20260623-134023.png](images/image-20260623-134023.png)

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08700true

![image-20260623-134137.png](images/image-20260623-134137.png)

REQ.PG-08701 a 08702true

REQ.PG-08703true

REQ.PG-08704true

![image-20260623-134406.png](images/image-20260623-134406.png)

REQ.PG-08800true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

![image-20260622-203339.png](images/image-20260622-203339.png)

REQ.PG-08900true

![image-20260623-123711.png](images/image-20260623-123711.png)

**Cenário: Cancelamento dos pagamentos agendados**

REQ.PG-08912true

![image-20260623-123753.png](images/image-20260623-123753.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-02500true

![image-20260623-134528.png](images/image-20260623-134528.png)

REC.PG-03000true

REC.PG-03100true

Ex.: Deseja cancelar este pagamento para João Rodrigues? Essa ação não pode ser desfeita e não impede o pagamento dos agendamentos futuros.

![image-20260622-203712.png](images/image-20260622-203712.png)

* * *

Matriz de status de pagamentostrue

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08601`

**Texto**

Disponibilizar funcionalidade de consulta ao histórico das autorizações de pagamento e seus respectivos status.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08604`

**Texto**

Disponibilizar funcionalidade de consulta e cancelamento das autorizações de pagamento ativas.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08605`

**Texto**

Para o comprovante de cada autorização de pagamento, além das informações descritas neste cenário, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para comprovante de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-08907`

**Texto**

Se a ITP disponibilizar a experiência de alteração da autorização de pagamento, exibir, na etapa de efetivação, mensagem informando que a autorização de pagamento anterior foi cancelada e substituída por um nova.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08908`

**Texto**

Permitir que o usuário cancele a autorização de pagamento.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08909`

**Texto**

Informar ao usuário sobre as regras para cancelamento, conforme definido pelo arranjo de pagamento. true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08910`

**Texto**

Informar ao usuário sobre a irreversibilidade do cancelamento e outras possíveis consequências.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08912`

**Texto**

Informar que o cancelamento de um pagamento da recorrência não impede a efetivação dos pagamentos futuros.
