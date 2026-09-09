# Pagamentos V5 – Not Cancelled

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Payments API – v5.0.0 - Open FVP
    
-   **Módulo de teste:** fvp-payments\_api\_recurring-payments-custom-not-cancelled\_open\_test-module\_v5
    

**Escopo de validação**

Valida que um consentimento de pagamentos recorrentes customizados pode ser criado e que os pagamentos são agendados com sucesso. O fluxo inicia com um POST /consents com o campo schedule.custom.dates definido para D+1 e D+2, retornando 201; após a autorização do usuário (redirect), o GET /consents retorna 200 em AUTHORISED. Em seguida, um POST /payments cria os dois pagamentos, cada um com o endToEndId apropriado, retornando 201; após polling em GET /payments/{paymentId} (RCVD/ACCP) sobre o último pagamento criado, o GET /payments dos dois retorna sucesso com status SCHD em ambos. Ao final, o client criado é excluído.

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

![att\_0\_for\_2065039902.png](images/att_0_for_2065039902.png)

**Modelo JSON**

jsonwide760truetrue
