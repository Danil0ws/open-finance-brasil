# Informações Gerais - [DC] Empréstimos - v2.5.0-beta.1

**Visão Geral**

A API Loans viabiliza o compartilhamento de informações das Operações de Crédito do tipo Empréstimo.

## **Empréstimos**: (GET /loans/v2/contracts)

**Visão Geral**

Obtém a lista de contratos de empréstimos mantidos pelos clientes da instituição transmissora.

Tags: [CNPJ (CNPJ Number)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#CNPJ-\(CNPJ-Number\)), [Custo Efetivo Total (CET)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Custo-Efetivo-Total-\(CET\)), [Empréstimo (Loan)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Empr%C3%A9stimo-\(Loan\)), [Encargo (Charge)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Encargo-\(Charge\)), [Ente Consignante (CnpjConsignee)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Ente-Consignante-\(CnpjConsignee\)), [Identificador padronizado da operação de crédito – Ipoc Code](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Identificador-Padronizado-da-Opera%C3%A7%C3%A3o-de-Cr%C3%A9dito-%E2%80%93-Ipoc-Code), [Indexador (Indexer)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Indexador-\(Indexer\)), [Sistema de Amortização Constante (SAC)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Sistema-de-Amortiza%C3%A7%C3%A3o-Constante-\(SAC\)), [Sistema Francês de Amortização (Price)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Sistema-Franc%C3%AAs-de-Amortiza%C3%A7%C3%A3o-\(Price\)), [Tarifa (Fee)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Tarifa-\(Fee\)), [Taxa Efetiva (EffectiveTax)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Taxa-Efetiva-\(EffectiveTax\)) e [Taxa nominal (NominalTax)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Taxa-nominal-\(NominalTax\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_List-2dca2a73.png](images/TLD_Loans_List-2dca2a73.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans\_List\_Conceitual-1a77830e.png](images/DER_Loans_List_Conceitual-1a77830e.png)

-   DER Lógico
    

![DER\_Loans\_List\_Logico-b44dc150.png](images/DER_Loans_List_Logico-b44dc150.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/loansGetContracts_v2.5.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/example_loansGetContracts_v2.5.csv)

##   
**Empréstimos - Contrato**: (GET /loans/v2/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Empréstimos

Tags: [CNPJ (CNPJ Number)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#CNPJ-\(CNPJ-Number\)), [Custo Efetivo Total (CET)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Custo-Efetivo-Total-\(CET\)), [Empréstimo (Loan)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Empr%C3%A9stimo-\(Loan\)), [Encargo (Charge)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Encargo-\(Charge\)), [Ente Consignante (CnpjConsignee)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Ente-Consignante-\(CnpjConsignee\)), [Identificador padronizado da operação de crédito – Ipoc Code](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Identificador-Padronizado-da-Opera%C3%A7%C3%A3o-de-Cr%C3%A9dito-%E2%80%93-Ipoc-Code), [Indexador (Indexer)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Indexador-\(Indexer\)), [Sistema de Amortização Constante (SAC)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Sistema-de-Amortiza%C3%A7%C3%A3o-Constante-\(SAC\)), [Sistema Francês de Amortização (Price)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Sistema-Franc%C3%AAs-de-Amortiza%C3%A7%C3%A3o-\(Price\)), [Tarifa (Fee)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Tarifa-\(Fee\)), [Taxa Efetiva (EffectiveTax)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Taxa-Efetiva-\(EffectiveTax\)) e [Taxa nominal (NominalTax)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Taxa-nominal-\(NominalTax\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Contract-fad2d027.png](images/TLD_Loans_Contract-fad2d027.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Contract-a02d96d4.png](images/DER_Loans_Contract-a02d96d4.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/loansGetContractsContractId_v2.5.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/example_loansGetContractsContractId_v2.5.csv)

## **Empréstimos - Garantias do Contrato**: (GET /loans/v2/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Empréstimos contratada

Tags: [Empréstimo (Loan)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Empr%C3%A9stimo-\(Loan\)) e [Garantia (Warranty)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Garantia-\(Warranty\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Warranties-9d79de56.png](images/TLD_Loans_Warranties-9d79de56.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Warranties-fa9fed2b.png](images/DER_Loans_Warranties-fa9fed2b.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/loansGetContractsContractIdWarranties_v2.5.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/example_loansGetContractsContractIdWarranties_v2.5.csv)

## **Empréstimos - Pagamentos do Contrato**: (GET /loans/v2/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Empréstimos contratadas

Tags: [Empréstimo (Loan)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Empr%C3%A9stimo-\(Loan\)), [Encargo (Charge)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Encargo-\(Charge\)), [Saldo Devedor (Outstanding Balance)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Saldo-Devedor-\(Outstanding-Balance\)) e [Tarifa (Fee)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Tarifa-\(Fee\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Payments-d4bed1ea.png](images/TLD_Loans_Payments-d4bed1ea.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![123.png](images/123.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/loansGetContractsContractIdPayments_v2.5.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/example_loansGetContractsContractIdPayments_v2.5.csv)

## **Empréstimos - Parcelas do Contrato**: (GET /loans/v2/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Empréstimos contratadas

Tags: [Empréstimo (Loan)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Empr%C3%A9stimo-\(Loan\)) e [Prestação Regular (Instalment)](https://openfinancebrasil.atlassian.net/wiki/spaces/DraftOF/pages/7996340/Gloss+rio#Presta%C3%A7%C3%A3o-Regular-\(Instalment\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Instalments-6076accf.png](images/TLD_Loans_Instalments-6076accf.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Instalments-a5bde7e6.png](images/DER_Loans_Instalments-a5bde7e6.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/loansGetContractsContractIdScheduledInstalments_v2.5.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/example_loansGetContractsContractIdScheduledInstalments_v2.5.csv)
