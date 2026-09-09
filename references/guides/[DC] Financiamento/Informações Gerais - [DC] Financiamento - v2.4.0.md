# Informações Gerais - [DC] Financiamento - v2.4.0

**Visão Geral**

A API Financings viabiliza o compartilhamento de informações das Operações de Crédito do tipo Financiamento.

##   
**Financiamentos**: (GET /financings/v2/contracts)

**Visão Geral**

Obtém dados referentes à operação de crédito de Financiamentos

Tags: CNPJ (CNPJ Number), CPF - Cadastro de Pessoa Física (CPF Number) e Financiamento (Financing).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_List-317a9f55.png](images/TLD_Financings_List-317a9f55.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings\_List\_Conceitual-78a6e363.png](images/DER_Financings_List_Conceitual-78a6e363.png)

-   DER Lógico
    

![DER\_Financings\_List-c771a67f.png](images/DER_Financings_List-c771a67f.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/financingsGetContracts_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_financingsGetContracts_v2.4.0.csv)

##   
**Financiamentos - Contrato**: (GET /financings/v2/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Financiamentos

Tags: CNPJ (CNPJ Number), CPF - Cadastro de Pessoa Física (CPF Number) , Custo Efetivo Total (CET), Encargo (Charge), Ente Consignante (CnpjConsignee), Financiamento (Financing), Identificador Padronizado da Operação de Crédito – Ipoc Code, Indexador (Indexer), Sistema de Amortização Constante (SAC), Sistema de Amortização Misto (SAM), Sistema Francês de Amortização (Price), Tarifa (Fee), Taxa Efetiva (EffectiveTax) e Taxa nominal (NominalTax).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Contract-28e66d10.png](images/TLD_Financings_Contract-28e66d10.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Contract-2dad086e.png](images/DER_Financings_Contract-2dad086e.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/financingsGetContractsContractId_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_financingsGetContractsContractId_v2.4.0.csv)

## **Financiamentos - Garantias do Contrato**: (GET /financings/v2/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Financiamentos contratada

Tags: Financiamento (Financing), Garantia (Warranty) e Sistema de Amortização Misto (SAM).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Warranties-45815cdc.png](images/TLD_Financings_Warranties-45815cdc.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Warranties-d85bb514.png](images/DER_Financings_Warranties-d85bb514.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/financingsGetContractsContractIdWarranties_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_financingsGetContractsContractIdWarranties_v2.4.0.csv)

##   
**Financiamentos - Pagamentos do Contrato**: (GET /financings/v2/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Financiamentos contratadas

Tags: Encargo (Charge), Financiamento (Financing), Identificador Padronizado da Operação de Crédito – Ipoc Code, Saldo Devedor (Outstanding Balance), Sistema de Amortização Constante (SAC), Sistema de Amortização Misto (SAM), Sistema Francês de Amortização (Price) e Tarifa (Fee).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Payments-38c034e2.png](images/TLD_Financings_Payments-38c034e2.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Payments-e2f69311.png](images/DER_Financings_Payments-e2f69311.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/financingsGetContractsContractIdPayments_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_financingsGetContractsContractIdPayments_v2.4.0.csv)

##   
**Financiamentos - Parcelas do Contrato**: (GET /financings/v2/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Financiamentos contratadas

Tags: Financiamento (Financing) e Prestação Regular (Instalment).

**Visão de alto de nível das estruturas de dados**

![TLD\_Financings\_Instalments-aaa0d467.png](images/TLD_Financings_Instalments-aaa0d467.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Financings-d24aedd7.png](images/DER_Financings-d24aedd7.png)

-   DER Lógico
    

![DER\_Financings\_Instalments-f7eb2f57.png](images/DER_Financings_Instalments-f7eb2f57.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/financingsGetContractsContractIdScheduledInstalments_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_financingsGetContractsContractIdScheduledInstalments_v2.4.0.csv)
