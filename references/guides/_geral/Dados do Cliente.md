# Dados do Cliente

_Para as devidas instruções de acesso e configurações iniciais da ferramenta, é recomendado que sejam seguidas as etapas presentes no Guia de Operação da FVP, na etapa “__Pré-requisitos e configurações para execução__”;_

A ferramenta pode ser acessada no link: [https://web.fvp.directory.openbankingbrasil.org.br/](https://web.fvp.directory.openbankingbrasil.org.br/)

-   **Plano de teste:** Customer Data APIs – v2/v3 - Happy Path – Open FVP
    
-   **Módulo de teste:** fvp-customer\_data\_unique\_happy\_path\_test-module
    

**Escopo de validação**

Valida que todos os endpoints das APIs de compartilhamento consentidas e registradas no Diretório podem ser acessados com sucesso, cobrindo o ciclo completo de consentimento e consumo de dados. Como pré-condições, exige brazilCpf informado, client\_id gerado no DCR, well-known registrado no Diretório e servidor com as APIs de Consentimento e de Recursos em versão 3.0.0 ou superior, além dos produtos do servidor obtidos no Diretório. O fluxo inicia com um POST /consents (v3.3.1) contendo todas as permissões existentes — escopo pessoal ou empresarial conforme CPF/CNPJ — e sem expirationDateTime, retornando 201; o GET /consents (v3.3.1) retorna 200 com status AWAITING\_AUTHORISATION e sem expirationDateTime na resposta. Após a autorização do consentimento pelo usuário (redirect), um novo GET /consents (v3.3.1) retorna 200 com status AUTHORISED, mantendo as permissões de Operações de Crédito, Investimentos e Câmbio. Em seguida, para cada endpoint de cada API de dados registrada e permitida, executa-se a chamada e a validação da resposta: o GET /resources retorna 200 ou 202 (neste caso, com polling de até 5 minutos até retornar 200) e os GET de Accounts, Credit Card, Customer, Financings, Invoice Financings, Loans, Bank Fixed Incomes, Credit Fixed Incomes, Variable Incomes, Funds, Treasure Titles e Exchange retornam 200. Por fim, o DELETE /consents (v3) retorna 204 e registra-se (log) a lista de endpoints testados.

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

![att\_0\_for\_2065236468.png](images/att_0_for_2065236468.png)

**Modelo JSON**

jsonwide760truetrue
