Informe #50 — 03 de setembro de 2021


Já está disponível na Área do Desenvolvedor a versão v1.0.4 das APIs Fase 2. Os seguintes ajustes foram realizados nas APIs do ciclo T2 – APIs de operações de crédito e API cartão de crédito:


- Correção do MaxLength de diferentes atributos, refletindo o maior ENUM especificado de cada campo;


- Correção do ENUM de subtipos de garantia das APIs de Operações de Crédito, removendo
“FATURA_CARTAO_CREDITO” e mantendo “EQUIPAMENTOS”.


Essa atualização já será refletida na versão definitiva do motor de conformidade.


Para mais detalhes, consultar o changelog na Área do Desenvolvedor.


Essa alteração coloca o Portal na versão v1.0.0-rc8.7.


**[ACESSE AS APIs FASE 2](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-2-apis-do-open-banking-brasil)**


Informamos que foi encontrado um erro na escrita da claim “userinfo” no documento do Guia do
Usuário para Instituições Receptoras de Dados e Iniciadores de Pagamento (TTP/PISP) nos seguintes tópicos:


- Apêndice A.2 - Exemplo de Corpo de Objeto de Solicitação Decodificado;


- Seção 1.4.3 - Exemplo de Request Object JWT assinado.


O valor correto esperado é “userinfo”. No entanto, a claim havia sido escrita erroneamente como
“user_info” nestes tópicos acima.


Os TPPs devem revisar suas implementações para garantir o uso da claim no formato correto.


**[ACESSE O GUIA DO USUÁRIO PARA TTP/PISP](https://openbanking-brasil.github.io/areadesenvolvedor/#guia-do-usuario-instituicao-receptora-ou-iniciadora-de-pagamentos)**


Informamos que será realizada uma correção textual no Portal referente à descrição da claim “iss”,
apresentada na seção “Como assinar o payload”:


Texto atual (versão com erro):

|Nome|Tipo|Obrigatório|Descrição<br>(requisição JWT e resposta JWT): o receptor da mensagem<br>deverá validar se o valor do campo iss coincide com o seu<br>próprio organisationId listado no diretório.|
|---|---|---|---|
|iss|string|true|true|



Texto a ser publicado (versão correta):

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|iss|string|true|(**_requisição JWT_** e**_resposta JWT_**): o receptor da mensagem<br>deverá validar se o valor do campo**iss** coincide com o<br>organisationId**da outra parte** listado no diretório.|



A fim de trazer mais clareza às instituições participantes, informamos que, conforme publicado no
Portal, é mandatório para os participantes do Open Banking Brasil o suporte ao padrão “Open Banking Brasil Financial-grade API Dynamic Client Registration 1.0”, que determina que os participantes devem suportar a RFC 7591 e a RFC 7592.


**Open Banking Brasil Financial-grade API Dynamic Client Registration 1.0:**


https://openbanking-brasil.github.io/areadesenvolvedor/#dynamic-client-registration


**OAuth 2.0 Dynamic Client Registration Protocol:**


https://datatracker.ietf.org/doc/html/rfc7591


**OAuth 2.0 Dynamic Client Registration Management Protocol:**


https://datatracker.ietf.org/doc/html/rfc7592


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


