Informe #53 — 09 de setembro de 2021


Está disponível na Área do Desenvolvedor a versão v1.0.4 das APIs Fase 2 ciclo T2: APIs de Operações de crédito e Cartão de crédito. Foram ajustados os seguintes pontos:


- APIs Operações de crédito: alteração do atributo minItens para 0 nos campos GET/contracts/
{contractId}/data/contractedFees e GET/contracts{contractId}/data/contractedFinanceCharges


- API Cartão de crédito: alteração do atributo minItens para 0 nos campos GET/credit-cardsaccounts/v1/accounts/data e GET/credit-cards-accounts/v1/accounts/{creditCardAccountId}/
bills/data/payments


Essa versão já será refletida na versão definitiva do motor de conformidade. Informações mais detalhadas se encontram no changelog na Área do Desenvolvedor


**[ACESSE AS APIs FASE 2](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-2-apis-do-open-banking-brasil)**


As seguintes atualizações foram realizadas na planilha de problemas conhecidos Fase 2, localizada na Área do Desenvolvedor. Atualizações contemplam orientações para:


- APIs Operações de crédito, campo GET/contracts/{contractId}/data/interestRates considerar
vazio como a não existência do dado; em caso de juros ser zero, deve ser enviado valor preenchido 0 (zero)


- API Cartão de crédito, campo GET/credit-cards-accounts/v1/accounts/{creditCardAccountId}/
limits/data considerer vazio como a não existência do dado; em caso de limite ser zero, deve
ser enviado valor preenchido 0 (zero) e em caso de limite flexível, informar objeto com flag
TRUE


- Para correspondência de subtipos de garantia das APIs de Operações de Crédito, utilizar
OUTRAS como subtipo nos casos 1301 (Acordos compensação / avais e fianças honrados) e
0822 (seguros assemelhados / Proagro)


Reforçamos a orientação a todos de, em casos de ambiguidade, prevalecer o que consta em
Swagger.


Para maiores detalhes destas atualizações, consultar a planilha de problemas conhecidos Fase 2
no Portal Open Banking.


Essas alterações colocam o Portal na versão v1.0.0-rc8.9


**[ACESSE OS PROBLEMAS CONHECIDOS](https://openbanking-brasil.github.io/areadesenvolvedor/#especificacoes-da-fase-2-do-open-banking-brasil)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


