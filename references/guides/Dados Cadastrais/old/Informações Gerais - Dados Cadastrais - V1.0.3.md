# Informações Gerais - Dados Cadastrais - V1.0.3

22

## **Visão geral**

A API Customers permite a consulta aos dados cadastrais de clientes, incluindo também dados de qualificação e de relacionamento financeiro.

## **Identificação pessoa natural** : (_GET_ /customers/v1/personal/identifications)

Obtém os registros de identificação da pessoa natural.

Esta especificação inclui todos os itens relevantes que permitam a ação e o efeito de identificar de forma única a pessoa natural através de seus dados cadastrais.

### Visão de alto nível das estruturas de dados

![TLD\_Personal\_Identification-e45ae8d0.png](images/TLD_Personal_Identification-e45ae8d0.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Personal-b3b3472b.png](images/DER_Personal-b3b3472b.png)

-   DER Lógico
    

![DER\_Personal\_Identification-638481f8.png](images/DER_Personal_Identification-638481f8.png)

### **Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-customersGetPersonalIdentifications_v1.md)

[Fazer download dos exemplos](https://openbankingbrasil.atlassian.net/wiki/download/attachments/6127799/examples_personal_identification.csv?version=1&modificationDate=1630935173381&cacheVersion=1&api=v2&download=true)

## **Identificação pessoa jurídica** : (_GET_ /customers/v1/business/identifications)

Obtém os registros de identificação da pessoa jurídica.

Esta especificação inclui todos os itens relevantes que permitam a ação e o efeito de identificar de forma única a pessoa jurídica através de seus dados cadastrais.

### Visão de alto nível das estruturas de dados

![TLD\_Business\_Identification\_v3-b494d90f.png](images/TLD_Business_Identification_v3-b494d90f.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Business.v1-9078d6c8.png](images/DER_Business.v1-9078d6c8.png)

-   DER Lógico
    

![DER\_Busines\_Identification.v1-65c3e452.png](images/DER_Busines_Identification.v1-65c3e452.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-customersGetBusinessIdentifications_v1.md)

[Fazer download dos exemplos](https://openbankingbrasil.atlassian.net/wiki/download/attachments/6127799/examples_business_identification.csv?version=1&modificationDate=1630935244501&cacheVersion=1&api=v2&download=true)

## **Qualificação pessoa natural** : (_GET_ /customers/v1/personal/qualifications)

Obtém os registros de qualificação da pessoa natural.

Esta especificação inclui todos os itens relevantes, que permitam as instituições apreciar, avaliar, caracterizar e classificar o cliente com a finalidade de conhecer o seu perfil de risco e sua capacidade econômico-financeira.

### Visão de alto nível das estruturas de dados

![TLD\_Personal\_Qualification-35e5512a.png](images/TLD_Personal_Qualification-35e5512a.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Personal-b3b3472b.png](images/DER_Personal-b3b3472b.png)

-   DER Lógico
    

![DER\_Personal\_Qualification-599a52d7.png](images/DER_Personal_Qualification-599a52d7.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-customersGetPersonalQualifications_v1.md)

[Fazer download dos exemplos](https://openbankingbrasil.atlassian.net/wiki/download/attachments/6127799/examples_personal_qualification.csv?version=1&modificationDate=1630935313511&cacheVersion=1&api=v2&download=true)

## **Qualificação pessoa jurídica** : (_GET_ /customers/v1/business/qualifications)

Obtém os registros de qualificação da pessoa jurídica.

Esta especificação inclui todos os itens relevantes, que permitam as instituições apreciar, avaliar, caracterizar e classificar o cliente com a finalidade de conhecer o seu perfil de risco e sua capacidade econômico-financeira.

### Visão de alto nível das estruturas de dados

![TLD\_Business\_Qualification\_v3-b2372f2a.png](images/TLD_Business_Qualification_v3-b2372f2a.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Business.v1-9078d6c8.png](images/DER_Business.v1-9078d6c8.png)

-   DER Lógico
    

![DER\_Business\_Qualification.v1-07c2d32e.png](images/DER_Business_Qualification.v1-07c2d32e.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-customersGetBusinessQualifications_v1.md)

[Fazer download dos exemplos](https://openbankingbrasil.atlassian.net/wiki/download/attachments/6127799/examples_business_qualification.csv?version=1&modificationDate=1630935479511&cacheVersion=1&api=v2&download=true)

## **Relacionamento pessoa natural** : (_GET_ /customers/v1/personal/financial-relations)

Obtém os registros de relacionamentos com a instituição financeira e de representantes da pessoa natural.

Considera-se relacionamento as informações que permitam conhecer desde quando a pessoa consultada é cliente da instituição, bem como um indicador dos produtos e serviços que ela consome atualmente.

### Visão de alto nível das estruturas de dados

![TLD\_Personal\_Financial\_Relation-b682e5ec.png](images/TLD_Personal_Financial_Relation-b682e5ec.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Personal-b3b3472b.png](images/DER_Personal-b3b3472b.png)

-   DER Lógico
    

![DER\_Personal\_FinancialRelation-a515c8c7.png](images/DER_Personal_FinancialRelation-a515c8c7.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-customersGetPersonalFinancialRelations_v1.md)

[Fazer download dos exemplos](https://openbankingbrasil.atlassian.net/wiki/download/attachments/6127799/examples_personal_financial_relation.csv?version=1&modificationDate=1630935683522&cacheVersion=1&api=v2&download=true)

## **Relacionamento pessoa jurídica** : (_GET_ /customers/v1/business/financial-relations)

Obtém os registros de relacionamentos com a instituição financeira e de representantes da pessoa jurídica.

Considera-se relacionamento as informações que permitam conhecer desde quando a pessoa consultada é cliente da instituição, bem como um indicador dos produtos e serviços que ela consome atualmente

### Visão de alto nível das estruturas de dados

![TLD\_Business\_Financial\_Relation\_v3-b682e5ec.png](images/TLD_Business_Financial_Relation_v3-b682e5ec.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Business.v1-9078d6c8.png](images/DER_Business.v1-9078d6c8.png)

-   DER Lógico
    

![DER\_Business\_FinancialRelation.v1-0e82ab78.png](images/DER_Business_FinancialRelation.v1-0e82ab78.png)

### Dicionário de dados

[Fazer download do dicionário de dados](data/references/openapi/dictionary-customersGetBusinessFinancialRelations_v1.md)

[Fazer download dos exemplos](https://openbankingbrasil.atlassian.net/wiki/download/attachments/6127799/examples_business_financial_relation.csv?version=1&modificationDate=1630935734130&cacheVersion=1&api=v2&download=true)
