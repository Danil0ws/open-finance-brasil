Informe #36 — 11 de agosto de 2021


Conforme o Informe #35 adiantou, foi retirada a obrigatoriedade do campo endToEndId para a data
de 30/08.


Este ajuste foi disponibilizado nesta quarta-feira (11/08), colocando o portal na versão v1.0.0-rc8.3
e a API Fase 3 na versão v1.0.0-rc5.4.


Para mais detalhes, verifique o changelog na Área do Desenvolvedor.


Além disso, é previsto para 12/08, inclusão do campo do CNPJ do iniciador no POST pix/payments,
como obrigatório. Assim que confirmado, um novo informe será publicado com a atualização.


**[ACESSE A API FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


Foi verificado uma inconsistência no Guia Operacional do Diretório Central (Versão 1.1.2 - pág. 53)
quanto no exemplo mostrado para cadastro de _endpoints_ Fase 2.


Nos exemplos, as URI demostradas estão sem a constante ‘open-banking’.


Favor verificar os cadastros para que contemplem a URI correta:


**API: consents**


- **Diretório (Family Type):** consents


- **Recursos (resources):**


     - https://api.banco.com.br/open-banking/consents/v1/consents


     - https://api.banco.com.br/open-banking/consents/v1/consents/{consentId}


**API: resources**


- **Diretório (Family Type):** resources


- **Recursos (resources):**


     - https://api.banco.com.br/open-banking/resources/v1/resources


**API: Customers**


- **Diretório (Family Type):**


     - customers-bussines


     - customers-personal


- **Recursos (resources):**


     - customers-personal


        - https://api.banco.com.br/open-banking/customers/v1/personal/identifications


        - https://api.banco.com.br/open-banking/customers/v1/personal/qualifications


        - https://api.banco.com.br/open-banking/customers/v1/personal/financial-relations


     - customers-business


        - https://api.banco.com.br/open-banking/customers/v1/business/identifications


        - https://api.banco.com.br/open-banking/customers/v1/business/qualifications


        - https://api.banco.com.br/open-banking/customers/v1/business/financial-relations


**[ACESSE O GUIA DO DIRETÓRIO](https://openbanking-brasil.github.io/areadesenvolvedor/documents/OpenBanking-Guia_Operacao_Diretorio_Central.pdf)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


