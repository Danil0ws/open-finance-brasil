Informe #46 — 27 de agosto de 2021


A partir de hoje, dia 27/08, estará aberto o envio do pedido de certificação dos testes de segurança
FAPI Brasil e DCR para instituições Fase 3.


Lembramos que o teste deverá ser realizado na plataforma da OIDF.


**[ACESSE A PLATAFORMA OIDF](https://www.certification.openid.net/login.html)**


Com o objetivo de dar mais clareza aos requisitos de segurança para acesso aos _endpoints_, tanto
de negócio quanto do _authorisation server_, o GT Segurança preparou a tabela abaixo, que explicita

- tipo de certificado de servidor a ser utilizado em cada _endpoint_, bem com a indicação dos _end-_
_points_ cujo acesso deve ser realizado exclusivamente por meio de autenticação mTLS.


Esta tabela será refletida nas especificações de segurança do Open Banking Brasil futuramente.


Com o objetivo de dar publicidade à deliberação realizada pelo Conselho Deliberativo em 31/05,
informamos que a validade do _refresh token_ deve ser igual à validade do consentimento. Este ajuste será explicitado na próxima versão do Perfil de Segurança do Open Banking Brasil.


Informamos uma alteração na documentação do Perfil de Segurança do Open Banking Brasil, no
que diz respeito aos padrões mínimos de nível de autenticação. Foi identificado que as exigências
contidas neste documento não estavam aderentes às exigências contidas na Resolução Conjunta
nº 1 de 2020 (art. 17, caput e art. 17 § 1º Inciso I).


Portanto, a seção 5.2.2.4 do Perfil de Segurança do Open Banking Brasil será atualizada, de forma
a contemplar a seguinte orientação:


_“A seguinte orientação deve ser observada para o mecanismo de autenticação:_


- _De acordo com o Art. 17 da Resolução Conjunta nº 01, as instituições devem adotar procedi-_
_mentos e controles para autenticação de cliente_ _**compatíveis com os aplicáveis ao acesso**_
_**a seus canais de atendimento eletrônicos.**_


- _Em observância à regulação em vigor, sugere-se que:_


      - _**Para a autenticação do usuário em autorizações de acessos às APIs de compar-**_
_**tilhamento de dados (Fase 2),**_ _os Authorization Servers_ _**deveriam**_ _adotar, no míni-_
_mo, método compatível com LoA2; e_


      - _**Para a autenticação do usuário em autorizações de acessos às APIs das fases**_
_**subsequentes,**_ _os Authorization Servers_ _**deveriam**_ _adotar método de autenticação_
_compatível com LoA3 ou superior._


_Em todos os casos, a adoção de mecanismo de autenticação mais rigoroso (LoA3 ou superior) fica_
_a critério da instituição transmissora ou detentora de conta, de acordo com sua avaliação de riscos_
_e de forma compatível com os mecanismos habitualmente utilizados. Portanto, o cliente de API_ _**não**_
_**deve**_ _estabelecer na claim acr qualquer método a ser exigido, mas o método adotado pelo ASPSP_
_deve ser retornado pelo Authorization Server na claim acr conforme estabelecido nesta definição.”_


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


