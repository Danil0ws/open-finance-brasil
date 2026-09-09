# Changelog - [SV] Pagamentos Automáticos - v2.2.0-rc.2 - v2.2.0-rc.1

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

-   \`CONTA\`, referente ás instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente ás instituições iniciadoras de pagamento participantes do Open Finance Brasil….  
    

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix automático e Transferências Inteligentes) para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos endpoints dedicados ao consentimento nesta API.

\# Orientações

-   \`CONTA\`, referente ás instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente ás instituições iniciadoras de pagamento participantes do Open Finance Brasil…  
    

/info

Alterado - "version"

Alteração

2.2.0-rc.1

2.2.0-rc.2

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/paymentReference

Alterado - "example"

Alteração

23-07-2025/P1W

R/2025-09-23/P1M

get/responses/200/data/items/paymentReference

Removido - "minLength"

Remoção

4

get/responses/200/data/items/paymentReference

Removido - "maxLength"

Remoção

14

get/responses/200/data/items/paymentReference

Removido - "pattern"

Remoção

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

get/responses/200/data/items/paymentReference

Alterado - "description"

Alteração

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO. 

-   O preenchimento deve seguir a seguinte lógica: 
    
-   Primeiro Pagamento: Caso se trate do pagamento inicial avulso, especificado no campo "/data/firstPayment", o valor deste campo deve ser preenchido com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes realizados após o pagamento inicial, o campo paymentReference deve ser preenchido com uma string de Intervalo ISO 8601 no formato \`\`\`<start>/<duration>\`\`\`, que representa o ciclo exato ao qual o pagamento se refere. 
    
-   O componente \`\`\`<start>\`\`\` deve indicar a data de iní­cio do ciclo especí­fico ao qual o pagamento enviado se refere. 
    
-   O componente \`\`\`<duration>\`\`\` deve corresponder ao código da periodicidade do consentimento (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual) 
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1W
    
-   Segundo ciclo: 30-07-2025/P1W
    
-   Terceiro ciclo: 06-07-2025/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1M
    
-   Segundo ciclo: 23-08-2025/P1M
    
-   Terceiro ciclo: 23-09-2025/P1M
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de iní­cio do ciclo especí­fico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

get/responses/200/data/items/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informaçíµes complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação
    
-   CONSENTIMENTO\_REVOGADO
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informaçíµes complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

get/responses/200/data/items/rejectionReason/code/enum

Removido - "CONSENTIMENTO\_REVOGADO"

Remoção

enum

get/responses/200/data/items/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transaçíµes pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informaçíµes ou recursos;
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   CONSENTIMENTO\_REVOGADO: O pagamento estava associado a um consentimento que foi revogado.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transaçíµes pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informaçíµes ou recursos;
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO "“ A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO "“ A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio
    

  

## POST /pix/recurring-payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido - "originalRecurringPaymentId"

Remoção

post/requestBody/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReferente" diferente de "zero"), apenas o método AUTO é permitido, ou;  
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReferente" igual a "zero"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto "sweeping" selecionado no "oneOf" do campo "/data/recurringConfiguration/"), apenas os métodos MANU, DICT e INIC são permitidos.  

post/requestBody/data/paymentReference

Alterado - "example"

Alteração

23-07-2025/P1W

R/2025-09-23/P1M

post/requestBody/data/paymentReference

Removido - "minLength"

Remoção

4

post/requestBody/data/paymentReference

Removido - "maxLength"

Remoção

14

post/requestBody/data/paymentReference

Removido - "pattern"

Remoção

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

post/requestBody/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO. 

-   O preenchimento deve seguir a seguinte lógica: 
    
-   Primeiro Pagamento: Caso se trate do pagamento inicial avulso, especificado no campo "/data/firstPayment", o valor deste campo deve ser preenchido com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes realizados após o pagamento inicial, o campo paymentReference deve ser preenchido com uma string de Intervalo ISO 8601 no formato \`\`\`<start>/<duration>\`\`\`, que representa o ciclo exato ao qual o pagamento se refere. 
    
-   O componente \`\`\`<start>\`\`\` deve indicar a data de iní­cio do ciclo especí­fico ao qual o pagamento enviado se refere. 
    
-   O componente \`\`\`<duration>\`\`\` deve corresponder ao código da periodicidade do consentimento (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual) 
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1W
    
-   Segundo ciclo: 30-07-2025/P1W
    
-   Terceiro ciclo: 06-07-2025/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1M
    
-   Segundo ciclo: 23-08-2025/P1M
    
-   Terceiro ciclo: 23-09-2025/P1M
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de iní­cio do ciclo especí­fico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

post/requestBody/data/riskSignals/manual/properties

Removido - "isCallingProgress"

Remoção

post/requestBody/data/riskSignals/manual/properties

Adicionado - "isCallInProgress"

Adição

post/requestBody/data/riskSignals/manual/accountTenure

Adicionado - "example"

Adição

21/05/2020

post/requestBody/data/riskSignals/manual/antennaInformation

Adicionado - "example"

Adição

CellIdentityLte:{mCi=2\*\*\*\*\*\*60 mPci=274 mTac=5\*\*\*1 mEarfcn=9510 mBands=\[28\] mBandwidth=2147483647 mMcc=724 mMnc=10 mAlphaLong=VIVO mAlphaShort=VIVO mAdditionalPlmns={} mCsgInfo=null}  

post/requestBody/data/riskSignals/manual/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

ID único do dispositivo gerado pela plataforma.  Utiliza-se a propriedade do sistema que identifica a combinação de usuário logado, chave de assinatura do aplicativo e dispositivo.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).  

post/requestBody/data/riskSignals/manual/deviceId

Alterado - "example"

Alteração

00000000-54b3-e7c7-0000-000046bffd97

00aa11bb22cc33dd

post/requestBody/data/riskSignals/manual/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante o pagamento for Android ou iOS.  

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.    
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).    
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

post/requestBody/data/riskSignals/manual/elapsedTimeSinceBoot

Adicionado - "example"

Adição

6356027

post/requestBody/data/riskSignals/manual/geolocation

Alterado - "description"

Alteração

Dados de geolocalização do cliente enquanto logado na iniciadora

Localização do usuário, obtida com seu consentimento.  
\[Android\] Informação obtida através do \[link\](https://developers.google.com/android/reference/com/google/android/gms/location/FusedLocationProviderClient#public-abstract-tasklocation-getlastlocation) considerando as permissões necessárias.   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/corelocation/).   
\[Restrição\] A ITP deve solicitar ao usuário a permissão para compartilhamento de sua localização. Este campo poderá ser omitido caso o GPS esteja indisponí­vel, isto é, sem sinal, ou em dispositivos sem o hardware necessário; ou caso o usuário negue o consentimento.  

post/requestBody/data/riskSignals/manual/geolocation/latitude

Adicionado - "example"

Adição

\-15.738.602

post/requestBody/data/riskSignals/manual/geolocation/longitude

Adicionado - "example"

Adição

\-47.926.498

post/requestBody/data/riskSignals/manual/geolocation/type

Adicionado - "example"

Adição

FINE

post/requestBody/data/riskSignals/manual/integrity

Alterado - "description"

Alteração

Informa a integridade do dispositivo e app.   
No Android, conforme documentação Play API Integrity - \[Android\](https://developer.android.com/google/play/integrity/overview?hl=pt-br).   
No iOS, conforme documentação App Attest \[iOS\](https://developer.apple.com/documentation/devicecheck/establishing\_your\_app\_s\_integrity)  

Informa a integridade do dispositivo e app.   
\[Android\] Conforme documentação Play API Integrity, \[link\](https://developer.android.com/google/play/integrity/overview?hl=pt-br).   
\[iOS\] Conforme documentação App Attest, \[link\](https://developer.apple.com/documentation/devicecheck/establishing\_your\_app\_s\_integrity).  

post/requestBody/data/riskSignals/manual/integrity/appRecognitionVerdict

Adicionado - "example"

Adição

PLAY\_RECOGNIZED

post/requestBody/data/riskSignals/manual/integrity/deviceRecognitionVerdict

Adicionado - "example"

Adição

\[\\"MEETS\_DEVICE\_INTEGRITY\\"\]

post/requestBody/data/riskSignals/manual/isCharging

Alterado - "description"

Alteração

Indica se a bateria do dispositivo está sendo carregada.

Indica se a bateria do dispositivo está sendo carregada.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/BatteryManager).   
\[iOS\] Informações obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620045-batterymonitoringenabled/).  

post/requestBody/data/riskSignals/manual/isCharging

Adicionado - "example"

Adição

true

post/requestBody/data/riskSignals/manual/isDevModeEnabled

Adicionado - "example"

Adição

post/requestBody/data/riskSignals/manual/isEmulated

Adicionado - "example"

Adição

post/requestBody/data/riskSignals/manual/isMockGPS

Alterado - "description"

Alteração

Indica se o dispositivo está usando um GPS falso.

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo \`COARSE\` ou \`FINE\`.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/location/Location.html#isMock()) ou, para versões anteriores í  12, \[link\](https://developer.android.com/reference/android/location/Location.html#isFromMockProvider()).   
\[iOS\] Informação obtida através dos links: sourceInformation, \[link\](https://developer.apple.com/documentation/corelocation/cllocation/3861803-sourceinformation). isSimulatedBySoftware, \[link\](https://developer.apple.com/documentation/corelocation/cllocationsourceinformation/3861807-issimulatedbysoftware).   

post/requestBody/data/riskSignals/manual/isMockGPS

Adicionado - "example"

Adição

post/requestBody/data/riskSignals/manual/isMonkeyRunner

Adicionado - "example"

Adição

post/requestBody/data/riskSignals/manual/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de "root".

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante o pagamento for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de "root".    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

post/requestBody/data/riskSignals/manual/language

Alterado - "description"

Alteração

Indica o idioma do dispositivo no formato ISO 639-1.

Indica o idioma do dispositivo no formato ISO 639-1.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/util/Locale#getLanguage()).  
\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/locale/languagecode/)  

post/requestBody/data/riskSignals/manual/language

Adicionado - "example"

Adição

pt

post/requestBody/data/riskSignals/manual/osVersion

Alterado - "description"

Alteração

Versão do sistema operacional.

Versão do sistema operacional.  
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/Build.VERSION#RELEASE).  
\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620043-systemversion/).  

post/requestBody/data/riskSignals/manual/osVersion

Adicionado - "example"

Adição

14

post/requestBody/data/riskSignals/manual/screenBrightness

Alterado - "description"

Alteração

Indica o ní­vel de brilho da tela do dispositivo.   
Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive;   
Em dispositivos iOS o valor é um ponto flutuante entre 0.0 e 1.0.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante o pagamento for Android ou iOS.  

Indica o ní­vel de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre "0.0" e "1.0". Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

post/requestBody/data/riskSignals/manual/screenDimensions

Alterado - "description"

Alteração

Dimensões da tela do dispositivo

Dimensões que o aplicativo ocupa na tela do dispositivo.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/view/WindowMetrics#getBounds()), ou, para versões anteriores í  11, \[link\](https://developer.android.com/reference/android/util/DisplayMetrics).   
\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/metal/mtlrasterizationratemap/3088873-screensize/).  

post/requestBody/data/riskSignals/manual/screenDimensions/height

Adicionado - "example"

Adição

2340

post/requestBody/data/riskSignals/manual/screenDimensions/width

Adicionado - "example"

Adição

1080

post/requestBody/data/riskSignals/manual/userTimeZoneOffset

Alterado - "description"

Alteração

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]  

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permite a omissão da parte correspondente aos minutos, caso esta última tenha valor zero. Assim, ambos os valores '-03:00' e '-03' são válidos e representam o mesmo fuso horário.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/time/ZonedDateTime#getOffset()) ou, para versões anteriores í  8.0, \[link\](https://developer.android.com/reference/java/util/TimeZone#getOffset(long)).   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/timezone/).  

post/requestBody/data/riskSignals/manual/userTimeZoneOffset

Adicionado - "example"

Adição

\-3

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido - "cancellation"

Remoção

post/responses/201/data/properties

Removido - "originalRecurringPaymentId"

Remoção

post/responses/201/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReferente" diferente de "zero"), apenas o método AUTO é permitido, ou;  
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReferente" igual a "zero"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto "sweeping" selecionado no "oneOf" do campo "/data/recurringConfiguration/"), apenas os métodos MANU, DICT e INIC são permitidos.  

post/responses/201/data/paymentReference

Alterado - "example"

Alteração

23-07-2025/P1W

R/2025-09-23/P1M

post/responses/201/data/paymentReference

Removido - "minLength"

Remoção

4

post/responses/201/data/paymentReference

Removido - "maxLength"

Remoção

14

post/responses/201/data/paymentReference

Removido - "pattern"

Remoção

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

post/responses/201/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO. 

-   O preenchimento deve seguir a seguinte lógica: 
    
-   Primeiro Pagamento: Caso se trate do pagamento inicial avulso, especificado no campo "/data/firstPayment", o valor deste campo deve ser preenchido com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes realizados após o pagamento inicial, o campo paymentReference deve ser preenchido com uma string de Intervalo ISO 8601 no formato \`\`\`<start>/<duration>\`\`\`, que representa o ciclo exato ao qual o pagamento se refere. 
    
-   O componente \`\`\`<start>\`\`\` deve indicar a data de iní­cio do ciclo especí­fico ao qual o pagamento enviado se refere. 
    
-   O componente \`\`\`<duration>\`\`\` deve corresponder ao código da periodicidade do consentimento (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual) 
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1W
    
-   Segundo ciclo: 30-07-2025/P1W
    
-   Terceiro ciclo: 06-07-2025/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1M
    
-   Segundo ciclo: 23-08-2025/P1M
    
-   Terceiro ciclo: 23-09-2025/P1M
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de iní­cio do ciclo especí­fico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

post/responses/201/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   CONSENTIMENTO\_REVOGADO
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

post/responses/201/data/rejectionReason/code/enum

Removido - "CONSENTIMENTO\_REVOGADO"

Remoção

enum

post/responses/201/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.      
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   CONSENTIMENTO\_REVOGADO: O pagamento estava associado a um consentimento que foi revogado.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.      
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status "PARTIALLY\_ACCEPTED").
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: Limite total excedido
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O limite de tentativas para liquidação do pagamento permitidas pelo arranjo foi excedido.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    

  

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status "PARTIALLY\_ACCEPTED").
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: Limite total excedido
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    

  

post/responses/422/errors/items/code/enum

Removido - "LIMITE\_TENTATIVAS\_EXCEDIDO"

Remoção

enum

post/responses/422/errors/items/code/enum

Removido - "DETALHE\_TENTATIVA\_INVALIDO"

Remoção

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição especí­fica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status "PARTIALLY\_ACCEPTED").
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O limite de tentativas para liquidação do pagamento permitidas pelo arranjo foi excedido.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    

  

Descrição especí­fica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status "PARTIALLY\_ACCEPTED").
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    

  

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Tí­tulo especí­fico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status "PARTIALLY\_ACCEPTED").
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: Limite total excedido
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: Limite de transação excedido.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: Limite de tentativas excedido.
    
-   FORA\_PRAZO\_PERMITIDO: Tentativa fora do prazo.
    
-   DETALHE\_TENTATIVA\_INVALIDO: Nova tentativa inválida
    

  

Tí­tulo especí­fico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status "PARTIALLY\_ACCEPTED").
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: Limite total excedido
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: Limite de transação excedido.
    
-   FORA\_PRAZO\_PERMITIDO: Tentativa fora do prazo.
    

  

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReferente" diferente de "zero"), apenas o método AUTO é permitido, ou;  
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReferente" igual a "zero"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto "sweeping" selecionado no "oneOf" do campo "/data/recurringConfiguration/"), apenas os métodos MANU, DICT e INIC são permitidos.  

get/responses/200/data/paymentReference

Alterado - "example"

Alteração

23-07-2025/P1W

R/2025-09-23/P1M

get/responses/200/data/paymentReference

Removido - "minLength"

Remoção

4

get/responses/200/data/paymentReference

Removido - "maxLength"

Remoção

14

get/responses/200/data/paymentReference

Removido - "pattern"

Remoção

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

get/responses/200/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO. 

-   O preenchimento deve seguir a seguinte lógica: 
    
-   Primeiro Pagamento: Caso se trate do pagamento inicial avulso, especificado no campo "/data/firstPayment", o valor deste campo deve ser preenchido com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes realizados após o pagamento inicial, o campo paymentReference deve ser preenchido com uma string de Intervalo ISO 8601 no formato \`\`\`<start>/<duration>\`\`\`, que representa o ciclo exato ao qual o pagamento se refere. 
    
-   O componente \`\`\`<start>\`\`\` deve indicar a data de iní­cio do ciclo especí­fico ao qual o pagamento enviado se refere. 
    
-   O componente \`\`\`<duration>\`\`\` deve corresponder ao código da periodicidade do consentimento (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual) 
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1W
    
-   Segundo ciclo: 30-07-2025/P1W
    
-   Terceiro ciclo: 06-07-2025/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1M
    
-   Segundo ciclo: 23-08-2025/P1M
    
-   Terceiro ciclo: 23-09-2025/P1M
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de iní­cio do ciclo especí­fico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

get/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   CONSENTIMENTO\_REVOGADO
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

get/responses/200/data/rejectionReason/code/enum

Removido - "CONSENTIMENTO\_REVOGADO"

Remoção

enum

get/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.      
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   CONSENTIMENTO\_REVOGADO: O pagamento estava associado a um consentimento que foi revogado.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.      
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

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

patch/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReferente" diferente de "zero"), apenas o método AUTO é permitido, ou;  
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReferente" igual a "zero"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto "automatic" selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto "sweeping" selecionado no "oneOf" do campo "/data/recurringConfiguration/"), apenas os métodos MANU, DICT e INIC são permitidos.  

patch/responses/200/data/paymentReference

Alterado - "example"

Alteração

23-07-2025/P1W

R/2025-09-23/P1M

patch/responses/200/data/paymentReference

Removido - "minLength"

Remoção

4

patch/responses/200/data/paymentReference

Removido - "maxLength"

Remoção

14

patch/responses/200/data/paymentReference

Removido - "pattern"

Remoção

^zero$|^\\d{2}-\\d{2}-\\d{4}\\/P(1W|1M|3M|6M|1Y)$

patch/responses/200/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO. 

-   O preenchimento deve seguir a seguinte lógica: 
    
-   Primeiro Pagamento: Caso se trate do pagamento inicial avulso, especificado no campo "/data/firstPayment", o valor deste campo deve ser preenchido com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes realizados após o pagamento inicial, o campo paymentReference deve ser preenchido com uma string de Intervalo ISO 8601 no formato \`\`\`<start>/<duration>\`\`\`, que representa o ciclo exato ao qual o pagamento se refere. 
    
-   O componente \`\`\`<start>\`\`\` deve indicar a data de iní­cio do ciclo especí­fico ao qual o pagamento enviado se refere. 
    
-   O componente \`\`\`<duration>\`\`\` deve corresponder ao código da periodicidade do consentimento (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual) 
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1W
    
-   Segundo ciclo: 30-07-2025/P1W
    
-   Terceiro ciclo: 06-07-2025/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: 23-07-2025/P1M
    
-   Segundo ciclo: 23-08-2025/P1M
    
-   Terceiro ciclo: 23-09-2025/P1M
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de iní­cio do ciclo especí­fico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de iní­cio do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

patch/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   CONSENTIMENTO\_REVOGADO
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

Código identificador do motivo de rejeição.  
Motivo da rejeição do pagamento. Informações complementares sobre o motivo do status.

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   CONSENTIMENTO\_INVALIDO
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   TITULARIDADE\_INCONSISTENTE
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   FORA\_PRAZO\_PERMITIDO
    
-   DETALHE\_TENTATIVA\_INVALIDO
    
-   DETALHE\_PAGAMENTO\_INVALIDO
    

\[Restrição\] Esse motivo deverá ser enviado quando o campo \`/data/status\` for igual a RJCT (REJECTED).  

patch/responses/200/data/rejectionReason/code/enum

Removido - "CONSENTIMENTO\_REVOGADO"

Remoção

enum

patch/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.      
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   CONSENTIMENTO\_REVOGADO: O pagamento estava associado a um consentimento que foi revogado.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domí­nios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.      
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido.
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou perí­odo da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Adicionado - "journey"

Adição

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Adicionado - "journey"

Adição

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

post/responses/201/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    

  

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO
    

  

post/responses/201/data/rejection/reason/code/enum

Adicionado - "FLUXO\_NAO\_SUPORTADO\_PRODUTO"

Adição

enum

post/responses/201/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual í  conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual í  conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido - "riskSignals"

Remoção

get/responses/200/data/properties

Adicionado - "journey"

Adição

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

get/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    

  

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO
    

  

get/responses/200/data/rejection/reason/code/enum

Adicionado - "FLUXO\_NAO\_SUPORTADO\_PRODUTO"

Adição

enum

get/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual í  conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual í  conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Método para rejeitar, revogar ou editar um consentimento de longa duração:   
1 - Informações sobre a revogação:

-   Caso bem sucedido, o consentimento vai para o status "REVOKED";
    
-   Apenas consentimentos com status "AUTHORISED" podem ser revogados;
    
-   Pagamentos automáticos associados ao consentimento e que estão agendados para ocorrer até as 23:59h do próximo dia (a partir do dia de
    

  
solicitação da revogação) deverão ser mantidos. Pagamentos agendados para ocorrer após esse perí­odo devem ser cancelados.

-   Demais orientações referentes a revogação podem ser encontrados no header da API, tópico "Validações", item 3.
    

2 - Informações sobre a edição:

-   Os campos que são passí­veis de edição e suas regras podem ser encontrados através do \[link\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/628195665);
    
-   A edição é possí­vel apenas em casos de consentimento para Pix Automático ("automatic" escolhido no oneOf do objeto "recurringConfiguration") e que encontrem-se autorizados (\`data.status == AUTHORISED\`);
    
-   O envio do item "/data/creditors/name" atualizará o nome do recebedor em todos os elementos do array.
    
-   Caso consentimento seja de valor fixo (campo "/data/recurringConfiguration/automatic/fixedAmount" preenchido) não é permitida a edição do campo "/data/recurringConfiguration/automatic/maximumVariableAmount".
    
-   Caso o recebedor tenha definido um piso para o limite a ser estipulado pelo pagador (campo "/data/recurringConfiguration/automatic/minimumVariableAmount" preenchido), o valor máximo de limite por transação definido pelo usuário pagador (campo "/data/recurringConfiguration/automatic/maximumVariableAmount") não pode ser menor que o valor estipulado pelo recebedor.
    
-   Caso o seja editado o prazo de expiração do consentimento e já existam pagamentos agendados para dias posteriores a nova data definida, estes pagamentos devem ser cancelados.
    

3 - Informações sobre a rejeição: 

-   Caso haja necessidade de cancelamento de um consentimento ainda não autorizado, o iniciador poderá chamar o endpoint para mover o consentimento para REJECTED.
    

  

Método para rejeitar, revogar ou editar um consentimento de longa duração:   
1 - Informações sobre a revogação:

-   Caso bem sucedido, o consentimento vai para o status "REVOKED";
    
-   Apenas consentimentos com status "AUTHORISED" podem ser revogados;
    
-   Caso a revogação seja realizada pelo recebedor entre 22:00h até 23:59h: Pagamentos automáticos associados ao consentimento e que estão agendados para ocorrer até as 23:59h do próximo dia (a partir do dia de solicitação da revogação) deverão ser mantidos. Pagamentos agendados para ocorrer após esse perí­odo devem ser cancelados.
    
-   Caso a revogação seja realizada pelo recebedor até as 22:00h ou pelo usuário pagador até as 23:59h: Pagamentos automáticos associados ao consentimento e que estão agendados para ocorrer até as 23:59h do próximo dia (apartir do dia de solicitação da revogação) deverão ser cancelados
    
-   Demais orientações referentes a revogação podem ser encontrados no header da API, tópico "Validações", item 3.
    

2 - Informações sobre a edição:

-   Os campos que são passí­veis de edição e suas regras podem ser encontrados através do \[link\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/628195665);
    
-   A edição é possí­vel apenas em casos de consentimento para Pix Automático ("automatic" escolhido no oneOf do objeto "recurringConfiguration") e que encontrem-se autorizados (\`data.status == AUTHORISED\`);
    
-   O envio do item "/data/creditors/name" atualizará o nome do recebedor em todos os elementos do array.
    
-   Caso consentimento seja de valor fixo (campo "/data/recurringConfiguration/automatic/fixedAmount" preenchido) não é permitida a edição do campo "/data/recurringConfiguration/automatic/maximumVariableAmount".
    
-   Caso o recebedor tenha definido um piso para o limite a ser estipulado pelo pagador (campo "/data/recurringConfiguration/automatic/minimumVariableAmount" preenchido), o valor máximo de limite por transação definido pelo usuário pagador (campo "/data/recurringConfiguration/automatic/maximumVariableAmount") não pode ser menor que o valor estipulado pelo recebedor.
    
-   Caso o seja editado o prazo de expiração do consentimento e já existam pagamentos agendados para dias posteriores a nova data definida, estes pagamentos devem ser cancelados.
    

3 - Informações sobre a rejeição: 

-   Caso haja necessidade de cancelamento de um consentimento ainda não autorizado, o iniciador poderá chamar o endpoint para mover o consentimento para REJECTED.
    

  

patch/requestBody/data/oneOf/0/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

 \*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa fí­sica/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurí­dica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

 \*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurí­dica.
    

  

Objeto contendo os dados do recebedor (creditor).

 \*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa fí­sica/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurí­dica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

 \*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurí­dica. 
    

 \*\*Informar apenas esse item não deve alterar nenhum outro parâmetro do consentimento\*\*  

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um perí­odo indeterminado; ou;

Caso enviado, esse campo deve ser, no mí­nimo, D, sendo D o dia da requisição e o horário deve ser ás 23:59:59 (UTC).  

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format). 

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um perí­odo indeterminado exceto em casos de edição exclusiva do campo "/data/creditors/name; ou; 

Caso enviado, esse campo deve ser, no mí­nimo, D, sendo D o dia da requisição e o horário deve ser ás 23:59:59 (UTC).  

patch/requestBody/data/oneOf/0/recurringConfiguration/automatic/maximumVariableAmount

Alterado - "description"

Alteração

Valor máximo permitido por cobrança, caso preenchido, representa um consentimento para pagamentos de valores variáveis.

\[Restrição\]  
Caso esse campo não seja enviado, a instituição detentora deve considerar o valor máximo do pagamento variável como indefinido;

Caso informado, o valor desse campo não deve ser inferior ao valor definido no campo "/data/recurringConfiguration/automatic/minimumVariableAmount".  

Valor máximo permitido por cobrança, caso preenchido, representa um consentimento para pagamentos de valores variáveis.

\[Restrição\]  
Caso esse campo não seja enviado, a instituição detentora deve considerar o valor máximo do pagamento variável como indefinido, exceto em casos de edição exclusiva do campo "/data/creditors/name";

Caso informado, o valor desse campo não deve ser inferior ao valor definido no campo "/data/recurringConfiguration/automatic/minimumVariableAmount".  

patch/requestBody/data/oneOf/0/riskSignals/properties

Removido - "isCallingProgress"

Remoção

patch/requestBody/data/oneOf/0/riskSignals/properties

Adicionado - "isCallInProgress"

Adição

patch/requestBody/data/oneOf/0/riskSignals/accountTenure

Adicionado - "example"

Adição

21/05/2020

patch/requestBody/data/oneOf/0/riskSignals/antennaInformation

Alterado - "example"

Alteração

CellIdentityLte:{ mCi=2\*\*\*\*\*\*60 mPci=274 mTac=5\*\*\*1 mEarfcn=9510 mBands=\[28\] mBandwidth=2147483647 mMcc=724 mMnc=10 mAlphaLong=VIVO mAlphaShort=VIVO mAdditionalPlmns={} mCsgInfo=null}, CellIdentityLte:{ mCi=1\*\*\*\*\*01 mPci=361 mTac=3\*\*\*6 mEarfcn=9410 mBands=\[28\]mBandwidth=2147483647 mMcc=724 mMnc=03 mAlphaLong=TIMBRASIL mAlphaShort=TIMBRASIL mAdditionalPlmns={} mCsgInfo=null}

CellIdentityLte:{mCi=2\*\*\*\*\*\*60 mPci=274 mTac=5\*\*\*1 mEarfcn=9510 mBands=\[28\] mBandwidth=2147483647 mMcc=724 mMnc=10 mAlphaLong=VIVO mAlphaShort=VIVO mAdditionalPlmns={} mCsgInfo=null}  

patch/requestBody/data/oneOf/0/riskSignals/deviceId

Alterado - "description"

Alteração

ID único do dispositivo gerado pela plataforma.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).  

ID único do dispositivo gerado pela plataforma.  Utiliza-se a propriedade do sistema que identifica a combinação de usuário logado, chave de assinatura do aplicativo e dispositivo.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID\_ID).   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor/).  

patch/requestBody/data/oneOf/0/riskSignals/deviceId

Alterado - "example"

Alteração

00000000-54b3-e7c7-0000-000046bffd97

00aa11bb22cc33dd

patch/requestBody/data/oneOf/0/riskSignals/elapsedTimeSinceBoot

Alterado - "description"

Alteração

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo for Android ou iOS.  

Indica por quanto tempo (em milissegundos) o dispositivo está ligado.    
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/SystemClock#elapsedRealtime%28%29).    
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/kernel/kern/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

patch/requestBody/data/oneOf/0/riskSignals/elapsedTimeSinceBoot

Adicionado - "example"

Adição

6356027

patch/requestBody/data/oneOf/0/riskSignals/geolocation

Alterado - "description"

Alteração

Localização do usuário, obtida com seu consentimento.

\[Android\] Informação obtida através do \[link\](https://developers.google.com/android/reference/com/google/android/gms/location/FusedLocationProviderClient#public-abstract-tasklocation-getlastlocation) considerando as permissões necessárias.

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/corelocation/).

\[Restrição\] A ITP deve solicitar ao usuário a permissão para compartilhamento de sua localização.  
Este campo poderá ser omitido caso o GPS esteja indisponí­vel, isto é, sem sinal, ou em dispositivos sem o hardware necessário; ou caso o usuário negue o consentimento para coleta do dado.  

Localização do usuário, obtida com seu consentimento.  
\[Android\] Informação obtida através do \[link\](https://developers.google.com/android/reference/com/google/android/gms/location/FusedLocationProviderClient#public-abstract-tasklocation-getlastlocation) considerando as permissões necessárias.   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/corelocation/).   
\[Restrição\] A ITP deve solicitar ao usuário a permissão para compartilhamento de sua localização. Este campo poderá ser omitido caso o GPS esteja indisponí­vel, isto é, sem sinal, ou em dispositivos sem o hardware necessário; ou caso o usuário negue o consentimento.  

patch/requestBody/data/oneOf/0/riskSignals/geolocation/latitude

Adicionado - "example"

Adição

\-15.738.602

patch/requestBody/data/oneOf/0/riskSignals/geolocation/longitude

Adicionado - "example"

Adição

\-47.926.498

patch/requestBody/data/oneOf/0/riskSignals/geolocation/type

Adicionado - "example"

Adição

FINE

patch/requestBody/data/oneOf/0/riskSignals/integrity

Alterado - "description"

Alteração

Informa a integridade do dispositivo e app.   
No Android, conforme documentação Play API Integrity - \[Android\](https://developer.android.com/google/play/integrity/overview?hl=pt-br).   
No iOS, conforme documentação App Attest \[iOS\](https://developer.apple.com/documentation/devicecheck/establishing\_your\_app\_s\_integrity)  

Informa a integridade do dispositivo e app.   
\[Android\] Conforme documentação Play API Integrity, \[link\](https://developer.android.com/google/play/integrity/overview?hl=pt-br).   
\[iOS\] Conforme documentação App Attest, \[link\](https://developer.apple.com/documentation/devicecheck/establishing\_your\_app\_s\_integrity).  

patch/requestBody/data/oneOf/0/riskSignals/isCharging

Alterado - "description"

Alteração

Indica se a bateria do dispositivo está sendo carregada.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/BatteryManager).

\[iOS\] Informações obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620045-batterymonitoringenabled/).  

Indica se a bateria do dispositivo está sendo carregada.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/BatteryManager).   
\[iOS\] Informações obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620045-batterymonitoringenabled/).  

patch/requestBody/data/oneOf/0/riskSignals/isCharging

Adicionado - "example"

Adição

true

patch/requestBody/data/oneOf/0/riskSignals/isDevModeEnabled

Adicionado - "example"

Adição

patch/requestBody/data/oneOf/0/riskSignals/isEmulated

Adicionado - "example"

Adição

patch/requestBody/data/oneOf/0/riskSignals/isMockGPS

Alterado - "description"

Alteração

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo COARSE ou FINE.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/location/Location.html#isMock()) ou, para versões anteriores á 12, \[link\](https://developer.android.com/reference/android/location/Location.html#isFromMockProvider()).

\[iOS\] Informação obtida através dos links: sourceInformation, \[link\](https://developer.apple.com/documentation/corelocation/cllocation/3861803-sourceinformation). isSimulatedBySoftware, \[link\](https://developer.apple.com/documentation/corelocation/cllocationsourceinformation/3861807-issimulatedbysoftware).  

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo \`COARSE\` ou \`FINE\`.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/location/Location.html#isMock()) ou, para versões anteriores á 12, \[link\](https://developer.android.com/reference/android/location/Location.html#isFromMockProvider()).   
\[iOS\] Informação obtida através dos links: sourceInformation, \[link\](https://developer.apple.com/documentation/corelocation/cllocation/3861803-sourceinformation). isSimulatedBySoftware, \[link\](https://developer.apple.com/documentation/corelocation/cllocationsourceinformation/3861807-issimulatedbysoftware).   

patch/requestBody/data/oneOf/0/riskSignals/isMockGPS

Adicionado - "example"

Adição

patch/requestBody/data/oneOf/0/riskSignals/isMonkeyRunner

Adicionado - "example"

Adição

patch/requestBody/data/oneOf/0/riskSignals/isRootedDevice

Alterado - "description"

Alteração

Indica se o dispositivo atualmente está com permissão de "root".

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de "root".    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

patch/requestBody/data/oneOf/0/riskSignals/language

Alterado - "description"

Alteração

Indica o idioma do dispositivo no formato ISO 639-1.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/util/Locale#getLanguage()).

\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/locale/languagecode/).  

Indica o idioma do dispositivo no formato ISO 639-1.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/util/Locale#getLanguage()).  
\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/locale/languagecode/)  

patch/requestBody/data/oneOf/0/riskSignals/language

Adicionado - "example"

Adição

pt

patch/requestBody/data/oneOf/0/riskSignals/osVersion

Alterado - "description"

Alteração

Versão do sistema operacional.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/Build.VERSION#RELEASE).

\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620043-systemversion/).  

Versão do sistema operacional.  
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/os/Build.VERSION#RELEASE).  
\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/uikit/uidevice/1620043-systemversion/).  

patch/requestBody/data/oneOf/0/riskSignals/osVersion

Adicionado - "example"

Adição

14

patch/requestBody/data/oneOf/0/riskSignals/screenBrightness

Alterado - "description"

Alteração

Indica o ní­vel de brilho da tela do dispositivo.

\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).

\[iOS\] O valor é ponto flutuante entre "0.0" e "1.0". Referência no \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo for Android ou iOS.  

Indica o ní­vel de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre "0.0" e "1.0". Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

patch/requestBody/data/oneOf/0/riskSignals/screenDimensions

Alterado - "description"

Alteração

Dimensões que o aplicativo ocupa na tela do dispositivo.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/view/WindowMetrics#getBounds()), ou, para versões anteriores á 11, \[link\](https://developer.android.com/reference/android/util/DisplayMetrics).

\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/metal/mtlrasterizationratemap/3088873-screensize/).  

Dimensões que o aplicativo ocupa na tela do dispositivo.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/view/WindowMetrics#getBounds()), ou, para versões anteriores á 11, \[link\](https://developer.android.com/reference/android/util/DisplayMetrics).   
\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/metal/mtlrasterizationratemap/3088873-screensize/).  

patch/requestBody/data/oneOf/0/riskSignals/screenDimensions/height

Adicionado - "example"

Adição

2340

patch/requestBody/data/oneOf/0/riskSignals/screenDimensions/width

Adicionado - "example"

Adição

1080

patch/requestBody/data/oneOf/0/riskSignals/userTimeZoneOffset

Alterado - "description"

Alteração

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permite a omissão da parte correspondente aos minutos, caso esta última tenha valor zero. Assim, ambos os valores '-03:00' e '-03' são válidos e representam o mesmo fuso horário.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/time/ZonedDateTime#getOffset()) ou, para versões anteriores á 8.0, \[link\](https://developer.android.com/reference/java/util/TimeZone#getOffset(long)).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/timezone/).  

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permite a omissão da parte correspondente aos minutos, caso esta última tenha valor zero. Assim, ambos os valores '-03:00' e '-03' são válidos e representam o mesmo fuso horário.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/time/ZonedDateTime#getOffset()) ou, para versões anteriores á 8.0, \[link\](https://developer.android.com/reference/java/util/TimeZone#getOffset(long)).   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/timezone/).  

patch/requestBody/data/oneOf/0/riskSignals/userTimeZoneOffset

Adicionado - "example"

Adição

\-3

patch/requestBody/data/oneOf/2/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    

  

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO
    

  

patch/requestBody/data/oneOf/2/rejection/reason/code/enum

Adicionado - "FLUXO\_NAO\_SUPORTADO\_PRODUTO"

Adição

enum

patch/requestBody/data/oneOf/2/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual á conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual á conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
    

  

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido - "riskSignals"

Remoção

patch/responses/200/data/properties

Adicionado - "journey"

Adição

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

patch/responses/200/data/rejection/reason/code

Alterado - "description"

Alteração

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    

  

Código indicador do motivo de rejeição.

-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   AUTENTICACAO\_DIVERGENTE
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO
    

  

patch/responses/200/data/rejection/reason/code/enum

Adicionado - "FLUXO\_NAO\_SUPORTADO\_PRODUTO"

Adição

enum

patch/responses/200/data/rejection/reason/detail

Alterado - "description"

Alteração

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual á conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual á conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
