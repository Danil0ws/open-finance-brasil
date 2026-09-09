# Iniciação de Pagamentos - Regras de Obrigatoriedade (additionalInfo)

v 1.10

**Guia de leitura**

1.  Se o campo não está listado, é porque não existe a obrigatoriedade de enviá-lo.
    
2.  Nos endpoints, a referência “v_x_” indica que se aplicam às versões listadas na coluna “Versões”. Por exemplo, Endpoint “open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}” e Versões “v1 v2” significa que o endpoint é válido para as versões 1 e 2.
    

Dica: para rolar a tabela horizontalmente, segure SHIFT e utilize o botão de rolagem do mouse.

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Iniciação de Pagamentos

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

**Tamanho máximo**

**Padrão**

**Exemplo**

authorisationFlow

Identifica o fluxo de autorização em que um pagamento ou operação foi solicitado

O campo deve ser preenchido com a string obtida em ".data.authorisationFlow". Se a informação for uma lista, utilize apenas o primeiro item. Caso a string de ".data.authorisationFlow" seja nula, preencha obrigatoriamente com HYBRID\_FLOW. É fundamental que sempre seja reportado um dos valores do enum (como HYBRID\_FLOW, CIBA ou FIDO), e nunca um valor nulo, pois para fins de telemetria é necessário identificar explicitamente qual fluxo de autorização foi utilizado, independentemente da permissão de valor nulo nas especificações das APIs do Open Finance.

string

CLIENT

Todos

POST  
GET  
PATCH

CIBA\_FLOW, FIDO\_FLOW, HYBRID\_FLOW

/open-banking/payments/vx/pix/payments  
/open-banking/payments/v_x_/pix/payments/{paymentId}​

v5

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

/open-banking/payments/v_x_/consents

v5

HYBRID\_FLOW

cancellationReason

Dados referentes ao usuário pagador que solicitou o cancelamento, o canal utilizado por ele e o motivo.

Preencher com o valor do campo ".cancellation.reason"  
Deve ser enviado quando o campo status é "CANC".

string

CLIENT

200

GET  
PATCH

CANCELADO\_PENDENCIA, CANCELADO\_AGENDAMENTO, CANCELADO\_MULTIPLAS\_ALCADA

/open-banking/payments/v_x_/pix/payments/{paymentId}

v5

CANCELADO\_PENDENCIA

cancelledFrom

Meio pelo qual foi realizado o cancelamento.

Preencher com o valor do campo ".cancellation.cancelledFrom"  
Deve ser enviado quando o campo status é "CANC".

string

CLIENT

200

GET  
PATCH

INICIADORA, DETENTORA

/open-banking/payments/v_x_/pix/payments/{paymentId}

v5

INICIADORA

companyProfileInfo

Objeto JSON que representa o perfil da Pessoa Jurídica (PJ) do cliente, contendo informações como a natureza jurídica e o porte da empresa, conforme a classificação oficial da Receita Federal do Brasil.  
Os itens indentados abaixo pertencem ao objeto companyProfileInfo e seguem as mesmas regras de obrigatoriedade.

**Obrigatório para clientes PJ.** O objeto deve conter um objeto de perfil da empresa. As informações de natureza jurídica e porte devem ser obtidas prioritariamente da **API oficial Consulta CNPJ (RFB/SERPRO) ou dos Dados Abertos do CNPJ (RFB)**, conforme o Dicionário de Dados do CNPJ da Receita Federal. Este objeto deve ser enviado como parte do additionalInfo ao consumir as APIs de criação de consentimento para dados e serviços.

-   [Consulta CNPJ — Catálogo de APIs governamentais](https://www.gov.br/conecta/catalogo/apis/consulta-cnpj) (API/Swagger)
    
-   [Portal de Dados Abertos](https://dados.gov.br/dados/conjuntos-dados/cadastro-nacional-da-pessoa-juridica---cnpj) (arquivo de dados)
    

object

CLIENT

Todos

POST

/open-banking/payments/v_x_/consents

v5

Objeto JSON

{ "naturezaJuridica": "2135", "porteEmpresa": "01" }

naturezaJuridica

Código que identifica a constituição jurídico-institucional da entidade, conforme a Tabela de Natureza Jurídica do IBGE, categorizando-a em: Administração pública; Entidades empresariais; Entidades sem fins lucrativos; Pessoas físicas e organizações internacionais; e Outras instituições extraterritoriais.

**Obrigatório para clientes PJ.** O cliente (receptor/iniciador) deve obter essa informação a partir de fontes oficiais (ex., Governo Federal/Dados Abertos/Base CNPJs ou API do SERPRO), com base no CNPJ do usuário, e reportá-la como parte do additionalInfo quando houver consumo as APIs de criação de consentimento para compartilhamento de dados e serviços.

string

CLIENT

Todos

POST

/open-banking/payments/v_x_/consents

v5

4

^\\d{4}$

2135

porteEmpresa

Código numérico que identifica o porte da empresa do cliente Pessoa Jurídica (PJ), conforme a classificação oficial da Receita Federal do Brasil.

**Obrigatório para clientes PJ.** O receptor/iniciador, que detém o CNPJ do usuário, é responsável por obter o código do porte da empresa. Esta informação deve ser consultada e validada a partir de fontes oficiais, como a base de Dados Abertos do CNPJ ou a API do SERPRO, ambas mantidas pelo Governo Federal, e conforme o Dicionário de Dados do CNPJ da Receita Federal. O valor deve ser enviado como parte do additionalInfo quando houver consumo as APIs de criação de consentimento para compartilhamento de dados e serviços.

string

CLIENT

Todos

POST

/open-banking/payments/v_x_/consents

v5

2

^\\d{2}$

01

consentId

O consentId é o identificador único do consentimento e deverá ser um URN - Uniform Resource Name.

Deve ser preenchido com a mesma string obtida no campo .data.consentId retornado após a chamada inicial na API "POST /consents”

string

CLIENT

Todos menos 4xx e 5xx para o método POST

POST  
GET  
PATCH

/open-banking/payments/v_x_/consents  
/open-banking/payments/v_x_/consents/{consentId}

v5

256

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD33123

consentId

O consentId é o identificador único do consentimento e deverá ser um URN - Uniform Resource Name.

Deve ser preenchido com a mesma string obtida no campo .data.consentId retornado após a chamada inicial na API "POST /consents”

string

CLIENT

Todos

POST  
GET  
PATCH

/open-banking/payments/v_x_/pix/payments  
/open-banking/payments/v_x_/pix/payments/{paymentId}​  
/open-banking/payments/v_x_/consents/{consentId}/pix/payments/

v5

256

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD33123

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

/open-banking/payments/v_x_/consents

v5

NO\_CREDENTIAL

errorCodes

Registrar os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

string

CLIENT

422

POST  
GET  
PATCH

**422ReponseError Create Consent**  
\["DATA\_PAGAMENTO\_INVALIDA"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["FORMA\_PAGAMENTO\_INVALIDA"\], \["NAO\_INFORMADO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PROPOSITO\_INVALIDO"\]

**CreateError PIX Payments**  
\["COBRANCA\_INVALIDA"\], \["CONSENTIMENTO\_INVALIDO"\], \["CONSENTIMENTO\_PENDENTE\_AUTORIZACAO"\], \["CONTA\_NAO\_PERMITE\_PAGAMENTO"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["NAO\_INFORMADO"\], \["PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"\], \["PAGAMENTO\_NAO\_PERMITE\_CANCELAMENTO"\], \["PAGAMENTO\_RECUSADO\_DETENTORA"\], \["PAGAMENTO\_RECUSADO\_SPI"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["QRCODE\_INVALIDO"\], \["SALDO\_INSUFICIENTE"\], \["VALOR\_ACIMA\_LIMITE"\], \["VALOR\_INVALIDO"\]

/open-banking/payments/v_x_/consents  
/open-banking/payments/v_x_/consents/{consentId}  
/open-banking/payments/v_x_/pix/payments  
/open-banking/payments/v_x_/pix/payments/{paymentId}​  
/open-banking/payments/v_x_/consents/{consentId}/pix/payments

v5

NAO\_INFORMADO

errorCodes

Registrar os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

string

CLIENT

4xx ou 5xx exceto 422

POST  
GET  
PATCH

/open-banking/payments/v_x_/consents  
/open-banking/payments/v_x_/consents/{consentId}  
/open-banking/payments/v_x_/pix/payments  
/open-banking/payments/v_x_/pix/payments/{paymentId}​  
/open-banking/payments/v_x_/consents/{consentId}/pix/payments

v5

localInstrument

Especifica a forma de iniciação do pagamento​

Deve ser preenchido com a mesma string informada no payload ".data.localInstrument"  
Se /data/payment/schedule enviado com valor diferente de single durante a criação do consentimento, apenas os métodos MANU, DICT ou QRES são permitidos.

string

CLIENT

Todos (POST)  
Todos menos 4xx e 5xx (GET/PATCH)

POST  
GET  
PATCH

DICT, INIC, MANU, QRDN, QRES, AUTO, APDN, APES

/open-banking/payments/v_x_/consents  
/open-banking/payments/v_x_/pix/payments/{paymentId}

v5

MANU

paymentDate

Data em que o pagamento será realizado

Deve ser enviado obrigatoriamente para os tipos de pagamento (paymentType) SWEEPING e AUTOMATIC  
Deve ser preenchido com o conteúdo de _data.payment.date_  
Mutualmente excludente com o campo _paymentSchedule_

string

CLIENT

201

POST

/open-banking/payments/v_x_/consents

v5

2021-01-01

paymentList

Lista de dados de pagamentos com pagamentos imediatos e agendamentos únicos ou recorrentes.  
Os itens indentados abaixo pertencem ao objeto paymentList e seguem as mesmas regras de obrigatoriedade

Deve ser enviado obrigatoriamente para os tipos de pagamento (paymentType) IMMEDIATE, SCHEDULED e RECURRENT, mesmo que a lista contenha apenas um item. Para o mesmo consentId não podem ser reportados nesta lista mais do que 60 paymentId.

object

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

\[{"paymentId":"4d4dec4b-5960-4041-8099-1340b8c8a4bb","consentId":"urn:bancoex:C1DD33123","statusUpdateDateTime":"2026-02-08T19:53:53Z","status":"ACSC"}\]'2021-01-01

paymentId

Código ou identificador único informado pela instituição detentora da conta para representar a iniciação de pagamento​

string

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

4d4dec4b-5960-4041-8099-1340b8c8a4bb

consentId

Identificador único do consentimento criado para a iniciação de pagamento solicitada​

string

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

urn:bancoex:C1DD33123

statusUpdateDateTime

Data e hora da última atualização da iniciação de pagamento

string

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

2026-02-08T19:53:53Z

status

Estado atual do pagamento

string

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

ACSC

rejectionReasonCode

Código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

string

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

NAO\_INFORMADO

rejectionReasonDetail

Detalhe sobre o código identificador do motivo de rejeição. Deve ser enviado vazio se não houver conteúdos, seguindo a mesma regra da API de negócio relacionada

string

CLIENT

201

POST

/open-banking/payments/v_x_/pix/payments

v5

Detalhes sobre a rejeição

paymentSchedule

Estrutura responsável pela parametrização dos pagamentos que acontecerão sob aquele consentimento

Deve ser enviado obrigatoriamente para os tipos de pagamento (paymentType) SCHEDULED e RECURRENT  
Deve ser preenchido com o conteúdo de _data.payment.schedule_  
Mutualmente excludente com o campo _paymentDate_

string

CLIENT

201

POST

/open-banking/payments/v_x_/consents

v5

{"monthly":{"dayOfMonth":3,"startDate":"2026-02-03","quantity":12},"additionalInformation":"nonononono"}

paymentType

Identifica o modo de pagamento acionado no consentimento

-   Se /data/payment/purpose = IMMEDIATE, paymentType = IMMEDIATE
    
-   Se /data/payment/purpose = SINGLE\_SCHEDULED, paymentType = SCHEDULED
    
-   Se /data/payment/purpose = RECURRENT\_SCHEDULED, paymentType = RECURRENT
    
-   Se /data/payment/purpose = WITHDRAW, paymentType = WITHDRAW
    
-   Se /data/payment/purpose = CHANGE, paymentType = CHANGE
    

string

CLIENT

Todos

POST  
PATCH

AUTOMATIC, CHANGE, IMMEDIATE, RECURRENT, SCHEDULED, SWEEPING, WITHDRAW

/open-banking/payments/v_x_/consents  
/open-banking/payments/v_x_/pix/payments  
/open-banking/payments/v_x_/pix/payments/{paymentId}​

v5

SCHEDULED

personType

Identifica a natureza do solicitante em uma transação ou consentimento.

Se .data.businessEntity estiver preenchido no payload, se estiver então preencher com "PJ", se não estiver então preencher com "PF"

string

CLIENT

Todos

POST

PF, PJ, PESSOA\_NATURAL, PESSOA\_JURIDICA

/open-banking/payments/v_x_/consents

v5

PJ

rejectionReasonCode

Código da razão pela qual um consentimento ou pagamento foi rejeitado

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.code" ou ".data.rejection.reason.code" ou ".data.cancellation.rejectionReason"​  
Obrigatório somente quando o status for RJCT ou REJECTED

string

CLIENT

Todos menos 4xx e 5xx

GET

**RejectionReasonType**  
\["AUTENTICACAO\_DIVERGENTE"\], \["CHAVE\_PIX\_DIVERGENTE\_AGENDAMENTO\_LIQUIDACAO"\], \["COBRANCA\_INVALIDA"\], \["CONSENTIMENTO\_INVALIDO"\], \["CONSENTIMENTO\_REVOGADO"\], \["CONTA\_NAO\_PERMITE\_PAGAMENTO"\], \["CONTAS\_ORIGEM\_DESTINO\_IGUAIS"\], \["DETALHE\_PAGAMENTO\_INVALIDO"\], \["DETALHE\_TENTATIVA\_INVALIDO"\], \["FALHA\_AGENDAMENTO\_PAGAMENTOS"\], \["FALHA\_INFRAESTRUTURA\_DETENTORA"\], \["FALHA\_INFRAESTRUTURA\_DICT"\], \["FALHA\_INFRAESTRUTURA\_ICP"\], \["FALHA\_INFRAESTRUTURA\_PSP\_RECEBEDOR"\], \["FALHA\_INFRAESTRUTURA\_SPI"\], \["FORA\_PRAZO\_PERMITIDO"\], \["LIMITE\_PERIODO\_QUANTIDADE\_EXCEDIDO"\], \["LIMITE\_PERIODO\_VALOR\_EXCEDIDO"\], \["LIMITE\_TENTATIVAS\_EXCEDIDO"\], \["LIMITE\_VALOR\_TOTAL\_CONSENTIMENTO\_EXCEDIDO"\], \["LIMITE\_VALOR\_TRANSACAO\_CONSENTIMENTO\_EXCEDIDO"\], \["NAO\_INFORMADO"\], \["PAGAMENTO\_DIVERGENTE\_CONSENTIMENTO"\], \["PAGAMENTO\_RECUSADO\_DETENTORA"\], \["PAGAMENTO\_RECUSADO\_SPI"\], \["PERMISSAO\_INSUFICIENTE"\], \["QRCODE\_INVALIDO"\], \["SALDO\_INSUFICIENTE"\], \["TITULARIDADE\_INCONSISTENTE"\], \["VALOR\_ACIMA\_LIMITE"\], \["VALOR\_INVALIDO"\]

**ConsentRejectionReason**  
\["AUTENTICACAO\_DIVERGENTE"\], \["CONTA\_NAO\_PERMITE\_PAGAMENTO"\], \["CONTAS\_ORIGEM\_DESTINO\_IGUAIS"\], \["FALHA\_INFRAESTRUTURA"\], \["NAO\_INFORMADO"\], \["QRCODE\_INVALIDO"\], \["REJEITADO\_USUARIO"\], \["SALDO\_INSUFICIENTE"\], \["TEMPO\_EXPIRADO\_AUTORIZACAO"\], \["TEMPO\_EXPIRADO\_CONSUMO"\], \["VALOR\_ACIMA\_LIMITE"\], \["VALOR\_INVALIDO"\]

/open-banking/payments/v_x_/consents/{consentId}  
/open-banking/payments/v_x_/pix/payments/{paymentId}​

v5

NAO\_INFORMADOAUTHORISED

rejectionReasonDetail

Detalhe mais específico sobre a rejeição de um consentimento ou pagamento

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.detail". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista.  
Caso consentimento rejeitado de versões nas quais não havia o campo rejectionReason retornar o seguinte detail: Motivo de rejeição inexistente em versões anteriores.  
Obrigatório somente quando o status for RJCT ou REJECTED

string

CLIENT

Todos menos 4xx e 5xx

GET

/open-banking/payments/v_x_/consents/{consentId}  
/open-banking/payments/v_x_/pix/payments/{paymentId}​

v5

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

**Para consentimentos:**

AUTHORISED, AWAITING\_AUTHORISATION, CONSUMED, PARTIALLY\_ACCEPTED, REJECTED, REVOKED

**Para pagamentos:**

ACCP, ACPD, ACSC, CANC, PDNG, RCVD, RJCT, SCHD

/open-banking/payments/vx/consents  
/open-banking/payments/vx/consents/{consentId}  
/open-banking/payments/vx/pix/payments  
/open-banking/payments/vx/pix/payments/{paymentId}​  
/open-banking/payments/v_x_/consents/{consentId}/pix/payments

v5

AUTHORISED

tokenId

Identificador único e criptograficamente seguro do token utilizado no consumo da API.  
A implementação do tokenId preencherá a lacuna de rastreabilidade, permitindo vincular a emissão de cada token (incluindo os de CLIENT\_CREDENTIALS) às suas respectivas jornadas, mesmo quando múltiplos consentimentos forem iniciados por um único token. Isso resultará em uma visão mais completa da jornada do token, aprimorando a capacidade de rastreabilidade e análise operacional para as instituições e do ecossistema

O tokenId será gerado pelo cliente (role CLIENT) no momento do reporte para a PCM, aplicado um hash SHA256 sobre o token recebido e um Pepper (segredo) gerenciado internamente pela instituição. Este tokenId deve ser reportado na PCM, complementando as informações já existentes de grant\_type e consentId (onde aplicável). Para garantir a robustez criptográfica do hash, o Pepper utilizado deverá ser um valor aleatório e criptograficamente forte, gerenciado internamente pela instituição. Recomenda-se um tamanho de 128 a 256 bits para o Pepper, aplicado no cálculo do tokenId, como por exemplo, SHA256 (token + Pepper). O tokenId será composto pelos 72 bits iniciais do hash Base64URL-safe encoded. 

 **Importante:** O tokenId será gerado apenas quando o token for recebido com sucesso na resposta do POST /token. Em casos nos quais a requisição ao POST /token resultar em erros 4xx ou 5xx, o token não será obtido e, consequentemente, o tokenId não poderá ser gerado. Nessas situações, o campo tokenId deve ser omitido do reporte à PCM.

string

CLIENT

Todos exceto 4xx e 5xx

Todos

/open-banking/payments/vx/consents  
/open-banking/payments/vx/consents/{consentId}  
/open-banking/payments/vx/pix/payments  
/open-banking/payments/vx/pix/payments/{paymentId}​  
/open-banking/payments/v_x_/consents/{consentId}/pix/payments

v5

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

webhookInteractionId

Indica o identificador x-webhook-interaction-id quando uma requisição GET é realizada após o estímulo de um webhook.

Caso o GET esteja sendo feito após o estímulo do webhook, o x-webhook-interaction-id deverá ser indicado

string

CLIENT

Todos menos 4xx e 5xx

GET

/open-banking/payments/v_x_/consents/{consentId}​

v5

530bfa60-e40f-4776-96c2-82b418aaa0af
