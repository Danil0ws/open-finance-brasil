# Changelog - [DC] Consentimento - v3.1.0 - v3.0.1

16falsenonelisttrue

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

-   SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES - INFORMACOES\_PJ\_NAO\_INFORMADAS - PERMISSOES\_PJ\_INCORRETAS - PERMISSAO\_PF\_PJ\_EM\_CONJUNTO - C...
    

-   SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES - INFORMACOES\_PJ\_NAO\_INFORMADAS - PERMISSOES\_PJ\_INCORRETAS - PERMISSAO\_PF\_PJ\_EM\_CONJUNTO - C...
    

post/responses/422/errors/items/code/enum

Adicionado - "DATA\_EXPIRACAO\_INVALIDA"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_NAO\_MAPEADO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição legível por humanos deste erro específico. Para o erro de data de expiração maior que um ano, diferente de prazo indeter...

Descrição legível por humanos deste erro específico.

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título legível por humanos deste erro específico. Para o erro de data de expiração maior que um ano, diferente de prazo indetermin...

Título legível por humanos deste erro específico.

## POST /consents/{consentId}/extends

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido obrigatóriedade no campo 'permissions'

Remoção

required

post/requestBody/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido obrigatóriedade no campo 'permissions'

Remoção

required

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

Data e hora de expiração da permissão. Deve ser preenchido caso o consentimento tenha data limite de validade. Uma string com data...

Data e hora de expiração da permissão. Reflete a data limite de validade do consentimento. Uma string com data e hora conforme esp...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na durante o processo de extensão do consentimento: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de...

Códigos de erros previstos na durante o processo de extensão do consentimento: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de...

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_NAO\_MAPEADO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: O consentimento informado não pode...

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: O consentimento informado não pode...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de múltipla a...

Título específico do erro reportado, de acordo com o código enviado: - DEPENDE\_MULTIPLA\_ALCADA: Necessário aprovação de múltipla a...
