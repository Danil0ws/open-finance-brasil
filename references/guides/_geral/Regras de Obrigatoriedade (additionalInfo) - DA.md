# Regras de Obrigatoriedade (additionalInfo) - DA

v 1.01

**Guia de leitura**

1.  Se o campo não está listado, é porque não existe a obrigatoriedade de enviá-lo.
    
2.  Nos endpoints, a referência “v_x_” indica que se aplicam às versões listadas na coluna “Versões”. Por exemplo, Endpoint “open-banking/automatic-payments/v_x_/recurring-consents/{recurringConsentId}” e Versões “v1 v2” significa que o endpoint é válido para as versões 1 e 2.
    

Dica: para rolar a tabela horizontalmente, segure SHIFT e utilize o botão de rolagem do mouse.

Dica: não existe a opção de exportar as tabelas para Excel, porém pode-se selecionar o conteúdo da página com CTRL+A, copiar e colar no Excel.

# Dados Abertos

**Campo**

**Grupo**

**Definição**

**Tipo**

**Http code**

**Métodos**

**Endpoints**

**Versões**

**Exemplo**

clientIp

Adiantamento a Depositantes

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-unarranged/v_x_/personal-unarranged-account-overdraft  
/open-banking/opendata-unarranged/v_x_/business-unarranged-account-overdraft

v1

192.168.0.1

clientIp

Câmbio

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/exchange/v_x_/online-rates  
/open-banking/exchange/v_x_/vet-values

v1

192.168.0.1

clientIp

Canais de Atendimento

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/channels/v_x_/branches  
/open-banking/channels/v_x_/electronic-channels  
/open-banking/channels/v_x_/phone-channels  
/open-banking/channels/v_x_/banking-agents

v2

192.168.0.1

clientIp

Cartão de Crédito

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-creditcards/v_x_/personal-credit-cards  
/open-banking/opendata-creditcards/v_x_/business-credit-cards

v1

192.168.0.1

clientIp

Contas

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-accounts/v_x_/business-accounts  
/open-banking/opendata-accounts/v_x_/personal-accounts

v1

192.168.0.1

clientIp

Credenciameto

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/acquiring-services/v_x_/personals  
/open-banking/acquiring-services/v_x_/businesses

v1

192.168.0.1

clientIp

Direitos Creditórios Descontados

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-invoicefinancings/v_x_/personal-invoice-financings  
/open-banking/opendata-invoicefinancings/v_x_/business-invoice-financings

v1

192.168.0.1

clientIp

Empréstimos

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-loans/v_x_/personal-loans  
/open-banking/opendata-loans/v_x_/business-loans

v1

192.168.0.1

clientIp

Financiamentos

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-financings/v_x_/personal-financings  
/open-banking/opendata-financings/v_x_/business-financings

v1

192.168.0.1

clientIp

Investimentos

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/investments/v_x_/funds  
/open-banking/investments​/v_x_/bank-fixed-incomes  
/open-banking/investments​/v_x_/credit-fixed-incomes  
/open-banking/investments​/v_x_/variable-incomes  
/open-banking/investments​/v_x_/treasure-titles

v1

192.168.0.1

clientIp

Previdência

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/pension/v_x_/risk-coverages  
/open-banking/pension/v_x_/survival-coverages

v2

192.168.0.1

clientIp

Seguros

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-insurance/v_x_/personals

v2

192.168.0.1

clientIp

Titulos de Capitalização

Endereço IPv4 ou IPv6 do client que fez a requisição

string

Todos

GET

/open-banking/opendata-capitalization/v_x_/bonds

v2

192.168.0.1
