# Changelog - [DC] Recursos - v3.0.0-rc.1 - v2.1.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API que trata da consulta do status de recursos para o Open Finance Brasil - Fase 2.\\  
Não possui segregação entre pessoa natural e pessoa jurídica.

\# Orientações importantes

-   A API resources lista os recursos vinculados ao consentimento específico, identificado por \`consentId\` e vinculado ao token enviado no header \`Authorization\`.
    
-   Os \`STATUS\` dos recursos listados DEVEM considerar não apenas o consentimento vinculado mas também a disponibilidade do recurso na instituição transmissora dos dados.
    
-   A \`permission\` específica desta API  - \`RESOURCES\_READ\` - DEVE ser solicitada pela instituição receptora na ocasião do pedido de criação do consentimento.
    
-   A consulta à API Resources não é obrigatória por parte das instituições receptoras - esta API foi criada para dar visibilidade da existência de ocorrências que possam impedir o compartilhamento de determinados recursos por parte da instituição transmissora dos dados.
    
-   O identificador do recurso devolvido na API Resources - \`resourceId\` - quando apresentado corresponde ao mesmo identificador designado para o recurso em sua API específica, o seja: o \`resourceId\` corresponde ao \`accountId\` da API accounts, ao \`creditCardAccountId\` da API de conta
    

pós-paga e assim sucessivamente.

\## Status previstos para os recursos listados na API Resources

-   AVAILABLE: indica que o recurso encontra-se disponível e o(s) consentimento(s) associado(s) possui(em) status \`AUTHORISED\`.
    
-   UNAVAILABLE: indica que o recurso não está mais disponível, por exemplo, em caso de uma conta encerrada.
    
-   TEMPORARILY\_UNAVAILABLE: indica que o recurso encontra-se temporariamente indisponível, embora o(s) consentimento(s) associado(s) possua(m) status \`AUTHORISED\`. 
    

Caso de exemplo: conta temporariamente bloqueada por suspeita de fraude.

-   PENDING\_AUTHORISATION: indica a existência de pendências para o compartilhamento do recurso, por exemplo, em caso de alçada dupla, quando é necessário o consentimento de mais de um titular.
    

\## Permissions necessárias para a API Resources  
\### \`/resources\`

-   permissions:
    
-   GET: \*\*RESOURCES\_READ\*\*
    

API que trata da consulta do status de recursos para o Open Finance Brasil - Dados cadastrais e transacionais.\\  
Não possui segregação entre pessoa natural e pessoa jurídica.

\# Orientações importantes

-   A API resources lista os recursos vinculados ao consentimento específico, identificado por \`consentId\` e vinculado ao token enviado no header \`Authorization\`.
    
-   A API Resources somente está disponível para consentimentos que se encontram no status \`AUTHORISED\`.
    
-   Os \`STATUS\` dos recursos listados DEVEM considerar não apenas o consentimento vinculado mas também a disponibilidade do recurso na instituição transmissora dos dados.
    
-   A \`permission\` específica desta API  - \`RESOURCES\_READ\` - DEVE ser solicitada pela instituição receptora na ocasião do pedido de criação do consentimento.
    
-   O identificador do recurso devolvido na API Resources - \`resourceId\` - quando apresentado corresponde ao mesmo identificador designado para o recurso em sua API específica, o seja: o \`resourceId\` corresponde ao \`accountId\` da API accounts, ao \`creditCardAccountId\` da API de conta
    

pós-paga e assim sucessivamente.

\## Status previstos para os recursos listados na API Resources

-   AVAILABLE: indica que o recurso encontra-se disponível e o(s) consentimento(s) associado(s) possui(em) status \`AUTHORISED\`.
    
-   UNAVAILABLE: indica que o recurso não está mais disponível, por exemplo, em caso de uma conta encerrada.
    
-   TEMPORARILY\_UNAVAILABLE: indica que o recurso encontra-se temporariamente indisponível, embora o(s) consentimento(s) associado(s) possua(m) status \`AUTHORISED\`. 
    

Caso de exemplo: conta temporariamente bloqueada por suspeita de fraude.

-   PENDING\_AUTHORISATION: indica a existência de pendências para o compartilhamento do recurso, por exemplo, em caso de alçada dupla, quando é necessário o consentimento de mais de um titular.
    

\## Permissions necessárias para a API Resources  
\### \`/resources\`

-   permissions:
    
-   GET: \*\*RESOURCES\_READ\*\*
    

## GET /resources

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/page-size

Alterado - "description"

Alteração

Quantidade total de registros por páginas.

Quantidade total de registros por páginas.  
A transmissora deve considerar entrada como 25, caso seja informado algum valor menor pela receptora.  
Enquanto houver mais que 25 registros a enviar, a transmissora deve considerar o mínimo por página como 25.  
Somente a última página retornada (ou primeira, no caso de página única) pode conter menos de 25 registros.  
Mais informações, acesse Especificações de APIs > Padrões > Paginação.

get/parameters/page-size

Alterado - "minimum"

Alteração

1

25

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/parameters/x-fapi-interaction-id

Alterado - "required"

Alteração

TRUE

get/parameters/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/parameters/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/parameters/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/parameters/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

get/responses

Adicionado - "202"

Adição

get/responses/200/data/items

Adicionado - "x-regulatory-required"

Adição

get/responses/200/data/items/resourceId

Alterado - "description"

Alteração

Identifica o recurso reportado pelo participante do Open Finance, no caso de:  
Contas de depósito à vista, de poupança ou de pagamento pré-paga : corresponde ao accountId;  
Conta de pagamento pós-paga: corresponde ao creditCardAccountId;  
Empréstimos, Financiamentos, Direitos creditórios descontados e Adiantamento a depositantes: corresponde ao contractId.  
Renda Fixa Crédito, Renda Fixa Bancária, Renda Variável, Títulos do Tesouro Direto e Fundos de Investimentos: corresponde ao investmentId

Identifica o recurso reportado pelo participante do Open Finance, no caso de:

-   Contas de depósito à vista, de poupança ou de pagamento pré-paga : corresponde ao accountId;
    
-   Conta de pagamento pós-paga: corresponde ao  creditCardAccountId;
    
-   Empréstimos, Financiamentos, Direitos creditórios descontados e Adiantamento a depositantes: corresponde ao contractId
    
-   Renda Fixa Bancária, Renda Fixa Crédito, Renda Variável, Título do Tesouro Direto e Fundo de Investimento: corresponde ao investmentId;
    
-   Câmbio: corresponde ao operationId.
    

get/responses/200/data/items/type

Alterado - "description"

Alteração

Tipo de recurso (vide Enum):

-   Account - Conta de depósito à vista, poupança ou pagamento pré-paga
    
-   Credit Card Account - Conta de pagamento pós-paga (Cartão de Crédito)
    
-   Loan - Empréstimo
    
-   Financing - Financiamento
    
-   Unarranged Account Overdraft - Cheque Especial
    
-   Invoice Financing - Financiamento de Fatura
    
-   Bank Fixed Income - Renda Fixa Bancária
    
-   Credit Fixed Income - Renda Fixa Crédito
    
-   Variabel Income - Renda Variável
    
-   Treasure Title - Título do Tesouro Direto
    
-   Fund - Fundo de Investimento
    

Tipo de recurso (vide Enum):

-   Account - Conta de depósito à vista, poupança ou pagamento pré-paga
    
-   Credit Card Account - Conta de pagamento pós-paga (Cartão de Crédito)
    
-   Loan - Empréstimo
    
-   Financing - Financiamento
    
-   Unarranged Account Overdraft - Cheque Especial
    
-   Invoice Financing - Financiamento de Fatura
    
-   Bank Fixed Income - Renda Fixa Bancária
    
-   Credit Fixed Income - Renda Fixa Crédito
    
-   Variabel Income - Renda Variável
    
-   Treasure Title - Título do Tesouro Direto
    
-   Fund - Fundo de Investimento
    
-   Exchange - Câmbio
    

get/responses/200/data/items/type/enum

Adicionado - "EXCHANGE"

Adição

enum

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "description"

Adição

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e envio obrigatório pela receptora (client) e o seu valor deve ser “espelhado” pela transmissora (server) no cabeçalho de resposta. Caso não seja recebido ou se for recebido um valor inválido, a transmissora deve gerar um x-fapi-interaction-id e retorná-lo na resposta com o HTTP Status Code 400. A receptora deve acatar o valor recebido da transmissora.

get/responses/200/headers/x-fapi-interaction-id

Alterado - "pattern"

Alteração

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$

get/responses/200/headers/x-fapi-interaction-id

Alterado - "maxLength"

Alteração

100

36

get/responses/200/headers/x-fapi-interaction-id

Removido - "description"

Remoção

Um UID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação. Se fornecido, o transmissor deve "reproduzir" esse valor no cabeçalho de resposta.

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "format"

Adição

uuid

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "minLength"

Adição

1

get/responses/200/headers/x-fapi-interaction-id

Adicionado - "example"

Adição

d78fc4e5-37ca-4da3-adf2-9b082bf92280

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
