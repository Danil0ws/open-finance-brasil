# Informações Gerais - Cartão de Crédito - v2.0.0

**Visão Geral**

A API Credit-cards-accounts viabiliza o compartilhamento dos dados de conta pós-paga(cartão de crédito), tais como limites, transações e faturas.

## **Lista de cartões de crédito:** (GET /credit-cards-accounts/v2/accounts)

**Visão Geral**

Método para obter a lista de contas de pagamento pós-paga mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento

Tags: [Bandeira (Credit Card Network)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioBandeira), [Cartão Múltiplo (Multiple CreditCard)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCartaoMultiplo), [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ) e [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_List-f5ed7649.png](images/TLD_CreditCardAccount_List-f5ed7649.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount\_List\_Conceitual-0e6048e1.png](images/DER_CreditCardAccount_List_Conceitual-0e6048e1.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_List\_Logico-e2ca0183.png](images/DER_CreditCardAccount_List_Logico-e2ca0183.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditCardsGetAccounts_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_list.csv)

## **Identificação de cartão de crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId})

**Visão Geral**

Obtém dados relativos ao conjunto de informações referentes à identificação da conta de pagamento pós-paga

Tags: [Bandeira (Credit Card Network)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioBandeira), [Cartão Múltiplo (Multiple CreditCard)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCartaoMultiplo), [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ) e [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga).

  
Visão de alto de nível das estruturas de dados

![TLD\_CreditCardAccount\_Identification-a9737a16.png](images/TLD_CreditCardAccount_Identification-a9737a16.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Identification-c203839a.png](images/DER_CreditCardAccount_Identification-c203839a.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditCardsGetAccountsCreditCardAccountId_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_identification.csv)

##   
**Limites de cartão de crédito**: ( GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/limits)

**Visão Geral**

Obtém dados dos limites: de Crédito Total e por Modalidade de Crédito relativos à conta de pagamento pós-paga.

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga), [Empréstimo Cartão Consignado (Payroll Loan)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEmprestimoCartaoConsignado) e [Limite Flexível (Flexible Limit)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioLimiteFlexivel).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Limits-da0b15b9.png](images/TLD_CreditCardAccount_Limits-da0b15b9.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Limits-a61a5c76.png](images/DER_CreditCardAccount_Limits-a61a5c76.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditCardsGetAccountsCreditCardAccountIdLimits_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_limits.csv)

## **Transações de cartão de crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/transactions)

**Visão Geral**

Obtém dados das transações relativas à conta de pagamento pós-paga.

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga), [Crédito Rotativo (Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCreditoRotativo) e [MCC (Merchant Category Code)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioMCC).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Transactions-30cd2d1e.png](images/TLD_CreditCardAccount_Transactions-30cd2d1e.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Transactions-3ec790c3.png](images/DER_CreditCardAccount_Transactions-3ec790c3.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditCardsGetAccountsCreditCardAccountIdTransactions_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_transactions.csv)

## **Transações de cartão de crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/transactions-current)

**Visão Geral**

Obtém dados das transações relativas à conta de pagamento pós-paga.

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga), [Crédito Rotativo (Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCreditoRotativo) e [MCC (Merchant Category Code)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioMCC).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Transactions-30cd2d1e.png](images/TLD_CreditCardAccount_Transactions-30cd2d1e.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Transactions-3ec790c3.png](images/DER_CreditCardAccount_Transactions-3ec790c3.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccountsAccountIdTransactionsCurrent_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_transactions.csv)

##   
**Fatura de Cartão de Crédito**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/bills)

**Visão Geral**

Obtém dados referentes à fatura da conta de pagamento pós-paga.

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga), [Crédito Rotativo (Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCreditoRotativo) e [Fatura (Bill)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioFatura).

Visão de alto de nível das estruturas de dados

![TLD\_CreditCardAccount\_Bill-18fa37a9.png](images/TLD_CreditCardAccount_Bill-18fa37a9.png)

DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Bill-eafe4a52.png](images/DER_CreditCardAccount_Bill-eafe4a52.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditCardsGetAccountsCreditCardAccountIdBills_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_bill.csv)

## **Transações de cartão de crédito por fatura**: (GET /credit-cards-accounts/v2/accounts/{creditCardAccountId}/bills/{billId}/transactions)

**Visão Geral**

Obtém a lista de transações da conta identificada por creditCardAccountId e billId.

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Conta de pagamento pós-paga (Credit Card)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioContaPagamentoPosPaga), [Crédito Rotativo (Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCreditoRotativo) e [MCC (Merchant Category Code)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioMCC).

**Visão de alto de nível das estruturas de dados**

![TLD\_CreditCardAccount\_Transactions-30cd2d1e.png](images/TLD_CreditCardAccount_Transactions-30cd2d1e.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_CreditCardAccount-62b49dec.png](images/DER_CreditCardAccount-62b49dec.png)

-   DER Lógico
    

![DER\_CreditCardAccount\_Transactions-3ec790c3.png](images/DER_CreditCardAccount_Transactions-3ec790c3.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-creditCardsGetAccountsCreditCardAccountIdBillsBillIdTransactions_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_credit_cards_accounts_transactions.csv)
