# Informações Gerais - Consentimento - v2.0.1

## **Visão Geral**

A API Consents viabiliza a criação, consulta e revogação dos consentimentos para a Fase 2 (customer-data) do [Open Finance Brasil](https://openfinancebrasil.org.br/).

## **Criar novo pedido de consentimento :** (_POST /consents/v2/consents)_

Método para a criação de um novo consentimento.

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-consentsPostConsents_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/101482514/consents.csv?version=2&amp;modificationDate=1683665990545&amp;cacheVersion=1&amp;api=v2&download=true)

## **Obter detalhes do consentimento identificado por consentId** : (_GET_ /consents/v2/consents/{consentId})

Método para obter detalhes do consentimento identificado por consentId.

**Dicionário de dados**

[Fazer download do dicionário de dados](data/references/openapi/dictionary-consentsGetConsentsConsentId_v2.md)

[Fazer download dos exemplos](https://openfinancebrasil.atlassian.net/wiki/download/attachments/101482514/consents_consentId.csv?api=v2&download=true)

## **Deletar / Revogar o consentimento identificado por consentId** : (_DELETE_ /consents/v2/consents/{consentId})

Método para deletar / revogar o consentimento identificado por consentId.
