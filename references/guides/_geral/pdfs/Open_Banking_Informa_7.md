Informe #7 — 17 de junho de 2021


**Ajustes relativos ao Consentimento**


- Adição dos campos loggedUser e businessEntity no payload


- Adição do campo expirationDateTime no payload do retorno. A definição do tempo de expiração ainda está em aberto, com discussões sendo finalizadas nos GT's


- Ajuste no dicionário para refletir campos com mandatoriedade explícita "Condicional"


- Descrição da consequência de retirada do JWS do header da API


- Adição do header x-fapi-interaction-id no retorno de todos os status no Swagger


- Adição do header Retry-After no retorno do status 429 no Swagger


**Ajustes relativos ao PIX**


- Mudança nos códigos de erro para formato de texto ao invés de número


- Ajuste no dicionário para refletir campos com mandatoriedade explícita "Condicional"


- Adição do campo endToEndId no payload de envio, com mandatoriedade "Obrigatório"


- Alteração do nome do campo "branchCode" para "issuerCode" a fim de refletir a ISO20.022
na tradução do nome "código de agência"


- Adição do header x-fapi-interaction-id no retorno de todos os status no Swagger


- Adição do header Retry-After no retorno do status 429 no Swagger


Essa publicação será disponibilizada nesta quinta-feira, colocando as APIs Fase 3 na versão 1.0.0rc2.0 e o portal na versão 6.9.


**[ACESSE AS APIs FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


Foi realizado um levantamento dos problemas já mapeados da Fase 2 do Open Banking Brasil, os
quais serão tratados e corrigidos futuramente.


Uma lista preliminar destes problemas foi compilada e disponibilizada no Portal do Open Banking
Brasil, contendo também orientações para o tratamento destas correções via comitê de versionamento.


**[ACESSE O DOCUMENTO](https://openbanking-brasil.github.io/areadesenvolvedor/documents/problemas_conhecidos_fase02_v01.pdf)**


Foram publicadas no dia 15/06, na Área do Desenvolvedor, as versões traduzidas para português
dos Guias end-to-end do usuário, um voltado para instituições receptoras de dados e outro para
instituições transmissoras.


Estas documentações visam fornecer às instituições financeiras o passo a passo da implementação das aplicações do Open Banking, e devem sempre ser consultadas através deste canal, na
Área do Desenvolvedor.


**[ACESSE OS GUIAS](https://openbanking-brasil.github.io/areadesenvolvedor/#guia-do-usuario-instituicao-transmissora)**


Dando seguimento à agenda de comunicações do Open Banking Brasil junto às instituições participantes, na próxima terça-feira, dia 22/06, será realizado um workshop sobre a ferramenta de certificação da OIDF – FAPI Brasil.


O objetivo deste evento é fornecer às instituições da Fase 2 uma demonstração dos testes de conformidade do perfil FAPI - Brasil e DCR que serão necessários para a emissão do certificado de
conformidade de segurança, incluindo também uma sessão de esclarecimento de dúvidas.


Relembramos que a plataforma da OIDF em versão beta foi disponibilizada no dia 11/06 e inclui
tanto os testes relativos ao Perfil FAPI, quanto aos testes do DCR.


O Convite do workshop será enviado aos administradores das instituições no diretório de participantes que requisitaram a certificação para a OIDF. O compartilhamento do convite aos responsáveis pela certificação é livre e recomendado.


**[ACESSE A PLATAFORMA DA OPENID](https://www.certification.openid.net/login.html)**


Você está recebendo este informe pois está cadastrado como administrador da sua instituição financeira no Diretório do
OPB. Caso não faça mais parte do Open Banking, por gentileza, atualize os dados no Diretório Financeiro.


