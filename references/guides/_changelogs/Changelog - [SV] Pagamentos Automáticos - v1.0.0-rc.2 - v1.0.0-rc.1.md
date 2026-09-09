# Changelog - [SV] Pagamentos Automáticos - v1.0.0-rc.2 - v1.0.0-rc.1

**A implementação e certificação do Pix Automático está pausada no momento. O produto Transferência Inteligentes (Sweeping Accounts) continua disponível para implementação e certificação.**

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

\-

Adicionado texto no header

Adição

6.1.13 Limite valor excedido por período: Foi atingido o valor limite permitido pelo usuário por um determinado período de tempo no consentimento do pagamento (LIMITE\_PERIODO\_VALOR\_EXCEDIDO);

6.1.14 Limite quantidade excedida por período: A quantidade de cobranças atingiu o limite determinado pelo usuário na criação do consentimento (LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO).

\-

Alterado a descrição do OAuth2ClientCredentials

Alteração

Fluxo OAuth necessário para que a iniciadora possa iniciar pagamentos. Requer o processo de redirecionamento e autenticação do usuário. Apenas pagamentos iniciados pela mesma iniciadora de pagamentos podem ser consultados ou cancelados através de modelo client credentials.

Fluxo OAuth necessário para que a iniciadora possa consultar ou cancelar pagamentos e criar ou consultar consentimentos. Apenas pagamentos e consentimentos iniciados pela mesma iniciadora de pagamentos podem ser consultados ou cancelados através deste modelo.

\-

Alterado texto no header

Alteração

\## Limites transacionais para Transferências Inteligentes

As transferências inteligentes são categorizadas como um Pix Imediato entre diferentes contas de mesma titularidade.

Sendo assim, a tratativa a ser dada aos limites definidos no consentimento desse produto devem ser as mesmas que a instituição aplica para os limites do arranjo Pix.

\## Limites transacionais para Transferências Inteligentes

-   As transferências inteligentes são categorizadas como um Pix Imediato entre diferentes contas de mesma titularidade. Sendo assim, a tratativa a ser dada aos limites definidos no consentimento desse produto devem ser as mesmas que a instituição aplica para os limites do arranjo Pix.
    

-   O cálculo do limite periódico disponível ao cliente deve seguir da seguinte maneira, considerando os cenários e
    

exemplos:

-   Limite Diário (Ex.: R$ 100,00): Este limite controla as transferências realizadas dentro de um único dia, considerando o período das 00:00h até as 23:59h. Por exemplo, se um usuário transferir R$ 50,00 às 10:00h, ele ainda terá R$ 50,00 disponíveis para transferências até a meia-noite do mesmo dia;
    

-   Limite Semanal (Ex.: R$ 1.000,00): O limite semanal abrange o período de uma semana inteira, começando às 00:00h de domingo e terminando às 23:59h do sábado. Por exemplo, se um usuário transferir R$ 200,00 na terça-feira e R$ 500,00 na quinta-feira, ele ainda poderá transferir até R$ 300,00 até o final do sábado;
    

-   Limite Mensal (Ex.: R$ 10.000,00): Este limite mensal é calculado do primeiro ao último dia de cada mês. Por exemplo, em um mês, se o usuário transferir R$ 2.000,00 na primeira semana e R$ 3.000,00 na segunda semana, ele ainda terá R$ 5.000,00 disponíveis para transferências pelo restante do mês;
    

-   Limite Anual (Ex.: R$ 50.000,00): O limite anual conta do primeiro dia de janeiro ao último dia de dezembro. Por exemplo, se um usuário transferir R$ 10.000,00 até março, mais R$ 15.000,00 até junho e mais R$ 20.000,00 até setembro, ele só poderá transferir outros R$ 5.000,00 até o final do ano;
    

-   Esses limites ajudam a gerenciar as transferências de fundos, garantindo que não excedam os montantes estabelecidos para cada período. Cada limite é independente e é recalculado conforme sua respectiva janela de tempo se reinicia.
    

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

post/requestBody/data/startDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

post/responses/201/data/startDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

post/responses/201/data/startDateTime

Removido - "type"

Remoção

string

post/data/rejection

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso status do consentimento igual a "REJECTED" ou "REVOKED".

\[Restrição\] Campo de preenchimento obrigatório caso status do consentimento igual a "REJECTED".

post/data/revocation

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso status do consentimento igual a "REVOKED".

## GET /recurring-consents/{recurringConsentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

get/responses/200/data/startDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

get/responses/200/data/startDateTime

Removido - "type"

Remoção

string

post/data/rejection

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso status do consentimento igual a "REJECTED" ou "REVOKED".

\[Restrição\] Campo de preenchimento obrigatório caso status do consentimento igual a "REJECTED".

post/data/revocation

Alterado - "description"

Alteração

\[Restrição\] Campo de preenchimento obrigatório caso status do consentimento igual a "REVOKED".

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/requestBody/data/oneOf/0/startDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

patch/requestBody/data/oneOf/0/startDateTime

Removido - "type"

Remoção

string

patch/requestBody/data/oneOf/1/startDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

patch/requestBody/data/oneOf/1/startDateTime

Removido - "type"

Remoção

string

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/properties

Removido obrigatóriedade no campo 'startDateTime'

Remoção

required

patch/responses/200/data/startDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

Data e hora em que o consentimento deve passar a ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://...

patch/responses/200/data/startDateTime

Removido - "type"

Remoção

string

patch/responses/data/rejectionReason/code

Alterado - "description"

Alteração

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
    

patch/responses/data/rejectionReason/detail

Alterado - "description"

Alteração

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
    

## POST /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/data/rejectionReason/code

Alterado - "description"

Alteração

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
    

post/responses/data/rejectionReason/detail

Alterado - "description"

Alteração

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/data/rejectionReason/code

Alterado - "description"

Alteração

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    

-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO
    
-   PAGAMENTO\_RECUSADO\_DETENTORA
    
-   PAGAMENTO\_RECUSADO\_SPI
    
-   FALHA\_INFRAESTRUTURA\_SPI
    
-   FALHA\_INFRAESTRUTURA\_ICP
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO
    

get/responses/data/rejectionReason/detail

Alterado - "description"

Alteração

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/data/rejectionReason/code

Alterado - "description"

Alteração

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
    

get/responses/data/rejectionReason/detail

Alterado - "description"

Alteração

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/data/rejectionReason/code

Alterado - "description"

Alteração

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
    

patch/responses/data/rejectionReason/detail

Alterado - "description"

Alteração

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status diferente de "AUTHORISED" ou está expirado);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
