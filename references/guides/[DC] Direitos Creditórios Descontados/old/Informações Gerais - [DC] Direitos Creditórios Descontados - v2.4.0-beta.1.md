# Informações Gerais - [DC] Direitos Creditórios Descontados - v2.4.0-beta.1

Visão Geral

A API Invoice-financings viabiliza o compartilhamento de informações das Operações de Crédito do tipo Direitos Creditórios Descontados.

## **Direitos Creditórios Descontados**: (GET /invoice-financings/v2/contracts)

**Visão Geral**

Conjunto de informações de contratos de direitos creditórios descontados mantidos pelo cliente na instituição transmissora e para os quais ele tenha fornecido consentimento

Tags: Direito Creditório Descontado (Invoice Financing) e Identificador padronizado da operação de crédito – Ipoc Code.

**Visão de alto de nível das estruturas de dados**

![TLD\_InvoiceFinancings\_List-36daf724.png](images/TLD_InvoiceFinancings_List-36daf724.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_InvoiceFinancings\_List\_Conceitual-cbb2adbb.png](images/DER_InvoiceFinancings_List_Conceitual-cbb2adbb.png)

-   DER Lógico
    

![DER\_InvoiceFinancings\_List-c771a67f.png](images/DER_InvoiceFinancings_List-c771a67f.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/invoiceFinancingsGetContracts_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_invoiceFinancingsGetContracts_v2.4.0.csv)

## **Direitos Creditórios Descontados - Contrato**: (GET /invoice-financings/v2/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Direitos Creditórios Descontados

Tags: Custo Efetivo Total (CET), Direito Creditório Descontado (Invoice Financing), Encargo (Charge), Ente Consignante (CnpjConsignee), Identificador padronizado da operação de crédito – Ipoc Code, Indexador (Indexer), Tarifa (Fee), Taxa Efetiva (EffectiveTax) e Taxa nominal (NominalTax).

**Visão de alto de nível das estruturas de dados**

![TLD\_InvoiceFinancings\_Contract-c63c2a6b.png](images/TLD_InvoiceFinancings_Contract-c63c2a6b.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_InvoiceFinancings-11ff0d5b.png](images/DER_InvoiceFinancings-11ff0d5b.png)

-   DER Lógico
    

![DER\_InvoiceFinancings\_Contract-c0c084b4.png](images/DER_InvoiceFinancings_Contract-c0c084b4.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/invoiceFinancingsGetContractsContractId_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_invoiceFinancingsGetContractsContractId_v2.4.0.csv)

## **Direitos Creditórios Descontados - Garantias do Contrato**: (GET /invoice-financings/v2/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Direitos Creditórios Descontados contratada

Tags: Direito Creditório Descontado (Invoice Financing) e Garantia (Warranty).

**Visão de alto de nível das estruturas de dados**

![TLD\_InvoiceFinancings\_Warranties-09b45d1c.png](images/TLD_InvoiceFinancings_Warranties-09b45d1c.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_InvoiceFinancings-11ff0d5b.png](images/DER_InvoiceFinancings-11ff0d5b.png)

-   DER Lógico
    

![DER\_InvoiceFinancings\_Warranties-f69e122e.png](images/DER_InvoiceFinancings_Warranties-f69e122e.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/invoiceFinancingsGetContractsContractIdWarranties_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_invoiceFinancingsGetContractsContractIdWarranties_v2.4.0.csv)

## **Direitos Creditórios Descontados - Pagamentos do Contrato**: (GET /invoice-financings/v2/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Direitos Creditórios Descontados contratadas

Tags: Direito Creditório Descontado (Invoice Financing), Encargo (Charge), Saldo Devedor (Outstanding Balance) e Tarifa (Fee).

**Visão de alto de nível das estruturas de dados**

![TLD\_InvoiceFinancings\_Payments-b8984bfa.png](images/TLD_InvoiceFinancings_Payments-b8984bfa.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_InvoiceFinancings-11ff0d5b.png](images/DER_InvoiceFinancings-11ff0d5b.png)

-   DER Lógico
    

![DER\_InvoiceFinancings\_Payments-98fc0ede.png](images/DER_InvoiceFinancings_Payments-98fc0ede.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/invoiceFinancingsGetContractsContractIdPayments_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_invoiceFinancingsGetContractsContractIdPayments_v2.4.0.csv)

##   
**Direitos Creditórios Descontados - Parcelas do Contrato**: (GET /invoice-financings/v2/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Direitos Creditórios Descontados contratadas

Tags: Direito Creditório Descontado (Invoice Financing).

**Visão de alto de nível das estruturas de dados**

![TLD\_InvoiceFinancings\_Instalments-77a8dcb2.png](images/TLD_InvoiceFinancings_Instalments-77a8dcb2.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_InvoiceFinancings-11ff0d5b.png](images/DER_InvoiceFinancings-11ff0d5b.png)

-   DER Lógico
    

![DER\_InvoiceFinancings\_Instalments-cfaf8413.png](images/DER_InvoiceFinancings_Instalments-cfaf8413.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/invoiceFinancingsGetContractsContractIdScheduledInstalments_v2.4.0.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_invoiceFinancingsGetContractsContractIdScheduledInstalments_v2.4.0.csv)
