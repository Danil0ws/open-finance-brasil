# v.23.00.00 Compartilhamento de Dados PF via hybrid flow com hand-off

# Visão Geral

A **Jornada de Compartilhamento de Dados** na modalidade _**Hybrid flow**_ **com** _**hand-off**_ é usada quando existe mudança de dispositivo (aplicativo móvel ou desktop) nas etapas de **Direcionamento** IR > IT e **Redirecionamento** IT > IR.

Ambas as instituições precisam garantir que as transições sejam seguras, claras e com o mínimo de fricção possível para o usuário.

Os requisitos e recomendações são os mesmos da Jornada de Compartilhamento de Dados via Hybrid Flow, com acréscimo de requisitos e recomendações nas etapas **Direcionamento (Etapa 2)** e **Redirecionamento** (Etapa 5).

* * *

# Etapa 1: Consentimento

Nesta etapa, o usuário inicia o compartilhamento de dados no ambiente da Instituição Receptora (IR), fornecendo as informações mínimas de identificação e compreendendo a finalidade do uso dos dados. O usuário também seleciona a instituição de origem dos dados, define quais categorias e agrupamentos serão compartilhados, ajusta o prazo da autorização e revisa os termos antes de prosseguir com a jornada.

A Instituição Receptora deve conduzir essa etapa de forma clara, transparente e orientada à finalidade informada, garantindo a correta identificação do usuário, a apresentação adequada das opções de compartilhamento e a visibilidade dos próximos passos.

#F4F5F7

## Requisitos - IR

**Cenário: Início do compartilhamento**

`REQ.DC-04000` Coletar e validar as informações mínimas necessárias para identificação do usuário, conforme o tipo de cadastro e o segmento.

`REQ.DC-04100` Se o usuário tiver cadastro prévio na Instituição Receptora de Dados, validar o CPF.

`REQ.DC-04200` Se o usuário tiver cadastro prévio na Instituição Receptora de Dados, validar também o CNPJ nos casos de segmento PJ.

`REQ.DC-04300` Se o usuário não tiver cadastro prévio na Instituição Receptora de Dados, coletar, no mínimo, o CPF nos casos de segmento PF.

`REQ.DC-04400` Se o usuário não tiver cadastro prévio na Instituição Receptora de Dados, coletar o CPF e o CNPJ nos casos de segmento PJ.

`REQ.DC-04500` Se o usuário não tiver cadastro prévio na Instituição Receptora de Dados, coletar outras informações de identificação consideradas necessárias pela Instituição Receptora de Dados para prosseguir com a jornada ou informações exigidas pela regulação vigente.

`REQ.DC-04600` Apresentar ao usuário a finalidade de uso dos dados de forma clara, seja na tela de início da jornada ou na tela de solicitação do consentimento.

`REQ.DC-04700` Disponibilizar ferramenta de busca para seleção da instituição de origem dos dados, com funcionamento baseado em marcas.

`REQ.DC-04800` Permitir que o usuário busque tanto pela marca da instituição quanto por um participante associado, exibindo corretamente a marca correspondente nos resultados.

`REQ.DC-04900` Exigir que a seleção final seja feita pela marca da instituição, e não pelo nome do participante associado.

`REQ.DC-05000` Exibir apenas marcas adequadas ao tipo de público identificado (PF ou PJ).

`REQ.DC-05100` Garantir que cada marca seja exibida uma única vez, mesmo que existam múltiplos registros para ela no Diretório de Participantes.

img 100![image-20260728-125712.png](images/image-20260728-125712.png)

**Cenário: Seleção de dados**

`REQ.DC-05200` Disponibilizar a visualização e a configuração, quando aplicável, dos dados objeto do compartilhamento.

`REQ.DC-05300` Exibir as categorias de dados na tela principal da jornada, ocultando os agrupamentos, mas permitindo que eles permaneçam acessíveis a partir da interação dos usuários.

-   Ex.: menu agrupado ou botão de mais detalhes.
    

`REQ.DC-05400` Discriminar categorias obrigatórias e opcionais para dados ou agrupamentos, observando que a obrigatoriedade só é permitida em casos de relação direta com a finalidade de uso.

`REQ.DC-05500` Especificar o motivo da obrigatoriedade, quando houver dados obrigatórios.

`REQ.DC-05600` Permitir a remoção ou inclusão de categorias e agrupamentos de dados opcionais no consentimento.

`REQ.DC-05700` Em cenários de transações de crédito, investimento e/ou câmbio, informar ao usuário que novas operações ou contratações dessas categorias terão seus dados automaticamente incorporados ao consentimento vigente.

img 200![image-20260825-175728.png](images/image-20260825-175728.png)

**Cenário: Prazo de consentimento**

`REQ.DC-05800` Exibir um campo que indique a duração ou o prazo do compartilhamento de dados.

`REQ.DC-05900` Preencher o campo de prazo por padrão, conforme entender mais adequado ao caso de uso.

`REQ.DC-06000` Disponibilizar ao usuário a possibilidade de alterar o prazo para, no mínimo, uma opção adicional além do prazo padrão.

`REQ.DC-06100` No caso de prazo indeterminado, identificar para o usuário como Indeterminado ou termo similar.

img 300

![image-20260623-014323.png](images/image-20260623-014323.png)

**Cenário: Informações da solicitação**

`REQ.DC-06500` Dar visibilidade sobre as próximas etapas até a conclusão da jornada.

`REQ.DC-06600` Utilizar, ao longo de toda a jornada, os termos definidos nas Tabelas de Dados para as categorias de dados, seus agrupamentos e respectivas descrições.

**Atenção!**

De acordo com a regulação vigente, na jornada de Compartilhamento de Dados, a apresentação de “Termos e Condições” ou recurso similar é **facultativa** para as Instituições Receptoras. No entanto, uma vez apresentados, devem obedecer aos requisitos a seguir.

`REQ.DC-06400` Se apresentar Termos e Condições, não utilizar opt-in.

`REQ.DC-06300` Se apresentar Termos e Condições, informar que, ao continuar, o usuário está concordando com esses termos.

`REQ.DC-06200` Se apresentar Termos e Condições, exibir o conteúdo de forma clara e objetiva.

img 400![image-20260728-130227.png](images/image-20260728-130227.png)

**Nota**

Os requisitos não exigem a apresentação de uma tela específica de revisão antes do direcionamento para a Instituição Transmissora de Dados. Fica a critério da Instituição Receptora de Dados incluir ou não uma tela para uma melhor experiência ou para auxiliar no cumprimento dos requisitos.

#F4F5F7

## Recomendações - IR

**Cenário: Onboarding**

REC.DC-01110

`REC.DC-01110` No início da jornada de compartilhamento de dados, ao menos no primeiro acesso do usuário, exibir onboarding para informar o usuário sobre o compartilhamento de dados.

REC.DC-01120

`REC.DC-01120` No onboarding, informar o usuário sobre a segurança do processo de compartilhamento de dados.

REC.DC-01131

`REC.DC-01131` No onboarding, informar o usuário sobre a seleção da instituição transmissora.

REC.DC-01140

`REC.DC-01140` No onboarding, informar o usuário sobre a possibilidade de escolha dos dados a serem compartilhados.

REC.DC-01150

`REC.DC-01150` No onboarding, informar o usuário sobre a possibilidade de definição do prazo de compartilhamento dos dados.

REC.DC-01161

`REC.DC-01161` No onboarding, informar o usuário sobre a necessidade de confirmação do compartilhamento de dados na instituição transmissora escolhida.

img 500![image-20260728-130833.png](images/image-20260728-130833.png)

**Cenário: Prazo de consentimento**

**Nota**

Caso os dados compartilhados sejam informações pontuais ou de prazo curto (por exemplo: dados para abertura de conta, contratação de empréstimo etc.) ou como um consentimento de compartilhamento pontual, que não necessita de prazo baseado em meses, é indicado que sejam apresentados prazos proporcionais (por exemplo: horas, dias ou semanas)

**Cenário: Informações da solicitação**

REC.DC-01200

-   `REC.DC-01200` Pré-selecionar os agrupamentos de dados correlacionados com a finalidade, permitindo que o usuário retire a seleção dos dados opcionais.
    

REC.DC-01300

-   `REC.DC-01300` Possibilitar marcar ou desmarcar múltiplos agrupamentos em uma só ação.
    

REC.DC-01400

-   `REC.DC-01400` Possibilitar que o usuário visualize, de forma clara e intuitiva, os dados que compõem cada agrupamento.
    

img 600![image-20260623-014941.png](images/image-20260623-014941.png)REC.DC-01500

-   `REC.DC-01500` Nos casos em que o usuário não possua cadastro prévio, além dos campos obrigatórios, solicitar informações adicionais necessárias para o seguimento da jornada.
    

REC.DC-01600

-   `REC.DC-01600` Informar ao usuário os benefícios de compartilhar dados opcionais, quando houver dados opcionais.
    

REC.DC-01700-   `REC.DC-01700` Reunir vários campos em um termo simples.
    
    -   Ex.: resumir a listagem de CEP, endereço, número, complemento, cidade, UF e país como “Endereço completo”.  REC.DC-01800

-   `REC.DC-01800` Simplificar a linguagem dos “Termos para o Usuário” definidos no Glossário de Experiência, evitando repetições.
    

REC.DC-01900

-   `REC.DC-01900` Quando aplicável, informar sobre a gratuidade da operação de forma clara e sem fricções que atrapalhem a jornada.
    

REC.DC-02000

-   `REC.DC-02000` Informar o usuário quando o escopo de dados de um novo consentimento for idêntico a outro já existente, para impedir a duplicação desnecessária e facilitar a gestão.
    

REC.DC-02100

-   `REC.DC-02100` Alertar sobre a possibilidade de falha na jornada em dispositivos com o recurso de ocultação de aplicativos ativado, orientando o usuário a desativar esse recurso se necessário.
    

![image-20260623-015249.png](images/image-20260623-015249.png)

* * *

# Etapa 2: Direcionamento _hybrid flow com hand-off_

Nesta etapa, o usuário é direcionado do ambiente da IR para o ambiente da IT para dar continuidade à jornada de compartilhamento de dados, por meio de um fluxo híbrido com _hand-off_ entre canais digitais (ex. celular e desktop). Durante o direcionamento, o usuário acompanha o processo por telas informativas, sem a necessidade de realizar ações adicionais, tendo visibilidade de que a transição está em andamento e é segura.

As instituições envolvidas devem garantir uma experiência clara, segura e contínua durante o direcionamento, comunicando de forma transparente o andamento da transição e reduzindo fricções entre canais. Também faz parte das atribuições das instituições disponibilizar mecanismos adequados para a continuidade da jornada, como direcionamento para aplicativo ou browser, e assegurar a retomada do fluxo em caso de interrupção, até a confirmação do compartilhamento de dados.

#F4F5F7

## Requisitos - IR

**Cenário: Tela de transição**

`REQ.DC-06800` Durante o direcionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o direcionamento.

`REQ.DC-06900` Na tela direcionamento, indicar que o direcionamento está em andamento.

-   Ex.: Estamos te direcionando para confirmar a operação.
    

`REQ.DC-07000` Na tela direcionamento, indicar que o direcionamento é seguro.

-   Ex.: Direcionamento com a segurança Open Finance.
    

![image-20260623-024627.png](images/image-20260623-024627.png)

#F4F5F7

## Requisitos - IT

**Tela de transição**

`REQ.DC-06840` Após o direcionamento da IR, apresentar ao usuário uma tela com instruções e ferramentas necessárias para continuidade da jornada pelo celular, de forma clara e simples.

![image-20260121-182142.png](images/image-20260121-182142.png)

#F4F5F7

## Recomendações - IR

**Cenário: Tela de transição**

-   `REC.DC-02200` Permitir que, caso a jornada seja interrompida nesta etapa, o usuário consiga retomá-la facilmente através dos canais digitais da instituição.
    
-   `REC.DC-02900` Utilizar o menor número de interações possível para reduzir a fricção na jornada.
    

-   `REC.DC-03000` Ao direcionar para o browser da Instituição Transmissora de Dados, pode-se abrir na aba da Receptora, ou seja, substituir a página da Receptora pela nova página da Transmissora, ou manter a aba da Receptora e abrir o browser da Instituição Transmissora em uma nova aba.
    

-   `REC.DC-03100` Seguir o padrão visual do aplicativo da IT para garantir segurança e familiaridade ao usuário.
    

-   `REC.DC-03200` Caso a IT possua mais de um canal disponível (app ou browser (desktop)_)_, oferecer a opção de acesso que julgar mais apropriada para a experiência do seu usuário.
    

**Nota**

Como não são todas as instituições que têm mais de um canal disponível, essa tela é opcional e deve ser implementada apenas quando aberta em ambiente desktop.

Além disso, essas opções podem estar em uma tela única de redirecionamento, facilitando a navegação do fluxo.

O exemplo abaixo foi desenhado em duas etapas apenas para garantir um melhor entendimento do processo de escolha do canal.

![image-20260623-024814.png](images/image-20260623-024814.png)#F4F5F7

## Recomendações - IT

**Cenário: Tela de transição**

-   `REC.DC-02900` Utilizar o menor número de interações possível para reduzir a fricção na jornada.
    

-   `REC.DC-03000` Ao direcionar para o browser da Instituição Transmissora de Dados, pode-se abrir na aba da Receptora, ou seja, substituir a página da Receptora pela nova página da Transmissora, ou manter a aba da Receptora e abrir o browser da Instituição Transmissora em uma nova aba.
    

-   `REC.DC-03100` Seguir o padrão visual do aplicativo da IT para garantir segurança e familiaridade ao usuário.
    

-   `REC.DC-03200` Caso a IT possua mais de um canal disponível (app ou browser (desktop)_)_, oferecer a opção de acesso que julgar mais apropriada para a experiência do seu usuário.
    

![image-20260623-024814.png](images/image-20260623-024814.png)

**Nota**

Como não são todas as instituições que têm mais de um canal disponível, essa tela é opcional e deve ser implementada apenas quando aberta em ambiente desktop.

Além disso, essas opções podem estar em uma tela única de redirecionamento, facilitando a navegação do fluxo.

O exemplo abaixo foi desenhado em duas etapas apenas para garantir um melhor entendimento do processo de escolha do canal.

-   `REC.DC-03300` Para facilitar o direcionamento do usuário do browser (desktop) para o aplicativo da IT, utilizar mecanismos como QR code dinâmico, código de ativação, entre outros.
    

-   `REC.DC-03400` Utilizar _DeepLink_ nas jornadas iniciadas em dispositivos móveis.
    

-   `REC.DC-03500` Utilizar elementos visuais e textuais que reforcem o direcionamento, como _loaders_, animações, barras de progresso ou indicadores visuais.
    

-   `REC.DC-03600` Alertar sobre a possibilidade de falha na jornada em dispositivos com o recurso de ocultação de aplicativos ativado, orientando o usuário a desativar esse recurso se necessário.
    

**Nota**

A interface é a representação ilustrativa de apenas uma das diversas opções, o QR Code dinâmico. Fica a cargo da instituição definir o melhor mecanismo de escolha.

![image-20260121-182919.png](images/image-20260121-182919.png)

* * *

# Etapa 3: Autenticação

Nesta etapa, o usuário acessa o ambiente da Instituição Transmissora e realiza a autenticação por meio dos canais digitais já utilizados pela instituição.

A Instituição Transmissora deve solicitar a autenticação conforme seus padrões usuais, sem exigir etapas adicionais ou métodos mais rigorosos do que os aplicados em outras operações. Também é sua responsabilidade validar a titularidade do usuário autenticado e, em caso de divergência em relação à solicitação de consentimento, interromper a jornada de forma imediata, apresentar mensagem de erro clara e orientar sobre os procedimentos disponíveis para resolução.

#F4F5F7

## Requisitos - IT

**Cenário: Login**

`REQ.DC-07300` Para o usuário se autenticar, é necessário que ele tenha acesso a um canal digital da Instituição Transmissora de Dados.

`REQ.DC-07400` Solicitar a autenticação do usuário conforme os padrões já definidos pela própria IT para operações fora do Open Finance, em conformidade com a regulação vigente.

`REQ.DC-07500` Não exigir etapas adicionais ou utilizar métodos mais rigorosos de autenticação não contemplados no canal digital a fim de desincentivar a transação, conforme a regulação vigente.

`REQ.DC-07600` Em dispositivo móvel, não exigir navegadores intermediários no direcionamento do usuário que vem do aplicativo da IR.

img 1000![image-20260120-135745.png](images/image-20260120-135745.png)

**Cenário: Validação da titularidade**

`REQ.DC-07700` No ambiente logado, fazer a validação da titularidade do usuário, com objetivo de garantir que a solicitação e a confirmação de compartilhamento estejam sendo realizadas pelo mesmo titular.

`REQ.DC-07800` Se a titularidade validada após a autenticação for diferente daquela associada à solicitação, interromper a jornada imediatamente e não exibir a tela de resumo da confirmação nem os dados da autorização.

`REQ.DC-07900` Se a titularidade validada após a autenticação for diferente daquela associada à solicitação, apresentar uma mensagem de erro clara sobre o motivo da interrupção.

`REQ.DC-08000` Se a titularidade validada após a autenticação for diferente daquela associada à solicitação, informar quais os procedimentos disponíveis para resolução do problema.

img 1100![image-20260623-020631.png](images/image-20260623-020631.png)

* * *

# Etapa 4: Confirmação

Nesta etapa, o usuário confirma, no ambiente da Instituição Transmissora, o compartilhamento dos dados conforme a solicitação realizada anteriormente na Instituição Receptora. Ele revisa as informações do consentimento, verifica os dados que serão compartilhados, a instituição destinatária e o prazo da autorização antes de confirmar ou cancelar a continuidade da jornada.

A Instituição Transmissora deve apresentar apenas os dados e categorias previamente selecionados, garantir transparência e conformidade com o escopo autorizado e conduzir a confirmação com o mínimo de interações necessárias. Também é sua responsabilidade permitir o cancelamento antes da confirmação, indicar a próxima etapa da jornada e assegurar o redirecionamento adequado à Instituição Receptora em caso de interrupção.

#F4F5F7

## Requisitos - IT

**Cenário: Informações de consentimento**

`REQ.DC-08100` Após a autenticação, informar a instituição que receberá os dados.

`REQ.DC-08110` Após a autenticação, informar o prazo ou data final.

`REQ.DC-08120` Após a autenticação, informar os dados que serão compartilhados.

`REQ.DC-08200` Em caso de prazo indeterminado, identificar o prazo como Indeterminado ou termo equivalente, sem exibir data final.

`REQ.DC-08300` Exibir somente as categorias e os agrupamentos de dados selecionados pelo usuário no ambiente da Instituição Receptora de Dados.

img 1200![image-20260623-020952.png](images/image-20260623-020952.png)

**Cenário: Seleção de origem**

**Nota**

Caso o login do usuário na Instituição Transmissora de Dados utilize o número da conta (acesso a uma conta por vez), não é esperado que haja multiplicidade de origem para a categoria Dados da Conta.

`REQ.DC-08400` Em casos de multiplicidade de origem/produto para as categorias de dados, permitir a seleção conforme o escopo de dados disponível no canal digital da Instituição Transmissora de Dados.

`REQ.DC-08500` Em casos de multiplicidade de origem/produto para as categorias de dados, apresentar todas as opções de origem/produto pré-selecionadas, com possibilidade de desmarcação para redução do escopo, mantendo no mínimo uma origem selecionada.

`REQ.DC-08600` Em casos de multiplicidade de origem/produto para as categorias de dados, quando uma mesma marca contemplar diferentes instituições percebidas pelo usuário de forma segregada, deixar claro a qual instituição cada opção de origem pertence.

img 1300![image-20260623-021550.png](images/image-20260623-021550.png)

`REQ.DC-08700` Disponibilizar multiplicidade de origem/produto somente para as seguintes categorias: Dados de contas (contas de depósito à vista, de poupança e de pagamento pré-pagas ou pós-pagas) e Cartões de crédito.

`REQ.DC-08800` Não disponibilizar seleção de origem para as demais categorias de dados, como dados cadastrais, investimentos, operações de crédito e câmbio. Para esses casos, compartilhar todos os dados existentes na Instituição Transmissora de Dados.

`REQ.DC-08900` Compartilhar as sub-modalidades dos produtos contratados ou distribuídos pela Instituição Transmissora de Dados, bem como as operações de câmbio contratadas, canceladas ou liquidadas por essa instituição. O acesso a essas sub-modalidades acontece em seus canais digitais.

`REQ.DC-09000` Em cenários de transações de crédito, investimento e/ou câmbio, informar ao usuário que novas operações ou contratações dessas categorias terão seus dados automaticamente incorporados ao consentimento vigente.

**Nota**

Os dados transacionais, operações de crédito, investimentos e de operações de câmbio serão compartilhados por até 12 meses retroativos, conforme [Resolução Conjunta nº1](data/references/Resolução_Conjunta_1.md).

img 1400![image-20260623-021800.png](images/image-20260623-021800.png)

**Cenário: Detalhes dos dados compartilhados**

`REQ.DC-09100` Não exibir de forma detalhada informações secundárias como o nome dos agrupamentos.

-   Ex.: saldo, limites e extratos.
    

`REQ.DC-09200` Não exibir de forma detalhada informações secundárias como informações da tabela de dados.

-   Ex.: transações de cartões de crédito - informações do cartão, identificação de transação, valor da transação, datas, identificação do estabelecimento.
    

**Nota**

Para apresentar os detalhamentos que a Instituição Transmissora de Dados julgar como necessários, deve-se utilizar recursos de User Experience conforme padrões da instituição, por exemplo: pequenos botões de informação (tooltips) (?) (+), expandir informação ao passar o mouse (mouseover), link do tipo “Mostrar mais” etc.

`REQ.DC-09300` Para situações nas quais o usuário compartilha uma categoria de produtos ou de contratos por meio de seleção única (ex.: operações de crédito, investimento e/ou câmbio), considerar todas as permissões para os produtos da mesma categoria, ainda que não os comercialize no momento da confirmação.

img 1500![image-20260623-021927.png](images/image-20260623-021927.png)

**Cenário: Detalhes para a confirmação**

`REQ.DC-09400` Apresentar ao usuário um indicativo da próxima etapa da jornada.

`REQ.DC-09500` Permitir que o usuário continue a transmissão dos dados com apenas uma única confirmação. Reduzir cliques desnecessários após a autenticação, admitindo apenas cliques adicionais para seleção de origens e digitação de credenciais, quando aplicável.

`REQ.DC-09600` Não apresentar Termos e Condições nesta etapa, mesmo que por meio de link, ainda que não se exija aceite e/ou leitura.

**Nota**

Conforme regulação vigente, etapas adicionais ou utilização de métodos mais rigorosos de autenticação não contempladas atualmente no canal digital da Instituição Transmissora de Dados serão interpretadas como mecanismos que desincentivam o compartilhamento de dados.

img 1600![image-20260623-022142.png](images/image-20260623-022142.png)

`REQ.DC-09700` Possibilitar que o usuário interrompa a jornada antes da confirmação.

`REQ.DC-09800` Garantir que a opção de interrupção da jornada não seja visualmente mais proeminente do que a opção de prosseguir.

`REQ.DC-09900` Quando houver cancelamento da confirmação de compartilhamento, redirecionar o usuário para a Instituição Receptora de Dados, respeitando os requisitos de redirecionamento de retorno (IT para IR).

img 1700![image-20260623-022304.png](images/image-20260623-022304.png)

**Cenário: Consentimento recém confirmado**

`REQ.DC-11400` Incluir no ambiente de gestão do Open Finance nos canais digitais as informações e o status do consentimento recém confirmado.

#F4F5F7

## Recomendações - IT

**Cenário: Detalhes dos dados compartilhados**

REC.DC-02300

-   `REC.DC-02300` Disponibilizar opção (ex. botão, link, etc) para a visualização granular das informações vinculadas a cada modalidade ocultadas por padrão, para os produtos de Crédito, Investimentos e Câmbio.
    
    -   **Crédito -** Ex.: número do contrato e valor.
        
    -   **Investimentos -** Ex.: renda fixa bancária e fundos de investimento.
        
    -   **Câmbio -** Ex.: identificação da operação e data de fechamento do contrato.
        

REC.DC-02400

-   `REC.DC-02400` Quando a IT não possuir algum agrupamento selecionado pelo usuário, apresentar mensagem informativa .
    
    -   Ex. “No momento, não encontramos nenhum produto que atenda aos dados selecionados.”
        

* * *

# Etapa 5: Redirecionamento hybrid flow com hand-off

Etapa 5 Introdução

Nesta etapa, o usuário segue do ambiente da Instituição Transmissora para o ambiente da Instituição Receptora para a efetivação do compartilhamento de dados. O usuário é orientado nesse processo por telas informativas.

A Instituição Transmissora deve comunicar de forma clara o resultado da solicitação e orientar o usuário a retornar ao canal da Instituição Receptora utilizado para a efetivação do compartilhamento.

#F4F5F7

## Requisitos - IT

**Cenário: Tela de transição**

**Aviso**

Na jornada Hybrid Flow com hand-off, não há redirecionamento de retorno para o ambiente desktop da Instituição Receptora de Dados. Nessa situação, a Instituição Transmissora deve observar os requisitos a seguir.

`REQ.DC-10110` Após a etapa de confirmação, informar que a solicitação foi concluída com sucesso ou apresentar o caso de erro pertinente.

`REQ.DC-10120` Após a etapa de confirmação, apresentar informações claras de continuidade, orientando o usuário a retornar ao canal da Receptora utilizado para visualizar o status do processo.

img 1800![image-20251120-165216.png](images/image-20251120-165216.png)#F4F5F7

## Recomendações - IT

**Cenário: Interrupção da jornada**

REC.DC-02500

-   `REC.DC-02500` Quando o fluxo de consentimento for interrompido nesta etapa, permitir o acesso fácil à visualização do status do processo pelos canais digitais da Instituição.
    

**Cenário: Tela de transição**

REC.DC-02600

-   `REC.DC-02600` Utilizar elementos visuais e textuais que reforcem o redirecionamento, como _loaders_, animações, barras de progresso ou indicadores visuais.
    

REC.DC-02700

-   `REC.DC-02700` No browser (desktop), ao identificar que o usuário finalizou a jornada no app da IT (com a confirmação, o cancelamento ou por timeout), exibir a página de redirecionamento para a IR.
    

![image-20260319-171227.png](images/image-20260319-171227.png)

* * *

# Etapa 6: Efetivação

Nesta etapa, o compartilhamento de dados é efetivado e o usuário visualiza, no ambiente da IR, o resultado da solicitação realizada. O usuário recebe a confirmação de sucesso ou insucesso do compartilhamento e pode consultar o status do consentimento, assim como os principais detalhes da autorização concedida.

A IR deve comunicar o resultado da jornada de forma clara e, em caso de sucesso, apresentar um resumo com informações essenciais, como validade do consentimento, finalidade do uso dos dados e escopo compartilhado.

#F4F5F7

## Requisitos - IR

**Cenário: Mensagem de sucesso**

`REQ.DC-10800` Assim que o usuário retornar da IT, apresentar uma tela informando o sucesso ou o insucesso do compartilhamento.

`REQ.DC-10810` Informar, com destaque, o caminho para acessar a área de gestão de compartilhamento de dados da IR.

`REQ.DC-10820` Informar, com destaque, que o compartilhamento de dados pode ser cancelado a qualquer momento tanto na IR quanto na IT.

`REQ.DC-10830` Se a IR oferecer alteração do compartilhamento de dados, informar, com destaque, que o compartilhamento de dados pode ser alterado a qualquer momento.

`REQ.DC-10840` Se a IR oferecer renovação (padrão ou simplificada) do compartilhamento de dados, no caso de vencimento determinado, informar, com destaque, que o compartilhamento de dados pode ser renovado a qualquer momento.

img 2000![image-20260825-143602.png](images/image-20260825-143602.png)

**Cenário: Detalhes do consentimento**

`REQ.DC-10900` Em caso de sucesso, exibir um resumo da solicitação.

-   Ex.: botão “detalhes” ou “veja mais”.
    

`REQ.DC-11000` No resumo da solicitação, apresentar o prazo e a data final. Em caso de prazo indeterminado, identificar como "Indeterminado" ou termo equivalente.

`REQ.DC-11100` No resumo da solicitação, informar o propósito do uso dos dados compartilhados.

`REQ.DC-11200` No resumo da solicitação, apresentar os tipos de dados compartilhados, como dados cadastrais, contas, cartões de crédito, investimentos e operações de crédito.

`REQ.DC-11300` Informar o usuário sobre os impactos quando algum escopo de dados solicitado inicialmente não for compartilhado e essa ausência impedir o cumprimento integral da funcionalidade, da finalidade ou do benefício oferecido pela Instituição Receptora de Dados.

**Nota**

O resumo contém as informações mínimas necessárias. Fica a critério de cada Instituição Receptora de Dados manter apenas o resumo ou substituí-lo por um comprovante mais completo.

img 2100![image-20260623-023828.png](images/image-20260623-023828.png)

**Cenário: Consentimento recém confirmado**

`REQ.DC-11400` Incluir no ambiente de gestão do Open Finance nos canais digitais as informações e o status do consentimento recém confirmado.

#F4F5F7

## Recomendações - IR

**Cenário: Detalhes do consentimento**

REC.DC-02800

-   `REC.DC-02800` No resumo do compartilhamento, exibir o nome da instituição de origem dos dados.
