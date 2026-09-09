# Iniciação de Pagamentos - Regras de Validação

v 1.06

**Objetivo desta página**

Demonstrar funcionalmente as regras de validação de qualidade de campos básicos e additionalInfos realizados na PCM. Estas validações são utilizadas para aberturas de tickets e monitoramento através do dashboard de Monitoramento Operacional.

**Guia de leitura**

1.  Nos endpoints, a referência “v_x_” deve ser substituída pela versão da API que está sendo enviada. Por exemplo, para a versão 4 (v4) dos endpoints de pagamento, enviar “open-banking/automatic-payments/**v**_**4**_/recurring-consents/{recurringConsentId}”.
    
2.  Nos endpoints, a referência % significa que vale para qualquer conteúdo antes ou depois, de acordo com o endpoint em questão. Por exemplo, “%/automatic-payments/v_x_/recurring-consents%” significa que vale para os endpoints “/open-banking/automatic-payments/v2/recurring-consents” e “/open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId}”.
    

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Iniciação de Pagamentos

**Campo**

**Regra**

authorisationFlow

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %payments/v_x_/pix/payments ou %payments/v_x_/pix/payments/{paymentId}
    
-   **E** método = POST, PATCH ou GET
    

**ENTÃO**

-   Se o authorisationFlow for nulo, retorna Nulo
    
-   Se o authorisationFlow for vazio, retorna Vazio
    
-   Se o authorisationFlow não for CIBA\_FLOW, FIDO\_FLOW ou HYBRID\_FLOW, retorna Invalido
    

authorisationFlowIntent

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents
    
-   **E** método = POST, PATCH ou GET
    

**ENTÃO**

-   Se o authorisationFlowIntent for nulo, retorna Nulo
    
-   Se o authorisationFlowIntent for vazio, retorna Vazio
    
-   Se o authorisationFlowIntent não for CIBA\_FLOW, FIDO\_FLOW ou HYBRID\_FLOW, retorna Invalido
    

cancellationReason

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/vx/pix/payments/{paymentId}
    
-   **E** método = PATCH ou GET
    
-   **E** statusCode = 200
    

**ENTÃO**

-   Se o cancellationReason for nulo, retorna Nulo
    
-   Se o cancellationReason for vazio, retorna Vazio
    
-   Se o cancellationReason não for CANCELADO\_PENDENCIA, CANCELADO\_AGENDAMENTO ou CANCELADO\_MULTIPLAS\_ALCADA, retorna Invalido
    

cancelledFrom

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/vx/pix/payments/{paymentId}
    
-   **E** método = PATCH ou GET
    
-   **E** statusCode = 200
    

**ENTÃO**

-   Se o cancelledFrom for nulo, retorna Nulo
    
-   Se o cancelledFrom for vazio, retorna Vazio
    
-   Se o cancelledFrom não for DETENTORA ou INICIADORA, retorna Invalido
    

companyProfileInfo

**SE**

-   Role = CLIENT
    
-   **E** personType = PJ ou PESSOA\_JURIDICA
    
-   **E** endpoint = %/payments/v_x_/consents
    
-   **E** método = POST
    

**ENTÃO**

-   Se naturezaJuridica e porteEmpresa forem simultaneamente nulos ou vazios, retorna Nulo/Vazio
    
-   Se naturezaJuridica for nulo ou vazio e porteEmpresa estiver preenchido, retorna Incompleto - sem Natureza Juridica
    
-   Se naturezaJuridica estiver preenchido e porteEmpresa estiver nulo ou vazio, retorna Incompleto - sem Porta da Empresa
    

consentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents ou %/payments/v_x_/consents/{consentId}
    
    -   **E** método = GET ou PATCH com qualquer statusCode  
        **OU** POST com statusCode diferente de 4xx e 5xx
        
-   **OU** %/payments/v_x_/pix/payments ou %/payments/v_x_/pix/payments/{paymentId}​ ou %/payments/v_4_/pix/payments/consents/{consentId} ou %/payments/v_5_/consents/{consentId}/pix/payments
    
    -   **E** método = POST, GET ou PATCH com qualquer statusCode
        

**ENTÃO**

-   Se o consentId for nulo, retorna Nulo
    
-   Se o consentId for vazio, retorna Vazio
    
-   Se o REGEX do consentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*''%/?#\]+, retorna Invalido
    

dropReason

**SE**

-   Role = SERVER
    
-   **E** endpoint = %/payments/v_x_/consents
    
-   **E** método = POST
    

**ENTÃO**

-   Se o dropReason for nulo, retorna Nulo
    
-   Se o dropReason for vazio, retorna Vazio
    
-   Se o dropReaso não for CREDENTIAL\_UNAVAILABLE, NONE, NO\_CREDENTIAL, NO\_AUTHORITY ou NO\_AUTHORITY\_PERSON\_MISMATCH, retorna Invalido
    

errorCodes

**SE**

-   Role = CLIENT
    
-   **E** statusCode = 4xx ou 5xx
    
-   **E** endpoint = %/payments/v_x_/consents%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["DATA\_PAGAMENTO\_INVALIDA"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["FORMA\_PAGAMENTO\_INVALIDA"\], \["NAO\_INFORMADO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\] ou \[“PROPOSITO\_INVALIDO“\], retorna Invalido
        
-   **OU** endpoint = %/payments/v_x_/pix/payments%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["COBRANCA\_INVALIDA"\], \["CONSENTIMENTO\_INVALIDO"\], \["CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"\], \["CONTA\_NAO\_PERMITE\_PAGAMENTO"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["NAO\_INFORMADO"\], \["PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"\], \["PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO"\], \["PAGAMENTO\_RECUSADO\_DETENTORA"\], \["PAGAMENTO\_RECUSADO\_SPI"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["QRCODE\_INVALIDO"\], \["SALDO\_INSUFICIENTE"\], \["VALOR\_ACIMA\_LIMITE"\] ou \["VALOR\_INVALIDO"\], retorna Invalido
        

localInstrument

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents ou %/payments/v_x_/pix/payments/{paymentId}
    
-   **E** método = POST
    
    -   **OU** PATCH, GET com statusCode diferente de 4xx e 5xx
        

**ENTÃO**

-   Se o localInstrument for nulo, retorna Nulo
    
-   Se o localInstrument for vazio, retorna Vazio
    
-   Se o localInstrument não for DICT, INIC, MANU, QRDN, QRES, AUTO, APDN ou APES, retorna Invalido
    

paymentDate

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents
    
-   **E** método = POST
    
-   **E** statusCode = 201
    
-   **E** paymentType = SWEEPING ou AUTOMATIC
    

**ENTÃO**

-   Se o paymentDate for nulo ou vazio e paymentSchedule for nulo ou vazio, retorna Deve ser informado pelo menos paymentDate ou paymentSchedule
    
-   Se o paymentDate não for nulo ou vazio e paymentSchedule não for nulo ou vazio, retorna Nao podem ser preenchidos simultaneamente paymentDate e paymentSchedule
    

paymentList

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/pix/payments
    
-   **E** método = POST
    
-   **E** statusCode = 201
    
-   **E** paymentType = IMMEDIATE, SCHEDULED ou RECURRENT
    

**ENTÃO**

-   Se o paymentList for nulo, retorna Nulo
    
-   Se o paymentList for vazio, retorna Vazio
    

paymentSchedule

**SE**

-   Role = CLIENT
    
-   **E** paymentType for SCHEDULED ou RECURRENT
    
-   **E** endpoint = %/payments/v_x_/consents
    
-   **E** método = POST
    
-   **E** statusCode = 201
    

**ENTÃO**

-   Se o conteúdo do paymentSchedule não tiver os tipos _single, daily, weekly, monthly_ ou _custom_, retorna Conteudo do additionalInfo paymentSchedule nulo ou invalido
    
-   Se o tipo de agendamento for _single_
    
    -   Se não possuir o campo _date_, retorna Conteudo do agendamento single nulo ou invalido
        
-   Se o tipo de agendamento for _daily_
    
    -   Se não possuir os campos _startDate_ ou _quantity_, retorna Conteudo do agendamento diario nulo ou invalido
        
-   Se o tipo de agendamento for _weekly_
    
    -   Se não possuir os campos _dayOfWeek, startDate_ ou _quantity_, retorna Conteudo do agendamento semanal nulo ou invalido
        
-   Se o tipo de agendamento for _monthly_
    
    -   Se não possuir os campos _dayOfMonth, startDate_ ou _quantity_, retorna Conteudo do agendamento mensal nulo ou invalido
        
-   Se o tipo de agendamento for _custom_
    
    -   Se não possuir o campo _dates_, retorna Conteudo do agendamento custom nulo ou invalido
        

paymentType

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents ou %/payments/v_x_/pix/payments
    
    -   **E** método = POST
        
-   **OU** endpoint = %/payments/v_x_/pix/payments/{paymentId}
    
    -   **E** método = PATCH
        

**ENTÃO**

-   Se paymentType for nulo, retorna Nulo
    
-   Se paymentType for vazio, retorna Vazio
    
-   Se paymentType não for AUTOMATIC, IMMEDIATE, RECURRENT, SCHEDULED, SWEEPING, WITHDRAW ou CHANGE, retorna Invalido
    

personType

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents
    
-   **E** método = POST
    

**ENTÃO**

-   Se personType for nulo, retorna Nulo
    
-   Se personType for vazio, retorna Vazio
    
-   Se personType não for PF, PJ, PESSOA\_JURIDICA ou PESSOA\_NATURAL, retorna Invalido
    

rejectionReasonCode

**SE**

-   Role = CLIENT
    
-   **E** status = RJCT ou REJECTED
    
-   **E** endpoint = %/payments/v_x_/consents/{consentId} ou %/payments/v_x_/pix/payments/{paymentId}
    
-   **E** método = GET
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se rejectionReasonCode for nulo, retorna Nulo
    
-   Se rejectionReasonCode for vazio, retorna Vazio
    
-   Se rejectionReasonCode não for AUTENTICACAO\_DIVERGENTE, CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO, COBRANCA\_INVALIDA, CONSENTIMENTO\_INVALIDO, CONSENTIMENTO\_REVOGADO, CONTA\_NAO\_PERMITE\_PAGAMENTO, CONTAS\_ORIGEM\_DESTINO\_IGUAIS, DETALHE\_PAGAMENTO\_INVALIDO, DETALHE\_TENTATIVA\_INVALIDO, FALHA\_AGENDAMENTO\_PAGAMENTOS, FALHA\_INFRAESTRUTURA, FALHA\_INFRAESTRUTURA\_DETENTORA, FALHA\_INFRAESTRUTURA\_DICT, FALHA\_INFRAESTRUTURA\_ICP, FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR, FALHA\_INFRAESTRUTURA\_SPI, FORA\_PRAZO\_PERMITIDO, LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO, LIMITE\_PERIODO\_VALOR\_EXCEDIDO LIMITE\_TENTATIVAS\_EXCEDIDO, LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO, LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO, NAO\_INFORMADO, PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO, PAGAMENTO\_RECUSADO\_DETENTORA, PAGAMENTO\_RECUSADO\_SPI, PERMISSAO\_INSUFICIENTE, QRCODE\_INVALIDO, REJEITADO\_USUARIO, SALDO\_INSUFICIENTE, TEMPO\_EXPIRADO\_AUTORIZACAO, TEMPO\_EXPIRADO\_CONSUMO, TITULARIDADE\_INCONSISTENTE, VALOR\_ACIMA\_LIMITE ou VALOR\_INVALIDO, retorna Invalido
    

rejectionReasonDetail

**SE**

-   Role = CLIENT
    
-   **E** status = RJCT ou REJECTED
    
-   **E** endpoint = %/payments/v_x_/consents/{consentId} ou %/payments/v_x_/pix/payments/{paymentId}
    
-   **E** método = GET
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se rejectionReasonDetail for nulo, retorna Nulo
    
-   Se rejectionReasonDetail for vazio, retorna Vazio
    

status

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents, %/payments/v_x_/pix/payments, %/payments/v_x_/pix/payments/{paymentId}, %/payments/v_4_/pix/payments/consents/{consentId} ou %/payments/v_5_/consents/{consentId}/pix/payments
    
    -   **E** método = POST, GET ou PATCH
        
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se status for nulo, retorna Nulo
    
-   Se status for vazio, retorna Vazio
    
-   Se status não for AWAITING\_AUTHORISATION, AUTHORISED, REJECTED, PARTIALLY\_ACCEPTED, REVOKED, CONSUMED, AWAITING\_RISK\_SIGNALS, AWAITING\_ACCOUNT\_HOLDER\_VALIDATION, AWAITING\_ENROLLMENT, RCVD, CANC, ACCP, ACPD, RJCT, ACSC, PDNG ou SCHD, retorna Invalido
    

tokenId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/%x/consents, %/payments/v%/consents/{consentId}, %/payments/v%/pix/payments, %/payments/v%/pix/payments/{paymentId}, %/payments/v4/pix/payments/consents/{consentId} ou %/payments/v5/consents/{consentId}/pix/payments
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se o tokenId for nulo, retorna Nulo
    
-   Se o tokenId for vazio, retorna Vazio
    

webhookInteractionId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/payments/v_x_/consents/{consentId}
    
-   **E** statusCode não é 4xx e 5xx
    

**ENTÃO**

-   Se o webhookInteractionId for nulo, retorna Nulo
    
-   Se o webhookInteractionId for vazio, retorna Vazio
