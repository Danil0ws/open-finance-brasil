# Informações Gerais - Consentimento - v2.2.0-rc.1

## **Visão Geral**

A API Consents viabiliza a criação, consulta e revogação dos consentimentos para a dados cadastrais e transacionais. (customer-data) do [Open Finance Brasil](https://openfinancebrasil.org.br/).

## **Criar novo pedido de consentimento :** (_POST /consents/v2/consents)_

Método para a criação de um novo consentimento.

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-consentsPostConsents_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_consentsPostConsents_v2.csv)

## **Obter detalhes do consentimento identificado por consentId** : (_GET_ /consents/v2/consents/{consentId})

Método para obter detalhes do consentimento identificado por consentId.

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-consentsGetConsentsConsentId_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_consentsGetConsentsConsentId_v2.csv)

## **Deletar / Revogar o consentimento identificado por consentId** : (_DELETE_ /consents/v2/consents/{consentId})

Método para deletar / revogar o consentimento identificado por consentId.

## **Obter detalhes de extensões feitas no consentimento identificado por consentId** : (GET /consents/{consentId}/extends)

Método para obter detalhes de extensões consentimento identificado por consentId.

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-consentsGetConsentsConsentIdExtends_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_consentsGetConsentsConsentIdExtends_v2.csv)

## **Renovar consentimento identificado por consentId :** (POST /consents/{consentId}/extends)

Método para renovar consentimento identificado por consentId, exceto casos com múltiplas alçadas. Nos casos de múltiplas alçadas, a transmissora deve retornar o status 422.

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-consentsPostConsentsConsentIdExtends_v2.md)

[Fazer download dos exemplos](https://openbanking-brasil.github.io/openapi/dictionary/example/examples_consentsPostConsentsConsentIdExtends_v2.csv)
