# Pagamentos Automáticos - Liquidação – Longa Duração

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Automatic Payments API – v2.2.0 - Automatic Pix Scheduling – restricted FVP.
    
-   **Módulos de teste:**
    
    -   **1º Módulo:** automatic-payments\_api\_automatic-pix-scheduling\_1-2\_test-module\_v2-2
        
    -   **2º Módulo:** automatic-payments\_api\_automatic-pix-scheduling\_2-2\_test-module\_v2-2
        

wide760

Nota: O Pix Automático foi desenvolvido para pagamentos destinados a pessoas jurídicas (empresas). A conta a ser creditada deve ser corporativa (CNPJ). Pagamentos para pessoas físicas não são suportados.

**Escopo de validação**

-   **1º Módulo**
    
    -   Agenda um pagamento recorrente e armazena os dados para a verificação posterior.  
        Cria-se o consentimento via POST /recurring-consents com campos de Pix Automático — referenceStartDate em D+1, expirationDateTime em D+180, interval SEMANAL, isRetryAccepted = FALSE e sem firstPayment —, retornando 201 em AWAITING\_AUTHORISATION; após a autorização (redirect), o GET /recurring-consents retorna 201 em AUTHORISED. Em seguida, um POST /recurring-payments de R$ 1,00 para D+2 retorna 201 e, após polling em GET /recurring-payments/{recurringPaymentId} (RCVD/ACCP), o pagamento fica em SCHD. Ao final, a Segunda Etapa é agendada para D+3 às 21:00 (BRT), persistindo-se consentId, paymentId, clientId e refresh\_token.
        
-   **2º Módulo**
    
    -   Confirma que o pagamento agendado foi executado com sucesso. Executada automaticamente em D+3 às 21:00 (BRT), recuperando os dados armazenados na Primeira Etapa.  
        Com o consentimento armazenado e um token client\_credentials, o GET /recurring-consents/{recurringConsentId} retorna 200 em AUTHORISED (com isRetryAccepted = FALSE e sem firstPayment). O GET /recurring-payments (com o recurringConsentId no header) retorna 200 e confirma um único pagamento com status ACSC e data anterior à atual.
        

**Preenchimento de Campos**

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

authorizationServerId

ID do Authorization Server da instituição no Diretório.

Obrigatório

770f6211-dbd4-4c84-b6b1-9104b4a99359

**Debtor Pessoa Física (PF)**

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

brazilCpf

CPF utilizado durante a autenticação.

Obrigatório

76109277673

**Debtor Pessoa Jurídica (PJ)**

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

**Debtor (PF e PJ)**

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

contractDebtorName

Nome do cliente devedor do contrato.

Obrigatório

João Silva

contractDebtorIdentification

CPF ou CNPJ do cliente devedor do contrato.

Obrigatório

76109277673

**Conta credora**

wide760

Importante: A conta recebedora deve, obrigatoriamente, pertencer a uma pessoa jurídica (CNPJ). Contas de pessoas físicas (CPF) não são válidas para fluxos de Pix Automático.

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

Creditor Account ISPB

Código ISPB da instituição financeira recebedora.

Obrigatório

99999004

Creditor Account Issuer

Código da agência da conta do recebedor.

Obrigatório

0001

Creditor Account Number

Número da conta credora.

Obrigatório

11188222

Creditor Account Type

Tipo da conta credora.

Obrigatório

SVGS

Creditor Account Name

Nome do titular da conta credora (recebedor).

Obrigatório

Empresa Exemplo S.A.

Creditor Account CPF/CNPJ

CNPJ do titular da conta credora (recebedor)

Obrigatório

50685362006773

wide760

**Sobre o campo accountType**: Indica o tipo de conta bancária utilizada pelo credor (recebedor). Este campo é obrigatório e deve ser consistente com os demais dados da conta (ISPB, agência, número).

**Valores Permitidos (conforme versão 2.2.0 da API do Open Finance Brasil):**

**Valor**

**Descrição**

CACC

Conta Corrente

SVGS

Conta Poupança

TRAN

Conta de Pagamento Pré-Paga

wide760

_**Nota**: Contas salário (SLRY) não são permitidas nessa API._

**Modelo de Configuração FVP**

![att\_0\_for\_2065040016.png](images/att_0_for_2065040016.png)

**Modelo JSON**

jsonwide760truetrue
