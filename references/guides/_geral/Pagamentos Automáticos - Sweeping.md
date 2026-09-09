# Pagamentos Automáticos - Sweeping

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Automatic Payments API – v2.2.0 - Open FVP
    
-   **Módulo de teste:** fvp\_automatic-payments\_api\_sweeping-accounts-core\_test-module\_v2-2
    

**Escopo de validação**

Valida que um pagamento por varredura de contas (sweeping) pode ser autorizado e executado e que, ao atingir o valor total do consentimento, este é encerrado (CONSUMED). Observação de configuração: se brazilCpf ou brazilCnpj for informado, o mesmo documento é usado tanto no loggedUser/businessEntity quanto no credor; caso contrário, a instituição precisa ter uma conta registrada com o CPF 99991111140.

O fluxo inicia com um POST /recurring-consents com os campos de sweeping, amount de R$ 1,00 e sem expirationDateTime, retornando 201 com status AWAITING\_AUTHORISATION; o GET /recurring-consents também retorna 201 em AWAITING\_AUTHORISATION. Após o usuário autorizar (redirect), um novo GET /recurring-consents retorna 201 com status AUTHORISED. Em seguida, um POST /recurring-payments inicia o primeiro pagamento com valor aleatório entre R$ 0,10 e R$ 0,49 para o credor selecionado, sem enviar ibgeTownCode, retornando 201; após polling em GET /recurring-payments/{recurringPaymentId} (RCVD/ACCP/ACPD), o pagamento liquida em ACSC, e o GET /recurring-consents/{recurringConsentId} confirma que o consentimento segue AUTHORISED. O processo é repetido para um segundo pagamento cujo valor é R$ 1,00 menos o valor do primeiro; nesse ponto, o GET /recurring-consents/{recurringConsentId} retorna 200 com status CONSUMED, indicando que o limite foi atingido. Por fim, o GET /recurring-payments (com o recurringConsentId no header) retorna 200 e recupera os dois paymentId, ambos com status ACSC.

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

**Conta credora (PF e PJ)**

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

**Modelo de Configuração FVP**

![att\_0\_for\_2065170903.png](images/att_0_for_2065170903.png)

**Modelo JSON**

jsonwide760true
