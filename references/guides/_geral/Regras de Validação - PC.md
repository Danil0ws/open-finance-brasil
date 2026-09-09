# Regras de Validação - PC

v 1.04

**Objetivo desta página**

Demonstrar funcionalmente as regras de validação de qualidade de campos básicos e additionalInfos realizados na PCM. Estas validações são utilizadas para aberturas de tickets e monitoramento através do dashboard de Monitoramento Operacional.

**Guia de leitura**

1.  Nos endpoints, a referência “v_x_” deve ser substituída pela versão da API que está sendo enviada. Por exemplo, para a versão 4 (v4) dos endpoints de pagamento, enviar “open-banking/automatic-payments/**v**_**4**_/recurring-consents/{recurringConsentId}”.
    
2.  Nos endpoints, a referência % significa que vale para qualquer conteúdo antes ou depois, de acordo com o endpoint em questão. Por exemplo, “%/automatic-payments/v_x_/recurring-consents%” significa que vale para os endpoints “/open-banking/automatic-payments/v2/recurring-consents” e “/open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId}”.
    

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Portabilidade de Crédito**

**Campo**

**Regra**

clientSSId

**SE**

-   Role = CLIENT
    
-   **E** método = POST, GET ou PATCH
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities%
    

**ENTÃO**

-   Se o clientSSId for nulo, retorna Nulo
    
-   Se o clientSSId for vazio, retorna Vazio
    
-   Se o REGEX do clientSSId não for ^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$, retorna Invalido
    

consentId

**SE**

-   Método = POST
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities ou %/credit-portability/v_x_/portabilities/{portabilityId}
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se o consentId for nulo, retorna Nulo
    
-   Se o consentId for vazio, retorna Vazio
    
-   Se o REGEX do consentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$, retorna Invalido
    

creationDateTime

**SE**

-   Role = CLIENT
    
-   **E** método = POST ou GET
    
-   **E** statusCode não é 4xx ou 5xx
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities ou %/credit-portability/v_x_/portabilities
    

**ENTÃO**

-   Se o creationDateTime for nulo, retorna Nulo
    
-   Se o creationDateTime for vazio, retorna Vazio
    
-   Se o REGEX do creationDateTime não for ^\\d{4}-\\d{2}-\\d{2}T(?:\[01\]\\d|2\[0-3\]):\[0-5\]\\d:\[0-5\]\\d(?:\\.\\d+)?(?:Z|\[+-\]\[01\]\\d:\[0-5\]\\d)$, retorna Invalido
    

creditPortabilityStatus

**SE**

-   Método = GET
    
-   **E** statusCode não é 4xx ou 5xx
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities/{portabilityId}
    

**ENTÃO**

-   Se o creditPortabilityStatus for nulo, retorna Nulo
    
-   Se o creditPortabilityStatus for vazio, retorna Vazio
    
-   Se o creditPortabilityStatus não for ACCEPTED\_SETTLEMENT\_COMPLETED, ACCEPTED\_SETTLEMENT\_IN\_PROGRESS, CANCELLED, PENDING, PAYMENT\_ISSUE, PORTABILITY\_COMPLETED, RECEIVED ou REJECTED, retorna Invalido
    

endpoint

**SE**

-   endpoint for nulo, retorna Nulo
    
-   endpoint for vazio, retorna Vazio
    
-   endpoint não for um endpoint válido para Portabilidade de Crédito, retorna Invalido
    

endpointUriPrefix

**SE**

-   Role = CLIENT
    
-   **E** método = POST, GET ou PATCH
    

**ENTÃO**

-   Se o endpointUriPrefix for nulo, retorna Nulo
    
-   Se o endpointUriPrefix for vazio, retorna Vazio
    
-   Se o REGEX do endpointUriPrefix não for ^\[- /:\_.',0-9a-zA-Z\]{0,200}$, retorna Invalido
    

errorCode

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities%
    
-   **E** método = POST, GET ou PATCH
    
-   **E** statusCode for 4xx ou 5xx
    

**ENTÃO**

-   Se o errorCode for nulo, retorna Nulo
    
-   Se o errorCode for vazio, retorna Vazio
    

portabilityId

**SE**

-   Método = POST ou GET
    
-   **E** statusCode não for 4xx ou 5xx
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities ou %/credit-portability/v_x_/portabilities/{portabilityId}
    

**ENTÃO**

-   Se o portabilityId for nulo, retorna Nulo
    
-   Se o portabilityId for vazio, retorna Vazio
    
-   Se o REGEX do portabilityId não for ^\[0-9a-fA-F\]{8}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{4}-\[0-9a-fA-F\]{12}$, retorna Invalido
    

rejectedBy

**SE**

-   Método = GET ou PATCH
    
-   **E** statusCode não é 4xx ou 5xx
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities/{portabilityId} ou %/credit-portability/v_x_/portabilities/{portabilityId}/cancel
    
-   **E** creditPortabilityStatus = REJECTED ou CANCELLED
    

**ENTÃO**

-   Se o rejectedBy for nulo, retorna Nulo
    
-   Se o rejectedBy for vazio, retorna Vazio
    
-   Se o rejectedBy não for CREDORA, PROPONENTE ou USUARIO, retorna Invalido
    

rejectionReason

**SE**

-   Método = GET ou PATCH
    
-   **E** statusCode não é 4xx ou 5xx
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities/{portabilityId} ou %/credit-portability/v_x_/portabilities/{portabilityId}/cancel
    
-   **E** creditPortabilityStatus = REJECTED ou CANCELLED
    

**ENTÃO**

-   Se o rejectionReason for nulo, retorna Nulo
    
-   Se o rejectionReason for vazio, retorna Vazio
    
-   Se o rejectedBy não for POLITICA\_DE\_CREDITO, SALDO\_DEVEDOR\_ATUALIZADO\_SUBSTANCIALMENTE\_DIVERGENTE, CLIENTE\_COM\_ACAO\_JUDICIAL, CONTRATO\_JA\_LIQUIDADO, DECURSO\_DO\_PRAZO\_PARA\_PAGAMENTO, MODALIDADE\_DA\_OPERACAO\_INCOMPATIVEL, PORTABILIDADE\_CANCELADA\_POR\_FALTA\_DE\_LIQUIDACAO, PORTABILIDADE\_EM\_ANDAMENTO, RETENCAO\_DO\_CLIENTE, CANCELADO\_PELO\_CLIENTE, DIVERGENCIA\_DE\_PAGAMENTO\_EFETUADO ou OUTROS, retorna Invalido
    

statusUpdateDateTime

**SE**

-   Método = GET
    
-   **E** statusCode não for 4xx ou 5xx
    
-   **E** endpoint = %/credit-portability/v_x_/portabilities/{portabilityId}
    

**ENTÃO**

-   Se o statusUpdateDateTime for nulo, retorna Nulo
    
-   Se o statusUpdateDateTime for vazio, retorna Vazio
