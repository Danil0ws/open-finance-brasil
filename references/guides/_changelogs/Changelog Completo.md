# Changelog Completo

## **Objetivo desta página**

Registrar as mudanças realizadas na documentação da PCM.

# **Primeiros passos**

**Área**

**Versão**

**Data**

**Mudança realizada**

**Release**

**Informa**

Índice das páginas

1.00

11/06/2026

-   Versão inicial
    

2026B

906 - 11/06/2026

Especificação Técnica

v.7

03/01/2023

-   Atualizadas as premissas técnicas
    

v.1

22/12/2022

-   Versão inicial
    

Manual de integração

v.12

16/03/2026

-   Inclusão do endpoint /token-fresh, que possibilita a geração de um novo token, ignorando o que está em cache.
    

2026A

859 - 11/03/2026

v.11

04/04/2024

-   Atualização de links da documentação da API
    
-   Inclusão do fluxo de autenticação
    
-   Alteração no exemplo de autenticação
    
-   Alteração no exemplo da interação com a API
    
-   Alteração no exemplo do cenário PAIRED\_INCONSISTENT
    

v.1

23/12/2022

-   Versão inicial
    

Lista de endpoints

1.06

26/08/2025

-   Remoção dos endpoints da v4 dePagamentos
    

2026C

1.05

22/06/2026

-   Inclusão do endpoint /open-banking/accounts/v2/accounts/{accountId}/reserved-balances
    

1.04

21/05/2026

-   Inclusão do endpoint de Pagamentos _/open-banking/payments/v5/consents/{consentId}/pix/payments_, em substituição ao endpoint _/open-banking/payments/v4/pix/payments/consents/{consentId}_. Ambos os endpoints permanecerão ativos durante o período de convivência entre as versões 4 e 5 da API de Pagamentos.
    
-   Inclusão dos endpoints da v5 da API de Pagamentos  
    /open-banking/payments/v5/consents  
    /open-banking/payments/v5/consents/{consentId}  
    /open-banking/payments/v5/consents/{consentId}/pix/payments   
    /open-banking/payments/v5/pix/payments  
    /open-banking/payments/v5/pix/payments/{paymentId}
    

2026B

906 - 11/06/2026

1.03

16/03/2026

-   Inclusão do endpoint de Portabilidade de Crédito /open-banking/credit-portability/v1/credit-operations/{contractId}/portability-eligibility
    

2026A

859 - 11/03/2026

1.02

10/11/2025

-   Inclusão do endpoint /open-banking/enrollments/v2/recurring-consents/{recurringConsentId}/authorise
    

2025D

815 - 18/11/2025

1.01

12/09/2025

-   Retirada do endpoint /open-banking/credit-portability/v1/credit-operations/{contractId}/portability-eligibility de Portabilidade de Crédito, incluído erronamente.
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

# **Especificações por Domínio**

**Área**

**Versão**

**Data**

**Mudança realizada**

**Release**

**Informa**

Visão Geral dos Campos da PCM

1.00

11/06/2026

-   Versão inicial
    

2026B

906 - 11/06/2026

**Dados Abertos**

Campos  
Obrigatórios e  
Opcionais

1.02

25/06/2026

-   Alteração do tipo do campo processTimespan - de _integer <int16>_ para _number_
    

2026C

1.01

11/06/2026

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Opendata API e quais campos são retornados no response
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    
-   Inclusão da coluna “Regras de Preenchimento”
    
-   processTimespan: correção do exemplo para refletir de forma correta o valor esperado
    
-   statusCode: inclusão de regra de preenchimento - _No contexto operacional do Open Finance, de acordo com a definição de governança, a instituição consumidora (Client) deve aguardar até 15 segundos pela resposta da instituição provedora (Server)._
    
    _Caso esse período seja atingido ou excedido (≥ 15 segundos) sem resposta, a instituição consumidora pode, por decisão própria e para preservar a experiência do usuário, encerrar a conexão. Nessa situação, o evento deve ser reportado com status code 408, caracterizando timeout na interação, ainda que a interrupção tenha sido iniciada pelo lado consumidor._
    
    _Por sua vez, quando a instituição estiver atuando como provedora (Server) e encerrar a conexão por não ter recebido a requisição completa dentro do tempo esperado, também deverá reportar status code 408, em conformidade com a RFC 7231._
    
-   endpoint: inclusão de regra de preenchimento - _Identificação do Endpoint: Deve ser preenchido com o identificador padronizado do endpoint, conforme uma lista (ENUM) predefinida.Não usar o caminho real: É fundamental NÃO utilizar o caminho completo da requisição original, que inclui dados variáveis (ex: IDs)._  
    _Exemplo: Se a requisição foi para /open-banking/credit-cards-accounts/v1/accounts/123456789/transactions, o valor a ser enviado no endpoint deve ser /open-banking/credit-cards-accounts/v1/accounts/{creditCardAccountId}/transactions. O dado real 123456789 não deve ser enviado no campo endpoint_
    
-   processTimespan: alteração da definição - _Tempo em milissegundos inteiros decorrido desde o recebimento do request até o momento imediatamente anterior ao envio do primeiro byte da resposta._
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Obrigatoriedade  
de additionalInfo

1.01

11/06/2026

-   Remoção do campo tokenId, pois constava indevidamente na tabela, uma vez que o mesmo não faz parte do escopo de Dados Abertos
    
-   Remoção da coluna “Regras de Preenchimento”, que estava somente replicando a coluna “Descrição”
    
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
        

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.01

11/06/2026

-   Ajustes realizados para refletir as regras de obrigatoriedade de additionalInfo
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Descarte

1.01

11/06/2026

-   Atualizado com os motivos de descarte dos últimos 6 meses
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

**Dados Cadastrais e Transacionais**

Campos  
Obrigatórios e  
Opcionais

1.02

25/08/2026

-   Alteração do tipo do campo processTimespan - de _integer <int16>_ para _number_
    

2026C

1.01

11/06/2026

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Private API, quais campos são retornados no response e quais são adicionais ao método GET.
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    
-   clientSSIDd: correção nas roles obrigatórias, o correto é somente CLIENT
    
-   processTimespan: correção do exemplo para refletir de forma correta o valor esperado
    
-   statusCode: maior esclarecimento na regra de preenchimento - _No contexto operacional do Open Finance, de acordo com a definição de governança, a instituição consumidora (Client) deve aguardar até 15 segundos pela resposta da instituição provedora (Server)._
    
    _Caso esse período seja atingido ou excedido (≥ 15 segundos) sem resposta, a instituição consumidora pode, por decisão própria e para preservar a experiência do usuário, encerrar a conexão. Nessa situação, o evento deve ser reportado com status code 408, caracterizando timeout na interação, ainda que a interrupção tenha sido iniciada pelo lado consumidor._
    
    _Por sua vez, quando a instituição estiver atuando como provedora (Server) e encerrar a conexão por não ter recebido a requisição completa dentro do tempo esperado, também deverá reportar status code 408, em conformidade com a RFC 7231._
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Obrigatoriedade  
de additionalInfo

1.06

25/08/2026

-   Todos os produtos - alteração na regra do tokenId - _obrigatório para todos os statusCode exceto 4xx e 5xx_
    
-   Recursos
    
    -   statusSummary - _obrigatório somente para statusCode 200_
        
-   Consentimentos
    
    -   dropReason - inclusão do enum _CREDENTIAL\_UNAVAILABLE_
        

2026C

1.05

11/06/2026

-   Todos os produtos: inclusão da coluna “Tipo”
    
-   Consentimentos
    
    -   journeyIsLinked: ajustada a regra de preenchimento - _Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.isLinked”, retornado após a chamada inicial na API “POST /consent” (Pagamentos Automáticos) ou “POST /enrollments” (Jornada Sem Redirecionamento) em caso de Jornada Otimizada. Em casos em que a informação não está disponível espera-se o envio do valor FALSE._
        
    -   tokenId: inclusão dos endpoints _/open-banking/consents/v3/consents/{consentId}/extends_ e _/open-banking/consents/v3/consents/{consentId}/extensions_
        
-   Recursos
    
    -   statusSummary: ajuste na regra de preenchimento
        

2026B

906 - 11/06/2026

1.04

16/03/2026

-   Inclusão de endpoints em Consentimentos, campo tokenId
    
    -   /open-banking/consents/v_x_/consents/{consentId}/extends
        
    -   /open-banking/consents/v_x_/consents/{consentId}/extensions
        

1.03

10/12/2025

-   Ajuste no padrão do campo consentId
    

1.02

10/11/2025

-   Inclusão do additionalInfo tokenId
    
-   Inclusão do additionalInfo journeyIsLinked, referente à Jornada Otimizada
    

2025D

815 - 18/11/2025

1.01

01/10/2025

-   Melhoria na descrição do campo companyProfileInfo, contemplando os links para pesquisa de CNPJ
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.04

25/08/2026

-   Todos os produtos - alteração na regra do tokenId - _obrigatório para todos os statusCode exceto 4xx e 5xx_
    
-   Recursos
    
    -   statusSummary - _obrigatório somente para statusCode 200_
        

2026C

1.03

11/06/2026

-   Ajustes realizados para refletir as regras de obrigatoriedade de additionalInfo
    

2026B

906 - 11/06/2026

1.02

16/.03/2026

-   Ajuste fino nas regras do consentId de Câmbio, Cartão de Crédito, Contas, Dados Cadastrais
    
    -   Remoção da validação de POST com status 4xx e 5xx
        
    -   Explicitação do GET como método validado
        
-   Retirada do endpoint %/payments/v_x_/consents, indevido no campo dropReason, pois é um endpoint de pagamentos
    

1.01

17/12/2025

-   Inclusão da validação do campo companyProfileInfo para Consentimentos, de acordo com a implementação realizada na release 2025C
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Descarte

1.01

11/06/2026

-   Atualizado com os motivos de descarte dos últimos 6 meses
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

**Pagamentos**

Campos  
Obrigatórios e  
Opcionais

1.02

25/08/2026

-   Alteração do tipo do campo processTimespan - de _integer <int16>_ para _number_
    

2026C

1.01

11/06/2026

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Private API, quais campos são retornados no response e quais são adicionais ao método GET.
    
-   Remoção da coluna “Métodos” para evitar conflito com a reestruturação da página
    
-   clientSSIDd: correção nas roles obrigatórias, o correto é somente CLIENT
    
-   processTimespan: correção do exemplo para refletir de forma correta o valor esperado
    
-   statusCode: maior esclarecimento na regra de preenchimento
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Obrigatoriedade  
de additionalInfo

1.10

25/08/2026

-   Todos os produtos
    
    -   Alteração na regra do tokenId - _obrigatório para todos os statusCode exceto 4xx e 5xx_
        
    -   dropReason - inclusão do enum _CREDENTIAL\_UNAVAILABLE_
        
-   Iniciação de pagamentos
    
    -   Remoção dos endpoints da v4
        
    -   paymentType - regra de preenchimento - caminho do purpose = _/data/payment/purpose_
        
    -   Inclusão da obrigatoriedade de envio dos campos cancellationReason e cancelledFrom
        
-   Jornada Sem Redirecionamento
    
    -   authenticatorAttachment - ajuste da regra de preenchimento - _Deve ser preenchido com a mesma string definida em ".data.authenticatorAttachment". Não havendo string, deve ser explicitamente enviada esse additionalInfo como sendo uma string vazia.​_  
        _Caso seja enviado um valor neste campo, o mesmo será validado contra o domínio dele_.
        
-   Pagamentos Automáticos
    
    -   errorCodes - obrigatório também para o endpoint /open-banking/automatic-payments/v2/pix/recurring-payments/{originalRecurringPaymentId}/retry
        
    -   Alteração na regra de obrigatoriedade do campo recurringConsentId
        
        -   Endpoint /open-banking/automatic-payments/v2/recurring-consents - obrigatório para POST e statusCode exceto 4xx e 5xx
            
        -   Endpoint /open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId} - obrigatório para GET ou PATCH para qualquer statusCode
            
        -   Endpoints /open-banking/automatic-payments/v2/pix/recurring-payments, /open-banking/automatic-payments/v2/pix/recurring-payments/{recurringPaymentId} e  
            /open-banking/automatic-payments/v2/pix/recurring-payments/{originalRecurringPaymentId}/retry - obrigatório para POST, GET ou PATCH para qualquer statusCode
            

2026C

1.09

11/06/2026

-   Todos os produtos: inclusão da coluna “Tipo”
    
-   Iniciação de Pagamentos
    
    -   paymentList: inclusão de regra de preenchimento para dar maior clareza da regra do campo - _envio para paymentType IMMEDIATE, RECURRENT e SCHEDULED, mesmo possuindo apenas um paymentId na lista._
        
    -   paymentType: inclusão de regra de preenchimento específica para a v5 de pagamentos
        
    -   rejectionReasonCode: complemento da regra de preenchimento - _Obrigatório somente quando o status for RJCT ou REJECTED_
        
    -   rejectionReasonDetail: complemento da regra de preenchimento - _Obrigatório somente quando o status for RJCT ou REJECTED_
        
-   Jornada Sem Redirecionamento
    
    -   Remoção da versão v1 da API nos endpoints válidos
        
    -   authenticatorAttachment: incluído o domínio do campo - _platform, cross-platform_
        
    -   platform: incluído o domínio do campo - _ANDROID, BROWSER, CROSS\_PLATFORM, IOS_
        
    -   revocationReasonCode: incluída a regra de preenchimento - _Deve ser preenchido com a mesma string obtida no ".data.cancellation.reason.revocationReason". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Dever ser enviado quando o status for REVOKED_
        
    -   tokenId: inclusão do endpoint _/open-banking/enrollments/v2/recurring-consents/{recurringConsentId}/authorise_
        
    -   journeyIsLinked: alteração da regra de preenchimento - _Deve ser preenchido com a string obtida no campo journey.isLinked, após a chamada inicial na API “POST /consents” se o parâmetro isLinked estiver preenchido na requisição no contexto de Jornada Otimizada. Em casos em que a informação não está disponível espera-se o envio do valor FALSE._
        
    -   journeyLinkId: complemento da regra de preenchimento - _Deve ser enviado se journeyIsLinked for TRUE_
        
-   Pagamentos Automáticos
    
    -   authorisationFlow: ajuste na descrição do campo - _Identifica o fluxo de autorização em que um pagamento ou operação foi solicitado. Descreve como o autenticador (por exemplo, um dispositivo FIDO) está anexado ao cliente que realiza a autenticação (ex: platform para autenticadores integrados como Face ID ou cross-platform para chaves de segurança USB)._
        
    -   errorCodes: correção do campo, estava duplicado. Foi dividido em regras para statusCode 422 e statusCode 4xx / 5xx exceto 422, a exemplo de Iniciação de Pagamentos
        
    -   interval: incluído domínio do campo - _SEMANAL, MENSAL, TRIMESTRAL, SEMESTRAL, ANUAL_
        
    -   isRetryAccepted: incluído domínio do campo - _TRUE, FALSE_
        
    -   originalRecurringPaymentId: inclusão do endpoint /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry, complemento da regra de preenchimento: _Para os endpoints /open-banking/automatic-payments/vx/pix/recurring-payments e /open-banking/automatic-payments/vx/pix/recurring-payments/{recurringPaymentId}, métodos GET e PATCH, a informação só deve ser enviada se retornado no response da API._
        
    -   paymentReference: complementada a regra de preenchimento - _Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO._
        
    -   paymentType: complemento da regra de preenchimento - **WITHDRAW:** PIX Saque e **CHANGE:** PIX Troco
        
    -   recurringConsentId: ajustada a descrição, incluída a regra de preenchimento e o endpoint /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry
        
    -   recurringPaymentDate: complementada a descrição - _Data em que o pagamento será realizado no formato timezone UTC-3 (UTC time format)_
        
    -   recurringPaymentId: ajustadas a descrição e a regra de preenchimento, incluído padrão do campo e o endpoint endpoint /open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry
        
    -   referenceStartDate: ajustada a descrição - _Data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data_
        
    -   rejectedBy: incluída a regra de preenchimento - _Deve ser preenchido com a mesma string obtida no ".data.rejection.rejectedBy". Obrigatório somente quando o status for RJCT ou REJECTED_
        
    -   rejectedFrom: incluída a regra de preenchimento - _Deve ser preenchido com a mesma string obtida no ".data.rejection.rejectedFrom". Obrigatório somente quando o status for RJCT ou REJECTED_
        
    -   rejectionReasonCode: complementada a regra de preenchimento - _Obrigatório somente quando o status for RJCT ou REJECTED_
        
    -   rejectionReasonDetail: incluída a regra de preenchimento - _Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Obrigatório somente quando o status for RJCT ou REJECTED_
        
    -   revocationReasonCode: incluída a regra de preenchimento - _Deve ser preenchido com a string obtida no campo ".data.revocation.reason.code". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Obrigatório somente quando o status for REVOKED_
        
    -   revocationReasonDetail: incluída a regra de preenchimento - _Deve ser preenchido com a string obtida no campo ".data.revocation.reason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista. Obrigatório somente quando o status for REVOKED_
        
    -   status: inclusão do endpoint _/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry_
        
    -   tokenId: inclusão do endpoint _/open-banking/automatic-payments/vx/pix/recurring-payments/{originalRecurringPaymentId}/retry_
        

2026B

906 - 11/06/2026

1.08

21/06/2026

-   Inclusão dos endpoints  
    /open-banking/payments/v5/consents  
    /open-banking/payments/v5/consents/{consentId}  
    /open-banking/payments/v5/consents/{consentId}/pix/payments   
    /open-banking/payments/v5/pix/payments  
    /open-banking/payments/v5/pix/payments/{paymentId}
    

1.07

16/03/2026

-   Inclusão de endpoints em Jornada Sem Redirecionamento, campo tokenId
    
    -   /open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise
        
    -   /open-banking/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
        
-   Unificação das tabelas de Pagamentos Automáticos e PIX Automático com a desativação da v1 de Pagamentos
    
-   Em Regras de Obrigatoriedade de addtionalInfo de Pagamentos Automáticos, substituição do consentId por recurringConsentId
    

1.06

23/01/2026

-   Ajuste na regra de preenchimento do campo errorCodes, dando clareza à regra vigente de envio de apenas um registro, e não de uma lista.
    
-   Ajuste na obrigatoriedade de envio dos campos journeyIsLinked e journeyLinkId para PIX Automáticos - retirada da restrição de 4xx e 5xx
    

1.05

01/12/2025

-   Inclusão do endpoint /open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise, na Jornada Sem Redirecionamento, para os additionalInfo enrollmentId, recurringConsentId e errorCodes.
    

2025D

815 - 18/11/2025

1.04

10/11/2025

-   Inclusão do additionalInfo recurringConsentId para o endpoint /open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options, mutuamente excludente com o additionalInfo consentId
    
-   Inclusão das regras de validação dos additionalInfo consentId e recurringConsentId para Jornada sem Redirecionamento
    
-   Inclusão do domínio AUTO no additionalInfo localInstrument para Iniciação de Pagamentos e PIX Automático
    
-   Retirado do domínio do additionalInfo errorCodes de Pagamentos Automáticos: DETALHE\_TENTATIVA\_INVALIDA e LIMITE\_TENTATIVAS\_EXCEDIDO
    
-   Incluído no domínio do additionalInfo rejectionReasonCode de Pagamentos Automáticos: FLUXO\_NAO\_SUPORTADO\_PRODUTO
    
-   Inclusão do additionalInfo authorisationFlowIntent para Iniciação de Pagamentos e Pagamentos Automáticos
    
-   Inclusão do additionalInfo tokenId para todas as jornadas
    
-   Inclusão dos additionalInfo journeyIsLinked e journeyLinkId em Jornada Sem Redirecionamento e PIX Automático, referentes à Jornada Otimizada
    

2025D

815 - 18/11/2025

1.03

01/10/2025

-   Melhoria na descrição do campo companyProfileInfo, contemplando os links para pesquisa de CNPJ
    
-   Inclusão do domínio do campo status para Pagamento Sem Redirecionamento
    

1.02

24/09/2025

-   Alteração na regra de preenchimento do campo authorisationFlow em Iniciação de Pagamentos e PIX Automático, de acordo com o contrato da API
    
-   Inclusão de domínio do campo authorisationFlow em Iniciação de Pagamentos e PIX Automático, de acordo com o contrato da API
    

1.01

12/09/2025

-   Retirada dos campos riskSignalsEnumList e rislSignalsQuantity, incluídos erroneamente na documentação
    
-   Ajustes na documentação:
    
    -   authorisationFlow: inclusão do endpoint /open-banking/payments/v_x_/pix/payments/{paymentId}​ e métodos GET/PATCH
        
    -   consentId: correção do padrão, exemplo e statusCodes
        
    -   errorCodes: ajuste no domínio para erros 422 demais erros
        
    -   paymentSchedule: correção na regra de preenchimento - deve ser mutualmente excludente com paymentDate
        
    -   paymentList: identificação dos itens que fazem parte da lista com o identificador paymentList\[\].
        
    -   paymentType: adequação da regra de preenchimento
        
    -   nfcPayment: ajuste na regra de preenchimento
        
    -   status: ajuste na descrição do campo para Pagamentos Sem Redirecionamento
        

1.00

22/08/2025

-   Versão inicial
    

Regras de  
Validação

1.07

25/08/2026

-   Todos os produtos - alteração na regra do tokenId - _obrigatório para todos os statusCode exceto 4xx e 5xx_
    
-   Iniciação de Pagamentos:
    
    -   Inclusão da obrigatoriedade de envio dos campos cancellationReason e cancelledFrom
        
-   Pagamentos Automáticos
    
    -   errorCodes - obrigatório também para o endpoint /open-banking/automatic-payments/v2/pix/recurring-payments/{originalRecurringPaymentId}/retry
        

2026C

1.06

11/06/2026

-   Ajustes realizados para refletir as regras de obrigatoriedade de additionalInfo
    

2026B

906 - 11/06/2026

1.05

20/02/2026

-   Inclusão das regras de validação de Estados de Pagamento
    

1.04

09/02/2026

-   Inclusão de campos: paymentSchedule e localInstrument
    
-   Ajustes diversos nas validações
    

1.03

15/10/2025

-   Inclusão da validação do campo companyProfileInfo para Iniciação de Pagamentos, Jornada Sem Redirecionamento e Pagamentos Automáticos, de acordo com a implementação realizada na release 2025C
    
-   Inclusão da validação do campo nfcPayment para Jornada Sem Redirecionamento, de acordo com implementação realizada na release 2025B
    

1.02

09/10/2025

-   Ajuste das regras de validação para refletir alterações feitas nas obrigatoriedades de campos da PCM
    

1.01

15/09/2025

-   Retirada da regra de validação do additionalInfo authenticatorAttachment devido ao campo não ser obrigatório
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Descarte

1.02

11/06/2026

-   Atualizado com os motivos de descarte dos últimos 6 meses
    

2026B

906 - 11/06/2026

1.01

20/02/2026

-   Inclusão das regras de descarte de Estados de Pagamento
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Jornada Otimizada

1.01

11/06/2026

-   journeyIsLinked: alteração da regra de preenchimento - _Deve ser preenchido com a string obtida no campo journey.isLinked, após a chamada inicial na API “POST /consents” se o parâmetro isLinked estiver preenchido na requisição no contexto de Jornada Otimizada. Em casos em que a informação não está disponível espera-se o envio do valor FALSE._
    
-   journeyLinkId: complemento da regra de preenchimento - _Deve ser enviado se journeyIsLinked for TRUE_
    

2026B

906 - 11/06/2026

1.00

18/11/2025

-   Versão inicial
    

**Portabilidade de crédito**

Funcionalidade  
e Campos

1.01

13/10/2025

-   Alteração do status ACCEPTED\_SETTLEMENT\_IN\_PROCESS para ACCEPTED\_SETTLEMENT\_IN\_PROGRESS
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Campos  
Obrigatórios e  
Opcionais

1.08

25/08/2026

-   rejectionReason - lista simples de valores possíveis, sem validação de status e rejectedBy
    
-   rejectedBy e rejectionReason - regra de preenchimento - obrigatório o envio para status REJECTED ou CANCELLED, retirado PAYMENT\_ISSUE
    

2026C

1.07

11/06/2026

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Credit Portability API, quais campos são retornados no response e quais são adicionais ao método GET.
    
-   processTimespan: correção do exemplo para refletir de forma correta o valor esperado
    
-   statusCode: maior esclarecimento na regra de preenchimento
    

2026B

906 - 11/06/2026

1.06

16/03/2026

-   Inclusão do endpoint /open-banking/credit-portability/v1/credit-operations/{contractId}/portability-eligibility
    

1.05

02/01/2026

-   Ajuste na visualização dos campos, separando os campos de acordo com a obrigatoriedade de envio no POST e recuperação através de GET na PCM, com o intuito de diferenciar os métodos e endopints exigidos pelas APIs de produtos contra a forma de envio e obtenção dos campos na PCM.
    

1.04

10/12/2025

-   Ajuste no padrão do campo consentId
    

1.03

10/11/2025

-   Inclusão dos campos creationDateTime e consentId
    
-   Exclusão dos campos role, contractId, originalContractTerm e propositionTerm
    
-   Inclusão das informações referentes à obrigatoriedade considerando Http code e endpoint
    
-   Complementadas as regras de preenchimento dos campos cresitPortabilityStatus, rejectedBy e rejectionReason para dar mais clareza
    

2025D

815 - 18/11/2025

1.02

13/10/2025

-   Alteração do domínio do campo creditPortabilityStatus - de ACCEPTED\_SETTLEMENT\_IN\_PROCESS para ACCEPTED\_SETTLEMENT\_IN\_PROGRESS
    

1.01

26/09/2025

-   Exclusão do campo Id do Reporte da API Client
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.04

25/08/2026

-   Ajustes realizados para refletir as regras de obrigatoriedade dos campos
    

2026C

1.03

11/06/2026

-   Ajustes realizados para refletir as regras de obrigatoriedade dos campos
    

2026B

906 - 11/06/2026

1.02

16/03/2026

-   Inclusão do endpoint /open-banking/credit-portability/v1/credit-operations/{contractId}/portability-eligibility
    

1.01

09/02/2026

-   Inclusão da regra de validação do campo consentId
    
-   Inclusão da regra de validação do campo errorCode
    
-   Ajustes diversos nas validações
    

1.00

03/12/2025

-   Versão inicial
    

2025D

815 - 18/11/2025

Regras de  
Descarte

1.,02

11/06/2026

-   Atualizado com os motivos de descarte dos últimos 6 meses
    

2026B

906 - 11/06/2026

1.0.1

10/12/2025

-   Inclusão das regras de descarte da API de Estados de Pagamento
    

1.00

10/11/2025

-   Versão inicial
    

2025D

815 - 18/11/2025

**Hybridflow**

Campos  
Obrigatórios e  
Opcionais

1.01

11/06/2026

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Hybrid Flow API e quais campos são retornados no response
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.01

11/06/2026

-   Ajustes realizados para refletir as regras de obrigatoriedade dos campos
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Descarte

1.01

11/06/2026

-   Atualizado com os motivos de descarte dos últimos 6 meses
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Diagramas de Fluxo

Diagrama de  
Envio de  
Reportes

v.3

03/09/2025

-   Atualização do diagrama
    

v.1

26/08/2025

-   Versão inicial
    

Diagrama de  
Sequência

v.1

26/08/2025

-   Versão inicial
    

**Segurança**

Campos  
Obrigatórios e  
Opcionais

1.01

25/08/2026

-   Alteração do tipo do campo processTimespan - de _integer <int16>_ para _number_
    

2026C

1.00

11/06/2025

-   Versão inicial
    

2026B

906 - 11/06/2026

Regras de  
Obrigatoriedade  
de additionalInfo

1.03

25/08/2026

-   tokenId - remoção dos endpoints /register e /register{clientId} (não têm obrigatoriedade de envio)
    

2026C

1.02

11/06/2025

-   consentId: complemento da regra de preenchimento - _Deve ser preenchido com a mesma string obtida no campo .data.consentId retornado após a chamada inicial na API "POST /consent”. \*Ao reportar o uso de um endpoint /token, o identificador único de consentimento só será reportado nos casos em que "grant\_type" é do tipo "authorization\_code" ou do tipo "refresh\_token"_
    
-   grantType: complemento da regra de preenchimento - _Deve ser preenchido com a mesma string enviada no campo ".grant\_type "​_  
    _**AUTHORIZATION\_CODE:** Utilizado na autorização de acesso a um recurso por meio de login de usuário_  
    _**REFRESH\_TOKEN:** Utilizado para obter um novo token de acesso quando o token anterior expira_  
    _**CLIENT\_CREDENTIALS:** Utilizado na autorização de acesso entre aplicações onde não há a figura do usuário_
    
-   webhookEnable: correção na regra de preenchimento; não deve ser enviado um valor booleano TRUE ou FALSE, mas sim uma string contendo ou TRUE ou FALSE.
    

2026B

906 - 11/06/2026

1.01

10/12/2025

-   Ajuste no padrão do campo consentId
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.03

25/08/2026

-   tokenId - remoção dos endpoints /register e /register{clientId}
    

2026C

1.02

11/06/2025

-   Ajustes realizados para refletir as regras de obrigatoriedade de additionalInfo
    

2026B

906 - 11/06/2026

1.01

05/03/2026

-   Ajuste na regra de validação do campo grantType
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Descarte

1.01

11/06/2025

-   Atualizado com os motivos de descarte dos últimos 6 meses
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

**Consentimentos**

Estoque de  
Consentimentos  
Ativos

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Campos  
Obrigatórios e  
Opcionais

1.02

25/08/2026

-   Ajuste na descrição do campo date
    

2026C

1.01

11/06/2025

-   Reestruturação da página, dando clareza dos campos que devem ser enviados no método POST da Consents API e quais campos são retornados no response
    

2026B

906 - 11/06/2026

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.01

09/02/2026

-   Inclusão da regra de validação de envio diário do estoque de consentimento
    
-   Inclusão da regra de validação dos campos clientOrgId e serverOrgId
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

**Estados de Pagamento**

Campos  
Obrigatórios e  
Opcionais

1.04

25/08/2026

-   Inclusão de enum em paymentType - WITHDRAW, CHANGE
    

2026C

1.03

11/06/2026

-   Correção da descrição do campo paymentList, dando maior clareza quanto ao seu escopo
    
-   Complemento da descrição do campo eventDateTime, incluindo o escopo de agendamento aos demais estados
    
-   Complemento da regra de validação da quantidade de paymentIds distintos para um mesmo consentId, passando a validar também a data do último pagamento
    

2026B

906 - 11/06/2026

1.02

10/12/2025

-   Ajuste no padrão do campo paymentId
    

1.01

03/10/2025

-   Correção do role responsável pelo envio - de CLIENT para SERVER
    
-   Inclusão do domínio “SCHEDULED” em paymentType
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Regras de  
Validação

1.01

25/08/2026

-   Inclusão de enum em paymentType - WITHDRAW, CHANGE
    

2026C

1.00

20/02/2026

-   Versão inicial
    

Regras de  
Validação -  
Comportamento  
Estados de  
Pagamento

1.02

25/08/2026

-   Refinamento da regra de validação “Ausência de status SCHD em Estados de Pagamento” - _Para pagamentos do tipo SCHEDULED ou RECURRENT, caso o pagamento não tenha sido rejeitado ou cancelado, deve haver obrigatoriamente um Estado de Pagamento SCHD_
    

2026C

1.01

11/06/2026

-   Revisão e ajustes nas regras e critérios de validação
    

2026B

906 - 11/06/2026

1.00

20/04/2026

-   Versão inicial
    

# **Integração Técnica**

**Área**

**Versão**

**Data**

**Mudança realizada**

**Release**

**Informa**

**Especificações de Reporte**

Processo de  
Reporte

v.50

31/10/2025

-   Atualização do link do manual de integtação
    
-   Inclusão e ajustes dos modelos dos reportes
    
-   Inclusão de informações sobre additionalInfo
    
-   Inclusão e ajustes das formas de envio
    

v.1

22/12/2022

-   Versão inicial
    

Processamento  
de Dados

v.11

21/11/2025

-   Retirado um trecho da Conciliação que estava gerando dúvida sobre o processo de descarte do campo fapiInteractionId x statusCode 408 e 5xx.
    
-   Ajustado o diagrama de Ciclo de vida do reporte para refletir o processo correto na ausência do fapiInteractionId para statusCode 408 e 5xx.
    
-   Ajustada a definição de ACCEPTED, refletindo o ajuste realizado no diagrama do Ciclo de vida de reporte.
    

v.10

23/02/2024

-   Inclusão do processo de conciliação
    
-   Inclusão do ciclo de vida do reporte
    

v.1

22/12/2022

-   Versão inicial
    

Tratamento de  
Divergências

v.4

25/12/2022

-   Ajuste de texto (inconsistências)
    

v.1

22/12/2022

-   Versão inicial
    

**Documentação da API**

v.7

07/10/2025

-   Movimentação da visualização legada para a estrutura de histórico
    

v.1

25/08/2025

-   Versão inicial
    

# **Gestão Operacional**

**Área**

**Versão**

**Data**

**Mudança realizada**

**Release**

**Informa**

**Notificações via ticket**

SLA de Envio 95%

1.02

10/11/2025

-   Ajuste da fórmula apresentada de cálculo do SLA - o cálculo está sendo feito corretamente, porém a fórmula documentada não estava refletindo a realidade
    

2025D

815 - 18/11/2025

1.01

10/10/2025

-   Início do envio dos tickets de SLA de Envio de Dados Cadastrais e Transacionais (Fases 2 e 4b)
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

SLA de envio 99%

1.01

11/06/2026

-   Maior clareza na referência do percentual de SLA - _perc\_sla\_metodo\_endpoint: percentual calculado do SLA por método e endpoint_
    

2026B

906 - 11/06/2026

1.00

25/03/2026

-   Versão inicial
    

Qualidade de  
Dados

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Reportes  
Descartados

1.01

03/11/2025

-   Início do envio dos tickets de Reportes Descartados de Segurança
    

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

Reportes  
Não Pareados

1.00

22/08/2025

-   Versão inicial
    

2025C

781 - 22/08/2025

**FAQ**

v.5

25/08/2026

-   Atualização das respostas às perguntas do FAQ
    

2026C

v.4

15/04/2024

-   Atualização do descritivo do SLA de reportes à PCM
    
-   Inclusão de informação sobre crítica de criação de consentimento
    

v.1

18/01/2023

-   Versão inicial
    

**Troubleshooting**

v.6

08/04/2024

-   Inclusão das críticas “Report is too old” e “OrganisationId doesn’t exist on Directory”
    

v.1

18/01/2023

-   Versão inicial
    

# **Controle de Versões**

**Área**

**Versão**

**Data**

**Mudança realizada**

**Release**

**Informa**

Release Notes

1.00

15/09/2025

-   Versão inicial
    

Release Candidate

1.00

09/10/2025

-   Versão inicial
    

Calendário de releases

1.00

09/10/2025

-   Versão inicial
    

Changelog completo

1.01

-   Reestruturação do changelog de acordo com a nova árvore de documentação da PCM
    

1.00

-   Versão inicial
    

2025C

781 - 22/08/2025
