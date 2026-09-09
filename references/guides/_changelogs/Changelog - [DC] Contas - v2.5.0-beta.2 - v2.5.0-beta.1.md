# Changelog - [DC] Contas - v2.5.0-beta.2 - v2.5.0-beta.1

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

Removido - "/accounts/{accountId}/reserved\_balances"

Remoção

paths

Adicionado - "/accounts/{accountId}/reserved-balances"

Adição

## GET /accounts/{accountId}/balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/hasReservedBalance

Alterado - "description"

Alteração

Informa se o cliente possui um saldo reservado. Caso o cliente possua reservas de saldo ativas, inclusive nos casos de saldo zerad...

Informa se o cliente possui um saldo reservado. Caso o cliente possua reservas de saldo ativas, inclusive nos casos de saldo zerad...

## GET /accounts/{accountId}/transactions-current

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/codeISPB

Alterado - "pattern"

Alteração

^\\d{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/items/codeISPB

Alterado - "description"

Alteração

Código único atribuído pelo Banco Central do Brasil a cada instituição participante do Sistema de Pagamentos. Este campo identifi...

Código único atribuído pelo Banco Central do Brasil a cada instituição participante do Sistema de Pagamentos. Este campo identifi...

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

get/responses/200/data/items/codeISPB

Alterado - "pattern"

Alteração

^\\d{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/items/codeISPB

Alterado - "description"

Alteração

Código único atribuído pelo Banco Central do Brasil a cada instituição participante do Sistema de Pagamentos. Este campo identifi...

Código único atribuído pelo Banco Central do Brasil a cada instituição participante do Sistema de Pagamentos. Este campo identifi...

get/responses/200/data/items/partieCompeCode

Alterado - "description"

Alteração

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...

Código identificador atribuído pelo Banco Central do Brasil às instituições participantes do STR (Sistema de Transferência de rese...
