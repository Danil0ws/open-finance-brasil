# Changelog - [SV] Pagamentos Automáticos - v1.0.0-rc.3 - v1.0.0-rc.2

**A implementação e certificação do Pix Automático está pausada no momento. O produto Transferência Inteligentes (Sweeping Accounts) continua disponível para implementação e certificação.**

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

\-

Adicionado texto no header

Adição

6.1.15 Titularidade Inconsistente: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração. Caso a liquidação seja negada pelo PSP Recebedor com erro BE01, cabe a detentora de conta mudar o status do pagamento para RJCT com essa reason (TITULARIDADE\_INCONSISTENTE).

## POST /recurring-consents

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

ost/responses/201/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser tr...

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser tr...

post/responses/201/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser tr...

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser tr...

get/responses/200/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

## PATCH /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/debtorAccount

Alterado - "description"

Alteração

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser tr...

Objeto que contém a identificação da conta de origem do pagador. As informações quanto à conta de origem do pagador poderão ser tr...

patch/responses/200/data/debtorAccount/ibgeTownCode

Alterado - "description"

Alteração

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

Campo utilizado pela iniciadora para cálculo do dia útil de liquidação do pagamento (vide especificação do endToEndId) baseado no ...

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "CONSENTIMENTO\_INVALIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "TITULARIDADE\_INCONSISTENTE"

Adição

enum

get/responses/200/data/items/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...
