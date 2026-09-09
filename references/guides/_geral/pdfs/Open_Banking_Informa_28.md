Informe #28 — 27 de julho de 2021


[Conforme Resolução BCB n° 114 de 14/07/2021 (link), a data de início da Fase 2 do Open Banking](data/references/Resolução_BCB_114.md)
Brasil foi alterada para 13/08.


Em linha com essa mudança, a Estrutura de Governança revisou o calendário de certificações para
compatibilizar com a nova data, considerando os seguintes marcos:


**13/08:** Publicação das APIs de Consentimento, Resources e Dados Cadastrais


**13/09:** Publicação das APIs de Contas


**27/09:** Publicação das APIs de Cartão de Crédito e Operações de Crédito


Os detalhes do início dos testes bem como datas limite para envio dos pedidos de certificação podem ser acessados no link abaixo.


**[ACESSE O CRONOGRAMA](https://openbanking-brasil.github.io/areadesenvolvedor/documents/cronograma_certificacao.pdf)**


No dia 13/07, foi disponibilizada a versão 4.1.19 do motor de conformidade da OIDF que trouxe
duas atualizações importantes nos testes de segurança do perfil brasileiro:


1) Em linha com a versão 1.0.3 das APIs da Fase 2 do Open Banking, atualização dos testes FAPI para que sempre demandem, no consentimento, o agrupamento de dados referente ao endpoint ACCOUNTS BALANCES.


2) Atualização dos testes DCR para que só aceitem certificados do tipo BRCAC e BRSEAL.


As instituições que se certificaram no teste DCR utilizando os certificados do tipo rtransport e
rtssigning devem se atentar para a mudança em caso de uma nova execução dos testes, visto que

- perfil antigo não será mais aceito.


Reforçamos que, por hora, não é necessária uma nova certificação para instituições que já se certificaram utilizando versões anteriores do motor de testes.


**[MAIS DETALHES SOBRE O RELEASE](https://gitlab.com/openid/conformance-suite/-/releases)**


Dando seguimento à agenda de comunicações do Open Banking Brasil junto às instituições
participantes, na próxima terça-feira, dia 03/08, será realizado um workshop sobre a ferramenta de
certificação da OIDF – FAPI Brasil.


O objetivo deste evento é fornecer às instituições da Fase 3 uma demonstração dos testes de
conformidade do perfil FAPI - Brasil e DCR que serão necessários para a emissão do certificado de
conformidade de segurança, incluindo também uma sessão de esclarecimento de dúvidas.


A plataforma da OIDF com a API da Fase 3 em versão beta será disponibilizada no dia 02/08 e
contempla o mesmo perfil de segurança utilizado na Fase 2.


O convite do workshop será enviado a todos os usuários cadastrados no diretório dos participantes
O compartilhamento do convite é livre e recomendado.


Reforçamos que as instituições que já se certificaram para a Fase 2 não precisarão se certificar
para a Fase 3.


**[ACESSE A PLATAFORMA DA OPENID](https://www.certification.openid.net/login.html)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


