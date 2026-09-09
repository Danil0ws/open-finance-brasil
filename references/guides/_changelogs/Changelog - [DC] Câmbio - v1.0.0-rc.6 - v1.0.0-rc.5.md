# Changelog - [DC] Câmbio - v1.0.0-rc.6 - v1.0.0-rc.5

## GET /operations/{operationId}

### Informações do endpoint

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get

Alterado - "description"

Alteração

Obtém os dados da operação de Câmbio identificada por operationId.

Obtém os dados da operação de Câmbio identificada por operationId. As alterações efetuadas na operação original devem ser represen...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/deliveryForeignCurrency

Alterado - "description"

Alteração

Forma de entrega da moeda estrangeira.

Forma de entrega da moeda estrangeira. \`\`\` |--------|-------------------------------------------------------------| | Código | EN...

get/responses/200/data/deliveryForeignCurrency/enum

Adicionado - "CONTA\_DEPOSITO\_EXPORTADOR\_MANTIDA\_NO\_EXTERIOR"

Adição

enum

get/responses/200/data/deliveryForeignCurrency/enum

Adicionado - "CONVENIO\_PAGAMENTOS\_E\_CREDITOS\_RECIPROCOS"

Adição

enum

get/responses/200/data/deliveryForeignCurrency/enum

Adicionado - "OUTRO\_NAO\_MAPEADO\_OFB"

Adição

enum

## GET /operations/{operationId}/events

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/deliveryForeignCurrency

Alterado - "description"

Alteração

Forma de entrega da moeda estrangeira.

Forma de entrega da moeda estrangeira. \`\`\` |--------|-------------------------------------------------------------| | Código | EN...

get/responses/200/data/items/deliveryForeignCurrency/enum

Adicionado - "CONTA\_DEPOSITO\_EXPORTADOR\_MANTIDA\_NO\_EXTERIOR"

Adição

enum

get/responses/200/data/items/deliveryForeignCurrency/enum

Adicionado - "CONVENIO\_PAGAMENTOS\_E\_CREDITOS\_RECIPROCOS"

Adição

enum

get/responses/200/data/items/deliveryForeignCurrency/enum

Adicionado - "OUTRO\_NAO\_MAPEADO\_OFB"

Adição

enum
