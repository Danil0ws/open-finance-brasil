# Changelog - [DC] Empréstimos - v2.5.0 - v2.4.0

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

get/responses/200/data/items/properties

Adicionado obrigatóriedade no campo 'productSubTypeCategory'

Adição

required

get/responses/200/data/items/properties

Adicionado - "productSubTypeCategory"

Adição

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

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado obrigatóriedade no campo 'productSubTypeCategory'

Adição

required

get/responses/200/data/properties

Adicionado - "productSubTypeCategory"

Adição

get/responses/200/data/properties

Adicionado - "hasInsuranceContracted"

Adição

get/responses/200/data/properties

Adicionado - "nextInstalmentAmount"

Adição

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

get/responses/200/data/contractAmount

Alterado - "description"

Alteração

Valor contratado da operação. Expresso em valor monetário com no mínimo 2 casas e no máximo 4 casas decimais. Nos casos em que não...

Valor contratado da operação. Não incluir valores de taxas, tarifas, encargos e seguros. Expresso em valor monetário com no mínim...

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

Data de vencimento Final da operação. Especificação RFC-3339. Informação deve ser enviada caso ela exista.

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

get/responses/200/data/interestRates/items/properties

Removido obrigatóriedade no campo 'preFixedRate'

Remoção

required

get/responses/200/data/interestRates/items/properties

Removido obrigatóriedade no campo 'postFixedRate'

Remoção

required

get/responses/200/data/interestRates/items/additionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/interestRates/items/postFixedRate

Alterado - "description"

Alteração

Taxa pós fixada aplicada sob o contrato da modalidade crédito. p.ex. 0.0045 .O preenchimento deve respeitar as 6 casas decimais, m...

Taxa pós fixada aplicada sob o contrato da modalidade crédito. p.ex. 0.0045 .O preenchimento deve respeitar as 6 casas decimais, m...

get/responses/200/data/interestRates/items/preFixedRate

Alterado - "description"

Alteração

Taxa pré fixada aplicada sob o contrato da modalidade crédito. p.ex. 0.014500. O preenchimento deve respeitar as 6 casas decimais,...

Taxa pré fixada aplicada sob o contrato da modalidade crédito. p.ex. 0.014500. O preenchimento deve respeitar as 6 casas decimais,...

get/responses/200/data/interestRates/items/referentialRateIndexerAdditionalInfo

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/interestRates/items/referentialRateIndexerSubType

Alterado - "description"

Alteração

"Sub tipos de taxas referenciais ou indexadores, conforme Anexo 5: Taxa referencial ou Indexador (Indx), do Documento 3040"

"Sub tipos de taxas referenciais ou indexadores, conforme Anexo 5: Taxa referencial ou Indexador (Indx), do Documento 3040. \[Rest...

get/responses/200/data/productName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

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

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

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

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /contracts/{contractId}/payments

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

get/responses/200/data/properties

Adicionado - "lastUpdatedContractOutstandingBalance"

Adição

get/responses/200/data/properties

Adicionado - "totalRemainingAmount"

Adição

get/responses/200/data/contractOutstandingBalance

Alterado - "description"

Alteração

Valor necessário para o cliente liquidar a dívida.

Valor necessário para o cliente liquidar a dívida, ou seja, este campo deve ser preenchido com o saldo devedor atualizado descrito...

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

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

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

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

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

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

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

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção

## GET /contracts/{contractId}/warranties

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/400/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/400/meta/properties

Removido - "totalRecords"

Remoção

get/responses/400/meta/properties

Removido - "totalPages"

Remoção

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/401/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/401/meta/properties

Removido - "totalRecords"

Remoção

get/responses/401/meta/properties

Removido - "totalPages"

Remoção

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/403/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/403/meta/properties

Removido - "totalRecords"

Remoção

get/responses/403/meta/properties

Removido - "totalPages"

Remoção

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/404/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/404/meta/properties

Removido - "totalRecords"

Remoção

get/responses/404/meta/properties

Removido - "totalPages"

Remoção

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/405/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/405/meta/properties

Removido - "totalRecords"

Remoção

get/responses/405/meta/properties

Removido - "totalPages"

Remoção

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/406/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/406/meta/properties

Removido - "totalRecords"

Remoção

get/responses/406/meta/properties

Removido - "totalPages"

Remoção

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/422/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/422/meta/properties

Removido - "totalRecords"

Remoção

get/responses/422/meta/properties

Removido - "totalPages"

Remoção

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/423/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/423/meta/properties

Removido - "totalRecords"

Remoção

get/responses/423/meta/properties

Removido - "totalPages"

Remoção

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/429/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/429/meta/properties

Removido - "totalRecords"

Remoção

get/responses/429/meta/properties

Removido - "totalPages"

Remoção

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/500/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/500/meta/properties

Removido - "totalRecords"

Remoção

get/responses/500/meta/properties

Removido - "totalPages"

Remoção

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/504/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/504/meta/properties

Removido - "totalRecords"

Remoção

get/responses/504/meta/properties

Removido - "totalPages"

Remoção

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/529/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/529/meta/properties

Removido - "totalRecords"

Remoção

get/responses/529/meta/properties

Removido - "totalPages"

Remoção

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalRecords'

Remoção

required

get/responses/default/meta/properties

Removido obrigatóriedade no campo 'totalPages'

Remoção

required

get/responses/default/meta/properties

Removido - "totalRecords"

Remoção

get/responses/default/meta/properties

Removido - "totalPages"

Remoção
