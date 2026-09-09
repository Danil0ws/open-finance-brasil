# Changelog - [SV] Pagamentos Automáticos - v2.2.0 - v2.2.0-rc.2

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix automático e Transferências Inteligentes) para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos endpoints dedicados ao consentimento nesta API.

\# Orientações

-   \`CONTA\`, referente às instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente às instituições iniciadoras de pagamento participantes do Open Finance Brasil….  
    

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix automático e Transferências Inteligentes) para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos endpoints dedicados ao consentimento nesta API.

\# Orientações

-   \`CONTA\`, referente às instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente às instituições iniciadoras de pagamento participantes do Open Finance Brasil….  
    

/info

Alterado - "version"

Alteração

2.2.0-rc.2

2.2.0

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/riskSignals/manual/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.    
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).    
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.    
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).    
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).    
\[Restrição\] Campo de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.  

post/requestBody/data/riskSignals/manual/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de “root”.    
\[Restrição\] Campo de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.  

post/requestBody/data/riskSignals/manual/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica o nível de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campo de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.  

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pelo fluxo que iniciou a solicitação.
    

  

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## PATCH /pix/recurring-payments/{recurringPaymentId}

### request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pelo fluxo que iniciou a solicitação.
    

  

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pelo fluxo que iniciou a solicitação.
    

  

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/oneOf/0/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.    
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).    
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.    
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).    
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).    
\[Restrição\] Campo de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.  

patch/requestBody/data/oneOf/0/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de “root”.    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de “root”.    
\[Restrição\] Campo de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.  

patch/requestBody/data/oneOf/0/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o nível de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

Indica o nível de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campo de envio obrigatório quando o usuário utilizar uma aplicação nativa para Android ou iOS.  

patch/requestBody/data/oneOf/2/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pelo fluxo que iniciou a solicitação.
    

  

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pelo fluxo que iniciou a solicitação.
