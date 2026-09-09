Informe #57 — 17 de setembro de 2021


Estão abertos os envios dos pedidos de certificações funcionais para instituições financeiras da Fase 2 para API Financing do Grupo T2.


Para mais detalhes de como realizar a submissão dos resultados dos testes, pedimos que sejam
seguidas as instruções disponibilizadas no GitLab.


Salientamos que, conforme Instrução Normativa n°133, a certificação é obrigatória para o registro
das APIs no Diretório de Participantes.


Relembramos que os envios dos pedidos de certificação para API Loans foram abertos em 15/09 e
que enviaremos um novo comunicado confirmando a abertura das certificações das demais APIs
Fase 2 do Grupo T2 - Credit card, Discounted credit rights e Unarranged overdraft - no momento
em que houver testes suficientes para validação do motor (retirada do WIP do plano de teste). Portanto, solicitamos às instituições da Fase 2 que continuem executando os testes.


Adicionalmente, informamos que todos os logs são inspecionados manualmente pelo fornecedor
para validação, portanto, execuções dos testes com sucesso não são garantia de certificação.


Caso a instituição encontre problemas nos testes, sugerimos que seja aberto um chamado no service desk.


**[ACESSE O GITLAB](https://gitlab.com/obb1/certification)** **[ACESSE O SERVICE DESK](https://servicedesk.openbankingbrasil.org.br/servicePortal)**


Atendendo demanda do BACEN o Conselho Deliberativo do Open Banking Brasil votou pela obrigatoriedade do atendimento de todos os casos de uso prioritários para a Iniciação de Pagamentos
e Compartilhamento de Dados até o dia 29/10/2021:


- Fluxos Same Device (fazem uso do Hybrid (Redirect) Flow):


     - App-to-app


     - App-to-browser


     - Browser-to-browser


     - Browser-to-app


- Fluxo Cross-device / desacoplado – para IFs app only (possível com Hybrid (Redirect) Flow
com Handoff):


     - Browser-to-app


Todos os casos de uso prioritários acima podem ser implementados através de Hybrid (Redirect)
Flow, inclusive o caso de uso browser-to-app desacoplado através de Handoff.


Para Iniciadoras de Pagamento e Receptoras de Dados o fluxo é transparente, sem a necessidade
de desenvolvimentos adicionais. Para Detentoras de Conta e Transmissoras de Dados app only o
Handoff permite o atendimento do fluxo desacoplado com as especificações atuais.


As especificações técnicas existentes, incluindo as de segurança, do Hybrid (Redirect) Flow são
suficientes para implementação do Handoff. Para maiores detalhes do funcionamento do Handoff,
visite o Guia de Experiência do Usuário.


**[ACESSE O GUIA DE EXPERIÊNCIA](https://openbanking-brasil.github.io/areadesenvolvedor/documents/GuiaDeExperienciaDoUsuarioCompartilhamentoDeDadosEIniciacaoDePagamento_v3.03.02.pdf)** **[ACESSE AS ESPECIFICAÇÕES](https://openbanking-brasil.github.io/specs-seguranca/open-banking-brasil-financial-api-1_ID2-ptbr.html)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


