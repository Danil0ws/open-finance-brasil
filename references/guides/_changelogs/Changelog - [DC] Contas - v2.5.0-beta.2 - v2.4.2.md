# Changelog - [DC] Contas - v2.5.0-beta.2 - v2.4.2

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de contas de depósito à vista, contas de poupança e contas pré-pagas do Open Finance Brasil – Fase 2. API que retorna informaç...

API de contas de depósito à vista, contas de poupança e contas pré-pagas do Open Finance Brasil – Fase 2. API que retorna informaç...

paths

Adicionado - "/accounts/{accountId}/reserved-balances"

Adição

## GET /accounts

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/properties

Removido obrigatóriedade no campo 'checkDigit'

Remoção

required

get/responses/200/data/items/checkDigit

Alterado - "description"

Alteração

Dígito da conta

Dígito da conta \[Restrição\] Obrigatoriamente deve ser preenchido quando o campo \`type\` for diferente de conta pré-paga. Nos casos...

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/data/items/companyCnpj

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/items/companyCnpj

Alterado - "description"

Alteração

Número completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde ao número de inscrição no Cadastro de Pessoa...

Registro completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde a representação alfanumérica da inscrição ...

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

## GET /accounts/{accountId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido obrigatóriedade no campo 'checkDigit'

Remoção

required

get/responses/200/data/checkDigit

Alterado - "description"

Alteração

Dígito da conta

Dígito da conta. \[Restrição\] Obrigatoriamente deve ser preenchido quando o campo "type" for diferente de conta pré-paga. Nos cas...

get/responses/200/headers

Adicionado - "x-v"

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

## GET /accounts/{accountId}/balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado - "hasReservedBalance"

Adição

get/responses/200/data/availableAmount

Alterado - "description"

Alteração

Saldo disponível para utilização imediata. No caso de conta de depósito a vista, sem considerar cheque especial e investimentos at...

Saldo disponível para utilização imediata. Não considera cheque especial, investimentos automáticos atrelados a conta e nem reserv...

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/data/availableAmount/amount

Alterado - "pattern"

Alteração

^-?\\d{1,15}\\.\\d{2,4}$

^\\d{1,15}\\.\\d{2,4}$

get/responses/200/data/availableAmount/amount

Alterado - "maxLength"

Alteração

21

20

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

## GET /accounts/{accountId}/overdraft-limits

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers

Adicionado - "x-v"

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

## GET /accounts/{accountId}/transactions-current

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/type/enum

Adicionado - "TRANSFERENCIA\_SALDO\_RESERVADO"

Adição

enum

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/data/items/partieCnpjCpf

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11}|\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/items/properties

Adicionado - "typeAdditionalInfo"

Adição

get

Alterado - "description"

Alteração

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId ma...

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga, identificada por accountId m...

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora original da transação.

Data e hora original da transação que é informada nos canais digitais. Para lançamentos Futuros a data informada deve ser a data p...

get/responses/200/links/first

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

get/responses/200/data/items/properties

Adicionado - "codeISPB"

Adição

get/responses/200/data/items/partieCompeCode

Alterado - "description"

Alteração

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

## GET /accounts/{accountId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/type/enum

Adicionado - "TRANSFERENCIA\_SALDO\_RESERVADO"

Adição

enum

get/responses/200/data/items/partieCnpjCpf

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11}|\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/items/properties

Adicionado - "typeAdditionalInfo"

Adição

get

Alterado - "description"

Alteração

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId ma...

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga, identificada por accountId m...

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora original da transação.

Data e hora original da transação que é informada nos canais digitais. Para lançamentos Futuros a data informada deve ser a data p...

get/responses/200/links/first

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

get/responses/200/data/items/properties

Adicionado - "codeISPB"

Adição

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/data/items/partieCompeCode

Alterado - "description"

Alteração

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...
