# Iniciação de Pagamentos Sem Redirecionamento - Regras de Validação

v 1.06

**Objetivo desta página**

Demonstrar funcionalmente as regras de validação de qualidade de campos básicos e additionalInfos realizados na PCM. Estas validações são utilizadas para aberturas de tickets e monitoramento através do dashboard de Monitoramento Operacional.

**Guia de leitura**

1.  Nos endpoints, a referência “v_x_” deve ser substituída pela versão da API que está sendo enviada. Por exemplo, para a versão 4 (v4) dos endpoints de pagamento, enviar “open-banking/automatic-payments/**v**_**4**_/recurring-consents/{recurringConsentId}”.
    
2.  Nos endpoints, a referência % significa que vale para qualquer conteúdo antes ou depois, de acordo com o endpoint em questão. Por exemplo, “%/automatic-payments/v_x_/recurring-consents%” significa que vale para os endpoints “/open-banking/automatic-payments/v2/recurring-consents” e “/open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId}”.
    

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Iniciação de Pagamentos Sem Redirecionamento

**Campo**

**Regra**

authenticatorAttachment

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration
    
-   **E** método = POST
    
-   **E** o authenticatorAttachment não está vazio
    

**ENTÃO**

-   Se o authenticatorAttachment não for platform ou cross-platform, retorna Invalido
    

cancelledFrom

**SE**

-   Role = CLIENT
    
-   **E** status = REVOKED
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = GET
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se o cancelledFrom for nulo, retorna Nulo
    
-   Se o cancelledFrom for vazio, retorna Vazio
    
-   Se o cancelledFrom não for INICIADORA ou DETENTORA, retorna Invalido
    

companyProfileInfo

**SE**

-   Role = CLIENT
    
-   **E** personType = PJ ou PESSOA\_JURIDICA
    
-   **E** endpoint = %/enrollments/v_x_/enrollments
    
-   **E** método = POST
    

**ENTÃO**

-   Se naturezaJuridica e porteEmpresa forem simultaneamente nulos ou vazios, retorna Nulo/Vazio
    
-   Se naturezaJuridica for nulo ou vazio e porteEmpresa estiver preenchido, retorna Incompleto - sem Natureza Juridica
    
-   Se naturezaJuridica estiver preenchido e porteEmpresa estiver nulo ou vazio, retorna Incompleto - sem Porta da Empresa
    

consentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/consents/{consentId}/authorise ou %/enrollments/vx/enrollments/{enrollmentId}/fido-sign-options
    
-   **E** não é método = POST com statusCode 4xx ou 5xx
    

**ENTÃO**

-   Se for o endpoint /open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options consentId e o recurringConsentId estiverem simultaneamente preenchidos, retorna Invalido - nao podem ser preenchidos simultaneamente consentId e recurringConsentId
    
-   Se for o endpoint /open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options consentId e o recurringConsentId estiverem simultaneamente vazios ou nulos, retorna Pelo menos consentId ou recurringConsentId deve estar preenchido
    
-   Se o enrollmentId e o consentId forem simultaneamente nulos, retorna Nulo
    
-   Se o enrollmentId e o consentId forem simultaneamente vazios, retorna Vazio
    
-   Se o REGEX do consentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*''%/?#\]+, retorna Invalido
    

dropReason

**SE**

-   Role = SERVER
    
-   **E** endpoint = %/enrollments/v_x_/enrollments
    
-   **E** método = POST
    

**ENTÃO**

-   Se o dropReason for nulo, retorna Nulo
    
-   Se o dropReason for vazio, retorna Vazio
    
-   Se o dropReason não for CREDENTIAL\_UNAVAILABLE, NONE, NO\_CREDENTIAL, NO\_AUTHORITY ou NO\_AUTHORITY\_PERSON\_MISMATCH, retorna Invalido
    

enrollmentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/open-banking/enrollments/v_x_/enrollments ou %/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise
    
    -   **E** método = POST
        
    -   **E** statusCode = 2x
        
-   **OU** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration, %/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options, %/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals ou %/enrollments/v_x_/consents/{consentId}/authorise
    
    -   **E** método = POST
        

**ENTÃO**

-   Se o enrollmentId e o consentId forem simultaneamente nulos, retorna Nulo
    
-   Se o enrollmentId e o consentId forem simultaneamente vazios, retorna Vazio
    

errorCodes

**SE**

-   Role = CLIENT
    
-   **E** statusCode = 4xx ou 5xx
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["CONTA\_INVALIDA"\], \["ERRO\_IDEMPOTENCIA"\], \["MOTIVO\_REJEICAO"\], \["MOTIVO\_REVOGACAO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSOES\_INVALIDAS"\], \["REJEITADO\_OUTRO\_SEM\_DETALHES"\], \["REVOGADO\_OUTRO\_SEM\_DETALHES"\] ou \["STATUS\_INVALIDO"\], retorna Invalido
        
-   **OU** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}/fido%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["CHALLENGE\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["EXTENSION\_INVALIDA"\], \["MAXIMO\_CHALLENGES\_ATINGIDO"\], \["ORIGEM\_FIDO\_INVALIDA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO"\], \["PUBLIC\_KEY\_INVALIDA"\], \["RP\_INVALIDA"\], \["STATUS\_CONSENTIMENTO\_INVALIDO"\] ou \["STATUS\_VINCULO\_INVALIDO"\], retorna Invalido
        
-   OU endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}/risk%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["ERRO\_IDEMPOTENCIA"\], \["FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\] ou \["STATUS\_VINCULO\_INVALIDO"\], retorna Invalido
        
-   **OU** endpoint = %/enrollments/v_x_/consents%
    
    -   Se o errorCodes for nulo, retorna Nulo
        
    -   Se o errorCodes for vazio, retorna Vazio
        
    -   Se o errorCodes possui mais de um item, retorna Multiplos itens
        
    -   Se statusCode = 422 e errorCodes não for \["COMBINACAO\_PERMISSOES\_INCORRETA"\], \["CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO"\], \["DATA\_EXPIRACAO\_INVALIDA"\], \["DEPENDE\_MULTIPLA\_ALCADA"\], \["ERRO\_IDEMPOTENCIA"\], \["ERRO\_NAO\_MAPEADO"\], \["ESTADO\_CONSENTIMENTO\_INVALIDO"\], \["FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA"\], \["INFORMACOES\_PJ\_NAO\_INFORMADAS"\], \["ORIGEM\_FIDO\_INVALIDA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSAO\_PF\_PJ\_EM\_CONJUNTO"\], \["PERMISSOES\_PJ\_INCORRETAS"\], \["RISCO"\], \["SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES"\], \["STATUS\_CONSENTIMENTO\_INVALIDO"\] ou \["STATUS\_VINCULO\_INVALIDO"\], retorna Invalido
        

journeyIsLinked

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x/_enrollments ou %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = POST ou GET
    

**ENTÃO**

-   Se journeyIsLinked for nulo, retorna Nulo
    
-   Se journeyIsLinked for vazio, retorna Vazio
    
-   Se journeyIsLinked não for TRUE ou FALSE, retorna Invalido
    

journeyLinkId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x/_enrollments ou %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = POST ou GET
    
-   **E** journeyIsLinked = TRUE
    

**ENTÃO**

-   Se journeyLinkId for nulo, retorna Nulo
    
-   Se journeyLinkId for vazio, retorna Vazio
    

nfcPayment

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/consents/{consentId}/authorise
    
-   **E** método = POST
    

**ENTÃO**

-   Se nfcPayment for nulo, retorna Nulo
    
-   Se nfcPayment for vazio, retorna Vazio
    
-   Se nfcPayment não for TRUE ou FALSE, retorna Invalido
    

personType

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/enrollments ou %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = POST ou GET
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se personType for nulo, retorna Nulo
    
-   Se personType for vazio, retorna Vazio
    
-   Se personType não for PF, PJ, PESSOA\_JURIDICA ou PESSOA\_NATURAL, retorna Invalido
    

platform

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options ou %/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options
    
-   **E** método = POST
    

**ENTÃO**

-   Se platform for nulo, retorna Nulo
    
-   Se platform for vazio, retorna Vazio
    
-   Se platform não for ANDROID, BROWSER, CROSS\_PLATFORM ou IOS, retorna Invalido
    

recurringConsentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_%_/enrollments/{enrollmentId}/fido-sign-options ou %/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise
    
-   **E** não é método = POST com statusCode 4xx ou 5xx
    

**ENTÃO**

-   Se for o endpoint /open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options consentId e o recurringConsentId estiverem simultaneamente preenchidos, retorna Invalido - nao podem ser preenchidos simultaneamente consentId e recurringConsentId
    
-   Se for o endpoint /open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options consentId e o recurringConsentId estiverem simultaneamente vazios ou nulos, retorna Pelo menos consentId ou recurringConsentId deve estar preenchido
    
-   Se o REGEX do recurringConsentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*''%/?#\]+, retorna Invalido
    

rejectionReasonCode

**SE**

-   Role = CLIENT
    
-   **E** status = REJECTED
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = PATCH ou GET
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se rejectionReasonCode for nulo, retorna Nulo
    
-   Se rejectionReasonCode for vazio, retorna Vazio
    
-   Se rejectionReasonCode não for REJEITADO\_DISPOSITIVO\_INCOMPATIVEL, REJEITADO\_FALHA\_FIDO, REJEITADO\_FALHA\_HYBRID\_FLOW, REJEITADO\_FALHA\_INFRAESTRUTURA, REJEITADO\_MANUALMENTE, REJEITADO\_MAXIMO\_CHALLENGES\_ATINGIDO, REJEITADO\_OUTRO, REJEITADO\_SEGURANCA\_INTERNA, REJEITADO\_TEMPO\_EXPIRADO\_ACCOUNT\_HOLDER\_VALIDATION, REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS, REJEITADO\_TEMPO\_EXPIRADO\_ENROLLMENT ou REJEITADO\_TITULARIDADE\_DIVERGENTE, retorna Invalido
    

revocationReasonCode

**SE**

-   Role = CLIENT
    
-   **E** status = REVOKED
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = PATCH  
    **OU** GET e statusCode = 200
    

**ENTÃO**

-   Se revocationReasonCode for nulo, retorna Nulo
    
-   Se revocationReasonCode for vazio, retorna Vazio
    
-   Se revocationReasonCode não for REVOGADO\_FALHA\_INFRAESTRUTURA, REVOGADO\_MANUALMENTE, REVOGADO\_OUTRO, REVOGADO\_SEGURANCA\_INTERNA ou REVOGADO\_VALIDADE\_EXPIRADA, retorna Invalido
    

rp

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options ou %/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options
    
-   **E** método = POST
    

**ENTÃO**

-   Se rp or nulo, retorna Nulo
    
-   Se rp for vazio, retorna Vazio
    

status

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/enrollments ou %/enrollments/v_x_/enrollments/{enrollmentId}
    
-   **E** método = POST ou GET
    
-   **E** statusCode = 2xx
    

**ENTÃO**

-   Se status for nulo, retorna Nulo
    
-   Se status for vazio, retorna Vazio
    
-   Se status não for AUTHORISED, REJECTED, REVOKED, AWAITING\_RISK\_SIGNALS, AWAITING\_ACCOUNT\_HOLDER\_VALIDATION ou AWAITING\_ENROLLMENT, retorna Invalido
    

tokenId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/enrollments/v_x_/enrollments%, %/enrollments/v_x_/consents/{consentId}/authorise, %/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se tokenId for nulo, retorna Nulo
    
-   Se tokenId for vazio, retorna Vazio
