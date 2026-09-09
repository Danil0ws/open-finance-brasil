# Changelog - [DC] Cartão de Crédito - v2.2.1 - v2.2.0

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de contas de pagamento pós-pagas do Open Finance Brasil – Fase 2.  
API que retorna informações de contas de pagamento pós-paga mantidas nas instituições transmissoras por seus clientes, incluindo dados como denominação, produto, bandeira, limites de crédito, informações sobre transações de pagamento efetuadas e faturas.

Não possui segregação entre pessoa natural e pessoa jurídica.\\  
Requer consentimento do cliente para todos os \`endpoints\`.

\# Orientações  
A \`Role\`  do diretório de participantes relacionada à presente API é a \`DADOS\`.\\  
Para todos os \`endpoints\` desta API é previsto o envio de um \`token\` através do header \`Authorization\`.\\  
Este token deverá estar relacionado ao consentimento (\`consentId\`) mantido na instituição transmissora dos dados, o qual permitirá a pesquisa e retorno, na API em questão, dos  
dados relacionados ao \`consentId\` específico relacionado.\\  
Os dados serão devolvidos na consulta desde que o \`consentId\` relacionado corresponda a um consentimento válido e com o status \`AUTHORISED\`.\\  
É também necessário que o recurso em questão (conta, contrato, etc) esteja disponível na instituição transmissora (ou seja, sem boqueios de qualquer natureza e com todas as autorizações/consentimentos já autorizados).\\  
Além disso as \`permissions\` necessárias deverão ter sido solicitadas quando da criação do consentimento relacionado (\`consentId\`).\\  
Relacionamos a seguir as \`permissions\` necessárias para a consulta de dados em cada \`endpoint\` da presente API.\\  
\### \`/accounts/{creditCardAccountId}/bills\`

-   description:
    
-   Só deve ser informada uma fatura já fechada.
    
-   Qualquer pagamento deve ser contado para a última fatura fechada.
    

\### \`/accounts/{creditCardAccountId}/bills/{billId}/transactions\`

-   description:
    
-   A lista a retornar se refere a transações após base 2/clearing/conciliado
    

\### \`/accounts/{creditCardAccountId}/transactions\`

-   description:
    
-   A lista a retornar se refere a transações após base 2/clearing/conciliado
    

\## Permissions necessárias para a API Credit-cards-accounts

Para cada um dos paths desta API, além dos escopos (\`scopes\`) indicados existem \`permissions\` que deverão ser observadas:

\### \`/accounts\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/bills\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_BILLS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/bills/{billId}/transactions\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_BILLS\_TRANSACTIONS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/limits\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_LIMITS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/transactions\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_TRANSACTIONS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/transactions-current\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_TRANSACTIONS\_READ\*\*
    

\## Data de imutabilidade por tipo de transação  
O identificador de transações de cartão de crédito é de envio obrigatório no Open Finance Brasil. De acordo com o tipo da transação deve haver o envio de um identificador único, estável e imutável, conforme tabela abaixo.  
\`\`\`  
  |-------------------|-------------------------|-----------------------|  
  | Tipo de Transação | Data da Obrigatoriedade | Data da Imutabilidade |  
  |-------------------|-------------------------|-----------------------|  
  | PAGAMENTO         | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | TARIFA            | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | OPERACOES\_CRED    | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | ESTORNO           | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | CASHBACK          | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | OUTROS            | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  \`\`\`

API de contas de pagamento pós-pagas do Open Finance Brasil – Fase 2.  
API que retorna informações de contas de pagamento pós-paga mantidas nas instituições transmissoras por seus clientes, incluindo dados como denominação, produto, bandeira, limites de crédito, informações sobre transações de pagamento efetuadas e faturas.

Não possui segregação entre pessoa natural e pessoa jurídica.\\  
Requer consentimento do cliente para todos os \`endpoints\`.

\# Orientações  
A \`Role\`  do diretório de participantes relacionada à presente API é a \`DADOS\`.\\  
Para todos os \`endpoints\` desta API é previsto o envio de um \`token\` através do header \`Authorization\`.\\  
Este token deverá estar relacionado ao consentimento (\`consentId\`) mantido na instituição transmissora dos dados, o qual permitirá a pesquisa e retorno, na API em questão, dos  
dados relacionados ao \`consentId\` específico relacionado.\\  
Os dados serão devolvidos na consulta desde que o \`consentId\` relacionado corresponda a um consentimento válido e com o status \`AUTHORISED\`.\\  
É também necessário que o recurso em questão (conta, contrato, etc) esteja disponível na instituição transmissora (ou seja, sem boqueios de qualquer natureza e com todas as autorizações/consentimentos já autorizados).\\  
Além disso as \`permissions\` necessárias deverão ter sido solicitadas quando da criação do consentimento relacionado (\`consentId\`).\\  
Relacionamos a seguir as \`permissions\` necessárias para a consulta de dados em cada \`endpoint\` da presente API.\\  
\### \`/accounts/{creditCardAccountId}/bills\`

-   description:
    
-   Só deve ser informada uma fatura já fechada.
    
-   Qualquer pagamento deve ser contado para a última fatura fechada.
    

\### \`/accounts/{creditCardAccountId}/bills/{billId}/transactions\`

-   description:
    
-   A lista a retornar se refere a transações após conciliado
    

\### \`/accounts/{creditCardAccountId}/transactions\`

-   description:
    
-   A lista a retornar se refere a transações após conciliado
    

\## Permissions necessárias para a API Credit-cards-accounts

Para cada um dos paths desta API, além dos escopos (\`scopes\`) indicados existem \`permissions\` que deverão ser observadas:

\### \`/accounts\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/bills\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_BILLS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/bills/{billId}/transactions\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_BILLS\_TRANSACTIONS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/limits\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_LIMITS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/transactions\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_TRANSACTIONS\_READ\*\*
    

\### \`/accounts/{creditCardAccountId}/transactions-current\`

-   permissions:
    
-   GET: \*\*CREDIT\_CARDS\_ACCOUNTS\_TRANSACTIONS\_READ\*\*
    

\## Data de imutabilidade por tipo de transação  
O identificador de transações de cartão de crédito é de envio obrigatório no Open Finance Brasil. De acordo com o tipo da transação deve haver o envio de um identificador único, estável e imutável, conforme tabela abaixo.  
\`\`\`  
  |-------------------|-------------------------|-----------------------|  
  | Tipo de Transação | Data da Obrigatoriedade | Data da Imutabilidade |  
  |-------------------|-------------------------|-----------------------|  
  | PAGAMENTO         | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | TARIFA            | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | OPERACOES\_CRED    | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | ESTORNO           | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | CASHBACK          | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  | OUTROS            | DO                      | Fatura fechada        |  
  |-------------------|-------------------------|-----------------------|  
  \`\`\`

## GET /accounts

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /accounts/{creditCardAccountId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /accounts/{creditCardAccountId}/bills

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /accounts/{creditCardAccountId}/bills/{billId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter a lista de transações da conta de pagamento pós-paga identificada por creditCardAccountId e billId mantida pelo cliente na instituição transmissora.  
A lista a retornar se refere a transações após base 2/clearing/conciliado

Método para obter a lista de transações da conta de pagamento pós-paga identificada por creditCardAccountId e billId mantida pelo cliente na instituição transmissora.  
A lista a retornar se refere a transações após conciliado.

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora original da transação.

Data e hora da transação disponível para os clientes nos canais digitais da instituição. Neste momento, é obrigatório preencher com dados reais com precisão de data, hora e minuto, mesmo que a instituição não exiba para o cliente nesse nível de granularidade, em algumas situações. Dessa forma, os segundos e milissegundos podem ser preenchidos com zero (0), por exemplo: 2024-01-29T11:15:00.000Z.

## GET /accounts/{creditCardAccountId}/limits

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## GET /accounts/{creditCardAccountId}/transactions

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter a lista de transações da conta de pagamento pós-paga identificada por creditCardAccountId mantida pelo cliente na instituição transmissora.  
A lista a retornar se refere a transações após base 2/clearing/conciliado

Método para obter a lista de transações histórica (últimos 12 meses, ou recorte desse período) da conta de pagamento pós-paga identificada por creditCardAccountId mantida pelo cliente na instituição transmissora.  
A lista a retornar se refere a transações após conciliado.

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora original da transação.

Data e hora da transação disponível para os clientes nos canais digitais da instituição. Neste momento, é obrigatório preencher com dados reais com precisão de data, hora e minuto, mesmo que a instituição não exiba para o cliente nesse nível de granularidade, em algumas situações. Dessa forma, os segundos e milissegundos podem ser preenchidos com zero (0), por exemplo: 2024-01-29T11:15:00.000Z.

## GET /accounts/{creditCardAccountId}/transactions-current

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Método para obter a lista de transações recentes (últimos 7 dias) da conta de pagamento pós-paga identificada por creditCardAccountId mantida pelo cliente na instituição transmissora.

Método para obter a lista de transações recentes (últimos 7 dias) da conta de pagamento pós-paga identificada por creditCardAccountId mantida pelo cliente na instituição transmissora.  
A lista a retornar se refere a transações após conciliado.

get/responses/200/data/items/transactionDateTime

Alterado - "description"

Alteração

Data e hora original da transação.

Data e hora da transação disponível para os clientes nos canais digitais da instituição. Neste momento, é obrigatório preencher com dados reais com precisão de data, hora e minuto, mesmo que a instituição não exiba para o cliente nesse nível de granularidade, em algumas situações. Dessa forma, os segundos e milissegundos podem ser preenchidos com zero (0), por exemplo: 2024-01-29T11:15:00.000Z.
