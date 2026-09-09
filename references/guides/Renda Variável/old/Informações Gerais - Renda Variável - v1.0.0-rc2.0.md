# Informações Gerais - Renda Variável - v1.0.0-rc2.0

**Visão Geral**

API de informações de operações de Renda Variável Open Finance Brasil – Fase 4. API que retorna informações de operações de investimento do tipo Renda Variável mantidas nas instituições transmissoras por seus clientes, incluindo dados como informações do produto, quantidade, saldos em posição do cliente, movimentações financeiras e detalhes da nota de negociação.

## **Product List:** (GET /variable-incomes/v1/investments)

**Visão Geral**

Obtém a lista de operações de Renda Variável mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento.

**Visão de alto de nível das estruturas de dados**

![image-20230405-201406.png](images/image-20230405-201406.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230405-195433.png](images/image-20230405-195433.png)

-   DER Lógico
    

![image-20230405-195537.png](images/image-20230405-195537.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-variableIncomesGetInvestments_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_variableIncomesGetInvestments_v1.csv)

## **Product Identification:** (GET /variable-incomes/v1/investments/{investmentId})

**Visão Geral**

Obtém os dados da operação de Renda Variável identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![image-20230405-195642.png](images/image-20230405-195642.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230405-195728.png](images/image-20230405-195728.png)

-   DER Lógico
    

![image-20230405-195801.png](images/image-20230405-195801.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-variableIncomesGetInvestmentsInvestmentId_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_variableIncomesGetInvestmentsInvestmentId_v1.csv)

## **Balances:** (GET /variable-incomes/v1/investments/{investmentId}/balances)

**Visão Geral**

Obtém a posição da operação de Renda Variável identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![image-20230405-201254.png](images/image-20230405-201254.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230405-195919.png](images/image-20230405-195919.png)

-   DER Lógico
    

![image-20230405-195959.png](images/image-20230405-195959.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-variableIncomesGetInvestmentsInvestmentIdBalances_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_variableIncomesGetInvestmentsInvestmentIdBalances_v1.csv)

## **Transactions:** (GET /variable-incomes/v1/investments/{investmentId}/transactions)

**Visão Geral**

Obtém as movimentações históricas (últimos 12 meses) da operação de Renda Variável identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![image-20230405-200434.png](images/image-20230405-200434.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230405-200125.png](images/image-20230405-200125.png)

-   DER Lógico
    

![image-20230427-163323.png](images/image-20230427-163323.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-variableIncomesGetInvestmentsInvestmentIdTransactions_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_variableIncomesGetInvestmentsInvestmentIdTransactions_v1.csv)

## **Transactions Current:** (GET /variable-incomes/v1/investments/{investmentId}/transactions-current)

**Visão Geral**

Obtém as movimentações recentes da operação de Renda Variável identificada por investmentId. O período a ser considerado para apresentação de movimentações será de até 7 dias - 7 dias anteriores da consulta, incluindo o dia da consulta (D-6).

**Visão de alto de nível das estruturas de dados**

![image-20230405-200359.png](images/image-20230405-200359.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230405-200814.png](images/image-20230405-200814.png)

-   DER Lógico
    

![image-20230427-163404.png](images/image-20230427-163404.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-variableIncomesGetInvestmentsInvestmentIdTransactionsCurrent_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_variableIncomesGetInvestmentsInvestmentIdTransactionsCurrent_v1.csv)

## **Broker Note Details:** (GET /variable-incomes/v1/investments/{investmentId}/broker-notes/{brokerNoteId})

**Visão Geral**

Obtém as informações da nota de negociação identificado nas movimentações de compra e venda de ativos em bolsa.

**Visão de alto de nível das estruturas de dados**

![image-20230405-200931.png](images/image-20230405-200931.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230405-200952.png](images/image-20230405-200952.png)

-   DER Lógico
    

![image-20230427-163441.png](images/image-20230427-163441.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-variableIncomesGetInvestmentsInvestmentIdBrokerNotesBrokerNoteId_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_variableIncomesGetInvestmentsInvestmentIdBrokerNotesBrokerNoteId_v1.csv)
