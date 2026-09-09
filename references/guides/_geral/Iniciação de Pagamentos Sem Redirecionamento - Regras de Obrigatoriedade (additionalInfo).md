# Iniciação de Pagamentos Sem Redirecionamento - Regras de Obrigatoriedade (additionalInfo)

v 1.10

**Guia de leitura**

1.  Se o campo não está listado, é porque não existe a obrigatoriedade de enviá-lo.
    
2.  Nos endpoints, a referência “v_x_” indica que se aplicam às versões listadas na coluna “Versões”. Por exemplo, Endpoint “open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}” e Versões “v1 v2” significa que o endpoint é válido para as versões 1 e 2.
    

Dica: para rolar a tabela horizontalmente, segure SHIFT e utilize o botão de rolagem do mouse.

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# **Pagamentos**

### Iniciação de Pagamentos Sem Redirecionamento

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

authenticatorAttachment​

Descreve como o autenticador (por exemplo, um dispositivo FIDO) está anexado ao cliente que realiza a autenticação (ex: platform para autenticadores integrados como Face ID ou cross-platform para chaves de segurança USB).

Deve ser preenchido com a mesma string definida em ".data.authenticatorAttachment". Não havendo string, deve ser explicitamente enviada esse additionalInfo como sendo uma string vazia.​  
Caso seja enviado um valor neste campo, o mesmo será validado contra o domínio dele.

string

CLIENT

Todos

POST

platform, cross-platform

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration​

v2

cross-platform

cancelledFrom

Informa o meio pelo qual foi realizado o cancelamento

Preencher com o valor do campo ".cancellation.cancelledFrom"  
Status do pagamento deve ser "REVOKED"

string

CLIENT

2xx

GET

INICIADORA, DETENTORA

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}​

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

/open-banking/enrollments/v_x_/enrollments

v2

{ "naturezaJuridica": "2135", "porteEmpresa": "01" }

naturezaJuridica

Código que identifica a constituição jurídico-institucional da entidade, conforme a Tabela de Natureza Jurídica do IBGE, categorizando-a em: Administração pública; Entidades empresariais; Entidades sem fins lucrativos; Pessoas físicas e organizações internacionais; e Outras instituições extraterritoriais.

**Obrigatório para clientes PJ.** O cliente (receptor/iniciador) deve obter essa informação a partir de fontes oficiais (ex., Governo Federal/Dados Abertos/Base CNPJs ou API do SERPRO), com base no CNPJ do usuário, e reportá-la como parte do additionalInfo quando houver consumo as APIs de criação de consentimento para compartilhamento de dados e serviços.

string

CLIENT

Todos

POST

/open-banking/enrollments/v_x_/enrollments

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

/open-banking/enrollments/v_x_/enrollments

v2

^\\d{2}$

01

consentId​

O consentId é o identificador único do consentimento e deverá ser um URN - Uniform Resource Name.

Deve ser preenchido com a mesma string obtida no campo .data.consentId retornado após a chamada inicial na API "POST /consents”

string

CLIENT

Todos menos 4xx e 5xx para o método POST

POST

/open-banking/enrollments/v_x_/consents/{consentId}/authorise  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options

v2

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

/open-banking/enrollments/v_x_/enrollments

v2

NO\_CREDENTIAL

enrollmentId

Identificador usado para registrar uma jornada ou um vínculo inicial

Deve ser preenchido com a mesma string obtida no campo .data.enrollmentId retornado após a chamada inicial na API "POST /enrollments".

string

CLIENT

2XX

POST

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD33123

enrollmentId

Identificador usado para registrar uma jornada ou um vínculo inicial

Deve ser preenchido com a mesma string obtida no campo .data.enrollmentId retornado após a chamada inicial na API "POST /enrollments".

string

CLIENT

Todos

POST

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals  
/open-banking/enrollments/v_x_/consents/{consentId}/authorise

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD33123

errorCodes

Registrar os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

string

CLIENT

422

POST  
GET  
PATCH

**422ReponseError Create Enrollment**  
\["CONTA\_INVALIDA"\], \["ERRO\_IDEMPOTENCIA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSOES\_INVALIDAS"\]  
**422ReponseError Cancel Enrollment**  
\["ERRO\_IDEMPOTENCIA"\], \["MOTIVO\_REJEICAO"\], \["MOTIVO\_REVOGACAO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["REJEITADO\_OUTRO\_SEM\_DETALHES"\], \["REVOGADO\_OUTRO\_SEM\_DETALHES"\], \["STATUS\_INVALIDO"\]  
**422ResponseError Fido Registration**  
\["CHALLENGE\_INVALIDO"\], \["ERRO\_IDEMPOTENCIA"\], \["EXTENSION\_INVALIDA"\], \["ORIGEM\_FIDO\_INVALIDA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PUBLIC\_KEY\_INVALIDA"\], \["RP\_INVALIDA"\], \["STATUS\_VINCULO\_INVALIDO"\]  
**422ResponseError Fido Registration-Options**  
\["ERRO\_IDEMPOTENCIA"\], \["MAXIMO\_CHALLENGES\_ATINGIDO"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["RP\_INVALIDA"\], \["STATUS\_VINCULO\_INVALIDO"\]  
**422ResponseError Risk Signals**  
\["ERRO\_IDEMPOTENCIA"\], \["FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["STATUS\_VINCULO\_INVALIDO"\]  
**422ResponseError Fido Sign Options**  
\["ERRO\_IDEMPOTENCIA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["PERMISSAO\_INVALIDA\_VINCULO\_CONSENTIMENTO"\], \["RP\_INVALIDA"\], \["STATUS\_CONSENTIMENTO\_INVALIDO"\], \["STATUS\_VINCULO\_INVALIDO"\]  
**422ResponseError Consents Authorization**  
\["CONTA\_DEBITO\_DIVERGENTE\_CONSENTIMENTO\_VINCULO"\], \["ERRO\_IDEMPOTENCIA"\], \["FALTAM\_SINAIS\_OBRIGATORIOS\_DA\_PLATAFORMA"\], \["ORIGEM\_FIDO\_INVALIDA"\], \["PARAMETRO\_INVALIDO"\], \["PARAMETRO\_NAO\_INFORMADO"\], \["RISCO"\], \["STATUS\_CONSENTIMENTO\_INVALIDO"\], \["STATUS\_VINCULO\_INVALIDO"\]  
**422ResponseError Create Consent**  
\["COMBINACAO\_PERMISSOES\_INCORRETA"\], \["DATA\_EXPIRACAO\_INVALIDA"\], \["DEPENDE\_MULTIPLA\_ALCADA"\], \["ERRO\_NAO\_MAPEADO"\], \["ESTADO\_CONSENTIMENTO\_INVALIDO"\], \["INFORMACOES\_PJ\_NAO\_INFORMADAS"\], \["PERMISSAO\_PF\_PJ\_EM\_CONJUNTO"\], \["PERMISSOES\_PJ\_INCORRETAS"\], \["SEM\_PERMISSOES\_FUNCIONAIS\_RESTANTES"\]

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals  
/open-banking/enrollments/v_x_/consents/{consentId}/authorise

v2

PARAMETRO\_INVALIDO

errorCodes

Registrar os códigos de erro detalhados de uma requisição que resultou em um erro HTTP (série 4xx ou 5xx).

Caso o HTTP Code seja 4XX ou 5XX, esse campo deve ser preenchido com a lista das strings obtidas em ".errors\[\].code", devendo constar apenas um código de erro.

string

CLIENT

4xx e 5xx exceto 422

POST  
GET  
PATCH

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals  
/open-banking/enrollments/v_x_/consents/{consentId}/authorise  
/open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise

v2

journeyIsLinked

Indica que o consentimento faz parte de uma jornada otimizada

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.isLinked”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada.  
Em casos em que a informação não está disponível espera-se o envio do valor FALSE.

string

CLIENT

Todos

POST  
GET

TRUE, FALSE

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}

v2

FALSE

journeyLinkId

Identifica o consentimento de dados vinculado a uma Jornada Otimizada.

Deve ser preenchido com a mesma string enviada ou recebida no campo “.data.journey.linkId”, retornado após a chamada inicial na API “POST /enrollments” em caso de Jornada Otimizada.  
Deve ser enviado se journeyIsLinked for TRUE.

string

CLIENT

Todos

POST  
GET

/open-banking/enrollments/v_x/_enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD331237

nfcPayment

Identifica se o pagamento foi realizado através de NFC

Enviar o valor do campo "x-bcb-nfc", presente no de request header do endpoint de autorização de consentimentos via JSR (POST /consents/{consentId}/authorise)

string

CLIENT

Todos

POST

TRUE, FALSE

/open-banking/enrollments/v_x_/consents/{consentId}/authorise

v2

FALSE

personType

Identifica a natureza do solicitante em uma transação ou consentimento.

Se .data.businessEntity estiver preenchido no payload, se estiver então preencher com "PJ", se não estiver então preencher com "PF"

string

CLIENT

2xx

POST  
GET

PF, PJ, PESSOA\_NATURAL, PESSOA\_JURIDICA

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}

v2

PJ

platform

Identifica a plataforma utilizada

Deve ser preenchido com a mesma string definida em ".data.platform"

string

CLIENT

Todos

POST

ANDROID, BROWSER, CROSS\_PLATFORM, IOS

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options

v2

ANDROID

recurringConsentId​

Identificador único do consentimento de longa duração criado para a iniciação de pagamento solicitada

Deverá ser um URN - Uniform Resource Name. Um URN, conforme definido na [RFC8141](https://tools.ietf.org/html/rfc8141) é um Uniform Resource Identifier - URI - que é atribuído sob o URI scheme "urn" e um namespace URN específico, com a intenção de que o URN seja um identificador de recurso persistente e independente da localização. Considerando a string urn:bancoex:C1DD33123 como exemplo para `recurringConsentId` temos:

-   o namespace(urn)
    
-   o identificador associado ao namespace da instituição transmissora (bancoex)
    
-   o identificador específico dentro do namespace (C1DD33123).  
    Informações mais detalhadas sobre a construção de namespaces devem ser consultadas na [RFC8141](https://tools.ietf.org/html/rfc8141).
    

string

CLIENT

Todos menos 4xx e 5xx para o método POST

POST

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise

v2

^urn:\[a-zA-Z0-9\]\[a-zA-Z0-9\\-\]{0,31}:\[a-zA-Z0-9()+,\\-.:=@;$\_!\*'%\\/?#\]+$

urn:bancoex:C1DD331237

rejectionReasonCode

Código da razão pela qual um consentimento ou pagamento foi rejeitado

Deve ser preenchido com a mesma string obtida no ".data.rejectionReason.code, “data.rejection.reason.code” ou “data.cancellation.reason.rejectionReason". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista.  
Dever ser enviado quando o status for REJECTED

string

CLIENT

Todos menos 4xx e 5xx

GET  
PATCH

REJEITADO\_DISPOSITIVO\_INCOMPATIVEL, REJEITADO\_FALHA\_FIDO, REJEITADO\_FALHA\_HYBRID\_FLOW, REJEITADO\_FALHA\_INFRAESTRUTURA, REJEITADO\_MANUALMENTE, REJEITADO\_MAXIMO\_CHALLENGES\_ATINGIDO, REJEITADO\_OUTRO, REJEITADO\_SEGURANCA\_INTERNA, REJEITADO\_TEMPO\_EXPIRADO\_ACCOUNT\_HOLDER\_VALIDATION, REJEITADO\_TEMPO\_EXPIRADO\_RISK\_SIGNALS, REJEITADO\_TEMPO\_EXPIRADO\_ENROLLMENT, REJEITADO\_TITULARIDADE\_DIVERGENTE

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}

v2

REJEITADO\_OUTRO

revocationReasonCode

Código indicador do motivo da revogação

Deve ser preenchido com a mesma string obtida no ".data.cancellation.reason.revocationReason". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista.  
Dever ser enviado quando o status for REVOKED

string

CLIENT

Todos (PATCH)  
200 (GET)

GET  
PATCH

REVOGADO\_FALHA\_INFRAESTRUTURA, REVOGADO\_MANUALMENTE, REVOGADO\_OUTRO, REVOGADO\_SEGURANCA\_INTERNA, REVOGADO\_VALIDADE\_EXPIRADA

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}

v2

REVOGADO\_OUTRO

rp

"Relying Party" (RP) onde reside originalmente na requisição FIDO

Deve ser preenchido com a mesma string definida em ".data.rp"

string

CLIENT

Todos

POST

/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options

v2

[passkey.app-demo.io](http://passkey.app-demo.io)

status

Identifica o status atual do recurso (como um consentimento, um pagamento ou vínculo) que está sendo reportado.

Deve ser preenchido com a mesma string obtida no ".data.status". Caso a informação esteja em formato de lista, enviar apenas o valor do primeiro item da lista

string

CLIENT

2xx

GET  
POST

AWAITING\_RISK\_SIGNALS, AWAITING\_ACCOUNT\_HOLDER\_VALIDATION, AWAITING\_ENROLLMENT, AUTHORISED, REVOKED, REJECTED

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}

v2

AWAITING\_RISK\_SIGNALS

tokenId

Identificador único e criptograficamente seguro do token utilizado no consumo da API.  
A implementação do tokenId preencherá a lacuna de rastreabilidade, permitindo vincular a emissão de cada token (incluindo os de CLIENT\_CREDENTIALS) às suas respectivas jornadas, mesmo quando múltiplos consentimentos forem iniciados por um único token. Isso resultará em uma visão mais completa da jornada do token, aprimorando a capacidade de rastreabilidade e análise operacional para as instituições e do ecossistema

O tokenId será gerado pelo cliente (role CLIENT) no momento do reporte para a PCM, aplicado um hash SHA256 sobre o token recebido e um Pepper (segredo) gerenciado internamente pela instituição. Este tokenId deve ser reportado na PCM, complementando as informações já existentes de grant\_type e consentId (onde aplicável). Para garantir a robustez criptográfica do hash, o Pepper utilizado deverá ser um valor aleatório e criptograficamente forte, gerenciado internamente pela instituição. Recomenda-se um tamanho de 128 a 256 bits para o Pepper, aplicado no cálculo do tokenId, como por exemplo, SHA256 (token + Pepper). O tokenId será composto pelos 72 bits iniciais do hash Base64URL-safe encoded. 

 **Importante:** O tokenId será gerado apenas quando o token for recebido com sucesso na resposta do POST /token. Em casos nos quais a requisição ao POST /token resultar em erros 4xx ou 5xx, o token não será obtido e, consequentemente, o tokenId não poderá ser gerado. Nessas situações, o campo tokenId deve ser omitido do reporte à PCM.

string

CLIENT

Todos exceto 4xx e 5xx

POST  
GET  
PATCH

/open-banking/enrollments/v_x_/enrollments  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-registration  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/fido-sign-options  
/open-banking/enrollments/v_x_/enrollments/{enrollmentId}/risk-signals  
/open-banking/enrollments/v_x_/consents/{consentId}/authorise  
/open-banking/enrollments/v_x_/recurring-consents/{recurringConsentId}/authorise

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
