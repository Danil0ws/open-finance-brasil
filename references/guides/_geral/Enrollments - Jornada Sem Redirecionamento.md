# Enrollments - Jornada Sem Redirecionamento

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Enrollments API – v2.2.0 - Payments – Open FVP
    
-   **Módulo de teste:** fvp-enrollments\_api\_payments-core\_open\_test-module\_v2-2
    

**Escopo de validação**

O teste garante que um pagamento sem redirecionamento alcance o estado aceito (ACSC). A partir de um SSA do Diretório, extrai-se a primeira URI de software\_origin\_uris e executa-se uma jornada completa de enrollment, guardando o enrollmentId e o refresh\_token (escopo nrp-consents); o GET /enrollments deve retornar 200, status AUTHORISED e dailyLimit/transactionLimit de R$ 1,00. Cria-se o consentimento (POST /consents, R$ 0,50), que é autorizado pela JSR — assinando o challenge do sign-options com a chave privada e enviando userHandle vazio —, com o GET /consents confirmando AUTHORISED. Em seguida, o pagamento é iniciado (POST /payments, FIDO\_FLOW, R$ 0,50) e acompanhado por polling enquanto o status for RCVD, ACCP ou ACPD, até liquidar em ACSC. Ao final, revoga-se o enrollment (PATCH /enrollments/{enrollmentId} → 204)

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

Emissor da conta credora: agência da instituição credora.

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

Creditor Account Proxy

Proxy (chave Pix) do recebedor.

Obrigatório

12345678901

Creditor Account CPF/CNPJ

CPF ou CNPJ do titular da conta credora (recebedor)

Obrigatório

50685362006773

**Modelo de Configuração FVP**

![att\_0\_for\_2064581263.png](images/att_0_for_2064581263.png)

**Modelo JSON**

jsonwide760truetrue
