# Changelog - [SV] Vínculo de dispositivo - v2.2.0-rc.2 - v2.1.0

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "version"

Alteração

2.1.0

2.2.0-rc.2

/tags

Alterado - "length"

Alteração

2

3

/tags

Adicionado - "2"

Adição

paths

Adicionado - "/recurring-consents/{recurringConsentId}/authorise"

Adição

## POST /enrollments

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Adicionado - "journey"

Adição

post/requestBody/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/permissions/items

Alterado - "description"

Alteração

Permissões atribuídas ao vínculo de conta:

-   PAYMENTS\_INITIATE: Iniciação de pagamentos sem redirecionamento à detentora.
    

Permissões atribuídas ao vínculo de conta:

-   PAYMENTS\_INITIATE: Permite a utilização do vinculo para iniciação de pagamentos sem redirecionamento nas famílias de API “payments-consents” e “payments-pix”.
    
-   RECURRING\_PAYMENTS\_INITIATE: Permite a utilização do vinculo para iniciação de Pix Automático sem redirecionamento nas famílias de API "payments-recurring-consents-automatic" e "payments-pix-recurring-payments-automatic".
    

post/requestBody/data/permissions/items/enum

Adicionado - "RECURRING\_PAYMENTS\_INITIATE"

Adição

enum

post/responses/201/data/properties

Adicionado - "journey"

Adição

post/responses/201/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/responses/201/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/permissions/items

Alterado - "description"

Alteração

Permissões atribuídas ao vínculo de conta:

-   PAYMENTS\_INITIATE: Iniciação de pagamentos sem redirecionamento à detentora.
    

Permissões atribuídas ao vínculo de conta:

-   PAYMENTS\_INITIATE: Permite a utilização do vinculo para iniciação de pagamentos sem redirecionamento nas famílias de API “payments-consents” e “payments-pix”.
    
-   RECURRING\_PAYMENTS\_INITIATE: Permite a utilização do vinculo para iniciação de Pix Automático sem redirecionamento nas famílias de API "payments-recurring-consents-automatic" e "payments-pix-recurring-payments-automatic".
    

post/responses/201/data/permissions/items/enum

Adicionado - "RECURRING\_PAYMENTS\_INITIATE"

Adição

enum

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## GET /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Adicionado - "journey"

Adição

get/responses/200/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/cancellation/reason/oneOf/0/rejectionReason

Alterado - "description"

Alteração

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis:

-   REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS: Expiração automática devido a timeout no status "AWAITING\_RISK\_SIGNALS". O envio de sinais de risco não foi concluído.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ACCOUNT\_HOLDER\_VALIDATION: Expiração automática devido a timeout no status "AWAITING\_ACCOUNT\_HOLDER\_VALIDATION". O processo de redirecionamento não foi concluído com sucesso.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ENROLLMENT: Expiração automática devido a timeout no status "AWAITING\_ENROLLMENT". O processo de criação e envio de credenciais FIDO2 não foi concluído com sucesso.
    

-   REJEITADO\_MAXIMO\_CHALLENGES\_ATINGIDO: Vínculo de conta rejeitado devido várias tentativas vínculo frustradas.
    

-   REJEITADO\_MANUALMENTE: Cancelamento manual, explicitamente a pedido do usuário.
    

-   REJEITADO\_DISPOSITIVO\_INCOMPATIVEL: Dispositivo não suporta o protocolo FIDO.
    

-   REJEITADO\_FALHA\_INFRAESTRUTURA: Falha na infraestrutura na detentora.
    

-   REJEITADO\_SEGURANCA\_INTERNA: Vínculo de conta rejeitado devido à política de segurança de instituição detentora ou iniciadora considerando a análise dos sinais de risco.
    

-   REJEITADO\_FALHA\_HYBRID\_FLOW: Vínculo de conta rejeitado por falha técnica no processo de redirecionamento (por exemplo: troca de authorization code por access token no FAPI Hybrid flow)
    

-   REJEITADO\_FALHA\_FIDO: Vínculo de conta rejeitado por falha técnica no processo de validação ou associação da credencial pública FIDO.
    

-   REJEITADO\_OUTRO: Outros motivos não descritos pelas demais. Indicar, neste caso, o motivo em "additionalInformation".
    

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis:

-   REJEITADO\_TITULARIDADE\_DIVERGENTE: A titularidade do usuário logado na detentora é incompatível com a informada na criação do enrollment
    

-   REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS: Expiração automática devido a timeout no status "AWAITING\_RISK\_SIGNALS". O envio de sinais de risco não foi concluído.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ACCOUNT\_HOLDER\_VALIDATION: Expiração automática devido a timeout no status "AWAITING\_ACCOUNT\_HOLDER\_VALIDATION". O processo de redirecionamento não foi concluído com sucesso.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ENROLLMENT: Expiração automática devido a timeout no status "AWAITING\_ENROLLMENT". O processo de criação e envio de credenciais FIDO2 não foi concluído com sucesso.
    

-   REJEITADO\_MAXIMO\_CHALLENGES\_ATINGIDO: Vínculo de conta rejeitado devido várias tentativas vínculo frustradas.
    

-   REJEITADO\_MANUALMENTE: Cancelamento manual, explicitamente a pedido do usuário.
    

-   REJEITADO\_DISPOSITIVO\_INCOMPATIVEL: Dispositivo não suporta o protocolo FIDO.
    

-   REJEITADO\_FALHA\_INFRAESTRUTURA: Falha na infraestrutura na detentora.
    

-   REJEITADO\_SEGURANCA\_INTERNA: Vínculo de conta rejeitado devido à política de segurança de instituição detentora ou iniciadora considerando a análise dos sinais de risco.
    

-   REJEITADO\_FALHA\_HYBRID\_FLOW: Vínculo de conta rejeitado por falha técnica no processo de redirecionamento (por exemplo: troca de authorization code por access token no FAPI Hybrid flow)
    

-   REJEITADO\_FALHA\_FIDO: Vínculo de conta rejeitado por falha técnica no processo de validação ou associação da credencial pública FIDO.
    

-   REJEITADO\_OUTRO: Outros motivos não descritos pelas demais. Indicar, neste caso, o motivo em "additionalInformation".
    

get/responses/200/data/cancellation/reason/oneOf/0/rejectionReason/enum

Adicionado - "REJEITADO\_TITULARIDADE\_DIVERGENTE"

Adição

enum

get/responses/200/data/debtorAccount/allOf/0/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/permissions/items

Alterado - "description"

Alteração

Permissões atribuídas ao vínculo de conta:

-   PAYMENTS\_INITIATE: Iniciação de pagamentos sem redirecionamento à detentora.
    

Permissões atribuídas ao vínculo de conta:

-   PAYMENTS\_INITIATE: Permite a utilização do vinculo para iniciação de pagamentos sem redirecionamento nas famílias de API “payments-consents” e “payments-pix”.
    
-   RECURRING\_PAYMENTS\_INITIATE: Permite a utilização do vinculo para iniciação de Pix Automático sem redirecionamento nas famílias de API "payments-recurring-consents-automatic" e "payments-pix-recurring-payments-automatic".
    

get/responses/200/data/permissions/items/enum

Adicionado - "RECURRING\_PAYMENTS\_INITIATE"

Adição

enum

get/responses/500

Adicionado - "headers"

Adição

get/responses/529

Adicionado - "headers"

Adição

## PATCH /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/cancellation/reason/oneOf/0/rejectionReason

Alterado - "description"

Alteração

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis:

-   REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS: Expiração automática devido a timeout no status "AWAITING\_RISK\_SIGNALS". O envio de sinais de risco não foi concluído.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ACCOUNT\_HOLDER\_VALIDATION: Expiração automática devido a timeout no status "AWAITING\_ACCOUNT\_HOLDER\_VALIDATION". O processo de redirecionamento não foi concluído com sucesso.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ENROLLMENT: Expiração automática devido a timeout no status "AWAITING\_ENROLLMENT". O processo de criação e envio de credenciais FIDO2 não foi concluído com sucesso.
    

-   REJEITADO\_MAXIMO\_CHALLENGES\_ATINGIDO: Vínculo de conta rejeitado devido várias tentativas vínculo frustradas.
    

-   REJEITADO\_MANUALMENTE: Cancelamento manual, explicitamente a pedido do usuário.
    

-   REJEITADO\_DISPOSITIVO\_INCOMPATIVEL: Dispositivo não suporta o protocolo FIDO.
    

-   REJEITADO\_FALHA\_INFRAESTRUTURA: Falha na infraestrutura na detentora.
    

-   REJEITADO\_SEGURANCA\_INTERNA: Vínculo de conta rejeitado devido à política de segurança de instituição detentora ou iniciadora considerando a análise dos sinais de risco.
    

-   REJEITADO\_FALHA\_HYBRID\_FLOW: Vínculo de conta rejeitado por falha técnica no processo de redirecionamento (por exemplo: troca de authorization code por access token no FAPI Hybrid flow)
    

-   REJEITADO\_FALHA\_FIDO: Vínculo de conta rejeitado por falha técnica no processo de validação ou associação da credencial pública FIDO.
    

-   REJEITADO\_OUTRO: Outros motivos não descritos pelas demais. Indicar, neste caso, o motivo em "additionalInformation".
    

Indica o motivo do cancelamento do vínculo de conta. Valores possíveis:

-   REJEITADO\_TITULARIDADE\_DIVERGENTE: A titularidade do usuário logado na detentora é incompatível com a informada na criação do enrollment
    

-   REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS: Expiração automática devido a timeout no status "AWAITING\_RISK\_SIGNALS". O envio de sinais de risco não foi concluído.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ACCOUNT\_HOLDER\_VALIDATION: Expiração automática devido a timeout no status "AWAITING\_ACCOUNT\_HOLDER\_VALIDATION". O processo de redirecionamento não foi concluído com sucesso.
    

-   REJEITADO\_TEMPO\_EXPIRADO\_ENROLLMENT: Expiração automática devido a timeout no status "AWAITING\_ENROLLMENT". O processo de criação e envio de credenciais FIDO2 não foi concluído com sucesso.
    

-   REJEITADO\_MAXIMO\_CHALLENGES\_ATINGIDO: Vínculo de conta rejeitado devido várias tentativas vínculo frustradas.
    

-   REJEITADO\_MANUALMENTE: Cancelamento manual, explicitamente a pedido do usuário.
    

-   REJEITADO\_DISPOSITIVO\_INCOMPATIVEL: Dispositivo não suporta o protocolo FIDO.
    

-   REJEITADO\_FALHA\_INFRAESTRUTURA: Falha na infraestrutura na detentora.
    

-   REJEITADO\_SEGURANCA\_INTERNA: Vínculo de conta rejeitado devido à política de segurança de instituição detentora ou iniciadora considerando a análise dos sinais de risco.
    

-   REJEITADO\_FALHA\_HYBRID\_FLOW: Vínculo de conta rejeitado por falha técnica no processo de redirecionamento (por exemplo: troca de authorization code por access token no FAPI Hybrid flow)
    

-   REJEITADO\_FALHA\_FIDO: Vínculo de conta rejeitado por falha técnica no processo de validação ou associação da credencial pública FIDO.
    

-   REJEITADO\_OUTRO: Outros motivos não descritos pelas demais. Indicar, neste caso, o motivo em "additionalInformation".
    

patch/requestBody/data/cancellation/reason/oneOf/0/rejectionReason/enum

Adicionado - "REJEITADO\_TITULARIDADE\_DIVERGENTE"

Adição

enum

patch/responses/500

Adicionado - "headers"

Adição

patch/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/fido-registration-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/422/errors/items/code/enum

Adicionado - "MAXIMO\_CHALLENGES\_ATINGIDO"

Adição

enum

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/fido-registration

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/risk-signals

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post

Alterado - "description"

Alteração

Envio de sinais de risco para iniciação do vínculo de dispositivo, o status do enrollment deve estar em \`AWAITING\_RISK\_SIGNALS\`. Após recebimento com sucesso dos sinais, o status do enrollment deve transitar para \`AWAITING\_ACCOUNT\_HOLDER\_VALIDATION\`.

Envio de sinais de risco para iniciação do vínculo de dispositivo, o status do enrollment deve estar em \`\`\`AWAITING\_RISK\_SIGNALS\`\`\`. Após recebimento com sucesso dos sinais, o status do enrollment deve transitar para \`\`\`AWAITING\_ACCOUNT\_HOLDER\_VALIDATION\`\`\`.  
Em casos de falha nesse método (HTTP Status 422), o vínculo deve transitar para \`\`\`REJECTED\`\`\` sincronamente.  
Em caso de sucesso no recebimento, a instituição detentora, a seu critério e após análise das informações fornecidas, pode rejeitar esse vínculo por validações internas de segurança.

post/requestBody/data/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

Utiliza-se a propriedade do sistema que identifica a combinação de usuário logado, chave de assinatura do aplicativo e dispositivo.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).

ID único do dispositivo gerado pela plataforma.  
A geração deve utilizar-se da propriedade do sistema que identifica a combinação de usuário logado, chave de assinatura do aplicativo e dispositivo ou de algoritmos heurísticos capazes de criar um identificador único para o dispositivo.  
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).  
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /enrollments/{enrollmentId}/fido-sign-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data

Removido - "required"

Remoção

post/requestBody/data

Removido - "properties"

Remoção

post/requestBody/data

Adicionado - "oneOf"

Adição

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite assinatura.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O status do consentimento não permite autorização.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Códigos de erros previstos:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite assinatura.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O status do consentimento não permite autorização.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO: A permissão definida no vínculo não é válida para o tipo de consentimento informado
    

post/responses/422/errors/items/code/enum

Adicionado - "PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite assinatura.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O status do consentimento não permite autorização.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    

Descrição específica do erro de acordo com o código reportado:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite assinatura.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O status do consentimento não permite autorização.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    
-   PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO: A permissão definida no vínculo não é válida para o tipo de consentimento informado.
    

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   RP\_INVALIDA: Relying party inválida.
    
-   STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inválido.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: Status do consentimento de pagamento inválido.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Título específico do erro reportado, de acordo com o código enviado:

-   RP\_INVALIDA: Relying party inválida.
    
-   STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inválido.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: Status do consentimento de pagamento inválido.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO: A permissão definida no vínculo não é válida para o tipo de consentimento informado
    

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /consents/{consentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody

Alterado - "description"

Alteração

Payload para criação de vínculo de conta.

Payload para autorização de um consentimento através do dispositivo vinculado.

post/requestBody/data/riskSignals/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

Utiliza-se a propriedade do sistema que identifica a combinação de usuário logado, chave de assinatura do aplicativo e dispositivo.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).

ID único do dispositivo gerado pela plataforma.  
A geração deve utilizar-se da propriedade do sistema que identifica a combinação de usuário logado, chave de assinatura do aplicativo e dispositivo ou de algoritmos heurísticos capazes de criar um identificador único para o dispositivo.  
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).  
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos:

-   STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O consentimento de pagamentos não possui status AWAITING\_AUTHORISATION.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Os sinais obrigatórios para a plataforma do usuário não foram enviados em sua totalidade.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Códigos de erros previstos:

-   STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O consentimento de pagamentos não possui status AWAITING\_AUTHORISATION.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Os sinais obrigatórios para a plataforma do usuário não foram enviados em sua totalidade.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   ORIGEM\_FIDO\_INVALIDA: O valor contido no campo \`\`\`fidoAssertion.response.clientDataJSON.origin\`\`\` não pode ser verificado.
    

post/responses/422/errors/items/code/enum

Adicionado - "ORIGEM\_FIDO\_INVALIDA"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado:

-   STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O consentimento de pagamentos não possui status AWAITING\_AUTHORISATION.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Os sinais obrigatórios para a plataforma do usuário não foram enviados em sua totalidade.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    

Descrição específica do erro de acordo com o código reportado:

-   STATUS\_VINCULO\_INVALIDO: O vínculo de conta não possui status AUTHORISED.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: O consentimento de pagamentos não possui status AWAITING\_AUTHORISATION.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Os sinais obrigatórios para a plataforma do usuário não foram enviados em sua totalidade.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    
-   ORIGEM\_FIDO\_INVALIDA: O valor contido no campo \`\`\`fidoAssertion.response.clientDataJSON.origin\`\`\` não pode ser verificado.
    

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inválido.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: Status do consentimento inválido.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Falta de sinais obrigatórios para a plataforma do usuário.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Título específico do erro reportado, de acordo com o código enviado:

-   STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inválido.
    
-   STATUS\_CONSENTIMENTO\_INVALIDO: Status do consentimento inválido.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Falta de sinais obrigatórios para a plataforma do usuário.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   ORIGEM\_FIDO\_INVALIDA: "Origin" não pode ser verificada.
    

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

## POST /recurring-consents/{recurringConsentId}/authorise
