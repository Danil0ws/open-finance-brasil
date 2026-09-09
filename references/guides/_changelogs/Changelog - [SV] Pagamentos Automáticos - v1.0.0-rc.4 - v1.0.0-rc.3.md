# Changelog - [SV] Pagamentos Automáticos - v1.0.0-rc.4 - v1.0.0-rc.3

**A implementação e certificação do Pix Automático está pausada no momento. O produto Transferência Inteligentes (Sweeping Accounts) continua disponível para implementação e certificação.**

  

## POST /pix/recurring-payment

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido obrigatóriedade no campo 'ibgeTownCode'

Remoção

required

post/requestBody/data/riskSignals/automatic

Alterado - "description"

Alteração

Representa a coleta de sinais de risco com a presença do usuário \[Restrição\] Obrigatório de ser enviado quando a transação não oc...

Representa a coleta de sinais de risco sem a presença do usuário \[Restrição\] Obrigatório de ser enviado quando a transação não oc...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

Removido obrigatóriedade no campo 'ibgeTownCode'

Remoção

required

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido obrigatóriedade no campo 'ibgeTownCode'

Remoção

required

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido obrigatóriedade no campo 'ibgeTownCode'

Remoção

required
