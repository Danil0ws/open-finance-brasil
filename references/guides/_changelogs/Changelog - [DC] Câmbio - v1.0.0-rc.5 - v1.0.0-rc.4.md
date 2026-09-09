# Changelog - [DC] Câmbio - v1.0.0-rc.5 - v1.0.0-rc.4

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

\-

Alterado - descrição do header

Alteração

São escopo de compartilhamento as operações de compra e venda de moeda estrangeira de liquidação pronta ou futura, inclusive com adiantamento. Operações de câmbio anuladas não são escopo de exposição, bem como eventos de vinculação de operações. A exposição se dará por cada operação de câmbio contratada pelo cliente.

São escopo de compartilhamento as operações negociadas no mercado primário, pronto (inclusive espécie, cartão pré pago, cartão de débito) e futuro (inclusive ACC, ACE ou trava cambial).

Devem ser compartilhadas as operações contratadas e disponibilizadas nos canais eletrônicos da instituição, mesmo nas situações nas quais a operação ainda não tenha sido registrada junto ao Banco Central. Caso o evento de contratação seja anulado no Sistema de Câmbio, o que significa que a operação foi anulada, então esta operação deixa de ser escopo de exposição. Caso o registro aconteça a operação deve ser complementada com o número de operação registrado e os eventos ocorridos.

Eventos de vinculação de operações não são escopo de exposição.

A exposição se dará por cada operação de câmbio contratada pelo cliente.

## GET /operations

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /operations/{operationId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/localCurrencyAdvancePercentage

Alterado - "description"

Alteração

Percentual do valor de moeda nacional concedido ao cliente antecipadamente. p.ex. 0.014500. O preenchimento deve respeitar as 6 c...

Percentual do valor de moeda estrangeira concedido ao cliente antecipadamente. p.ex. 0.014500. O preenchimento deve respeitar as ...

## GET /operations/{operationId}/events

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/localCurrencyAdvancePercentage

Alterado - "description"

Alteração

Percentual do valor de moeda nacional concedido ao cliente antecipadamente. p.ex. 0.014500. O preenchimento deve respeitar as 6 c...

Percentual do valor de moeda estrangeira concedido ao cliente antecipadamente. p.ex. 0.014500. O preenchimento deve respeitar as ...
