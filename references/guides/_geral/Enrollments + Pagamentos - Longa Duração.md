# Enrollments + Pagamentos - Longa Duração

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Enrollments API – v2.2.0 - Payments Scheduling – Restricted FVP
    
-   **Módulos de teste:**
    
    -   **1º Módulo:** enrollments\_api\_payments\_scheduled-pix-verification\_1-2\_test-module\_v5
        
    -   **2º Módulo:** enrollments\_api\_payments\_scheduled-pix-verification\_2-2\_test-module\_v5
        

**Escopo de validação**

-   1º Módulo
    
    -   Agenda dois pagamentos pela Jornada Sem Redirecionamento e armazena os dados para a verificação posterior.  
        A partir de um SSA do Diretório, extrai-se a primeira URI de software\_origin\_uris e executa-se uma jornada completa de enrollment, guardando o enrollmentId e o refresh\_token (escopo nrp-consents); o GET /enrollments deve retornar 200, status AUTHORISED e dailyLimit/transactionLimit de R$ 1,00. Cria-se o consentimento (POST /consents) com schedule.daily de quantidade 2, startDate em D+1 e valor de R$ 1,00, que é autorizado pela JSR — assinando o challenge do sign-options com a chave privada e enviando userHandle vazio — chegando a AUTHORISED. Em seguida, agendam-se os dois pagamentos (POST /payments, FIDO\_FLOW, R$ 1,00 cada) para D+1 e D+2, que, após polling (RCVD/ACCP), ficam ambos com status SCHD. O consentId, os paymentId e o refreshToken são persistidos, e a Segunda Etapa é agendada para D+3 às 05:00 (BRT).
        
-   2º Módulo
    
    -   Executada automaticamente em D+3 às 05:00 (BRT), recuperando as informações armazenadas na Primeira Etapa. Com os paymentId persistidos e um token client\_credentials, o GET /payments/{paymentId} dos dois pagamentos deve retornar 200, status ACSC e data anterior à atual para ambos. Ao final, revoga-se o enrollment (PATCH /enrollments/{enrollmentId} → 204).
        

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

CPF utilizado durante a autenticação

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

Creditor Account Proxy

Proxy (chave Pix) do recebedor.

Obrigatório

12345678901

Creditor Account CPF/CNPJ

CPF ou CNPJ do titular da conta credora (recebedor)

Obrigatório

50685362006773

**Modelo de Configuração FVP**

![att\_0\_for\_2064581361.png](images/att_0_for_2064581361.png)

**Modelo JSON**

jsonwide760truetrue
