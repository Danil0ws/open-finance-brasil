# Informações Gerais - [DC] Fundos de Investimento - v1.1.0-beta.1

**Visão Geral**

API de informações de operações de Fundos de Investimento Open Finance Brasil – Fase 4. API que retorna informações de operações de investimento do tipo Fundos de Investimento mantidas nas instituições transmissoras por seus clientes, incluindo dados como informações do produto, quantidade, saldos em posição do cliente e movimentações financeiras.

## **Product List:** (GET /funds/v1/investments)

**Visão Geral**

Obtém a lista de operações de Fundos de Investimento mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento.

**Visão de alto de nível das estruturas de dados**

![image-20230418-201728.png](images/image-20230418-201728.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230418-201756.png](images/image-20230418-201756.png)

-   DER Lógico
    

![image-20230418-201812.png](images/image-20230418-201812.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/fundsGetInvestments_v1.1.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_fundsGetInvestments_v1.csv)

## **Product Identification:** (GET /funds/v1/investments/{investmentId})

**Visão Geral**

Obtém os dados da operação de Fundos de Investimento identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![image-20230418-201838.png](images/image-20230418-201838.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230418-201905.png](images/image-20230418-201905.png)

-   DER Lógico
    

![image-20230418-201933.png](images/image-20230418-201933.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/fundsGetInvestmentsInvestmentId_v1.1.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_fundsGetInvestmentsInvestmentId_v1.csv)

## **Balances:** (GET /funds/v1/investments/{investmentId}/balances)

**Visão Geral**

Obtém a posição da operação de Fundos de Investimento identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![image-20230418-202004.png](images/image-20230418-202004.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230418-202019.png](images/image-20230418-202019.png)

-   DER Lógico
    

![image-20230418-202047.png](images/image-20230418-202047.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/fundsGetInvestmentsInvestmentIdBalances_v1.1.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_fundsGetInvestmentsInvestmentIdBalances_v1.csv)

## **Transactions:** (GET /funds/v1/investments/{investmentId}/transactions)

**Visão Geral**

Obtém as movimentações históricas (últimos 12 meses) da operação de Fundos de Investimento identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![image-20230418-202116.png](images/image-20230418-202116.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230418-202130.png](images/image-20230418-202130.png)

-   DER Lógico
    

![image-20230418-202215.png](images/image-20230418-202215.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/fundsGetInvestmentsInvestmentIdTransactions_v1.1.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_fundsGetInvestmentsInvestmentIdTransactions_v1.csv)

## **Transactions Current:** (GET /funds/v1/investments/{investmentId}/transactions-current)

**Visão Geral**

Obtém as movimentações recentes da operação de Fundos de Investimento identificada por investmentId. O período a ser considerado para apresentação de movimentações será de até 7 dias - 7 dias anteriores da consulta, incluindo o dia da consulta (D-6).

**Visão de alto de nível das estruturas de dados**

![image-20230418-202247.png](images/image-20230418-202247.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230418-202259.png](images/image-20230418-202259.png)

-   DER Lógico
    

![image-20230418-202319.png](images/image-20230418-202319.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/fundsGetInvestmentsInvestmentIdTransactionsCurrent_v1.1.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_fundsGetInvestmentsInvestmentIdTransactionsCurrent_v1.csv)
