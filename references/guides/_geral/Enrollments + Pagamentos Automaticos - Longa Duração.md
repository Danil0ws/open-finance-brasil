# Enrollments + Pagamentos Automaticos - Longa Duração

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Enrollments API – v2.2.0 - Automatic Payments Scheduling – Restricted FVP
    
-   **Módulos de teste:**
    
    -   **1º Módulo:** enrollments\_api\_automatic-payments\_automatic-pix-scheduling\_1-2\_test-module\_v2-2
        
    -   **2º Módulo:** enrollments\_api\_automatic-payments\_automatic-pix-scheduling\_2-2\_test-module\_v2-2
        

wide760

O Pix Automático foi desenvolvido para pagamentos destinados a pessoas jurídicas (empresas). A conta a ser creditada deve ser corporativa (CNPJ). Pagamentos para pessoas físicas não são suportados.

**Escopo de validação**

-   1º Módulo
    
    -   Agenda um pagamento recorrente pela Jornada Sem Redirecionamento e armazena os dados para a verificação posterior. Cria-se o consentimento recorrente (SEMANAL, início D+1, expiração D+180, isRetryAccepted = FALSE, sem firstPayment), que é autorizado pela JSR — assinando o challenge do sign-options com a chave privada — chegando a AUTHORISED. Por fim, agenda-se um pagamento de R$ 1,00 para D+2, que fica com status SCHD. O recurringConsentId, o enrollmentId e os tokens ficam persistidos para uso na Segunda Etapa.
        
-   2º Módulo
    
    -   Executada automaticamente em D+3 (um dia após a data agendada, D+2), recuperando as informações armazenadas na Primeira Etapa. Com os dados persistidos, valida-se o consentimento (AUTHORISED, isRetryAccepted = FALSE, sem firstPayment) e o pagamento único, que deve estar em ACSC com data anterior à atual. Ao final, revogam-se o consentimento e o enrollment (PATCH → 204).
        

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

**Conta credora (PF e PJ)**

wide760

Importante: A conta recebedora deve, obrigatoriamente, pertencer a uma pessoa jurídica (CNPJ). Contas de pessoas físicas (CPF) não são válidas para fluxos de Pix Automático.

**Campo**

**Descrição**

**Obrigatoriedade**

**Exemplo**

Creditor Account ISPB

Código ISPB da instituição financeira credora.

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

Sobre o campo **accountType**: Indica o tipo de conta bancária utilizada pelo credor (recebedor). Este campo é obrigatório e deve ser consistente com os demais dados da conta (ISPB, agência, número).

**Valores Permitidos (conforme versão 2.2.0 da API):**

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

![att\_0\_for\_2065171016.png](images/att_0_for_2065171016.png)

**Modelo JSON**

jsonwide760truetrue
