# Estados de Pagamento - Regras de Validação

v 1.01

**Objetivo desta página**

Demonstrar funcionalmente as regras de validação de qualidade de campos básicos e additionalInfos realizados na PCM. Estas validações são utilizadas para aberturas de tickets e monitoramento através do dashboard de Monitoramento Operacional.

**Guia de leitura**

1.  Nos endpoints, a referência “v_x_” deve ser substituída pela versão da API que está sendo enviada. Por exemplo, para a versão 4 (v4) dos endpoints de pagamento, enviar “open-banking/automatic-payments/**v**_**4**_/recurring-consents/{recurringConsentId}”.
    
2.  Nos endpoints, a referência % significa que vale para qualquer conteúdo antes ou depois, de acordo com o endpoint em questão. Por exemplo, “%/automatic-payments/v_x_/recurring-consents%” significa que vale para os endpoints “/open-banking/automatic-payments/v2/recurring-consents” e “/open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId}”.
    

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Estados de Pagamento

**Campo**

**Regra**

cancellationReason

**SE**

-   paymentStatus = CANC
    

**ENTÃO**

-   Se o statusReasonCode for nulo, retorna Nulo
    
-   Se o statusReasonCode for vazio, retorna Vazio
    
-   Se o statusReasonCode não for CANCELADO\_AGENDAMENTO, CANCELADO\_PENDENCIA ou CANCELADO\_MULTIPLAS\_ALCADAS, retorna Invalido
    

clientOrgid

-   Se o clientOrgId for nulo, retorna Nulo
    
-   Se o clientOrgId for vazio, retorna Vazio
    

consentId

-   Se o consentId for nulo, retorna Nulo
    
-   Se o consentId for vazio, retorna Vazio
    
-   Se o REGEX do consentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*''%\\/?#\]+$, retorna Invalido
    

eventDateTime

-   Se o eventDateTime for nulo, retorna Nulo
    
-   Se o eventDateTime for vazio, retorna Vazio
    

paymentId

-   Se o paymentId for nulo, retorna Nulo
    
-   Se o paymentId for vazio, retorna Vazio
    
-   Se o REGEX do paymentId não for ^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$, retorna Invalido
    

paymentStatus

-   Se o paymentStatus for nulo, retorna Nulo
    
-   Se o paymentStatus for vazio, retorna Vazio
    
-   Se o paymentStatus não for CANC, RJCT, ACSC ou SCHD, retorna Invalido
    

paymentType

-   Se o paymentType for nulo, retorna Nulo
    
-   Se o paymentType for vazio, retorna Vazio
    
-   Se o paymentType não for SWEEPING, IMMEDIATE, SCHEDULED, RECURRENT, AUTOMATIC, WITHDRAW ou CHANGE, retorna Invalido
    

qtd\_paymentId

**SE**

-   paymentType = RECURRENT
    
-   **E** quantidade de paymentId diferentes para o mesmo consentId for maior do que 60
    

**ENTÃO**

-   Retorna Quantidade de paymentId para o consentId maior do que 60 para pagamentos recorrentes
    

rejectionReason

**SE**

-   paymentStatus = RJCT
    

**ENTÃO**

-   Se o statusReasonCode for nulo, retorna Nulo
    
-   Se o statusReasonCode for vazio, retorna Vazio
    
-   Se o statusReasonCode não for AUTENTICACAO\_DIVERGENTE, CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO, COBRANCA\_INVALIDA, CONSENTIMENTO\_INVALIDO, CONSENTIMENTO\_REVOGADO, CONTA\_NAO\_PERMITE\_PAGAMENTO, CONTAS\_ORIGEM\_DESTINO\_IGUAIS, DETALHE\_PAGAMENTO\_INVALIDO, DETALHE\_TENTATIVA\_INVALIDO, FALHA\_AGENDAMENTO\_PAGAMENTOS, FALHA\_INFRAESTRUTURA, FALHA\_INFRAESTRUTURA\_DETENTORA, FALHA\_INFRAESTRUTURA\_DICT, FALHA\_INFRAESTRUTURA\_ICP, FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR, FALHA\_INFRAESTRUTURA\_SPI, FORA\_PRAZO\_PERMITIDO, LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO, LIMITE\_PERIODO\_VALOR\_EXCEDIDO, LIMITE\_TENTATIVAS\_EXCEDIDO, LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO, LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO, NAO\_INFORMADO, PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO, PAGAMENTO\_RECUSADO\_DETENTORA, PAGAMENTO\_RECUSADO\_SPI, PERMISSAO\_INSUFICIENTE, QRCODE\_INVALIDO, REJEITADO\_USUARIO, SALDO\_INSUFICIENTE, TEMPO\_EXPIRADO\_AUTORIZACAO, TEMPO\_EXPIRADO\_CONSUMO, TITULARIDADE\_INCONSISTENTE, VALOR\_ACIMA\_LIMITE ou VALOR\_INVALIDO, retorna Invalido
