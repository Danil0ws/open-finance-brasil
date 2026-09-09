# Informações Gerais - Empréstimos - v2.0.0

**Visão Geral**

A API Loans viabiliza o compartilhamento de informações das Operações de Crédito do tipo Empréstimo.

## **Empréstimos**: (GET /loans/v2/contracts)

**Visão Geral**

Obtém a lista de contratos de empréstimos mantidos pelos clientes da instituição transmissora.

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Custo Efetivo Total (CET)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCET), [Empréstimo (Loan)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEmprestimo), [Encargo (Charge)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEncargo), [Ente Consignante (CnpjConsignee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEnteConsignante), [Identificador padronizado da operação de crédito – Ipoc Code](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIPOC), [Indexador (Indexer)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIndexador), [Sistema de Amortização Constante (SAC)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioSAC), [Sistema Francês de Amortização (Price)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioPrice), [Tarifa (Fee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTarifa), [Taxa Efetiva (EffectiveTax)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTaxaEfetiva) e [Taxa nominal (NominalTax)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTaxaNominal).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_List-2dca2a73.png](images/TLD_Loans_List-2dca2a73.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans\_List\_Conceitual-1a77830e.png](images/DER_Loans_List_Conceitual-1a77830e.png)

-   DER Lógico
    

![DER\_Loans\_List\_Logico-b44dc150.png](images/DER_Loans_List_Logico-b44dc150.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-loansGetContracts_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_loans_contract_list.csv)

##   
**Empréstimos - Contrato**: (GET /loans/v2/contracts/{contractId})

**Visão Geral**

Obtém dados referentes à identificação da operação de crédito de Empréstimos

Tags: [CNPJ (CNPJ Number)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCNPJ), [Custo Efetivo Total (CET)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioCET), [Empréstimo (Loan)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEmprestimo), [Encargo (Charge)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEncargo), [Ente Consignante (CnpjConsignee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEnteConsignante), [Identificador padronizado da operação de crédito – Ipoc Code](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIPOC), [Indexador (Indexer)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioIndexador), [Sistema de Amortização Constante (SAC)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioSAC), [Sistema Francês de Amortização (Price)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioPrice), [Tarifa (Fee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTarifa), [Taxa Efetiva (EffectiveTax)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTaxaEfetiva) e [Taxa nominal (NominalTax)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTaxaNominal).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Contract-fad2d027.png](images/TLD_Loans_Contract-fad2d027.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Contract-a02d96d4.png](images/DER_Loans_Contract-a02d96d4.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-loansGetContractsContractId_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_loans_contract.csv)

## **Empréstimos - Garantias do Contrato**: (GET /loans/v2/contracts/{contractId}/warranties)

**Visão Geral**

Obtém dados referentes às garantias que avalizam a operação de crédito de Empréstimos contratada

Tags: [Empréstimo (Loan)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEmprestimo) e [Garantia (Warranty)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioGarantia).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Warranties-9d79de56.png](images/TLD_Loans_Warranties-9d79de56.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Warranties-fa9fed2b.png](images/DER_Loans_Warranties-fa9fed2b.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-loansGetContractsContractIdWarranties_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_loans_warranties.csv)

## **Empréstimos - Pagamentos do Contrato**: (GET /loans/v2/contracts/{contractId}/payments)

**Visão Geral**

Obtém dados dos pagamentos referentes às operações de crédito de Empréstimos contratadas

Tags: [Empréstimo (Loan)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEmprestimo), [Encargo (Charge)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEncargo), [Saldo Devedor (Outstanding Balance)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioSaldoDevedor) e [Tarifa (Fee)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioTarifa).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Payments-d4bed1ea.png](images/TLD_Loans_Payments-d4bed1ea.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Payments-018c7f0b.png](images/DER_Loans_Payments-018c7f0b.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-loansGetContractsContractIdPayments_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_loans_payments.csv)

## **Empréstimos - Parcelas do Contrato**: (GET /loans/v2/contracts/{contractId}/scheduled-instalments)

**Visão Geral**

Obtém dados referentes às parcelas / prestações da operação de crédito de Empréstimos contratadas

Tags: [Empréstimo (Loan)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioEmprestimo) e [Prestação Regular (Instalment)](https://openbanking-brasil.github.io/areadesenvolvedor/#glossarioPrestacaoRegular).

**Visão de alto de nível das estruturas de dados**

![TLD\_Loans\_Instalments-6076accf.png](images/TLD_Loans_Instalments-6076accf.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![DER\_Loans-14b4a0b8.png](images/DER_Loans-14b4a0b8.png)

-   DER Lógico
    

![DER\_Loans\_Instalments-a5bde7e6.png](images/DER_Loans_Instalments-a5bde7e6.png)

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-loansGetContractsContractIdScheduledInstalments_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/areadesenvolvedor/dictionary/example/examples_loans_scheduled_instalments.csv)
