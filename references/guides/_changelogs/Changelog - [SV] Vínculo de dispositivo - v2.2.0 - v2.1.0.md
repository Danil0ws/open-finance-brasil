# Changelog - [SV] Vínculo de dispositivo - v2.2.0 - v2.1.0

## Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

Família de API para permitir o pagamento sem redirecionamento via Open Finance Brasil.   
Permite tanto o gerenciamento dos dispositivos vinculados as contas quanto a autorização de consentimentos criados via fluxo sem redirecionamento.

\## Validação de origin nos endpoints FIDO

Durante o cadastro do cliente (DCR/DCM), o software statement assertion possui um atributo nomeado software\_origin\_uris.  
Esse atributo armazena as origens permitidas para utilização do protocolo FIDO.  
Nas chamadas que possuem o argumento clientDataJSON (fido-registration e authorise), o atributo origin deve ser extraído do clientDataJSON e deve ser realizada a verificação se a origin do mesmo está contida no software\_origin\_uris informado no momento do DCR/DCM.  
Caso a instituição iniciadora altere ou inclua o valor do atributo software\_origin\_uris, será necessária realização de um novo processo de DCM com as detentoras  

Família de API para permitir o pagamento sem redirecionamento via Open Finance Brasil.   
Permite tanto o gerenciamento dos dispositivos vinculados as contas quanto a autorização de consentimentos criados via fluxo sem redirecionamento.

\## Validação de origin nos endpoints FIDO

Durante o cadastro do cliente (DCR/DCM), o software statement assertion possui um atributo nomeado software\_origin\_uris.  
Esse atributo armazena as origens permitidas para utilização do protocolo FIDO.  
Nas chamadas que possuem o argumento clientDataJSON (fido-registration e authorise), o atributo origin deve ser extraído do clientDataJSON e deve ser realizada a verificação se a origin do mesmo está contida no software\_origin\_uris informado no momento do DCR/DCM.

Caso a instituição iniciadora altere ou inclua o valor do atributo software\_origin\_uris, será necessária realização de um novo processo de DCM com as detentoras.

\## Sobre os limites do dispositivo vinculado no Pix Automático

Existem alguns limites que estão envolvidos durante o processo de autorização de um consentimento e o envio dos pagamentos, seja do inicial avulso ou das recorrências, para Pix Automático. Os limites envolvidos e o tratamento esperado pela instituição detentora são: 

-   Limite diário do vínculo: Deve ser considerado apenas durante o pagamento inicial avulso e não deve ser considerado para pagamentos que representem as recorrências de Pix Automático.
    
-   Limite por transação do vínculo: Deve ser considerado apenas durante o pagamento inicial avulso e não deve ser considerado para pagamentos que representem as recorrências de Pix Automático.  
    

Considerando que a falha no pagamento inicial avulso não implica em rejeite síncrono do consentimento de Pix Automático, problemas de limite e/ou saldo não devem impedir a criação ou autorização do consentimento.    
O valor mínimo definido pelo recebedor no âmbito do Pix Automático também não é alvo de validação durante a autorização do consentimento através desta API.    
Por fim, os limites do pagamento das recorrências a ser considerado são os definidos no consentimento de Pix Automático.  

/info

Alterado - "version"

Alteração

2.1.0

2.2.0

/tags

Alterado - "length"

Alteração

2

3

/tags

Adicionado - "Pix Automático"

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

post/responses

Adicionado - "504"

Adição

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

post/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

Adição

post/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

post/security/0

Removido - "OAuth2ClientCredentials"

Remoção

post/security/0

Adicionado - "OAuth2ClientCredentialsPayments"

Adição

## GET /enrollments/{enrollmentId}

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses

Adicionado - "504"

Adição

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

get/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

get/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

Adição

get/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

get/security/0

Removido - "OAuth2ClientCredentials"

Remoção

get/security/0

Adicionado - "OAuth2ClientCredentialsPayments"

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

patch/responses

Adicionado - "415"

Adição

patch/responses

Adicionado - "504"

Adição

patch/responses/500

Adicionado - "headers"

Adição

patch/responses/529

Adicionado - "headers"

Adição

patch/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

patch/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

Adição

patch/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

patch/security/0

Removido - "OAuth2ClientCredentials"

Remoção

patch/security/0

Adicionado - "OAuth2ClientCredentialsPayments"

Adição

## POST /enrollments/{enrollmentId}/fido-registration-options

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post

Alterado - "description"

Alteração

Método para obter os parâmetros para criação de uma nova credencial FIDO2. Um novo challenge deve ser criado a cada chamada.  
Os parâmetros da resposta devem ser compatíveis com a definição \[W3C\](https://www.w3.org/TR/webauthn-2/#dictionary-makecredentialoptions)  

Método para obter os parâmetros para criação de uma nova credencial FIDO2. Um novo challenge deve ser criado \*\*para cada enrollment, limitando a um challenge por enrollmentId\*\*. Os parâmetros da resposta devem ser compatíveis com a definição \[W3C\](https://www.w3.org/TR/webauthn-2/#dictionary-makecredentialoptions)  

post/responses

Adicionado - "504"

Adição

post/responses/201/data/excludeCredentials

Adicionado - "description"

Adição

Lista de IDs de credenciais já existentes para este usuário e autenticador. É utilizado para evitar a criação de múltiplas credenciais para o mesmo usuário em mesmo autenticador. Caso seja enviado, a iniciadora pode rejeitar o registro de uma das credenciais já existentes no dispositivo, ou seguir com a criação, substituindo ou não o vínculo já existente.  

post/responses/201/data/timeout

Alterado - "description"

Alteração

Timeout, em milissegundos, para registro da credencial FIDO2.

Representa, em milissegundos, o tempo de validade do challenge para registro da credencial FIDO2. O valor desse campo deverá ser 300000, representando 5 minutos. Esse valor foi definido com base na máquina de estados do vínculo e na documentação do protocolo da webAuthn.  

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova credencial.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

  

Códigos de erros previstos:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova credencial.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   MAXIMO\_CHALLENGES\_ATINGIDO: Parâmetros de assinatura FIDO já foram gerados para o enrollmentId especificado.
    

  

post/responses/422/errors/items/code/enum

Adicionado - "MAXIMO\_CHALLENGES\_ATINGIDO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova credencial.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    

  

Descrição específica do erro de acordo com o código reportado:

-   RP\_INVALIDA: O identificador da Relying Party informado não pode ser verificado.
    
-   STATUS\_VINCULO\_INVALIDO: O status do vínculo de conta é tal que não permite o registro de nova credencial.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    
-   MAXIMO\_CHALLENGES\_ATINGIDO: Parâmetros de assinatura FIDO já foram gerados para o enrollmentId especificado.
    

  

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   RP\_INVALIDA: Relying party inválida.
    
-   STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inválido.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

  

Título específico do erro reportado, de acordo com o código enviado:

-   RP\_INVALIDA: Relying party inválida.
    
-   STATUS\_VINCULO\_INVALIDO: Status do vínculo de conta inválido.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   MAXIMO\_CHALLENGES\_ATINGIDO: Parâmetros de assinatura FIDO já foram gerados para o enrollmentId especificado.
    

  

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

post/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2AuthorizationCodeRecurringPayments`"

Adição

post/security

Adicionado - "`OAuth2AuthorizationCodePaymentsAndRecurring`"

Adição

post/security/0

Removido - "OAuth2AuthorizationCode"

Removido - "OAuth2AuthorizationCode"

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adicionado - "OAuth2AuthorizationCodePayments"

## POST /enrollments/{enrollmentId}/fido-registration

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Adicionado - "504"

Adição

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

post/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2AuthorizationCodeRecurringPayments`"

Adição

post/security

Adicionado - "`OAuth2AuthorizationCodePaymentsAndRecurring`"

Adição

post/security/0

Removido - "OAuth2AuthorizationCode"

Removido - "OAuth2AuthorizationCode"

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adicionado - "OAuth2AuthorizationCodePayments"

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

post/requestBody/data

Alterado - "description"

Alteração

Informa a integridade do dispositivo e app

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.   
Em casos de autenticação cross-platform, deve ser considerado o dispositivo utilizado para acesso ao canal da instituição, não o autenticador externo utilizado para assinatura.    
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.   

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

post/requestBody/data/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.   

post/requestBody/data/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de “root”.

\[Restrição\] Campos de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.   

post/requestBody/data/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo.

\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).

\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica o nível de brilho da tela do dispositivo.

\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).

\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).

 \[Restrição\] Campos de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.   

post/responses

Adicionado - "504"

Adição

post/responses/500

Adicionado - "headers"

Adição

post/responses/529

Adicionado - "headers"

Adição

post/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

Adição

post/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

post/security/0

Removido - "OAuth2ClientCredentials"

Remoção

post/security/0

Adicionado - "OAuth2ClientCredentialsPayments"

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

post/responses

Adicionado - "504"

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

post/security

Alterado - Quantidade de fluxos de geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2AuthorizationCodeRecurringPayments`"

Adição

post/security

Adicionado - "`OAuth2AuthorizationCodePaymentsAndRecurring`"

Adição

post/security/0

Removido - "OAuth2AuthorizationCode"

Removido - "OAuth2AuthorizationCode"

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adicionado - "OAuth2AuthorizationCodePayments"

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

post/requestBody/data/riskSignals

Alterado - "description"

Alteração

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.  
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.  

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.   
Em casos de autenticação cross-platform, deve ser considerado o dispositivo utilizado para acesso ao canal da instituição, não o autenticador externo utilizado para assinatura.    
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.   

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

post/requestBody/data/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.   

post/requestBody/data/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de “root”.

\[Restrição\] Campos de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.   

post/requestBody/data/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo.

\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).

\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica o nível de brilho da tela do dispositivo.

\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).

\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).

\[Restrição\] Campos de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.   

post/responses

Adicionado - "504"

Adição

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

post/security

Alterado - Quantidade de fluxos para geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2AuthorizationCodeRecurringPayments`"

Adição

post/security

Adicionado - "`OAuth2AuthorizationCodePaymentsAndRecurring`"

Adição

post/security/0

Removido - "OAuth2AuthorizationCode"

Removido - "OAuth2AuthorizationCode"

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adicionado - "OAuth2AuthorizationCodePayments"

## POST /recurring-consents/{recurringConsentId}/authorise
