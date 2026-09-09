# Portabilidade de Crédito - CPC

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Credit Portability API – v1.0.0 - Personal – Open FVP
    
-   **Módulo de teste:** fvp-credit-portability\_api\_received-portability\_test-module\_v1
    

**Escopo de validação**

Valida que uma solicitação de portabilidade de crédito alcança o status RECEIVED. Pré-condição: o usuário deve possuir ao menos um contrato CREDITO\_PESSOAL\_CLEAN com elegibilidade de portabilidade DISPONIVEL e isEligible = TRUE.

O fluxo inicia com um POST /consents com o grupo de permissões de Operações de Crédito, retornando 201 com status AWAITING\_AUTHORISATION; após a autorização do usuário (redirect), o GET /consents/{consentId} retorna 200 em AUTHORISED. Em seguida, o GET /resources retorna 200 ou 202 (neste caso, com polling de até 5 minutos até 200). O teste então descobre e valida o contrato: o GET de contratos de empréstimo retorna 200 e recupera os contractId com productSubType = CREDITO\_PESSOAL\_SEM\_CONSIGNACAO e o companyCnpj \[1\]; para cada contractId, o GET /credit-operations/{contractId}/portability-eligibility é chamado até encontrar um com status DISPONIVEL e isEligible = TRUE (ou retorna estado de aviso). Do contrato selecionado, coletam-se, via GET, a instalmentPeriodicity \[2\], os dueInstalments (scheduled-installments) \[3\] e o contractOutstandingBalance (payments) \[4\].

Com esses dados, o POST /portabilities é enviado com creditor.companyCnpj = \[1\], instalmentPeriodicity = \[2\], proposedContract.totalNumberOfInstalments = \[3\] e contractAmount = \[4\], retornando 202. O GET /portabilities/{portabilityId} retorna 200 com data.status = RECEIVED. Em seguida, o PATCH /portabilities/{portabilityId}/cancel (com rejectedBy = USUARIO e reason.type = CANCELADO\_PELO\_CLIENTE) retorna 200, e um novo GET /portabilities/{portabilityId} confirma 200 com status CANCELLED e statusReason.reasonType = CANCELADO\_PELO\_CLIENTE. Por fim, o DELETE /consents/{consentId} retorna 204.

**Preenchimento de Campos**

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

authorizationServerId

ID do Authorization Server da instituição no Diretório.

Obrigatório

770f6211-dbd4-4c84-b6b1-9104b4a99359

**Segmento Pessoa Física (PF)**

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

brazilCpf

CPF utilizado durante a autenticação.

Obrigatório

76109277673

**Segmento Pessoa Jurídica (PJ)**

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

brazilCpf

CPF utilizado durante a autenticação.

Obrigatório

76109277673

brazilCnpj

CNPJ utilizado durante a autenticação, caso o teste seja com um usuário pessoa jurídica.

Obrigatório

82799716000165

**Modelo de Configuração FVP**

![att\_0\_for\_2065039903.png](images/att_0_for_2065039903.png)

**Modelo JSON**

jsonwide760truetrue
