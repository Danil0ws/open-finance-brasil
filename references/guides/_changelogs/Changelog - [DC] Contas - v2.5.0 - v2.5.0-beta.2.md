# Changelog - [DC] Contas - v2.5.0 - v2.5.0-beta.2

## GET /accounts/{accountId}/balances

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/availableAmount/amount

Alterado - "pattern"

Alteração

^\\d{1,15}\\.\\d{2,4}$

^-?\\d{1,15}\\.\\d{2,4}$

get/responses/200/data/availableAmount/amount

Alterado - "maxLength"

Alteração

20

21

## GET /accounts/{accountId}/transactions-current

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/fromBookingDate

Alterado - "description"

Alteração

Data inicial de filtragem. O período máximo utilizado no filtro é de 7 dias inclusive (D-6).    
\[Restrição\] Deve obrigatoriamente ser enviado caso o campo toBookingDate seja informado.  
Caso não seja informado, deve ser assumido o dia atual.  

Data inicial de filtragem. O período máximo utilizado no filtro é de 7 dias no passado, inclusive (D-6), e 12 meses no futuro. A filtragem deve ser feita utilizando o campo \`transactionDateTime\`.

\[Restrição\] Deve obrigatoriamente ser enviado caso o campo toBookingDate seja informado. Caso não seja informado, deve ser assumido o dia atual.  

get/parameters/toBookingDate

Alterado - "description"

Alteração

Data final de filtragem. O período máximo utilizado no filtro é de 7 dias inclusive (D-6).    
\[Restrição\] Deve obrigatoriamente ser enviado caso o campo fromBookingDate seja informado.  
Caso não seja informado, deve ser assumido o dia atual.  

Data final de filtragem. O período máximo utilizado no filtro é de 7 dias no passado, inclusive (D-6), e 12 meses no futuro. A filtragem deve ser feita utilizando o campo \`transactionDateTime\`.

\[Restrição\] Deve obrigatoriamente ser enviado caso o campo fromBookingDate seja informado. Caso não seja informado, deve ser assumido o dia atual.   

get/responses/200/data/items/type/enum

Adicionado - "APLICACAO\_FINANCEIRA"

Adição

## GET /accounts/{accountId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/type/enum

Adicionado - "APLICACAO\_FINANCEIRA"

Adição
