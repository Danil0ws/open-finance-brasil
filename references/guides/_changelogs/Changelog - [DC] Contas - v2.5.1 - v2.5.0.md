# Changelog - [DC] Contas - v2.5.1 - v2.5.0

## GET /accounts/{accountId}/reserved-balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter os saldos reservados em produtos caixinhas/reserva

Método para obter os saldos reservados em produtos caixinhas/reserva.

\[RESTRIÇÃO\] Está no escopo de compartilhamento da API Contas: Reservas sem rendimento, como forma se separar dinheiro para gasto futuro, e Reservas com rendimento, mas não atreladas a um investimento associado ao CPF/CNPJ do cliente.

Nos casos em que o produto é ofertado pela transmissora mas o cliente não possui reserva de saldo, a listagem do endpoint reserved-balances deve vir vazia, com status code 200.

Para instituições que não possuam o produto reserva de saldo, deve ser retornado o HTTP Status Code 404 – Not Found, seguindo os padrões de response para as APIs do ecossistema.
