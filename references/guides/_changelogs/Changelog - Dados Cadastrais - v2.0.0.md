# Changelog - Dados Cadastrais - v2.0.0

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
    

## API Customers

GET /personal/identifications

**Campo**

**O que foi feito?**

data

Adicionado minItems

birthDate

Alterado exemplo

brandName

Alterada descrição

civilName

Alterado pattern

companiesCnpj

Renomeado campo para o plural  
Alterado pattern  
Adicionado minItems

contacts/emails

Alterado minItems

contacts/phones

Alterado minItems

contacts/phones/areaCode

Removido maxLength  
Removido enum

contacts/phones/countryCallingCode

Alterado pattern  
Adicionado Restrição

contacts/phones/number

Alterado pattern

contacts/phones/phoneExtension

Alterada mandatoriedade  
Alterado pattern

contacts/phones/type

Removido maxLength

contacts/postalAddresses

Alterado minItems

contacts/postalAddresses/address

Alterada mandatoriedade  
Alterado pattern  
Adicionado minLength

contacts/postalAddresses/countryCode

Alterada mandatoriedade  
Alterada descrição  
Adicionado pattern

contacts/postalAddresses/countrySubDivision

Alterada mandatoriedade  
Removido NA do enum

contacts/postalAddresses/districtName

Alterada mandatoriedade  
Alterada descrição

contacts/postalAddresses/geographicCoordinates/latitude

Alterada descrição  
Alterado exemplo  
Alterada mandatoriedade

contacts/postalAddresses/geographicCoordinates/longitude

Alterada descrição  
Alterado exemplo  
Alterada mandatoriedade

contacts/postalAddresses/postCode

Alterada mandatoriedade  
Pattern alterado

documents

Realocados os campos: passportNumber, passportCountry, passportExpirationDate e passportIssueDate em um novo objeto chamado passport

documents/cpfNumber

Alterada mandatoriedade  
Alterado pattern  
Alterada a descrição

documents/otherDocuments/number

Alterado maxLength

documents/passport

Criado objeto com os atributos number, country, expirationDate e issueDate

documents/passport/number

Alterado pattern

documents/passport/expirationDate

Alterada mandatoriedade

filiation

Alterada mandatoriedade  
Adicionado minItems

filiation/civilName

Alterado pattern

filiation/socialName

Removido exemplo  
Alterado pattern  
Alterada mandatoriedade

filiation/type

Removida a opção SEM\_FILIACAO do enum

hasBrazilianNationality

Nullable removido

maritalStatusCode

Alterado exemplo  
Alterada descrição  
Adicionada restrição  
Alterada mandatoriedade

maritalStatusAdditionalInfo

Alterada descrição  
Alterado exemplo

nationality

Alterada mandatoriedade  
Adicionado minItems

nationality/documents/additionalInfo

Adicionado campo

nationality/documents/expirationDate

Alterada mandatoriedade  
Alterado o pattern

nationality/documents/issueDate

Alterada mandatoriedade  
Alterado o pattern

nationality/documents/typeAdditionalInfo

Removido campo

nationality/otherNationalitiesInfo

Adicionado pattern  
Alterada descrição

otherDocuments

Alterada mandatoriedade

otherDocuments/type

Alterada mandatoriedade

otherDocuments/typeAdditionalInfo

Alterado exemplo  
Alterada mandatoriedade

otherDocuments/checkDigit

Alterada mandatoriedade

otherDocuments/country

Alterado pattern

otherDocuments/expirationDate

Alterada mandatoriedade  
Alterado pattern

otherNationalitiesInfo

Alterado para lista

sex

Removido do enum a opção "NAO\_DISPONIVEL"  
Alterada mandatoriedade

socialName

Alterada mandatoriedade

updateDateTime

Alterada descrição

personalId

Alterado pattern  
Adicionado minLength

Header

Criado campo pagination-key

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /personal/qualifications

**Campo**

**O que foi feito?**

companyCnpj

Alterado pattern

informedIncome

Alterada mandatoriedade

informedIncome/amount

Convertido em objeto com os atributos amount e currency  
Alterada descrição

informedIncome/amount/amount

Adicionado campo e suas propriedades

informedIncome/amount/currency

Adicionado campo e suas propriedades

informedIncome/currency

Removido deste nível

informedIncome/date

Alterado pattern

informedIncome/frequency

Removida opção SEM\_FREQUENCIA\_RENDA\_INFORMADA do enum

informedPatrimony

Alterada mandatoriedade

informedPatrimony/currency

Removido deste nível

informedPatrimony/amount

Convertido em objeto com os atributos amount e currency  
Alterada descrição

informedPatrimony/amount/amount

Adicionado campo e suas propriedades

informedPatrimony/amount/currency

Adicionado campo e suas propriedades

informedPatrimony/year

Removido nullable  
Removido maxLength  
Alterada descrição

occupationCode

Alterada mandatoriedade

occupationDescription

Alterada mandatoriedade  
Alterada descrição

updateDateTime

Alterada descrição

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

GET /personal/financial-relations

Campo

O que foi feito?

accounts

Alterado minItems

accounts/branchCode

Alterada mandatoriedade  
Alterado pattern  
Alterada descrição

accounts/compeCode

Alterado pattern

accounts/number

Alterado pattern

accounts/type

Removido a opção do enum "SEM\_TIPO\_CONTA  
Alterada descrição

accounts/subtype

Removido a opcão do enum "SEM\_SUB\_TIPO\_CONTA”  
Alterada descrição

procurators

Adicionado minItems  
Adicionada restrição

procurators/cpfNumber

Alterado pattern

procurators/socialName

Alterada mandatoriedade  
Atualizada descrição

procurators/type

Removido maxLength  
Removido opção NAO\_POSSUI do enum

productsServicesType

Removido maxLength

productsServicesTypeAdditionalInfo

Alterado o pattern

updateDateTime

Alterada descrição

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

GET /business/identifications

**Campo**

**O que foi feito?**

data

Adicionado minItems

brandName

Alterada descrição

businessId

Alterado pattern  
Adicionado minLength

cnpjNumber

Pattern alterado

companyCnpjNumber

Renomeado para companiesCnpj

companiesCnpj

Alterado pattern  
Adicionado minItems  
Alterada mandatoriedade

contacts/emails

Adicionado minItems

contacts/phones

Adicionado minItems

contacts/phones/areaCode

Removido maxLength  
Removido enum

contacts/phones/countryCallingCode

Alterado pattern  
Alterada mandatoriedade  
Adicionada descrição

contacts/phones/number

Alterado pattern

contacts/phones/phoneExtension

Alterada mandatoriedade  
Alterado pattern

contacts/phones/type

Removido maxLength

contacts/postalAddresses/address

Alterada mandatoriedade  
Alterado pattern  
Adicionado minLength  
Atualizada descrição

contacts/postalAddresses/countryCode

Alterada mandatoriedade  
Adicionado pattern  
Atualizada descrição

contacts/postalAddresses/countrySubDivision

Alterada mandatoriedade  
Alterado pattern  
Removido NA do enum

contacts/postalAddresses/districtName

Alterada mandatoriedade  
Alterada descrição

contacts/postalAddresses/geographicCoordinates/latitude

Alterada mandatoriedade  
Alterado exemplo  
Alterada descrição

contacts/postalAddresses/geographicCoordinates/longitude

Alterada mandatoriedade  
Alterado exemplo  
Atualizada descrição

contacts/postalAddresses/postCode

Alterada mandatoriedade  
Alterado pattern

contacts/postalAddresses/townName

Alterada descrição  
Adicionado minLength  
Alterado pattern

otherDocuments

Alterado minItems

otherDocuments/country

Alterado pattern  
Alterada descrição

otherDocuments/expirationDate

Alterada mandatoriedade  
Alterado pattern

otherDocuments/type

Alterada mandatoriedade

parties/civilName

Alterada descrição  
Alterada mandatoriedade

parties/companyName

Alterada descrição  
Alterada mandatoriedade

parties/documentCountry

Alterada descrição  
Alterado pattern  
Alterada mandatoriedade

parties/documentExpirationDate

Alterada mandatoriedade  
Alterado pattern

parties/shareholding

Alterada mandatoriedade  
Adicionado o format double  
Alterado exemplo  
Alterado maxLength  
Alterado minLength  
Alterado pattern  
Alterada descrição

parties/socialName

Alterada mandatoriedade  
Alterada descrição

parties/startDate

Alterada mandatoriedade

parties/type

Removido maxLength

tradeName

Alterada mandatoriedade

updateDateTime

Alterada descrição

Header

Criado campo pagination-key

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

Response code

Alterado response Default

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529

GET /business/qualifications

**Campo**

**O que foi feito?**

economicActivities

Alterada mandatoriedade  
Adicionado minItems

economicActivities/code

Alterado pattern  
Adicionado minLength  
Alterado o type  
Alterado exemplo

economicActivities/isMain

Alterada descrição

informedPatrimony

Alterada mandatoriedade

informedPatrimony/amount

Convertido para objeto com os atributos amount e currency

informedPatrimony/currency

Removido deste nível

informedPatrimony/amount/amount

Adicionado campo e suas propriedades

informedPatrimony/amount/currency

Adicionado campo e suas propriedades

informedPatrimony/date

Alterado pattern

informedRevenue

Alterada mandatoriedade

informedRevenue/amount

Convertido para objeto com os atributos amount e currency

informedRevenue/amount/amount

Adicionado campo e suas propriedades

informedRevenue/amount/currency

Adicionado campo e suas propriedades

informedRevenue/currency

Removido deste nivel

informedRevenue/frequency

Alterada mandatoriedade  
Removida opção SEM\_FREQUENCIA\_FATURAMENTO\_INFORMADO do enum

informedRevenue/frequencyAdditionalInfo

Alterada mandatoriedade

informedRevenue/year

Removido nullable  
Removido maxLength  
Alterada descrição

updateDateTime

Alterada descrição

Header

Criado campo pagination-key

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

GET /business/financial-relations

**Campo**

**O que foi feito?**

accounts

Alterado minItems

accounts/branchCode

Alterada mandatoriedade  
Alterado pattern  
Alterada descrição

accounts/compeCode

Alterado pattern

accounts/number

Alterado pattern

accounts/type

Atualizada a descrição  
Removida opção SEM\_TIPO\_CONTA do enum

procurators

Adicionado minItems

procurators/cnpjCpfNumber

Alterado pattern

procurators/socialName

Alterada descrição  
Alterada mandatoriedade

procurators/type

Removido maxLength  
Removida opção NAO\_POSSUI do enum

productsServicesType

Removido maxLength

Propriedade de extensibilidade

Removida a explicitude do additionalProperties

updateDateTime

Alterada descrição

Response code

Alterado response Default

Response code

Adicionado o status code 422

Response code

Adicionado o status code 423

Response code

Adicionado o status code 529
