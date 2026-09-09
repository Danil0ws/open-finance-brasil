# Changelog - [SV] Vínculo de dispositivo - v2.2.0 - v2.2.0-rc.3

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

post/responses

Adicionado - "504"

Adição

post/security

Alterado - Quantidade de fluxos para geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

post/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

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

get/security

Alterado - Quantidade de fluxos para geração de credencial

Alteração

1

3

get/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

get/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

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

patch/responses

Adicionado - "415"

Adição

patch/responses

Adicionado - "504"

Adição

patch/security

Alterado - Quantidade de fluxos para geração de credencial

Alteração

1

3

patch/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

patch/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

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

post/responses

Adicionado - "504"

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

Remoção

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adição

## POST /enrollments/{enrollmentId}/fido-registration

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses

Adicionado - "504"

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

Remoção

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adição

## POST /enrollments/{enrollmentId}/risk-signals

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data

Alterado - "description"

Alteração

Informa a integridade do dispositivo e app

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.   
Em casos de autenticação cross-platform, deve ser considerado o dispositivo utilizado para acesso ao canal da instituição, não o autenticador externo utilizado para assinatura.    
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.   

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

post/security

Alterado - "length"

Alteração

1

3

post/security

Adicionado - "1"

Adição

post/security

Adicionado - "2"

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

post/responses

Adicionado - "504"

Adição

post/security

Alterado - Quantidade de fluxos para geração de credencial

Alteração

1

3

post/security

Adicionado - "`OAuth2ClientCredentialsPaymentsAndRecurring`"

Adição

post/security

Adicionado - "`OAuth2ClientCredentialsRecurringPayments`"

Adição

post/security/0

Removido - "OAuth2ClientCredentials"

Remoção

post/security/0

Adicionado - "OAuth2ClientCredentialsPayments"

Adição

## POST /consents/{consentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/riskSignals

Alterado - "description"

Alteração

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.  
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.  

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.   
Em casos de autenticação cross-platform, deve ser considerado o dispositivo utilizado para acesso ao canal da instituição, não o autenticador externo utilizado para assinatura.    
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.   

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

Remoção

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adição

## POST /recurring-consents/{recurringConsentId}/authorise

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/riskSignals

Alterado - "description"

Alteração

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.  
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.  

Conjunto de sinais extraídos do dispositivo do usuário para ativação do consentimento de pagamento.   
Em casos de autenticação cross-platform, deve ser considerado o dispositivo utilizado para acesso ao canal da instituição, não o autenticador externo utilizado para assinatura.    
A obrigatoriedade das informações variam de acordo com a plataforma utilizada.   

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

Adicionado - "415"

Adição

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
    
-   ORIGEM\_FIDO\_INVALIDA: O valor contido no campo \`\`\`fidoAssertion.response.clientDataJSON.origin\`\`\` não pode ser verificado.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.                 
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Os sinais obrigatórios para a plataforma do usuário não foram enviados em sua totalidade.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

  

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
    
-   ORIGEM\_FIDO\_INVALIDA: O valor contido no campo \[response.clientDataJSON.origin\](https://www.w3.org/TR/webauthn-2/#dom-authenticatorresponse-clientdatajson) não pode ser verificado.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Os sinais obrigatórios para a plataforma do usuário não foram enviados em sua totalidade.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro \[nome\_campo\] obrigatório não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro \[nome\_campo\] não obedece as regras de formatação esperadas.
    
-   ERRO\_IDEMPOTENCIA: Conteúdo da mensagem (claim data) diverge do conteúdo associado a esta chave de idempotência (x-idempotency-key).
    

  

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
    
-   ORIGEM\_FIDO\_INVALIDA: "Origin" não pode ser verificada.
    
-   RISCO: Validação síncrona dos sinais de risco impediram a ativação do consentimento.
    
-   FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA: Falta de sinais obrigatórios para a plataforma do usuário.
    
-   CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO: A conta de débito informada pelo iniciador não condiz com a conta de débito vinculada ao dispositivo.
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

  

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

Remoção

post/security/0

Adicionado - "OAuth2AuthorizationCodePayments"

Adição
