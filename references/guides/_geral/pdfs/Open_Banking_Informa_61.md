Informe #61 — 24 de setembro de 2021


Foi detectada uma incoerência entre o exemplo na área de desenvolvedor do padrão dos links e o
_swagger_ desta mesma especificação.


Relembramos que o recomendado é que as instituições consultem diretamente o _swagger_ das especificações para parametrizar seus desenvolvimentos.


Adicionalmente, informamos que o motor de conformidade funcional apresenta testes já corrigindo
estes _gaps_ entre especificação, exemplos e _swagger_ .


Dessa forma, as instituições devem seguir o seguinte para ajustar suas especificações, no que tange ao padrão dos links:


- Os campos self, first, last, prev e next não podem ser null. Se não houver o link, o atributo
simplesmente não deve ser enviado;


- Há uma validação em cima da presença dos atributos. Por exemplo, o envio de 'next' quando
se está na última página (self = totalPages) não deve ocorrer e está sendo validado;


- Qualquer link enviado nestes atributos devem estar com o link https, e não http;


- O valor do campo totalPages tem que ser mínimo 1


Para consultar todas validações, acesse o Gitlab do motor.


**[ACESSE O GITLAB](https://gitlab.com/obb1/certification/-/merge_requests/200/diffs#4efda8abb90562b91bd36e4c85a126599c7674a6)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


