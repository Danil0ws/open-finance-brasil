# Campos regulatórios - [DC] Consentimento

### Campos obrigatórios segundo a regulação

Os campos listados abaixo são obrigatórios por regulação de acordo com o Banco Central.​

Além disso, ao longo da especificação, o atributo x-regulatory-required indica a obrigatoriedade regulatória de cada campo dentro dos objetos.​

Para mais informações sobre preenchimento dos campos e relação com a obrigatoriedade técnica, consulte a página "Obrigatoriedade de campos" na seção "Padrões“.

**Endpoint**

**Campos**

**Regulação**

POST /consents

Requisição

data.loggedUser.document.identification

RESOLUÇÃO CONJUNTA Nº 1

data.businessEntity.document.identification

RESOLUÇÃO CONJUNTA Nº 1

data.permissions

RESOLUÇÃO CONJUNTA Nº 1

data.expirationDateTime

RESOLUÇÃO CONJUNTA Nº 1

Resposta

data.permissions

RESOLUÇÃO CONJUNTA Nº 1

data.expirationDateTime

RESOLUÇÃO CONJUNTA Nº 1

GET /consents/{consentId}

Resposta

data.permissions

RESOLUÇÃO CONJUNTA Nº 1

data.consentId

RESOLUÇÃO CONJUNTA Nº 1

data.expirationDateTime

RESOLUÇÃO CONJUNTA Nº 1

POST /consents/{consentId}/extends

Requisição

data.loggedUser.document.identification

RESOLUÇÃO CONJUNTA Nº 1

data.businessEntity.document.identification

RESOLUÇÃO CONJUNTA Nº 1

data.expirationDateTime

RESOLUÇÃO CONJUNTA Nº 1

Resposta

data.permissions

RESOLUÇÃO CONJUNTA Nº 1

data.expirationDateTime

RESOLUÇÃO CONJUNTA Nº 1

GET /consents/{consentId}/extensions

Resposta

data.loggedUser.document.identification

RESOLUÇÃO CONJUNTA Nº 1

data.expirationDateTime

RESOLUÇÃO CONJUNTA Nº 1
