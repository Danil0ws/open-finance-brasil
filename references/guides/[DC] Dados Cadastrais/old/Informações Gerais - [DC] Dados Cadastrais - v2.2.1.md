# Informações Gerais - [DC] Dados Cadastrais -  v2.2.1

22

## **Visão geral**

A API Customers permite a consulta aos dados cadastrais de clientes, incluindo também dados de qualificação e de relacionamento financeiro.

## **Identificação pessoa natural** : (_GET_ /customers/v2/personal/identifications)

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

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/customersGetPersonalIdentifications_v2.2.1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_customersGetPersonalIdentifications_v2.csv)

## **Identificação pessoa jurídica** : (_GET_ /customers/v2/business/identifications)

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

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/customersGetBusinessIdentifications_v2.2.1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_customersGetBusinessIdentifications_v2.csv)

## **Qualificação pessoa natural** : (_GET_ /customers/v2/personal/qualifications)

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

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/customersGetPersonalQualifications_v2.2.1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_customersGetPersonalQualifications_v2.csv)

## **Qualificação pessoa jurídica** : (_GET_ /customers/v2/business/qualifications)

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

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/customersGetBusinessQualifications_v2.2.1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_customersGetBusinessQualifications_v2.csv)

## **Relacionamento pessoa natural** : (_GET_ /customers/v2/personal/financial-relations)

Obtém os registros de relacionamentos com a instituição financeira e de representantes da pessoa natural.

Considera-se relacionamento as informações que permitam conhecer desde quando a pessoa consultada é cliente da instituição, bem como um indicador dos produtos e serviços que ela consome atualmente.

### Visão de alto nível das estruturas de dados

![DadosCadastrais (1).png](images/DadosCadastrais%20-1-.png)

### DER - Diagramas de Entidade e Relacionamento

-   DER Conceitual
    

![DER\_Personal-b3b3472b.png](images/DER_Personal-b3b3472b.png)

-   DER Lógico
    

![DER\_Personal\_FinancialRelation-a515c8c7.png](images/DER_Personal_FinancialRelation-a515c8c7.png)

### Dicionário de dados

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/customersGetPersonalFinancialRelations_v2.2.1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_customersGetPersonalFinancialRelations_v2.csv)

## **Relacionamento pessoa jurídica** : (_GET_ /customers/v2/business/financial-relations)

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

[Fazer download do dicionário de dados](https://openbanking-brasil.github.io/openapi/dictionary/customersGetBusinessFinancialRelations_v2.2.1.csv)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_customersGetBusinessFinancialRelations_v2.csv)

## Tabela descritiva das possibilidades de retorno para a API Dados Cadastrais

**Cenário**​

**API Dados Cadastrais** ​

**Code**​

Sem consentimento​

401 UNAUTHORIZED​

\-​

Com consentimento recusado (REJECTED)​

401 UNAUTHORIZED​

\-​

Com consentimento autorizado (pendente múltipla alçada)​

403 FORBIDDEN​

STATUS\_PENDING\_ AUTHORISATION​

Com consentimento autorizado (aprovado múltipla alçada)​

200 Retorna dados​

\-​

Com consentimento autorizado (aprovado múltipla alçada) – cliente com bloqueio temporário​

403 FORBIDDEN​

STATUS\_TEMPORARY\_ UNAVAILABLE​

Com consentimento autorizado (aprovado múltipla alçada) - cliente encerrou relacionamento​

403 FORBIDDEN​

STATUS\_UNAVAILABLE​

Com consentimento autorizado (recusado múltipla alçada)​

403 FORBIDDEN​

STATUS\_UNAVAILABLE​

Com consentimento revogado ou expirado​

401 UNAUTHORIZED​

\-​
