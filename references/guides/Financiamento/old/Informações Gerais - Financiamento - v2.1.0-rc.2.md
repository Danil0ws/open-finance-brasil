# Informações Gerais - Financiamento - v2.1.0-rc.2

**Visão Geral**

A API Financings viabiliza o compartilhamento de informações das Operações de Crédito do tipo Financiamento.

##   
**Financiamentos**: (GET /financings/v2/contracts)

**Visão Geral**

Obtém dados referentes à operação de crédito de Financiamentos

Tags: [CNPJ (CNPJ Number)](data/references/guides/Gloss.md)), [CPF - Cadastro de Pessoa Física (CPF Number)](data/references/guides/Gloss.md)) e [Financiamento (Financing)](data/references/guides/Gloss.md)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_List-317a9f55.png](images/TLD_Financings_List-317a9f55.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings\_List\_Conceitual-78a6e363.png](images/DER_Financings_List_Conceitual-78a6e363.png)

-   DER Lógico
    

![DER\_Financings\_List-c771a67f.png](images/DER_Financings_List-c771a67f.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-financingsGetContracts_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/10059794/financingsGetContracts.csv?api=v2&download=true)

##   
**Financiamentos - Contrato**: (GET /financings/v2/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Financiamentos

Tags: [CNPJ (CNPJ Number)](data/references/guides/Gloss.md)), [CPF - Cadastro de Pessoa Física (CPF Number)](data/references/guides/Gloss.md)), [Custo Efetivo Total (CET)](data/references/guides/Gloss.md)), [Encargo (Charge)](data/references/guides/Gloss.md)), [Ente Consignante (CnpjConsignee)](data/references/guides/Gloss.md)), [Financiamento (Financing)](data/references/guides/Gloss.md)), [Identificador Padronizado da Operação de Crédito – Ipoc Code](data/references/guides/Gloss.md), [Indexador (Indexer)](data/references/guides/Gloss.md)), [Sistema de Amortização Constante (SAC)](data/references/guides/Gloss.md)), [Sistema de Amortização Misto (SAM)](data/references/guides/Gloss.md)), [Sistema Francês de Amortização (Price)](data/references/guides/Gloss.md)), [Tarifa (Fee)](data/references/guides/Gloss.md)), [Taxa Efetiva (EffectiveTax)](data/references/guides/Gloss.md)) e [Taxa nominal (NominalTax)](data/references/guides/Gloss.md)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Contract-28e66d10.png](images/TLD_Financings_Contract-28e66d10.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Contract-2dad086e.png](images/DER_Financings_Contract-2dad086e.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-financingsGetContractsContractId_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/10059794/financingsGetContractsContractId.csv?api=v2&download=true)

## **Financiamentos - Garantias do Contrato**: (GET /financings/v2/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Financiamentos contratada

Tags: [Financiamento (Financing)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230/Gloss+rio#Financiamento-\(Financing\)), [Garantia (Warranty)](data/references/guides/Gloss.md)) e [Sistema de Amortização Misto (SAM)](data/references/guides/Gloss.md)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Warranties-45815cdc.png](images/TLD_Financings_Warranties-45815cdc.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Warranties-d85bb514.png](images/DER_Financings_Warranties-d85bb514.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-financingsGetContractsContractIdWarranties_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/10059794/financingsGetContractsContractIdWarranties.csv?api=v2&download=true)

##   
**Financiamentos - Pagamentos do Contrato**: (GET /financings/v2/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Financiamentos contratadas

Tags: [Encargo (Charge)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Encargo-\(Charge\)), [Financiamento (Financing)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Financiamento-\(Financing\)), [Identificador Padronizado da Operação de Crédito – Ipoc Code](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Identificador-Padronizado-da-Opera%C3%A7%C3%A3o-de-Cr%C3%A9dito-%E2%80%93-Ipoc-Code), [Saldo Devedor (Outstanding Balance)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Saldo-Devedor-\(Outstanding-Balance\)), [Sistema de Amortização Constante (SAC)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Sistema-de-Amortiza%C3%A7%C3%A3o-Constante-\(SAC\)), [Sistema de Amortização Misto (SAM)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Sistema-de-Amortiza%C3%A7%C3%A3o-Misto-\(SAM\)), [Sistema Francês de Amortização (Price)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Sistema-Franc%C3%AAs-de-Amortiza%C3%A7%C3%A3o-\(Price\)) e [Tarifa (Fee)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Tarifa-\(Fee\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Payments-38c034e2.png](images/TLD_Financings_Payments-38c034e2.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Payments-e2f69311.png](images/DER_Financings_Payments-e2f69311.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-financingsGetContractsContractIdPayments_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/10059794/financingsGetContractsContractIdPayments.csv?api=v2&download=true)

##   
**Financiamentos - Parcelas do Contrato**: (GET /financings/v2/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Financiamentos contratadas

Tags: [Financiamento (Financing)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Financiamento-\(Financing\)) e [Prestação Regular (Instalment)](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230#Presta%C3%A7%C3%A3o-Regular-\(Instalment\)).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Instalments-aaa0d467.png](images/TLD_Financings_Instalments-aaa0d467.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Instalments-f7eb2f57.png](images/DER_Financings_Instalments-f7eb2f57.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-financingsGetContractsContractIdScheduledInstalments_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/10059794/financingsGetContractsContractIdScheduledInstalments.csv?api=v2&download=true)
