# Changelog - [DC] Dados Cadastrais - v2.3.0 - v2.2.1

16falsenonelisttrue

## GET /business/financial-relations

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/procurators/items/civilName

Alterado - "description"

Alteração

Nome civil completo ou Razão Social

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

get/responses/200/data/procurators/items/cnpjCpfNumber

Alterado - "pattern"

Alteração

^\\d{11}$|^\\d{14}$

^(\[0-9\]{11}|\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/procurators/items/cnpjCpfNumber

Alterado - "description"

Alteração

Identificação do Representante Legal ou Procurador. Número do cadastro nas Receita Federal (Preencher com CPF ou CNPJ sem formata...

Identificação do Representante Legal ou Procurador. Registro do cadastro na Receita Federal (Preencher com CPF ou CNPJ sem formata...

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/headers

Adicionado - "x-v"

Adição

## GET /business/identifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/cnpjNumber

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/items/cnpjNumber

Alterado - "description"

Alteração

Número completo do CNPJ da Empresa consultada - o CNPJ corresponde ao número de inscrição no Cadastro de Pessoa Jurídica. Deve-se...

Número completo do CNPJ da Empresa consultada - o CNPJ corresponde a representação alfanumérica da inscrição no Cadastro de Pessoa...

get/responses/200/data/items/companiesCnpj

Alterado - "description"

Alteração

Número completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde ao número de inscrição no Cadastro de Pessoa...

Representação alfanumérica completa do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde a representação alfanumé...

get/responses/200/data/items/companiesCnpj/items

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/items/companyName

Alterado - "maxLength"

Alteração

70

144

get/responses/200/data/items/parties/items/civilName

Alterado - "description"

Alteração

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

get/responses/200/data/items/parties/items/companyName

Alterado - "maxLength"

Alteração

70

144

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/headers

Adicionado - "x-v"

Adição

## GET /business/qualifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/headers

Adicionado - "x-v"

Adição

## GET /personal/financial-relations

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/paychecksBankLink/items/employerCnpjCpf

Alterado - "pattern"

Alteração

^\\d{14}$|^\\d{11}$

^(\[0-9\]{11}|\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/paychecksBankLink/items/employerName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/paychecksBankLink/items/paycheckBankCnpj

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/paychecksBankLink/items/paycheckBankIspb

Alterado - "description"

Alteração

Número ISPB (Identificador do Sistema de Pagamentos Brasileiros) do instituição financeira contratada para prestar serviço de paga...

Registro ISPB (Identificador do Sistema de Pagamentos Brasileiros) da instituição contratada para prestar serviço de pagamento de ...

get/responses/200/data/paychecksBankLink/items/paycheckBankIspb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/portabilitiesReceived/items/employerCnpjCpf

Alterado - "pattern"

Alteração

^\\d{14}$|^\\d{11}$

^(\[0-9\]{11}|\[0-9A-Z\]{12}\[0-9\]{2})$

get/responses/200/data/portabilitiesReceived/items/employerCnpjCpf

Alterado - "description"

Alteração

Número de inscrição (CPF/CNPJ) do empregador (contratante dos serviços de pagamento), conforme recebido pela comunicação de portab...

Registro de inscrição (CPF/CNPJ) do empregador (contratante dos serviços de pagamento), conforme recebido pela comunicação de port...

get/responses/200/data/portabilitiesReceived/items/employerName

Alterado - "pattern"

Alteração

^(?!\\s)\[\\w\\W\\s\]\*\[^\\s\]$

^\[^\\s\](.\*\[^\\s\])?$

get/responses/200/data/portabilitiesReceived/items/paycheckBankDetainerCnpj

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/portabilitiesReceived/items/paycheckBankDetainerCnpj

Alterado - "description"

Alteração

Número de inscrição no Cadastro Nacional da Pessoa Jurídica (CNPJ) do banco folha (instituição financeira detentora da conta salár...

Registro de inscrição no Cadastro Nacional da Pessoa Jurídica (CNPJ) do banco folha (instituição detentora da conta salário) confo...

get/responses/200/data/portabilitiesReceived/items/paycheckBankDetainerIspb

Alterado - "description"

Alteração

Número do ISPB do Banco Folha (instituição financeira detentora da conta salário) conforme recebido pela comunicação de portabilid...

Registro do ISPB do Banco Folha (instituição detentora da conta salário) conforme recebido pela comunicação de portabilidade.

get/responses/200/data/portabilitiesReceived/items/paycheckBankDetainerIspb

Alterado - "pattern"

Alteração

^\[0-9\]{8}$

^\[0-9A-Z\]{8}$

get/responses/200/data/procurators/items/civilName

Alterado - "description"

Alteração

Nome civil completo da pessoa natural. (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o re...

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

## GET /personal/identifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/items/civilName

Alterado - "description"

Alteração

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

get/responses/200/data/items/companiesCnpj

Alterado - "description"

Alteração

Número completo do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde ao número de inscrição no Cadastro de Pessoa...

Representação alfanumérica completa do CNPJ da instituição responsável pelo Cadastro - o CNPJ corresponde a representação alfanumé...

get/responses/200/data/items/companiesCnpj/items

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/items/contacts

Alterado - "description"

Alteração

Conjunto de informações referentes às formas para contatar o cliente.

Conjunto de informações referentes às formas para contatar o cliente. Os dados deste campo são de envio obrigatório. Só não devem ...

get/responses/200/data/items/filiation/items/civilName

Alterado - "description"

Alteração

Nome civil completo da pessoa relativa à filiação. (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natura...

Nome civil completo da pessoa natural (Direito fundamental da pessoa, o nome civil é aquele atribuído à pessoa natural desde o reg...

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/headers

Adicionado - "x-v"

Adição

## GET /personal/qualifications

### Response

**Campo**

**O que foi alterado?**

**Tipo da Alteração**

**Antes**

**Depois**

get/responses/200/data/companyCnpj

Alterado - "pattern"

Alteração

^\\d{14}$

^\[0-9A-Z\]{12}\[0-9\]{2}$

get/responses/200/data/occupationDescription

Alterado - "description"

Alteração

Campo livre, de preenchimento obrigatório. Se selecionada a opção \*occupationCode\* "RECEITA\_FEDERAL" ou "CBO", informar o código d...

Campo de livre preenchimento para informar o código da ocupação ou um descritivo da ocupação. Ao preencher o campo atentar para o ...

get/responses/200/data/employers

Adicionado - "employers"

Adição

get/responses/200/data/employers/cnpjCpf

Adicionado - "cnpjCpf"

Adição

get/responses/200/data/employers/name

Adicionado - "name"

Adição

get/responses/200/headers

Adicionado - "x-v"

Adição

get/responses/200/links/first

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/last

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/next

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/prev

Alterado - "maxLength"

Alteração

2000

4048

get/responses/200/links/self

Alterado - "maxLength"

Alteração

2000

4048
