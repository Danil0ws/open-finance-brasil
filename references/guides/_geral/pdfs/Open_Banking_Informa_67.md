Informe #67 — 08 de outubro de 2021


Informamos que foi detectado um novo domínio utilizando a técnica de IMPERSONATING DOMAIN:


- Domínio: open-bankings[.]com


- IP: 104[.]21[.]30[.]161


- Data de criação: 06 Oct 2021, 11:40


Foi identificado que o mesmo se encontra avaliado como Phishing, Malicious Activity.


Recomendamos a todos a realização do bloqueio do domínio em gateways de internet e e-mails.


Informamos a publicação da versão ID2 do documento Dynamic Client Registration (DCR), gerada
a partir de um profundo detalhamento dos mecanismos de controle de acesso aos serviços DCR/
DCM com base nas RFCs 7591 e 7592. Além disso, alguns trechos da documentação foram reescritos de forma a aumentar a clareza do documento.


Foram contempladas as seguintes alterações no documento:


 - Seção 5 – Esclarecimento adicional sobre o payload do registro de clientes


 - Seção 6.1 – Esclarecimento adicional sobre a necessidade do authorisation server suportar
OpenID Connect Discovery / FAPI


 - Seção 7.1 – Adequações diversas referente às obrigações e opcionalidades do authorisation
server, para refletir as exigências das RFCs 7591 e 7592


 - Seção 7.2.1 – Retirada de texto apresentado em local inadequado


 - Seção 8 – Orientação adicional sobre a validação do software statement pelo authorisation
server


 - Seção 9.1 – Informação adicional referenciando o Swagger DCR, também construído pelo GT
Segurança


 - Seção 9.2 – Descrição adicional sobre as chaves públicas do Diretório de Participantes e suas utilidades


 - Seção 9.3 (9.3.1 e 9.3.2) – Informação adicional sobre os mecanismos de autenticação e autorização dos serviços de DCR e DCM, detalhada com base no detalhamento das orientações provenientes das RFCs 7591 e 7592


Esta versão ID2 do documento pode ser acessada pelo link abaixo (versão em português), no entanto, o link disponível no Portal ainda não está atualizado. Esta atualização está prevista para
acontecer nos próximos dias, assim como a publicação da versão em inglês do documento.


Adicionalmente, informamos que este trabalho de revisão permitiu que fossem identificados novos
testes de segurança a serem implementados. A OpenID Foundation já está trabalhando para desenvolver os novos testes em conformidade com essa nova versão da documentação, o que acarretará a necessidade de recertificação das instituições a partir de 15 de outubro.


**Destacamos, portanto, a necessidade de todas as instituições verificarem desde já a aderên-**
**cia de suas implementações com esta nova versão do documento.**


Foram identificados casos de inibição de instituições financeiras transmissoras na etapa de consentimento de instituições receptoras, motivados pela omissão, por parte das receptoras, de algumas marcas de um mesmo conglomerado.


Relembramos a todos que, caso a mesma instituição transmissora tenha cadastrado duas ou mais
marcas diferentes, todas devem ser refletidas na jornada de compartilhamento de dados. Caso
contrário, pode-se gerar frustração ao usuário, que pode não encontrar a marca que possui identificação ou acabar fazendo uma seleção incorreta por proximidade, e consequentemente, não conseguir autenticar-se devidamente.


Assim, solicitamos que as instituições receptoras revisem esta implementação para disponibilizar
ao usuário todas as instituições possíveis para a transmissão de dados.


Uma exceção à regra se dá para o caso em que uma marca está cadastrada duas ou mais vezes
no diretório de participantes com o _mesmo nome_ . Neste caso, deve ser listada apenas uma vez.


Informamos que, assim como na Jornada de Compartilhamento de Dados, na Jornada de Iniciação
de Pagamento, a utilização do Internet Explorer poderá ocasionar interrupção da jornada por problemas técnicos do navegador.


Logo, recomendamos que, ao identificar a utilização do Internet Explorer pelo usuário, seja exibido
um alerta ao cliente para que utilize outro navegador compatível.


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


