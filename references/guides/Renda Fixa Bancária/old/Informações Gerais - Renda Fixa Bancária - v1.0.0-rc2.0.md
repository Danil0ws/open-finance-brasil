# Informações Gerais - Renda Fixa Bancária - v1.0.0-rc2.0

**Visão Geral**

A API bank-fixed-incomes viabiliza o compartilhamento dos dados dos produtos de investimentos de renda fixa bancária como; listagem dos produtos, detalhe do produto, posição do produto e movimentações históricas e recentes do produto do cliente.

## **Product List:** (GET /bank-fixed-incomes/v1/investments)

**Visão Geral**

Obtém a lista de operações de Renda Fixa Bancária mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento.

**Visão de alto de nível das estruturas de dados**

![GET\_ProductList\_visaoAltoNivel.png](images/GET_ProductList_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![GET\_ProductList\_DER\_conceitual.png](images/GET_ProductList_DER_conceitual.png)

-   DER Lógico
    

![GET\_ProductList\_DER\_logico.png](images/GET_ProductList_DER_logico.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-banktFixedIncomesGetInvestments_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_bankFixedIncomesGetInvestments_v1.csv)

## **Product Identification:** (GET /bank-fixed-incomes/v1/investments/{investmentId})

**Visão Geral**

Obtém os dados da operação de Renda Fixa Bancária identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![GET\_ProductIdentification\_visaoAltoNivel.png](images/GET_ProductIdentification_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_bancaria-v4.png](images/DER_conceitual_bancaria-v4.png)

-   DER Lógico
    

![GET\_ProductIdentification\_DER\_logica.png](images/GET_ProductIdentification_DER_logica.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-banktFixedIncomesGetInvestmentsInvestmentId_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_bankFixedIncomesGetInvestmentsInvestmentId_v1.csv)

## **Balances:** (GET /bank-fixed-incomes/v1/investments/{investmentId}/balances)

**Visão Geral**

Obtém a posição da operação de Renda Fixa Bancária identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![GET\_Balances\_visaoAltoNivel.png](images/GET_Balances_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_bancaria-v4.png](images/DER_conceitual_bancaria-v4.png)

-   DER Lógico
    

![GET\_Balances\_DER\_logico.png](images/GET_Balances_DER_logico.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-banktFixedIncomesGetInvestmentsInvestmentIdBalances_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_bankFixedIncomesGetInvestmentsInvestmentIdBalances_v1.csv)

## **Transactions:** (GET /bank-fixed-incomes/v1/investments/{investmentId}/transactions)

**Visão Geral**

Obtém as movimentações da operação de Renda Fixa Bancária identificada por investmentId.

**Visão de alto de nível das estruturas de dados**

![GET\_Transactions\_visaoAltoNivel.png](images/GET_Transactions_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_bancaria-v4.png](images/DER_conceitual_bancaria-v4.png)

-   DER Lógico
    

![image-20230427-165914.png](images/image-20230427-165914.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-banktFixedIncomesGetInvestmentsInvestmentIdTransactions_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_bankFixedIncomesGetInvestmentsInvestmentIdTransactions_v1.csv)

## **Transactions Current:** (GET /bank-fixed-incomes/v1/investments/{investmentId}/transactions-current)

**Visão Geral**

Obtém as movimentações recentes da operação de Fundos de Investimento identificada por investmentId. O período a ser considerado para apresentação de movimentações será de até 7 dias - 7 dias anteriores da consulta, incluindo o dia da consulta (D-6).

**Visão de alto de nível das estruturas de dados**

![GET\_Transactions\_visaoAltoNivel.png](images/GET_Transactions_visaoAltoNivel.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_conceitual\_bancaria-v4.png](images/DER_conceitual_bancaria-v4.png)

-   DER Lógico
    

![image-20230427-170009.png](images/image-20230427-170009.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-banktFixedIncomesGetInvestmentsInvestmentIdTransactionsCurrent_v1.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_banktFixedIncomesGetInvestmentsInvestmentIdTransactionsCurrent_v1.csv)
