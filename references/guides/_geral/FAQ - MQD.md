# FAQ - MQD

**O que significa a sigla M.Q.D.?**

M.Q.D. é a sigla para Motor de Qualidade de Dados, ferramenta de código aberto que avalia a qualidade dos dados compartilhados entre os participantes do Open Finance Brasil, assegurando a integridade das informações. O MQD valida respostas de APIs contra JSON Schemas oficiais e gera relatórios que alimentam o cálculo mensal do IQD (Índice de Qualidade dos Dados).

* * *

**Quais grupos de APIs são validados pelo MQD?**

O MQD valida dois grupos de APIs:

1.  **Dados do Cliente (DC)** — Consentimento, Recursos, Dados Cadastrais, Contas, Cartão de Crédito, Operações de Crédito (Empréstimos, Financiamento, Adiantamento a Depositantes, Direitos Creditórios), Investimentos (Renda Fixa Crédito, Renda Fixa Bancária, Renda Variável, Tesouro Direto, Fundos de Investimento) e Câmbio.
    
2.  **Portabilidade de Crédito (PC)** — Portabilidade de Crédito.
    

A lista completa de endpoints pode ser consultada na página: [https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/619413971/Tabela+de+endpoints+validados+pelo+Motor+de+Qualidade+de+Dados+MQD?atl\_f=PAGETREE](data/references/guides/Tabela.md)

* * *

**O que é o IQD e como o MQD se relaciona com ele?**

O IQD (Índice de Qualidade dos Dados) é a nota mensal que avalia a qualidade dos dados de cada instituição no Open Finance Brasil. O MQD é o sistema que coleta e valida os dados que alimentam o cálculo do IQD. A cada transação validada pelo MQD Client, os resultados são enviados ao servidor central, que os processa semanalmente (tickets de qualidade) e mensalmente (cálculo do IQD no dia 15). Para detalhes sobre as fórmulas do IQD, consulte a página Índice de Qualidade dos Dados (IQD) .

* * *

**Como funciona a convivência de versões no MQD?**

O MQD suporta múltiplas versões de uma mesma API simultaneamente, durante períodos de convivência. Para especificar qual versão deve ser validada, inclua o header `versionHeader` na requisição ao MQD com o valor da versão desejada (ex: `2.4.0`). Caso o header não seja informado, a validação será feita automaticamente contra a versão mais recente configurada no sistema.

* * *

**Temos a necessidade de teste funcional ou certificação específica dos participantes para o MQD?**

É disponibilizado um ambiente Sandbox seguro para que as instituições realizem testes funcionais da aplicação antes de entrar em produção. A instituição pode configurar a variável de ambiente `ENVIRONMENT=SANDBOX` para utilizar este ambiente.

* * *

**Quais são os padrões de certificado de segurança que precisam ser adotados para se instalar o MQD?**

O MQD utiliza as práticas de confiabilidade e segurança do ecossistema de finanças abertas, incluindo:

-   Certificados ICP-Brasil para conexão mTLS com o servidor central
    
-   Fluxo de segurança "client\_credentials" com token de acesso (OAuth2)
    
-   Proxy NGINX para terminação mTLS
    

* * *

**A instalação do MQD é obrigatória?**

Sim, seguindo o cronograma aprovado pelo GT de Qualidade de Dados. Todas as instituições participantes do Open Finance Brasil devem instalar e manter o MQD operacional.

* * *

**Como validar a data da request?**

O body enviado ao MQD é dinâmico — é o mesmo response obtido da transmissora. Por isso ele não é definido estaticamente no Swagger. O MQD valida o body contra o JSON Schema da API/versão indicada no header `endpointName`.

* * *

**O report enviado para o servidor central deverá conter todos os requests de um x intervalo de tempo, ou caso alguns dados ainda estejam em processamento poderão ser enviados na próxima janela?**

O relatório contém todos os resultados de validação processados até o momento do envio. Caso existam itens ainda em processamento na fila interna, estes serão incluídos no próximo envio. A janela padrão de envio é configurável via variáveis de ambiente (`REPORT_EXECUTION_WINDOW` e `REPORT_EXECUTION_NUMBER`).

* * *

**A Instituição Financeira precisa estar com a organization id registrada em algum lugar pro getJWKToken?**

O cliente precisa de dois IDs:

1.  **ID da própria organização** — configurado como variável de ambiente `SERVER_ORG_ID` na configuração do container
    
2.  **ID da organização contraparte** — enviado como header `serverOrgId` em cada request ao MQD
    

* * *

**Temos cenários com retornos de grandes payloads. O MQD está preparado para lidar com esses retornos grandes?**

Não há limite de tamanho de payload para o MQD, tanto no tamanho individual quanto na quantidade de mensagens. Recomendamos o monitoramento constante do contêiner — dependendo da carga entregue, será necessário aumentar os recursos (RAM e CPU) para processar adequadamente todas as mensagens. O MQD usa uma fila interna para processar as validações de forma assíncrona, retornando 200 imediatamente após o enfileiramento.

* * *

**Onde encontro o changelog de versões do MQD?**

O changelog está disponível no repositório GitHub do projeto: [https://github.com/OpenBanking-Brasil/mqd-client](https://github.com/OpenBanking-Brasil/mqd-client)

As alterações incluem novas APIs suportadas, correções de schemas e melhorias de compatibilidade.

* * *

**Qual é o SLA de disponibilidade do MQD?**

O MQD possui dois níveis de SLA:

-   **MQD Server (lado OFB):** 99,99% de disponibilidade — a infraestrutura central que recebe os relatórios está sempre disponível.
    
-   **MQD Client (lado IF):** 90% de disponibilidade — a instituição deve garantir que o MQD Client esteja operacional no mínimo 90% do tempo. Indisponibilidades abaixo desse patamar podem impactar o Fator de Consistência (FC) no cálculo do IQD, já que a quantidade de reports enviados será inferior à esperada.
    

* * *

**Onde solicito acesso ao repositório do MQD?**

O acesso pode ser solicitado através do Portal de Solicitação de Acessos: [https://openfinancebrasil.atlassian.net/servicedesk/customer/portal/1/group/17](https://openfinancebrasil.atlassian.net/servicedesk/customer/portal/1/group/17)
