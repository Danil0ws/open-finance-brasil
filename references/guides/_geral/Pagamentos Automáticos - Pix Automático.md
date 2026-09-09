# Pagamentos Automáticos - Pix Automático

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Automatic Pix Payments – v2.2.0 - Automatic Pix – Open FVP
    
-   **Módulo de teste:** fvp\_automatic-payments\_api\_automatic-pix-semanal-core\_open\_test-module\_v2-2
    

wide760

Nota: O Pix Automático foi desenvolvido para pagamentos destinados a pessoas jurídicas (empresas). A conta a ser creditada deve ser corporativa (CNPJ). Pagamentos para pessoas físicas não são suportados.

**Escopo de validação**

O teste valida que um Pix Automático semanal pode ser autorizado, executado e cancelado, exigindo R$ 2,00 na conta do devedor em D+0. Cria-se o consentimento recorrente (POST /recurring-consents) com início em D+1, periodicidade SEMANAL, valor fixo de R$ 0,50 e um firstPayment de R$ 1,00 em D+0; após a autorização pelo usuário, o consentimento passa a AUTHORISED. O primeiro pagamento (R$ 1,00) é executado e acompanhado até liquidar em ACSC; um segundo pagamento, agendado para D+2 (R$ 0,50), fica em SCHD e é então cancelado via PATCH, indo para CANC. Ao final, confirma-se que os dois pagamentos retornam com os status ACSC e CANC, respectivamente.

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

**Nota**: Contas salário (SLRY) não são permitidas nessa API.

## **Modelo de Configuração FVP**

![att\_0\_for\_2065236438.png](images/att_0_for_2065236438.png)

**Modelo JSON**

jsonwide760true
