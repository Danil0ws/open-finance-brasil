# Changelog - [SV] Pagamentos - v5.0.0 - v5.0.0-rc.1

## Alterações na seção de orientações do swagger

**Campo**

**Antes**

**Depois**

versão

5.0.0-rc.1

5.0.0

descrição

API de Iniciação de Pagamentos, responsável por viabilizar as operações de iniciação de pagamentos para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos \`endpoints\` dedicados ao consentimento nesta API.

\# Orientações  
No diretório de participantes duas \`Roles\` estão relacionadas à presente API:

-   \`CONTA\`, referente às instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente às instituições iniciadoras de pagamento participantes do Open Finance Brasil.
    

  
Os tokens utilizados para consumo nos endpoints de consentimentos devem possuir o scope \`payments\` e os \`endpoints\` de pagamentos devem possuir os \`scopes\`, \`openid\` e \`payments\`.  
Esta API não requer a implementação de \`permissions\` para sua utilização. Todas as requisições e respostas devem ser assinadas seguindo o protocolo estabelecido na sessão <a href="https://openbanking-brasil.github.io/areadesenvolvedor/#assinaturas" target="\_blank">Assinaturas</a> do guia de segurança.

\## Regras do arranjo Pix  
A implementação e o uso da API de Pagamentos Pix devem seguir as regras do arranjo Pix do Banco Central, que podem ser encontradas no link abaixo:    
\[https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao\_pix\](https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao\_pix)

\## Assinatura de payloads

No contexto da API Payment Initiation, os \`payloads\` de mensagem que trafegam tanto por parte da instituição iniciadora de transação de pagamento quanto por parte da instituição detentora  
de conta devem estar assinados. Para o processo de assinatura destes \`payloads\` as instituições devem seguir as especificações de segurança publicadas no Portal do desenvolvedor:

-   Certificados exigidos para assinatura de mensagens:
    

  
\[\[EN\] Padrão de Certificados Open Finance Brasil 2.1\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82084176/EN+Padr+o+de+Certificados+Open+Finance+Brasil+2.1%20%E2%80%8B)

-   Como assinar o payload JWS: \[Como Assinar o Payload\](data/references/guides/Como.md)
    

\## Controle de acesso

Os endpoints de consulta e cancelamento devem suportar somente acesso a partir de access\_token emitido por meio de um grant\_type do tipo client\_credentials.

Para a criação do consentimento deve-se utilizar client\_credentials e para criação de pagamentos deve-se utilizar authorization\_code.

\## Aprovações de múltipla alçada

-   Para o caso de pagamento imediato, todas as aprovações necessárias devem ser realizadas nos canais da detentora até às 23:59 (horário de Brasília) da data de solicitação do pagamento.
    

  
Já para o caso de pagamento agendado, todas as aprovações devem ser realizadas até o exato dia anterior à data/hora prevista para primeira liquidação, respeitando a data/hora limite suportada pela detentora.  
Caso não seja possível aprovação, o consentimento deve ser rejeitado pelo detentor.

\## Validações para pagamentos recorrentes

-   No cenário onde o usuário pagador tenha agendado recorrências para os dias 29, 30 ou 31 de cada mês e o dia previsto na recorrência não exista no respectivo mês,
    

  
o iniciador deve enviar a ordem de pagamento para liquidação com o endToEndId representando o dia seguinte à data prevista para a liquidação.  
Se identificado pelo detentor que a data enviada no endToEndId corresponde a um dia inexistente, ele deve rejeitar o pagamento com erro 422,  
com código PARAMETRO\_INVALIDO e detalhe “Data de liquidação inválida”

-   Quando o detentor receber mais de um item na lista de pagamentos enviados pelo iniciador e optar por responder
    

  
assincronamente, é de responsabilidade do detentor realizar a transição para o status SCHD de todos os itens enviados na  
lista de pagamentos em até 60 minutos (contados a partir da resposta de sucesso da solicitação).  
Caso não seja possível realizar a transição de todos os pagamentos para SCHD, o detentor deverá mover todos os pagamentos  
enviados pelo iniciador naquela mesma requisição para RJCT e preencher o motivo de rejeição correspondente,  
FALHA\_AGENDAMENTO\_PAGAMENTOS. O consentimento irá para CONSUMED.

-   Durante a liquidação de pagamentos agendados, seguindo a resolução BCB n402, de 22/07/2024, previamente ao envio de um
    

  
pagamento à liquidação, o detentor deve consultar a chave utilizada para o agendamento no DICT. Se a consulta retornar que  
a chave Pix não está registrada ou que os dados da chave divergem dos dados durante o agendamento, o detentor não deve  
enviar o Pix para Liquidação. Todos os pagamentos associados a esse consentimento devem ser rejeitados com o  
motivo CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO, e o usuário pagador deve ser notificado

\## Pix Saque e Troco

-   A partir da versão 5.0.0 da API Pagamentos passa a ser possível a realização de Saques e Trocos através das funcionalidades disponíveis para tal no arranjo Pix. Para a realização das operações, as ITPs devem passar a reportar o payloadJWS completo que foi gerado pelo PSP do Recebedor, o qual contém todos os dados necessários para a validação das informações da operação em questão. 
    
-   Ao receber um pedido de criação de consentimento que esteja marcado como \`\`\`WITHDRAW\`\`\` ou \`\`\`CHANGE\`\`\` no campo \`\`\`/data/payment/purpose\`\`\`, o PSP do Pagador (Detentor) deverá consultar os dados do agente e do facilitador do serviço dentro do payloadJWS enviado pelo ITP, assim como os outros dados pertinentes a operação solicitada. 
    
-   A identificação também deverá ser realizada pelo PSP do Pagador ao enviar a mensagem \`\`\`PACS.008\`\`\` ao SPI, com a marcação correta da finalidade da transação sendo realizada, bem como outras informações necessárias para a correta liquidação da operação de Saque ou Troco. 
    
-   Outras regras que devem ser observadas durante a validação e liquidação do QRCode de Pix Saque ou Pix Troco podem ser encontrados no Manual de Padrões para Iniciação do Pix, disponível no site do Banco Central.
    

\## Validações  
\*\*Validações\*\* (\*após o processo de DCR e obtenção de token client credential\*– não escopo dessa documentação)   
Durante a jornada de iniciação de pagamento, diferentes validações são necessárias pela instituição detentora  
de conta e devem ocorrer conforme a seguir:

1.  Na criação do consentimento (\*POST /consents\*);
    
2.  Na criação do pagamento - Síncrono (\*POST /payments\*);
    
3.  Validações na consulta do pagamento (\*GET /pix/payments/{paymentId}\*);
    
4.  Demais validações executadas durante o processamento assíncrono do pagamento pela detentora, poderão ser consultados pela iniciadora através do endpoint (\*GET /pix/payments/{paymentId}\*) previstos com retorno HTTP Code 200 - OK com status RJCT (Rejected) e rejectionReason;
    
5.  Demais validações executadas durante o processamento assíncrono do consentimento pela detentora poderão ser consultados pela iniciadora através do endpoint (\*GET /consents/{consentId}\*) previstos com retorno HTTP Code 200 – OK com status REJECTED e rejectionReason
    

\*\*Os tipos de validações dispostas abaixo não determinam a ordem em que as instituições devem implementá-las\*\*

1.  \*\*Validações na criação do consentimento (\_POST /consents\_)\*\* 
    

  
  1.1 \*\*Orientações Iniciais\*\*   
    &ensp;1.1.1 Não devem ser retornadas na resposta deste endpointinformações associadas ao usuário/cliente (ex.  insuficiência de saldo, conta inexistente/bloqueada).   
    &ensp;1.1.2 Não devem ser executadas validações no DICT (Diretório de Identificadores de Contas Transacionais do Pix), a partir dos dados compartilhados nesse \*endpoint\*. Tais  validações podem ocorrer somente na criação do pagamento;   
    &ensp;1.1.3 Não devem ser realizadas validações de informações sobre o usuário/cliente durante a criação do consentimento.  
  1.2 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;1.2.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;1.2.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;1.2.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;1.2.4 Validação de Claims (exceto data);   
      &emsp;1.2.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;1.2.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  1.3 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*    
    &ensp;1.3.1 \*\*Sintáticos\*\*   
      &emsp;1.3.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios são informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;1.3.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;1.3.2 \*\*Semânticos\*\*   
      &emsp;1.3.2.1 Forma de pagamento: Valida se a forma de pagamento é suportada pela detentora (FORMA\_PAGAMENTO\_INVALIDA) \*\*Obs. No detalhe do erro, a variável “modalidade” deve ser comunicada pela detentora da forma mais clara possível - ex. modalidade de pagamento não suportada (\_localInstrument\_ - QRES) ou tipo de arranjo pagamento não suportado (\_type\_ – ex. Pix / TED – previsto para inclusão futura);\*\*   
      &emsp;1.3.2.2 Data de pagamento: Valida se a data de pagamento enviada é válida para a forma de pagamento selecionada (DATA\_PAGAMENTO\_INVALIDA);   
      &emsp;1.3.2.3 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;1.3.2.4 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;1.3.2.5 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA).   
      &emsp;1.3.2.6  O propósito informado é incompatível com os dados presentes na transação. (PROPOSITO\_INVALIDO)

2.  \*\*Validações na criação do pagamento - Síncrono (\_POST /payments\_)\*\* 
    

  
  2.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;2.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;2.1.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;2.1.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;2.1.4 Validação de Claims (exceto data);   
      &emsp;2.1.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;2.1.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  2.2 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*   
    &ensp;2.2.1 \*\*Sintáticos\*\*   
      &emsp;2.3.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios são informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;2.3.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;2.2.2 \*\*Semânticos\*\*   
      &emsp;2.2.2.1 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
      &emsp;2.2.2.2 Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora (VALOR\_ACIMA\_LIMITE);   
      &emsp;2.2.2.3 Valor informado (QR Code): Valida se valor enviado é válido para o QR Code informado (VALOR\_INVALIDO);   
      &emsp;2.2.2.4 Cobrança inválida: Valida expiração, vencimento e status (COBRANCA\_INVALIDA);   
      &emsp;2.2.2.5 Status Consentimento: Valida se o consentimento encontra-se em um dos estados finais “CONSUMED” ou “REJECTED" (CONSENTIMENTO\_INVALIDO);   
      &emsp;2.2.2.6 Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO)   
      &emsp;2.2.2.7 Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa (ex. chave Pix inválida, QRCode inválido, conta bloqueada);   
      &emsp;2.2.2.8 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;2.2.2.9 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;2.2.2.10 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA);   
      &emsp;2.2.2.11 Consentimento pendente de autorização: Em \`PARTIALLY\_ACCEPTED\` aguardando aprovação de múltiplas alçadas. Não consome nem invalida o consentimento (CONSENTIMENTO\_PENDENTE\_AUTORIZACAO).   
  2.3 \*\*Casos de erro para validações síncronas no DICT\*\*   
    &ensp;Nesse cenário, o pagamento não é criado, porém o consentimento deve ser alterado para o status CONSUMED Retorno esperado do endpoint POST/Payments: HTTP Code 422 - Unprocessable Entity:   
    &ensp;• Erro por dados inválidos: Conforme item \*\*2.2.2.8\*\*   
    &ensp;• Erro por suspeita de fraude: Conforme item \*\*2.2.2.9\*\* 

3.  \*\*Validações na consulta do pagamento (\_GET /pix/payments/{paymentId}\_)\*\* 
    

  
  3.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token)\*\*   
    &ensp;3.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;3.1.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED). 

4.  \*\*Demais validações executadas durante o processamento assíncrono do pagamento pela detentora, poderão ser consultados pela iniciadora através do endpoint \_GET /pix/payments/{paymentId}\_ previstos com retorno HTTP Code 200 - OK com status RJCT (Rejected) e rejectionReason conforme abaixo (detalhamento adicional na documentação técnica da API):\*\* 
    

  
  4.1 \*\*Demais validações durante processamento assíncrono\*\*   
    &ensp;4.1.1 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento. No caso de um pagamento agendado, a validação só ocorre na tentativa de liquidação do pagamento (SALDO\_INSUFICIENTE);   
    &ensp;4.1.2 Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora (VALOR\_ACIMA\_LIMITE);   
    &ensp;4.1.3 Valor informado (QR Code): Valida se valor enviado é válido para o QR Code informado (VALOR\_INVALIDO);   
    &ensp;4.1.4 Cobrança inválida: Valida expiração, vencimento e status (COBRANCA\_INVALIDA);   
    &ensp;4.1.5 Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO);   
    &ensp;4.1.6 Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa (ex. chave Pix inválida, QRCode inválido, conta bloqueada);   
    &ensp;4.1.7 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
    &ensp;4.1.8 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
    &ensp;4.1.9 Validação SPI: Externaliza validações no SPI (PAGAMENTO\_RECUSADO\_SPI);   
    &ensp;4.1.10 Falha em agendamentos: Uma ou mais incidências de pagamento não foram possíveis de ser agendadas (FALHA\_AGENDAMENTO\_PAGAMENTOS);   
    &ensp;4.1.11 Divergências entre dados das chaves pix para agendamento e liquidação: O pagamento agendado não pode ser enviado para liquidação devido a divergências entre dados da chave recebedora utilizada para criação do agendamento com a chave recebedora em momento de liquidação (CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO);   
    &ensp;4.1.12 Erro de infraestrutura na consulta ao DICT: Ocorreu uma falha de infraestrutura durante a consulta ao DICT (FALHA\_INFRAESTRUTURA\_DICT);    
    &ensp;4.1.13 Erro de infraestrutura na consulta ao ICP: Ocorreu uma falha de infraestrutura durante a consulta ao ICP (FALHA\_INFRAESTRUTURA\_ICP);    
    &ensp;4.1.14 Erro de infraestrutura na comunicação com o PSP do recebedor: Ocorreu uma falha de infraestrutura durante a comunicação com o PSP do recebedor (FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR);    
    &ensp;4.1.15 Erro de infraestrutura interno na detentora: Ocorreu uma falha de infraestrutura interna na detentora durante o processamento do pagamento (FALHA\_INFRAESTRUTURA\_DETENTORA);    
    &ensp;4.1.16 Erro de infraestrutura na consulta ao SPI: Ocorreu uma falha de infraestrutura durante a consulta ao SPI (FALHA\_INFRAESTRUTURA\_SPI).    
  4.2 \*\*Casos de erro para validações assíncronas no DICT\*\*   
    &ensp;Neste cenário o pagamento é criado com sucesso (status RCVD) e o consentimento é consumido (status CONSUMED), porém, as validações contra o DICT só ocorrerão de forma assíncrona e em caso de negativa será percebido pela iniciadora na consulta do pagamento (GET /Payments).   
    &ensp;Retorno esperado do endpoint GET /Payments: HTTP Code 200 - OK.   
    &ensp;Status do Pagamento: RJCT (Rejected), com as seguintes opções rejectionReason:   
    &ensp;• Erro por dados inválidos: Conforme item \*\*4.1.7\*\*;   
    &ensp;• Erro por suspeita de fraude: Conforme item \*\*4.1.8\*\*.

5.  \*\*Demais validações executadas durante o processamento assíncrono do consentimento pela detentora poderão ser consultados pela iniciadora através do endpoint \_GET /consents/{consentId}\_ previstos com retorno HTTP Code 200 – OK com status REJECTED e rejectionReason conforme abaixo:\*\* 
    

  
  5.1 \*\*Validações durante o processamento assíncrono\*\*   
    &ensp;5.1.1 - Falha de infraestrutura: Ocorreu algum erro interno na detentora durante processamento da criação do consentimento (FALHA\_INFRAESTRUTURA)   
    &ensp;5.1.2 - Tempo de autorização expirado: O usuário não confirmou o consentimento e o mesmo expirou (TEMPO\_EXPIRADO\_AUTORIZACAO);   
    &ensp;5.1.3 - Rejeitado pelo usuário: O usuário explicitamente rejeitou a autorização do consentimento (REJEITADO\_USUARIO);   
    &ensp;5.1.4 - Mesma conta origem/destino: A conta indicada pelo usuário para recebimento é a mesma selecionada para o pagamento (CONTAS\_ORIGEM\_DESTINO\_IGUAIS);   
    &ensp;5.1.5 - Tipo de conta inválida: A conta indicada não permite operações de pagamento (CONTA\_NAO\_PERMITE\_PAGAMENTO);   
    &ensp;5.1.6 - Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento. Essa validação não deverá ocorrer no caso de um pagamento agendado (SALDO\_INSUFICIENTE);   
    &ensp;5.1.7 - Limites da transação: Valida se o valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente (VALOR\_ACIMA\_LIMITE);   
    &ensp;5.1.8 - QRCode inválido: O QRCode utilizado para a iniciação de pagamento não é válido (QRCODE\_INVALIDO);   
    &ensp;5.1.9 - Valor inválido: O valor enviado não é válido para o QR Code informado (VALOR\_INVALIDO);   
    &ensp;5.1.10 - Não informado: Demais validações não explicitamente informadas (ex. suspeita de fraude) e consentimentos rejeitados em versões que não existiam o campo rejectionReason na API de Pagamentos (NAO\_INFORMADO)   
    &ensp;5.1.11 - Tempo expirado consumo: O usuário não finalizou o fluxo de pagamento e o consentimento expirou (TEMPO\_EXPIRADO\_CONSUMO).    
    &ensp;5.1.12 - Autenticação divergente: O usuário autenticado no ambiente da detentora não é o mesmo usuário autenticado no ambiente da iniciadora e que criou o consentimento (AUTENTICACAO\_DIVERGENTE).    
  5.2 \*\*\[Momentos obrigatórios de validação dos rejectionReasons de acordo com o funil de consentimentos.\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/150863940) Para casos em que um consentimento for rejeitado por mais de um motivo, seguir a ordem de prioridade da tabela.\*\*  
  \`\`\`  
  |----------------------------------|------------------------------|---------------------|  
  | Etapas do funil de consentimento | rejectionReason/code         | Ordem de prioridade |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | TEMPO\_EXPIRADO\_AUTORIZACAO   |          1          |  
  | Início da autenticação           | FALHA\_INFRAESTRUTURA         |          2          |  
  |                                  | NAO\_INFORMADO                |          3          |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | TEMPO\_EXPIRADO\_AUTORIZACAO   |          1          |  
  |                                  | REJEITADO\_USUARIO            |          2          |  
  | Conclusão da autenticação        | FALHA\_INFRAESTRUTURA         |          3          |  
  |                                  | NAO\_INFORMADO                |          4          |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | AUTENTICACAO\_DIVERGENTE      |          1          |  
  |                                  | CONTA\_NAO\_PERMITE\_PAGAMENTO  |          2          |  
  |                                  | CONTAS\_ORIGEM\_DESTINO\_IGUAIS |          3          |  
  |                                  | VALOR\_INVALIDO               |          4          |  
  | Autorização do cliente           | QRCODE\_INVALIDO              |          5          |  
  |                                  | VALOR\_ACIMA\_LIMITE           |          6          |  
  |                                  | SALDO\_INSUFICIENTE           |          7          |  
  |                                  | FALHA\_INFRAESTRUTURA         |          8          |  
  |                                  | NAO\_INFORMADO                |          9          |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | FALHA\_INFRAESTRUTURA         |          1          |  
  | Authorisation code emitido       | NAO\_INFORMADO                |          2          |  
  |                                  | TEMPO\_EXPIRADO\_CONSUMO       |          3          |  
  |----------------------------------|------------------------------|---------------------|  
  \`\`\`  
  5.3 \*\*Momentos obrigatórios de validação dos rejectionReasons de consentimentos autorizados via JSR\*\*   
  Consentimentos autorizados a partir do fluxo sem redirecionamento possuem um funil de conversão diferente, dado que não há o redirecionamento e este é um grande segregador das etapas do funil.   
  Devido a isso, as validações e a ordem que estas devem ser feitas, descritas no tópico anterior, não se aplicam integralmente aos consentimentos que foram autorizados no fluxo sem redirecionamento. Para consentimentos autorizados via fluxo sem redirecionamento, os únicos motivos de rejeição cabíveis são:

-   TEMPO\_EXPIRADO\_AUTORIZACAO – Utilizado quando o gesto FIDO não foi realizado a tempo pelo cliente final
    
-   TEMPO\_EXPIRADO\_CONSUMO – Utilizado quando o ITP, em posse do consentimento autorizado, não envia o pagamento.
    
-   FALHA\_INFRAESTRUTURA – Utilizado quando uma falha sistêmica impediu o avanço no processo do consentimento. 
    

  
  Demais validações que antes ocorriam no consentimento, agora devem ocorrer apenas em momento de pagamento. Permitindo assim que a detentora de contas tenha tempo de realizar as validações de maneira assíncrona a autorização do consentimento

  ### Cancelamento de Pagamentos  
  Existem dois \`endpoints\` para cancelamento de pagamentos, um deles é o \_PATCH /pix/payments/{paymentId}\_ e o outro é o \_PATCH /consents/{consentId}/pix/payments\_.

-   O \_PATCH /pix/payments/{paymentId}\_ deve ser utilizado para o cancelamento de um pagamento de forma unitária. Não deve ser utilizado para o cancelamento de todos os agendamentos recorrentes associados a um consentimento.
    
-   O \_PATCH /consents/{consentId}/pix/payments\_ deve ser utilizado no cancelamento de todas as ocorrências de pagamentos agendados presentes em uma recorrência de pagamentos. Todos os pagamentos associados ao consentimento informado e passíveis de cancelamento (ainda não liquidados, com os status PDNG e SCHD) deverão ser cancelados.
    

  
   
  ## Quantidade máxima permitida para agendamentos recorrentes  
  A quantidade máxima de pagamentos que podem transitar do iniciador para o detentor são de 60 pagamentos, independente do modelo de recorrência definido no consentimento, respeitando o prazo máximo de dois anos para agendamentos.  
  Caso a opção de recorrência enviada pelo iniciador não respeite a regra acima, o detentor deve retornar o erro 422 "PARAMETRO\_INVALIDO" com o detalhe "Quantidade permitida de pagamentos excedida".  

API de Iniciação de Pagamentos, responsável por viabilizar as operações de iniciação de pagamentos para o Open Finance Brasil.  
Para cada uma das formas de pagamento previstas é necessário obter prévio consentimento do cliente através dos \`endpoints\` dedicados ao consentimento nesta API.

\# Orientações  
No diretório de participantes duas \`Roles\` estão relacionadas à presente API:

-   \`CONTA\`, referente às instituições detentoras de conta participantes do Open Finance Brasil;
    
-   \`PAGTO\`, referente às instituições iniciadoras de pagamento participantes do Open Finance Brasil.
    

  
Os tokens utilizados para consumo nos endpoints de consentimentos devem possuir o scope \`payments\` e os \`endpoints\` de pagamentos devem possuir os \`scopes\`, \`openid\` e \`payments\`.  
Esta API não requer a implementação de \`permissions\` para sua utilização. Todas as requisições e respostas devem ser assinadas seguindo o protocolo estabelecido na sessão <a href="https://openbanking-brasil.github.io/areadesenvolvedor/#assinaturas" target="\_blank">Assinaturas</a> do guia de segurança.

\## Regras do arranjo Pix  
A implementação e o uso da API de Pagamentos Pix devem seguir as regras do arranjo Pix do Banco Central, que podem ser encontradas no link abaixo:    
\[https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao\_pix\](https://www.bcb.gov.br/estabilidadefinanceira/pix?modalAberto=regulamentacao\_pix)

\## Assinatura de payloads

No contexto da API Payment Initiation, os \`payloads\` de mensagem que trafegam tanto por parte da instituição iniciadora de transação de pagamento quanto por parte da instituição detentora  
de conta devem estar assinados. Para o processo de assinatura destes \`payloads\` as instituições devem seguir as especificações de segurança publicadas no Portal do desenvolvedor:

-   Certificados exigidos para assinatura de mensagens:
    

  
\[\[EN\] Padrão de Certificados Open Finance Brasil 2.1\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82084176/EN+Padr+o+de+Certificados+Open+Finance+Brasil+2.1%20%E2%80%8B)

-   Como assinar o payload JWS: \[Como Assinar o Payload\](data/references/guides/Como.md)
    

\## Controle de acesso

Os endpoints de consulta e cancelamento devem suportar somente acesso a partir de access\_token emitido por meio de um grant\_type do tipo client\_credentials.

Para a criação do consentimento deve-se utilizar client\_credentials e para criação de pagamentos deve-se utilizar authorization\_code.

\## Aprovações de múltipla alçada

-   Para o caso de pagamento imediato, todas as aprovações necessárias devem ser realizadas nos canais da detentora até às 23:59 (horário de Brasília) da data de solicitação do pagamento.
    

  
Já para o caso de pagamento agendado, todas as aprovações devem ser realizadas até o exato dia anterior à data/hora prevista para primeira liquidação, respeitando a data/hora limite suportada pela detentora.  
Caso não seja possível aprovação, o consentimento deve ser rejeitado pelo detentor.

\## Validações para pagamentos recorrentes

-   No cenário onde o usuário pagador tenha agendado recorrências para os dias 29, 30 ou 31 de cada mês e o dia previsto na recorrência não exista no respectivo mês,
    

  
o iniciador deve enviar a ordem de pagamento para liquidação com o endToEndId representando o dia seguinte à data prevista para a liquidação.  
Se identificado pelo detentor que a data enviada no endToEndId corresponde a um dia inexistente, ele deve rejeitar o pagamento com erro 422,  
com código PARAMETRO\_INVALIDO e detalhe “Data de liquidação inválida”

-   Quando o detentor receber mais de um item na lista de pagamentos enviados pelo iniciador e optar por responder
    

  
assincronamente, é de responsabilidade do detentor realizar a transição para o status SCHD de todos os itens enviados na  
lista de pagamentos em até 60 minutos (contados a partir da resposta de sucesso da solicitação).  
Caso não seja possível realizar a transição de todos os pagamentos para SCHD, o detentor deverá mover todos os pagamentos  
enviados pelo iniciador naquela mesma requisição para RJCT e preencher o motivo de rejeição correspondente,  
FALHA\_AGENDAMENTO\_PAGAMENTOS. O consentimento irá para CONSUMED.

-   Durante a liquidação de pagamentos agendados, seguindo a resolução BCB n402, de 22/07/2024, previamente ao envio de um
    

  
pagamento à liquidação, o detentor deve consultar a chave utilizada para o agendamento no DICT. Se a consulta retornar que  
a chave Pix não está registrada ou que os dados da chave divergem dos dados durante o agendamento, o detentor não deve  
enviar o Pix para Liquidação. Todos os pagamentos associados a esse consentimento devem ser rejeitados com o  
motivo CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO, e o usuário pagador deve ser notificado

\## Pix Saque e Troco

-   A partir da versão 5.0.0 da API Pagamentos passa a ser possível a realização de Saques e Trocos através das funcionalidades disponíveis para tal no arranjo Pix. Para a realização das operações, as ITPs devem passar a reportar o payloadJWS completo que foi gerado pelo PSP do Recebedor, o qual contém todos os dados necessários para a validação das informações da operação em questão. 
    
-   Ao receber um pedido de criação de consentimento que esteja marcado como \`\`\`WITHDRAW\`\`\` ou \`\`\`CHANGE\`\`\` no campo \`\`\`/data/payment/purpose\`\`\`, o PSP do Pagador (Detentor) deverá consultar os dados do agente e do facilitador do serviço dentro do payloadJWS enviado pelo ITP, assim como os outros dados pertinentes a operação solicitada. 
    
-   A identificação também deverá ser realizada pelo PSP do Pagador ao enviar a mensagem \`\`\`PACS.008\`\`\` ao SPI, com a marcação correta da finalidade da transação sendo realizada, bem como outras informações necessárias para a correta liquidação da operação de Saque ou Troco. 
    
-   Apenas pagamentos iniciados por usuários com plenos poderes de aprovação (que não necessitam de outras aprovações para autorização do consentimento) são permitidos. Pagamentos dependentes de múltiplas alçadas aprovadoras devem ter o consentimento rejeitado, após a autorização do primeiro aprovador, com o motivo PERMISSAO\_INSUFICIENTE. 
    
-   Outras regras que devem ser observadas durante a validação e liquidação do QRCode de Pix Saque ou Pix Troco podem ser encontrados no Manual de Padrões para Iniciação do Pix, disponível no site do Banco Central.
    

\## Validações  
\*\*Validações\*\* (\*após o processo de DCR e obtenção de token client credential\*– não escopo dessa documentação)   
Durante a jornada de iniciação de pagamento, diferentes validações são necessárias pela instituição detentora  
de conta e devem ocorrer conforme a seguir:

1.  Na criação do consentimento (\*POST /consents\*);
    
2.  Na criação do pagamento - Síncrono (\*POST /payments\*);
    
3.  Validações na consulta do pagamento (\*GET /pix/payments/{paymentId}\*);
    
4.  Demais validações executadas durante o processamento assíncrono do pagamento pela detentora, poderão ser consultados pela iniciadora através do endpoint (\*GET /pix/payments/{paymentId}\*) previstos com retorno HTTP Code 200 - OK com status RJCT (Rejected) e rejectionReason;
    
5.  Demais validações executadas durante o processamento assíncrono do consentimento pela detentora poderão ser consultados pela iniciadora através do endpoint (\*GET /consents/{consentId}\*) previstos com retorno HTTP Code 200 – OK com status REJECTED e rejectionReason
    

\*\*Os tipos de validações dispostas abaixo não determinam a ordem em que as instituições devem implementá-las\*\*

1.  \*\*Validações na criação do consentimento (\_POST /consents\_)\*\* 
    

  
  1.1 \*\*Orientações Iniciais\*\*   
    &ensp;1.1.1 Não devem ser retornadas na resposta deste endpointinformações associadas ao usuário/cliente (ex.  insuficiência de saldo, conta inexistente/bloqueada).   
    &ensp;1.1.2 Não devem ser executadas validações no DICT (Diretório de Identificadores de Contas Transacionais do Pix), a partir dos dados compartilhados nesse \*endpoint\*. Tais  validações podem ocorrer somente na criação do pagamento;   
    &ensp;1.1.3 Não devem ser realizadas validações de informações sobre o usuário/cliente durante a criação do consentimento.  
  1.2 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;1.2.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;1.2.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;1.2.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;1.2.4 Validação de Claims (exceto data);   
      &emsp;1.2.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;1.2.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  1.3 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*    
    &ensp;1.3.1 \*\*Sintáticos\*\*   
      &emsp;1.3.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios são informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;1.3.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;1.3.2 \*\*Semânticos\*\*   
      &emsp;1.3.2.1 Forma de pagamento: Valida se a forma de pagamento é suportada pela detentora (FORMA\_PAGAMENTO\_INVALIDA) \*\*Obs. No detalhe do erro, a variável “modalidade” deve ser comunicada pela detentora da forma mais clara possível - ex. modalidade de pagamento não suportada (\_localInstrument\_ - QRES) ou tipo de arranjo pagamento não suportado (\_type\_ – ex. Pix / TED – previsto para inclusão futura);\*\*   
      &emsp;1.3.2.2 Data de pagamento: Valida se a data de pagamento enviada é válida para a forma de pagamento selecionada (DATA\_PAGAMENTO\_INVALIDA);   
      &emsp;1.3.2.3 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;1.3.2.4 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;1.3.2.5 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA).   
      &emsp;1.3.2.6  O propósito informado é incompatível com os dados presentes na transação. (PROPOSITO\_INVALIDO)

2.  \*\*Validações na criação do pagamento - Síncrono (\_POST /payments\_)\*\* 
    

  
  2.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token, jwt, assinatura)\*\*   
    &ensp;2.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;2.1.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED);   
    &ensp;2.1.3 Validação de assinatura da mensagem: Valida se assinatura das mensagens enviadas está correta – HTTP Code 400 (BAD\_SIGNATURE);   
    &ensp;2.1.4 Validação de Claims (exceto data);   
      &emsp;2.1.4.1 Valida se dados (aud, iss, iat e jti) são válidos - HTTP status code 403 – (INVALID\_CLIENT);   
      &emsp;2.1.4.2 Valida reuso de jti - HTTP Code 403 (INVALID\_CLIENT).   
  2.2 \*\*Casos de erro sintáticos e semânticos, previstos com retorno HTTP Code 422 - Unprocessable Entity (detalhamento adicional na documentação técnica da API):\*\*   
    &ensp;2.2.1 \*\*Sintáticos\*\*   
      &emsp;2.3.1.1 Envio de campos obrigatórios: Valida se todos os campos obrigatórios são informados (PARAMETRO\_NAO\_INFORMADO);   
      &emsp;2.3.1.2 Formatação de parâmetros: Valida se parâmetros informados obedecem a formatação especificada (PARAMETRO\_INVALIDO).   
    &ensp;2.2.2 \*\*Semânticos\*\*   
      &emsp;2.2.2.1 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento (SALDO\_INSUFICIENTE);   
      &emsp;2.2.2.2 Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora (VALOR\_ACIMA\_LIMITE);   
      &emsp;2.2.2.3 Valor informado (QR Code): Valida se valor enviado é válido para o QR Code informado (VALOR\_INVALIDO);   
      &emsp;2.2.2.4 Cobrança inválida: Valida expiração, vencimento e status (COBRANCA\_INVALIDA);   
      &emsp;2.2.2.5 Status Consentimento: Valida se o consentimento encontra-se em um dos estados finais “CONSUMED” ou “REJECTED" (CONSENTIMENTO\_INVALIDO);   
      &emsp;2.2.2.6 Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO)   
      &emsp;2.2.2.7 Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa (ex. chave Pix inválida, QRCode inválido, conta bloqueada);   
      &emsp;2.2.2.8 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
      &emsp;2.2.2.9 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
      &emsp;2.2.2.10 Idempotência: Valida se há divergência entre chave de idempotência e informações enviadas (ERRO\_IDEMPOTENCIA);   
      &emsp;2.2.2.11 Consentimento pendente de autorização: Em \`PARTIALLY\_ACCEPTED\` aguardando aprovação de múltiplas alçadas. Não consome nem invalida o consentimento (CONSENTIMENTO\_PENDENTE\_AUTORIZACAO).   
  2.3 \*\*Casos de erro para validações síncronas no DICT\*\*   
    &ensp;Nesse cenário, o pagamento não é criado, porém o consentimento deve ser alterado para o status CONSUMED Retorno esperado do endpoint POST/Payments: HTTP Code 422 - Unprocessable Entity:   
    &ensp;• Erro por dados inválidos: Conforme item \*\*2.2.2.8\*\*   
    &ensp;• Erro por suspeita de fraude: Conforme item \*\*2.2.2.9\*\* 

3.  \*\*Validações na consulta do pagamento (\_GET /pix/payments/{paymentId}\_)\*\* 
    

  
  3.1 \*\*Casos de erro relacionados às permissões de segurança para acesso à API (ex. certificado, access\_token)\*\*   
    &ensp;3.1.1 Validação de Certificado: Valida utilização de certificado correto durante processo de DCR - HTTP Code 401 (INVALID\_CLIENT);   
    &ensp;3.1.2 Validação de Access\_Token: Verifica se Access\_Token utilizado está correto - HTTP Code 401 (UNAUTHORIZED). 

4.  \*\*Demais validações executadas durante o processamento assíncrono do pagamento pela detentora, poderão ser consultados pela iniciadora através do endpoint \_GET /pix/payments/{paymentId}\_ previstos com retorno HTTP Code 200 - OK com status RJCT (Rejected) e rejectionReason conforme abaixo (detalhamento adicional na documentação técnica da API):\*\* 
    

  
  4.1 \*\*Demais validações durante processamento assíncrono\*\*   
    &ensp;4.1.1 Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento. No caso de um pagamento agendado, a validação só ocorre na tentativa de liquidação do pagamento (SALDO\_INSUFICIENTE);   
    &ensp;4.1.2 Limites da transação: Valida se valor (ou quantidade de transações) ultrapassa faixa de limite parametrizada na detentora (VALOR\_ACIMA\_LIMITE);   
    &ensp;4.1.3 Valor informado (QR Code): Valida se valor enviado é válido para o QR Code informado (VALOR\_INVALIDO);   
    &ensp;4.1.4 Cobrança inválida: Valida expiração, vencimento e status (COBRANCA\_INVALIDA);   
    &ensp;4.1.5 Divergência entre pagamento e consentimento: Valida se dados do pagamento são diferentes dos dados do consentimento (PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO);   
    &ensp;4.1.6 Recusado pela detentora: Valida se pagamento foi recusado pela detentora (PAGAMENTO\_RECUSADO\_DETENTORA), com a descrição do motivo de recusa (ex. chave Pix inválida, QRCode inválido, conta bloqueada);   
    &ensp;4.1.7 Detalhes do pagamento: Valida se determinado parâmetro informado obedece às regras de negócio (DETALHE\_PAGAMENTO\_INVALIDO);   
    &ensp;4.1.8 Demais validações não explicitamente informadas (ex. suspeita de fraude): (NAO\_INFORMADO);   
    &ensp;4.1.9 Validação SPI: Externaliza validações no SPI (PAGAMENTO\_RECUSADO\_SPI);   
    &ensp;4.1.10 Falha em agendamentos: Uma ou mais incidências de pagamento não foram possíveis de ser agendadas (FALHA\_AGENDAMENTO\_PAGAMENTOS);   
    &ensp;4.1.11 Divergências entre dados das chaves pix para agendamento e liquidação: O pagamento agendado não pode ser enviado para liquidação devido a divergências entre dados da chave recebedora utilizada para criação do agendamento com a chave recebedora em momento de liquidação (CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO);   
    &ensp;4.1.12 Erro de infraestrutura na consulta ao DICT: Ocorreu uma falha de infraestrutura durante a consulta ao DICT (FALHA\_INFRAESTRUTURA\_DICT);    
    &ensp;4.1.13 Erro de infraestrutura na consulta ao ICP: Ocorreu uma falha de infraestrutura durante a consulta ao ICP (FALHA\_INFRAESTRUTURA\_ICP);    
    &ensp;4.1.14 Erro de infraestrutura na comunicação com o PSP do recebedor: Ocorreu uma falha de infraestrutura durante a comunicação com o PSP do recebedor (FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR);    
    &ensp;4.1.15 Erro de infraestrutura interno na detentora: Ocorreu uma falha de infraestrutura interna na detentora durante o processamento do pagamento (FALHA\_INFRAESTRUTURA\_DETENTORA);    
    &ensp;4.1.16 Erro de infraestrutura na consulta ao SPI: Ocorreu uma falha de infraestrutura durante a consulta ao SPI (FALHA\_INFRAESTRUTURA\_SPI).    
  4.2 \*\*Casos de erro para validações assíncronas no DICT\*\*   
    &ensp;Neste cenário o pagamento é criado com sucesso (status RCVD) e o consentimento é consumido (status CONSUMED), porém, as validações contra o DICT só ocorrerão de forma assíncrona e em caso de negativa será percebido pela iniciadora na consulta do pagamento (GET /Payments).   
    &ensp;Retorno esperado do endpoint GET /Payments: HTTP Code 200 - OK.   
    &ensp;Status do Pagamento: RJCT (Rejected), com as seguintes opções rejectionReason:   
    &ensp;• Erro por dados inválidos: Conforme item \*\*4.1.7\*\*;   
    &ensp;• Erro por suspeita de fraude: Conforme item \*\*4.1.8\*\*.

5.  \*\*Demais validações executadas durante o processamento assíncrono do consentimento pela detentora poderão ser consultados pela iniciadora através do endpoint \_GET /consents/{consentId}\_ previstos com retorno HTTP Code 200 – OK com status REJECTED e rejectionReason conforme abaixo:\*\* 
    

  
  5.1 \*\*Validações durante o processamento assíncrono\*\*   
    &ensp;5.1.1 - Falha de infraestrutura: Ocorreu algum erro interno na detentora durante processamento da criação do consentimento (FALHA\_INFRAESTRUTURA)   
    &ensp;5.1.2 - Tempo de autorização expirado: O usuário não confirmou o consentimento e o mesmo expirou (TEMPO\_EXPIRADO\_AUTORIZACAO);   
    &ensp;5.1.3 - Rejeitado pelo usuário: O usuário explicitamente rejeitou a autorização do consentimento (REJEITADO\_USUARIO);   
    &ensp;5.1.4 - Mesma conta origem/destino: A conta indicada pelo usuário para recebimento é a mesma selecionada para o pagamento (CONTAS\_ORIGEM\_DESTINO\_IGUAIS);   
    &ensp;5.1.5 - Tipo de conta inválida: A conta indicada não permite operações de pagamento (CONTA\_NAO\_PERMITE\_PAGAMENTO);   
    &ensp;5.1.6 - Saldo do usuário: Valida se a conta selecionada possui saldo suficiente para realizar o pagamento. Essa validação não deverá ocorrer no caso de um pagamento agendado (SALDO\_INSUFICIENTE);   
    &ensp;5.1.7 - Limites da transação: Valida se o valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente (VALOR\_ACIMA\_LIMITE);   
    &ensp;5.1.8 - QRCode inválido: O QRCode utilizado para a iniciação de pagamento não é válido (QRCODE\_INVALIDO);   
    &ensp;5.1.9 - Valor inválido: O valor enviado não é válido para o QR Code informado (VALOR\_INVALIDO);   
    &ensp;5.1.10 - Não informado: Demais validações não explicitamente informadas (ex. suspeita de fraude) e consentimentos rejeitados em versões que não existiam o campo rejectionReason na API de Pagamentos (NAO\_INFORMADO)   
    &ensp;5.1.11 - Tempo expirado consumo: O usuário não finalizou o fluxo de pagamento e o consentimento expirou (TEMPO\_EXPIRADO\_CONSUMO).    
    &ensp;5.1.12 - Autenticação divergente: O usuário autenticado no ambiente da detentora não é o mesmo usuário autenticado no ambiente da iniciadora e que criou o consentimento (AUTENTICACAO\_DIVERGENTE).    
    &ensp;5.1.13 - Permissão insuficiente: A solicitação de Saque ou Troco foi realizada por um usuário sem plenos poderes de aprovação (PERMISSAO\_INSUFICIENTE).   
  5.2 \*\*\[Momentos obrigatórios de validação dos rejectionReasons de acordo com o funil de consentimentos.\](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/150863940) Para casos em que um consentimento for rejeitado por mais de um motivo, seguir a ordem de prioridade da tabela.\*\*  
  \`\`\`  
  |----------------------------------|------------------------------|---------------------|  
  | Etapas do funil de consentimento | rejectionReason/code         | Ordem de prioridade |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | TEMPO\_EXPIRADO\_AUTORIZACAO   |          1          |  
  | Início da autenticação           | FALHA\_INFRAESTRUTURA         |          2          |  
  |                                  | NAO\_INFORMADO                |          3          |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | TEMPO\_EXPIRADO\_AUTORIZACAO   |          1          |  
  |                                  | REJEITADO\_USUARIO            |          2          |  
  | Conclusão da autenticação        | FALHA\_INFRAESTRUTURA         |          3          |  
  |                                  | NAO\_INFORMADO                |          4          |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | AUTENTICACAO\_DIVERGENTE      |          1          |  
  |                                  | CONTA\_NAO\_PERMITE\_PAGAMENTO  |          2          |  
  |                                  | CONTAS\_ORIGEM\_DESTINO\_IGUAIS |          3          |  
  |                                  | VALOR\_INVALIDO               |          4          |  
  | Autorização do cliente           | QRCODE\_INVALIDO              |          5          |  
  |                                  | VALOR\_ACIMA\_LIMITE           |          6          |  
  |                                  | SALDO\_INSUFICIENTE           |          7          |  
  |                                  | FALHA\_INFRAESTRUTURA         |          8          |  
  |                                  | NAO\_INFORMADO                |          9          |  
  |----------------------------------|------------------------------|---------------------|  
  |                                  | FALHA\_INFRAESTRUTURA         |          1          |  
  | Authorisation code emitido       | NAO\_INFORMADO                |          2          |  
  |                                  | TEMPO\_EXPIRADO\_CONSUMO       |          3          |  
  |----------------------------------|------------------------------|---------------------|  
  \`\`\`  
  5.3 \*\*Momentos obrigatórios de validação dos rejectionReasons de consentimentos autorizados via JSR\*\*   
  Consentimentos autorizados a partir do fluxo sem redirecionamento possuem um funil de conversão diferente, dado que não há o redirecionamento e este é um grande segregador das etapas do funil.   
  Devido a isso, as validações e a ordem que estas devem ser feitas, descritas no tópico anterior, não se aplicam integralmente aos consentimentos que foram autorizados no fluxo sem redirecionamento. Para consentimentos autorizados via fluxo sem redirecionamento, os únicos motivos de rejeição cabíveis são:

-   TEMPO\_EXPIRADO\_AUTORIZACAO – Utilizado quando o gesto FIDO não foi realizado a tempo pelo cliente final
    
-   TEMPO\_EXPIRADO\_CONSUMO – Utilizado quando o ITP, em posse do consentimento autorizado, não envia o pagamento.
    
-   FALHA\_INFRAESTRUTURA – Utilizado quando uma falha sistêmica impediu o avanço no processo do consentimento. 
    

  
  Demais validações que antes ocorriam no consentimento, agora devem ocorrer apenas em momento de pagamento. Permitindo assim que a detentora de contas tenha tempo de realizar as validações de maneira assíncrona a autorização do consentimento

  ### Cancelamento de Pagamentos  
  Existem dois \`endpoints\` para cancelamento de pagamentos, um deles é o \_PATCH /pix/payments/{paymentId}\_ e o outro é o \_PATCH /consents/{consentId}/pix/payments\_.

-   O \_PATCH /pix/payments/{paymentId}\_ deve ser utilizado para o cancelamento de um pagamento de forma unitária. Não deve ser utilizado para o cancelamento de todos os agendamentos recorrentes associados a um consentimento.
    
-   O \_PATCH /consents/{consentId}/pix/payments\_ deve ser utilizado no cancelamento de todas as ocorrências de pagamentos agendados presentes em uma recorrência de pagamentos. Todos os pagamentos associados ao consentimento informado e passíveis de cancelamento (ainda não liquidados, com os status PDNG e SCHD) deverão ser cancelados.
    

  
   
  ## Quantidade máxima permitida para agendamentos recorrentes

  A quantidade máxima de pagamentos que podem transitar do iniciador para o detentor são de 60 pagamentos, independente do modelo de recorrência definido no consentimento, respeitando o prazo máximo de dois anos para agendamentos.  
  Caso a opção de recorrência enviada pelo iniciador não respeite a regra acima, o detentor deve retornar o erro 422 "PARAMETRO\_INVALIDO" com o detalhe "Quantidade permitida de pagamentos excedida".  

paths - Alterado

/pix/payments/consents/{consentId}

/consents/{consentId}/pix/payments

## POST /consents

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

post/requestBody/data/payment/ibgeTownCode

Alterado - "description"

Alteração

O campo ibgetowncode, no arranjo PIX, tem o mesmo comportamento que o campo codMun descrito no manual do PIX.   
Caso a informação referente ao município não seja enviada; o PSP do recebedor assumirá que não existem feriados estaduais e municipais no período em questão;   
No caso de QRCode Dinâmico com vencimento, deve prevalecer o código do município do usuário pagador informado pelo prestador do serviço de iniciação.   

O campo ibgetowncode, no arranjo PIX, tem o mesmo comportamento que o campo codMun descrito no manual do PIX.   
Caso a informação referente ao município não seja enviada; o PSP do recebedor assumirá que não existem feriados estaduais e municipais no período em questão;   
No caso de QRCode Dinâmico com vencimento, deve prevalecer o código do município do usuário pagador informado pelo prestador do serviço de iniciação.    
\[Restrição\] Para QRCode Dinâmico com vencimento é obrigatório o envio desse parâmetro pelo ITP para que o Detentor possa utiliza-lo em sua consulta. É obrigatório que o Detentor utilize o valor informado pelo ITP em sua consulta ao QRCode no PSP Recebedor  

post/requestBody/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento.  
O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em  
relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+730 corridos a  
partir da data do consentimento, também considerando o fuso horário de Brasília.  

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.   
\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em relação à data de criação do consentimento. O prazo máximo admitido para agendamento é de dois anos, contados a partir da data de criação do consentimento, limitando-se ao dia e mês correspondentes no segundo ano subsequente (Ex.: consentimento criado em 10/07/2026 permite agendamento até 10/07/2028).  

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

post/responses/201/data/payment/ibgeTownCode

Alterado - "description"

Alteração

O campo ibgetowncode, no arranjo PIX, tem o mesmo comportamento que o campo codMun descrito no manual do PIX.   
Caso a informação referente ao município não seja enviada; o PSP do recebedor assumirá que não existem feriados estaduais e municipais no período em questão;   
No caso de QRCode Dinâmico com vencimento, deve prevalecer o código do município do usuário pagador informado pelo prestador do serviço de iniciação.   

O campo ibgetowncode, no arranjo PIX, tem o mesmo comportamento que o campo codMun descrito no manual do PIX.   
Caso a informação referente ao município não seja enviada; o PSP do recebedor assumirá que não existem feriados estaduais e municipais no período em questão;   
No caso de QRCode Dinâmico com vencimento, deve prevalecer o código do município do usuário pagador informado pelo prestador do serviço de iniciação.    
\[Restrição\] Para QRCode Dinâmico com vencimento é obrigatório o envio desse parâmetro pelo ITP para que o Detentor possa utiliza-lo em sua consulta. É obrigatório que o Detentor utilize o valor informado pelo ITP em sua consulta ao QRCode no PSP Recebedor  

post/responses/201/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento.  
O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em  
relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+730 corridos a  
partir da data do consentimento, também considerando o fuso horário de Brasília.  

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.   
\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em relação à data de criação do consentimento. O prazo máximo admitido para agendamento é de dois anos, contados a partir da data de criação do consentimento, limitando-se ao dia e mês correspondentes no segundo ano subsequente (Ex.: consentimento criado em 10/07/2026 permite agendamento até 10/07/2028).  

## GET /consents/{consentId}

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

get/responses/200/data/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

get/responses/200/data/payment/ibgeTownCode

Alterado - "description"

Alteração

O campo ibgetowncode, no arranjo PIX, tem o mesmo comportamento que o campo codMun descrito no manual do PIX.   
Caso a informação referente ao município não seja enviada; o PSP do recebedor assumirá que não existem feriados estaduais e municipais no período em questão;   
No caso de QRCode Dinâmico com vencimento, deve prevalecer o código do município do usuário pagador informado pelo prestador do serviço de iniciação.   

O campo ibgetowncode, no arranjo PIX, tem o mesmo comportamento que o campo codMun descrito no manual do PIX.   
Caso a informação referente ao município não seja enviada; o PSP do recebedor assumirá que não existem feriados estaduais e municipais no período em questão;   
No caso de QRCode Dinâmico com vencimento, deve prevalecer o código do município do usuário pagador informado pelo prestador do serviço de iniciação.    
\[Restrição\] Para QRCode Dinâmico com vencimento é obrigatório o envio desse parâmetro pelo ITP para que o Detentor possa utiliza-lo em sua consulta. É obrigatório que o Detentor utilize o valor informado pelo ITP em sua consulta ao QRCode no PSP Recebedor  

get/responses/200/data/payment/schedule/oneOf/0/single/date

Alterado - "description"

Alteração

Define a data alvo da liquidação do pagamento.  
O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.

\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em  
relação a data do consentimento considerando o fuso horário de Brasília e deverá ser no máximo D+730 corridos a  
partir da data do consentimento, também considerando o fuso horário de Brasília.  

Define a data alvo da liquidação do pagamento. O fuso horário de Brasília deve ser utilizado para criação e racionalização sobre os dados deste campo.   
\[Restrição\] Esse campo deverá sempre ser no mínimo D+1 corrido, ou seja, a data imediatamente posterior em relação à data de criação do consentimento. O prazo máximo admitido para agendamento é de dois anos, contados a partir da data de criação do consentimento, limitando-se ao dia e mês correspondentes no segundo ano subsequente (Ex.: consentimento criado em 10/07/2026 permite agendamento até 10/07/2028).  

get/responses/200/data/rejectionReason/code

Alterado - "description"

Alteração

Define o código da razão pela qual o consentimento foi rejeitado

-   AUTENTICACAO\_DIVERGENTE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   TEMPO\_EXPIRADO\_CONSUMO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   QRCODE\_INVALIDO
    

  

Define o código da razão pela qual o consentimento foi rejeitado

-   AUTENTICACAO\_DIVERGENTE
    
-   VALOR\_INVALIDO
    
-   NAO\_INFORMADO
    
-   FALHA\_INFRAESTRUTURA
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO
    
-   TEMPO\_EXPIRADO\_CONSUMO
    
-   REJEITADO\_USUARIO
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO
    
-   SALDO\_INSUFICIENTE
    
-   VALOR\_ACIMA\_LIMITE
    
-   QRCODE\_INVALIDO
    
-   PERMISSAO\_INSUFICIENTE
    

  

get/responses/200/data/rejectionReason/code/enum

Adicionado - "PERMISSAO\_INSUFICIENTE"

Adição

enum

get/responses/200/data/rejectionReason/detail

Alterado - "description"

Alteração

Contém informações adicionais ao consentimento rejeitado.

-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador​
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado;
    
-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\].
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo.
    
-   TEMPO\_EXPIRADO\_CONSUMO: O usuário não finalizou o fluxo de pagamento e o consentimento expirou;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento.
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento.
    
-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente.
    
-   QRCODE\_INVALIDO: O QRCode utilizado para a iniciação de pagamento não é válido.
    

\[Restrição\] Caso consentimento rejeitado de versões nas quais não havia o campo rejectionReason retornar o seguinte detail: Motivo de rejeição inexistente em versões anteriores.  

Contém informações adicionais ao consentimento rejeitado.

-   AUTENTICACAO\_DIVERGENTE : Usuário autenticado no detentor diverge do usuário autenticado no iniciador​
    
-   VALOR\_INVALIDO: O valor enviado não é válido para o QR Code informado;
    
-   NAO\_INFORMADO: Não informada pela detentora de conta;
    
-   FALHA\_INFRAESTRUTURA: \[Descrição de qual falha na infraestrutura inviabilizou o processamento\].
    
-   TEMPO\_EXPIRADO\_AUTORIZACAO: Consentimento expirou antes que o usuário pudesse confirmá-lo.
    
-   TEMPO\_EXPIRADO\_CONSUMO: O usuário não finalizou o fluxo de pagamento e o consentimento expirou;
    
-   REJEITADO\_USUARIO: O usuário rejeitou a autorização do consentimento
    
-   CONTAS\_ORIGEM\_DESTINO\_IGUAIS: A conta selecionada é igual à conta destino e não permite realizar esse pagamento.
    
-   CONTA\_NAO\_PERMITE\_PAGAMENTO: A conta selecionada é do tipo \[salario/investimento/liquidação/outros\] e não permite realizar esse pagamento.
    
-   SALDO\_INSUFICIENTE: A conta selecionada não possui saldo suficiente para realizar o pagamento.
    
-   VALOR\_ACIMA\_LIMITE: O valor ultrapassa o limite estabelecido \[na instituição/no arranjo/outro\] para permitir a realização de transações pelo cliente.
    
-   QRCODE\_INVALIDO: O QRCode utilizado para a iniciação de pagamento não é válido.
    
-   PERMISSAO\_INSUFICIENTE: A solicitação de Saque ou Troco foi realizada por um usuário sem plenos poderes de aprovação.  
    

\[Restrição\] Caso consentimento rejeitado de versões nas quais não havia o campo rejectionReason retornar o seguinte detail: Motivo de rejeição inexistente em versões anteriores.  

## POST /pix/payments

### Request

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/requestBody/data/items/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

post/responses/201/data/items/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

## GET /pix/payments/{paymentId}

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

get/responses/200/data/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

## PATCH pix/payments/{paymentId}

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

patch/responses/200/data/payment/amount

Alterado - "description"

Alteração

Valor da transação com 2 casas decimais. Para QR Code estático com valor pré-determinado no QR Code e para QR Code dinâmico de cobrança ou QRCode Dinâmico de Pix Saque com indicação de que o valor não pode ser alterado ("modalidadeAlteracao" igual a 0): O campo amount deve ser preenchido com o valor estabelecido no QR Code.   
Caso seja preenchido com valor divergente do QR Code que não permita alteração, deve ser retornado um erro HTTP Status 422 VALOR\_INVALIDO.  

Valor da transação com 2 casas decimais. Para pagamento de QRCodes, a composição do valor segue as regras abaixo, de acordo com o tipo de QRCode e o produto associado a ele:   
 ▪ QR Code Estático: Se o QR Code contém valor, o campo amount deve ser preenchido com esse valor. Se o valor não estiver presente, o valor deve ser preenchido pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança Imediata (COB): O campo amount deve ser preenchido com o valor da cobrança (valor.original). Quando valor.modalidadeAlteracao for igual a 1, o valor pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento.   
 ▪ QR Code Dinâmico de Cobrança com Vencimento (COBV): O campo amount deve ser preenchido com o valor final da cobrança, correspondente à composição: valor original, deduzidos eventuais abatimentos e descontos, acrescidos de eventuais juros e multa. O campo modalidadeAlteracao não se aplica a COBV; o valor não pode ser alterado pelo usuário pagador.   
 ▪ QR Code Dinâmico de Pix Saque: O campo amount deve ser preenchido com o valor do saque (valor.retirada.saque.valor). Quando valor.retirada.saque.modalidadeAlteracao for igual a 1, o valor do saque pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ QR Code Dinâmico de Pix Troco: O campo amount deve ser preenchido com o valor total da transação, correspondente à soma do valor da compra (valor.original) com o valor do troco (valor.retirada.troco.valor). O valor da compra (valor.original) não pode ser alterado. Quando valor.retirada.troco.modalidadeAlteracao for igual a 1, apenas o valor do troco pode ser alterado pelo usuário pagador, em ambiente da ITP, antes da criação do consentimento e respeitados os limites definidos pelo facilitador de serviço de saque.   
 ▪ Para todos os cenários em que o valor não pode ser alterado, o campo amount deve ser preenchido com o valor estabelecido no QR Code. Caso o campo amount seja preenchido com valor divergente do esperado, deve ser retornado o erro HTTP Status 422 com código VALOR\_INVALIDO.   

## PATCH consents/{consentId}/pix/payments

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
