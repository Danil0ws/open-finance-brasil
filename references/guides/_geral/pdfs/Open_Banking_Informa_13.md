Informe #13 — 30 de junho de 2021


Os seguintes pontos foram ajustados nas APIs Fase 3:


- Retirada do campo endToEndId no payload de envio do PIX e retorno à descrição anterior,
onde "xxxxxxxx" é a identificação do agente que gerou o <endToEndId>, podendo ser o ISPB
do participante direto ou o ISPB do participante indireto.


- Adição do campo localInstrument (formaDeIniciacao) para explicitar o tipo de PIX iniciado
(manual, chave ou QR Code) e evitar erros de preenchimento na PACS.008, conforme sugestão do Banco Central.


- Ajuste no texto de restrição do Proxy (chave PIX) para refletir o condicional - agora associado
ao preenchimento do campo localInstrument.


- Adição de descrição textual no diagrama para reforçar a responsabilidade da Detentora na
validação de iniciação do PIX.


Estes ajustes serão disponibilizados nesta quarta-feira (30/06), colocando a API Fase 3 na versão
1.0.0-rc4.0 e o portal na versão 7.1.


Assim que confirmado se esta publicação atende os requisitos da Fase 3, a API Fase 3 passará
para a versão oficial 1.0.0.


Para maiores detalhes, verifique o change log da versão.


**[ACESSE AS APIs FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


Foi disponibilizada uma nova versão do Guia Operacional do Diretório Central. As principais alterações presentes na nova versão são listadas abaixo:


- Adição: foi adicionado um novo detalhamento apresentando os “Tipos de Usuários”;


- Adição: foi adicionado no rodapé do slide “Cadastramento de Conglomerado” uma nota que
caso a organização faça parte de um conglomerado é fundamental referenciar as organizações filhas com a organização mãe;


- Adição: foi adicionada uma nova seção “Cadastrando Contatos de Notificação”;


- Adição: foi adicionada uma nova seção “Cadastrando reivindicações de domínio de autoridade”;


- Adição: foi adicionada uma nova seção “Cadastrando reivindicações de autoridade”;


- Adição: foi adicionada uma nova seção “Criando uma nova reivindicação de autoridade de
software”;


- Alteração: a seção “Criando uma solicitação de Assinatura de Certificado (CSR) em Sandbox”
foi ajustada para “Criando certificados de transporte e assinatura em Sandbox”;


- Adição: foi adicionado a seção “Carregando certificados emitidos por autoridade de certificação em Produção”;


- Adição: foi adicionado a seção “Modelo de Segurança Poderes dos Usuários no Diretório”;


- Alteração: campo " Description " no cadastro do Authorisation Server.


**[ACESSE O GUIA DO DIRETÓRIO](https://openbanking-brasil.github.io/areadesenvolvedor/documents/OpenBankingGuiaOperacaoDiretorioCentral.pdf)** **[ACESSE AS DIRETRIZES DO DIRETÓRIO](https://openbanking-brasil.github.io/areadesenvolvedor/#diretrizes-tecnicas-do-diretorio)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


