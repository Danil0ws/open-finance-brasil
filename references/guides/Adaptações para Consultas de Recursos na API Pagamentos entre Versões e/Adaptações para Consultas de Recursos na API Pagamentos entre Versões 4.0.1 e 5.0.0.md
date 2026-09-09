# Adaptações para Consultas de Recursos na API Pagamentos entre Versões 4.0.1 e 5.0.0

## Introdução e objetivo

A introdução das funcionalidades de Pix Saque, Pix Troco, adoção dos instrumentos de liquidação que representam a iniciação por aproximação (NFC) e a formalização do funil de rejeição da Jornada Sem Redirecionamento (JSR) resultaram no versionamento da API Pagamentos para a versão 5.0.0. Foram implementadas diversas alterações (disponíveis para consulta na página de changelog desta versão), porém, devido a características inerentes do consentimento dessa API, certos aspectos requerem observação durante a operação de recursos pertencentes a versões anteriores. Estes pontos são abordados nas seções subsequentes.

Este documento complementa o changelog da API e define quais operações podem ser realizadas entre as versões e quais não podem. Além disso, detalha o tratamento a ser aplicado a cada um dos campos que apresentam alguma mudança em suas regras de negócio ou técnicas significativas para a execução das consultas de recursos no Open Finance.

Ressalta-se que a versão 4.0.1 da API Pagamentos não permitia a operação dos produtos Pix Saque e Pix Troco, portanto, as adequações especificadas neste documento aplicam-se predominantemente às consultas de operações iniciadas em versões anteriores e consultadas na versão 5.0.0.

## Orientações Gerais

Haverá um período de convivência entre as versões 4.0.1 e 5.0.0, durante o qual ambas estarão disponíveis. Ao final do período, apenas a versão 5.0.0 ficará disponível, e os ITPs deverão ter migrado integralmente suas chamadas até esta data.

Consentimentos da API Pagamentos são de uso único. Após criados e autorizados, são utilizados para gerar pagamento(s), transitando para o status `CONSUMED`. A partir deste ponto, ficam disponíveis apenas para consultas.

Não será permitida a criação de um consentimento em uma versão e a sua utilização para iniciação de pagamento em uma versão diferente, independentemente dos campos envolvidos na transação. O consentimento e o pagamento subsequente devem pertencer à mesma versão da API.

Neste cenário, deve-se retornar o código de erro HTTP 422 com os seguintes detalhes:  
**code:** PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO;  
**detail:** Divergência entre versões de consentimento e pagamento.

Pagamentos e consentimentos criados em versões anteriores devem permanecer consultáveis através dos endpoints `GET /consents/{consentId}`, `GET /pix/payments/{paymentId}` da versão 5.0.0 durante e após o período de convivência.

Não será permitida a consulta de um consentimento ou pagamento criado na versão 5.0.0 através dos endpoints da versão 4.0.1.

Neste cenário, deve-se retornar o código de erro HTTP 400.

Por fim, pagamentos agendados criados em versões anteriores poderão ser cancelados através do endpoint `PATCH /pix/payments/{paymentId}` da versão 5.0.0 durante e após o período de convivência.

## Orientações Específicas

### 1\. Análise Comparativa do corpo de resposta do GET /consents/{consentId} entre as Versões 4.0.1 e 5.0.0

#### 1.1 Campos Adicionados na Versão 5.0.0:

Campo (XPath)

Obrigatoriedade

Tipo de Dado

Descrição

Ação

`data>payment>purpose`

Obrigatório quando `data>payment>type` for igual a `PIX` (único valor possível, portanto sempre obrigatório).

enum

Finalidade da transação. Valores: `IMMEDIATE`, `SINGLE_SCHEDULED`, `RECURRENT_SCHEDULED`, `WITHDRAW`, `CHANGE`.

Derivar o valor a partir dos dados do consentimento v4.0.1, conforme regra da seção 1.5.

`data>payment>details>payloadJWS`

Obrigatório quando `data>payment>details>localInstrument` for igual a `APDN` ou `QRDN`.

string

Payload JWS obtido pela ITP na leitura do QR dinâmico.

Retornar o valor fixo `inexistente.inexistente.inexistente`, conforme seção 1.5. Não há como derivar o valor real, pois o JWT é gerado pelo PSP do Recebedor no momento da leitura do QR e não foi capturado em recursos da v4.0.1.

#### 1.2 Campos Modificados (Mudanças de Conteúdo):

Campo (XPath)

Versão 4.0.1

Versão 5.0.0

Ação

`data>businessEntity>document>identification`

Pattern: `^\d{14}$`.

Pattern: `^[0-9A-Z]{12}[0-9]{2}$`.

Sem ação. Devolver valor atual.

`data>creditor>cpfCnpj`

Pattern: `^\d{11}$|^\d{14}$`.

Pattern: `^([0-9]{11})$|^([0-9A-Z]{12}[0-9]{2})$`.

Sem ação. Devolver valor atual.

`data>creditor>name`

Pattern: `^([A-Za-zÀ-ÖØ-öø-ÿ,.@:&*+_<>()!?/\\$%\d' -]+)$`.

Pattern: `^[\u0020-\u007E\u00A1-\u00FF]+$`.

Sem ação. Devolver valor atual.

`data>debtorAccount>ispb`

Pattern: `^[0-9]{8}$`.

Pattern: `^[0-9A-Z]{8}$`.

Sem ação. Devolver valor atual.

`data>payment>details>creditorAccount>ispb`

Pattern: `^[0-9]{8}$`.

Pattern: `^[0-9A-Z]{8}$`.

Sem ação. Devolver valor atual.

`data>payment>details>localInstrument`

Enum: `MANU`, `DICT`, `QRDN`, `QRES`, `INIC`.

Enum ampliado: `MANU`, `DICT`, `APDN`, `QRDN`, `APES`, `QRES`, `INIC`.

Sem ação. Devolver o valor original informado na criação do consentimento.

#### 1.3 Campos Modificados (Mudanças de Obrigatoriedade):

Campo (XPath)

Versão 4.0.1

Versão 5.0.0

Ação

`data>payment>schedule>additionalInformation`

Inexistente no nível raiz do `schedule`. Na v4.0.1, o campo `additionalInformation` existia apenas dentro de `schedule>custom`, obrigatório somente para agendamento custom.

Promovido ao nível raiz do `schedule` com `required`, tornando-se obrigatório para todos os tipos de agendamento (`single`, `daily`, `weekly`, `monthly`, `custom`).

Para consentimentos custom da v4.0.1, derivar o valor a partir de `schedule>custom>additionalInformation`. Para os demais tipos de agendamento, retornar o valor fixo `Informação não disponível para consentimentos originados em versão anterior`, conforme seção 1.5.

`data>rejectionReason>code`

Enum sem `AUTENTICACAO_DIVERGENTE` e `PERMISSAO_INSUFICIENTE`.

Novos valores adicionados ao enum.

Sem ação. Devolver valor atual.

#### 1.4 Campos Removidos na Versão 5.0.0:

Campo (XPath)

Motivo/Observação

Ação

`data>payment>schedule>custom>additionalInformation`

Realocado para o nível raiz do `schedule` (ver seção 1.3). Não se trata de descontinuação: o campo deixou de existir dentro de `custom` e passou a ser obrigatório no nível raiz do `schedule`.

Para consentimentos custom da v4.0.1, o valor deve ser utilizado para preencher `data>payment>schedule>additionalInformation` na resposta da v5, conforme seção 1.3.

#### 1.5 Tratamentos para campos obrigatórios sem origem na versão 4.0.1:

**Derivação de** `data>payment>purpose`

O valor deve ser derivado a partir da estrutura do consentimento v4.0.1:

Condição no consentimento v4.0.1

Valor derivado

Campo `data>payment>date` preenchido (pagamento único e imediato, sem objeto `schedule`).

`IMMEDIATE`

Objeto `data>payment>schedule>single` preenchido.

`SINGLE_SCHEDULED`

Objeto `data>payment>schedule>daily`, `weekly`, `monthly` ou `custom` preenchido.

`RECURRENT_SCHEDULED`

Os valores `WITHDRAW` e `CHANGE` não se aplicam a recursos da v4.0.1, dado que os produtos Pix Saque e Pix Troco não eram suportados nesta versão.

**Valor fixo para** `data>payment>details>payloadJWS` **e** `data>payment>schedule>additionalInformation` **(agendamentos não-custom)**

Para estes campos não há dado de origem na v4.0.1 nem regra de derivação aplicável, adota-se o preenchimento com valor fixo sentinela, que atende às restrições de schema da v5.0.0:

Campo (XPath)

Valor fixo

Observação

`data>payment>details>payloadJWS`

`inexistente.inexistente.inexistente`

Satisfaz o pattern `^[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+$` (três segmentos). O valor é um sentinela e não representa um JWS válido; a detentora não deve tentar decodificá-lo como JWT.

`data>payment>schedule>additionalInformation`

`Informação não disponível para consentimentos originados em versão anterior`

Satisfaz o pattern `[\w\W\s]*` e o limite de 255 caracteres.

### 2\. Análise Comparativa do corpo de resposta do GET /pix/payments/{paymentId} entre as Versões 4.0.1 e 5.0.0

#### 2.1 Campos Modificados (Mudanças de Conteúdo):

Campo (XPath)

Versão 4.0.1

Versão 5.0.0

Ação

`data>cnpjInitiator`

Pattern: `^\d{14}$`.

Pattern: `^[0-9A-Z]{12}[0-9]{2}$`.

Sem ação. Devolver valor atual.

`data>creditorAccount>ispb`

Pattern: `^[0-9]{8}$`.

Pattern: `^[0-9A-Z]{8}$`.

Sem ação. Devolver valor atual.

`data>endToEndId`

Pattern: `^([E])([0-9]{8})([0-9]{4})...`.

Pattern: `^([E])([0-9A-Z]{8})([0-9]{4})...`.

Sem ação. Devolver valor atual.

`data>localInstrument`

Enum: `MANU`, `DICT`, `QRDN`, `QRES`, `INIC`.

Enum ampliado: `MANU`, `DICT`, `APDN`, `QRDN`, `APES`, `QRES`, `INIC`.

Sem ação. Devolver o valor original informado na criação do pagamento.

`data>rejectionReason>code`

Enum sem `CHAVE_PIX_DIVERGENTE_AGENDAMENTO_LIQUIDACAO`, `CONTA_NAO_PERMITE_PAGAMENTO`, `QRCODE_INVALIDO` e os granulares de `FALHA_INFRAESTRUTURA_*`.

Novos valores adicionados ao enum.

Sem ação. Devolver valor atual.

## Conclusão

Adotando as ações necessárias, as consultas de recursos entre as versões (anterior e recente) devem ocorrer de forma suave pelas ITPs e Detentoras que sigam as especificações e realizem as adequações de retrocompatibilidade.
