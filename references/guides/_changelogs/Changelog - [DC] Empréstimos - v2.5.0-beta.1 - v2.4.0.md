# Changelog - [DC] Empréstimos - v2.5.0-beta.1 - v2.4.0

none

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

## GET /contracts/{contractId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/dueDate

Alterado - "description"

Alteração

Data de vencimento Final da operação. Especificação RFC-3339. Informação deve ser enviada caso ela exista.

Data do último vencimento da operação, seguindo a especificação RFC-3339. Informação deve ser enviada caso ela exista. Especialmen...

get/responses/200/data/interestRates

Alterado - "description"

Alteração

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade...

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade...

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

get/responses/200/data/interestRates/items/properties

Removido obrigatóriedade no campo 'preFixedRate'

Remoção

required

get/responses/200/data/interestRates/items/properties

Removido obrigatóriedade no campo 'postFixedRate'

Remoção

required

get/responses/200/data/interestRates/items/referentialRateIndexerSubType

Alterado - "description"

Alteração

"Sub tipos de taxas referenciais ou indexadores, conforme Anexo 5: Taxa referencial ou Indexador (Indx), do Documento 3040"

get/responses/200/data/properties

Adicionado - "hasInsuranceContracted"

Adição

get/responses/200/data/properties

Adicionado obrigatóriedade no campo 'productSubTypeCategory'

Adição

required

get/responses/200/data/properties

Adicionado - "productSubTypeCategory"

Adição

get/responses/200/data/properties

Adicionado - "nextInstalmentAmount"

Adição

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/links/first

Alterado - "format"

Alteração

uri

url

get/responses/200/links/first

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/last

Alterado - "format"

Alteração

uri

url

get/responses/200/links/last

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/next

Alterado - "format"

Alteração

uri

url

get/responses/200/links/next

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

get/responses/200/links/prev

Alterado - "format"

Alteração

uri

url

get/responses/200/links/prev

Removido - "pattern"

Remoção

^(https:\\/\\/)?(www\\.)?\[-a-zA-Z0-9@:%.\_\\+~#=\]{2,256}\\.\[a-z\]{2,6}\\b(\[-a-zA-Z0-9@:%\_\\+.~#?&\\/\\/=\]\*)$

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

get/responses/200/data/contractAmount

Alterado - "description"

Alteração

Valor contratado da operação. Expresso em valor monetário com no mínimo 2 casas e no máximo 4 casas decimais. Nos casos em que não houver este valor explícito no contrato do produto, enviar como 0.00

Valor contratado da operação. Não incluir valores de taxas, tarifas, encargos e seguros.  
Expresso em valor monetário com no mínimo 2 casas e no máximo 4 casas decimais.  
Nos casos em que não houver este valor explícito no contrato do produto, enviar como 0.00

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

get/responses/200/data/interestRates

Alterado - "description"

Alteração

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade...

Objeto que traz o conjunto de informações necessárias para demonstrar a composição das taxas de juros remuneratórios da Modalidade…

## GET /contracts/{contractId}/payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado - "lastUpdatedcontractOutstandingBalanceDateTime"

Adição

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

get/responses/200/data/contractOutstandingBalance

Alterado - "description"

Alteração

Valor necessário para o cliente liquidar a dívida.

Valor necessário para o cliente liquidar a dívida, ou seja, este campo deve ser preenchido com o saldo devedor atualizado descrito no DDC (Documento Descritivo de Crédito).  
O valor a liquidar atualizado do dia deve ser ajustado para compartilhamento pela Transmissora até às 10:00 do mesmo dia, especialmente para Crédito Pessoal Clean, escopo de Portabilidade de Crédito, pois este valor é utilizado pela Receptora em papel de Proponente para pagamento à Transmissora em papel de Credora.

get/responses/200/data/properties

Adicionado - "totalRemainingAmount"

Adição

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

## GET /contracts/{contractId}/scheduled-instalments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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

## GET /contracts/{contractId}/warranties

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

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
