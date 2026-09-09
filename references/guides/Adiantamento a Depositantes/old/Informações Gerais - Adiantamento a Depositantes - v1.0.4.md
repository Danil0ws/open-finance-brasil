# Informações Gerais - Adiantamento a Depositantes - v1.0.4

17

**Visão Geral**

A API Unarranged-accounts-overdraft viabiliza o compartilhamento de informações das Operações de Crédito do tipo Adiantamento a Depositantes.

## **Adiantamento a Depositantes**: (GET /unarranged-accounts-overdraft/v1/contracts)

**Visão Geral**

Obtém dados referentes à operação de crédito de Adiantamento a Depositantes

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioAdiantamentoDepositante) e [Identificador padronizado da operação de crédito – Ipoc Code](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIPOC).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_List-11e82848.png](images/TLD_UnarrangedAccountsOverdraft_List-11e82848.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccOverdraft\_List\_Conceitual-7cb78532.png](images/DER_UnarrangedAccOverdraft_List_Conceitual-7cb78532.png)

-   DER Lógico
    

![DER\_UnarrangedAccountOverdraft\_List-62c962b2.png](images/DER_UnarrangedAccountOverdraft_List-62c962b2.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/unarrangedAccountsOverdraftGetContracts_v1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_unarranged_accounts_overdraft_contract_list.csv)

##   
**Adiantamento a Depositantes - Contrato**: (GET /unarranged-accounts-overdraft/v1/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Adiantamento a Depositantes

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioAdiantamentoDepositante), [Custo Efetivo Total (CET)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCET), [Encargo (Charge)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEncargo), [Identificador padronizado da operação de crédito – Ipoc Code](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIPOC), [Indexador (Indexer)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIndexador), [Sistema de Amortização Constante (SAC)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioSAC), [Sistema Francês de Amortização (Price)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioPrice), [Tarifa (Fee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTarifa), [Taxa Efetiva (EffectiveTax)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTaxaEfetiva) e [Taxa nominal (NominalTax)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTaxaNominal).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Contract-b511db56.png](images/TLD_UnarrangedAccountsOverdraft_Contract-b511db56.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Contract-cf6c3b8d.png](images/DER_UnarrangedAccountsOverdraft_Contract-cf6c3b8d.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/unarrangedAccountsOverdraftGetContractsContractId_v1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_unarranged_accounts_overdraft_contract.csv)

## **Adiantamento a Depositantes - Garantias do Contrato**: (GET /unarranged-accounts-overdraft/v1/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Adiantamento a Depositantes contratada

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioAdiantamentoDepositante) e [Garantia (Warranty)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioGarantia).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Warranties-9db6e796.png](images/TLD_UnarrangedAccountsOverdraft_Warranties-9db6e796.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Warranties-9ff37998.png](images/DER_UnarrangedAccountsOverdraft_Warranties-9ff37998.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/unarrangedAccountsOverdraftGetContractsContractIdWarranties_v1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_unarranged_accounts_overdraft_warranties.csv)  

## **Adiantamento a Depositantes - Pagamentos do Contrato**: (GET /unarranged-accounts-overdraft/v1/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Adiantamento a Depositantes contratadas

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioAdiantamentoDepositante), [Encargo (Charge)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEncargo), [Saldo Devedor (Outstanding Balance)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioSaldoDevedor) e [Tarifa (Fee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTarifa).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Payments-19ca5a52.png](images/TLD_UnarrangedAccountsOverdraft_Payments-19ca5a52.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Payments-f5bdbe9f.png](images/DER_UnarrangedAccountsOverdraft_Payments-f5bdbe9f.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/unarrangedAccountsOverdraftGetContractsContractIdPayments_v1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_unarranged_accounts_overdraft_payments.csv)

##   
**Adiantamento a Depositantes - Parcelas do Contrato**: (GET /unarranged-accounts-overdraft/v1/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Adiantamento a Depositantes contratadas

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioAdiantamentoDepositante).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Instalments-13550441.png](images/TLD_UnarrangedAccountsOverdraft_Instalments-13550441.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Instalments-92c17364.png](images/DER_UnarrangedAccountsOverdraft_Instalments-92c17364.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/unarrangedAccountsOverdraftGetContractsContractIdScheduledInstalments_v1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_unarranged_accounts_overdraft_scheduled_instalments.csv)
