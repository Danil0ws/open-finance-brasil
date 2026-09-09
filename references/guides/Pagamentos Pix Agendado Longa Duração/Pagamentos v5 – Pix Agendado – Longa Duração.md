# Pagamentos v5 – Pix Agendado – Longa Duração

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Payments API – v5.0.0 – Scheduling – Restricted FVP
    
-   **Módulos de teste:**
    
    -   **1º Módulo:** payments\_api\_scheduled-pix-verification\_1-2\_test-module\_v5
        
    -   **2º Módulo:** payments\_api\_scheduled-pix-verification\_2-2\_test-module\_v5
        

**Escopo de validação**

-   1º Módulo
    
    -   Agenda dois pagamentos e armazena os dados necessários para a verificação posterior.  
        Cria-se o consentimento via POST /consents com schedule.daily de quantidade 2, startDate em D+1 e valor de R$ 1,00, retornando 201; após a autorização do usuário (redirect), o GET /consents retorna 200 em AUTHORISED. Em seguida, um POST /payments agenda os dois pagamentos (R$ 1,00 cada, com o endToEndId apropriado) para D+1 e D+2; após polling em GET /payments/{paymentId} (RCVD/ACCP) sobre o último pagamento criado, o GET /payments dos dois retorna 200 com status SCHD em ambos. Ao final, a Segunda Etapa é agendada para D+3 às 05:00 (BRT), persistindo-se consentId, os paymentId e o refreshToken.
        
-   2º Módulo
    
    -   Confirma que os pagamentos agendados foram executados com sucesso. Executada automaticamente em D+3 às 05:00 (BRT), recuperando os dados armazenados na Primeira Etapa. Com os paymentId persistidos e um token client\_credentials, o GET /payments/{paymentId} dos dois pagamentos retorna 200, com status ACSC e data anterior à atual para ambos.
        

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

![att\_0\_for\_2065236540.png](images/att_0_for_2065236540.png)

**Modelo JSON**

jsonwide760truetrue
