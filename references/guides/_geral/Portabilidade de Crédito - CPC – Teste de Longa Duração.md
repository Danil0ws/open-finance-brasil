# Portabilidade de Crédito - CPC – Teste de Longa Duração

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   Plano de teste: Credit Portability API – v1.0.0 - Personal Scheduling – Restricted FVP
    
-   **Módulos de teste:**
    
    -   **1º Módulo:** fvp-credit-portability\_api\_accepted\_settlement\_1-3\_test-module\_v1
        
    -   **2º Módulo:** fvp-credit-portability\_api\_accepted\_settlement\_2-3\_test-module\_v1
        
    -   **3º Módulo**: fvp-credit-portability\_api\_accepted\_settlement\_3-3\_test-module\_v1
        

**Escopo de validação**

-   **1º Módulo**
    
    -   Garante que a solicitação de portabilidade alcança o status RECEIVED e armazena os dados para o acompanhamento. Pré-condição: o usuário deve ter ao menos um contrato CREDITO\_PESSOAL\_CLEAN com concurrent-management DISPONIVEL e isEligible = TRUE.  
        Cria-se o consentimento via POST /consents com o grupo de Operações de Crédito, retornando 201 em AWAITING\_AUTHORISATION; após a autorização (redirect), o GET /consents/{consentId} retorna 200 em AUTHORISED e o GET /resources retorna 200 ou 202 (neste caso, polling de até 5 minutos até 200). O teste então descobre o contrato: o GET de contratos de empréstimo (200) retorna os contractId com productSubType = CREDITO\_PESSOAL\_SEM\_CONSIGNACAO e o companyCnpj \[1\]; para cada contractId, o GET /credit-operations/{contractId}/portability-eligibility é chamado até encontrar um com status DISPONIVEL e isEligible = TRUE (ou retorna estado de aviso). Do contrato selecionado, coletam-se instalmentPeriodicity \[2\], dueInstalments (scheduled-installments) \[3\] e contractOutstandingBalance (payments) \[4\]. Com esses dados, o POST /portabilities é enviado com creditor.companyCnpj = \[1\], instalmentPeriodicity = \[2\], proposedContract.totalNumberOfInstalments = \[3\] e contractAmount = \[4\], retornando 202; o GET /portabilities/{portabilityId} retorna 200 com data.status = RECEIVED. Ao final, a Segunda Etapa é agendada para D+1 (próximo dia útil) às 10:10 (BRT), persistindo-se consentId, contractId, portabilityId, clientId, refresh\_token e countIteration\[1\] = 0.
        
-   **2º Módulo**
    
    -   Garante que a solicitação alcança ACCEPTED\_SETTLEMENT\_IN\_PROGRESS e, então, cancela a portabilidade. Executada a partir dos dados armazenados.  
        O GET /portabilities/{portabilityId} retorna 200 com data.status igual a PENDING ou ACCEPTED\_SETTLEMENT\_IN\_PROGRESS. Se PENDING, verifica-se countIteration\[1\] < 2 e reagenda-se a própria Segunda Etapa para o próximo dia útil, incrementando countIteration\[1\]. Se ACCEPTED\_SETTLEMENT\_IN\_PROGRESS, verifica-se countIteration\[1\] < 3 e prossegue-se ao cancelamento: o PATCH /portabilities/{portabilityId}/cancel (com rejectedBy = USUARIO e reason.type = CANCELADO\_PELO\_CLIENTE) retorna 200, e um novo GET /portabilities/{portabilityId} confirma 200 com status CANCELLED e statusReason.reasonType = CANCELADO\_PELO\_CLIENTE. A Terceira Etapa é então agendada para D+1 às 00:01 (BRT), persistindo consentId, contractId, portabilityId, clientId e refresh\_token.
        
-   **3º Módulo**
    
    -   Garante que o contrato retorna ao status DISPONIVEL. Executada a partir dos dados armazenados.  
        O GET /credit-operations/{contractId}/portability-eligibility retorna 200 com data.portability.status = DISPONIVEL e data.portability.isEligible = TRUE. Por fim, o DELETE /consents/{consentId} retorna 204.
        

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

![att\_0\_for\_2065040035.png](images/att_0_for_2065040035.png)

**Modelo JSON**

jsonwide760truetrue
