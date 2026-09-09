# Changelog - [DA] Canais de Atendimento - v2.0.0-beta.1

Alteração na parte de orientações dentro do swagger

**Campo**

**O que foi alterado?**

description

Alterado - nomenclatura da API

description

description

title

title

GET /banking-agents

**Campo**

**O que foi feito?**

get/responses/200/

example

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

get/responses/200/data/brand/companies/contractors/bankingAgents/services

Removido - maxItens

get/responses/200/data

Adicionado - “participant“

get/responses/200/data/brand/name​​

Alterado - caminho e nome

get/responses/200/data/brand/companies/name​​

Alterado - caminho

get/responses/200/data/brand/companies/cnpjNumber​​

Alterado - caminho

get/responses/200/data/brand/companies/contractors/bankingAgents

Alterado - caminho

get/responses/200/data/brand/companies/contractors

Alterado - caminho

get/responses/200/data/brand/companies/contractors

Alterado - caminho

get/responses/200/data/brand​

Removido

get/responses/200/data/brand/companies​

Removido

get/responses/200/

example

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/countryCode

Alterado - “description“

get/responses/200/data/bankingAgents/items/contractors/items/name

pattern

get/responses/200/data/bankingAgents/items/identification/corporationName

pattern

get/responses/200/data/bankingAgents/items/identification/groupName

pattern

get/responses/200/data/bankingAgents/items/locations/items/availability/exception

pattern

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/additionalInfo

pattern

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/address

pattern

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/country

pattern

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/districtName

pattern

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/townName

pattern

get/responses/200/data/bankingAgents/items/services/items/additionalInfo

pattern

get/responses/200/data/participant/brand

pattern

get/responses/200/data/participant/name

pattern

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses/200/data\[\]/participant/brand​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/name​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/cnpjNumber​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/contractors\[\]/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/identification/corporationName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/identification/groupName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/identification/isUnderestablishment

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/address​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/districtName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/townName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/ibgeCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/countrySubDivision

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/postalCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/country

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/countryCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/availability/exception

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/availability/isPublicAccessAllowed

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/phones\[\]/type

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/phones\[\]/countryCallingCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/phones\[\]/areaCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/phones\[\]/number

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/services\[\]/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/bankingAgents\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/postalCode

Alterado - Pattern

get/responses/200/data\[\]/participant/cnpjNumber

Alterado - Pattern

get/responses/200/data\[\]/bankingAgents\[\]/identification/isUnderestablishment

Alterado - Mandatoridade

get/responses/200/data/bankingAgents\[\]/locations\[\]/postalAddress/ibgeCode​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/postalAddress/country​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/postalAddress/countryCode​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/availability/exception​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/availability/isPublicAccessAllowed​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/phones\[\]/type​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/phones\[\]/countryCallingCode​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/phones\[\]/areaCode​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/locations\[\]/phones\[\]/number​​

Removido - x-regulatory-required

get/responses/200/data/bankingAgents\[\]/contractors\[\]/name​​

Removido - x-regulatory-required

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/countryCode

Adicionado - MinLenght

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/countryCode

Adicionado - MaxLenght

get/responses/200/data\[\]/bankingAgents\[\]/locations\[\]/postalAddress/countryCode

Adicionado - Pattern

get/responses/200/data

Adicionado - Descrição

get/responses/200/data/participant

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/locations\[\]/postalAddress

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/identification

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/identification/corporationName

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/identification/groupName

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/locations\[\]/availability

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/locations\[\]/availability/standards\[\]

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/locations\[\]/availability/exception

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/locations\[\]/availability/isPublicAccessAllowed

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/locations\[\]/phones\[\]

Adicionado - Descrição

get/responses/200/data/bankingAgents\[\]/contractors\[\]/name

Adicionado - Descrição

get/responses/200/Meta

Adicionado - Descrição

get/responses/200/Link

Adicionado - Descrição

get/responses/200/components/schemas/ResponseBankingAgentsList/example

Remover - Exemplo

get/responses/200/data/bankingAgents\[\]/identification/corporationName

Adicionado - Exemplo

get/responses/200/data/bankingAgents\[\]/identification/groupName

Adicionado - Exemplo

get/responses/200/data/bankingAgents\[\]/identification/isUnderestablishment

Adicionado - Exemplo

get/responses/200/data/bankingAgents\[\]/contractors\[\]/name

Adicionado - Exemplo

get/responses/200/links/prev

Adicionado - Exemplo

get/responses/200/links/next

Adicionado - Exemplo

get/responses/200/data/bankingAgents/items/contractors/items/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/contractors/items/cnpjNumber

pattern

get/responses/200/data/bankingAgents/items/contractors/items/name

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/identification/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/identification/cnpjNumber

pattern

get/responses/200/data/bankingAgents/items/identification/corporationName

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/identification/groupName

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/availability/exception

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/phones/items/areaCode

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/phones/items/countryCallingCode

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/phones/items/number

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/additionalInfo

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/address

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/country

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/districtName

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/geographicCoordinates/latitude

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/geographicCoordinates/longitude

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/ibgeCode

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/postCode

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/townName

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/services/items/additionalInfo

Adicionado - "minLength"

get/responses/200/data/participant/brand

Adicionado - "minLength"

get/responses/200/data/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/participant/name

Adicionado - "minLength"

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/200/data/bankingAgents/items/locations/items/postalAddress/additionalInfo

example

get/responses/200/data/bankingAgents/items/services/items/additionalInfo

example

GET /branches

**Campo**

**O que foi feito?**

get/responses/200/data/brand/companies/items/branches/items/postalAddresses/countryCode

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/branches/items/postalAddresses/countryCode

Adicionado - "pattern"

get/responses/200/

example

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

get/responses/200/data/brand/companies/branches/availability/standards

Removido - maxItens

get/responses/200/data/brand/companies/branches/services

Removido - maxItens

get/responses/200/data

Alterado - “type“

get/responses/200/data

Adicionado - “participant“

get/responses/200/data/brand/name​​

Alterado - caminho e nome

get/responses/200/data/brand/companies/name​​

Alterado - caminho

get/responses/200/data/brand/companies/cnpjNumber​​

Alterado - caminho

get/responses/200/data/brand/companies/urlComplementaryList​​​

Alterado - caminho

get/responses/200/data/brand/companies/branches/identification

Alterado - caminho

get/responses/200/data/brand/companies/branches/postalAddresses

Alterado - caminho

get/responses/200/data/brand/companies/branches/availability

Alterado - caminho

get/responses/200/data/brand/companies/branches/phones

Alterado - caminho

get/responses/200/data/brand/companies/branches/services

Alterado - caminho

get/responses/200/data/brand​​

Removido

get/responses/200/data/brand/companies​​

Removido

get/responses/200/data/brand/companies/branches​

Removido

get/responses/200/

example

get/responses/200/data/items/availability/exception

Alterado - “description“

get/responses/200/data/items/availability/exception

pattern

get/responses/200/data/items/identification/checkDigit

pattern

get/responses/200/data/items/identification/name

pattern

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/postalAddresses/additionalInfo

pattern

get/responses/200/data/items/postalAddresses/address

pattern

get/responses/200/data/items/postalAddresses/country

pattern

get/responses/200/data/items/postalAddresses/districtName

pattern

get/responses/200/data/items/postalAddresses/townName

pattern

get/responses/200/data/items/services/items/additionalInfo

pattern

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses/200/data\[\]/identification/type

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/code

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/checkDigit

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/relatedBranch

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/openingDate

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/address

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/districtName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/townName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/ibgeCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/countrySubDivision

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/postalCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/country

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddresses/countryCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/availability/exception

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/availability/isPublicAccessAllowed

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/phones\[\]/type

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/phones\[\]/countryCallingCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/phones\[\]/areaCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/phones\[\]/number

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/brand​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/name​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/cnpjNumber​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/urlComplementaryList​​

Adicionado - "x-regulatory-required"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords

get/responses/200/data/postalAdresses

Alterado - nome do campo

get/responses/200/data\[\]/idenification/code

Alterado - Pattern

get/responses/200/data\[\]/participant/cnpjNumber

Alterado - Pattern

get/responses/200/data\[\]/phones\[\]/type

Alterado - Mandatoriedade

get/responses/200/data\[\]/availability/exception

Alterado - Mandatoriedade

get/responses/200/data/identification/relatedBranch​​

Removido - x-regulatory-required

get/responses/200/data/identification/openingDate​​

Removido - x-regulatory-required

get/responses/200/data/postalAddresses/ibgeCode​​

Removido - x-regulatory-required

get/responses/200/data/postalAddresses/country​​

Removido - x-regulatory-required

get/responses/200/data/postalAddresses/countryCode​​

Removido - x-regulatory-required

get/responses/200/data/availability/exception​​

Removido - x-regulatory-required

get/responses/200/data/availability/isPublicAccessAllowed​​

Removido - x-regulatory-required

get/responses/200/data/phones\[\]/type​​

Removido - x-regulatory-required

get/responses/200/data/phones\[\]/countryCallingCode​​

Removido - x-regulatory-required

get/responses/200/data/phones\[\]/areaCode​​

Removido - x-regulatory-required

get/responses/200/data/phones\[\]/number​​

Removido - x-regulatory-required

get/responses/200/data

Adicionado - minItem

get/responses/200/data

Adicionado - Descrição

get/responses/200/data

Adicionado - Descrição

get/responses/200/data/postalAddress

Adicionado - Descrição

get/responses/200/data/participant/urlComplementaryList

Adicionado - Descrição

get/responses/200/data/identification

Adicionado - Descrição

get/responses/200/data/postalAddress

Adicionado - Descrição

get/responses/200/data/availability

Adicionado - Descrição

get/responses/200/Meta

Adicionado - Descrição

get/responses/200/Link

Adicionado - Descrição

get/responses/200/components/schemas/ResponseBranchesList/example

Remover - Example

get/responses/200/data/participant/brand

Adicionado - Exemplo

get/responses/200/data/participant/name

Adicionado - Exemplo

get/responses/200/data/identification/code

Adicionado - Exemplo

get/responses/200/data/identification/checkDigit

Adicionado - Exemplo

get/responses/200/data/identification/name

Adicionado - Exemplo

get/responses/200/data/identification/relatedBranch

Adicionado - Exemplo

get/responses/200/data/identification/openingDate

Adicionado - Exemplo

get/responses/200/data/availability/exception

Adicionado - Exemplo

get/responses/200/data/availability/isPublicAccessAllowed

Adicionado - Exemplo

get/responses/200/links/prev

Adicionado - Exemplo

get/responses/200/links/next

Adicionado - Exemplo

get/responses/200/data/items/availability/exception

Adicionado - "minLength"

get/responses/200/data/items/availability/standards/items/closingTime

pattern

get/responses/200/data/items/availability/standards/items/openingTime

pattern

get/responses/200/data/items/identification/checkDigit

Adicionado - "minLength"

get/responses/200/data/items/identification/code

Adicionado - "minLength"

get/responses/200/data/items/identification/name

Adicionado - "minLength"

get/responses/200/data/items/identification/openingDate

Adicionado - "minLength"

get/responses/200/data/items/identification/relatedBranch

Adicionado - "minLength"

get/responses/200/data/items/participant/brand

Adicionado - "minLength"

get/responses/200/data/items/participant/name

Adicionado - "minLength"

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "minLength"

get/responses/200/data/items/phones/items/areaCode

Adicionado - "minLength"

get/responses/200/data/items/phones/items/countryCallingCode

Adicionado - "minLength"

get/responses/200/data/items/phones/items/number

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/additionalInfo

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/address

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/country

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/countryCode

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/districtName

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/geographicCoordinates/latitude

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/geographicCoordinates/longitude

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/ibgeCode

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/postCode

pattern

get/responses/200/data/items/postalAddress/postCode

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/townName

Adicionado - "minLength"

get/responses/200/data/items/services/items/additionalInfo

Adicionado - "minLength"

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/additionalInfo

example

get/responses/200/data/items/services/items/additionalInfo

Adicionado - "example"

GET /electronic-channels

**Campo**

**O que foi feito?**

get/responses/200/

example

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

get/responses/200/data/brand/companies/electronicChannels

Removido - maxItens

get/responses/200/data/brand/companies/electronicChannels/services

Removido - maxItens

get/responses/200/data

Alterado - “type“

get/responses/200/data

Adicionado - “participant“

get/responses/200/data/brand/name​​

Alterado - caminho e nome

get/responses/200/data/brand/companies/name​​

Alterado - caminho

get/responses/200/data/brand/companies/cnpjNumber​​

Alterado - caminho

get/responses/200/data/brand/companies/urlComplementaryList​​​

Alterado - caminho

get/responses/200/data/brand/companies/electronicChannels/identification

Alterado - caminho

get/responses/200/data/brand/companies/electronicChannels/services

Alterado - caminho

get/responses/200/data/brand​​

Removido

get/responses/200/data/brand/companies​​

Removido

get/responses/200/data/brand/companies/electronicChannels​

Removido

get/responses/200/

example

get/responses/200/data/items/identification/additionalInfo

pattern

get/responses/200/data/items/identification/urls/items

pattern

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/services/items/additionalInfo

pattern

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses/200/data\[\]/participant/brand​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/name​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/cnpjNumber​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/urlComplementaryList​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/type

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/urls\[\]

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords

get/responses/200/data\[\]/participant/cnpjNumber

Alterado - Pattern

get/responses/200/data

Adicionado - minItem

get/responses/200/data

Adicionado - Descrição

get/responses/200/data

Adicionado - Descrição

get/responses/200/data/participant/urlComplementaryList

Adicionado - Descrição

get/responses/200/data/identification

Adicionado - Descrição

get/responses/200/data/identification/urls\[\]

Adicionado - Descrição

get/responses/200/Meta

Adicionado - Descrição

get/responses/200/Link

Adicionado - Descrição

get/responses/200/components/schemas/ResponseElectronicChannelsList/**example**

Remover - Example

get/responses/200/data/identification/urls\[\]

Adicionado - Exemplo

get/responses/200/links/prev

Adicionado - Exemplo

get/responses/200/links/next

Adicionado - Exemplo

get/responses/200/data/items/identification/additionalInfo

Adicionado - "minLength"

get/responses/200/data/items/identification/urls/items

Adicionado - "minLength"

get/responses/200/data/items/participant/brand

Adicionado - "minLength"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/items/participant/name

Adicionado - "minLength"

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "minLength"

get/responses/200/data/items/services/items/additionalInfo

Adicionado - "minLength"

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/200/data/items/identification/additionalInfo

Adicionado - "example"

get/responses/200/data/items/services/items/additionalInfo

example

GET /phone-channels

**Campo**

**O que foi feito?**

get/responses/200/

example

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

/data/brand/companies/phoneChannels/services

Removido - maxItens

/data

Alterado - “type“

/data

Adicionado - “participant“

/data/brand/name​​

Alterado - caminho e nome

/data/brand/companies/name​​

Alterado - caminho

/data/brand/companies/cnpjNumber​​

Alterado - caminho

/data/brand/companies/urlComplementaryList​​​

Alterado - caminho

/data/brand/companies/phoneChannels/identification

Alterado - caminho

/data/brand/companies/phoneChannels/services

Alterado - caminho

/data/brand​​

Removido

/data/brand/companies​​

Removido

/data/brand/companies/phoneChannels​

Removido

get/responses/200/

example

get/responses/200/data/items/identification/additionalInfo

pattern

get/responses/200/data/items/identification/phones/items/additionalInfo

pattern

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/services/items/additionalInfo

pattern

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses/200/data\[\]/participant/brand​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/name​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/cnpjNumber​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/urlComplementaryList​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/type

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/phones\[\]/countryCallingCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/phones\[\]/areaCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/phones\[\]/number

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords

get/responses/200/data\[\]/participant/cnpjNumber

Alterado - Pattern

get/responses/200/data\[\]/idenification/phones\[\]/areaCode

Alterado - Pattern

get/responses/200/data\[\]/idenification/phones\[\]/number

Alterado - Pattern

get/responses/200/data\[\]/idenification/phones\[\]/countryCallingCode

Alterado - Pattern

get/responses/200/data\[\]/identification/phones\[\]/countryCallingCode

Alterado - Mandatoriedade

get/responses/200/data\[\]/identification/phones\[\]/areaCode

Alterado - Mandatoriedade

get/responses/200/data/identification/phones\[\]/number

Alterado - MaxLength

get/responses/200/data

Adicionado - minItem

get/responses/200/data

Adicionado - Descrição

get/responses/200/data

Adicionado - Descrição

get/responses/200/data/participant/urlComplementaryList

Adicionado - Descrição

get/responses/200/data/identification

Adicionado - Descrição

get/responses/200/data/identification/phones\[\]/additionalInfo

Adicionado - Descrição

get/responses/200/Meta

Adicionado - Descrição

get/responses/200/Link

Adicionado - Descrição

get/responses/200/components/schemas/ResponsePhoneChannelsList/**example**

Remover - Example

get/responses/200/links/prev

Adicionado - Exemplo

get/responses/200/links/next

Adicionado - Exemplo

get/responses/200/data/items/identification/additionalInfo

Adicionado - "minLength"

get/responses/200/data/items/identification/phones/items/additionalInfo

Adicionado - "minLength"

get/responses/200/data/items/identification/phones/items/areaCode

Adicionado - "minLength"

get/responses/200/data/items/identification/phones/items/countryCallingCode

Adicionado - "minLength"

get/responses/200/data/items/identification/phones/items/number

Adicionado - "minLength"

get/responses/200/data/items/participant/brand

Adicionado - "minLength"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/items/participant/name

Adicionado - "minLength"

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "minLength"

get/responses/200/data/items/services/items/additionalInfo

Adicionado - "minLength"

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/200/data/items/identification/additionalInfo

Adicionado - "example"

get/responses/200/data/items/identification/phones/items/additionalInfo

example

get/responses/200/data/items/services/items/additionalInfo

example

GET /shared-automated-teller-machines

**Campo**

**O que foi feito?**

get/responses/200/data/brand/companies/items/sharedAutomatedTellerMachines/items/postalAddress/countryCode

Adicionado - "maxLength"

get/responses/200/data/brand/companies/items/sharedAutomatedTellerMachines/items/postalAddress/countryCode

Adicionado - "pattern"

get/responses/200/

example

get/responses/200/links/first

example

get/responses/200/links/first

Adicionado - "maxLength"

get/responses/200/links/first

Adicionado - "pattern"

get/responses/200/links/last

example

get/responses/200/links/last

Adicionado - "maxLength"

get/responses/200/links/last

Adicionado - "pattern"

get/responses/200/links/next

Adicionado - "maxLength"

get/responses/200/links/next

Adicionado - "pattern"

get/responses/200/links/prev

Adicionado - "maxLength"

get/responses/200/links/prev

Adicionado - "pattern"

get/responses/200/links/self

example

get/responses/200/links/self

Adicionado - "maxLength"

get/responses/200/links/self

Adicionado - "pattern"

/data/brand/companies/sharedAutomatedTellerMachines

Removido - maxItens

/data

Alterado - “type“

/data

Adicionado - “participant“

/data/brand/name​​

Alterado - caminho e nome

/data/brand/companies/name​​

Alterado - caminho

/data/brand/companies/cnpjNumber​​

Alterado - caminho

/data/brand/companies/urlComplementaryList​​​

Alterado - caminho

/data/brand/companies/sharedAutomatedTellerMachines/identification

Alterado - caminho

/data/brand/companies/sharedAutomatedTellerMachines/postalAddresses

Alterado - caminho

/data/brand/companies/sharedAutomatedTellerMachines/availability

Alterado - caminho

/data/brand/companies/sharedAutomatedTellerMachines/services

Alterado - caminho

/data/brand​​

Removido

/data/brand/companies​​

Removido

/data/brand/companies/sharedAutomatedTellerMachines​

Removido

get/responses/200/data/items/postalAddress/countryCode

Alterado - “description“

get/responses/200/data/items/availability/exception

pattern

get/responses/200/data/items/identification/ownerName

pattern

get/responses/200/data/items/participant/brand

pattern

get/responses/200/data/items/participant/name

pattern

get/responses/200/data/items/participant/urlComplementaryList

pattern

get/responses/200/data/items/postalAddress/additionalInfo

pattern

get/responses/200/data/items/postalAddress/address

pattern

get/responses/200/data/items/postalAddress/country

pattern

get/responses/200/data/items/postalAddress/districtName

pattern

get/responses/200/data/items/postalAddress/townName

pattern

get/responses/200/data/items/services/items/additionalInfo

pattern

get/parameters/page

Adicionado - "format"

get/parameters/page

Adicionado - "maximum"

get/parameters/page-size

Adicionado - "format"

get/parameters/page-size

Adicionado - "maximum"

get/responses

Adicionado - "400"

get/responses

Adicionado - "404"

get/responses

Adicionado - "405"

get/responses

Adicionado - "429"

get/responses

Adicionado - "500"

get/responses/200/data\[\]/participant/brand​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/name​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/cnpjNumber​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/participant/urlComplementaryList​​

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/identification/ownerName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/address

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/districtName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/townName

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/ibgeCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/countrySubDivision

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/postalCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/country

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/postalAddress/countryCode

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/availability/exception

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/availability/isPublicAccessAllowed

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/name

Adicionado - "x-regulatory-required"

get/responses/200/data\[\]/services\[\]/code

Adicionado - "x-regulatory-required"

get/responses/400/meta

removido - totalPages e totalRecords

get/responses/404/meta

removido - totalPages e totalRecords

get/responses/405/meta

removido - totalPages e totalRecords

get/responses/429/meta

removido - totalPages e totalRecords

get/responses/500/meta

removido - totalPages e totalRecords

get/responses/504/meta

removido - totalPages e totalRecords

get/responses/529/meta

removido - totalPages e totalRecords

get/responses/default/meta

removido - totalPages e totalRecords

get/responses/200/data\[\]/participant/cnpjNumber

Alterado - Pattern

get/responses/200/data\[\]/locations\[\]/postalAddress/postalCode

Alterado - Pattern

get/responses/200/data/participant/brand​​

Removido - x-regulatory-required

get/responses/200/data/participant/name​​

Removido - x-regulatory-required

get/responses/200/data/participant/cnpjNumber​​

Removido - x-regulatory-required

get/responses/200/data/participant/urlComplementaryList​​

Removido - x-regulatory-required

get/responses/200/data/identification/ownerName

Removido - x-regulatory-required

get/responses/200/data/postalAddress/address​​

Removido - x-regulatory-required

get/responses/200/data/postalAddress/districtName​​

Removido - x-regulatory-required

get/responses/200/data/postalAddress/townName

Removido - x-regulatory-required

get/responses/200/data/postalAddress/ibgeCode​​

Removido - x-regulatory-required

get/responses/200/data/postalAddress/countrySubDivision​​

Removido - x-regulatory-required

get/responses/200/data/postalAddress/postCode​​

Removido - x-regulatory-required

get/responses/200/data/postalAddress/country​​

Removido - x-regulatory-required

get/responses/200/data/postalAddress/countryCode​​

Removido - x-regulatory-required

get/responses/200/data/availability/exception​​

Removido - x-regulatory-required

get/responses/200/data/availability/isPublicAccessAllowed​​

Removido - x-regulatory-required

get/responses/200/data/services\[\]/name​​

Removido - x-regulatory-required

get/responses/200/data/services\[\]/code​​

Removido - x-regulatory-required

get/responses/200/data

Adicionado - minItem

get/responses/200/data

Adicionado - Descrição

get/responses/200/data

Adicionado - Descrição

get/responses/200/data/postalAddress

Adicionado - Descrição

get/responses/200/data/identification

Adicionado - Descrição

get/responses/200/data/postalAddress

Adicionado - Descrição

get/responses/200/data/availability

Adicionado - Descrição

get/responses/200/data/availability/standards\[\]

Adicionado - Descrição

get/responses/200/data/availability/exception

Adicionado - Descrição

get/responses/200/data/availability/isPublicAccessAllowed

Adicionado - Descrição

get/responses/200/data/services\[\]

Adicionado - Descrição

get/responses/200/Meta

Adicionado - Descrição

get/responses/200/Link

Adicionado - Descrição

get/responses/200/links/prev

Adicionado - Exemplo

get/responses/200/links/next

Adicionado - Exemplo

get/responses/200/data/items/availability/exception

Adicionado - "minLength"

get/responses/200/data/items/availability/standards/items/closingTime

pattern

get/responses/200/data/items/availability/standards/items/openingTime

pattern

get/responses/200/data/items/identification/ownerName

Adicionado - "minLength"

get/responses/200/data/items/participant/brand

Adicionado - "minLength"

get/responses/200/data/items/participant/cnpjNumber

Adicionado - "minLength"

get/responses/200/data/items/participant/name

Adicionado - "minLength"

get/responses/200/data/items/participant/urlComplementaryList

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/additionalInfo

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/address

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/country

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/countryCode

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/districtName

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/geographicCoordinates/latitude

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/geographicCoordinates/longitude

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/ibgeCode

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/postCode

pattern

get/responses/200/data/items/postalAddress/postCode

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/townName

Adicionado - "minLength"

get/responses/200/data/items/services/items/additionalInfo

Adicionado - "minLength"

get/responses/200/links/first

Adicionado - "minLength"

get/responses/200/links/last

Adicionado - "minLength"

get/responses/200/links/next

Adicionado - "minLength"

get/responses/200/links/prev

Adicionado - "minLength"

get/responses/200/links/self

Adicionado - "minLength"

get/responses/200/data/items/postalAddress/additionalInfo

example

get/responses/200/data/items/services/items/additionalInfo

example
