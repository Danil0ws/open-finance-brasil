# Changelog - [DC] Contas - v2.2.1 - v2.3.0

none

  

## GET /accounts/{accountId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/compeCode

Alterado - "description"

Alteração

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

## GET /accounts/{accountId}/balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/automaticallyInvestedAmount/amount

Alterado - "pattern"

Alteração

^\\d{1,15}\\.\\d{2,4}$

^-?\\d{1,15}\\.\\d{2,4}$

get/responses/200/data/automaticallyInvestedAmount/amount

Alterado - "maxLength"

Alteração

20

21

## GET /accounts/{accountId}/transactions

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId ma...

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId ma...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/partieCompeCode

Alterado - "description"

Alteração

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

## GET /accounts/{accountId}/transactions-curent

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter a lista de transações recentes (últimos 7 dias) da conta de depósito à vista, poupança ou pagamento pré-paga ide...

Método para obter a lista de transações da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId ma...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/partieCompeCode

Alterado - "description"

Alteração

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

## GET /accounts/{accountId}/overdraft-limits

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter os limites da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId mantida pelo ...

Método para obter os limites da conta de depósito à vista, poupança ou pagamento pré-paga identificada por accountId mantida pelo ...
