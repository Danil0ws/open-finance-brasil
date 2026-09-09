# Changelog - [DC] Consentimento - v3.4.0-rc.1 - v3.3.1

none

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/loggedUser/properties

Adicionado - "name"

Adição

## GET /consents/{consentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Define o código da razão pela qual o consentimento foi rejeitado.

-   CONSENT\_EXPIRED – consentimento que ultrapassou o tempo limite para autorização.
    
-   CUSTOMER\_MANUALLY\_REJECTED – cliente efetuou a rejeição do consentimento manualmente através de interação nas instituições participantes.
    
-   CUSTOMER\_MANUALLY\_REVOKED – cliente efetuou a revogação após a autorização do consentimento.
    
-   CONSENT\_MAX\_DATE\_REACHED – consentimento que ultrapassou o tempo limite de compartilhamento.
    
-   CONSENT\_TECHNICAL\_ISSUE – consentimento que foi rejeitado devido a um problema técnico que impossibilita seu uso pela instituição receptora, por exemplo: falha associada a troca do AuthCode pelo AccessToken, durante o processo de Hybrid Flow.
    
-   INTERNAL\_SECURITY\_REASON – consentimento que foi rejeitado devido as políticas de segurança aplicada pela instituição transmissora.
    

Define o código da razão pela qual o consentimento foi rejeitado.

-   CONSENT\_EXPIRED – consentimento que ultrapassou o tempo limite para autorização.
    
-   CUSTOMER\_MANUALLY\_REJECTED – cliente efetuou a rejeição do consentimento manualmente através de interação nas instituições participantes.
    
-   CUSTOMER\_MANUALLY\_REVOKED – cliente efetuou a revogação após a autorização do consentimento.
    
-   CONSENT\_MAX\_DATE\_REACHED – consentimento que ultrapassou o tempo limite de compartilhamento.
    
-   CONSENT\_TECHNICAL\_ISSUE – consentimento que foi rejeitado devido a um problema técnico que impossibilita seu uso pela instituição receptora, por exemplo: falha associada a troca do AuthCode pelo AccessToken, durante o processo de Hybrid Flow.
    
-   INTERNAL\_SECURITY\_REASON – consentimento que foi rejeitado devido as políticas de segurança aplicada pela instituição transmissora.
    
-   CONSENT\_MISSING\_INFORMATION - rejeição por falta do nome do usuário PJ no CIBA.
    

get/responses/200/data/rejection/reason/code/enum

Adicionado - "CONSENT\_MISSING\_INFORMATION"

Adição
