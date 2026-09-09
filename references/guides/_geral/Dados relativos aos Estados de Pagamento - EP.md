# Dados relativos aos Estados de Pagamento - EP

v 1.03

## **Objetivo**

Complementar o reporte do iniciador e disponibilizar uma API dedicada para que a detentora reporte estados determinados dos pagamentos (agendados, liquidados, rejeitados ou cancelados), permitindo a obtenção de informações precisas e consolidadas.

Para isso, serão disponibilizadas uma nova API e novos campos de additionalInfo, conforme descritos abaixo.

A especificação da API pode ser encontrada aqui: API Estados de Pagamento - SV

## **Terminologia**

Os termos abaixo estão no contexto da Plataforma de Coleta de Métricas, que por sua vez está no contexto do Open Finance Brasil.  

**Client e Server**  

Em uma interação, a parte que solicita os dados é chamada de _client_, ao passo que a parte que devolve os dados é _server_. Portanto, supondo que A faça uma consulta em B pelos dados de uma conta, esses dados serão transmitidos por quem recebeu a solicitação, e recebidos por quem a fez. Neste caso, A é o _client_ e B é o _server_.   

## **Novos campos de additionalInfo**

**/payments/v4/consents**

**/payments/v5/consents**

POST / HTTP code 201

**Campo** 

**Descrição** 

**paymentDate**

Data em que o pagamento será realizado (mutualmente excludente com o campo _data.payment.schedule_)

**paymentSchedule**

Estrutura responsável pela parametrização dos pagamentos que acontecerão sob aquele consentimento (mutualmente excludente com o campo _data.payment.date_).

É esperado o envio do objeto, independente do tempo de agendamento

**/payments/v4/pix/payments**

**/payments/v5/pix/payments**

POST / HTTP code 201

**Campo** 

**Descrição** 

**paymentList**

Lista de dados de pagamentos com agendamento imediatos, agendados ou recorrentes.

**paymentId**

Código ou identificador único informado pela instituição detentora da conta para representar a iniciação de pagamento

**consentId**

Identificador único do consentimento criado para a iniciação de pagamento solicitada

**statusUpdateDateTime**

Data e hora da última atualização da iniciação de pagamento

**status**

Estado atual do pagamento

**rejectionReasonCode**

Código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

**rejectionReasonDetail**

Detalhe sobre o código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

**/automatic-payments/v2/pix/recurring-payments**

POST / HTTP code 201

**Campo** 

**Descrição** 

**recurringPaymentDate**

Data em que o pagamento será realizado

**/automatic-payments/v2/pix/recurring-payments**

GET / HTTP code 200

**Campo** 

**Descrição** 

**paymentList**

Lista de dados de pagamentos com agendamento imediatos, agendados ou recorrentes.

**paymentId**

Código ou identificador único informado pela instituição detentora da conta para representar a iniciação de pagamento

**consentId**

Identificador único do consentimento criado para a iniciação de pagamento solicitada

**statusUpdateDateTime**

Data e hora da última atualização da iniciação de pagamento

**status**

Estado atual do pagamento

**rejectionReasonCode**

Código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

**rejectionReasonDetail**

Detalhe sobre o código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

## **Descrição funcional da nova API**

**Campo** 

**Descrição** 

**eventDateTime¹**

Data e hora associada à mudança de estados reportados abaixo, como agendamento, liquidação, rejeição ou cancelamento. Formato AAAA-MM-DD hh:mm:ss reportado em UTC 0

**paymentType¹**

Tipo do pagamento realizado. _Enum_ esperado: AUTOMATIC, IMMEDIATE, RECURRENT, SCHEDULED, SWEEPING

**clientOrgId¹**

Identificador da organização cliente que realizou ou solicitou o pagamento

**consentId¹**

Identificador único do consentimento criado para aquele pagamento

**paymentId¹**

Código único para identificar a transação de pagamento

**paymentStatus¹**

_Status_ de agendamento ou final do pagamento. Deve seguir o _enum_ especificado. (ACSC, RJCT, CANC e SCHD)

**statusReasonCode**

Campo atrelado ao _status_ do pagamento. Quando o _status_ for RJCT (Rejected), o valor deve ser preenchido com o motivo da rejeição (valores previstos em _rejectionReason.Code_). Quando o _status_ for CANC (Cancelled), o valor deve ser preenchido com motivo do cancelamento (valores previstos em _cancellationReason.Code_)

¹ Campos com preenchimento obrigatório para que a mensagem seja considerada válida na ingestão 

## **Detalhes operacionais**

**Parâmetro** 

**Regra**

**Justificativa**

**Consulta de reporte**

Permitir a consulta de um reporte em específico utilizando seu identificador único (fapiInteractionId)

-   Garantir que instituições possam recuperar informações previamente enviadas, possibilitando a rastreabilidade
    

**Frequência de envio**

Assim que o Pix entrar no estado a ser reportado ou diariamente

-   Alinha-se com a prática atual das instituições que enviam reportes diários
    
-   Proporciona dados mais atualizados e granulares
    
-   Facilita a detecção até D+1 de tendências e anomalias
    

**Período de referência**

Das 00:00:00 às 23:59:59 de uma mesma Data do campo _eventDatetime_ considerando o como referência o fuso horário de Brasília (UTC-3)

-   Cada reporte deve possuir registros de apenas uma data em UTC-3
    

**Prazo de SLA esperado de Reporte**

Transações realizadas dentro da janela de Período de Referência devem ser reportadas até 08:00 (horário de Brasília) do D+1

-   Garante que os dados sejam processados em um _pipeline_ uniforme e respeitem a janela única de processamento
    

**Limite máximo de envio**

7 dias a contar do _eventDatetime_

-   Garante janela de ajustes e recebimento de dados, conforme padrão utilizado pelo ecossistema
    

## **Regras de validação**

-   Verificar se o _clientOrgId_ informado existe no ecossistema. Se não, descartar o registro particular e criticar
    
-   Garantir que _eventDateTime_ seja sempre anterior ou igual à data de _reportingDateTime_. Se não, descartar
    
-   Para o SLA de envio de reportes, confirmar que o envio dos dados relativos ao período de referência que consta em _eventDateTime_ ocorreu até D+1 às 08:00
    
-   Para _paymentType_ RECURRENT, validar que não há mais de 60 _paymentIds_ por _consentId_s, independentemente do modelo de recorrência definido no consentimento. A data do último pagamento agendado não pode ultrapassar o correspondente dia e mês do segundo ano subsequente à data de criação do consentimento (Ex.: consentimento criado em 15/03/2026 admite agendamentos até 15/03/2028)_._ Se houverem mais de 60 ou a data do último pagamento não estiver de acordo com a regra, ingerir e criticar.
    
-   Verificar se o campo _status_ for preenchido com RJCT (Rejected), validar que o campo _statusReasonCode_ contém um código válido conforme definido em _rejectionReason.code._ Se não, ingerir e criticar
    
-   Verificar se o campo _status_ for preenchido com CANC (Cancelled), validar que o campo _statusReasonCode_ contém um código válido de cancelamento conforme definido em _cancellationReason_._code_ Se não, ingerir e criticar
    
-   No GET, garantir que o _reportId_ fornecido pertence à instituição autenticada (por meio do _token_ de acesso)
    
-   No POST, garantir que o limite de envio por requisição seja respeitado, com um máximo de 5.000 registros por requisição
    

## **Diagrama de relacionamento**

-   _reportId_ (interno - único por requisição)
    
-   _reportingDateTime_ (interno – único por requisição)
    
-   _eventDateTime_ (pode ter múltiplos - referente a alteração do _status_ para cada pagamento reportado)
    
-   └── _clientOrgId_ (pode ter múltiplos)
    

    └── _paymentType_ (múltiplos por clientOrgId - IMMEDIATE, SCHEDULED, RECURRENT, etc.)

        └── _consentId_ (múltiplos por _paymentType_)

            └── _paymentId_ (múltiplos por consentId, até 60 para RECURRENT)

                └── _status, statusReasonCode_ (específicos para cada _paymentId_)

![image-20250819-162819.png](images/image-20250819-162819.png)

## **Documentação da API**

Documentação da API - PCM
