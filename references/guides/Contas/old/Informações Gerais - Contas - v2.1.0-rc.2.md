# Informações Gerais - Contas - v2.1.0-rc.2

22

## **Visão Geral**

A API Accounts viabiliza o compartilhamento das informações de contas de depósito à vista, contas de poupança e contas de pagamento pré-paga tais como limites, transações e saldos.

## **Lista de contas** : (_GET_ /accounts/v2/accounts)

Obtém a lista de contas consentidas pelo cliente.

Método para obter a lista de contas depósito à vista, poupança e pagamento pré-pagas mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento.

### Visão de alto nível das estruturas de dados

![TLD\_Accounts\_List-3ae2ea95.png](images/TLD_Accounts_List-3ae2ea95.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Lista\_Accounts-ad24ecda.png](images/DER_Lista_Accounts-ad24ecda.png)

-   DER Lógico
    

![DER\_Accounts\_List-e1f46aff.png](images/DER_Accounts_List-e1f46aff.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccounts_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/9797751/accounts.csv?api=v2&download=true)

## **Identificação da conta** : (_GET_ /accounts/v2/accounts/{accountId})

Obtém os dados de identificação da conta mantidos na instituição transmissora.

Essa especificação inclui todos os artefatos relevantes para a Especificação de API sobre a Identificação de uma conta de: depósito à vista, poupança ou de pagamento pré-paga referente às informações transacionais de cliente.

### Visão de alto nível das estruturas de dados

![TLD\_Accounts\_Identification-0eff3ae2.png](images/TLD_Accounts_Identification-0eff3ae2.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Accounts-938055b7.png](images/DER_Accounts-938055b7.png)

-   DER Lógico
    

![DER\_Accounts\_Identification-0f670ea1.png](images/DER_Accounts_Identification-0f670ea1.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccountsAccountId_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/9797751/accounts_accountId.csv?api=v2&download=true)

## **Saldos da conta** : (GET /accounts/v2/accounts/{accountId}/balances)

Obtém os saldos da conta mantidos na instituição transmissora.

Essa especificação inclui todos os artefatos relevantes para a Especificação de API sobre os saldos de uma conta de: depósito à vista, poupança ou de pagamento pré-paga referente às informações transacionais de cliente.

### Visão de alto nível das estruturas de dados

![TLD\_Accounts\_Balances-8e5025a9.png](images/TLD_Accounts_Balances-8e5025a9.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Accounts-938055b7.png](images/DER_Accounts-938055b7.png)

-   DER Lógico
    

![DER\_Accounts\_Balances-a5644351.png](images/DER_Accounts_Balances-a5644351.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccountsAccountIdBalances_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/9797751/accounts_accountId_balances.csv?api=v2&download=true)

## **Transações da conta** : (_GET_ /accounts/v2/accounts/{accountId}/transactions)

Obtém a lista de transações da conta mantidos na instituição transmissora.

Essa especificação inclui todos os artefatos relevantes para a Especificação de API sobre as transações efetivadas e os pagamentos autorizados de uma conta de: depósito à vista, poupança ou de pagamento pré-paga referente às informações transacionais de cliente.

### Visão de alto nível das estruturas de dados

![TLD\_Accounts\_Transactions-21d19863.png](images/TLD_Accounts_Transactions-21d19863.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Accounts-938055b7.png](images/DER_Accounts-938055b7.png)

-   DER Lógico
    

![DER\_Accounts\_Transactions-3f393c02.png](images/DER_Accounts_Transactions-3f393c02.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccountsAccountIdTransactions_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/9797751/accounts_accountId_transactions.csv?api=v2&download=true)

## **Transações da conta** : (_GET_ /accounts/v2/accounts/{accountId}/transactions-current)

Obtém a lista de transações da conta mantidos na instituição transmissora.

Essa especificação inclui todos os artefatos relevantes para a Especificação de API sobre as transações efetivadas e os pagamentos autorizados de uma conta de: depósito à vista, poupança ou de pagamento pré-paga referente às informações transacionais de cliente.

### Visão de alto nível das estruturas de dados

![TLD\_Accounts\_Transactions-21d19863.png](images/TLD_Accounts_Transactions-21d19863.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Accounts-938055b7.png](images/DER_Accounts-938055b7.png)

-   DER Lógico
    

![DER\_Accounts\_Transactions-3f393c02.png](images/DER_Accounts_Transactions-3f393c02.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccountsAccountIdTransactionsCurrent_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/9797751/accounts_accountId_transactions_current.csv?api=v2&download=true)

## **Limites da conta** : (GET /accounts/v2/accounts/{accountId}/overdraft-limits)

Obtém os dados de limite de cheque especial e de adiantamento a depositante da conta mantidos na instituição transmissora.

Essa especificação inclui todos os artefatos relevantes para a Especificação de API sobre os valores utilizado e disponível do limite do Cheque Especial e o valor em excesso (Adiantamento a depositante) de uma conta de depósito à vista, referente às informações transacionais de cliente.

### Visão de alto nível das estruturas de dados

![TLD\_Accounts\_OverdraftLimits-7a1d1486.png](images/TLD_Accounts_OverdraftLimits-7a1d1486.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Accounts-938055b7.png](images/DER_Accounts-938055b7.png)

-   DER Lógico
    

![DER\_Accounts\_OverdraftLimits-7278deb6.png](images/DER_Accounts_OverdraftLimits-7278deb6.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-accountsGetAccountsAccountIdOverdraftLimits_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/9797751/accounts_accountId_overdraft_limits.csv?api=v2&download=true)
