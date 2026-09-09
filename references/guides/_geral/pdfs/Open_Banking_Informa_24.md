Informe #24 — 20 de julho de 2021


Já está disponível, na Área do Desenvolvedor, ajustes na versão 1.0.3 das APIs da Fase 2.


Os seguintes pontos da API Customers foram alterados:


- Inclusão no Enum do campo Identificação PN sex de opção ‘NÃO_DISPONIVEL’


- Adição no campo Identificação PN hasBrazilianNationality de nullable: True


Também, foi ajustado o description da API Consents, adicionando o código de erro 422 no método
de geração do consentimento, caso não restem permissões funcionais suportadas pela
transmissora.


Estes ajustes colocam o portal na versão 7.9.


Adicionalmente, salientamos que, no Informe #23, foi apresentado que os campos seriam nullable:
True, no entanto essa orientação foi revista, conforme consta neste Informe.


Para maiores detalhes, verifique o changelog no Área do Desenvolvedor.


**[ACESSE AS APIs FASE 2](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-2-apis-do-open-banking-brasil)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


