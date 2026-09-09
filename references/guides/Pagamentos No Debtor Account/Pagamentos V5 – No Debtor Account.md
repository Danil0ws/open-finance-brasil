# Pagamentos V5 – No Debtor Account

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Payments API – v5.0.0 - Open FVP
    
-   **Módulo de teste:** payments\_api\_no-debtor-account\_open\_test-module\_v5
    

**Escopo de validação**

Valida que, quando a conta de débito não é informada na requisição, o usuário é solicitado a selecioná-la durante a autorização. O fluxo inicia com um POST /consents sem informação de conta devedora e usando localInstrument DICT, retornando 201. Após o redirecionamento do usuário para autorizar o consentimento, o GET /consents retorna 200 com status AUTHORISED. Em seguida, o POST /payments retorna 201 e o pagamento é acompanhado por polling em GET /payments/{paymentId} enquanto o status for RCVD, ACCP ou ACPD, até atingir o estado definitivo ACSC.

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

**Conta credora (PF e PJ)**

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

CPF ou CNPJ do titular da conta credora (recebedor)

Obrigatório

50685362006773

Creditor Account Proxy

Proxy (chave Pix) do recebedor.

Obrigatório

12345678901

**Modelo de Configuração FVP**

![att\_0\_for\_2065170913.png](images/att_0_for_2065170913.png)

**Modelo JSON**

jsonwide760true
