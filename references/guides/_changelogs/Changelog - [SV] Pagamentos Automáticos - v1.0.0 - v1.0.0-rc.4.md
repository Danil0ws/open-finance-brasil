# Changelog - [SV] Pagamentos Automáticos - v1.0.0 - v1.0.0-rc.4

**A implementação e certificação do VRP está pausada no momento. Os produtos Transferência Inteligentes (Sweeping Accounts) e Pix Automático continuam disponíveis para implementação e certificação.**

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

Alterado - "description"

Alteração

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix automático e Transferências Inteligentes) para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos endpoints dedicados ao consentimento nesta API.

\# Orientações

-   \`CONTA\`, referente às instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente às instituições iniciadoras de pagamento participantes do Open Finance Brasil.
    

Os tokens utilizados para consumo nos endpoints de consentimentos devem possuir o scope recurring-payments e os endpoints de pagamentos recorrentes devem possuir os scopes openid e recurring-payments.  
Esta API não requer a implementação de permissions para sua utilização.  
Todas as requisições e respostas devem ser assinadas seguindo o protocolo estabelecido na sessão Assinaturas do guia de segurança.

\## Orientações gerais sobre os consentimentos de pagamentos automáticos

-   Duração e reutilização do consentimento: A utilização das credenciais geradas a partir de uma autorização de um consentimento recorrente deve durar até que o consentimento recorrente atinja o fim do seu ciclo de vida, conforme detalhado na sua \[máquina de estados\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/198410647).
    
-   Credenciais: As credenciais (authorization\_code) geradas na autorização do consentimento devem ser utilizadas para criação dos pagamentos subsequentes utilizando o mecanismo de refresh, caso necessário. Maiores informações através do link \[\[PT\] Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3 - Área do Desenvolvedor -Open Finance Brasil - Área do Desenvolvedor ([atlassian.net](http://atlassian.net))\]([https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82051180/PT+Open+Finance+Brasil+Financial-grade+API+Security+Profile+1.0+Implementers+Draft+3#7.2.2.-Servidor-de-autorização](data/references/guides/PT.md))
    

\## Regras do arranjo Pix  
A implementação e o uso da API de Pagamentos Automáticos (Pix) devem seguir as regras do arranjo Pix do Banco Central, que podem ser encontradas no link abaixo:   
\[Banco Central do Brasil\]([https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao\_pix](https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao_pix))

\## Assinatura de payloads  
No contexto da API de Pagamentos Automáticos, os payloads de mensagem que trafegam tanto por parte da instituição iniciadora de transação de pagamento quanto por parte da instituição detentora de conta devem estar assinados.  
Para o processo de assinatura destes payloads, as instituições devem seguir as especificações de segurança publicadas no Portal do desenvolvedor.

\## Controle de acesso

-   Os endpoints de consulta de pagamentos GET /pix/recurring-payments/{recurringPaymentId} e GET /pix/recurring-payments devem suportar acesso a partir de access\_token emitido por meio de um grant\_type do tipo client credentials, como opção do uso do token vinculado ao consentimento (hybrid flow).
    
-   Para evitar vazamento de informação, a detentora deve validar que o pagamento consultado pertence ao ClientId que o criou e, caso haja divergências, retorne um erro HTTP 400.
    

\## Aprovações de múltipla alçada

Todas as aprovações devem ser realizadas até a data/hora limite suportada pela detentora e em tempo hábil para realizar o primeiro pagamento.

\## Validações da edição do consentimento recorrente para o produto Pix Automático

Para permitir a edição dos campos de um consentimento na iniciadora sem que se faça necessário o redirecionamento para o  
ambiente da detentora de conta, é necessário o envio de indicadores de risco.  
Esta medida visa proporcionar à detentora de conta as informações necessárias para decidir sobre os ajustes no consentimento de forma segura

\## Validações

Durante a jornada de iniciação de pagamento, diferentes validações são necessárias pela instituição detentora de conta e devem ocorrer conforme a seguir:

1.  \*\*Validações na criação do consentimento de longa duração (\_POST /recurring-consents\_)\*\* 
    

  1.1 \*\*Orientações Iniciais\*\*   
    &ensp;1.1.1 Não devem ser retornadas na resposta deste endpoint informações associadas ao usuário/cliente (ex. insuficiência de saldo, conta inexistente/bloqueada).   
    &ensp;1.1.2 Não devem ser realizadas validações de informações sobre o usuário/cliente durante a criação do consentimento.   
  1.2 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;1.2.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;1.2.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;1.2.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;1.2.4 Validação de Claims (exceto data);   
      &emsp;1.2.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;1.2.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  1.3 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*    
    &ensp;1.3.1 \*\*Sintáticos\*\*   
      &emsp;1.3.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios foram informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;1.3.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;1.3.2 \*\*Semânticos\*\*   
      &emsp;1.3.2.1 Data de pagamento: Valida se a data de pagamento enviada é válida para a forma de pagamento selecionada (DATA\_PAGAMENTO\_INVALIDA);   
      &emsp;1.3.2.2 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;1.3.2.3 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;1.3.2.4 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA);   
      &emsp;1.3.2.5 Funcionalidade não habilitada: A detentora de conta não oferece o serviço nessa modalidade (FUNCIONALIDADE\_NAO\_HABILITADA). 

1.  \*\*Demais validações executadas durante o processamento assíncrono do consentimento pela detentora poderão ser consultados pela iniciadora através do endpoint GET /recurring-consents/{recurringConsentId} previstos com retorno HTTP Code 200 – OK com status REJECTED e rejectionReason conforme abaixo:\*\* 
    

  2.1 \*\*Validações durante o processamento assíncrono do consentimento\*\*   
    &ensp;2.1.1 Falha de infraestrutura: Ocorreu algum erro interno na detentora durante processamento da criação do consentimento (FALHA\_INFRAESTRUTURA);   
    &ensp;2.1.2 Tempo de autorização expirado: O usuário não confirmou o consentimento e o mesmo expirou (TEMPO\_EXPIRADO\_AUTORIZACAO);   
    &ensp;2.1.3 Rejeitado pelo usuário: O usuário explicitamente rejeitou a autorização do consentimento (REJEITADO\_USUARIO);   
    &ensp;2.1.4 Mesma conta origem/destino: A conta indicada pelo usuário para recebimento é a mesma selecionada para o pagamento (CONTAS\_ORIGEM\_DESTINO\_IGUAIS);   
    &ensp;2.1.5 Tipo de conta inválida: A conta indicada não permite operações de pagamento (CONTA\_NAO\_PERMITE\_PAGAMENTO);   
    &ensp;2.1.6 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
    &ensp;2.1.7 Limites da transação: Valida se o valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente (VALOR\_ACIMA\_LIMITE); 

1.  \*\*Demais validações executadas durante o processamento assíncrono do consentimento pela detentora, poderão ser consultados pela iniciadora através dos endpoints GET /recurring-consents/{recurringConsentId} previstos com retorno HTTP Code 200 - OK com status REVOKED e revocationReason conforme abaixo (detalhamento adicional na documentação técnica da API).\*\* 
    

  3.1 \*\*Demais validações durante o processamento assíncrono:\*\*   
    &ensp;3.1.1 Nao informado: Validações não explicitamente informadas (ex. suspeita de fraude) (NAO\_INFORMADO);   
    &ensp;3.1.2 Revogado pelo recebedor: O usuário recebedor solicitou explicitamente ao iniciador a revogação do consentimento (ex: término de contrato) (REVOGADO\_RECEBEDOR);   
    &ensp;3.1.3 Revogado pelo pagador: O usuário pagador solicitou explicitamente a revogação do consentimento (REVOGADO\_USUARIO). 

1.  \*\*Validações na criação do pagamento - Síncrono (\_POST /pix/recurring-payments\_)\*\* 
    

  4.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;4.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;4.1.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;4.1.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;4.1.4 Validação de Claims (exceto data);   
      &emsp;4.1.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;4.1.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  4.2 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*   
    &ensp;4.2.1 Sintáticos   
      &emsp;4.2.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios são informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;4.2.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;4.2.2 Semânticos   
      &emsp;4.2.2.1 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
      &emsp;4.2.2.2 Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora na conta do cliente pagador (VALOR\_ACIMA\_LIMITE);   
      &emsp;4.2.2.3 Valor informado: Valida se valor enviado é válido para o consentimento associado ao pagamento (VALOR\_INVALIDO);   
      &emsp;4.2.2.4 Status Consentimento: Valida se status de consentimento é diferente de “AUTHORISED” (CONSENTIMENTO\_INVALIDO);   
      &emsp;4.2.2.5 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;4.2.2.6 Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO)   
      &emsp;4.2.2.7 Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa;   
      &emsp;4.2.2.8 Detalhes do pagamento: Valida se determinado parâmetro informado obedece as regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;4.2.2.9 Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI) (PAGAMENTO\_RECUSADO\_SPI);   
      &emsp;4.2.2.10 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA);   
      &emsp;4.2.2.11 Limite valor excedido por período: Foi atingido o valor limite permitido pelo usuário por um determinado período de tempo no consentimento do pagamento (LIMITE\_PERIODO\_VALOR\_EXCEDIDO);   
      &emsp;4.2.2.12 Limite quantidade excedida por período: A quantidade de cobranças atingiu o limite determinado pelo usuário na criação do consentimento (LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO). 

1.  \*\*Validações na consulta do pagamento (\_GET /pix/recurring-payments/{recurringPaymentId}\_ e \_GET /pix/recurring-payments\_)\*\* 
    

  5.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token)\*\*   
    &ensp;5.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;5.1.2 Validações de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED).

1.  \*\*Demais validações executadas durante o processamento assíncrono do pagamento pela detentora, poderão ser consultados pela iniciadora através dos endpoints \_GET /pix/recurring-payments/{recurringPaymentId}\_ e \_GET /pix/recurring-payments\_ previstos com retorno HTTP Code 200 - OK com status RJCT (Rejected) e rejectionReason conforme abaixo (detalhamento adicional na documentação técnica da API):\*\* 
    

  6.1 \*\*Demais validações durante o processamento assíncrono:\*\*   
    &ensp;6.1.1 - Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
    &ensp;6.1.2 - Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora (VALOR\_ACIMA\_LIMITE);   
    &ensp;6.1.3 - Valor informado: Valida se valor enviado é válido para o consentimento do pagamento (VALOR\_INVALIDO);   
    &ensp;6.1.4 - Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
    &ensp;6.1.5 - Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO);   
    &ensp;6.1.6 - Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa;   
    &ensp;6.1.7 - Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI) (PAGAMENTO\_RECUSADO\_SPI);   
    &ensp;6.1.8 - Erro de infraestrutura na consulta ao SPI: Ocorreu uma falha de infraestrutura durante a consulta ao SPI(FALHA\_INFRAESTRUTURA\_SPI);   
    &ensp;6.1.9 - Erro de infraestrutura na consulta ao ICP: Ocorreu uma falha de infraestrutura durante a consulta ao ICP (FALHA\_INFRAESTRUTURA\_ICP);   
    &ensp;6.1.10 - Erro de infraestrutura na comunicação com o PSP do recebedor: Ocorreu uma falha de infraestrutura durante a comunicação com o PSP do recebedor (FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR);   
    &ensp;6.1.11 - Erro de infraestrutura interno na detentora: Ocorreu uma falha de infraestrutura interna na detentora durante o processamento do pagamento (FALHA\_INFRAESTRUTURA\_DETENTORA);   
    &ensp;6.1.12 - Status Consentimento: Valida se status de consentimento é diferente de “AUTHORISED” (CONSENTIMENTO\_INVALIDO);   
    &ensp;6.1.13 - Limite valor excedido por período: Foi atingido o valor limite permitido pelo usuário por um determinado período de tempo no consentimento do pagamento (LIMITE\_PERIODO\_VALOR\_EXCEDIDO);   
    &ensp;6.1.14 - Limite quantidade excedida por período: A quantidade de cobranças atingiu o limite determinado pelo usuário na criação do consentimento (LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO).   
    &ensp;6.1.15 - Titularidade Inconsistente: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração. Caso a liquidação seja negada pelo PSP Recebedor com erro BE01, cabe a detentora de conta mudar o status do pagamento para RJCT com essa reason (TITULARIDADE\_INCONSISTENTE) 

\## Validações antifraude da Transferências Inteligentes

-   Afim de garantir a mesma titularidade e aumentar a segurança das transações do produto Transferências Inteligentes, as validações abaixo poderão ser realizadas pela detetora de conta e pela iniciadora, quando localinstrument for igual a DICT ou INIC. A detentora PODE usar a API Consultar Vinculo (DICT API) do arranjo Pix e validar no momento de transação ao menos os atributos abaixo mencionados:
    
-   se o valor dos atributos de fraude abaixo são iguais a 0, de modo a evitar que contas criadas especificamente para uso indevido da Transferências Inteligentes impactem o ecossistema
    
-   OwnerStatistics.Spi.FraudMarkers.ApplicationFrauds.d90
    
-   OwnerStatistics.Spi.FraudMarkers.MuleAccounts.d90
    
-   OwnerStatistics.Spi.FraudMarkers.ScammerAccounts.d90
    
-   OwnerStatistics.Spi.FraudMarkers.OtherFrauds.d90
    
-   OwnerStatistics.Spi.FraudMarkers.UnknownFrauds.d90
    

\## Limites transacionais para Transferências Inteligentes

-   As transferências inteligentes são categorizadas como um Pix Imediato entre diferentes contas de mesma titularidade. Sendo assim, a tratativa a ser dada aos limites definidos no consentimento desse produto devem ser as mesmas que a instituição aplica para os limites do arranjo Pix.
    
-   O cálculo do limite periódico disponível ao cliente deve seguir da seguinte maneira, considerando os cenários e
    

exemplos:

-   Limite Diário (Ex.: R$ 100,00): Este limite controla as transferências realizadas dentro de um único dia, considerando o período das 00:00h até as 23:59h. Por exemplo, se um usuário transferir R$ 50,00 às 10:00h, ele ainda terá R$ 50,00 disponíveis para transferências até a meia-noite do mesmo dia;
    
-   Limite Semanal (Ex.: R$ 1.000,00): O limite semanal abrange o período de uma semana inteira, começando às 00:00h de domingo e terminando às 23:59h do sábado. Por exemplo, se um usuário transferir R$ 200,00 na terça-feira e R$ 500,00 na quinta-feira, ele ainda poderá transferir até R$ 300,00 até o final do sábado;
    
-   Limite Mensal (Ex.: R$ 10.000,00): Este limite mensal é calculado do primeiro ao último dia de cada mês. Por exemplo, em um mês, se o usuário transferir R$ 2.000,00 na primeira semana e R$ 3.000,00 na segunda semana, ele ainda terá R$ 5.000,00 disponíveis para transferências pelo restante do mês;
    
-   Limite Anual (Ex.: R$ 50.000,00): O limite anual conta do primeiro dia de janeiro ao último dia de dezembro. Por exemplo, se um usuário transferir R$ 10.000,00 até março, mais R$ 15.000,00 até junho e mais R$ 20.000,00 até setembro, ele só poderá transferir outros R$ 5.000,00 até o final do ano;
    
-   Esses limites ajudam a gerenciar as transferências de fundos, garantindo que não excedam os montantes estabelecidos para cada período. Cada limite é independente e é recalculado conforme sua respectiva janela de tempo se reinicia.
    

API de Iniciação de Pagamentos automáticos, responsável por viabilizar as operações de iniciação de pagamentos automáticos (Pix automático e Transferências Inteligentes) para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos endpoints dedicados ao consentimento nesta API.

\# Orientações

-   \`CONTA\`, referente às instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente às instituições iniciadoras de pagamento participantes do Open Finance Brasil.
    

Os tokens utilizados para consumo nos endpoints de consentimentos devem possuir o scope recurring-payments e os endpoints de pagamentos recorrentes devem possuir os scopes openid e recurring-payments.  
Esta API não requer a implementação de permissions para sua utilização.  
Todas as requisições e respostas devem ser assinadas seguindo o protocolo estabelecido na sessão Assinaturas do guia de segurança.

\## Orientações gerais sobre os consentimentos de pagamentos automáticos

-   Duração e reutilização do consentimento: A utilização das credenciais geradas a partir de uma autorização de um consentimento recorrente deve durar até que o consentimento recorrente atinja o fim do seu ciclo de vida, conforme detalhado na sua \[máquina de estados\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/198410647).
    
-   Credenciais: As credenciais (authorization\_code) geradas na autorização do consentimento devem ser utilizadas para criação dos pagamentos subsequentes utilizando o mecanismo de refresh, caso necessário. Maiores informações através do link \[\[PT\] Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3 - Área do Desenvolvedor -Open Finance Brasil - Área do Desenvolvedor ([atlassian.net](http://atlassian.net))\]([https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82051180/PT+Open+Finance+Brasil+Financial-grade+API+Security+Profile+1.0+Implementers+Draft+3#7.2.2.-Servidor-de-autorização](data/references/guides/PT.md))
    

\## Regras do arranjo Pix  
A implementação e o uso da API de Pagamentos Automáticos (Pix) devem seguir as regras do arranjo Pix do Banco Central, que podem ser encontradas no link abaixo:   
\[Banco Central do Brasil\]([https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao\_pix](https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao_pix))

\## Assinatura de payloads  
No contexto da API de Pagamentos Automáticos, os payloads de mensagem que trafegam tanto por parte da instituição iniciadora de transação de pagamento quanto por parte da instituição detentora de conta devem estar assinados.  
Para o processo de assinatura destes payloads, as instituições devem seguir as especificações de segurança publicadas no Portal do desenvolvedor.

\## Controle de acesso

-   Os endpoints de consulta de pagamentos GET /pix/recurring-payments/{recurringPaymentId} e GET /pix/recurring-payments devem suportar acesso a partir de access\_token emitido por meio de um grant\_type do tipo client credentials, como opção do uso do token vinculado ao consentimento (hybrid flow).
    
-   Para evitar vazamento de informação, a detentora deve validar que o pagamento consultado pertence ao ClientId que o criou e, caso haja divergências, retorne um erro HTTP 400.
    

\## Aprovações de múltipla alçada

Todas as aprovações devem ser realizadas até a data/hora limite suportada pela detentora e em tempo hábil para realizar o primeiro pagamento.

\## Validações da edição do consentimento recorrente para o produto Pix Automático

Para permitir a edição dos campos de um consentimento na iniciadora sem que se faça necessário o redirecionamento para o  
ambiente da detentora de conta, é necessário o envio de indicadores de risco.  
Esta medida visa proporcionar à detentora de conta as informações necessárias para decidir sobre os ajustes no consentimento de forma segura

\## Validações

Durante a jornada de iniciação de pagamento, diferentes validações são necessárias pela instituição detentora de conta e devem ocorrer conforme a seguir:

1.  \*\*Validações na criação do consentimento de longa duração (\_POST /recurring-consents\_)\*\* 
    

  1.1 \*\*Orientações Iniciais\*\*   
    &ensp;1.1.1 Não devem ser retornadas na resposta deste endpoint informações associadas ao usuário/cliente (ex. insuficiência de saldo, conta inexistente/bloqueada).   
    &ensp;1.1.2 Não devem ser realizadas validações de informações sobre o usuário/cliente durante a criação do consentimento.   
  1.2 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;1.2.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;1.2.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;1.2.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;1.2.4 Validação de Claims (exceto data);   
      &emsp;1.2.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;1.2.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  1.3 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*    
    &ensp;1.3.1 \*\*Sintáticos\*\*   
      &emsp;1.3.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios foram informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;1.3.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;1.3.2 \*\*Semânticos\*\*   
      &emsp;1.3.2.1 Data de pagamento: Valida se a data de pagamento enviada é válida para a forma de pagamento selecionada (DATA\_PAGAMENTO\_INVALIDA);   
      &emsp;1.3.2.2 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;1.3.2.3 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;1.3.2.4 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA);   
      &emsp;1.3.2.5 Funcionalidade não habilitada: A detentora de conta não oferece o serviço nessa modalidade (FUNCIONALIDADE\_NAO\_HABILITADA). 

1.  \*\*Demais validações executadas durante o processamento assíncrono do consentimento pela detentora poderão ser consultados pela iniciadora através do endpoint GET /recurring-consents/{recurringConsentId} previstos com retorno HTTP Code 200 – OK com status REJECTED e rejectionReason conforme abaixo:\*\* 
    

  2.1 \*\*Validações durante o processamento assíncrono do consentimento\*\*   
    &ensp;2.1.1 Falha de infraestrutura: Ocorreu algum erro interno na detentora durante processamento da criação do consentimento (FALHA\_INFRAESTRUTURA);   
    &ensp;2.1.2 Tempo de autorização expirado: O usuário não confirmou o consentimento e o mesmo expirou (TEMPO\_EXPIRADO\_AUTORIZACAO);   
    &ensp;2.1.3 Rejeitado pelo usuário: O usuário explicitamente rejeitou a autorização do consentimento (REJEITADO\_USUARIO);   
    &ensp;2.1.4 Mesma conta origem/destino: A conta indicada pelo usuário para recebimento é a mesma selecionada para o pagamento (CONTAS\_ORIGEM\_DESTINO\_IGUAIS);   
    &ensp;2.1.5 Tipo de conta inválida: A conta indicada não permite operações de pagamento (CONTA\_NAO\_PERMITE\_PAGAMENTO);   
    &ensp;2.1.6 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
    &ensp;2.1.7 Limites da transação: Valida se o valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente (VALOR\_ACIMA\_LIMITE); 

1.  \*\*Demais validações executadas durante o processamento assíncrono do consentimento pela detentora, poderão ser consultados pela iniciadora através dos endpoints GET /recurring-consents/{recurringConsentId} previstos com retorno HTTP Code 200 - OK com status REVOKED e revocationReason conforme abaixo (detalhamento adicional na documentação técnica da API).\*\* 
    

  3.1 \*\*Demais validações durante o processamento assíncrono:\*\*   
    &ensp;3.1.1 Nao informado: Validações não explicitamente informadas (ex. suspeita de fraude) (NAO\_INFORMADO);   
    &ensp;3.1.2 Revogado pelo recebedor: O usuário recebedor solicitou explicitamente ao iniciador a revogação do consentimento (ex: término de contrato) (REVOGADO\_RECEBEDOR);   
    &ensp;3.1.3 Revogado pelo pagador: O usuário pagador solicitou explicitamente a revogação do consentimento (REVOGADO\_USUARIO). 

1.  \*\*Validações na criação do pagamento - Síncrono (\_POST /pix/recurring-payments\_)\*\* 
    

  4.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;4.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;4.1.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;4.1.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;4.1.4 Validação de Claims (exceto data);   
      &emsp;4.1.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;4.1.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  4.2 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*   
    &ensp;4.2.1 Sintáticos   
      &emsp;4.2.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios são informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;4.2.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;4.2.2 Semânticos   
      &emsp;4.2.2.1 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
      &emsp;4.2.2.2 Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora na conta do cliente pagador (VALOR\_ACIMA\_LIMITE);   
      &emsp;4.2.2.3 Valor informado: Valida se valor enviado é válido para o consentimento associado ao pagamento (VALOR\_INVALIDO);   
      &emsp;4.2.2.4 Status Consentimento: Valida se o consentimento encontra-se em um dos estados finais “CONSUMED”, “REVOKED” ou “REJECTED" (CONSENTIMENTO\_INVALIDO);    
      &emsp;4.2.2.5 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;4.2.2.6 Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO)   
      &emsp;4.2.2.7 Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa;   
      &emsp;4.2.2.8 Detalhes do pagamento: Valida se determinado parâmetro informado obedece as regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;4.2.2.9 Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI) (PAGAMENTO\_RECUSADO\_SPI);   
      &emsp;4.2.2.10 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA);   
      &emsp;4.2.2.11 Limite valor excedido por período: Foi atingido o valor limite permitido pelo usuário por um determinado período de tempo no consentimento do pagamento (LIMITE\_PERIODO\_VALOR\_EXCEDIDO);   
      &emsp;4.2.2.12 Limite quantidade excedida por período: A quantidade de cobranças atingiu o limite determinado pelo usuário na criação do consentimento (LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO);    
      &emsp;4.2.2.13 Consentimento pendente de autorização: Consentimento em “PARTIALLY\_ACCEPTED” aguardando aprovação de múltiplas alçadas (CONSENTIMENTO\_PENDENTE\_AUTORIZACAO).

1.  \*\*Validações na consulta do pagamento (\_GET /pix/recurring-payments/{recurringPaymentId}\_ e \_GET /pix/recurring-payments\_)\*\* 
    

  5.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token)\*\*   
    &ensp;5.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;5.1.2 Validações de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED).

1.  \*\*Demais validações executadas durante o processamento assíncrono do pagamento pela detentora, poderão ser consultados pela iniciadora através dos endpoints \_GET /pix/recurring-payments/{recurringPaymentId}\_ e \_GET /pix/recurring-payments\_ previstos com retorno HTTP Code 200 - OK com status RJCT (Rejected) e rejectionReason conforme abaixo (detalhamento adicional na documentação técnica da API):\*\* 
    

  6.1 \*\*Demais validações durante o processamento assíncrono:\*\*   
    &ensp;6.1.1 - Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
    &ensp;6.1.2 - Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora (VALOR\_ACIMA\_LIMITE);   
    &ensp;6.1.3 - Valor informado: Valida se valor enviado é válido para o consentimento do pagamento (VALOR\_INVALIDO);   
    &ensp;6.1.4 - Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
    &ensp;6.1.5 - Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO);   
    &ensp;6.1.6 - Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa;   
    &ensp;6.1.7 - Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI) (PAGAMENTO\_RECUSADO\_SPI);   
    &ensp;6.1.8 - Erro de infraestrutura na consulta ao SPI: Ocorreu uma falha de infraestrutura durante a consulta ao SPI(FALHA\_INFRAESTRUTURA\_SPI);   
    &ensp;6.1.9 - Erro de infraestrutura na consulta ao ICP: Ocorreu uma falha de infraestrutura durante a consulta ao ICP (FALHA\_INFRAESTRUTURA\_ICP);   
    &ensp;6.1.10 - Erro de infraestrutura na comunicação com o PSP do recebedor: Ocorreu uma falha de infraestrutura durante a comunicação com o PSP do recebedor (FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR);   
    &ensp;6.1.11 - Erro de infraestrutura interno na detentora: Ocorreu uma falha de infraestrutura interna na detentora durante o processamento do pagamento (FALHA\_INFRAESTRUTURA\_DETENTORA);   
    &ensp;6.1.12 - Status Consentimento: Valida se o consentimento encontra-se em um dos estados finais “CONSUMED”, “REVOKED” ou “REJECTED" (CONSENTIMENTO\_INVALIDO);   
    &ensp;6.1.13 - Limite valor excedido por período: Foi atingido o valor limite permitido pelo usuário por um determinado período de tempo no consentimento do pagamento (LIMITE\_PERIODO\_VALOR\_EXCEDIDO);   
    &ensp;6.1.14 - Limite quantidade excedida por período: A quantidade de cobranças atingiu o limite determinado pelo usuário na criação do consentimento (LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO).   
    &ensp;6.1.15 - Titularidade Inconsistente: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração. Caso a liquidação seja negada pelo PSP Recebedor com erro BE01, cabe a detentora de conta mudar o status do pagamento para RJCT com essa reason (TITULARIDADE\_INCONSISTENTE) 

\## Validações antifraude da Transferências Inteligentes

-   Afim de garantir a mesma titularidade e aumentar a segurança das transações do produto Transferências Inteligentes, as validações abaixo poderão ser realizadas pela detetora de conta e pela iniciadora, quando localinstrument for igual a DICT ou INIC. A detentora PODE usar a API Consultar Vinculo (DICT API) do arranjo Pix e validar no momento de transação ao menos os atributos abaixo mencionados:
    
-   se o valor dos atributos de fraude abaixo são iguais a 0, de modo a evitar que contas criadas especificamente para uso indevido da Transferências Inteligentes impactem o ecossistema
    
-   OwnerStatistics.Spi.FraudMarkers.ApplicationFrauds.d90
    
-   OwnerStatistics.Spi.FraudMarkers.MuleAccounts.d90
    
-   OwnerStatistics.Spi.FraudMarkers.ScammerAccounts.d90
    
-   OwnerStatistics.Spi.FraudMarkers.OtherFrauds.d90
    
-   OwnerStatistics.Spi.FraudMarkers.UnknownFrauds.d90
    

\## Limites transacionais e crédito pré-aprovado para Transferências inteligentes

-   Existem três tipos de limites para o produto Transferências inteligentes
    
-   Crédito pré-aprovado (cheque especial): Caso o cliente possua o produto, poderá utilizá-lo durante as transações associadas ao produto Transferências inteligentes.
    
-   Limite do Pix atrelado à conta do cliente: Limite de transações definido individualmente para cada conta do cliente, conforme regras de dias e horários do arranjo Pix.
    
-   Limites do consentimento: Configurado ou não pelo cliente em momento de criação do consentimento, podendo ser dependente ou não de um período.
    
-   O cálculo do limite periódico disponível ao cliente deve seguir da seguinte maneira, considerando os cenários e
    

exemplos:

-   Limite Diário (Ex.: R$ 100,00): Este limite controla as transferências realizadas dentro de um único dia, considerando o período das 00:00h até as 23:59h. Por exemplo, se um usuário transferir R$ 50,00 às 10:00h, ele ainda terá R$ 50,00 disponíveis para transferências até a meia-noite do mesmo dia;
    
-   Limite Semanal (Ex.: R$ 1.000,00): O limite semanal abrange o período de uma semana inteira, começando às 00:00h de domingo e terminando às 23:59h do sábado. Por exemplo, se um usuário transferir R$ 200,00 na terça-feira e R$ 500,00 na quinta-feira, ele ainda poderá transferir até R$ 300,00 até o final do sábado;
    
-   Limite Mensal (Ex.: R$ 10.000,00): Este limite mensal é calculado do primeiro ao último dia de cada mês. Por exemplo, em um mês, se o usuário transferir R$ 2.000,00 na primeira semana e R$ 3.000,00 na segunda semana, ele ainda terá R$ 5.000,00 disponíveis para transferências pelo restante do mês;
    
-   Limite Anual (Ex.: R$ 50.000,00): O limite anual conta do primeiro dia de janeiro ao último dia de dezembro. Por exemplo, se um usuário transferir R$ 10.000,00 até março, mais R$ 15.000,00 até junho e mais R$ 20.000,00 até setembro, ele só poderá transferir outros R$ 5.000,00 até o final do ano;
    
-   Esses limites ajudam a gerenciar as transferências de fundos, garantindo que não excedam os montantes estabelecidos para cada período. Cada limite é independente e é recalculado conforme sua respectiva janela de tempo se reinicia.
    

## GET /pix/recurring-payments

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/data/items/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

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
    
-   TITULARIDADE\_INCONSISTENTE: Conta atualmente não associada ao CPF/CNPJ do consentimento de longa duração.
    

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
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
    

## POST /pix/recurring-payment

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122) ) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/201/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

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
    

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
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
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    

post/responses/422/errors/items/code

Alterado - "description"

Alteração

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status não é "authorised" ou está expirado).
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Códigos de erros previstos na criação da iniciação de pagamento:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
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
    

post/responses/422/errors/items/code/enum

Adicionado - "CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"

Adição

enum

post/responses/422/errors/items/detail

Alterado - "description"

Alteração

Descrição específica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status não é "authorised" ou está expirado).
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Descrição específica do erro de acordo com o código reportado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
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
    

post/responses/422/errors/items/title

Alterado - "description"

Alteração

Título específico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado.
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO: A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO: A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    
-   CONSENTIMENTO\_INVALIDO: Consentimento inválido (status não é "authorised" ou está expirado).
    
-   PARAMETRO\_NAO\_INFORMADO: Parâmetro não informado.
    
-   PARAMETRO\_INVALIDO: Parâmetro inválido.
    
-   NAO\_INFORMADO: Não informada pela detentora de conta.
    
-   PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO: Dados do pagamento divergentes dos dados do consentimento.
    
-   DETALHE\_PAGAMENTO\_INVALIDO: Detalhe do pagamento inválido.
    
-   PAGAMENTO\_RECUSADO\_DETENTORA: Pagamento recusado pela detentora de conta.
    
-   PAGAMENTO\_RECUSADO\_SPI: Pagamento recusado no Sistema de Pagamentos Instantâneos (SPI).
    
-   ERRO\_IDEMPOTENCIA: Erro idempotência.
    

Título específico do erro reportado, de acordo com o código enviado:

-   SALDO\_INSUFICIENTE: Esta conta não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente.
    
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
    

## GET /pix/recurring-payments/{recurringPaymentId}

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

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
    

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
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
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    

## PATCH /pix/recurring-payments/{recurringPaymentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Detalhe sobre o código identificador do motivo de rejeição.

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
    

Detalhe sobre o código identificador do motivo de rejeição.

-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento;
    
-   VALOR\_ACIMA\_LIMITE: O valor (ou quantidade de transações) ultrapassa a faixa de limite parametrizada na detentora para permitir a realização de transações pelo cliente;
    
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
    
-   LIMITE\_PERIODO\_VALOR\_EXCEDIDO – A transação não pode ser realizada pois o valor parametrizado no consentimento foi excedido.
    
-   LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO – A transação não pode ser realizada pois a quantidade parametrizada no consentimento foi excedida.
    

## POST /recurring-consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

post/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

## GET /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

get/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

## PATCH /recurring-consents/{recurringConsentId}

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/parameters/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

patch/responses/200/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/400/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/401/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/403/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/404/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/405/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/406/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/422/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/500/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

patch/responses/504/headers/x-fapi-interaction-id

Alterado - "description"

Alteração

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...

Um UUID \[RFC4122\]([https://tools.ietf.org/html/rfc4122](https://tools.ietf.org/html/rfc4122)) usado como um ID de correlação entre request e response. Campo de geração e...
