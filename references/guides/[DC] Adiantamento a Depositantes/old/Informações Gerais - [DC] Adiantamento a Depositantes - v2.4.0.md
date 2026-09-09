# Informações Gerais - [DC] Adiantamento a Depositantes - v2.4.0

17

**Visão Geral**

A API Unarranged-accounts-overdraft viabiliza o compartilhamento de informações das Operações de Crédito do tipo Adiantamento a Depositantes.

## **Adiantamento a Depositantes**: (GET /unarranged-accounts-overdraft/v2/contracts)

**Visão Geral**

Obtém dados referentes à operação de crédito de Adiantamento a Depositantes

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Adiantamento-a-Depositante-\(Unarranged-Account-Overdraft\)) e [Identificador padronizado da operação de crédito – Ipoc Code](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Identificador-Padronizado-da-Opera%C3%A7%C3%A3o-de-Cr%C3%A9dito-%E2%80%93-Ipoc-Code).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_List-11e82848.png](images/TLD_UnarrangedAccountsOverdraft_List-11e82848.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccOverdraft\_List\_Conceitual-7cb78532.png](images/DER_UnarrangedAccOverdraft_List_Conceitual-7cb78532.png)

-   DER Lógico
    

![DER\_UnarrangedAccountOverdraft\_List-62c962b2.png](images/DER_UnarrangedAccountOverdraft_List-62c962b2.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/unarrangedAccountsOverdraftGetContracts_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_unarrangedAccountsOverdraftGetContracts_v2.4.0.csv)

##   
**Adiantamento a Depositantes - Contrato**: (GET /unarranged-accounts-overdraft/v2/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Adiantamento a Depositantes

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Adiantamento-a-Depositante-\(Unarranged-Account-Overdraft\)), [Custo Efetivo Total (CET)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Custo-Efetivo-Total-\(CET\)), [Encargo (Charge)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Encargo-\(Charge\)), [Identificador padronizado da operação de crédito – Ipoc Code](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Identificador-Padronizado-da-Opera%C3%A7%C3%A3o-de-Cr%C3%A9dito-%E2%80%93-Ipoc-Code), [Indexador (Indexer)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Indexador-\(Indexer\)), [Sistema de Amortização Constante (SAC)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Sistema-de-Amortiza%C3%A7%C3%A3o-Constante-\(SAC\)), [Sistema Francês de Amortização (Price)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Sistema-Franc%C3%AAs-de-Amortiza%C3%A7%C3%A3o-\(Price\)), [Tarifa (Fee)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Tarifa-\(Fee\)), [Taxa Efetiva (EffectiveTax)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Taxa-Efetiva-\(EffectiveTax\)) e [Taxa nominal (NominalTax)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Taxa-nominal-\(NominalTax\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Contract-b511db56.png](images/TLD_UnarrangedAccountsOverdraft_Contract-b511db56.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Contract-cf6c3b8d.png](images/DER_UnarrangedAccountsOverdraft_Contract-cf6c3b8d.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/unarrangedAccountsOverdraftGetContractsContractId_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_unarrangedAccountsOverdraftGetContractsContractId_v2.4.0.csv)

## **Adiantamento a Depositantes - Garantias do Contrato**: (GET /unarranged-accounts-overdraft/v2/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Adiantamento a Depositantes contratada

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Adiantamento-a-Depositante-\(Unarranged-Account-Overdraft\)) e [Garantia (Warranty)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Garantia-\(Warranty\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Warranties-9db6e796.png](images/TLD_UnarrangedAccountsOverdraft_Warranties-9db6e796.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Warranties-9ff37998.png](images/DER_UnarrangedAccountsOverdraft_Warranties-9ff37998.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/unarrangedAccountsOverdraftGetContractsContractIdWarranties_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_unarrangedAccountsOverdraftGetContractsContractIdWarranties_v2.4.0.csv)  

## **Adiantamento a Depositantes - Pagamentos do Contrato**: (GET /unarranged-accounts-overdraft/v2/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Adiantamento a Depositantes contratadas

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Adiantamento-a-Depositante-\(Unarranged-Account-Overdraft\)), [Encargo (Charge)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Encargo-\(Charge\)), [Saldo Devedor (Outstanding Balance)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Saldo-Devedor-\(Outstanding-Balance\)) e [Tarifa (Fee)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Tarifa-\(Fee\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Payments-19ca5a52.png](images/TLD_UnarrangedAccountsOverdraft_Payments-19ca5a52.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Payments-f5bdbe9f.png](images/DER_UnarrangedAccountsOverdraft_Payments-f5bdbe9f.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/unarrangedAccountsOverdraftGetContractsContractIdPayments_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_unarrangedAccountsOverdraftGetContractsContractIdPayments_v2.4.0.csv)

##   
**Adiantamento a Depositantes - Parcelas do Contrato**: (GET /unarranged-accounts-overdraft/v2/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Adiantamento a Depositantes contratadas

Tags: [Adiantamento a Depositante (Unarranged Account Overdraft)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Adiantamento-a-Depositante-\(Unarranged-Account-Overdraft\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_UnarrangedAccountsOverdraft\_Instalments-13550441.png](images/TLD_UnarrangedAccountsOverdraft_Instalments-13550441.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_UnarrangedAccountsOverdraft-1f5fe687.png](images/DER_UnarrangedAccountsOverdraft-1f5fe687.png)

-   DER Lógico
    

![DER\_UnarrangedAccountsOverdraft\_Instalments-92c17364.png](images/DER_UnarrangedAccountsOverdraft_Instalments-92c17364.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/unarrangedAccountsOverdraftGetContractsContractIdScheduledInstalments_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_unarrangedAccountsOverdraftGetContractsContractIdScheduledInstalments_v2.4.0.csv)
