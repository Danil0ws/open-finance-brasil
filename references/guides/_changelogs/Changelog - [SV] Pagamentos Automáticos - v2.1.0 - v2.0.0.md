# Changelog - [SV] Pagamentos Automáticos - v2.1.0 - v2.0.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "version"

Alteração

2.0.0

2.1.0

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido a obrigatoriedade do campo “creditorAccount”

Remoção

Obrigatório

Condicional

get/responses/200/data/properties/creditorAccount

Alterado - "description"

Alteração

`Objeto que contém a identificação da conta de destino do beneficiário/recebedor.`

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.  
\[Restrição\]  
Caso o pagamento tenha sido criado utilizando versão 2.0.0 ou superior, o retorno desse objeto é obrigatório pela instituição detentora

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido a obrigatoriedade do campo “creditorAccount”

Remoção

Obrigatório

Condicional

get/responses/200/data/properties/creditorAccount

Alterado - "description"

Alteração

`Objeto que contém a identificação da conta de destino do beneficiário/recebedor.`

Objeto que contém a identificação da conta de destino do beneficiário/recebedor.  
\[Restrição\]  
Caso o pagamento tenha sido criado utilizando versão 2.0.0 ou superior, o retorno desse objeto é obrigatório pela instituição detentora
