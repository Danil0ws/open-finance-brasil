Informe #4 Extraordinário — 11 de junho de 2021


 - Retorno das APIs Fase 1 para o repositório principal (antes eram mantidas em repositório separado)


 - Consolidação do primeiro lote de ajustes das APIs Fase 1, publicação v1.0.1:


     - API - Discovery - Correção no arquivo OAS no schema "Status": atributo
"unavailableEndpoints"


     - API - Produtos e serviços - Correção no arquivo OAS: versão do artefato de v2 para v1


     - API - Produtos e serviços - Correção no arquivo OAS no schema
"PersonalAccountCompany": atributo "cnpjNumbers"


     - API - Produtos e serviços - Correção no arquivo OAS no schema "FinancingService":
atributo "customers"


     - API - Produtos e serviços - Correção no arquivo OAS no schema
"FinancingInterestRate": atributo "customers"


     - API - Produtos e serviços - Correção no dicionário de cartão de crédito de pessoa natural: campos "minimum/rate" e "maximum/rate"


     - API - Produtos e serviços - Correção no dicionário de cartão de crédito de pessoa natural: campo "rate"


     - Padrões - Códigos de resposta HTTP - Inclusão de nota para código 200


 - Alteração da versão do Portal para v1.0.0-rc6.7. No entanto, esta alteração tem como objetivo
apenas dar visibilidade de que houve ajustes no Portal. As versões de cada Fase são:


     - APIs Fase 3: v1.0.0-rc1.0 (não alterado)


     - APIs Fase 2: v1.0.0-rc6.6 (não alterado)


     - APIs Fase 1: v1.0.1 (alterado na atualização atual)


 - Planejamento da estratégia de versionamento do Portal. Assim que concluído, será comunicado em informe específico


**[ACESSE A ÁREA DO DESENVOLVEDOR](https://openbanking-brasil.github.io/areadesenvolvedor/)**


Para a entrada segura e assertiva no Ecossistema do Open Banking, a Estrutura Inicial disponibilizou hoje, dia 11/06, a versão beta das ferramentas de testes e homologação das APIs desenvolvidas pelas Instituições Participantes da Fase 2 do Open Banking.


Dois motores foram disponibilizados, i) a ferramenta do Open Banking Brasil, desenvolvida pela
Raidiam, que irá testar aspectos funcionais das APIs, ii) e a ferramenta da OpenID Foundation, que
irá testar a conformidade em segurança com o Perfil FAPI Brasil.


Dentro do escopo previsto pelo motor de testes, destacamos, de maneira não exaustiva, as principais validações que estão em curso de desenvolvimento:


- Open Banking Brasil – Funcional (Disponível API accounts)


     - Estrutura das URLs


     - Cabeçalhos


     - Códigos de Resposta


     - Escopos e Permissões


     - Schema / Estrutura da API


- OIDF - Segurança


     - Perfil FAPI BR (Disponível em versão beta)


     - DCR – Dynamic Client Registration (Ainda não disponível)


     - Perfil CIBA BR - Não detalhado nessa versão do Guia (Ainda não disponível)


Vale notar que o principal objetivo desse release Beta é não só adiantar o desenvolvimento das
instituições financeiras, mas também garantir que as ferramentas estão validando as especificações de maneira correta. Dessa forma, é importante a efetiva utilização da ferramenta pelos participantes e comunicação entre as IFs e a estrutura de governança em face de quaisquer problemas
encontrados, através do nosso Service Desk: https://servicedesk.openbankingbrasil.org.br/


Para utilização da ferramenta da OIDF, as instruções podem ser consultadas através do link:


**[ACESSE AS INTRUÇÕES](https://openid.net/certification/fapi_op_testing/)**


Um exemplo da configuração do teste pode ser encontrado em:


**[VEJA EXEMPLO](https://gitlab.com/openid/conformance-suite/-/wikis/Brazil-Example-Configuration)**


Em caso de dúvidas sobre a execução dos testes, pedimos que entrem em contato pelo e-mail
certificate@oidf.org. Para relatar possíveis bugs ou alterações necessárias, pedimos que a instituição abra um novo issue em:


**[ABRA UM NOVO ISSUE](https://gitlab.com/openid/conformance-suite/-/issues/new)**


No dia 22/06 será realizado um Workshop em que haverá demonstração e esclarecimento de dúvidas sobre a ferramenta da OIDF.


Para a ferramenta de testes de conformidade funcional, a plataforma pode ser acessada em:


**[ACESSE A PLATAFORMA](https://web.conformance.directory.openbankingbrasil.org.br/)**


No release de hoje, 11/06, a ferramenta já está configurada com a primeira versão do perfil de segurança FAPI Brasil, disponibilizada pela OIDF. Além disso, está disponível para a data de hoje
apenas o teste relativo a API de contas. Novas APIs serão disponibilizadas ao longo do mês.


Para a execução dos testes funcionais das APIs, sem segurança, é necessário a execução da ferramenta localmente, disponibilizada no endereço https://gitlab.com/obb1/certification. As informações como realizar esse processo podem ser encontradas na documentação de referência, abaixo.


Para acesso à plataforma e criação do plano de testes, é possível seguir o seguinte guia:


**[ACESSE O GUIA](https://openbanking-brasil.github.io/areadesenvolvedor/documents/Guia_OBB.pdf)**


Além disso, também é possível consultar a documentação de referência, ainda em versão draft, por
meio do link:


**[CONSULTE A DOCUMENTAÇÃO](https://gitlab.com/obb1/certification/-/wikis/Introduction)**


Vale notar que a ferramenta do Open Banking Brasil é baseada na ferramenta da OIDF, logo a extensa documentação produzida pela OIDF também se aplica a essa plataforma.


No dia 15/06 será realizado um Workshop que irá demonstrar a ferramenta de conformidade funcional do Open Banking Brasil.


Foram disponibilizadas as datas dos releases das ferramentas de conformidades, workshops e documentações relativas ao processo de certificação das instituições que participarão do go-live para
a Fase 2, no dia 15/07.


**[ACESSE O CRONOGRAMA DE CERTIFICAÇÃO](https://openbanking-brasil.github.io/areadesenvolvedor/documents/Cronograma Sandbox_Vers%C3%A3o - 20210609.pdf)**


Você está recebendo este informe pois está cadastrado como administrador da sua instituição financeira no Diretório do
OPB. Caso não faça mais parte do Open Banking, por gentileza, atualize os dados no Diretório Financeiro.


