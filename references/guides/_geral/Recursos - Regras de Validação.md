# Recursos - Regras de Validação

v 1.04

**Objetivo desta página**

Demonstrar funcionalmente as regras de validação de qualidade de campos básicos e additionalInfos realizados na PCM. Estas validações são utilizadas para aberturas de tickets e monitoramento através do dashboard de Monitoramento Operacional.

**Guia de leitura**

1.  Nos endpoints, a referência “v_x_” deve ser substituída pela versão da API que está sendo enviada. Por exemplo, para a versão 4 (v4) dos endpoints de pagamento, enviar “open-banking/automatic-payments/**v**_**4**_/recurring-consents/{recurringConsentId}”.
    
2.  Nos endpoints, a referência % significa que vale para qualquer conteúdo antes ou depois, de acordo com o endpoint em questão. Por exemplo, “%/automatic-payments/v_x_/recurring-consents%” significa que vale para os endpoints “/open-banking/automatic-payments/v2/recurring-consents” e “/open-banking/automatic-payments/v2/recurring-consents/{recurringConsentId}”.
    

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Dados Cadastrais e Transacionais**

### Recursos

**Campo**

**Regra**

consentId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/resources/%
    
-   **E** método = GET
    

**ENTÃO**

-   Se o consentId for nulo, retorna Nulo
    
-   Se o consentId for vazio, retorna Vazio
    
-   Se o REGEX do consentId não for ^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*''%/?#\]+, retorna Invalido
    

statusSummary

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/resources/%
    
-   **E** método = GET
    
-   **E** statusCode - 200
    

**ENTÃO**

-   Se available, unavailable, temporary\_unavailable e pending\_authorisation forem nulos, retorna Nulo
    
-   Se available, unavailable, temporary\_unavailable e pending\_authorisation forem vazios, retorna Vazio
    

tokenId

**SE**

-   Role = CLIENT
    
-   **E** endpoint = %/resources/%
    
-   **E** statusCode não é 4xx ou 5xx
    

**ENTÃO**

-   Se o tokenId for nulo, retorna Nulo
    
-   Se o tokenId for vazio, retorna Vazio
