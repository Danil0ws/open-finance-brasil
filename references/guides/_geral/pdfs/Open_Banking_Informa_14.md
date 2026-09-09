Informe #14 — 02 de julho de 2021


Alteração da versão das APIs da fase 2 para 1.0.0 conforme necessidade apresentada para a certificação de conformidade. APIs de Consents, Resources e Customers serão alteradas até o final do
dia de hoje (02/07) e APIs restantes serão alteradas ao longo da próxima semana. Os seguintes
pontos foram ajustados nas APIs Fase 2:


- Correção da expressão regular em diversos campos das APIs Consents, Resources e Customers. Para adiantar o desenvolvimento das instituições, também disponibilizamos uma prévia
[das modificações a serem realizadas. Acesse aqui](https://github.com/OpenBanking-Brasil/conformance/blob/main/documents/HML-AJUSTES-APIs-e-Portal-Fase-2-T0.xlsx)


- Esclarecimento adicional sobre os campos transactionFromDateTime e transactionToDateTi[me da API Consents na seção de Problemas conhecidos da especificação, Fase 2](https://openbanking-brasil.github.io/areadesenvolvedor/#especificacoes-da-fase-2-do-open-banking-brasil)


- Campo expirationDateTime da API Consents passa a ser obrigatório, dado que é o limitador
do consentimento


Estes ajustes serão disponibilizados nesta sexta-feira (02/07), colocando o portal na versão v1.0.0rc7.2 e todas as APIs da fase 2 na versão v1.0.0. Para maiores detalhes, verifique o changelog na
Área do Desenvolvedor.


**[ACESSE AS APIs FASE 2](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-2-apis-do-open-banking-brasil)**


Os seguintes pontos foram ajustados nas APIs Fase 3:


- Correção do campo consentId para compatibilizar com a mesma construção da Fase 2
(pattern e tamanho)


Este ajuste será disponibilizado nesta sexta-feira (02/07), colocando o portal na versão v1.0.0-rc7.2
e a API da fase 3 na versão v1.0.0-rc5.0. Para maiores detalhes, verifique o changelog na Área do
Desenvolvedor.


**[ACESSE AS APIs FASE 3](https://openbanking-brasil.github.io/areadesenvolvedor/#fase-3-apis-do-open-banking-brasil)**


O GT UX elaborou uma nova versão do Guia de Experiência (Versão 3.02.03 - 02/07/2021) para
contemplar os ajustes e melhorias apontadas pelo Bacen, e também pelos participantes e Grupos
Técnicos da Convenção. Confira abaixo as principais alterações:


- Atualização Tabela de Status para o Cliente - Compartilhamento de Dados: remoção do status de consentimento “revoked” com indicação de solução técnica


- Atualização Tabela de Status para o Cliente - Iniciação de Pagamento: manutenção dos status finais para o cliente, porém com maior detalhamento no cruzamento dos status das APIs
“Consentimento” vs “Payments”


- Inclusão de recomendação sobre a Renovação do Consentimento para Compartilhamento de
Dados


- Alteração de nomenclatura na Jornada de Compartilhamento de Dados, de dados
“obrigatórios” para dados “necessários”


O Guia estará disponível para download no Portal até o final do dia de hoje (02/07).


**[ACESSE O GUIA DE EXPERIÊNCIA](https://openbanking-brasil.github.io/areadesenvolvedor/#guia-de-experiencia-de-compartilhamento-de-dados-e-iniciacao-de-pagamento)**


Para cadastrar ou descadastrar um endereço de e-mail para recebimento dos informes com as últimas atualizações do
Open Banking, deve ser enviada requisição para o contato: gt-comunicacao@openbankingbr.org


