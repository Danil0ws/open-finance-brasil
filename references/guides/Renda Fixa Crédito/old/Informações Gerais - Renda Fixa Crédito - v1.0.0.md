# Informações Gerais - Renda Fixa Crédito - v1.0.0

17

## **Product List:** (GET /credit-fixed-incomes/v1/investments)

**Visão Geral**

Obtém a lista de operações de Renda Fixa Crédito mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento.

**Visão de alto de nível das estruturas de dados**

![GET\_ProductList\_visaoAltoNivel.png](images/GET_ProductList_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![GET\_ProductList\_DER\_conceitual.png](images/GET_ProductList_DER_conceitual.png)

-   DER Lógico
    

![GET\_ProductList\_DER\_logico.png](images/GET_ProductList_DER_logico.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditFixedIncomesGetInvestments_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditFixedIncomesGetInvestments_v1.csv)

## **Product Identification:** (GET /credit-fixed-incomes/v1/investments/{investmentId})

**Visão Geral**

Obtém os dados da operação de Renda Fixa Crédito identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![GET\_ProductIdentification\_visaoAltoNivel.png](images/GET_ProductIdentification_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_credito-v4.png](images/DER_conceitual_credito-v4.png)

-   DER Lógico
    

![GET\_ProductIdentification\_DER\_logico.png](images/GET_ProductIdentification_DER_logico.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditFixedIncomesGetInvestmentsInvestmentId_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditFixedIncomesGetInvestmentsInvestmentId_v1.csv)

## **Balances:** (GET /credit-fixed-incomes/v1/investments/{investmentId}/balances)

**Visão Geral**

Obtém a posição da operação de Renda Fixa Crédito identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![GET\_Balances\_visaoAltoNivel.png](images/GET_Balances_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_credito-v4.png](images/DER_conceitual_credito-v4.png)

-   DER Lógico
    

![GET\_Balances\_DER\_logico.png](images/GET_Balances_DER_logico.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditFixedIncomesGetInvestmentsInvestmentIdBalances_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditFixedIncomesGetInvestmentsInvestmentIdBalances_v1.csv)

## **Transactions:** (GET /credit-fixed-incomes/v1/investments/{investmentId}/transactions)

**Visão Geral**

Obtém as movimentações da operação de Renda Fixa Crédito identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![GET\_Transactions\_visaoAltoNivel.png](images/GET_Transactions_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_credito-v4.png](images/DER_conceitual_credito-v4.png)

-   DER Lógico
    

![image-20230427-164630.png](images/image-20230427-164630.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditFixedIncomesGetInvestmentsInvestmentIdTransactions_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditFixedIncomesGetInvestmentsInvestmentIdTransactions_v1.csv)

## **Transactions Current:** (GET /credit-fixed-incomes/v1/investments/{investmentId}/transactions-current)

**Visão Geral**

Obtém as movimentações recentes da operação de Fundos de Investimento identificada por investmentId. O período a ser considerado para apresentação de movimentações será de até 7 dias - 7 dias anteriores da consulta, incluindo o dia da consulta (D-6).

**Visão de alto de nível das estruturas de dados**

![GET\_Transactions\_visaoAltoNivel.png](images/GET_Transactions_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_credito-v4.png](images/DER_conceitual_credito-v4.png)

-   DER Lógico
    

![image-20230427-164720.png](images/image-20230427-164720.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditFixedIncomesGetInvestmentsInvestmentIdTransactionsCurrent_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditFixedIncomesGetInvestmentsInvestmentIdTransactionsCurrent_v1.csv)
