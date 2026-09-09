# Changelog - [DC] Empréstimos - v2.5.0 - 2.5.0-beta.1

none

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de informações de operações de empréstimos do Open Finance Brasil – Fase 2. API que retorna informações de operações de crédit...

API de informações de operações de empréstimos do Open Finance Brasil – Fase 2. API que retorna informações de operações de crédit...

## GET /contracts

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/productSubTypeCategory

Alterado - "description"

Alteração

Categoria para classificação específica relacionada com a submodalidade do produto. Atenção: o preenchimento com o enum CREDITO\_PE...

Categoria destinada à classificação específica relacionada à submodalidade do produto. As orientações a seguir devem ser observada...

get/responses/200/data/items/brandName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/items/companyCnpj

Alterado - "pattern"

Alteração

\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/items/companyCnpj

Alterado - "description"

Alteração

Número completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde ao número de inscrição no Cadastro de Pessoa...

Representação alfanumérica completa do CNPJ da instituição responsável pelo contrato de empréstimo afim de identificar a instituiç...

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/amortizationScheduledAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/cnpjConsignee

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/cnpjConsignee

Alterado - "description"

Alteração

CNPJ do consignante (CNPJ corresponde ao número de inscrição no Cadastro de Pessoa Jurídica). Deve-se ter apenas os números do C...

CNPJ do consignante (CNPJ corresponde ao número de inscrição no Cadastro de Pessoa Jurídica). Deve-se ter apenas a representação...

get/responses/200/data/contractDate

Alterado - "description"

Alteração

Data de contratação da operação de crédito. Especificação RFC-3339

Data de contratação da operação de crédito. Especificação RFC-3339. Para produtos rotativos, productSubType \`CHEQUE\_ESPECIAL\` e \`C...

get/responses/200/data/contractedFees/items/feeCode

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/contractedFees/items/feeName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/contractedFinanceCharges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/dueDate

Alterado - "description"

Alteração

Data do último vencimento da operação, seguindo a especificação RFC-3339. Informação deve ser enviada caso ela exista. Especialmen...

Data do último vencimento da operação, seguindo a especificação RFC-3339. Informação deve ser enviada caso ela exista. Especialmen...

get/responses/200/data/instalmentPeriodicityAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/interestRates

Alterado - "description"

Alteração

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade...

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade...

get/responses/200/data/interestRates/items/additionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/interestRates/items/postFixedRate

Alterado - "description"

Alteração

Taxa pós fixada aplicada sob o contrato da modalidade crédito. p.ex. 0.0045 .O preenchimento deve respeitar as 6 casas decimais, m...

Taxa pós fixada aplicada sob o contrato da modalidade crédito. p.ex. 0.0045.O preenchimento deve respeitar as 6 casas decimais, me...

get/responses/200/data/interestRates/items/referentialRateIndexerAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/interestRates/items/taxPeriodicity

Alterado - "description"

Alteração

"Periodicidade da taxa . (Vide Enum) a.m - ao mês a.a. - ao ano"

"Periodicidade da taxa. (Vide Enum) a.m - ao mês a.a. - ao ano"

get/responses/200/data/nextInstalmentAmount

Alterado - "description"

Alteração

Informa o valor da próxima parcela à vencer. Para contratos liquidados, retornar zero, seguindo o pattern. \[Restrição\] O envio...

Informa o valor de face (corresponde ao valor da parcela no vencimento). Para contratos liquidados, retornar zero, seguindo o patt...

get/responses/200/data/productName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/productSubTypeCategory

Alterado - "description"

Alteração

Categoria para classificação específica relacionada com a submodalidade do produto. Atenção: o preenchimento com o enum CREDITO\_PE...

Categoria destinada à classificação específica relacionada à submodalidade do produto. As orientações a seguir devem ser observada...

get/responses/200/data/settlementDate

Alterado - "description"

Alteração

Data de liquidação da operação.

Data de liquidação da operação. Data do cancelamento do contrato para casos em que não há saldo devedor restante. No caso de cance...

get/responses/200/links/properties

Removido - "first"

Remoção

get/responses/200/links/properties

Removido - "prev"

Remoção

get/responses/200/links/properties

Removido - "next"

Remoção

get/responses/200/links/properties

Removido - "last"

Remoção

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

## GET /contracts/{contractId}/payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters

Removido - "page"

Remoção

get/parameters

Removido - "page-size"

Remoção

get/parameters

Removido - "pagination-key"

Remoção

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/lastUpdatedContractOutstandingBalance

Alterado - "description"

Alteração

Data e hora da última atualização do valor do campo contractOutstandingBalance, conforme especificação RFC-3339, formato UTC. \[Res...

Data e hora da última atualização do valor do campo contractOutstandingBalance, conforme especificação RFC-3339, formato UTC. \[R...

get/responses/200/data/properties

Removido - "lastUpdatedcontractOutstandingBalanceDateTime"

Remoção

get/responses/200/data/properties

Adicionado - "lastUpdatedContractOutstandingBalance"

Adição

get/responses/200/data/releases/items/overParcel/charges/items/chargeAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/releases/items/overParcel/fees/items/feeCode

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/releases/items/overParcel/fees/items/feeName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/releases/items/paidAmount

Alterado - "description"

Alteração

Valor do pagamento referente ao contrato da modalidade de crédito consultada. Expresso em valor monetário com no mínimo 2 casas e...

Valor do pagamento referente ao contrato da modalidade de crédito consultada . Expresso em valor monetário com no mínimo 2 casas e...

get/responses/200/data/totalRemainingAmount

Alterado - "description"

Alteração

Valor total que falta para o cliente liquidar o contrato, considerando o somatório total de todas as parcelas a vencer e vencidas,...

Valor total que falta para o cliente liquidar o contrato, considerando o somatório total de todas as parcelas a vencer e vencidas,...

get/responses/200/links/properties

Removido - "first"

Remoção

get/responses/200/links/properties

Removido - "prev"

Remoção

get/responses/200/links/properties

Removido - "next"

Remoção

get/responses/200/links/properties

Removido - "last"

Remoção

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção

## GET /contracts/{contractId}/scheduled-instalments

### Parameter

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters

Removido - "page"

Remoção

get/parameters

Removido - "page-size"

Remoção

get/parameters

Removido - "pagination-key"

Remoção

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/links/properties

Removido - "first"

Remoção

get/responses/200/links/properties

Removido - "prev"

Remoção

get/responses/200/links/properties

Removido - "next"

Remoção

get/responses/200/links/properties

Removido - "last"

Remoção

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/200/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/200/meta/properties

Removido - "totalRecords"

Remoção

get/responses/200/meta/properties

Removido - "totalPages"

Remoção
