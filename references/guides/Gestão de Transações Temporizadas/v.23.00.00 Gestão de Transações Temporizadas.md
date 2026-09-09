# v.23.00.00 Gestão de Transações Temporizadas

Esta página reúne os requisitos e recomendações para gestão das **transações que exigem análise adicional por parte da Instituição Detentora de Conta (ID**).

* * *

# Gestão na ITP

Esta seção reúne os requisitos e recomendações para gestão de Transações Temporizadas na Instituição Iniciadora de Transação de Pagamento (ITP).

![image-20260624-170631.png](images/image-20260624-170631.png)

* * *

## Gestão das transações na ITP

REQ.PG-08700true

Ex.: (Autorização) Ativa, (Pix) Concluído/Enviado, (Pix) Não concluído/Não enviado, Cancelado, Pendente, Em processamento, Em análise, Expirado, Rejeitado/Negado etc.

![image-20260624-170657.png](images/image-20260624-170657.png)

REQ.PG-08800true

REQ.PG-15500true

REQ.PG-15600true

![image-20260624-170039.png](images/image-20260624-170039.png)REQ.PG-15500

-   `REQ.PG-15700` Se após análise, a solicitação for negada pela Detentora selecionada, indicar ao usuário, quando aplicável, outra Detentora e/ou forma de iniciação de pagamento.
    

![image-20260624-170337.png](images/image-20260624-170337.png)

* * *

# Gestão na ID

Esta seção reúne os requisitos e recomendações para gestão de Transações Temporizadas na Instituição Detentora de Conta (ID).

![image-20260422-193419.png](images/image-20260422-193419.png)

## Gestão das transações na ID

wide760#F4F5F7

## Requisitos - ID

REQ.PG-08700true

Ex.: (Autorização) Ativa, (Pix) Concluído/Enviado, (Pix) Não concluído/Não enviado, Cancelado, Pendente, Em análise, Expirado, Rejeitado etc.

![image-20260624-170815.png](images/image-20260624-170815.png)

REQ.PG-08800true

REQ.PG-15500true

REQ.PG-15600true

![image-20260624-171318.png](images/image-20260624-171318.png)true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Gestão (Transações Temporizadas)

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-15700`

**Texto**

Se após análise, a solicitação for negada pela Detentora selecionada, indicar ao usuário, quando aplicável, outra Detentora e/ou forma de iniciação de pagamento.
