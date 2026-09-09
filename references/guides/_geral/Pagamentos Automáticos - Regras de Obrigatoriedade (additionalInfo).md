# Pagamentos Automáticos - Regras de Obrigatoriedade (additionalInfo)

v 1.10

**Guia de leitura**

1.  Se o campo não está listado, é porque não existe a obrigatoriedade de enviá-lo.
    
2.  Nos endpoints, a referência “v_x_” indica que se aplicam às versões listadas na coluna “Versões”. Por exemplo, Endpoint “open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}” e Versões “v1 v2” significa que o endpoint é válido para as versões 1 e 2.
    

Dica: para rolar a tabela horizontalmente, segure SHIFT e utilize o botão de rolagem do mouse.

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Pagamentos Automáticos

**Campo**

**Definição**

**Regra de preenchimento**

**Tipo**

**Roles**

**Http code**

**Métodos**

**Domínio**

**Endpoints**

**Versões**

**Padrão**

**Exemplo**

amountType

Valida se o serviço contratado possui maior conversão em relação ao tipo do valor definido, sendo ele fixo ou variável​

-   Se não enviando nem ".data.recurringConfiguration.automatic.fixedAmount" e nem ".data.recurringConfiguration.automatic.maximumVariableAmount", “VARIAVEL”; ou
    
-   Se enviado fixedAmount, “FIXO”; ou
    
-   Se enviado maximumVariableAmount, “VARIAVEL”
    

Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

FIXO, VARIAVEL

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

FIXO

authorisationFlow

Identifica o fluxo de autorização em que um pagamento ou operação foi solicitado. Descreve como o autenticador (por exemplo, um dispositivo FIDO) está anexado ao cliente que realiza a autenticação (ex: platform para autenticadores integrados como Face ID ou cross-platform para chaves de segurança USB).

O campo deve ser preenchido com a string obtida em ".data.authorisationFlow". Se a informação for uma lista, utilize apenas o primeiro item. Caso a string de ".data.authorisationFlow" seja nula, preencha obrigatoriamente com HYBRID\_FLOW. É fundamental que sempre seja reportado um dos valores do enum (como HYBRID\_FLOW, CIBA ou FIDO), e nunca um valor nulo, pois para fins de telemetria é necessário identificar explicitamente qual fluxo de autorização foi utilizado, independentemente da permissão de valor nulo nas especificações das APIs do Open Finance.

string

CLIENT

Todos

POST  
GET  
PATCH

CIBA\_FLOW, FIDO\_FLOW, HYBRID\_FLOW

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

HYBRID\_FLOW

authorisationFlowIntent

Permite a desambiguação e clara distinção entre as jornadas de pagamento que demandam ou não redirecionamento do usuário, já na etapa de provisionamento do consentimento

O campo deve ser preenchido obrigatoriamente com um dos valores do enum: HYBRID\_FLOW, CIBA\_FLOW ou FIDO\_FLOW. A instituição iniciadora deve comunicar a intenção de fluxo de autorização que será utilizado na jornada de pagamento. Esta informação é essencial para a desambiguação das jornadas de pagamento na etapa de consentimento.

 **Nota técnica:** Esta informação não existe tecnicamente nesta etapa da API de Consents; cabe à instituição iniciadora, por seu conhecimento prévio, reportar sua intenção de fluxo que será efetivamente utilizado na transação.

string

CLIENT

Todos

POST  
GET  
PATCH

CIBA\_FLOW, FIDO\_FLOW, HYBRID\_FLOW

/open-banking/automatic-payments/v_x_/recurring-consents

v2

HYBRID\_FLOW

cancellationReason

Identifica o estado que o pagamento estava quando foi cancelado​

Preencher com o valor do campo ".cancellation.reason"  
Deve ser enviado quando em um GET ou POST /payment e o campo status é "CANC" ou em um PATCH /payment (que é a API de cancelamento).

string

CLIENT

2xx

POST  
GET  
PATCH

CANCELADO\_AGENDAMENTO, CANCELADO\_PENDENCIA

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

CANCELADO\_PENDENCIA

cancelledFrom

Informa o meio pelo qual foi realizado o cancelamento

Preencher com o valor do campo ".cancellation.cancelledFrom"  
Status do pagamento deve ser "CANC"

string

CLIENT

2xx

POST  
GET  
PATCH

DETENTORA, INICIADORA

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

INICIADORA

companyProfileInfo

Objeto JSON que representa o perfil da Pessoa Jurídica (PJ) do cliente, contendo informações como a natureza jurídica e o porte da empresa, conforme a classificação oficial da Receita Federal do Brasil.  
Os itens indentados abaixo pertencem ao objeto companyProfileInfo e seguem as mesmas regras de obrigatoriedade.

**Obrigatório para clientes PJ**. O objeto deve conter um objeto de perfil da empresa. As informações de natureza jurídica e porte devem ser obtidas prioritariamente da **API oficial Consulta CNPJ (RFB/SERPRO) ou dos Dados Abertos do CNPJ (RFB)**, conforme o Dicionário de Dados do CNPJ da Receita Federal. Este objeto deve ser enviado como parte do additionalInfo ao consumir as APIs de criação de consentimento para dados e serviços.

-   [Consulta CNPJ — Catálogo de APIs governamentais](https://www.gov.br/conecta/catalogo/apis/consulta-cnpj) (API/Swagger)
    
-   [Portal de Dados Abertos](https://dados.gov.br/dados/conjuntos-dados/cadastro-nacional-da-pessoa-juridica---cnpj) (arquivo de dados)
    

object

CLIENT

Todos

POST

/open-banking/automatic-payments/v_x_/recurring-consents

v2

Objeto JSON

{ "naturezaJuridica": "2135", "porteEmpresa": "01" }

naturezaJuridica

Código que identifica a constituição jurídico-institucional da entidade, conforme a Tabela de Natureza Jurídica do IBGE, categorizando-a em: Administração pública; Entidades empresariais; Entidades sem fins lucrativos; Pessoas físicas e organizações internacionais; e Outras instituições extraterritoriais.

**Obrigatório para clientes PJ.** O cliente (receptor/iniciador) deve obter essa informação a partir de fontes oficiais (ex., Governo Federal/Dados Abertos/Base CNPJs ou API do SERPRO), com base no CNPJ do usuário, e reportá-la como parte do additionalInfo quando houver consumo as APIs de criação de consentimento para compartilhamento de dados e serviços.

string

CLIENT

Todos

POST

/open-banking/automatic-payments/v_x_/recurring-consents

v2

^\\d{4}$

2135

porteEmpresa

Código numérico que identifica o porte da empresa do cliente Pessoa Jurídica (PJ), conforme a classificação oficial da Receita Federal do Brasil.

**Obrigatório para clientes PJ**. O receptor/iniciador, que detém o CNPJ do usuário, é responsável por obter o código do porte da empresa. Esta informação deve ser consultada e validada a partir de fontes oficiais, como a base de Dados Abertos do CNPJ ou a API do SERPRO, ambas mantidas pelo Governo Federal, e conforme o Dicionário de Dados do CNPJ da Receita Federal. O valor deve ser enviado como parte do additionalInfo quando houver consumo as APIs de criação de consentimento para compartilhamento de dados e serviços.

string

CLIENT

Todos

POST

/open-banking/automatic-payments/v_x_/recurring-consents

v2

^\\d{2}$

01

dropReason

Razão pela qual um usuário não conseguiu prosseguir em uma jornada, especificamente no contexto de consentimentos

O campo dropReason deve ser adicionado nas informações do campo additionalInfo que deverá ser enviado no reporte do provedor do serviço consumido (papel SERVER)  
O reporte deverá ser feito por todos os transmissores de dados e detentoras de conta. Para os casos em que ocorram falhas técnicas que impossibilitem a verificação do CPF/CNPJ (incluindo, mas não se limitando, a erros HTTP 4xx, 500 ou timeout na resposta), o reporte deve ser realizado com o valor NO\_CREDENTIAL, Em jornadas de múltipla alçada de pessoas jurídicas, quando a autenticação é bem-sucedida mas os poderes constituídos são insuficientes para finalização do Hybrid Flow, deve-se usar NO\_AUTHORITY.

**NONE**: quando o CPF (loggedUser) / CNPJ (businessEntity) possui credencial autenticadora e poderes suficientes para prosseguir o fluxo monitorado - exemplo: PF, cliente, que possui credencial ativa, mas não se autenticou; cliente que se autenticou utilizando a credencial correta.  
**NO\_CREDENTIAL**: quando o CPF (loggedUser) / CNPJ (businessEntity) não for cliente ou não possuir credencial válida/ativa para prosseguir no fluxo monitorado ou quando o HTTP response code for diferente de 201.  
**NO\_AUTHORITY**: quando o CPF (loggedUser) / CNPJ (businessEntity) consegue se autenticar, mas não dispõe de poderes ou alçadas para prosseguir no fluxo de compartilhamento de dados e serviços.  
**NO\_AUTHORITY\_PERSON\_MISMATCH**: quando o CPF (loggedUser) não possui relação com a credencial utilizada na etapa de autenticação do Hybrid Flow - exemplo: consentimento criado para um CPF e autenticado por outro; criado para um CNPJ e autenticado por CPF sem relação com o CNPJ.  
**CREDENTIAL\_UNAVAILABLE:** O CPF/CNPJ é cliente e possui credencial cadastrada, mas ela está **temporariamente indisponível** para uso, ou uma falha técnica impediu a verificação do estado da credencial havendo indício de vínculo com a instituição.

string

SERVER

Todos

POST

CREDENTIAL\_UNAVAILABLE, NO\_AUTHORITY, NO\_AUTHORITY\_PERSON\_MISMATCH, NO\_CREDENTIAL, NONE

/open-banking/automatic-payments/v_x_/recurring-consents

v2

NO\_CREDENTIAL

errorCodes

Registra os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

string

CLIENT

422

POST

**ReponseError Create Consent**  
\["DATA\_PAGAMENTO\_INVALIDA"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["FUNCIONALIDADE\_NAO\_HABILITADA"\], \["NAO\_INFORMADO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\]

**422ReponseError Recurring Consent**  
\["CAMPO\_NAO\_PERMITIDO"\], \["CONSENTIMENTO\_NAO\_PERMITE\_CANCELAMENTO"\], \["DETALHE\_EDICAO\_INVALIDO"\], \["FALTAM\_SINAIS\_OBRIGATORIOS\_PLATAFORMA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSAO\_INSUFICIENTE"\]

**422ResponseError PIX Recurring Payment**  
\["CONSENTIMENTO\_INVALIDO"\], \["CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["FORA\_PRAZO\_PERMITIDO"\], \["LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO"\], \["LIMITE\_PERIODO\_VALOR\_EXCEDIDO"\], \["LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"\], \["LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"\], \["NAO\_INFORMADO"\], \["PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PAGAMENTO\_RECUSADO\_DETENTORA"\], \["PAGAMENTO\_RECUSADO\_SPI"\], \["SALDO\_INSUFICIENTE"\], \["VALOR\_ACIMA\_LIMITE"\], \["VALOR\_INVALIDO"\]

**422ReponseErrorCreate Retry Recurring Payment PaymentId**  
\["CANCELAMENTO\_FORA\_PERIODO\_PERMITIDO"\], \["PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\]

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry

v2

NAO\_INFORMADO

errorCodes

Registra os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

string

CLIENT

4xx ou 5xx exceto 422

POST

GET

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{originalRecurringPaymentId}/retry

v2

hasMinimumAmount

Valida se possui o valor mínimo definido pelo usuário recebedor​

-   Se preenchido o campo “.data/recurringConfiguration.automatic.minimumVariableAmount”, enviar "TRUE"; ou
    
-   Se não preenchido o campo “.data.recurringConfiguration.automatic.minimumVariableAmount” enviar "FALSE"
    

Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

TRUE, FALSE

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

TRUE

interval

Periodicidade que a recorrência foi definida (semanal, trimestral, anual...)​

Preencher com o valor do campo ".data.recurringConfiguration.interval"

Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

SEMANAL, MENSAL, TRIMESTRAL, SEMESTRAL, ANUAL

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

ANUAL

isFirstPayment

Valida se o serviço possui um pagamento associado na adesão

-   Se preenchido o campo ".data.recurringConfiguration.automatic.firstPayment", enviar "TRUE"; ou
    
-   Se não preenchido o campo ".data.recurringConfiguration.automatic.firstPayment", enviar "FALSE"
    

Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

TRUE, FALSE

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

TRUE

isRetryAccepted

Identifica se foi autorizado a tentativas de pagamento em dias subsequentes na situação de falha do pagamento da recorrência​

Preencher com o valor do campo ".data.recurringConfiguration.automatic.isRetryAccepted"

Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

TRUE, FALSE

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

TRUE

journeyIsLinked

Indica que o consentimento faz parte de uma jornada otimizada.

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.isLinked”, retornado após a chamada inicial na API “POST /consent” em caso de Jornada Otimizada.  
Em casos em que a informação não está disponível espera-se o envio do valor FALSE.

string

CLIENT

Todos

POST  
GET

TRUE, FALSE

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

FALSE

journeyLinkId

Identifica o consentimento de dados vinculado a uma Jornada Otimizada.

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.linkId”, retornado após a chamada inicial na API “POST /consent” em caso de Jornada Otimizada.  
Deve ser enviado se journeyIsLinked for TRUE.

string

CLIENT

Todos

POST  
GET

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD331237

localInstrument

Especifica a forma de iniciação do pagamento​

Deve ser preenchido com a mesma string informada no payload ".data.localInstrument"  
Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar uma recorrência (valor do campo "/data/paymentReference" diferente de "zero"), apenas o método AUTO é permitido, ou; Caso consentimento associado a tentativa de pagamento seja para Pix automático (objeto “automatic” selecionado no oneOf do campo "/data/recurringConfiguration") e a referência do pagamento indicar o pagamento inicial avulso (valor do campo "/data/paymentReference" igual a "zero"), apenas o método MANU é permitido. Para consentimentos de Transferências Inteligentes (objeto “sweeping” selecionado no “oneOf” do campo “/data/recurringConfiguration/”), apenas os métodos MANU, DICT e INIC são permitidos

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

DICT, INIC, MANU, QRDN, QRES, AUTO, APDN, APES

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

DICT

originalRecurringPaymentId

Identifica o primeiro pagamento da recorrência em relação as retentativas​

Preencher com o valor do campo ".data.originalRecurringPaymentId"  
Para os endpoints /open-banking/automatic-payments/v_x_/pix/recurring-payments e /open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}, métodos GET e PATCH, a informação só deve ser enviada se retornado no response da API.  
Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST/PATCH)  
Todos menos 4xx e 5xx (GET)

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

v2

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

TXpRMU9UQTROMWhZV2xSU1FUazJSMDl

paymentList

Lista de dados de pagamentos com pagamentos inteligentes e automáticos  
Os itens indentados abaixo pertencem ao objeto paymentList e seguem as mesmas regras de obrigatoriedade

object

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

\[{"paymentId":"4d4dec4b-5960-4041-8099-1340b8c8a4bb","consentId":"urn:bancoex:C1DD33123","statusUpdateDateTime":"2026-02-08T19:53:53Z","status":"ACSC"}\]

paymentId

Código ou identificador único informado pela instituição detentora da conta para representar a iniciação de pagamento​

string

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

4d4dec4b-5960-4041-8099-1340b8c8a4bb

recurringConsentId

Identificador único do consentimento criado para a iniciação de pagamento solicitada​

string

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

urn:bancoex:C1DD33123

statusUpdateDateTime

Data e hora da última atualização da iniciação de pagamento

string

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

'2026-02-08T19:53:53Z

status

Estado atual do pagamento

string

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

ACSC

rejectionReasonCode

Código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

string

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

NAO\_INFORMADO

rejectionReasonDetail

Detalhe sobre o código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

string

CLIENT

200

GET

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

Detalhes sobre a rejeição

paymentReference

Identifica a referência do pagamento no tempo (semanal, mensal, trimestral...)​

Preencher com o valor do campo "paymentReference"  
Campo de preenchimento obrigatório caso seja um pagamento de Pix automático e deve ser enviado para critérios de coleta de métricas do ecossistema. Caso essa regra não seja respeitada, a instituição detentora da conta deve retornar um erro HTTP 422 com o código DETALHE\_PAGAMENTO\_INVALIDO.  
Deve ser preenchido quando paymentType for AUTOMATIC

string

CLIENT

Todos (POST/PATCH)  
Todos menos 4xx e 5xx (GET)

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

_R/2025-09-23/P1M_

paymentType

Identifica o modo de pagamento acionado no consentimento

Identifica o modo de pagamento acionado no consentimento e deve ser preenchido de acordo com o campo ".data.recurringConfiguration/oneOf"

**IMMEDIATE**: Pix sem configuração de agendamento  
**SCHEDULED**: Pix com configuração de agendamento  
**RECURRENT**: Pix com agendamento e recorrência  
**SWEEPING**: Chamadas de pagamentos inteligentes  
**AUTOMATIC**: Pagamentos automáticos  
**WITHDRAW:** PIX Saque  
**CHANGE:** PIX Troco

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

AUTOMATIC, IMMEDIATE, RECURRENT, SCHEDULED, SWEEPING, WITHDRAW, CHANGE

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

AUTOMATIC

personType

Identifica a natureza do solicitante em uma transação ou consentimento.

Se .data.businessEntity estiver preenchido no payload, se estiver então preencher com "PJ", se não estiver então preencher com "PF"

string

CLIENT

2xx

POST  
GET  
PATCH

PF, PJ, PESSOA\_NATURAL, PESSOA\_JURIDICA

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

PJ

recurringConsentId

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada

Preencher com o valor do campo ".data.recurringConsentId"​

string

CLIENT

Todos menos 4xx e 5xx

POST

/open-banking/automatic-payments/v_x_/recurring-consents

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD331237

recurringConsentId

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada

Preencher com o valor do campo ".data.recurringConsentId"​

string

CLIENT

Todos

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD331237

recurringPaymentDate

Data em que o pagamento será realizado no formato timezone UTC-3 (UTC time format)

Deve ser preenchido com a mesma string obtida no ".data.date".

string

CLIENT

201

POST

/open-banking/automatic-payments/v_x_/pix/recurring-payments

v2

2023-10-10

recurringPaymentId

Código ou identificador único informado pela instituição detentora da conta para representar a iniciação de pagamento.

Preencher com o valor do campo ".data.recurringPaymentId"​

string

CLIENT

Todos menos 4xx e 5xx

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

v2

^\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,99}$

TXpRMU9UQTROMWhZV2xSU1FUazJSMDl

referenceStartDate

Data prevista para o início do ciclo de cobrança dos pagamentos associados à recorrência. Trata-se de uma string com data conforme especificação RFC-3339, seguindo o horário de Brasília (UTC-3). O pagamento inicial avulso, declarado no objeto firstPayment do consentimento, não está sujeito a essa data

Preencher com o valor do campo ".data.recurringConfiguration.automatic.referenceStartDate". Deve ser preenchido quando paymentType for AUTOMATIC.

string

CLIENT

2xx

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

2025-09-01

rejectedBy

Quem iniciou a solicitação de rejeição

Deve ser preenchido com a mesma string obtida no ".data.rejection.rejectedBy".  
Obrigatório somente quando o status for RJCT ou REJECTED

string

CLIENT

Todos menos 4xx e 5xx

GET  
PATCH

DETENTORA, INICIADORA, USUARIO

/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

INICIADORA

rejectedFrom

Canal onde iniciou-se o processo de rejeição

Deve ser preenchido com a mesma string obtida no ".data.rejection.rejectedFrom".  
Obrigatório somente quando o status for RJCT ou REJECTED

string

CLIENT

Todos menos 4xx e 5xx

GET  
PATCH

DETENTORA, INICIADORA

/open-banking/automatic-payments/vx/recurring-consents/{recurringConsentId}

v2

INICIADORA

rejectionReasonCode

Código da razão pela qual um consentimento ou pagamento foi rejeitado

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.code". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista  
Obrigatório somente quando o status for RJCT ou REJECTED

string

CLIENT

Todos menos 4xx e 5xx

POST  
GET  
PATCH

**Pagamentos**  
\["CONSENTIMENTO\_INVALIDO"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["DETALHE\_TENTATIVA\_INVALIDO"\], \["FALHA\_INFRAESTRUTURA\_DETENTORA"\], \["FALHA\_INFRAESTRUTURA\_ICP"\], \["FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR"\], \["FALHA\_INFRAESTRUTURA\_SPI"\], \["FORA\_PRAZO\_PERMITIDO"\], \["LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO"\], \["LIMITE\_PERIODO\_VALOR\_EXCEDIDO"\], \["LIMITE\_TENTATIVAS\_EXCEDIDO"\], \["LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"\], \["NAO\_INFORMADO"\], \["LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"\], \["PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"\], \["PAGAMENTO\_RECUSADO\_DETENTORA"\], \["PAGAMENTO\_RECUSADO\_SPI"\], \["SALDO\_INSUFICIENTE"\], \["TITULARIDADE\_INCONSISTENTE"\], \["VALOR\_ACIMA\_LIMITE"\], \["VALOR\_INVALIDO"\]  
**ConsentRejectionReason**  
\["AUTENTICACAO\_DIVERGENTE"\], \["CONTA\_NAO\_PERMITE\_PAGAMENTO"\], \["CONTAS\_ORIGEM\_DESTINO\_IGUAIS"\], \["FALHA\_INFRAESTRUTURA"\], \["FLUXO\_NAO\_SUPORTADO\_PRODUTO"\], \["NAO\_INFORMADO"\], \["REJEITADO\_USUARIO"\], \["TEMPO\_EXPIRADO\_AUTORIZACAO"\], \["VALOR\_ACIMA\_LIMITE"\]

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

NAO\_INFORMADO

rejectionReasonDetail

Detalhe mais específico sobre a rejeição de um consentimento ou pagamento

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista  
Obrigatório somente quando o status for RJCT ou REJECTED

string

CLIENT

Todos menos 4xx e 5xx

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}

v2

O usuário rejeitou a autorização do consentimento

revocationReasonCode

Código indicador do motivo da revogação

Deve ser preenchido com a string obtida no campo ".data.revocation.reason.code". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista  
Obrigatório somente quando o status for REVOKED

string

CLIENT

Todos (POST/GET)  
Todos menos 4xx e 5xx (PATCH)

POST  
GET  
PATCH

NAO\_INFORMADO, REVOGADO\_RECEBEDOR, REVOGADO\_USUARIO

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

REVOGADO\_RECEBEDOR

revocationReasonDetail

Detalhe sobre a revogação referente ao consentimento​

Deve ser preenchido com a string obtida no campo ".data.revocation.reason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista  
Obrigatório somente quando o status for REVOKED

string

CLIENT

Todos (POST/GET)  
Todos menos 4xx e 5xx (PATCH)

POST  
GET  
PATCH

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}

v2

O usuário rejeitou a autorização do consentimento

status

Identifica o status atual do recurso (como um consentimento ou um pagamento) que está sendo reportado.

Deve ser preenchido com a mesma string obtida no ".data.status". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista

string

CLIENT

2xx

POST  
GET  
PATCH

**Para consentimentos:** AWAITING\_AUTHORISATION, PARTIALLY\_ACCEPTED, AUTHORISED, REJECTED, REVOKED, CONSUMED.  
**Para pagamentos:** RCVD, CANC, ACCP, ACPD, RJCT, ACSC, PDNG, SCHD.

/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

v2

PDNG

tokenId

Identificador único e criptograficamente seguro do token utilizado no consumo da API.  
A implementação do tokenId preencherá a lacuna de rastreabilidade, permitindo vincular a emissão de cada token (incluindo os de CLIENT\_CREDENTIALS) às suas respectivas jornadas, mesmo quando múltiplos consentimentos forem iniciados por um único token. Isso resultará em uma visão mais completa da jornada do token, aprimorando a capacidade de rastreabilidade e análise operacional para as instituições e do ecossistema

O tokenId será gerado pelo cliente (role CLIENT) no momento do reporte para a PCM, aplicado um hash SHA256 sobre o token recebido e um Pepper (segredo) gerenciado internamente pela instituição. Este tokenId deve ser reportado na PCM, complementando as informações já existentes de grant\_type e consentId (onde aplicável). Para garantir a robustez criptográfica do hash, o Pepper utilizado deverá ser um valor aleatório e criptograficamente forte, gerenciado internamente pela instituição. Recomenda-se um tamanho de 128 a 256 bits para o Pepper, aplicado no cálculo do tokenId, como por exemplo, SHA256 (token + Pepper). O tokenId será composto pelos 72 bits iniciais do hash Base64URL-safe encoded. 

 **Importante:** O tokenId será gerado apenas quando o token for recebido com sucesso na resposta do POST /token. Em casos nos quais a requisição ao POST /token resultar em erros 4xx ou 5xx, o token não será obtido e, consequentemente, o tokenId não poderá ser gerado. Nessas situações, o campo tokenId deve ser omitido do reporte à PCM.

string

CLIENT

Todos exceto 4xx e 5xx

Todos

/open-banking/automatic-payments/v_x_/recurring-consents  
/open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}  
/open-banking/automatic-payments/v_x_/pix/recurring-payments  
/open-banking/automatic-payments/v_x_/pix/recurring-payments/{recurringPaymentId}  
/open-banking/automatic-payments/vx/pix​/recurring-payments​/{originalRecurringPaymentId}​/retry

v2

**Dados de entrada**

-   Token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...' (JWT completo)
    
-   Pepper: '\[valor secreto da instituição\]'
    

  
**Processo**  
Concatenar: token + pepper  
Hash SHA256: da string concatenada  
Truncar: primeiros 72 bits (9 bytes)  
Codificar: Base64URL-safe  
**Resultado**  
{  
"additionalInfo": {  
"tokenId": "c9ng8aKzxNXm"  
}  
}
