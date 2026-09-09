# v.23.00.00 Notificações de Pix Agendado

Esta página reúne os requisitos e recomendações referentes ao envio de notificações durante a jornada do Pix Agendado, inclusive para alterações e cancelamentos feitos através da área de gestão. Essas comunicações podem ser feitas pela Instituição Iniciadora de Transação de Pagamento (ITP) ou pela Instituição Detentora de Conta (ID), conforme definido pelo arranjo de pagamento. 

Nota.Regulamentação e Arranjotrue

# Notificações sobre as autorizações

wide760#F4F5F7

## Requisitos - ITP

REQ.PG-10800

**Cenário: Sobre a autorização de pagamento**

**Nota**  
A forma de envio da notificação é de livre escolha do participante.

-   `REQ.PG-10800` Notificar o usuário sobre o sucesso ou o insucesso da autorização do agendamento, informando o motivo em caso de insucesso, conforme as regras do arranjo de pagamento.
    

![image-20260623-184447.png](images/image-20260623-184447.png)

* * *

# Notificações sobre os pagamentos

REQ.PG-09000true  
Ex.: O Pix Agendado no valor de R$100,00 foi enviado para João Rodrigues da Silva CPF \*\*\*.345.678-\*\*.

![image-20260623-174012.png](images/image-20260623-174012.png)

REQ.PG-09001

-   `REQ.PG-09001` Notificar o usuário se a conta recebedora for encerrada, informando-o de que esse é o motivo para a não efetivação do pagamento atual e dos futuros.
    

Ex.: O Pix Agendado para João Rodrigues (R$ 100,00) não foi realizado porque a conta do recebedor foi encerrada. Altere a conta na Área de Gestão.

![image-20260623-174046.png](images/image-20260623-174046.png)

wide760#F4F5F7

## Recomendações - ID

REC.PG-03200**Cenário: Sobre pagamentos**

**Nota**  
A forma de envio da notificação é de livre escolha do participante.

-   `REC.PG-03200` Na notificação de encerramento da conta do recebedor, direcionar o usuário para a jornada de Alteração/Cancelamento da autorização de pagamento, a fim de possibilitar a manutenção dos pagamentos com o cadastro de uma nova conta recebedora.   

Ex.: O Pix Agendado para João Rodrigues (R$ 100,00) não foi realizado porque a conta do recebedor foi encerrada. Altere a conta na Área de Gestão.

![image-20260623-183131.png](images/image-20260623-183131.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Notificações

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-10800`

**Texto**

Notificar o usuário sobre o sucesso ou o insucesso da autorização do agendamento, informando o motivo em caso de insucesso, conforme as regras do arranjo de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Transferências Inteligentes

**Jornada**

Notificações

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-09001`

**Texto**

Notificar o usuário se a conta recebedora for encerrada, informando-o de que esse é o motivo para a não efetivação do pagamento atual e dos futuros.
