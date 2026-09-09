# Changelog - Cartão de Crédito - v2.0.0

#### **Descrição macro das alterações aplicadas às APIs de Dados Cadastrais e Transacionais em relação aos payloads:**

-   Nenhum campo poderá receber o valor NA. Seguem regras de acordo com os casos:
    
    -   Obrigatórios: foram revistas as mandatoriedades a fim de atender as regras de negócios de cada um dos produtos;
        
    -   Opcionais: para estes casos basta não enviar o campo;
        
    -   Condicionais: se comportam como opcionais, exceto quando o cenário se encaixar na restrição incluída na descrição;
        
    -   Enums: Retiradas as opções com valor NAO\_APLICA e similares;
        
    -   Removidos todos os atributos Nullable dos campos, que foram analisados obedecendo critérios de mandatoriedade e cenários de negócio.
        
-   Com o objetivo de normalizar o formato dos dados entre as pontas, foram acrescentados patterns em todos os campos elegíveis.
    
-   Foram normalizados os atributos dos campos de acordo com o seu tipo de dado.
    
-   Todas as ocorrências de campos _additionalInfo_ foram alteradas para opcional ou condicional de acordo com suas características de negócio. Para os campos condicionais foram acrescentadas restrições de cenário de uso.
    
-   Foram alterados todos os campos numéricos do tipo double para string com format double, com isso garantimos que exista um formato de dados padrão, tornando possível que todas as casas, considerando suas peculiaridades sistêmicas, consigam realizar o tráfego das informações.
    
-   Revista a mandatoriedade dos arrays, considerando os seguintes cenários:
    
    -   Obrigatórios, passam a receber minItems: 0. Considerando que caso as informações não existam, o array precisa ser enviado vazio. Nesse cenário atendemos ao conjunto de informações relativas a um produto, onde um cenário específico não pode ser atendido mesmo existindo como característica do produto, é como quem está enviando dizer “não tenho essa informação para este produto”.
        
    -   Opcionais e condicionais, passam a receber minItems: 1. Caso não exista a informação basta não enviar o array, existindo, deve ser preenchido pelo menos 1.
        
-   Inserção e remoção de campos atendendo às especificidades de cada produto (API).
    
-   Removidos os campos totalPages e totalRecords dos exemplos de response codes de exceção.
    
-   Adicionados novos response codes.
    

GET /accounts

**Campo**

**O que foi feito?**

brandName

Alterada descrição do campo

companyCnpj

Alterado pattern

productType

Removido maxLength

creditCardNetwork

Removido maxLength

networkAdditionalInfo

Alterado exemplo

networkAdditionalInfo

Alterado o exemplo

creditCardAccountId

Alterado o pattern

Adicionado minLength

Header

Adicionado campo pagination-key

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /accounts/{creditCardAccountId}

**Campo**

**O que foi feito?**

productType

Removido maxLength

creditCardNetwork

Removido maxLength

networkAdditionalInfo

Alterado o exemplo

identificationNumber

Alterado o pattern  
Adicionado minLength

paymentMethod

Adicionada descrição

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /accounts/{creditCardAccountId}/bills

**Campo**

**O que foi feito?**

data

Adicionado minItems

billTotalAmount

Convertido em objeto com os atributos amount e currency  
Alterada descrição

billTotalAmountCurrency

Removido campo

billMinimumAmountCurrency

Removido campo

billTotalAmount/amount

Alterada descrição  
Alterado pattern

data/billMinimumAmount

Convertido em objeto com os atributos amount e currency  
MaxLength alterado

financeCharges

Alterada mandatoriedade

data/financeCharges/type

Removido maxLength  
Removida opção “SEM\_ENCARGO“

data/financeCharges/amount

Alterado pattern  
Alterado descrição  
Nullable removido  
Alterado para string  
Alterado exemplo  
Alterado minLength  
Alterado maxLength

payments/amount

Alterado pattern  
Alterada a descrição  
Alterado para string  
Alterado exemplo  
Alterado minLength

data/payments/valueType

Removido maxLength  
Alterada descrição

data/payments/paymentMode

Removido maxLength

billId

Alterado o pattern  
Adicionado minLength

Swagger

Alterado texto em Orientações Gerais

Swagger

Alterada descrição do endpoint

Header

Adicionado campo pagination-key

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /accounts/{creditCardAccountId}/bills/{billId}/transactions

**Campo**

**O que foi feito?**

data

Adicionado minItems

lineName

Removido campo

creditDebitType

Removido maxLength

transactionType

Removido maxLength

transactionalAdditionalInfo

Pattern adicionado

transactionDate

Alterado pattern

paymentType

Removido maxLength  
Alterada descrição

feeType

Removido maxLength  
Alterada mandatoriedade  
Adicionada restrição

feeTypeAdditionalInfo

Alterada mandatoriedade  
Pattern adicionado

otherCreditsType

Removido maxLength  
Alterada mandatoriedade

otherCreditsAdditionalInfo

Pattern adicionado  
Alterada mandatoriedade  
Adicionado restrição

chargeNumber

Removido maxLength  
Nullable removido  
Alterada mandatoriedade  
Adicionada restrição  
Alterado exemplo  
Adicionado maximum

brazilianAmount

Convertido em objeto com os atributos amount e currency  
Alterada descrição  
Alterada mandatoriedade

brazilianAmount/amount

Alterado maxLength  
Alterado minLength  
Alterado exemplo  
Alterado format para double

amount

Convertido em objeto com os atributos amount e currency  
Alterada descrição  
Alterada mandatoriedade

amount/amount

Alterado maxLength  
Alterado minLength  
Alterado example  
Alterado format para double

currency

Removido campo

billPostDate

Alterado pattern

payeeMCC

Removido nullable  
Removido maxLength  
Adicionado maximum  
Alterada mandatoriedade

links/last

Removido campo

transactionId

Alterado pattern

Adicionado minLength

identificationNumber

Alterado pattern

Adicionado minLength

billId

Alterado pattern

Adicionado minLength

Swagger

Alterado texto em Orientações Gerais

Swagger

Alterada descrição do endpoint

Header

Adicionado campo pagination-key

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /accounts/{creditCardAccountId}/limits

**Campo**

**O que foi feito?**

data

Alterada mandatoriedade  
Adicionado minItems

creditLineLimitType

Alterada descrição  
Removido maxLength

consolidationType

Alterada descrição  
Removido maxLength

lineName

Removido maxLength

lineNameAdditionalInfo

Adicionado maxLength

limitAmount

Convertido em objeto com os atributos amount e currency  
Alterada descrição  
Alterada mandatoriedade

limitAmount/amount

Alterado para string com format double  
Alterada descrição  
Alterada mandatoriedade  
Adicionada restrição  
Alterado pattern  
Alterado minLength  
Alterado exemplo  
Removido nullable

limitAmount/currency

Alterado pattern  
Alterada descrição  
Adicionada restrição

limitAmountCurrency

Removido campo

usedAmount

Convertido em objeto com os atributos amount e currency  
Alterada descrição  
Alterada mandatoriedade

usedAmount/amount

Alterado para string com format double  
Alterada descrição  
Alterado pattern  
Alterado minLength  
Alterado maxLength  
Alterado exemplo  
Removido nullable

usedAmount/currency

Alterado pattern

usedAmountCurrency

Removido campo

availableAmount

Convertido em objeto com os atributos amount e currency  
Alterada descrição  
Alterada mandatoriedade

availableAmount/amount

Alterado para string com format double  
Alterada mandatoriedade  
Adicionada restrição  
Alterado minLength  
Alterado maxLength  
Alterado exemplo  
Removido nullable

availableAmount/currency

Alterado pattern  
Alterada mandatoriedade  
Adicionada restrição

availableAmountCurrency

Removido campo

identificationNumber

Alterado pattern  
Adicionado minLength

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /accounts/{creditCardAccountId}/transactions

**Campo**

**O que foi feito?**

data

Alterado minItems

lineName

Removido campo

creditDebitType

Removido maxLength

transactionType

Removido maxLength

transactionalAdditionalInfo

Pattern adicionado  
Alterada mandatoriedade

paymentType

Removido maxLength  
Alterada descrição

feeType

Removido maxLength  
Alterada mandatoriedade  
Adicionada restrição

feeTypeAdditionalInfo

Pattern adicionado  
Alterada mandatoriedade

otherCreditsType

Removido maxLength  
Alterada mandatoriedade  
Adicionada restrição

otherCreditsAdditionalInfo

Pattern adicionado  
Alterada mandatoriedade  
Adicionado restrição  
Alterada descrição

chargeNumber

Alterada mandatoriedade  
Adicionado restrição  
Maximum adicionado  
Nullable removido  
Removido maxLength  
Alterado exemplo

brazilianAmount

Convertido em objeto com os atributos amount e currency

brazilianAmount/amount

Alterada descrição

brazilianAmount/currency

Alterada descrição

amount

Convertido em objeto com os atributos amount e currency

amount/amount

Alterada descrição

currency

Removido campo

transactionDate

Alterado pattern

billPostDate

Alterado pattern

payeeMCC

Removido de nullable  
Removido maxLength  
Adicionado maximum  
Alterada mandatoriedade

transactionId

Alterado de pattern  
Adicionado minLength

identificationNumber

Alterado pattern  
Adicionado minLength

billId

Alterado pattern  
Adicionado minLength

links/last

Removido campo

meta/totalRecords

Removido campo

meta/totalPages

Removido campo

Swagger

Alterada descrição do endpoint

Swagger

Alterado texto em Orientações Gerais

Header

Adicionado campo pagination-key

Header

Adicionada restrição em fromTransactionDate

Header

Adicionada restrição em toTransactionDate

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /accounts/{creditCardAccountId}/transactions-current

**Campo**

**O que foi feito?**

Novo endpoint

Novo endpoint
