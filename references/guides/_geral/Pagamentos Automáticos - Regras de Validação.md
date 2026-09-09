# Pagamentos Automáticos - Regras de Validação

v 1.06

**Objetivo desta página**

Demonstrar funcionalmente as regras de validação de qualidade de campos básicos e additionalInfos realizados na PCM. Estas validações são utilizadas para aberturas de tickets e monitoramento através do dashboard de Monitoramento Operacional.

**Guia de leitura**

1.  Nos endpoints, a referência “v_x_” deve ser substituída pela versão da API que está sendo enviada. Por exemplo, para a versão 4 (v4) dos endpoints de pagamento, enviar “open-banking/automatic-payments/**v**_**4**_/recurring-consents/{recurringConsentId}”.
    
2.  Nos endpoints, a referência % significa que vale para qualquer conteúdo antes ou depois, de acordo com o endpoint em questão. Por exemplo, “%/automatic-payments/v_x_/recurring-consents%” significa que vale para os endpoints “/open-banking/automatic-payments/v2/recurring-consents” e “/open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId}”.
    

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Pagamentos Automáticos

**Campo**

**Regra**

amountType

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents%
    
-   **E** método = POST  
    **OU** PATCH ou GET com statusCode diferente de 4xx ou 5xx
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se o amountType for nulo, retorna Nulo
    
-   Se o amountType for vazio, retorna Vazio
    
-   Se o amountType não for FIXO ou VARIAVEL, retorna Invalido
    

authorisationFlow

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments ou %/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   **E** método = POST, PATCH ou GET
    

**ENTÃO**

-   Se o authorisationFlow for nulo, retorna Nulo
    
-   Se o authorisationFlow for vazio, retorna Vazio
    
-   Se o authorisationFlow não for CIBA\_FLOW, FIDO\_FLOW ou HYBRID\_FLOW, retorna Invalido
    

authorisationFlowIntent

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents
    
-   **E** método = POST, PATCH ou GET
    

**ENTÃO**

-   Se o authorisationFlowIntent for nulo, retorna Nulo
    
-   Se o authorisationFlowIntent for vazio, retorna Vazio
    
-   Se o authorisationFlowIntent não for CIBA\_FLOW, FIDO\_FLOW ou HYBRID\_FLOW, retorna Invalido
    

cancellationReason

**SE**

-   Role = CLIENT
    
-   **E** status = CANC
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments ou %/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   **E** método = POST, PATCH ou GET
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se o cancellationReason for nulo, retorna Nulo
    
-   Se o cancellationReason for vazio, retorna Vazio
    
-   Se o cancellationReason não for CANCELADO\_AGENDAMENTO ou CANCELADO\_PENDENCIA, retorna Invalido
    

cancelledFrom

**SE**

-   Role = CLIENT
    
-   **E** status = CANC
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments ou %/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   **E** método = POST, GET ou PATCH
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se o cancelledFrom for nulo, retorna Nulo
    
-   Se o cancelledFrom for vazio, retorna Vazio
    
-   Se o cancelledFrom não for INICIADORA ou DETENTORA, retorna Invalido
    

companyProfileInfo

**SE**

-   Role = CLIENT
    
-   **E** personType = PJ ou PESSOA\_JURIDICA
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents
    
-   **E** método = POST
    

**ENTÃO**

-   Se naturezaJuridica e porteEmpresa forem simultaneamente nulos ou vazios, retorna Nulo/Vazio
    
-   Se naturezaJuridica for nulo ou vazio e porteEmpresa estiver preenchido, retorna Incompleto - sem Natureza Juridica
    
-   Se naturezaJuridica estiver preenchido e porteEmpresa estiver nulo ou vazio, retorna Incompleto - sem Porta da Empresa
    

dropReason

**SE**

-   Role = SERVER
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents
    
-   **E** método = POST
    

**ENTÃO**

-   Se o dropReason for nulo, retorna Nulo
    
-   Se o dropReason for vazio, retorna Vazio
    
-   Se o dropReason não for CREDENTIAL\_UNAVAILABLE, NONE, NO\_CREDENTIAL, NO\_AUTHORITY ou NO\_AUTHORITY\_PERSON\_MISMATCH, retorna Invalido
    

errorCodes

**SE**

-   Role = CLIENT
    
-   **E** statusCode = 4xx ou 5xx
    
-   **E** endpoint = %automatic-payments/v_x_/recurring-payments%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO"\], \["CONSENTIMENTO\_INVALIDO"\], \["CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["FORA\_PRAZO\_PERMITIDO"\], \["LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO"\], \["LIMITE\_PERIODO\_VALOR\_EXCEDIDO"\], \["LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"\], \["LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"\], \["NAO\_INFORMADO"\], \["PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"\], \["PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO"\], \["PAGAMENTO\_RECUSADO\_DETENTORA"\], \["PAGAMENTO\_RECUSADO\_SPI"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["SALDO\_INSUFICIENTE"\], \["VALOR\_ACIMA\_LIMITE"\] ou \["VALOR\_INVALIDO"\], retorna Invalido
        
-   **OU** endpoint = %automatic-payments/v_x_/recurring-consents%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["CAMPO\_NAO\_PERMITIDO"\], \["CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO"\], \["DATA\_PAGAMENTO\_INVALIDA"\], \["DETALHE\_EDICAO\_INVALIDO"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["FALTAM\_SINAIS\_OBRIGATORIOS\_PLATAFORMA"\], \["FUNCIONALIDADE\_NAO\_HABILITADA"\], \["NAO\_INFORMADO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSAO\_INSUFICIENTE"\], retorna Invalido
        

hasMinimumAmount

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents%
    
-   **E** método = POST
    
    **OU** método = GET ou PATCH e statusCode diferente de 4xx e 5xx
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se o hasMinimumAmount for nulo, retorna Nulo
    
-   Se o hasMinimumAmount for vazio, retorna Vazio
    
-   Se o hasMinimumAmount não for TRUE ou FALSE, retorna Invalido
    

interval

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents%
    
-   **E** método = POST  
    **OU** método = GET ou PATCH e statusCode diferente de 4xx e 5xx
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se interval for nulo, retorna Nulo
    
-   Se interval for vazio, retorna Vazio
    
-   Se interval não for SEMANAL, MENSAL, TRIMESTRAL, SEMESTRAL ou ANUAL, retorna Invalido
    

isFirstPayment

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents%
    
-   **E** método = POST  
    **OU** método = GET ou PATCH e statusCode diferente de 4xx e 5xx
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se isFirstPayment for nulo, retorna Nulo
    
-   Se isFirstPayment for vazio, retorna Vazio
    
-   Se isFirstPayment não for TRUE ou FALSE, retorna Invalido
    

isRetryAccepted

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents%
    
-   **E** método = POST  
    **OU** GET ou PATCH e statusCode diferente de 4xx e 5xx
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se isRetryAccepted for nulo, retorna Nulo
    
-   Se isRetryAccepted for vazio, retorna Vazio
    
-   Se isRetryAccepted não for TRUE ou FALSE, retorna Invalido
    

journeyIsLinked

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents, %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   **E** método = POST ou GET
    

**ENTÃO**

-   Se journeyIsLinked for nulo, retorna Nulo
    
-   Se journeyIsLinked for vazio, retorna Vazio
    
-   Se journeyIsLinked não for TRUE ou FALSE, retorna Invalido
    

journeyLinkId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents, %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   **E** método = POST ou GET
    
-   **E** journeyIsLinked = TRUE
    

**ENTÃO**

-   Se journeyLinkId for nulo, retorna Nulo
    
-   Se journeyLinkId for vazio, retorna Vazio
    

localInstrument

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments ou %/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   **E** método = POST
    
    -   **OU** PATCH, GET com statusCode diferente de 4xx e 5xx
        

**ENTÃO**

-   Se o localInstrument for nulo, retorna Nulo
    
-   Se o localInstrument for vazio, retorna Vazio
    
-   Se o localInstrument não for DICT, INIC, MANU, QRDN, QRES, AUTO, APDN ou APES, retorna Invalido
    

originalRecurringPaymentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   **E** método = POST
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se o originalRecurringPaymentId for nulo, retorna Nulo
    
-   Se o originalRecurringPaymentId for vazio, retorna Vazio
    

paymentList

**SE**

-   Role = CLIENT
    
-   **E** endpoint = automatic-payments/v_x_/pix/recurring-payments
    
-   **E** método = GET
    
-   **E** statusCode = 200
    
-   **E** paymentType = SWEEPING ou AUTOMATIC
    

**ENTÃO**

-   Se o paymentList for nulo, retorna Nulo
    
-   Se o paymentList for vazio, retorna Vazio
    

paymentReference

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments% ou /automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   **E** método = POST e PATCH  
    **OU** GET e statusCode diferente de 4xx e 5xx
    
-   **E** paymentType = AUTOMATIC
    

**ENTÃO**

-   Se paymentReference for nulo, retorna Nulo
    
-   Se paymentReference for vazio, retorna Vazio
    

paymentType

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents% ou %/automatic-payments/v_x_/pix/recurring-payments% e não for %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
    -   **E** método = POST
        
        -   **OU** GET ou PATCH com statusCode diferente de 4xx e 5xx
            

**ENTÃO**

-   Se o paymentType for nulo, retorna Nulo
    
-   Se o paymentType for vazio, retorna Vazio
    
-   Se o paymentType não for AUTOMATIC, IMMEDIATE, RECURRENT, SCHEDULED, SWEEPING, WITHDRAW ou CHANGE, retorna Invalido
    

personType

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents ou %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   **E** método = POST, PATCH ou GET
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se personType for nulo, retorna Nulo
    
-   Se personType for vazio, retorna Vazio
    
-   Se personType não for PF, PJ, PESSOA\_JURIDICA, PESSOA\_NATURAL, retorna Invalido
    

recurringConsentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = /automatic-payments/v_x_/recurring-consents
    
    -   **E** método = POST
        
    -   **E** statusCode diferente de 4xx e 5xx
        
-   **OU** endpoint = %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
    -   **E** método = GET ou PATCH
        
-   **OU** endpoint = %/automatic-payments/v_x_/pix/recurring-payments, %/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId} ou
    
    %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
    -   **E** método = POST, GET ou PATCH
        

**ENTÃO**

-   Se recurringConsentId for nulo, retorna Nulo
    
-   Se recurringConsentId for vazio, retorna Vazio
    
-   Se o REGEX do recurringConsentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*''%/?#\]+, retorna Invalido
    

recurringPaymentDate

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments
    
-   **E** método = POST
    
-   **E** statusCode = 201
    

**ENTÃO**

-   Se recurringPaymentDate for nulo, retorna Nulo
    
-   Se recurringPaymentDate for vazio, retorna Vazio
    

recurringPaymentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments% ou %/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}
    
-   **E** método = POST, GET e PATCH
    
-   **E** statusCode não é 4xx e 5xx
    

**ENTÃO**

-   Se recurringPaymentId for nulo, retorna Nulo
    
-   Se recurringPaymentId for vazio, retorna Vazio
    
-   Se o REGEX do recurringPaymentId não for ^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$, retorna Invalido
    

referenceStartDate

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/vx/recurring-consents ou %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   **E** método = POST, GET e PATCH
    
-   **E** statusCode = 2xx
    
-   **E** paymenttType = AUTOMATIC
    

**ENTÃO**

-   Se referenceStartDate for nulo, retorna Nulo
    
-   Se referenceStartDate for vazio, retorna Vazio
    

rejectedBy

**SE**

-   Role = CLIENT
    
-   **E** status = RJCT ou REJECTED
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   **E** método = PATCH ou GET
    
-   **E** statusCode não é 4xx e 5xx
    

**ENTÃO**

-   Se o rejectedBy for nulo, retorna Nulo
    
-   Se o rejectedBy for vazio, retorna Vazio
    
-   Se o rejectedBy não for DETENTORA, INICIADORA, USUARIO, retorna Invalido
    

rejectedFrom

**SE**

-   Role = CLIENT
    
-   **E** status = RJCT ou REJECTED
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents/{recurringConsentId}
    
-   **E** método = PATCH ou GET
    
-   **E** statusCode não é 4xx e 5xx
    

**ENTÃO**

-   Se o rejectedFrom for nulo, retorna Nulo
    
-   Se o rejectedFrom for vazio, retorna Vazio
    
-   Se o rejectedFrom não for DETENTORA, INICIADORA, retorna Invalido
    

rejectionReasonCode

**SE**

-   Role = CLIENT
    
-   **E** status = RJCT ou REJECTED
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents% ou %/automatic-payments/v_x_/pix/recurring-payments%
    
-   **E** endpoint não for %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   **E** método = POST, GET ou PATCH
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se rejectionReasonCode for nulo, retorna Nulo
    
-   Se rejectionReasonCode for vazio, retorna Vazio
    
-   Se rejectionReasonCode não for CONSENTIMENTO\_INVALIDO, CONTA\_NAO\_PERMITE\_PAGAMENTO, CONTAS\_ORIGEM\_DESTINO\_IGUAIS, FALHA\_INFRAESTRUTURA, FALHA\_INFRAESTRUTURA\_DETENTORA, FALHA\_INFRAESTRUTURA\_ICP, FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR, FALHA\_INFRAESTRUTURA\_SPI, FLUXO\_NAO\_SUPORTADO\_PRODUTO, FORA\_PRAZO\_PERMITIDO, LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO, LIMITE\_PERIODO\_VALOR\_EXCEDIDO, LIMITE\_TENTATIVAS\_EXCEDIDO, LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO, LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO, NAO\_INFORMADO, PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO, PAGAMENTO\_RECUSADO\_DETENTORA, PAGAMENTO\_RECUSADO\_SPI, REJEITADO\_USUARIO, SALDO\_INSUFICIENTE, TEMPO\_EXPIRADO\_AUTORIZACAO, TITULARIDADE\_INCONSISTENTE, VALOR\_ACIMA\_LIMITE, VALOR\_INVALIDO, retorna Invalido
    

rejectionReasonDetail

**SE**

-   Role = CLIENT
    
-   **E** status = RJCT ou REJECTED
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents/ ou %/automatic-payments/v_x_/recurring-consents//{recurringConsentId}
    
-   **E** método = POST, GET ou PATCH
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se rejectionReasonDetail for nulo, retorna Nulo
    
-   Se rejectionReasonDetail for vazio, retorna Vazio
    

revocationReasonCode

**SE**

-   Role = CLIENT
    
-   **E** status = REVOKED
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents% ou %/automatic-payments/v_x_/pix/recurring-payments%
    
-   **E** endpoint não for %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   **E** método = POST ou GET  
    **OU** PATCH com statusCode diferente de 4xx e 5xx
    

**ENTÃO**

-   Se revocationReasonCode for nulo, retorna Nulo
    
-   Se revocationReasonCode for vazio, retorna Vazio
    
-   Se revocationReasonCode não for NAO\_INFORMADO, REVOGADO\_RECEBEDOR ou REVOGADO\_USUARIO, retorna Invalido
    

revocationReasonDetail

**SE**

-   Role = CLIENT
    
-   **E** status = REVOKED
    
-   **E** endpoint = %/automatic-payments/v_x_/recurring-consents% ou %/automatic-payments/v_x_/recurring-payments%
    
-   **E** endpoint não for %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   **E** método = POST ou GET  
    **OU** PATCH e statusCode diferente de 4xx e 5xx
    

**ENTÃO**

-   Se revocationReasonDetail for nulo, retorna Nulo
    
-   Se revocationReasonDetail for vazio, retorna Vazio
    

status

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments% ou %/automatic-payments/v_x_/recurring-consents%
    
-   **E** endpoint não for %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   **E** método = GET, PATCH ou POST
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se status for nulo, retorna Nulo
    
-   Se status for vazio, retorna Vazio
    
-   Se status não for AWAITING\_AUTHORISATION, AUTHORISED, REJECTED, PARTIALLY\_ACCEPTED, REVOKED, CONSUMED, AWAITING\_RISK\_SIGNALS, AWAITING\_ACCOUNT\_HOLDER\_VALIDATION, AWAITING\_ENROLLMENT, RCVD, CANC, ACCP, ACPD, RJCT, ACSC, PDNG ou SCHD, retorna Invalido
    

tokenId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/automatic-payments/v_x_/pix/recurring-payments% ou %/automatic-payments/v_x_/recurring-consents%
    
-   **E** endpoint não for %/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se tokenId for nulo, retorna Nulo
    
-   Se tokenId for vazio, retorna Vazio
