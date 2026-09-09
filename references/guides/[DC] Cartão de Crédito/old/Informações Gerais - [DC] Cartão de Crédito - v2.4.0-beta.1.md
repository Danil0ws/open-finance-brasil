# Informações Gerais - [DC] Cartão de Crédito - v2.4.0-beta.1

**Visão Geral**

A API Credit-cards-accounts viabiliza o compartilhamento dos dados de conta pós-paga(cartão de crédito), tais como limites, transações e faturas.

## **Lista de cartões de crédito:** (GET /credit-cards-accounts/v2/accounts)

**Visão Geral**

Método para obter a lista de contas de pagamento pós-paga mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento

Tags: Bandeira (Credit Card Network), Cartão Múltiplo (Multiple CreditCard), CNPJ (CNPJ Number) e Conta de pagamento pós-paga (Credit Card).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_List-f5ed7649.png](images/TLD_CreditCardAccount_List-f5ed7649.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount\_List\_Conceitual-0e6048e1.png](images/DER_CreditCardAccount_List_Conceitual-0e6048e1.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_List\_Logico-e2ca0183.png](images/DER_CreditCardAccount_List_Logico-e2ca0183.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccounts_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccounts_v2.4.0.csv)

## **Identificação de cartão de crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId})

**Visão Geral**

Obtém dados relativos ao conjunto de informações referentes à identificação da conta de pagamento pós-paga

Tags: Bandeira (Credit Card Network), Cartão Múltiplo (Multiple CreditCard), CNPJ (CNPJ Number) e Conta de pagamento pós-paga (Credit Card).

  
Visão de alto de nível das estruturas de dados

![TLD\_CreditCardAccount\_Identification-a9737a16.png](images/TLD_CreditCardAccount_Identification-a9737a16.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Identification-c203839a.png](images/DER_CreditCardAccount_Identification-c203839a.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccountsCreditCardAccountId_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccountsCreditCardAccountId_v2.4.0.csv)

##   
**Limites de cartão de crédito**: ( GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/limits)

**Visão Geral**

Obtém dados dos limites: de Crédito Total e por Modalidade de Crédito relativos à conta de pagamento pós-paga.

Tags: CNPJ (CNPJ Number), Conta de pagamento pós-paga (Credit Card), Empréstimo Cartão Consignado (Payroll Loan) e Limite Flexível (Flexible Limit).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Limits-da0b15b9.png](images/TLD_CreditCardAccount_Limits-da0b15b9.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Limits-a61a5c76.png](images/DER_CreditCardAccount_Limits-a61a5c76.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccountsCreditCardAccountIdLimits_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccountsCreditCardAccountIdLimits_v2.4.0.csv)

## **Transações de cartão de crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/transactions)

**Visão Geral**

Obtém dados das transações relativas à conta de pagamento pós-paga.

Tags: CNPJ (CNPJ Number), Conta de pagamento pós-paga (Credit Card), Crédito Rotativo (Overdraft) e MCC (Merchant Category Code).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Transactions-30cd2d1e.png](images/TLD_CreditCardAccount_Transactions-30cd2d1e.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Transactions-3ec790c3.png](images/DER_CreditCardAccount_Transactions-3ec790c3.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccountsCreditCardAccountIdTransactions_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccountsCreditCardAccountIdTransactions_v2.4.0.csv)

## **Transações de cartão de crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/transactions-current)

**Visão Geral**

Obtém dados das transações relativas à conta de pagamento pós-paga.

Tags: CNPJ (CNPJ Number), Conta de pagamento pós-paga (Credit Card), Crédito Rotativo (Overdraft) e MCC (Merchant Category Code).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Transactions-30cd2d1e.png](images/TLD_CreditCardAccount_Transactions-30cd2d1e.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Transactions-3ec790c3.png](images/DER_CreditCardAccount_Transactions-3ec790c3.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccountsCreditCardAccountIdTransactionsCurrent_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccountsCreditCardAccountIdTransactionsCurrent_v2.4.0.csv)

##   
**Fatura de Cartão de Crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/bills)

**Visão Geral**

Obtém dados referentes à fatura da conta de pagamento pós-paga.

Tags: CNPJ (CNPJ Number), Conta de pagamento pós-paga (Credit Card), Crédito Rotativo (Overdraft) e Fatura (Bill).

Visão de alto de nível das estruturas de dados

![TLD\_CreditCardAccount\_Bill-18fa37a9.png](images/TLD_CreditCardAccount_Bill-18fa37a9.png)

DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Bill-eafe4a52.png](images/DER_CreditCardAccount_Bill-eafe4a52.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccountsCreditCardAccountIdBills_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccountsCreditCardAccountIdBills_v2.4.0.csv)

## **Transações de cartão de crédito por fatura**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/bills/{billId}/transactions)

**Visão Geral**

Obtém a lista de transações da conta identificada por creditCardAccountId e billId.

Tags: CNPJ (CNPJ Number), Conta de pagamento pós-paga (Credit Card), Crédito Rotativo (Overdraft) e MCC (Merchant Category Code).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Transactions-30cd2d1e.png](images/TLD_CreditCardAccount_Transactions-30cd2d1e.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Transactions-3ec790c3.png](images/DER_CreditCardAccount_Transactions-3ec790c3.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/creditCardsGetAccountsCreditCardAccountIdBillsBillIdTransactions_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_creditCardsGetAccountsCreditCardAccountIdBillsBillIdTransactions_v2.4.0.csv)
