# Changelog - [SV] Pagamentos Automáticos - v2.2.0-rc.2 - v2.1.0

## Alterações na seção de orientações do swagger

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

/info

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix au...

/info

Alterado - "version"

Alteração

2.1.0

2.2.0-rc.2

paths

Adicionado - "/pix/recurring-payments/{originalRecurringPaymentId}/retry"

Adição

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/originalRecurringPaymentId

Alterado - "description"

Alteração

Campo que contém o código ou o identificador da tentativa original de pagamento que falhou.  
Código ou identificador único criado pela instituição detentora da conta para representar a iniciação de pagamento.  
Caso informado, devem ser retornados todos os pagamentos associados ao identificador informado, sendo eles o pagamento original (dono do identificador) e as novas tentativas que enviaram o identificador na sua requisição, indicando que representam nova tentativa.  

Campo que contém o código ou o identificador da tentativa original de pagamento que falhou.   
Código ou identificador único criado pela instituição detentora da conta para representar a iniciação de pagamento.   
Caso informado, devem ser retornados todos os pagamentos associados ao identificador informado, sendo eles o pagamento original (dono do identificador) e as novas tentativas que enviaram o identificador na sua requisição, indicando que representam nova tentativa.  

get/responses/200/data/items/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/items/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

get/responses/200/data/items/paymentReference

Removido - "maxLength"

Remoção

10

get/responses/200/data/items/paymentReference

Alterado - "description"

Alteração

\[Restrição\]  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detentora deve retornar erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.

-   Primeiro pagamento: Se for o pagamento inicial especificado em “/data/firstPayment”, preencha o campo com a string fixa “zero”.
    
-   Semanal: Preencha com W$numSemana-$ano, onde $numSemana representa o número da semana no ano. Exemplo: "W50-2024".
    
-   Mensal: Use M$mês-$ano, onde $mês representa o mês com dois dígitos. Exemplo: "M09-2024".
    
-   Trimestral: Utilize Q$trimestre-$ano, onde $trimestre indica o trimestre do ano (1 a 4).
    
-   Janeiro a Março: Q1-$ano (ex.: "Q1-2024").
    
-   Abril a Junho: Q2-$ano (ex.: "Q2-2024").
    
-   Julho a Setembro: Q3-$ano (ex.: "Q3-2024").
    
-   Outubro a Dezembro: Q4-$ano (ex.: "Q4-2024").
    
-   Semestral: Utilize $semestre-$ano, onde $semestre indica o semestre do ano (1 para janeiro a junho e 2 para julho a dezembro).
    
-   Janeiro a Junho: S1-$ano (ex.: "S1-2024").
    
-   Julho a Dezembro: S2-$ano (ex.: "S2-2024").
    
-   Anual: Use Y$ano, apenas com o ano. Exemplo: "Y2024".
    
-   Exemplo de Formatos:
    
-   Primeiro pagamento: "zero"
    
-   Semanal: "W50-2024"
    
-   Mensal: "M09-2024"
    
-   Trimestral: "Q3-2024"
    
-   Semestral: "S2-2024"
    
-   Anual: "Y2024"
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de início do ciclo específico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

get/responses/200/data/items/paymentReference

Adicionado - "example"

Adição

R/2025-09-23/P1M

get/responses/200/data/items/rejectionReason/code

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
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   CONSENTIMENTO\_REVOGADO: O pagamento estava associado a um consentimento que foi revogado.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final);
    
-   FALHA\_INFRAESTRUTURA\_SPI: Indica uma falha no Sistema de Pagamentos Instantâneos (SPI);
    
-   FALHA\_INFRAESTRUTURA\_ICP: Indica uma falha na Infraestrutura de Chaves Públicas (ICP);
    
-   FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR: Indica uma falha na infraestrutura do Prestador de Serviço de Pagamento (PSP) que recebe o pagamento;
    
-   FALHA\_INFRAESTRUTURA\_DETENTORA: indica uma falha na infraestrutura da instituição detentora das informações ou recursos;
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração.
    
-   LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO: O valor da transação excede o limite global do consentimento.
    
-   LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO: O valor da transação ultrapassar o limite de valor por transação.
    
-   LIMITE\_TENTATIVAS\_EXCEDIDO: O máximo de tentativas de liquidação permitidas pelo arranjo foi atingido
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio
    

  

get/responses/200/data/items/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo “localInstrument”:

MANU - O campo transactionIdentification não deve ser preenchido;   
DICT - O campo transactionIdentification não deve ser preenchido;   
INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]).  

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo localInstument: 

-   MANU - O campo transactionIdentification não deve ser preenchido; 
    
-   DICT - O campo transactionIdentification não deve ser preenchido; 
    
-   INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]); 
    
-   AUTO – O campo transactionIdentification não deve ser preenchido.
    

  

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

post/requestBody/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/requestBody/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

post/requestBody/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    

\[Restrição\] Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto “sweeping” selecionado no “oneOf” do campo “/data/recurringConfiguration/”), apenas os métodos MANU, DICT e INIC são permitidos.  

post/requestBody/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

post/requestBody/data/paymentReference

Removido - "maxLength"

Remoção

10

post/requestBody/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detentora deve retornar erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.

-   Primeiro pagamento: Se for o pagamento inicial especificado em “/data/firstPayment”, preencha o campo com a string fixa “zero”.
    
-   Semanal: Preencha com W$numSemana-$ano, onde $numSemana representa o número da semana no ano. Exemplo: "W50-2024".
    
-   Mensal: Use M$mês-$ano, onde $mês representa o mês com dois dígitos. Exemplo: "M09-2024".
    
-   Trimestral: Utilize Q$trimestre-$ano, onde $trimestre indica o trimestre do ano (1 a 4).
    
-   Janeiro a Março: Q1-$ano (ex.: "Q1-2024").
    
-   Abril a Junho: Q2-$ano (ex.: "Q2-2024").
    
-   Julho a Setembro: Q3-$ano (ex.: "Q3-2024").
    
-   Outubro a Dezembro: Q4-$ano (ex.: "Q4-2024").
    
-   Semestral: Utilize $semestre-$ano, onde $semestre indica o semestre do ano (1 para janeiro a junho e 2 para julho a dezembro).
    
-   Janeiro a Junho: S1-$ano (ex.: "S1-2024").
    
-   Julho a Dezembro: S2-$ano (ex.: "S2-2024").
    
-   Anual: Use Y$ano, apenas com o ano. Exemplo: "Y2024".
    
-   Exemplo de Formatos:
    
-   Primeiro pagamento: "zero"
    
-   Semanal: "W50-2024"
    
-   Mensal: "M09-2024"
    
-   Trimestral: "Q3-2024"
    
-   Semestral: "S2-2024"
    
-   Anual: "Y2024"
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de início do ciclo específico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

post/requestBody/data/paymentReference

Adicionado - "example"

Adição

R/2025-09-23/P1M

post/requestBody/data/recurringConsentId

Alterado - "description"

Alteração

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada. Deverá ser um URN - Uniform Resource Name.  
Um URN, conforme definido na \[RFC8141\](https://tools.ietf.org/html/rfc8141) é um Uniform Resource  
Identifier - URI - que é atribuído sob o URI scheme "urn" e um namespace URN específico, com a intenção de que o URN  
seja um identificador de recurso persistente e independente da localização.  
Considerando a string urn:bancoex:C1DD33123 como exemplo para \`recurringConsentId\` temos:

-   o namespace(urn)
    
-   o identificador associado ao namespace da instituição transmissora (bancoex)
    
-   o identificador específico dentro do namespace (C1DD33123).
    

  
Informações mais detalhadas sobre a construção de namespaces devem ser consultadas na \[RFC8141\](https://tools.ietf.org/html/rfc8141).

\[Restrição\] Este campo é de preenchimento obrigatório quando o valor do campo authorisationFlow for igual a FIDO\_FLOW.  

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada. Deverá ser um URN - Uniform Resource Name.  
Um URN, conforme definido na \[RFC8141\](https://tools.ietf.org/html/rfc8141) é um Uniform Resource  
Identifier - URI - que é atribuído sob o URI scheme "urn" e um namespace URN específico, com a intenção de que o URN  
seja um identificador de recurso persistente e independente da localização.  
Considerando a string urn:bancoex:C1DD33123 como exemplo para \`recurringConsentId\` temos:

-   o namespace(urn)
    
-   o identificador associado ao namespace da instituição transmissora (bancoex)
    
-   o identificador específico dentro do namespace (C1DD33123). 
    

  
Informações mais detalhadas sobre a construção de namespaces devem ser consultadas na \[RFC8141\](https://tools.ietf.org/html/rfc8141). 

\[Restrição\] Este campo é de preenchimento obrigatório quando o valor do campo authorisationFlow for igual a FIDO\_FLOW.  

post/requestBody/data/riskSignals/manual/properties

Removido - "isCallingProgress"

Remoção

post/requestBody/data/riskSignals/manual/properties

Adicionado - "isCallInProgress"

Adição

post/requestBody/data/riskSignals/manual/accountTenure

Adicionado - "example"

Adição

2020-05-21

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
\[Restrição\] A ITP deve solicitar ao usuário a permissão para compartilhamento de sua localização. Este campo poderá ser omitido caso o GPS esteja indisponível, isto é, sem sinal, ou em dispositivos sem o hardware necessário; ou caso o usuário negue o consentimento.  

post/requestBody/data/riskSignals/manual/geolocation/latitude

Adicionado - "example"

Adição

\-15.738602

post/requestBody/data/riskSignals/manual/geolocation/longitude

Adicionado - "example"

Adição

\-47.926498

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
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/location/Location.html#isMock()) ou, para versões anteriores à 12, \[link\](https://developer.android.com/reference/android/location/Location.html#isFromMockProvider()).   
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

Indica se o dispositivo atualmente está com permissão de “root”.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante o pagamento for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de “root”.    
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

Indica o nível de brilho da tela do dispositivo.   
Em dispositivos Android o valor é um inteiro, entre 0 e 255, inclusive;   
Em dispositivos iOS o valor é um ponto flutuante entre 0.0 e 1.0.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante o pagamento for Android ou iOS.  

Indica o nível de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

post/requestBody/data/riskSignals/manual/screenDimensions

Alterado - "description"

Alteração

Dimensões da tela do dispositivo

Dimensões que o aplicativo ocupa na tela do dispositivo.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/view/WindowMetrics#getBounds()), ou, para versões anteriores à 11, \[link\](https://developer.android.com/reference/android/util/DisplayMetrics).   
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
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/time/ZonedDateTime#getOffset()) ou, para versões anteriores à 8.0, \[link\](https://developer.android.com/reference/java/util/TimeZone#getOffset(long)).   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/timezone/).  

post/requestBody/data/riskSignals/manual/userTimeZoneOffset

Adicionado - "example"

Adição

\-03

post/requestBody/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo localInstument:

-   MANU - O campo transactionIdentification não deve ser preenchido;
    
-   DICT - O campo transactionIdentification não deve ser preenchido;
    
-   INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]).
    

  

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo localInstument: 

-   MANU - O campo transactionIdentification não deve ser preenchido; 
    
-   DICT - O campo transactionIdentification não deve ser preenchido; 
    
-   INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]); 
    
-   AUTO – O campo transactionIdentification não deve ser preenchido.
    

  

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

post/responses/201/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/responses/201/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

post/responses/201/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    

\[Restrição\] Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto “sweeping” selecionado no “oneOf” do campo “/data/recurringConfiguration/”), apenas os métodos MANU, DICT e INIC são permitidos.  

post/responses/201/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

post/responses/201/data/paymentReference

Removido - "maxLength"

Remoção

10

post/responses/201/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detentora deve retornar erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.

-   Primeiro pagamento: Se for o pagamento inicial especificado em “/data/firstPayment”, preencha o campo com a string fixa “zero”.
    
-   Semanal: Preencha com W$numSemana-$ano, onde $numSemana representa o número da semana no ano. Exemplo: "W50-2024".
    
-   Mensal: Use M$mês-$ano, onde $mês representa o mês com dois dígitos. Exemplo: "M09-2024".
    
-   Trimestral: Utilize Q$trimestre-$ano, onde $trimestre indica o trimestre do ano (1 a 4).
    
-   Janeiro a Março: Q1-$ano (ex.: "Q1-2024").
    
-   Abril a Junho: Q2-$ano (ex.: "Q2-2024").
    
-   Julho a Setembro: Q3-$ano (ex.: "Q3-2024").
    
-   Outubro a Dezembro: Q4-$ano (ex.: "Q4-2024").
    
-   Semestral: Utilize $semestre-$ano, onde $semestre indica o semestre do ano (1 para janeiro a junho e 2 para julho a dezembro).
    
-   Janeiro a Junho: S1-$ano (ex.: "S1-2024").
    
-   Julho a Dezembro: S2-$ano (ex.: "S2-2024").
    
-   Anual: Use Y$ano, apenas com o ano. Exemplo: "Y2024".
    
-   Exemplo de Formatos:
    
-   Primeiro pagamento: "zero"
    
-   Semanal: "W50-2024"
    
-   Mensal: "M09-2024"
    
-   Trimestral: "Q3-2024"
    
-   Semestral: "S2-2024"
    
-   Anual: "Y2024"
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de início do ciclo específico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

post/responses/201/data/paymentReference

Adicionado - "example"

Adição

R/2025-09-23/P1M

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
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

post/responses/201/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo “localInstrument”:

MANU - O campo transactionIdentification não deve ser preenchido;   
DICT - O campo transactionIdentification não deve ser preenchido;   
INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]).  

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo localInstument: 

-   MANU - O campo transactionIdentification não deve ser preenchido; 
    
-   DICT - O campo transactionIdentification não deve ser preenchido; 
    
-   INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]); 
    
-   AUTO – O campo transactionIdentification não deve ser preenchido.
    

  

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
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    

  

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    

  

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

Descrição específica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    

  

Descrição específica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    

  

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    
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
    

  

Título específico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (em status final).
    
-   CONSENTIMENTO\_PENDENTE\_AUTORIZACAO: Consentimento pendente autorização de múltiplas alçadas (status “PARTIALLY\_ACCEPTED”).
    
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

get/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

get/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    

\[Restrição\] Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto “sweeping” selecionado no “oneOf” do campo “/data/recurringConfiguration/”), apenas os métodos MANU, DICT e INIC são permitidos.  

get/responses/200/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

get/responses/200/data/paymentReference

Removido - "maxLength"

Remoção

10

get/responses/200/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detentora deve retornar erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.

-   Primeiro pagamento: Se for o pagamento inicial especificado em “/data/firstPayment”, preencha o campo com a string fixa “zero”.
    
-   Semanal: Preencha com W$numSemana-$ano, onde $numSemana representa o número da semana no ano. Exemplo: "W50-2024".
    
-   Mensal: Use M$mês-$ano, onde $mês representa o mês com dois dígitos. Exemplo: "M09-2024".
    
-   Trimestral: Utilize Q$trimestre-$ano, onde $trimestre indica o trimestre do ano (1 a 4).
    
-   Janeiro a Março: Q1-$ano (ex.: "Q1-2024").
    
-   Abril a Junho: Q2-$ano (ex.: "Q2-2024").
    
-   Julho a Setembro: Q3-$ano (ex.: "Q3-2024").
    
-   Outubro a Dezembro: Q4-$ano (ex.: "Q4-2024").
    
-   Semestral: Utilize $semestre-$ano, onde $semestre indica o semestre do ano (1 para janeiro a junho e 2 para julho a dezembro).
    
-   Janeiro a Junho: S1-$ano (ex.: "S1-2024").
    
-   Julho a Dezembro: S2-$ano (ex.: "S2-2024").
    
-   Anual: Use Y$ano, apenas com o ano. Exemplo: "Y2024".
    
-   Exemplo de Formatos:
    
-   Primeiro pagamento: "zero"
    
-   Semanal: "W50-2024"
    
-   Mensal: "M09-2024"
    
-   Trimestral: "Q3-2024"
    
-   Semestral: "S2-2024"
    
-   Anual: "Y2024"
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de início do ciclo específico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

get/responses/200/data/paymentReference

Adicionado - "example"

Adição

R/2025-09-23/P1M

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
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

get/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo “localInstrument”:

MANU - O campo transactionIdentification não deve ser preenchido;   
DICT - O campo transactionIdentification não deve ser preenchido;   
INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]).  

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo localInstument: 

-   MANU - O campo transactionIdentification não deve ser preenchido; 
    
-   DICT - O campo transactionIdentification não deve ser preenchido; 
    
-   INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]); 
    
-   AUTO – O campo transactionIdentification não deve ser preenchido.
    

  

## PATCH /pix/recurring-payments/{recurringPaymentId}

### request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch

Alterado - "description"

Alteração

Esse endpoint deve ser usado para cancelar as transações que estejam em uma das seguintes situações:  
Agendada com sucesso (SCHD), retida para análise (PDNG). Caso a requisição seja bem sucedida, a transação vai para a situação CANC.

Caso o status do pagamento seja diferente de SCHD/PDNG ou alguma outra regra de negócio impeça o cancelamento, a requisição PATCH retorna  
HTTP Status 422 com o code PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO.

Caso receba um 422, a iniciadora deve fazer uma requisição GET no pagamento para verificar a situação atual dele, bem como detalhes associados.

\[Restrição\] Para o Pix automático (“recurringConfiguration” igual a “automatic”) tanto o recebedor quanto o pagador poderão realizar o cancelamento,  
sendo permitido ao recebedor a solicitação de cancelamento até as 22:00 (Horário de Brasília) e ao pagador até as 23:59 (Horário de Brasília) do dia anterior à data de efetivação do pagamento,  
exceto para os casos de novas tentativas em dias subsequentes, onde apenas o recebedor pode cancelar, também até as 22:00h.  

Esse endpoint deve ser usado para cancelar as transações que estejam em uma das seguintes situações:   
Agendada com sucesso (SCHD), retida para análise (PDNG). Caso a requisição seja bem sucedida, a transação vai para a situação CANC.

Caso o status do pagamento seja diferente de SCHD/PDNG ou alguma outra regra de negócio impeça o cancelamento, a requisição PATCH retorna  
HTTP Status 422 com o code PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO.

Caso receba um 422, a iniciadora deve fazer uma requisição GET no pagamento para verificar a situação atual dele, bem como detalhes associados.

\[Restrição\] Para o Pix automático (“recurringConfiguration” igual a “automatic”) tanto o recebedor quanto o pagador poderão realizar o cancelamento,  
sendo permitido ao recebedor a solicitação de cancelamento até as 22:00 (Horário de Brasília) e ao pagador até as 23:59 (Horário de Brasília) do dia anterior à data de efetivação do pagamento,  
exceto para os casos de novas tentativas em dias subsequentes, onde apenas o recebedor pode cancelar, também até as 22:00h.  

patch/requestBody/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/data/cancellation/cancelledBy/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/cnpjInitiator

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

patch/responses/200/data/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/endToEndId

Alterado - "pattern"

Alteração

^(\[E\])(\[0-9\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

^(\[E\])(\[0-9A-Z\]{8})(\[0-9\]{4})(0\[1-9\]|1\[0-2\])(0\[1-9\]|\[1-2\]\[0-9\]|3\[0-1\])(2\[0-3\]|\[01\]\[0-9\])(\[0-5\]\[0-9\])(\[a-zA-Z0-9\]{11})$

patch/responses/200/data/localInstrument

Alterado - "description"

Alteração

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    

\[Restrição\] Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration"), apenas o método MANU é permitido.  

Especifica a forma de iniciação do pagamento

-   MANU - Inserção manual de dados da conta transacional
    
-   DICT - Inserção manual de chave Pix
    
-   INIC - Indica que o recebedor (creditor) contratou o Iniciador de Pagamentos especificamente para realizar iniciações de pagamento em que o beneficiário é previamente conhecido
    
-   AUTO - Indica o pagamento de uma recorrência de Pix automático, onde o consentimento foi previamente autorizado pelo pagador e o pagamento é realizado automaticamente pelo Iniciador de Pagamentos sob comando do recebedor.
    

\[Restrição\]   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou;   
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido.   
Para consentimentos de Transferências Inteligentes (objeto “sweeping” selecionado no “oneOf” do campo “/data/recurringConfiguration/”), apenas os métodos MANU, DICT e INIC são permitidos.  

patch/responses/200/data/localInstrument/enum

Adicionado - "AUTO"

Adição

enum

patch/responses/200/data/paymentReference

Removido - "maxLength"

Remoção

10

patch/responses/200/data/paymentReference

Alterado - "description"

Alteração

\[Restrição\]  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático, caso não respeitado, a instituição detentora deve retornar erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.

-   Primeiro pagamento: Se for o pagamento inicial especificado em “/data/firstPayment”, preencha o campo com a string fixa “zero”.
    
-   Semanal: Preencha com W$numSemana-$ano, onde $numSemana representa o número da semana no ano. Exemplo: "W50-2024".
    
-   Mensal: Use M$mês-$ano, onde $mês representa o mês com dois dígitos. Exemplo: "M09-2024".
    
-   Trimestral: Utilize Q$trimestre-$ano, onde $trimestre indica o trimestre do ano (1 a 4).
    
-   Janeiro a Março: Q1-$ano (ex.: "Q1-2024").
    
-   Abril a Junho: Q2-$ano (ex.: "Q2-2024").
    
-   Julho a Setembro: Q3-$ano (ex.: "Q3-2024").
    
-   Outubro a Dezembro: Q4-$ano (ex.: "Q4-2024").
    
-   Semestral: Utilize $semestre-$ano, onde $semestre indica o semestre do ano (1 para janeiro a junho e 2 para julho a dezembro).
    
-   Janeiro a Junho: S1-$ano (ex.: "S1-2024").
    
-   Julho a Dezembro: S2-$ano (ex.: "S2-2024").
    
-   Anual: Use Y$ano, apenas com o ano. Exemplo: "Y2024".
    
-   Exemplo de Formatos:
    
-   Primeiro pagamento: "zero"
    
-   Semanal: "W50-2024"
    
-   Mensal: "M09-2024"
    
-   Trimestral: "Q3-2024"
    
-   Semestral: "S2-2024"
    
-   Anual: "Y2024"
    

  

\[Restrição\] Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.   
O preenchimento deve seguir a seguinte lógica: 

-   Primeiro Pagamento: Se for o pagamento inicial especificado no campo /data/firstPayment, preencha o campo com a string fixa "zero". 
    
-   Pagamentos Recorrentes (Subsequentes): Para todos os pagamentos recorrentes após o inicial, o campo paymentReference deve ser preenchido com uma string ISO 8601 no formato \`\`\`R/<start>/<duration>\`\`\`, representando o ciclo exato que está sendo pago. 
    
-   \`\`\`R\`\`\`, seguindo o padrão ISO8601 para representar a recorrência única do ciclo que se iniciou no dia informado no componente \`\`\`<start>\`\`\`. 
    
-   O componente \`\`\`<start>\`\`\` deve ser a data de início do ciclo específico, no formato \`\`\`YYYY-MM-DD\`\`\`, ao qual o pagamento sendo enviado se refere.   
    
-   O componente \`\`\`<duration>\`\`\` representa o intervalo de ciclos definido para o consentimento autorizado (P1W para semanal, P1M para mensal, P3M para trimestral, P6M para semestral e P1Y para anual).  
    
-   Exemplos:
    
-   1: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Semanal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1W
    
-   Segundo ciclo:  R/2025-07-30/P1W
    
-   Terceiro ciclo: R/2025-08-06/P1W
    
-   2: Data de início do ciclo definido no consentimento: 23/07/25
    
-   Periodicidade definida no consentimento: Mensal
    
-   Preenchimento do paymentReference:
    
-   Primeiro ciclo: R/2025-07-23/P1M
    
-   Segundo ciclo: R/2025-08-23/P1M
    
-   Terceiro ciclo: R/2025-09-23/P1M
    

  

patch/responses/200/data/paymentReference

Adicionado - "example"

Adição

R/2025-09-23/P1M

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
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: Valida se o valor ultrapassa o limite estabelecido \[na instituição (conta ou canal)/no arranjo\] para permitir a realização de transações pelo cliente;
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o consentimento associado ao pagamento;
    
-   NAO\_INFORMADO: Não reportado/identificado pela instituição detentora de conta;
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento;
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: \[descrição do motivo de recusa\];
    
-   PAGAMENTO\_RECUSADO\_SPI: \[código de erro conforme tabela de domínios reason PACS.002\];
    
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
    
-   FORA\_PRAZO\_PERMITIDO: O horário ou período da requisição não permite o agendamento pelo detentor.
    
-   DETALHE\_TENTATIVA\_INVALIDO: O parâmetro \[nome\_do(s)\_campo(s)\] inseridos para a nova tentativa de pagamento não condizem com o pagamento original que falhou e não são permitidos na nova tentativa de pagamento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Valida se determinado parâmetro informado obedece as regras de negócio.
    

  

patch/responses/200/data/transactionIdentification

Alterado - "description"

Alteração

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo “localInstrument”:

MANU - O campo transactionIdentification não deve ser preenchido;   
DICT - O campo transactionIdentification não deve ser preenchido;   
INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]).  

Trata-se de um identificador de transação que deve ser retransmitido intacto pelo PSP do pagador ao gerar a ordem de pagamento.  
Essa informação permitirá ao recebedor identificar e correlacionar a transferência, quando recebida, com a apresentação das instruções ao pagador.  
Os caracteres permitidos no contexto do Pix para o campo txid (EMV 62-05) são:Letras minúsculas, de 'a' a 'z' Letras maiúsculas, de 'A' a 'z' Dígitos decimais, de '0' a '9'.

\[Restrição\] Preenchimento condicional de acordo com o conteúdo do campo localInstument: 

-   MANU - O campo transactionIdentification não deve ser preenchido; 
    
-   DICT - O campo transactionIdentification não deve ser preenchido; 
    
-   INIC - O campo transactionIdentification deve ser preenchido obrigatoriamente e deve conter até 25 caracteres alfanuméricos (\[a-z|A-Z|0-9\]); 
    
-   AUTO – O campo transactionIdentification não deve ser preenchido.
    

  

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

post/requestBody/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/requestBody/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/requestBody/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/data/loggedUser" e "/data/businessEntity".

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/requestBody/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência.  
Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).  

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data.  

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/properties

Adicionado - "journey"

Adição

post/responses/201/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

post/responses/201/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/data/loggedUser" e "/data/businessEntity".

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

post/responses/201/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência.  
Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).  

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data.  

post/responses/201/data/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

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
    
-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
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

post/responses/201/data/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

post/responses/201/data/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

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
    
-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor ultrapassa o limite estabelecido para permitir a realização de transações pelo cliente;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
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

get/responses/200/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/data/loggedUser" e "/data/businessEntity".

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência.  
Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).  

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data.  

get/responses/200/data/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

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
    
-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
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

get/responses/200/data/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

get/responses/200/data/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

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
    
-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor ultrapassa o limite estabelecido para permitir a realização de transações pelo cliente;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
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

-   Caso bem sucedido, o consentimento vai para o status “REVOKED”;
    
-   Apenas consentimentos com status “AUTHORISED” podem ser revogados;
    
-   Pagamentos automáticos associados ao consentimento e que estão agendados para ocorrer até as 23:59h do próximo dia (a partir do dia de
    

  
solicitação da revogação) deverão ser mantidos. Pagamentos agendados para ocorrer após esse período devem ser cancelados.

-   Demais orientações referentes a revogação podem ser encontrados no header da API, tópico “Validações”, item 3.
    

2 - Informações sobre a edição:

-   Os campos que são passíveis de edição e suas regras podem ser encontrados através do \[link\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/628195665);
    
-   A edição é possível apenas em casos de consentimento para Pix Automático (“automatic” escolhido no oneOf do objeto “recurringConfiguration”);
    
-   O envio do item "/data/creditors/name" atualizará o nome do recebedor em todos os elementos do array.
    
-   Caso consentimento seja de valor fixo (campo “/data/recurringConfiguration/automatic/fixedAmount” preenchido) não é permitida a edição do campo “/data/recurringConfiguration/automatic/maximumVariableAmount”.
    
-   Caso o recebedor tenha definido um piso para o limite a ser estipulado pelo pagador (campo “/data/recurringConfiguration/automatic/minimumVariableAmount” preenchido), o valor máximo de limite por transação definido pelo usuário pagador (campo “/data/recurringConfiguration/automatic/maximumVariableAmount”) não pode ser menor que o valor estipulado pelo recebedor.
    
-   Caso o seja editado o prazo de expiração do consentimento e já existam pagamentos agendados para dias posteriores a nova data definida, estes pagamentos devem ser cancelados.
    

3 - Informações sobre a rejeição: 

-   Caso haja necessidade de cancelamento de um consentimento ainda não autorizado, o iniciador poderá chamar o endpoint para mover o consentimento para REJECTED.
    

  

Método para rejeitar, revogar ou editar um consentimento de longa duração:   
1 - Informações sobre a revogação:

-   Caso bem sucedido, o consentimento vai para o status “REVOKED”;
    
-   Apenas consentimentos com status “AUTHORISED” podem ser revogados;
    
-   Caso a revogação seja realizada pelo recebedor entre 22:00h até 23:59h: Pagamentos automáticos associados ao consentimento e que estão agendados para ocorrer até as 23:59h do próximo dia (a partir do dia de solicitação da revogação) deverão ser mantidos. Pagamentos agendados para ocorrer após esse período devem ser cancelados.
    
-   Caso a revogação seja realizada pelo recebedor até as 22:00h ou pelo usuário pagador até as 23:59h: Pagamentos automáticos associados ao consentimento e que estão agendados para ocorrer até as 23:59h do próximo dia (apartir do dia de solicitação da revogação) deverão ser cancelados
    
-   Demais orientações referentes a revogação podem ser encontrados no header da API, tópico “Validações”, item 3.
    

2 - Informações sobre a edição:

-   Os campos que são passíveis de edição e suas regras podem ser encontrados através do \[link\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/628195665);
    
-   A edição é possível apenas em casos de consentimento para Pix Automático (“automatic” escolhido no oneOf do objeto “recurringConfiguration”) e que encontrem-se autorizados (\`data.status == AUTHORISED\`);
    
-   O envio do item "/data/creditors/name" atualizará o nome do recebedor em todos os elementos do array.
    
-   Caso consentimento seja de valor fixo (campo “/data/recurringConfiguration/automatic/fixedAmount” preenchido) não é permitida a edição do campo “/data/recurringConfiguration/automatic/maximumVariableAmount”.
    
-   Caso o recebedor tenha definido um piso para o limite a ser estipulado pelo pagador (campo “/data/recurringConfiguration/automatic/minimumVariableAmount” preenchido), o valor máximo de limite por transação definido pelo usuário pagador (campo “/data/recurringConfiguration/automatic/maximumVariableAmount”) não pode ser menor que o valor estipulado pelo recebedor.
    
-   Caso o seja editado o prazo de expiração do consentimento e já existam pagamentos agendados para dias posteriores a nova data definida, estes pagamentos devem ser cancelados.
    

3 - Informações sobre a rejeição: 

-   Caso haja necessidade de cancelamento de um consentimento ainda não autorizado, o iniciador poderá chamar o endpoint para mover o consentimento para REJECTED.
    

  

patch/requestBody/data/oneOf/0/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

patch/requestBody/data/oneOf/0/creditors/items

Alterado - "description"

Alteração

Objeto contendo os dados do recebedor (creditor).

 \*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

 \*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica.
    

  

Objeto contendo os dados do recebedor (creditor).

 \*\*Regras para Transferências inteligentes:\*\*

1.  Para clientes pessoa física/natural:
    

-   Deve aceitar apenas um item no array; e;
    
-   O CPF informado deve ser o mesmo do \`/data/loggedUser/document/identification\`.
    

2.  Para clientes pessoa jurídica:
    

-   Não há limite para quantidade de itens no array; e;
    
-   O(s) CNPJ informado deve possuir a mesma raiz do CNPJ enviado no campo \`/data/businessEntity/document/identification\`.
    

 \*\*Regras para Pix Automático:\*\*

-   Apenas um item é permitido no array; e;
    
-   O documento informado deve ser de um recebedor pessoa jurídica. 
    

 \*\*Informar apenas esse item não deve alterar nenhum outro parâmetro do consentimento\*\*  

patch/requestBody/data/oneOf/0/expirationDateTime

Alterado - "description"

Alteração

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um período indeterminado; ou;

Caso enviado, esse campo deve ser, no mínimo, D, sendo D o dia da requisição e o horário deve ser às 23:59:59 (UTC).  

Data e hora em que o consentimento deve deixar de ser válido. Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format). 

\[Restrição\] Caso esse campo não seja enviado, a instituição detentora deve considerar a extensão do prazo para um período indeterminado exceto em casos de edição exclusiva do campo “/data/creditors/name; ou; 

Caso enviado, esse campo deve ser, no mínimo, D, sendo D o dia da requisição e o horário deve ser às 23:59:59 (UTC).  

patch/requestBody/data/oneOf/0/recurringConfiguration/automatic/maximumVariableAmount

Alterado - "description"

Alteração

Valor máximo permitido por cobrança, caso preenchido, representa um consentimento para pagamentos de valores variáveis.

\[Restrição\]  
Caso esse campo não seja enviado, a instituição detentora deve considerar o valor máximo do pagamento variável como indefinido;

Caso informado, o valor desse campo não deve ser inferior ao valor definido no campo "/data/recurringConfiguration/automatic/minimumVariableAmount".  

Valor máximo permitido por cobrança, caso preenchido, representa um consentimento para pagamentos de valores variáveis.

\[Restrição\]  
Caso esse campo não seja enviado, a instituição detentora deve considerar o valor máximo do pagamento variável como indefinido, exceto em casos de edição exclusiva do campo “/data/creditors/name”;

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

2020-05-21

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
Este campo poderá ser omitido caso o GPS esteja indisponível, isto é, sem sinal, ou em dispositivos sem o hardware necessário; ou caso o usuário negue o consentimento para coleta do dado.  

Localização do usuário, obtida com seu consentimento.  
\[Android\] Informação obtida através do \[link\](https://developers.google.com/android/reference/com/google/android/gms/location/FusedLocationProviderClient#public-abstract-tasklocation-getlastlocation) considerando as permissões necessárias.   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/corelocation/).   
\[Restrição\] A ITP deve solicitar ao usuário a permissão para compartilhamento de sua localização. Este campo poderá ser omitido caso o GPS esteja indisponível, isto é, sem sinal, ou em dispositivos sem o hardware necessário; ou caso o usuário negue o consentimento.  

patch/requestBody/data/oneOf/0/riskSignals/geolocation/latitude

Adicionado - "example"

Adição

\-15.738602

patch/requestBody/data/oneOf/0/riskSignals/geolocation/longitude

Adicionado - "example"

Adição

\-47.926498

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

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/location/Location.html#isMock()) ou, para versões anteriores à 12, \[link\](https://developer.android.com/reference/android/location/Location.html#isFromMockProvider()).

\[iOS\] Informação obtida através dos links: sourceInformation, \[link\](https://developer.apple.com/documentation/corelocation/cllocation/3861803-sourceinformation). isSimulatedBySoftware, \[link\](https://developer.apple.com/documentation/corelocation/cllocationsourceinformation/3861807-issimulatedbysoftware).  

Indica se o dispositivo está usando um GPS falso. Deve ser enviado sempre que exista o campo geolocation com tipo \`COARSE\` ou \`FINE\`.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/location/Location.html#isMock()) ou, para versões anteriores à 12, \[link\](https://developer.android.com/reference/android/location/Location.html#isFromMockProvider()).   
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

Indica se o dispositivo atualmente está com permissão de “root”.

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário for Android ou iOS.  

Indica se o dispositivo atualmente está com permissão de “root”.    
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

Indica o nível de brilho da tela do dispositivo.

\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).

\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/kernel/kern/).

\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo for Android ou iOS.  

Indica o nível de brilho da tela do dispositivo.    
\[Android\] O valor é inteiro, tipicamente entre 0 a 255, podendo a faixa de valores variar de acordo com o fabricante do celular. Referência no \[link\](https://developer.android.com/reference/android/provider/Settings.System#SCREEN\_BRIGHTNESS).    
\[iOS\] O valor é ponto flutuante entre “0.0” e “1.0”. Referência no \[link\](https://developer.apple.com/documentation/uikit/uiscreen/).    
\[Restrição\] Campos de envio obrigatório quando o sistema operacional utilizado pelo usuário durante a vinculação de conta ou realização do pagamento for Android ou iOS.  

patch/requestBody/data/oneOf/0/riskSignals/screenDimensions

Alterado - "description"

Alteração

Dimensões que o aplicativo ocupa na tela do dispositivo.

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/view/WindowMetrics#getBounds()), ou, para versões anteriores à 11, \[link\](https://developer.android.com/reference/android/util/DisplayMetrics).

\[iOS\] - Informação obtida através do \[link\](https://developer.apple.com/documentation/metal/mtlrasterizationratemap/3088873-screensize/).  

Dimensões que o aplicativo ocupa na tela do dispositivo.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/android/view/WindowMetrics#getBounds()), ou, para versões anteriores à 11, \[link\](https://developer.android.com/reference/android/util/DisplayMetrics).   
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

\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/time/ZonedDateTime#getOffset()) ou, para versões anteriores à 8.0, \[link\](https://developer.android.com/reference/java/util/TimeZone#getOffset(long)).

\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/timezone/).  

Indica a configuração de fuso horário do dispositivo do usuário, com o formato UTC offset: ±hh\[:mm\]. O formato especificado permite a omissão da parte correspondente aos minutos, caso esta última tenha valor zero. Assim, ambos os valores '-03:00' e '-03' são válidos e representam o mesmo fuso horário.   
\[Android\] Informação obtida através do \[link\](https://developer.android.com/reference/java/time/ZonedDateTime#getOffset()) ou, para versões anteriores à 8.0, \[link\](https://developer.android.com/reference/java/util/TimeZone#getOffset(long)).   
\[iOS\] Informação obtida através do \[link\](https://developer.apple.com/documentation/foundation/timezone/).  

patch/requestBody/data/oneOf/0/riskSignals/userTimeZoneOffset

Adicionado - "example"

Adição

\-03

patch/requestBody/data/oneOf/2/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

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
    
-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
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

patch/requestBody/data/oneOf/2/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

patch/requestBody/data/oneOf/2/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

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
    
-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor ultrapassa o limite estabelecido para permitir a realização de transações pelo cliente;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
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

patch/responses/200/data/businessEntity/document/identification

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

patch/responses/200/data/creditors/items/cpfCnpj

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/debtorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor

Alterado - "description"

Alteração

Informações sobre o cliente devedor do contrato.

Informações sobre o cliente devedor do contrato. Pode possuir titularidade diferente do usuário pagador descrito nos objetos "/data/loggedUser" e "/data/businessEntity".

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractDebtor/document/identification

Alterado - "pattern"

Alteração

^(?:\\d{11}|\\d{14})$

^(\[0-9\]{11})$|^(\[0-9A-Z\]{12}\[0-9\]{2})$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/contractId

Alterado - "description"

Alteração

Identificador do contrato de transação

Identificador do contrato do cliente localizado no ambiente do recebedor. Essa informação pode ser fornecida pelo recebedor ou gerada pela ITP durante a criação do consentimento (se previsto em acordo com o recebedor).  

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/firstPayment/creditorAccount/ispb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

patch/responses/200/data/recurringConfiguration/oneOf/0/automatic/referenceStartDate

Alterado - "description"

Alteração

Representa a data prevista para a primeira ocorrência de um pagamento associado a recorrência.  
Uma string com data e hora conforme especificação \[RFC-3339\](https://datatracker.ietf.org/doc/html/rfc3339), sempre com a utilização de timezone UTC(UTC time format).  

Representa a data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data.  

patch/responses/200/data/rejection/reason/code

Alterado - "example"

Alteração

VALOR\_ACIMA\_LIMITE

AUTENTICACAO\_DIVERGENTE

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
    
-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
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

patch/responses/200/data/rejection/reason/code/enum

Removido - "SALDO\_INSUFICIENTE"

Remoção

enum

patch/responses/200/data/rejection/reason/code/enum

Removido - "VALOR\_ACIMA\_LIMITE"

Remoção

enum

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
    
-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor ultrapassa o limite estabelecido para permitir a realização de transações pelo cliente;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    

  

Detalhe sobre o motivo de rejeição indicado no campo \`/data/rejection/reason/code\`

-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\];
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento;
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento;
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento;
    
-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador;
    
-   FLUXO\_NAO\_SUPORTADO\_PRODUTO: O consentimento está configurado para um produto ainda não suportado pela Jornada sem Redirecionamento.
