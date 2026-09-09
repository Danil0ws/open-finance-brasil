# Testes e validações

## **Execução dos testes da FVP Automática na FVP Manual**

Os testes executados pela FVP Automática também podem ser executados manualmente na FVP em ambiente de Produção (PRD). Essa opção permite que a instituição analise as falhas identificadas e valide as correções realizadas antes da próxima execução automática.

No entanto, a execução manual não contempla necessariamente todos os testes disponíveis na FVP Automática. Portanto, os resultados obtidos na FVP Manual devem ser utilizados como apoio à análise e à correção das falhas, não como uma reprodução integral da execução automática.

Para executar os testes disponíveis na FVP, acesse a [Ferramenta de Validação em Produção](https://web.fvp.directory.openbankingbrasil.org.br) e selecione os seguintes campos:

Execução dos testes na Automatic FVP Mirror - Open FVP seguindo acessando a Ferramenta de Validação em Produição (Inserir Hiperlik), acessando a FVP deve escolher os seguintes campos:

**Campo**

**Valor**

**Specification**

Open Finance Brasil

**Entity Under Test**

Open Finance Brasil Functional Production Tests – FVP

**Test Plan**

Automatic FVP Mirror - Open FVP

O plano de testes Automatic FVP Mirror - Open FVP está disponível em Produção e reúne parte dos testes realizados pela FVP Automática.

Exemplo:

![att\_0\_for\_2065039496.png](images/att_0_for_2065039496.png)

Após selecionar os parâmetros, inicie a execução do plano de testes e acompanhe os resultados apresentados pela ferramenta.

## **Configuração de Teste – FVP (Ambiente de Produção)**

Os testes da **FVP Automática** foram projetados para execução no ambiente de **Produção**. Os testes disponíveis na FVP Manual podem auxiliar na investigação e na validação das correções, mas não abrangem necessariamente todos os testes executados pela FVP Automática.

Além disso, os certificados, as chaves e as demais configurações utilizadas pela instituição podem variar entre os ambientes. Por esse motivo, a aprovação nos testes disponíveis na FVP Manual não garante a aprovação na execução automatizada da FVP Automática.

Para obter mais informações sobre cada teste executado pela FVP Automática, consulte a seção Tabela de testes.

## **Execução no Motor de Conformidade Funcional**

Os testes também podem ser executados no Motor de Conformidade Funcional, em ambiente de Sandbox, para apoiar a validação das implementações e a correção das falhas em ambiente de homologação.

O plano de teste disponível nesse ambiente é:

-   **DCR - Automatic FVP Mirror - Conformance Suite** — [Web Conformance](https://web.conformance.directory.openbankingbrasil.org.br)
    

## **Configuração de Teste – FVP (Ambiente de Produção)**

**Preenchimento de Campos**

**Campo**

**Descrição**

**Obrigatoriedade**

authorizationServerId

ID do Authorization Server da instituição no Diretório.

Obrigatório

**Segmento Pessoa Física (PF)**

**Campo**

**Descrição**

**Obrigatoriedade**

brazilCpf

CPF utilizado durante a autenticação.

Obrigatório

**Segmento Pessoa Jurídica (PJ)**

**Campo**

**Descrição**

**Obrigatoriedade**

brazilCpf

CPF utilizado durante a autenticação.

Obrigatório

brazilCnpj

CNPJ utilizado durante a autenticação, caso o teste seja com um usuário pessoa jurídica.

Obrigatório

**Debtor (PF e PJ)**

**Campo**

**Descrição**

**Obrigatoriedade**

Payment consent - Debtor Account ISPB

Código ISPB da instituição financeira devedor do contrato.

Obrigatório

Payment consent - Debtor Account Issuer

Código da agência da conta do devedor.

Obrigatório

Payment consent - Debtor Account Number

Número da conta devedora.

Obrigatório

Payment consent - Debtor Account Type

Tipo da conta devedora.

Obrigatório

Recurring Payment consent - Contract Debtor Name

Nome do cliente devedor do contrato.

Obrigatório

Recurring Payment consent - Contract Debtor Identification

CPF ou CNPJ do cliente devedor do contrato.

Obrigatório

**Conta Credora (PF ou PJ)**

**Campo**

**Descrição**

**Obrigatoriedade**

Creditor Account ISPB

Código ISPB da instituição financeira credora.

Obrigatório

Creditor Account Issuer

Código da agência da conta do recebedor.

Obrigatório

Creditor Account Number

Número da conta credora.

Obrigatório

Creditor Account Type

Tipo da conta credora.

Obrigatório

Creditor Account Name

Nome titular da conta credora (recebedor).

Obrigatório

Creditor Account CPF/CNPJ

CPF ou CNPJ do titular da conta credora (recebedor)

Obrigatório

**Modelo JSON**

jsonwide760truetrue
