# Release Notes

v 1.00

## **Objetivo desta página**

Relacionar a lista de iniciativas implementadas em cada uma das Releases da PCM

2026C1800

**Data da release:** 01/09/2026

**Data do Informa:** 26/08/2026

**Número do Informa:**

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Ajustes no Swagger PCM

Alteração

Correções de enum

Correção de enums dos campos status, authorisationFlow, authorisationFlowIntent, dropReason e personType

-   status com trailing space ('PAIRED ')
    
-   authorisationFlow com leading space (' FIDO\_FLOW')
    
-   authorisationFlowIntent com trailing space ('CIBA\_FLOW ')
    
-   dropReason com leading space (' NONE')
    
-   dropReason com valor concatenado ('NO\_CREDENTIAL, NONE')
    
-   personType com valor PESSOA\_JURÍDICA (com acento)
    

-   status sem trailing space ('PAIRED')
    
-   authorisationFlow sem leading space ('FIDO\_FLOW')
    
-   authorisationFlowIntent sem trailing space ('CIBA\_FLOW')
    
-   dropReason sem leading space ('NONE')
    
-   dropReason com valores separados ('NO\_CREDENTIAL'
    
    'NONE')
    
-   personType com valor PESSOA\_JURIDICA (sem acento)
    

Inclusão

Novos enums

Inclusão de enums faltantes no Swagger - redirectType de Hybridfow e Iniciação de Pagamentos - localInstrument

-   Enums no Swagger - redirectType de Hybridfow - AWAITING\_HANDOFF, AWAITING\_USER\_AUTH e AWAITING\_REDIRECT\_TO\_APP
    
-   Enums no Swagger - Iniciação de Pagamentos - localInstrument - DICT, INIC, MANU, QRDN, QRES e AUTO
    

-   Enums no Swagger - redirectType de Hybridfow - AWAITING\_HANDOFF, AWAITING\_USER\_AUTH, AWAITING\_REDIRECT\_TO\_APP, AUTHORISED e REJECTED
    
-   Enums no Swagger - Iniciação de Pagamentos - localInstrument - DICT, INIC, MANU, QRDN, QRES, AUTO, APDN e APES
    

Ajustes na documentação funcional

Alteração

Ajustes diversos

-   Campos obrigatórios de Dados Abertos, Dados Cadastrais e Transacionais, Serviços, Segurança - processTimespan
    
-   Iniciação de Pagamentos - campo paymentType
    
-   Iniciação de Pagamentos (v5) - cancellationReason e cancelledFrom
    
-   Dados Cadastrais e Transacionais e Pagamentos - tokenId
    
-   Dados Cadastrais e Transacionais - Consentimentos - statusSummary
    
-   Portabilidade de Crédito - rejectedBy e rejectionReason
    
-   Portabilidade de Crédito - rejectionReason
    
-   Pagamentos Automáticos - errorCodes
    
-   Pagamentos Sem Redirecionamento - authenticatorAttachment
    
-   Segurança - tokenId
    
-   Estados de Pagamento - regra de validação - clarificação na regra de validação da exigência do status SCHD
    
-   Estados de Pagamento - paymentType
    

-   Campos obrigatórios de Dados Abertos, Dados Cadastrais e Transacionais, Serviços, Segurança - tipo do campo processTimespan = _integer <int16>_
    
-   Iniciação de Pagamentos - paymentType - regra de preenchimento - caminho do purpose = /_data/payment/details/purpose_
    
-   Dados Cadastrais e Transacionais e Pagamentos - tokenId - obrigatório para todos os statusCode
    
-   Dados Cadastrais e Transacionais - Consentimentos - statusSummary - obrigatório para todos os statusCode
    
-   Portabilidade de Crédito - rejectedBy e rejectionReason - regra de preenchimento - obrigatório o envio para status REJECTED, CANCELLED ou PAYMENT\_ISSUE
    
-   Portabilidade de Crédito - rejectionReason - validação por status e rejectedBy
    
-   Pagamentos Automáticos - errorCodes - sem o endpoint /open-banking/automatic-payments/v2/pix/recurring-payments/{originalRecurringPaymentId}/retry na lista de endpoints obrigatórios
    
-   Pagamentos Sem Redirecionamento - authenticatorAttachment - _Deve ser preenchido com a mesma string definida em ".data.authenticatorAttachment". Não havendo string, deve ser explicitamente enviada esse additionalInfo como sendo uma string vazia.​_
    
-   Segurança - tokenId - obrigatoriedade de envio para os endpoints /register e /register{clientId}
    
-   Estados de Pagamento - regra de validação Ausência de status SCHD em Estados de Pagamento - _Caso o pagamento não tenha sido rejeitado ou cancelado, deve haver obrigatoriamente um Estado de Pagamento SCHD_
    
-   Estados de Pagamento - paymentType - SWEEPING, IMMEDIATE, SCHEDULED, RECURRENT ou AUTOMATIC
    
-   Estados de Pagamento dentro da estrutura de pagamentos
    

-   Campos obrigatórios de Dados Abertos, Dados Cadastrais e Transacionais, Serviços, Segurança - tipo do campo processTimespan = _number_.
    
-   Iniciação de Pagamentos - paymentType - regra de preenchimento - caminho do purpose = _/data/payment/purpose_
    
-   Iniciação de Pagamentos (v5) - obrigatoriedade de envio dos campos cancellationReason e cancelledFrom na tabela de additionalInfo e regras de validação.
    
-   Dados Cadastrais e Transacionais e Pagamentos - tokenId - obrigatório para todos os statusCode exceto 4xx e 5xx
    
-   Dados Cadastrais e Transacionais - Recursos - statusSummary - obrigatório somente para statusCode 200
    
-   Portabilidade de Crédito - rejectedBy e rejectionReason - regra de preenchimento - obrigatório o envio para status REJECTED ou CANCELLED
    
-   Portabilidade de Crédito - rejectionReason - lista simples de valores possíveis, sem validação de status e rejectedBy
    
-   Pagamentos Automáticos - errorCodes - obrigatório também para o endpoint /open-banking/automatic-payments/v2/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   Pagamentos Sem Redirecionamento - authenticatorAttachment - _Deve ser preenchido com a mesma string definida em ".data.authenticatorAttachment". Não havendo string, deve ser explicitamente enviada esse additionalInfo como sendo uma string vazia.​_  
    _Caso seja enviado um valor neste campo, o mesmo será validado contra o domínio dele_.
    
-   Segurança - tokenId - endpoints /register e /register{clientId} não têm obrigatoriedade de envio
    
-   Estados de Pagamento - regra de validação Ausência de status SCHD em Estados de Pagamento - _Para pagamentos do tipo SCHEDULED ou RECURRENT, caso o pagamento não tenha sido rejeitado ou cancelado, deve haver obrigatoriamente um Estado de Pagamento SCHD_
    
-   Estados de Pagamento - paymentType - SWEEPING, IMMEDIATE, SCHEDULED, RECURRENT, AUTOMATIC, WITHDRAW ou CHANGE
    
-   Reorganização de Estados de Pagamento para uma estrutura apartada
    
-   Criação de uma estrutura para detalhamento de campos ou regras extensas (dropReason)
    

FAQ PCM

Alteração

Revisão do conteúdo

Ajustes nas respostas desatualizadas

Página desatualizada

Conceitos e respostas ajustados

Alteração no dropReason

Alteração

Inclusão de enum

Incluído o enum CREDENTIAL\_UNAVAILABLE

enum do dropReason = NO\_AUTHORITY, NO\_AUTHORITY\_PERSON\_MISMATCH, NO\_CREDENTIAL, NONE

-   enum do dropReason = NO\_AUTHORITY, NO\_AUTHORITY\_PERSON\_MISMATCH, NO\_CREDENTIAL, NONE, CREDENTIAL\_UNAVAILABLE
    
-   Página dedicada às novas regras do dropReason
    

Refinamento da regra de obrigatoriedade do campo recurringConsentId

Alteração

Ajuste na regra de obrigatoriedade do recurringConsentId

Alteração nos endpoints / statusCode

Todos os statusCode para os endpoints:

-   /open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   /open-banking/automatic-payments/v_x_/pix/recurring-payments
    
-   /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry
    

-   Endpoint /open-banking/automatic-payments/v2/recurring-consents - obrigatório para POST e statusCode exceto 4xx e 5xx
    
-   Endpoint /open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId} - obrigatório para GET ou PATCH para qualquer statusCode
    
-   Endpoints /open-banking/automatic-payments/v2/pix/recurring-payments, /open-banking/automatic-payments/v2/pix/recurring-payments/{recurringPaymentId} e  
    /open-banking/automatic-payments/v2/pix/recurring-payments/{originalRecurringPaymentId}/retry - obrigatório para POST, GET ou PATCH para qualquer statusCode
    

2026B1800

**Data da release:** 11/06/2026

**Data do Informa:** 11/06/2026

**Número do Informa:** 906

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Novos endpoints aceitos pela PCM

Inclusão

Inclusão de novos endpoints da API de Pagamentos

Endpoints incluídos:

-   /open-banking/payments/v5/consents
    
-   /open-banking/payments/v5/consents/{consentId}
    
-   /open-banking/payments/v5/consents/{consentId}/pix/payments
    
-   /open-banking/payments/v5/pix/payments
    
-   /open-banking/payments/v5/pix/payments/{paymentId}
    

Somente endpoints da v4 da API de Pagamentos

Endpoints das v4 e v5 da API de Pagamentos

Dados Abertos - Campos Obrigatórios e Opcionais

Alteração

Reestruturação da página

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Opendata API e quais campos são retornados no response
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    
-   Inclusão da coluna “Regras de Preenchimento”
    

Tabela com campos misturados entre campos de POST e RESPONSE da PCM, falta da regra de preenchimento

Tabelas separadas para campos que devem ser enviados via POST, com regra de preenchimento e campos retornados em RESPONSE, dando clareza do contexto de cada campo

Alteração

processTimespan

-   Alteração do exemplo para refletir de forma correta o valor esperado
    
-   Alteração da definição
    

120

Tempo em milissegundos inteiros decorrido desde o registro do timestamp até a chegada do primeiro byte da resposta do server.

120.000000

Tempo em milissegundos inteiros decorrido desde o recebimento do request até o momento imediatamente anterior ao envio do primeiro byte da resposta.

Inclusão

statusCode

Inclusão de regra de preenchimento

Sem regra de preenchimento

No contexto operacional do Open Finance, de acordo com a definição de governança, a instituição consumidora (Client) deve aguardar até 15 segundos pela resposta da instituição provedora (Server).

Caso esse período seja atingido ou excedido (≥ 15 segundos) sem resposta, a instituição consumidora pode, por decisão própria e para preservar a experiência do usuário, encerrar a conexão. Nessa situação, o evento deve ser reportado com status code 408, caracterizando timeout na interação, ainda que a interrupção tenha sido iniciada pelo lado consumidor.

Por sua vez, quando a instituição estiver atuando como provedora (Server) e encerrar a conexão por não ter recebido a requisição completa dentro do tempo esperado, também deverá reportar status code 408, em conformidade com a RFC 7231.

Inclusão

endpoint

Inclusão da regra de preenchimento

Sem regra de preenchimento

Identificação do Endpoint: Deve ser preenchido com o identificador padronizado do endpoint, conforme uma lista (ENUM) predefinida.Não usar o caminho real: É fundamental NÃO utilizar o caminho completo da requisição original, que inclui dados variáveis (ex: IDs).  
Exemplo: Se a requisição foi para /open-banking/credit-cards-accounts/v1/accounts/123456789/transactions, o valor a ser enviado no endpoint deve ser /open-banking/credit-cards-accounts/v1/accounts/{creditCardAccountId}/transactions. O dado real 123456789 não deve ser enviado no campo endpoint

Dados Abertos - Obrigatoriedade de additionalInfo

Exclusão

tokenId

Remoção do campo tokenId, pois o mesmo não existe dentro do contexto de Dados Abertos

tokenId declarado como um campo obrigatório para Dados Abertos

tokenId removido da tabela

Alteração

Versões das APIs

-   Atualização das versões de API
    
    -   Atendimento: v2
        
    -   Previdência: v2
        
    -   Seguros: v2
        
    -   Títulos de Capitalização: v2
        
    -   Remoção do grupo Produtos e Serviços, que foi desmembrado em grupos menores
        
-   Inclusão de novos grupos:
    
    -   Contas
        
    -   Cartão de Crédito
        
    -   Direitos Creditórios Descontados
        
    -   Empréstimos
        
    -   Financiamentos
        
    -   Adiantamento a Depositantes
        

-   Atendimento: v1
    
-   Previdência: v1
    
-   Seguros: v1
    
-   Títulos de Capitalização: v1
    
-   Produtos e Serviços v1
    

-   Atendimento: v2
    
-   Previdência: v2
    
-   Seguros: v2
    
-   Títulos de Capitalização: v2
    
-   Contas: v1
    
-   Cartão de Crédito: v1
    
-   Direitos Creditórios Descontados: v1
    
-   Empréstimos: v1
    
-   Financiamentos: v1
    
-   Adiantamento a Depositantes: v1
    

Dados Cadastrais e Transacionais - Campos Obrigatórios e Opcionais

Alteração

Reestruturação da página

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Private API, quais campos são retornados no response e quais são adicionais ao método GET
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    

Tabela com campos misturados entre campos de POST, GET e RESPONSE da PCM

Tabelas separadas para campos que devem ser enviados via POST, campos retornados em RESPONSE e em GET, dando clareza do contexto de cada campo

Alteração

clientSSId

Correção nas roles obrigatórias, o correto é somente CLIENT

CLIENT / SERVER

CLIENT

Alteração

processTimespan

Alteração do exemplo para refletir de forma correta o valor esperado

120

120.000000

Alteração

statusCode

Maior esclarecimento na regra de preenchimento

Para informações adicionais, por favor consulte Reporte - Área do Desenvolvedor - Open Finance Brasil - Área do Desenvolvedor

No contexto operacional do Open Finance, de acordo com a definição de governança, a instituição consumidora (Client) deve aguardar até 15 segundos pela resposta da instituição provedora (Server).

Caso esse período seja atingido ou excedido (≥ 15 segundos) sem resposta, a instituição consumidora pode, por decisão própria e para preservar a experiência do usuário, encerrar a conexão. Nessa situação, o evento deve ser reportado com status code 408, caracterizando timeout na interação, ainda que a interrupção tenha sido iniciada pelo lado consumidor.

Por sua vez, quando a instituição estiver atuando como provedora (Server) e encerrar a conexão por não ter recebido a requisição completa dentro do tempo esperado, também deverá reportar status code 408, em conformidade com a RFC 7231.

Dados Cadastrais e Transacionais - Obrigatoriedade de additionalInfo

Alteração

Consentimento - journeyIsLinked

Alteração na regra de preenchimento

Deve ser preenchido com a string obtida no campo journey.isLinked, após a chamada inicial na API “POST /consents” se o parâmetro isLinked estiver preenchido na requisição no contexto de Jornada Otimizada

**Não deve ser reportado o campo journeyIsLinked ou journeyLinkId quando:**

-   O consentimento for criado fora do contexto de Jornada Otimizada, ou seja, quando não houver indicação de journey.isLinked=true no payload da criação do consentimento
    
-   O consentimento for do tipo convencional (ex.: consents isolados, enrollments isolados, recurring-consents isolados), sem vínculo com outro consentimento
    

Nestes casos, a transmissora/detentora deve omitir os campos journeyIsLinked e journeyLinkId no reporte à PCM

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.isLinked”, retornado após a chamada inicial na API “POST /consent” (Pagamentos Automáticos) ou “POST /enrollments” (Jornada Sem Redirecionamento) em caso de Jornada Otimizada. Em casos em que a informação não está disponível espera-se o envio do valor FALSE.

Alteração

Recursos - statusSummary

Alteração na regra de preenchimento

Sumarização da quantidade por ENUM observado em _data.status_

Sumarização da quantidade por ENUM observado em data.status  
Obrigatório para PF e PJ

Pagamentos - Dados Relativos a Estados de Pagamento (Definição do Produto)

Alteração

paymentList

Correção da descrição do campo paymentList, dando maior clareza quanto ao seu escopo

Lista de dados de pagamentos com agendamento recorrentes.

Lista de dados de pagamentos com agendamento imediatos, agendados ou recorrentes.

Alteração

eventDateTime

Complemento da descrição do campo eventDateTime, incluindo o escopo de agendamento aos demais estados

Data e hora associada a mudança de estados finais reportados abaixo, como liquidação, rejeição ou cancelamento. Formato AAAA-MM-DD hh:mm:ss reportado em UTC 0

Data e hora associada à mudança de estados reportados abaixo, como agendamento, liquidação, rejeição ou cancelamento. Formato AAAA-MM-DD hh:mm:ss reportado em UTC 0

Alteração

Regra de Validação – paymentId

Complemento da regra de validação da quantidade de paymentIds distintos para um mesmo consentId, passando a validar também a data do último pagamento

Para _paymentType_ RECURRENT, validar que não há mais de 60 _paymentIds_ por _consentId._ Se houverem mais de 60, ingerir e criticar

Para _paymentType_ RECURRENT, validar que não há mais de 60 _paymentIds_ por _consentId_s, independentemente do modelo de recorrência definido no consentimento. A data do último pagamento agendado não pode ultrapassar o correspondente dia e mês do segundo ano subsequente à data de criação do consentimento (Ex.: consentimento criado em 15/03/2026 admite agendamentos até 15/03/2028)_._ Se houverem mais de 60 ou a data do último pagamento não estiver de acordo com a regra, ingerir e criticar.

Pagamentos - Campos Obrigatórios e Opcionais

Alteração

Reestruturação da página

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Private API, quais campos são retornados no response e quais são adicionais ao método GET
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    

Tabela com campos misturados entre campos de POST, GET e REPONSE da PCM

Tabelas separadas para campos que devem ser enviados via POST, campos retornados em RESPONSE e em GET, dando clareza do contexto de cada campo

Alteração

clientSSId

Correção nas roles obrigatórias, o correto é somente CLIENT

CLIENT / SERVER

CLIENT

Alteração

processTimespan

Alteração do exemplo para refletir de forma correta o valor esperado

120

120.000000

Alteração

statusCode

Maior esclarecimento na regra de preenchimento

Para informações adicionais, por favor consulte Reporte - Área do Desenvolvedor - Open Finance Brasil - Área do Desenvolvedor

No contexto operacional do Open Finance, de acordo com a definição de governança, a instituição consumidora (Client) deve aguardar até 15 segundos pela resposta da instituição provedora (Server).

Caso esse período seja atingido ou excedido (≥ 15 segundos) sem resposta, a instituição consumidora pode, por decisão própria e para preservar a experiência do usuário, encerrar a conexão. Nessa situação, o evento deve ser reportado com status code 408, caracterizando timeout na interação, ainda que a interrupção tenha sido iniciada pelo lado consumidor.

Por sua vez, quando a instituição estiver atuando como provedora (Server) e encerrar a conexão por não ter recebido a requisição completa dentro do tempo esperado, também deverá reportar status code 408, em conformidade com a RFC 7231.

Pagamentos - Obrigatoriedade de additionalInfo

Inclusão

Iniciação de Pagamentos - paymentList

Inclusão de regra de preenchimento para dar maior clareza da regra do campo

Sem regra de preenchimento

Deve ser enviado obrigatoriamente para os tipos de pagamento (paymentType) IMMEDIATE, SCHEDULED e RECURRENT, mesmo que a lista contenha apenas um item. Para o mesmo consentId não podem ser reportados nesta lista mais do que 60 paymentId.

Inclusão

Iniciação de Pagamentos - paymentType

Inclusão de regra de preenchimento específica para a v5 de pagamentos

Sem regra de preenchimento para v5

-   Se /data/payment/details/purpose = IMMEDIATE, paymentType = IMMEDIATE
    
-   Se /data/payment/details/purpose = SINGLE\_SCHEDULED, paymentType = SCHEDULED
    
-   Se /data/payment/details/purpose = RECURRENT\_SCHEDULED, paymentType = RECURRENT
    
-   Se /data/payment/details/purpose = WITHDRAW, paymentType = WITHDRAW
    
-   Se /data/payment/details/purpose = CHANGE, paymentType = CHANGE
    

Inclusão

Iniciação de Pagamentos - localInstrument

Inclusão de domínio

DICT, INIC, MANU, QRDN, QRES, AUTO

DICT, INIC, MANU, QRDN, QRES, AUTO, APDN, APES

Inclusão

Iniciação de Pagamentos - rejectionReasonCode

Inclusão de domínio

Lista de rejectionReasonCode antes da v5 de Pagamentos

Lista de rejectionReasonCode com os novos motivos de rejeição:  
AUTENTICACAO\_DIVERGENTE​

-   CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   QRCODE\_INVALIDO
    
-   PERMISSAO\_INSUFICIENTE
    

Inclusão

Iniciação de Pagamentos - errorCodes

Inclusão de domínio

Lista de errorCodes antes da v5 de Pagamentos

Lista de errorCodes com o novo erro:

-   PROPOSITO\_INVALIDO
    

Exclusão

Jornada Sem Redirecionamento

Remoção da versão v1 da API nos endpoints válidos

Endpoints da v1 da API sendo apresentados como válidos

Somente endpoints da v2 são válidos

Inclusão

Jornada Sem Redirecionamento - authenticatorAttachment

Incluído o domínio do campo

Sem domínio declarado

platform, cross-platform

Inclusão

Jornada Sem Redirecionamento - platform

Incluído o domínio do campo

Sem domínio declarado

ANDROID, BROWSER, CROSS\_PLATFORM, IOS

Inclusão

Jornada Sem Redirecionamento - revocationReasonCode

Incluída a regra de preenchimento

Sem regra de preenchimento

Deve ser preenchido com a mesma string obtida no ".data.cancellation.reason.revocationReason". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Dever ser enviado quando o status for REVOKED

Inclusão

Jornada Sem Redirecionamento - tokenId

Incluído o endpoint /open-banking/enrollments/v2/recurring-consents/{recurringConsentId}/authorise

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals  
/open-banking/enrollments/v_x_/consents/{consentId}/authorise  
/open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals  
/open-banking/enrollments/v_x_/consents/{consentId}/authorise  
/open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry  
/open-banking/enrollments/v2/recurring-consents/{recurringConsentId}/authorise

Alteração

Jornada Sem Redirecionamento - journeyIsLinked

Alteração da regra de preenchimento

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.isLinked”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada

Deve ser preenchido com a string obtida no campo journey.isLinked, após a chamada inicial na API “POST /consents” se o parâmetro isLinked estiver preenchido na requisição no contexto de Jornada Otimizada. Em casos em que a informação não está disponível espera-se o envio do valor FALSE.

Alteração

Jornada Sem Redirecionamento - journeyLinkId

Complemento da regra de preenchimento

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.linkId”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada.

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.linkId”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada.  
Deve ser enviado se journeyIsLinked for TRUE

Alteração

Pagamentos Automáticos - authorisationFlow

Ajuste na descrição do campo

Identifica o fluxo de autorização em que um pagamento ou operação foi solicitado

Identifica o fluxo de autorização em que um pagamento ou operação foi solicitado. Descreve como o autenticador (por exemplo, um dispositivo FIDO) está anexado ao cliente que realiza a autenticação (ex: platform para autenticadores integrados como Face ID ou cross-platform para chaves de segurança USB).

Alteração

Pagamentos Automáticos - errorCodes

Correção do campo, estava duplicado. Foi dividido em regras para statusCode 422 e statusCode 4xx / 5xx exceto 422, a exemplo de Iniciação de Pagamentos

Linhas duplicadas para errorCodes

Linhas separadas em 422 e demais erros, a exemplo da Iniciação de Pagamentos

Inclusão

Pagamentos Automáticos - interval

Incluído domínio do campo

Sem domínio delcarado

SEMANAL, MENSAL, TRIMESTRAL, SEMESTRAL, ANUAL

Inclusão

Pagamentos Automáticos - isRetryAccepted

Incluído domínio do campo

Sem domínio delcarado

TRUE, FALSE

Alteração

Pagamentos Automáticos - originalRecurringPaymentId

Complemento da regra de preenchimento

Preencher com o valor do campo ".data.originalRecurringPaymentId"  
Deve ser preenchido quando paymentType for AUTOMATIC

Preencher com o valor do campo ".data.originalRecurringPaymentId"  
Para os endpoints /open-banking/automatic-payments/v_x_/pix/recurring-payments e /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}, métodos GET e PATCH, a informação só deve ser enviada se retornado no response da API.  
Deve ser preenchido quando paymentType for AUTOMATIC

Inclusão

Pagamentos Automáticos - originalRecurringPaymentId

Inclusão do endpoint /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

Alteração

Pagamentos Automáticos - paymentReference

Complementada a regra de preehchimento

Preencher com o valor do campo ".data.paymentReference"

Deve ser preenchido quando paymentType for AUTOMATIC

Preencher com o valor do campo "paymentReference"  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.  
Deve ser preenchido quando paymentType for AUTOMATIC

Alteração

Pagamentos Automáticos - paymentType

Complementada a regra de preehchimento

Identifica o modo de pagamento acionado no consentimento e deve ser preenchido de acordo com o campo ".data.recurringConfiguration/oneOf"

**IMMEDIATE**: Pix sem configuração de agendamento  
**SCHEDULED**: Pix com configuração de agendamento  
**RECURRENT**: Pix com agendamento e recorrência  
**SWEEPING**: Chamadas de pagamentos inteligentes  
**AUTOMATIC**: Pagamentos automáticos

Identifica o modo de pagamento acionado no consentimento e deve ser preenchido de acordo com o campo ".data.recurringConfiguration/oneOf"

**IMMEDIATE**: Pix sem configuração de agendamento  
**SCHEDULED**: Pix com configuração de agendamento  
**RECURRENT**: Pix com agendamento e recorrência  
**SWEEPING**: Chamadas de pagamentos inteligentes  
**AUTOMATIC**: Pagamentos automáticos  
**WITHDRAW:** PIX Saque  
**CHANGE:** PIX Troco

Alteração / Inclusão

Pagamentos Automáticos - recurringConsentId

Ajustada a descrição, incluída a regra de preenchimento e o endpoint /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

-   O consentId é o identificador único do consentimento e deverá ser um URN - Uniform Resource Name.
    
-   /open-banking/automatic-payments/v_x_/recurring-consents  
    /open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
    /open-banking/automatic-payments/v_x_/pix/recurring-payments  
    /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    

-   Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada
    
-   Preencher com o valor do campo ".data.recurringConsentId"​
    
-   /open-banking/automatic-payments/v_x_/recurring-consents  
    /open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
    /open-banking/automatic-payments/v_x_/pix/recurring-payments  
    /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
    /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry
    

Alteração

Pagamentos Automáticos - recurringPaymentDate

Complementada a descrição

Data em que o pagamento será realizado

Data em que o pagamento será realizado no formato timezone UTC-3 (UTC time format)

Alteração / Inclusão

Pagamentos Automáticos - recurringPaymentId

Ajustadas a descrição e a regra de preenchimento, incluído padrão do campo e o endpoint endpoint /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

-   Contagem de acionamentos feitos no pagamento​
    
-   Para Pagamentos v4: Preencher com o valor do campo "/data/paymentId"  
    Para Pagamentos Automáticos v2: Preencher com o valor do campo "/data/recurringPaymentId"​
    
-   /open-banking/automatic-payments/v_x_/pix/recurring-payments  
    /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    

-   Código ou identificador único informado pela instituição detentora da conta para representar a iniciação de pagamento.
    
-   Preencher com o valor do campo ".data.recurringPaymentId"​
    
-   ^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$
    
-   /open-banking/automatic-payments/v_x_/pix/recurring-payments  
    /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
    /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry
    

Alteração

Pagamentos Automáticos - referenceStartDate

Ajustada a descrição

Data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência

Data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data

Inclusão

Pagamentos Automáticos - rejectedBy

Incluída a regra de preenchimento

Sem regra de preenchimento

Deve ser preenchido com a mesma string obtida no ".data.rejection.rejectedBy". Obrigatório somente quando o status for RJCT ou REJECTED

Inclusão

Pagamentos Automáticos - rejectedFrom

Incluída a regra de preenchimento

Sem regra de preenchimento

Deve ser preenchido com a mesma string obtida no ".data.rejection.rejectedFrom". Obrigatório somente quando o status for RJCT ou REJECTED

Alteração

Pagamentos Automáticos - rejectionReasonCode

Complementada a regra de preenchimento

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.code". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.code". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista  
Obrigatório somente quando o status for RJCT ou REJECTED

Inclusão

Pagamentos Automáticos - rejectionReasonDetail

Inclusão na regra de preenchimento

Sem regra de preenchimento

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Obrigatório somente quando o status for RJCT ou REJECTED

Inclusão

Pagamentos Automáticos - revocationReasonCode

Inclusão na regra de preenchimento

Sem regra de preenchimento

Deve ser preenchido com a string obtida no campo ".data.revocation.reason.code". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista  
Obrigatório somente quando o status for REVOKED

Inclusão

Pagamentos Automáticos - revocationReasonDetail

Inclusão na regra de preenchimento

Sem regra de preenchimento

Deve ser preenchido com a string obtida no campo ".data.revocation.reason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Obrigatório somente quando o status for REVOKED

Inclusão

Pagamentos Automáticos - status

Inclusão do endpoint _/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry_

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

/open-banking/automatic-payments/vx/pix/recurring-payments  
/open-banking/automatic-payments/vx/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/recurring-consents  
/open-banking/automatic-payments/vx/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

Inclusão

Pagamentos Automáticos - tokenId

Inclusão do endpoint _/open-banking/automatic-payments/vx/pix/recurring-payments/{originalRecurringPaymentId}/retry_

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/pix/recurring-payments/{originalRecurringPaymentId}/retry

Jornada Otimizada

Alteração

journeyIsLinked

Alteração da regra de preenchimento

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.isLinked”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada.

Deve ser preenchido com a string obtida no campo journey.isLinked, após a chamada inicial na API “POST /enrollments” se o parâmetro isLinked estiver preenchido na requisição no contexto de Jornada Otimizada. Em casos em que a informação não está disponível espera-se o envio do valor FALSE.

Alteração

journeyLinkId

Complementada a regra de preenchimento

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.i sLinked”, retornado após a chamada inicial na API “POST /consent” em caso de Jornada Otimizada

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.linkId”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada  
Deve ser enviado se journeyIsLinked for TRUE

Alteração

Exceções de reporte

Removida a exceção de reporte e incluída uma observação importante em seu lugar

-   Não deve ser reportado o campo journeyIsLinked ou journeyLinkId quando:
    
    -   O consentimento for criado fora do contexto de Jornada Otimizada, ou seja, quando não houver indicação de journey.isLinked=true no payload da criação do consentimento
        
    -   O consentimento for do tipo convencional (ex.: consents isolados, enrollments isolados, recurring-consents isolados), sem vínculo com outro consentimento
        
-   Nestes casos, a transmissora/detentora deve omitir os campos journeyIsLinked e journeyLinkId no reporte à PCM
    

Para estes endpoints os campos journeyIsLinked e journeyLinkId devem ser preenchidos. Caso se trate de uma Jornada Otimizada, em jjourneyIsLinked enviar TRUE; caso contrário, enviar FALSE. O campo jounryLinkId deve ser enviado caso journeyIsLinked seja TRUE.

Portabilidade de Crédito - Campos Obrigatórios e Opcionais

Alteração

Reestruturação da página

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Opendata API e quais campos são retornados no response
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    

Tabela com campos misturados entre campos de POST, GET e REPONSE da PCM

Tabelas separadas para campos que devem ser enviados via POST, campos retornados em RESPONSE e em GET, dando clareza do contexto de cada campo

Alteração

processTimespan

Alteração do exemplo para refletir de forma correta o valor esperado

120

120.000000

Alteração

statusCode

Maior esclarecimento na regra de preenchimento

Para informações adicionais, por favor consulte Reporte - Área do Desenvolvedor - Open Finance Brasil - Área do Desenvolvedor

No contexto operacional do Open Finance, de acordo com a definição de governança, a instituição consumidora (Client) deve aguardar até 15 segundos pela resposta da instituição provedora (Server).

Caso esse período seja atingido ou excedido (≥ 15 segundos) sem resposta, a instituição consumidora pode, por decisão própria e para preservar a experiência do usuário, encerrar a conexão. Nessa situação, o evento deve ser reportado com status code 408, caracterizando timeout na interação, ainda que a interrupção tenha sido iniciada pelo lado consumidor.

Por sua vez, quando a instituição estiver atuando como provedora (Server) e encerrar a conexão por não ter recebido a requisição completa dentro do tempo esperado, também deverá reportar status code 408, em conformidade com a RFC 7231.

Hybrid Flow - Campos Obrigatórios e Opcionais

Alteração

Reestruturação da página

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Hybrid Flow API e quais campos são retornados no response
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    

Tabela com campos misturados entre campos de POST e RESPONSE da PCM

Tabelas separadas para campos que devem ser enviados via POST e campos retornados em RESPONSE, dando clareza do contexto de cada campo

Segurança - Campos Obrigatórios e Opcionais

Inclusão

Criação da página

Criação da página de campos obrigatórios e opcionais de Segurança

Página não existente

Página criada com os campos obrigatórios e opcionais de Segurança

Segurança - Obrigatoriedade de additionalInfo

Alteração

consentId

Complementada a regra de preenchimento

Deve ser preenchido com a mesma string obtida no campo .data.consentId retornado após a chamada inicial na API "POST /consent

Deve ser preenchido com a mesma string obtida no campo .data.consentId retornado após a chamada inicial na API "POST /consent”. \*Ao reportar o uso de um endpoint /token, o identificador único de consentimento só será reportado nos casos em que "grant\_type" é do tipo "authorization\_code" ou do tipo "refresh\_token"

Alteração

grantType

Complementada a regra de preenchimento

Deve ser preenchido com a mesma string enviada no campo ".grant\_type "​

Deve ser preenchido com a mesma string enviada no campo ".grant\_type "​  
**AUTHORIZATION\_CODE:** Utilizado na autorização de acesso a um recurso por meio de login de usuário  
**REFRESH\_TOKEN:** Utilizado para obter um novo token de acesso quando o token anterior expira  
**CLIENT\_CREDENTIALS:** Utilizado na autorização de acesso entre aplicações onde não há a figura do usuário

Alteração

webhookEnable

Correção na regra de preenchimento; não deve ser enviado um valor booleano TRUE ou FALSE, mas sim uma string contendo ou TRUE ou FALSE.

Valor booleano

Valor string

Estoque de Consentimentos - Campos Obrigatórios e Opcionais

Alteração

Reestruturação da página

Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Consents API e quais campos são retornados no response

Tabela com campos misturados entre campos de POST e RESPONSE da PCM

Tabelas separadas para campos que devem ser enviados via POST e campos retornados em RESPONSE, dando clareza do contexto de cada campo

Notificações via ticket

Alteração

SLA de envio 99%

Maior clareza na referência do percentual de SLA

perc\_sla: percentual calculado do SLA

perc\_sla\_metodo\_endpoint: percentual calculado do SLA por método e endpoint

Alteração

Comportamento e Qualidade Estados de Pagamentos

Revisão e alteração das regras de validação

Regras removidas:

-   Não encontrado schedule para pagamento agendado/recorrente no endpoint de consentimentos
    
-   Tipo de pagamento IMMEDIATE / SWEEPING incompatível com agendamento
    
-   Tipo de pagamento SCHEDULED só pode ter tipo de agendamento single
    
-   Tipo de pagamento RECURRENT não pode ter tipo de agendamento single
    
-   Última parcela vigente não reportada em estados de pagamento
    

Regras alteradas:

-   paymentId não encontrado em estados de pagamento
    
-   Último estado de pagamento informado inconsistente: Exceto se a parcela ainda não venceu, nem foi cancelada, obrigatoriamente o último estado de pagamento deve ser ACSC, RJCT ou CANC.
    

Regras alteradas:

-   paymentId / recurringPaymentId não encontrado em estados de pagamento
    
-   Último estado de pagamento informado inconsistente: Dentre os status ACSC, RJCT e CANC, o último status do Pagamento não deve ser diferente do informado no Estado de Pagamento.
    

Nova regra:

-   Ausência de status SCHD em Estados de Pagamento: Caso o pagamento não tenha sido rejeitado ou cancelado, deve haver obrigatoriamente um Estado de Pagamento SCHD
    

Regras de Validação (geral)

Alteração

Campos alterados em cada produto

Ajuste nas regras de validação para refletir todas as mudanças pontuadas nesta release

Regras antigas

Regras ajustadas

Regras de descarte (gera)

Alteração

Regras de descartes de todos os produtos

Regras de descarte atualizadas com os motivos de descarte dos últimos 8 meses

Regras de descarte até 08/2025

Regras de descarte até 04/2026

Swagger

Alteração

Campos alterados em cada produto

Ajuste no swagger para refletir todas as mudanças pontuadas nesta release

Swagger destaulizado

Swagger atualizado

2026A1800

**Data da release:** 17/03/2026

**Data do Informa:** 11/03/2026

**Número do Informa:** 859 / 860 / 867

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Inclusão de novo endpoint para Portabilidade de Crédito

Inclusão

Novo endpoint /credit-operations/{contractId}/portability-eligibility ingerido pela PCM

Ingestão e monitoramento do novo endpoint /credit-operations/{contractId}/portability-eligibility de Portabilidade de Crédito

Endpoint não monitorado pela PCM

Endpoint sendo monitorado pela PCM

Inclusão na documentação do endpoint /credit-operations/{contractId}/portability-eligibility da Portabilidade de Crédito

Inclusão

Inclusão do endpoint na validação dos campos de Portabildiade de Crédito

Inclusão do endpoint na validação dos campos:

-   clientOrgId
    
-   clientSSId
    
-   consentId
    
-   correlationId
    
-   endpoint
    
-   endpointUriPrefix
    
-   errorCode
    
-   fapiInteractionId
    
-   httpMethod
    
-   serverOrgId
    
-   statusCode
    
-   timestamp
    

Validação dos campos não consideravam o novo endpoint.

Documentação das regras de validação atualizada com o novo endpoint

Criação do fluxo fresh (/token-fresh), que sempre gera um token novo, ignorando qualquer token em cache para leitura.

Inclusão

Inclusão de novo fluxo para obtenção de token

É possível utilizar o fluxo fresh, ficando a cargo das instituições o comportamento mais adequado a cada situação.

`<endereço de autenticação conforme ambiente>/token-fresh/`

O fluxo fresh sempre gera um token novo, ignorando qualquer token em cache para leitura. Após a leitura, salva esse token em cache.

O comportamento desse endpoint é:

-   Ao chamar o endpoint fresh, o sistema **não reutiliza** token de cache existente.
    
-   O sistema chama o provedor de autenticação e obtém **um token novo**.
    
-   Em seguida, esse token novo **também é gravado no cache**.
    
-   Depois disso, uma chamada ao endpoint `/token` pode retornar esse token recém-gerado, desde que ele ainda esteja válido.
    

Em resumo: **fresh ignora cache na entrada, mas alimenta cache na saída**.

Para a maioria das requisições, o uso de **token em cache continua sendo o comportamento padrão**, trazendo:

-   menor latência
    
-   menos chamadas externas
    
-   melhor escalabilidade do sistema
    

Isso mantém o sistema **rápido e eficiente para uso cotidiano**.

Não era possível gerar um novo token, sendo obrigatório sempre a utilização do token em cache

Possibilidade de geração de novo token que ignora o que está armazenado em cache

Envio dos tickets de validação - comportamento e qualidade de Estados de Pagamento, onde é feita a verificação entre a parametrização dos pagamentos realizada através da API Private, nos reportes de Pagamentos, e seus respectivos estados enviados através da API Payment Status.

Inclusão

Emissão de novo ticket de validação dos dados referentes aos Estados de Pagamento

As regras de validação podem ser encontradas em: [https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/1588461583](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/1588461583)

Integração entre os reportes de pagamento e seus respectivos estados sem monitoramento

Criação das regras de validação e emissão de tickets correspondentes

Obrigatoriedade de additionalInfo de Pagamantos Automáticos

Alteração

Remoção do campo consentId e inclusão do recurringConsentId na tabela de additionalInfo de Pagamentos Automáticos

Explicitação da obrigatoriedade de envio do campo recurringConsentId em pagamentos automáticos, em substituição ao consentId.

Dados de consentimento dos reportes sendo recebidos no additionalInfo consentId

Dados de consentimento dos reportes sendo recebidos no additionalInfo recurringConsentId

Unificação das tabelas de additionalInfo dos produtos Pagamentos Automáticos e Exclusivo PIX Automático

Alteração

Unificação das tabelas de regras de validação

Com a desativação da v1 de Pagamentos Automáticos fez-se necessária a unificação das tabelas, visto que a divisão estava sendo mantida única e exclusivamente para manter o histórico de regras de validação da v1 e as regras de PIX Automático da v2.

Tabelas de campos additionalInfo de Pagamentos Automáticos e PIX Automáticos distintas

Tabela unificada sob o nome de additionalInfo de Pagamentos Automáticos

2025D1800

**Data da release:** 17/11/2025

**Data do Informa:** 18/11/2025

**Número do Informa:** 815 / 823

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Reestruturação da documentação da PCM, reorganizando os itens por contexto

Alteração

Reorganização da estrutura da árvore

Principais benefícios:

-   Organização dos itens por contexto, de forma que siga uma jornada de construção e entendimento dentro do contexto da PCM.
    

Itens “soltos” dentro da estrutura da PCM, unificação de itens por tipo (validação, addinfo, descartes) e não por contexto.

Criação de árvores de contexto que mostrem o contexto da PCM dentro de um fluxo.

Inclusão da documentação das regras de descarte de Portabilidade de Crédito

Inclusão

Disponibilização das regras de descarte de Portabilidade de Crédito

As regras de descarte de reportes de Portabilidade de Crédito não estavam documentadas.

Regras de descarte de reportes de Portabilidade de Crédito não documentadas.

Documentação das regras de descarte de reportes de Portabilidade de Crédito.

Ajustes na documentação de campos obrigatórios e opcionais de Portabilidade de Crédito

Alteração

Inclusões, exclusões e adequações dos campos da Portabilidade de Crédito na PCM

-   Inclusão de http code e endpoints/versões
    
-   Adequação da obrigatoriedade de envio de acordo com o statusCode
    
-   Inclusão dos campos creationDateTime, consentId e errorCode
    
-   Remoção dos campos originalContractTerm, propositionTerm e contractId
    
-   Ajustes nas regras de preenchimento para tornar mais claro a origem do dado
    

Tabela de campos obrigatórios e opcionais não aderentes às alterações realizadas no produto

Tabela de campos obrigatórios e opcionais alinhado com as últimas atualizações do produto

Revisão nas regras de descarte de reportes de Portabilidade de Crédito

Alteração

Regras de descarte de reportes de Portabilidade de Crédito

-   Retirada a obrigatoriedade dos campos portabilityId, creationDateTime e creditPortabilityStatus para casos de statusCode 4xx e 5xx
    
-   Retirada a validação de enum do campo rejectionReason (será validado dentro do processo de aferição de qualidade dos reportes)
    

Reportes sendo descartados indevidamente

Regras de descarte ajustadas

Descarte indevido de reportes de Estados de Pagamento

Alteração

Ajuste no enum do campo paymentType na validação da ingestão da PCM

Correção de um erro que estava descartando indevidamente reportes de Estados de Pagamento no campo paymentType (SCHEDULED)

Rejeitando paymentType do tipo SCHEDULED

Crítica ajustada para aceitar corretamente

Descarte indevido de reportes de Dados Cadastrais e Transacionais

Alteração

Ajuste do tipo do campo statusSummary e seus subitens

Correção de um erro que estava descartando indevidamente reportes de Dados Cadastrais e Transacionais no additionalInfo statusSummary

Rejeitando statusSummary (enviando string, correto número)

Ajustada a regra do statusSummary (aceitando string)

Jornada Sem Redirecionamento - enums

Alteração

Inclusão de enums dos campos errorCodes e rejectionReasonCode

-   Inclusão de novos errorCodes:
    
    -   ORIGEM\_FIDO\_INVALIDA no POST /consents/{consentId}/authorise
        
    -   MAXIMO\_CHALLENGES\_ATINGIDO no POST /enrollments/{enrollmentId}/fido-registration-options
        
    -   PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO em /enrollments/{enrollmentId}/fido-sign-options
        
-   Inclusão de novo rejectionReasonCode:
    
    -   REJEITADO\_TITULARIDADE\_DIVERGENTE no GET /enrollments/enrollmentId
        

Não existente

Novos enums adicionados na documentação funcional e nos critérios de aberturas de ticket de qualidade de dados e dashboard de monitoramento operacional

Jornada Sem Redirecionamento - novo endpoint

Inclusão

Novo endpoint ingerido pela PCM

Novo endpoint para autorização de consentimentos recorrentes de PIX Automático:

-   /recurring-consents/{recurringConsentId}/authorise
    

Não existente

Novo endpoint sendo ingerido pela PCM

PIX Automático - enums

Alteração

Inclusão e exclusção de enums dos campos localInstrument, errorCodes e rejectionReasonCode

-   Inclusão de novo localInstrument:
    
    -   AUTO em GET /pix/payments/{recurringPaymentId} e PATCH /pix/payments/{recurringPaymentId}
        
-   Remoção de rejectionReasonCode:
    
    -   CONSENTIMENTO\_REVOGADO de POST/pix/recurring-payments, GET /pix/recurringpayments/{recurringPaymentId} e PATCH /pix/recurring-payments/{recurringPaymentId}
        
-   Remoção de errorCodes:
    
    -   DETALHE\_TENTATIVA\_INVALIDA e LIMITE\_TENTATIVAS\_EXCEDIDO de POST /pix/recurring-payments
        
-   Inclusão de novo rejectionReasonCode:
    
    -   FLUXO\_NAO\_SUPORTADO\_PRODUTO em POST /recurring-consents, GET /recurring-consents/{recurringConsentId} e PATCH /recurring-consents/{recurringConsentId}
        

Não existente

Novos enums adicionados na documentação funcional e nos critérios de aberturas de ticket de qualidade de dados e dashboard de monitoramento operacional

Novo additionalInfo tokenId em todas as APIs da PCM

Inclusão

Novo additionalInfo

Inclusão do additionalInfo tokenId nas APIs Private, Hybridflow e Open Data no papel CLIENT. Este campo atuará como um identificador único e criptograficamente seguro do token utilizado no consumo da API

Não existente

additionalInfo sendo ingerido pela PCM

Novo additionalInfo authorisationFlowIntent na API Private

Inclusão

Novo additionalInfo

Inclusão do additionalInfo authorisationFlowIntent, no reporte da etapa de solicitação de consentimento. O propósito principal deste campo é permitir a desambiguação e clara distinção entre as jornadas de pagamento que demandam ou não redirecionamento do usuário, já na etapa de provisionamento do consentimento

Não existente

additionalInfo sendo ingerido pela PCM

Novo additionalInfo recurringConsentId na API Private

Inclusão

Novo additionalInfo

Inclusão do additionalInfo recurringConsentId mutuamente exclusivo com consentId para o endpoint POST /enrollments/{enrollmentId}/fido-sign-options

Não existente

additionalInfo sendo ingerido pela PCM

Jornada Otimizada

Inclusão

Novos additionalInfo

Inclusão de additionalInfo para Jornada Otimizada:

-   Consentimentos: journeyIsLinked
    
-   JSR e PIX Automático: journeyIsLinked e journeyLinkId
    

Não existente

additionalInfo sendo ingerido pela PCM

Nova regra de descarte - timestamp

Inclusão

Nova regra de descarte em todas as APIs

Inclusão de regra de descarte para o campo timestamp:

-   Não permitir o recebimento de timestamp com data futura superior a 5 minutos da data de recebimento do reporte na PCM
    
    -   Não permitir o recebimento de timestamp fora do formato válido (YYYY-MM-DDTHH:mm:ss.sssZ)
        

Não existente

Reportes descartados que infrinjam a nova regra

Ajuste na formatação do campo "expires\_in"

Alteração

Ajuste no retorno do campo expires\_in

Ajuste na formatação do campo "expires\_in" no retorno de um novo token para envio doa dados da PCM

Retornando sempre o valor inicial, não o total restante

Retornando o total restante

2025C1800

**Data da release:** 01/09/2025

**Data do Informa:** 22/08/2025

**Número do Informa:** 781

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Evolução da estrutura funcional na Área do Desenvolvedor, permitindo reorganizar, ampliar e evidenciar regras de Monitoramento Operacional.

Inclusão

Criação da documentação funcional

Principais benefícios e entregáveis:

-   Reorganização dos Campos Adicionais (Addinfos), unificando as informações em tabelas por Famílias de Produtos;
    
-   Criação de estrutura contendo as regras de descartes, qualidade e pareamento de reportes, em aderência aos dados demonstrados no _Dashboar_d de Monitoramento Operacional e tickets emitidos;
    
-   Criação de página de _Changelog_, permitindo acompanhamento das mudanças na documentação.
    

Tabelas de additionalInfo espalhadas, regras não documentadas

Área de documentação funcional estruturada para comportar tabela unificada de additionalInfo e documentação de regras

Evolução da estrutura _Swagger_ no padrão Open API, disponível na Área do Desenvolvedor

Evolução

Disponibilização de novo swagger

Principais benefícios e entregáveis:

-   Acelerador de integrações, com a geração de docs (_Swagger_ UI/ReDoc), SDKs e stubs automaticamente, viabilizando a geração de contratos de testes;
    
-   Possibilidade de automação e validação de entradas/saídas com JSON _Schema_, mitigando riscos de quebras antes da publicação em produção;
    
-   Remoção de ambiguidades na escrita e fonte única para áreas e perfis envolvidos;
    
-   Acompanhamento do versionamento das mudanças;
    
-   Maior portabilidade e menor acoplamento, independentemente da linguagem/_framework_.
    

Swagger baseado na documentação OpenAPI

Swagger baseado na documentação APIDog

Portabilidade de Crédito

Alteração

Obrigatoriedade do campo portabilityId e lista de endpoints

-   Aprimoramento da documentação funcional na PCM;
    
-   Inclusão da obrigatoriedade de ingestão do campo PortabilityId em todos os _endpoints_ da API;
    
-   Atualização dos _endpoints_ aceitos.Endpoints aceitos pela PCM
    

portabilityId não era obrigatório em todos os endpoints; lista de endpoints aceitos pela PCM não apresentava os endpoints de Portabilidade de Crédito

portabilityId obrigatório em todos os endpoints; endpoints de Portabilidade de Crédito apresentados na lista de endpoints aceitos pela PCM

Novo campo Addinfo statusSummary, que permite o monitoramento da jornada de consentimentos para o público PJ, através do reporte pelos receptores de todos os estados observados na API _Resources._

Inclusão

Novo additionalInfo

![image-20250909-182537.png](images/image-20250909-182537.png)

Tabela de Obrigatoriedade de additionalInfo - Dados Cadastrais e Transacionais

Não existente

additionalInfo statusSummary incluído na API Resources

Novo campo Addinfo companyProfileInfo, que permite observar a Natureza Jurídica e Porte do Cliente PJ, através do reporte do lado cliente no consumo das APIs de consentimentos para recepção de dados cadastrais e de pagamentos.

Inclusão

Novo additionalInfo

![image-20250909-182618.png](images/image-20250909-182618.png)

Tabela de Obrigatoriedade de additionalInfo - Pagamentos

Tabela de Obrigatoriedade de additionalInfo - Dados Cadastrais e Transacionais

Não existente

additionalInfo _companyProfileInfo_ incluído na API Private para Pagamentos e Clientes

Novo _endpoint_ Path /pix/recurring-payments/{originalRecurringPaymentId}/retry de retentativas de pagamentos e Addinfo referencestartDate, para identificação da data prevista para início do ciclo de cobrança dos pagamentos associados à recorrência no Pix Automático.

Inclusão

Novo endpoint e additionalInfo

Endpoints aceitos pela PCM

![image-20250909-182831.png](images/image-20250909-182831.png)

Tabela de Obrigatoriedade de additionalInfo - Pagamentos

Não existente

endpoint _/pix/recurring-payments/{originalRecurringPaymentId}/retry_ incluído na lista de endpoints aceitos pela PCM; additionalInfo _referencestartDate_ incluído na API Private para Pagamentos

Novo _endpoint_ PATCH /consents/{consentId}/pix/payments, para consulta de recursos na API Pagamentos, a partir do identificador do consentimento.

Inclusão

Novo endpoint

Endpoints aceitos pela PCM

Não existente

endpoint _/consents/{consentId}/pix/payments_ incluído na lista de endpoints aceitos pela PCM

Novo Fluxo de Ingestão de Reportes para obtenção dos Estados de Pagamentos, com o objetivo de garantir a identificação precisa da liquidação, rejeição e outros estados de pagamentos.

Inclusão

Nova API

Dados relativos aos estados de pagamentos

Não existente

Criação de API de Dados Relativos aos Estados de Pagamento, com a devida documentação funcional

Atualização dos _endpoints_ aceitos na PCM, reforçando a necessidade de reporte para os _endpoints_ de investimentos em Dados Transacionais e de Clientes.

Evolução

Lista de endpoints aceitos pela PCM

Endpoints aceitos pela PCM

Lista de endpoints não apresentava os endpoints de investimentos

Lista de endpoints aceitos pela PCM atualizada com os endpoints de investimentos

Demais melhorias funcionais

Alteração

Fluxo do HybridFlow atualizado, definições dos campos de Hybridflow

-   Detalhamento das informações no fluxo _Hybrid Flow_
    

/report-api/v2/hybrid-flow/client/redirect-to-server:

1.  Incluída a descrição do campo “uriAuthorizationEndpoint”: Endpoint utilizado para o redirecionamento do usuário conforme cadastrado pela transmissora/detentora no arquivo .well-known/openid-configuration sem qualquer parâmetro introduzido pelo sistema da receptora/iniciadora. Caso a URI tenha mais de 200 caracteres de extensão, **truncar.**
    
2.  Alterado o campo uriAuthorizationEndpoint no exemplo para "[https://auth.banco.com.br/open-banking/Auth](https://auth.banco.com.br/open-banking/Auth)"
    

/report-api/v2/hybrid-flow/server/redirect-target:

1.  Alterado o texto da descrição para "Inclusão de reporte de chegada de usuário em sistema da transmissora/detentora. É ESSENCIAL A LEITURA DO DIAGRAMA DE SEQUÊNCIA PARA O ENTENDIMENTO DE COMO DEVE SER FEITO O REPORTE. Ao enviar um report, a Plataforma vai fazer o processo de validação de maneira síncrona e devolver o resultado dessa validação na resposta. O status HTTP de retorno será 200 caso o reporte enviado seja aceito."
    
2.  Incluída a descrição do campo “uriAuthorizationEndpoint”: Endpoint utilizado para o redirecionamento do usuário conforme cadastrado pela transmissora/detentora no arquivo .well-known/openid-configuration sem qualquer parâmetro introduzido pelo sistema da receptora/iniciadora. Caso a URI tenha mais de 200 caracteres de extensão, **truncar**
    
3.  Alterado o campo uriAuthorizationEndpoint no exemplo para "[https://auth.banco.com.br/openbanking/Auth](https://auth.banco.com.br/openbanking/Auth)"
    

/report-api/v2/hybrid-flow/server/authenticated

1.  Alterado o texto da descrição para "Inclusão de reporte de que o usuário está apto a prosseguir com a autorização do consentimento. Deverá ser enviado após o usuário se autenticar/entrar na área autenticada e antes de autorizar o consentimento. É ESSENCIAL A LEITURA DO DIAGRAMA DE SEQUÊNCIA PARA O ENTENDIMENTO DE COMO DEVE SER FEITO O REPORTE. Ao enviar um reporte, a Plataforma vai fazer o processo de validação de maneira síncrona e devolver o resultado dessa validação na resposta. O status HTTP de retorno será 200 caso o reporte enviado seja aceito."
    

/report-api/v2/hybrid-flow/server/redirect-to-client

1.  Alterado o campo uri\_callback no exemplo para "[https://receptora.com.br/open-banking/landing-page](https://receptora.com.br/open-banking/landing-page)"
    
2.  No campo uri\_callback, incluída a descrição "Preencher com a uri\_callback registrada pelo sistema consumidor durante o DCR/DCM. Caso a URI tenha mais de 200 caracteres de extensão, **truncar**."
    

Demais melhorias funcionais

Alteração

Descrição do campo clientIp

-   Maior detalhamento funcional do campo clientIp.
    

clientIp estava obrigatório para enrollments

Alterada a documentação de forma a ficar claro que o campo clientip no enrollment é opcional

Demais melhorias funcionais

Alteração

Descrição do campo dropReason

-   Maior detalhamento funcional do campo dropReason
    

De " \* NO\_CREDENTIAL: quando o CPF (loggedUser) / CNPJ (businessEntity) não for cliente ou não possuir credencial válida/ativa para prosseguir no fluxo monitorado. "

Para " \* NO\_CREDENTIAL: quando o CPF (loggedUser) / CNPJ (businessEntity) não for cliente ou não possuir credencial válida/ativa para prosseguir no fluxo monitorado ou quando o HTTP response code for diferente de 201"

2025B1800

**Data da release:** 01/07/2025

**Data do Informa:** 16/06/2025

**Número do Informa:** 753

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Portabilidade de Crédito

Inclusão

Lançamento da documentação na versão beta

Lançamento da documentação na versão beta, permitindo o entendimento para a ingestão dos reportes a serem monitorados através da PCM

Não existente

Disponibilização da documentação da nova API de Portabilidade de Crédito

Tratamento de Conglomerado e Organizações Filhas

Evolução

Tratamento no recebimento de reportes para identificar conglomerados enviando dados de organizações filhas

Solução que possibilitará, a partir de 18/06/2025, a uma organização mãe ou filha o envio de reportes utilizando o certificado válido de qualquer organização pertencente ao conglomerado.

Descarte de reportes devido às organizações filhas não possuírem certificado; não-pareamento de reportes quando as organizações reportam client ou server da organização filha, mas o conglomerado reporta como mãe.

Tratamento no recebimento do reporte, identificando que é uma organização filha utilizando o certificado da organização mãe, eliminando os descartes e problemas de pareamento.

Novo additionalInfo nfcPayment

Inclusão

Novo additionalInfo no fluxo da JSR

Inclusão de campo adicional (AdditionalInfo) nfcPayment na PCM: a inclusão do campo no monitoramento permite a identificação do pagamento quando realizado através do método de aproximação no POS (Point of Safe) via NFC (Near Field Communication) no fluxo da JSR.

Não existente

additionalInfo nfcPayment incluído na API Private

Alteração no additionalInfo dropReason

Alteração

Novos domínios para o additionalInfo

Adequação dos valores disponíveis do campo (AdditionlInfo) DropReason: a alteração permite a correta distinção, esclarecendo valores previstos para envio no campo

Domínio:  
NO\_CREDENTIAL, NONE

Domínio:  
NO\_AUTHORITY, NO\_AUTHORITY\_PERSON\_MISMATCH, NO\_CREDENTIAL, NONE

Detalhamento do additionalInfo grantType

Evolução

Descrição do domínio do campo grantType

Detalhamento dos valores disponíveis do campo (AdditionalInfo) GrantType

Não especificado

Domínio:  
AUTHORIZATION\_CODE, REFRESH\_TOKEN, CLIENT\_CREDENTIALS

Release 2025A / 2025A11800

**Data da release:** 01/04/2025

**Data do Informa:** 13/03/2025

**Número do Informa:** 709 / 723 / 731 / 752

**Contexto**

**Tipo de alteração**

**O que foi alterado?**

**Detalhes**

**Antes**

**Depois**

Novos campos de additionalInfo para PIX Automático

Inclusão

Inclusão de novos campos additionalInfo; criação de tabela de obrigatoriedade de additionalInfo para PIX Automático

Esta atualização possibilitará uma análise mais apurada do serviço, e segue o cronograma de implementação da v2.0.0 da API Pagamentos automáticos (Pix automático), conforme comunicado no Informa #661

Não existentes

Inclusão dos additionalInfo:

-   amountType
    
-   interval
    
-   isfirstPayment
    
-   hasMinimumAmount​
    
-   isRetryAccepted
    
-   originalRecurringPaymentId
    
-   paymentReference
    
-   cancellationReason​
    

Nova API de Dados Relativos à Quantidade de Consentimentos Ativos e Únicos por clientes

Inclusão

Nova API para recebimento de dados relativos a Estoque de Consentimentos

Apuração dos dados de Estoque de Consentimentos através da PCM, não mais por planilhas autorreportadas.

Dados recebidos via planilha

Dados recebidos pela PCM

Chamada da Private API (GET)

Alteração

Alteração na forma de chamada da API

Maior eficiência e aumento de performance do recurso

Chamada pelo reportId

Chamada pelo fapiInteractionId
