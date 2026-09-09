Informe #47 — 30 de agosto de 2021


Já está disponível na Área do Desenvolvedor a versão v1.0.3 das APIs Fase 2. Foi ajustado o seguinte ponto da API Accounts:


- Alterado o número mínimo de ocorrência (minItems: 0) exigido para a resposta dos métodos
abaixo, de forma a viabilizar que a instituição compartilhe uma lista vazia caso o cliente não
possua uma conta ou não possua transações no período consultado:


      - GET/accounts/data


      - GET/accounts/{accountId}/transactions/data


Essa versão já será refletida na versão definitiva do motor de conformidade. Informações mais
detalhadas se encontram no changelog na Área do Desenvolvedor.


**[ACESSE AS APIs FASE 2](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-2-apis-do-open-banking-brasil)**


Já está disponível na Área do Desenvolvedor, a versão v1.0.1 da API Fase 3. Foi ajustado o seguinte ponto:


Alterado description, na seção “Assinatura de payloads”, com o seguinte texto:


_No contexto da API Payment Initiation, os `payloads` de mensagem que trafegam tanto por parte_
_da instituição iniciadora de transação de pagamento quanto por parte da instituição detentora de_
_conta devem estar assinados. Para o processo de assinatura destes `payloads` as instituições_
_devem seguir as especificações de segurança publicadas na Área do Desenvolvedor:_


_Certificados exigidos para assinatura de mensagens:_


_[Padrões de certificados digitais Open Banking Brasil](https://openbanking-brasil.github.io/specs-_
_seguranca/open-banking-brasil-certificate-standards-1_ID1.html)_


Informações mais detalhadas se encontram no changelog na Área do Desenvolvedor.


**[ACESSE A API FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


Foram realizados os seguintes ajustes no menu da Área do Desenvolvedor do Portal, visando dar
mais clareza aos usuários:


- Inclusão de quebra de linha e tooltip nos textos do menu;


- Reposicionamento dos itens “"API Admin" e "API Comuns" da sessão Fase 1, para uma nova
seção "Monitoramento APIs v1.0.2"


Essas alterações colocam o Portal na versão v1.0.0-rc8.6.


**[ACESSE A ÁREA DO DESENVOLVEDOR](https://openbanking-brasil.github.io/areadesenvolvedor/)**


Informamos que o início da certificação funcional para APIs do Grupo T1 não ocorrerá hoje (30/08).


Devido a alterações realizadas na API Accounts (conforme este Comunicado #47), o motor de conformidade está recebendo ajustes finais, sendo a nova previsão para abertura do período de certificação terça-feira, dia 31/08.


Lembramos às instituições financeiras que, no dia 17/08, foi disponibilizada uma nova versão da
Seção “Quem participa” do Portal Open Banking. A página contempla diversas informações importantes e reguladas, sendo alimentada diretamente dos dados disponibilizados no Diretório de participantes do Open Banking. Assim, inconsistências no cadastro do Diretório podem ter implicações
diretas na jornada do cliente no compartilhamento de dados, que já está em andamento.


Diante do exposto, solicitamos que as instituições acessem a seção “Quem participa”, revisem suas informações e efetuem as correções necessárias no Diretório até 10/09. Abaixo seguem algumas observações para padronização dos campos:


- Nome: deve refletir a maneira como a IF se apresenta para o cidadão, atentando-se aos caracteres maiúsculos/minúsculos;


- Logo: deve estar no formato .svg e o fundo deve ser visível em qualquer ambiente - importante a leitura das páginas 256 e 257 do Guia de Experiência do Usuário


Ao clicar e ver mais detalhes:


- Descrição: deve conter breve descrição e evitar termos como “API” e/ou “Open Banking” importante leitura da página 49 do Guia de Operação do Diretório


Adicionalmente, informamos que, por enquanto, o campo “tipo de instituição” é apresentado como
“-“ para todas as instituições.


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


