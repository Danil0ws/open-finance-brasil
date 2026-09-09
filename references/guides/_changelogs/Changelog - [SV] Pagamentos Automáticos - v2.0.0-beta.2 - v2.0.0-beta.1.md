# Changelog - [SV] Pagamentos Automáticos - v2.0.0-beta.2 - v2.0.0-beta.1

**A implementação e certificação do VRP está pausada no momento. Os produtos Transferência Inteligentes (Sweeping Accounts) e Pix Automático continuam disponíveis para implementação e certificação.**

16falsenonelisttrue

## Release Notes

### Mudanças Comuns para Transferências Inteligentes e Pix Automático

**Item**

**Descrição**

**Impacto**

**Referência**

**1.1. Consentimento - Prazo Máximo para primeira Autorização**

Antes: 05 minutos  
Agora: 60 minutos

Desenvolvedores precisam ajustar a lógica de autorização para considerar o novo prazo.

Página da Máquina de Estados da versão 2.0.0-beta.2, estado AWAITING\_AUTHORISATION

**1.2. Alteração de Campo** `/data/startDateTime`

O campo `/data/startDateTime` foi movido para `/data/recurringConfiguration/sweeping/startDateTime`.

Continua operando para Transferências Inteligentes conforme a versão anterior, mas os desenvolvedores devem atualizar suas integrações para refletir a nova localização do campo.

Para representar a data de início para consentimentos de Pix Automático, foi criado um campo, mais detalhes no item 3.4 deste documento.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

**1.3. Restrição no Campo** `/data/transactionIdentification`

Adicionada restrição indicando quando o campo deve ou não ser preenchido.

Verifique as condições específicas antes de enviar este campo nas requisições para evitar erros.

Endpoints de Pagamento Recorrente, na Especificação técnica (OAS)

### Transferências Inteligentes

**Item**

**Descrição**

**Impacto**

**Referência**

**2.1. Mudança no Estado do Pagamento para Cálculo de Limites**

Alteração no estado considerado para o cálculo dos limites do consentimento.

Atualize a lógica de verificação conforme o novo critério.

Header da Especificação, tópico “Limites Transacionais para Transferências Inteligentes”

**2.2. Adição do Campo** `/data/recurringConfiguration/sweeping/startDateTime`

Representa a data e hora de validade do consentimento para transferências inteligentes.

Implementar o novo campo nas integrações para gerenciar a validade dos consentimentos.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

**2.3. Alteração na Descrição do Campo** `/data/riskSignals/automatic/lastLoginDateTime`

Ampliadas as possibilidades de recuperação dos valores para cenários de BaaS.

Atualize a implementação para contemplar os novos cenários suportados pelo campo.

Endpoints de Pagamento Recorrente, na Especificação técnica (OAS)

### Pix Automático

**Item**

**Descrição**

**Impacto**

**Referência**

**3.1. Falha na Liquidação do primeiro pagamento (declarado no campo “/data/recurringConfiguration/automatic/firstPayment”)**

Falhas na liquidação não caracterizam rejeição no consentimento.

Nesse cenário, o recebedor decide se continua com o consentimento ativo, aplicável tanto para pagamentos imediatos quanto agendados para datas futuras.

A definir

**3.2. Novas Tentativas Intradia e** `endToEndId`

O ITP deve realizar novas tentativas até as 12:00h.

Atualize a lógica para geração e envio de `endToEndId` conforme necessário.

Área do Desenvolvedor, Página Tentativas Intradia e Extradia para Pix automático, no conjunto de informações Gerais da API de Pagamentos Automáticos.

**3.3. Restrição para Pagamentos no Campo** `/data/proxy`

Não enviar o campo `/data/proxy` quando o valor de `/data/localInstrument` for `"MANU"`.

Ajuste as requisições para obedecer a esta restrição.

Endpoints de Pagamento Recorrente, na Especificação técnica (OAS)

**3.4. Criação do Campo** `/data/recurringConfiguration/automatic/referenceStartDateTime`

Representa a data prevista para a primeira ocorrência de um pagamento recorrente.

Permite novas cobranças periódicas a partir dessa data, garantindo a data inicial de validade do consentimento.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

**3.5. Alterações no Endpoint PATCH** `/recurring-consents/{recurringConsentId}`

**Obrigatoriedade:** Os objetos `/data/riskSignals` e `/data/creditors` agora são obrigatórios.  
**Restrições Adicionais:** Campos `/data/recurringConfiguration/automatic/maximumVariableAmount` e `/data/expirationDateTime` podem ser alterados para valores indeterminados.

Atualize as requisições PATCH para incluir os campos obrigatórios e respeitar as novas restrições.

Header da Especificação, tópico “Validações da Edição do Consentimento Recorrente para o Produto Pix Automático”

**3.6. Rejeição de Tentativas Intradia Fora do Prazo**

Se o ITP não respeitar o prazo de até 12:00h para novas tentativas intradia, ou os 7 dias após a falha da tentativa original, ou tenta realizar o agendamento fora do prazo de 10 a 2 dias permitidos, o detentor deve rejeitar a tentativa com o motivo `FORA_PRAZO_PERMITIDO`.

Implemente a lógica para rejeitar tentativas fora do prazo especificado.

Header da Especificação Técnica, tópico “Validações”, itens 4 e 6.

**3.7. Adição do Campo** `/data/paymentReference`

Campo obrigatório para pagamentos de Pix Automático, deve ser preenchido com a referência do período cobrado.  
**Regras de Preenchimento:** Diferentes conforme o tipo de periodicidade selecionada para o consentimento.

Assegure-se de que o campo seja preenchido corretamente de acordo com as regras para cada tipo de periodicidade e ciclo vigente

Endpoints de Pagamento Recorrente, na Especificação técnica (OAS)

**3.8. Remoção da Obrigatoriedade do Campo** `/data/recurringConfiguration/automatic/firstPayment/creditorAccount/issuer`

O campo não é mais obrigatório.

Atualize as requisições para não exigir este campo.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

**3.9. Adição de** `rejectionReason` **e Erro Síncrono para Novas Tentativas de Pagamento**

Implementação de `rejectionReason` para novas tentativas após falha da original, utilizando o motivo `DETALHE_TENTATIVA_INVALIDO` quando o ITP informar mais de um `endToEndId` e/ou uma nova data de liquidação.

Ajuste o tratamento de erros para incluir este novo motivo de rejeição.

Header da Especificação Técnica, tópico “Validações”, itens 4 e 6.

**3.10. Alteração no Campo de Tentativas de Pagamento**

Remoção do campo `/data/lastRetryRecurringPaymentIds` e adição do campo `/data/originalRecurringPaymentId`.

Informar apenas a tentativa de pagamento original que falhou.  
A contagem das tentativas fica a cargo do back-end das instituições.

Endpoints de Pagamento Recorrente, na Especificação técnica (OAS)

**3.11. Remoção do Campo** `/data/recurringConfiguration/automatic/month`

Devido à alteração do mecanismo de definição de periodicidade, este campo perdeu seu uso.

Atualize as requisições removendo este campo.

Veja o changelog entre as versões 1.0.0 e 2.0.0-beta.1 para mais detalhes.

**3.12. Renomeação do Campo** `/data/recurringConfiguration/automatic/period` **para** `/data/recurringConfiguration/automatic/interval`

Alteração para maior clareza sobre o significado do campo.

Atualize todas as referências e implementações para utilizar o novo nome.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

**3.13. Adição do Novo Parâmetro de Filtro** `originalRecurringPaymentId` **no Endpoint GET** `/pix/recurring-payments`

Permite a busca de todas as tentativas de pagamento associadas a um pagamento original que falhou.

Utilize o novo `queryParam` para filtrar as tentativas conforme necessário.

Endpoint GET /pix/recurring-payments, na Especificação técnica (OAS)

**3.14. Adição do Novo Motivo de Rejeição para Edição de Consentimento**

`FALTA_PERMISSAO_EDICAO` representa a falta de permissão para editar o consentimento. Apenas usuários com plenos poderes sobre o consentimento podem realizar alterações via PATCH.

Implemente a lógica para rejeitar tentativas de edição sem permissão adequada.

Endpoint PATCH /recurring-consent/{recurringConsentId}, na Especificação técnica (OAS)

**3.15. Adição da Estrutura Padrão de Identificação do Cliente no Endpoint PATCH** `/recurring-consents/{recurringConsentId}`

Inclusão dos objetos `/data/loggedUser` e `/data/businessEntity` para identificação do cliente.

Atualize as requisições PATCH para incluir estas estruturas.

Endpoint PATCH /recurring-consent/{recurringConsentId}, na Especificação técnica (OAS)

**3.16. Validação da Data da Primeira Ocorrência de Recorrência**

A data da primeira ocorrência DEVE ser posterior à data de liquidação do primeiro pagamento.

Assegure-se de que as cobranças de recorrência iniciem em data posterior ao pagamento do primeiro pagamento (considerado como pagamento da adesão ao serviço).

A definir

**3.17. Adição do Campo** `/data/updatedAtDateTime`

Campo inserido para equalizar as datas de alteração do recurso em ambos os ambientes, ITP e Detentor.

Inclua este campo nas respostas para rastreamento das atualizações.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

**3.18. Definição de Erros e Motivos de Rejeição que Contabilizam como Tentativa de Pagamento**

Apenas os seguintes erros/motivos de rejeição contabilizam como tentativas de pagamento:  
`SALDO_INSUFICIENTE`  
`VALOR_ACIMA_LIMITE`  
`NAO_INFORMADO`  
`PAGAMENTO_RECUSADO_DETENTORA`  
`PAGAMENTO_RECUSADO_SPI`  
`FALHA_INFRAESTRUTURA_SPI`  
`FALHA_INFRAESTRUTURA_ICP`  
`FALHA_INFRAESTRUTURA_PSP_RECEBEDOR`  
`FALHA_INFRAESTRUTURA_DETENTORA`  
`LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO`

Ajuste o tratamento de erros para contabilizar apenas estes motivos como tentativas de pagamento.  
**Nota:** Demais erros da API não contabilizam como tentativa e/ou não se aplicam.

Área do Desenvolvedor, Página Tentativas Intradia e Extradia para Pix automático, no conjunto de informações Gerais da API de Pagamentos Automáticos.

**3.19. Correções no Objeto** `/data/recurringConfiguration/automatic/contractDebtor/`

Permite o envio de devedores Pessoa Física (PF) ou Pessoa Jurídica (PJ).

Assegure-se de que as requisições suportem ambos os tipos de devedores.

Endpoints de Consentimento Recorrente, na Especificação técnica (OAS)

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

## GET /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters

Adicionado - "originalRecurringPaymentId"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/properties

Removido - "lastRetryRecurringPaymentIds"

Remoção

get/responses/200/data/items/properties

Adicionado - "originalRecurringPaymentId"

Adição

get/responses/200/data/items/properties

Adicionado - "paymentReference"

Adição

get/responses/200/data/items/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

get/responses/200/data/items/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

get/responses/200/data/items/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## POST /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido - "lastRetryRecurringPaymentIds"

Remoção

post/requestBody/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

post/requestBody/data/properties

Adicionado - "paymentReference"

Adição

post/requestBody/data/proxy

Alterado - "description"

Alteração

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

post/requestBody/data/riskSignals/automatic/lastLoginDateTime

Alterado - "description"

Alteração

Data e hora da última interação do cliente com o aplicativo/sistema da instituição iniciadora.

Caso o usuário pagador tenha acesso ao ambiente da iniciadora de pagamentos, utilizar data e hora da última interação do cliente c...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido - "lastRetryRecurringPaymentIds"

Remoção

post/responses/201/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

post/responses/201/data/properties

Adicionado - "paymentReference"

Adição

post/responses/201/data/proxy

Alterado - "description"

Alteração

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

post/responses/201/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

post/responses/201/data/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

post/responses/201/data/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

post/responses/201/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

post/responses/201/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação da iniciação de pagamento: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para...

Códigos de erros previstos na criação da iniciação de pagamento: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para...

post/responses/422/errors/items/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

post/responses/422/errors/items/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para r...

Descrição específica do erro de acordo com o código reportado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para r...

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente ...

Título específico do erro reportado, de acordo com o código enviado: - SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente ...

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido - "lastRetryRecurringPaymentIds"

Remoção

get/responses/200/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

get/responses/200/data/properties

Adicionado - "paymentReference"

Adição

get/responses/200/data/proxy

Alterado - "description"

Alteração

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

get/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

get/responses/200/data/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

get/responses/200/data/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

get/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

get/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido - "lastRetryRecurringPaymentIds"

Remoção

patch/responses/200/data/properties

Adicionado - "originalRecurringPaymentId"

Adição

patch/responses/200/data/properties

Adicionado - "paymentReference"

Adição

patch/responses/200/data/proxy

Alterado - "description"

Alteração

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

Chave cadastrada no DICT pertencente ao recebedor. Os tipos de chaves podem ser: telefone, e-mail, cpf/cnpj ou chave aleatória. N...

patch/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

Código identificador do motivo de rejeição. Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status. ...

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "FORA\_PRAZO\_PERMITIDO"

Adição

enum

patch/responses/200/data/rejectionReason/code/enum

Adicionado - "DETALHE\_TENTATIVA\_INVALIDO"

Adição

enum

patch/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

Detalhe sobre o código identificador do motivo de rejeição. - SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente...

patch/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento. E...

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido - "startDateTime"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDateTime"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping

Adicionado - "required"

Adição

post/requestBody/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/properties

Alterado- "period"

Alteração

Period

Interval

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

post/responses/201/data/properties

Removido - "startDateTime"

Remoção

post/responses/201/data/properties

Adicionado - "updatedAtDateTime"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDateTime"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado obrigatóriedade no campo 'startDateTime'

Adição

required

post/responses/201/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/properties

Alterado- "period"

Alteração

Period

Interval

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

get/responses/200/data/properties

Removido - "startDateTime"

Remoção

get/responses/200/data/properties

Adicionado - "updatedAtDateTime"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDateTime"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado obrigatóriedade no campo 'startDateTime'

Adição

required

get/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Alterado- "period"

Alteração

Period

Interval

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

Método para rejeitar, revogar ou editar um consentimento de longa duração: 1 - Informações sobre a revogação: - Caso bem sucedid...

patch/requestBody/data/oneOf/0/properties

Removido - "startDateTime"

Remoção

patch/requestBody/data/oneOf/0

Adicionado - "required"

Adição

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https:/...

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https:/...

patch/requestBody/data/oneOf/0/recurringConfiguration/automatic/maximumVariableAmount

Alterado - "description"

Alteração

Valor máximo permitido por cobrança, caso preenchido, representa um consentimento para pagamentos de valores variáveis.

Valor máximo permitido por cobrança, caso preenchido, representa um consentimento para pagamentos de valores variáveis. \[Restriçã...

patch/requestBody/data/oneOf/0/properties

Adicionado - "loggedUser"

Adição

patch/requestBody/data/oneOf/0/properties

Adicionado - "businessEntity"

Adição

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

patch/responses/200/data/properties

Removido - "startDateTime"

Remoção

patch/responses/200/data/properties

Adicionado - "updatedAtDateTime"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado obrigatóriedade no campo 'referenceStartDateTime'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Adicionado - "referenceStartDateTime"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/properties

Removido obrigatóriedade no campo 'issuer'

Remoção

required

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado obrigatóriedade no campo 'startDateTime'

Adição

required

patch/responses/200/data/recurringConfiguration/oneOf/1/sweeping/properties

Adicionado - "startDateTime"

Adição

patch/responses/422/errors/items/code/enum

Adicionado - "PERMISSAO\_INSUFICIENTE"

Adição

enum

patch/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado:

-   CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do consentimento não permite a realização do cancelamento (em status "CONSUMED" ou "REJECTED")
    
-   CAMPO\_NAO\_PERMITIDO: O(s) campo(s) solicitado(s) para edição não podem ser editados.
    

Descrição específica do erro de acordo com o código reportado:

-   CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do consentimento não permite a realização do cancelamento (em status "CONSUMED" ou "REJECTED")
    
-   CAMPO\_NAO\_PERMITIDO: O(s) campo(s) solicitado(s) para edição não podem ser editados.
    
-   PERMISSAO\_INSUFICIENTE: Consentimento possui múltiplas alçadas aprovadoras e não permite a edição pelo usuário atual.
    

patch/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do consentimento não permite a realização do cancelamento (em status "CONSUMED" ou "REJECTED")
    
-   CAMPO\_NAO\_PERMITIDO: O(s) campo(s) solicitado(s) para edição não podem ser editados.
    

Título específico do erro reportado, de acordo com o código enviado:

-   CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO: O status do consentimento não permite a realização do cancelamento (em status "CONSUMED" ou "REJECTED")
    
-   CAMPO\_NAO\_PERMITIDO: O(s) campo(s) solicitado(s) para edição não podem ser editados.
    
-   Permissão insuficiente para edição.
    

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Removido - "month"

Remoção

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/properties

Alterado- "period"

Alteração

Period

Interval

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^(?:\\d{11}|\\d{14})$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "maxLength"

Remoção

4

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "example"

Remoção

CNPJ

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Removido - "pattern"

Remoção

^\[A-Z\]{4}$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/rel

Adicionado - "enum"

Adição
