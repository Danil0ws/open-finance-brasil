# Changelog - [SV] Vínculo de dispositivo - v2.0.0-rc.1 - 2.0.0-beta.1

## POST /enrollments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Adicionado - "enrollmentName"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido obrigatóriedade no campo 'expirationDateTime'

Remoção

required

post/responses/201/data/properties

Adicionado - "enrollmentName"

Adição

post/responses/201/data/expirationDateTime

Alterado - "description"

Alteração

O instante de expiração deste vínculo de conta, de acordo com a regulação vigente.

Data e hora definida pelo usuário em que o vínculo do dispositivo deve expirar, perdendo sua validade. \[Restrição\] Campo obrigató...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação do vínculo de conta: • PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de conta n...

Códigos de erros previstos na criação do vínculo de conta: - PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de conta nã...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de con...

Descrição específica do erro de acordo com o código reportado: - PERMISSOES\_INVALIDAS: As permissões associadas ao vínculo de cont...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • PERMISSOES\_INVALIDAS: Permissões inválidas. • CONTA\_INVAL...

Título específico do erro reportado, de acordo com o código enviado: - PERMISSOES\_INVALIDAS: Permissões inválidas. - CONTA\_INVALID...

## GET /enrollments/{enrollmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado - "enrollmentName"

Adição

get/responses/200/data/properties

Removido obrigatóriedade no campo 'expirationDateTime'

Remoção

required

get/responses/200/data/expirationDateTime

Alterado - "description"

Alteração

O instante de expiração deste vínculo de conta, de acordo com a regulação vigente.

Data e hora definida pelo usuário em que o vínculo do dispositivo deve expirar, perdendo sua validade.

\[Restrição\] Campo obrigatório que deverá ser retornado quando o vínculo de dispositivo estiver ou passar pelo estado AUTHORISED;

## PATCH /enrollments/{enrollmentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos no cancelamento do vínculo de conta: • STATUS\_INVALIDO: O status do vínculo de conta não permite cance...

Códigos de erros previstos no cancelamento do vínculo de conta: - STATUS\_INVALIDO: O status do vínculo de conta não permite cancel...

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

patch/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_INVALIDO: O status do vínculo de conta não permite cancel...

Descrição específica do erro de acordo com o código reportado: - STATUS\_INVALIDO: O status do vínculo de conta não permite cancela...

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_INVALIDO: Status inválido. • MOTIVO\_REJEICAO: Moti...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_INVALIDO: Status inválido. - MOTIVO\_REJEICAO: Motivo...

## POST /enrollments/{enrollmentId}/fido-registration

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova cred...

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova crede...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que ...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que n...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_VINCULO\_INVALIDO: Status inválido do vínculo de con...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status inválido do vínculo de cont...

## POST /enrollments/{enrollmentId}/fido-registration-options

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/user/id

Alterado - "description"

Alteração

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

Identificador único do usuário sob registro em formato base64. A conversão deste valor para o formato original (BufferSource ou Ar...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. • STATUS\_VINCULO\_...

Códigos de erros previstos: - RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. - STATUS\_VINCULO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • RP\_INVALIDA: O identificador da Relying Party informado não pode...

Descrição específica do erro de acordo com o código reportado: - RP\_INVALIDA: O identificador da Relying Party informado não pode ...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • RP\_INVALIDA: Relying party inválida. • STATUS\_VINCULO\_INV...

Título específico do erro reportado, de acordo com o código enviado: - RP\_INVALIDA: Relying party inválida. - STATUS\_VINCULO\_INVAL...

## POST /enrollments/{enrollmentId}/fido-sign-options

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. • STATUS\_VINCULO\_...

Códigos de erros previstos: - RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado. - STATUS\_VINCULO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • RP\_INVALIDA: O identificador da Relying Party informado não pode...

Descrição específica do erro de acordo com o código reportado: - RP\_INVALIDA: O identificador da Relying Party informado não pode ...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • RP\_INVALIDA: Relying party inválida. • STATUS\_VINCULO\_INV...

Título específico do erro reportado, de acordo com o código enviado: - RP\_INVALIDA: Relying party inválida. - STATUS\_VINCULO\_INVAL...

## POST /consents/{consentId}/authorise

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post

Alterado - "description"

Alteração

Autorização de um consentimento de pagamentos em status \`AWAITING\_AUTHORISATION\` a partir do access\_token emitido pela jornada sem...

Autorização de um consentimento de pagamentos em status \`AWAITING\_AUTHORISATION\` a partir do access\_token emitido pela jornada sem...

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

post/requestBody/data/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

post/requestBody/data/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

post/requestBody/data/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. • STATUS\_CONSENTIMENTO\_I...

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. - STATUS\_CONSENTIMENTO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: • STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. • STATUS\_CONSENTIMENTO\_I...

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED. - STATUS\_CONSENTIMENTO\_IN...

post/responses/422/errors/items/code/enum

Adicionado - "CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: • STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AU...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: • STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

## POST /enrollments/{enrollmentId}/risk-signals

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

post/requestBody/data/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

post/requestBody/data/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

post/requestBody/data/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

post/requestBody/data/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

post/requestBody/data/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

post/requestBody/data/screenDimensions

Alterado - "description"

Alteração

Dimensões que o aplicativo ocupa na tela do dispositivo. \[Android\] Informação obtida através do \[link\]([https://developer.androi](https://developer.androi)...

Dimensões que o aplicativo ocupa na tela do dispositivo. \[Android\] Informação obtida através do \[link\]([https://developer.android](https://developer.android)....

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompatível com a operação.

Códigos de erros previstos: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompatível com a operação. - FALTAM\_SINAI...

post/responses/422/errors/items/code/enum

Adicionado - "FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_NAO\_INFORMADO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "PARAMETRO\_INVALIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "ERRO\_IDEMPOTENCIA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompat...

Descrição específica do erro de acordo com o código reportado: - STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é incompat...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

Título específico do erro reportado, de acordo com o código enviado: - STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inváli...

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'isRootedDevice'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'screenBrightness'

Remoção

required

post/requestBody/data/riskSignals/properties

Removido obrigatóriedade no campo 'elapsedTimeSinceBoot'

Remoção

required

post/requestBody/data/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

Indica por quanto tempo (em milissegundos) o dispositivo está ligado. \[Android\] Informação obtida através do \[link\]([https://devel](https://devel)...

post/requestBody/data/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

Indica se o dispositivo atualmente está com permissão de “root”. \[Restrição\] Campos de envio obrigatório quando o sistema operaci...

post/requestBody/data/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...

Indica o nível de brilho da tela do dispositivo. \[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valor...
