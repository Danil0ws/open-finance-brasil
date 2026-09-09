Informe #62 — 28 de setembro de 2021


Neste terça-feira (28/set), foi disponibilizado o plano de teste FAPI para _relying parties_ do Motor de
Conformidade da OpenID Foundation (OIDF). O objetivo da ferramenta é permitir o teste das receptoras de dados e iniciadoras de transação de pagamento.


Adicionalmente, informamos que o início do envio de pedidos de certificação RP está previsto para
ocorrer em 04/out e que enviaremos um novo comunicado confirmando a abertura.


Relembramos a todos que a execução dos testes é recomendada e que as iniciadoras de transação de pagamento (Fase 3) deverão obter suas certificações de segurança _relying parties_ .


Caso a instituição encontre problemas nos testes, pedimos que abra um chamado no GitLab.



**[PLATAFORMA DA OIDF](https://www.certification.openid.net/login.html)**



**[INSTRUÇÕES PARA TESTES](https://openid.net/fapi-rp-conformance-testing-certification-submission-overview-for-open-banking-brazil/)** **[CHAMADOS VIA GITLAB](https://gitlab.com/openid/conformance-suite/-/issues/new)**



O GT UX disponibilizou, no dia 28/set, uma nova versão do Guia de Experiência (versão
v3.04.03). Nesta versão estão contemplados os seguintes ajustes:


- Inclusão dos Requisitos e Recomendações para Iniciação de Pagamentos - Agendamento
único;


- Inclusão de orientações e telas ilustrativas sobre as modalidades de Pix no Open Banking: Pix inserção manual (dados da conta), chave Pix ou QR Code;


- Inclusão da Tabela de Dados de Iniciação de Pagamento: informações que devem aparecer
para o usuário na iniciadora e na detentora;


Algumas outras melhorias foram realizadas no Guia de Experiência, mas não alteram as recomendações e requisitos anteriores, buscam apenas garantir clareza para os desenvolvedores na implementação das jornadas do Open Banking.


**[ACESSE O GUIA DE EXPERIÊNCIA](https://openbanking-brasil.github.io/areadesenvolvedor/#guia-de-experiencia-de-compartilhamento-de-dados-e-iniciacao-de-pagamento)**


Informamos que foram identificados casos de instituições que não estão aderentes ao Guia Operacional do Diretório para publicação das APIs Fase 2, dificultando o consumo automático de APIs
por parte das receptoras.


Exemplo ilustrativo de cadastro distintos:


- Instituição A) /consents/v1/consents/{consentId}


- Instituição B) /consents/v1/consents


Dessa forma, solicitamos às instituições que verifiquem suas APIs cadastradas no Diretório, adequando-as ao padrão estabelecido no Guia Operacional do Diretório o mais breve possível.


**[ACESSE O GUIA DO DIRETÓRIO](https://openbanking-brasil.github.io/areadesenvolvedor/documents/OpenBanking-Guia_Operacao_Diretorio_Central.pdf)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


