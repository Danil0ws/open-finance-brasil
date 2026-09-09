# v.23.00.00 Compartilhamento de Dados PJ com múltiplos aprovadores

# Visão Geral

A **Jornada de Compartilhamento de Dados com Múltiplos Aprovadores** é utilizada quando o compartilhamento precisa ser autorizado por outros usuários da mesma conta.

Nessa jornada, o usuário solicitante inicia o compartilhamento na IR, é direcionado para a IT e informado sobre a necessidade de aprovação adicional. Os aprovadores podem autorizar ou rejeitar a solicitação. Após a decisão, o solicitante é informado sobre o resultado.

É fundamental que IR e IT garantam informações claras e precisas a todos os usuários envolvidos na transação.

Os requisitos de recomendações apresentados nesta página são os mesmos da Jornada de Compartilhamento de Dados via Hybrid Flow, com alterações e acréscimos na **Etapa de Confirmação (Etapa 4)** e na **Efetivação (Etapa 6)**.

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

img 200![image-20260825-204506.png](images/image-20260825-204506.png)

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

# Etapa 2: Direcionamento

Etapa 1 Introdução

Nesta etapa, o usuário é direcionado do ambiente da IR para o ambiente da IT a fim de confirmar o compartilhamento dos dados. O usuário acompanha o direcionamento por meio de uma tela informativa, sem a necessidade de realizar ações adicionais, tendo visibilidade de que o processo é seguro e de que a jornada continuará no ambiente da instituição de origem dos dados.

A Instituição Receptora deve informar de forma clara que o direcionamento está em andamento e assegurar que a transição ocorra sem fricções. É recomendável que a IR permita a retomada da jornada em caso de interrupção. Já a Instituição Transmissora deve conduzir o direcionamento para um canal digital seguro, priorizando o uso de aplicativo quando disponível e garantindo uma experiência contínua e confiável.

#F4F5F7

## Requisitos - IR

**Cenário: Tela de transição**

`REQ.DC-06800` Durante o direcionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o direcionamento.

`REQ.DC-06900` Na tela direcionamento, indicar que o direcionamento está em andamento.

-   Ex.: Estamos te direcionando para confirmar a operação.
    

`REQ.DC-07000` Na tela direcionamento, indicar que o direcionamento é seguro.

-   Ex.: Direcionamento com a segurança Open Finance.
    

`REQ.DC-07100` Na tela direcionamento, não exigir qualquer ação adicional do usuário para confirmar o direcionamento, uma vez que a etapa possui caráter exclusivamente informativo.

`REQ.DC-07200` Em dispositivos móveis, direcionar o usuário diretamente para o aplicativo da IT, sem passar por navegadores intermediários.

img 800![image-20260623-015632.png](images/image-20260623-015632.png)#F4F5F7

## Requisitos - IT

**Cenário: Seleção de métodos de direcionamento**

`REQ.DC-06700` Levar o usuário para um canal digital seguro, observando a seguinte ordem de preferência:

1.  Direcionar para o aplicativo da IT (Hybrid Flow).
    
2.  Direcionar para a loja de aplicativos, caso aplicativo da IT não esteja instalado.
    
3.  Direcionar para o ambiente browser da IT (Hybrid Flow) ou para a loja de aplicativo.
    
4.  Direcionar para o aplicativo da IT com Hand-off (Hybrid Flow com Hand-off).
    
5.  Direcionar para o aplicativo da IT (Hybrid Flow com Hand-off) ou para o ambiente em desktop da IT (Hybrid Flow).
    

img 900![image-20251118-131123.png](images/image-20251118-131123.png)#F4F5F7

## Recomendações - IR

**Cenário: Tela de transição**

-   `REC.DC-02200` Permitir que, caso a jornada seja interrompida nesta etapa, o usuário consiga retomá-la facilmente através dos canais digitais da instituição.
    

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

# Etapa 4: Confirmação com múltiplos aprovadores

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

**Cenário: Dinâmica de aprovação adicional, além do solicitante**

`REQ.DC-11500` Seguir os poderes já vigentes para a movimentação de conta nas políticas internas da Instituição Transmissora de Dados.

`REQ.DC-11600` Não constituir alçadas e poderes específicos para fins de compartilhamento de dados.

`REQ.DC-11700` Seguir as mesmas dinâmicas de alçada e fila de aprovação vigentes para movimentações de conta fora do Open Finance de acordo com a configuração de cada usuário dentro da instituição.

`REQ.DC-11800` Estender para o âmbito do Open Finance os mecanismos já disponibilizados nos canais da instituição que permitam a representantes legais devidamente constituídos autorizar ou delegar poderes para outras pessoas.

`REQ.DC-11900` No caso de conta conjunta, desde que haja acesso eletrônico por titulares, permitir a cada titular compartilhar apenas sua própria informação cadastral, sem depender da confirmação de todos os titulares da conta.

`REQ.DC-12000` No caso de conta conjunta, desde que haja acesso eletrônico por titulares, e caso o acesso a informações transacionais da conta dependa da autorização de todos os titulares, exigir a confirmação de todos os titulares da conta para efetivar o compartilhamento de dados.

**Cenário: Confirmação do usuário solicitante**

**Aviso**

A etapa de confirmação do usuário solicitante na Instituição Transmissora de Dados está sujeita a todos os requisitos gerais especificados para a etapa de confirmação e, adicionalmente, aos requisitos abaixo.

`REQ.DC-12100` Especificar a necessidade de uma ou mais aprovações adicionais, de acordo com a política de poderes de cada Instituição.

`REQ.DC-12200` Apresentar instruções claras sobre o caminho dentro da Instituição Transmissora de Dados que o aprovador deve acessar para atuar e efetivar o compartilhamento.

`REQ.DC-12300` Especificar que o prazo máximo para atuação do(s) aprovador(es) é de 15 dias corridos, contados a partir da aprovação do consentimento pelo solicitante.

`REQ.DC-12400` Deixar claro que caso o prazo expire será necessário um novo pedido de compartilhamento.

`REQ.DC-12500` Ao concluir a etapa de confirmação redirecionar o solicitante de volta para a Instituição Receptora de Dados.

![image-20260623-025841.png](images/image-20260623-025841.png)

**Cenário: Confirmação do aprovador**

`REQ.DC-12600` Após a conclusão de todas as aprovações necessárias na Instituição Transmissora de Dados, notificar o solicitante via canal eletrônico padrão da Instituição Transmissora de Dados sobre a atualização de status do consentimento.

`REQ.DC-12700` Solicitar a atuação do aprovador de forma assíncrona após confirmação do usuário solicitante.

`REQ.DC-12800` Notificar o(s) aprovador(es) via canal eletrônico padrão da Instituição Transmissora de Dados sobre a ação necessária.

-   Ex.: SMS, push etc.
    

`REQ.DC-12900` Na tela de confirmação do aprovador, exibir, no mínimo, as mesmas informações da operação apresentadas ao usuário solicitante na etapa de confirmação na Instituição Transmissora de Dados.

`REQ.DC-13000` No fluxo do aprovador, apresentar a identificação do usuário que iniciou a jornada e dos outros aprovadores envolvidos na operação, caso existam.

`REQ.DC-13100` No fluxo do aprovador, especificar que o prazo máximo para atuação do(s) aprovador(es) é de 15 dias corridos, contados a partir da aprovação do consentimento pelo solicitante.

`REQ.DC-13200` No fluxo do aprovador, deixar claro que caso o prazo expire será necessário um novo pedido de compartilhamento.

![image-20260623-030050.png](images/image-20260623-030050.png)

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
        

**Cenário: Geral**

REC.DC-03700

-   `REC.DC-03700` A linguagem (“Termo para o Cliente”) presente no Glossário de Experiência pode ser simplificada, para evitar repetitividade, e apresentada de outras formas (p.ex.: no infinitivo).
    

REC.DC-03800

-   `REC.DC-03800` Caso o usuário queira cancelar o compartilhamento de dados na etapa de confirmação da Transmissora, mostrar um alerta para confirmar a ação do usuário.
    

Ex. Deseja cancelar o compartilhamento de dados?

REC.DC-00390

-   `REC.DC-03900` Caso os aprovadores não tomem as ações necessárias em até 7 dias, enviar novas notificações para lembrar o usuário responsável pela aprovação da pendência, por meio de seu canal eletrônico padrão.  
    Ex.: SMS, push, etc.
    

REC.DC-04000

-   `REC.DC-04000` De acordo com as especificações de Fase 2 mais recentes, a Instituição Receptora de Dados pode informar ao solicitante que o seu compartilhamento de dados está pendente de aprovação na Instituição Transmissora.  
    Ex.: SMS, push, etc.
    

* * *

# Etapa 5: Redirecionamento

Etapa 5 Introdução

Nesta etapa, o usuário é redirecionado do ambiente da Instituição Transmissora para o ambiente da Instituição Receptora para a efetivação do compartilhamento de dados. O usuário acompanha o processo por meio de uma tela informativa, sem a necessidade de realizar qualquer ação adicional, sendo informado de que o redirecionamento está em andamento e ocorre de forma segura.

A Instituição Transmissora deve garantir que o redirecionamento seja automático, sem o uso de navegadores intermediários. Também pode possibilitar a consulta ao status do processo em caso de interrupção, assegurando continuidade e clareza na experiência.

#F4F5F7

## Requisitos - IT

**Cenário: Tela de transição**

`REQ.DC-10100` Durante o redirecionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o redirecionamento.

`REQ.DC-10200` Na tela de redirecionamento, informar que o redirecionamento está em andamento.

`REQ.DC-10300` Na tela de redirecionamento, informar que o redirecionamento é seguro.

`REQ.DC-10400` Na tela de redirecionamento, informar que o redirecionamento é necessário para efetivação da operação.

-   Ex.: Aguarde enquanto te redirecionamos para concluir a operação.
    

`REQ.DC-10500` Não exigir qualquer ação adicional do usuário para confirmar o redirecionamento, o caráter da etapa é apenas informativo.

`REQ.DC-10600` Em dispositivos móveis, redirecionar o usuário diretamente para o aplicativo da IR, sem a passagem por navegadores intermediários.

`REQ.DC-10700` Redirecionar o usuário ao mesmo ambiente da IR utilizado no início da jornada (aplicativo ou browser).

img 1800![image-20260818-185441.png](images/image-20260818-185441.png)#F4F5F7

## Recomendações - IT

**Cenário: Interrupção da jornada**

REC.DC-02500

-   `REC.DC-02500` Quando o fluxo de consentimento for interrompido nesta etapa, permitir o acesso fácil à visualização do status do processo pelos canais digitais da Instituição.
    

**Cenário: Tela de transição**

REC.DC-02600

-   `REC.DC-02600` Utilizar elementos visuais e textuais que reforcem o redirecionamento, como _loaders_, animações, barras de progresso ou indicadores visuais.
    

![image-20260818-184204.png](images/image-20260818-184204.png)

* * *

# Etapa 6: Efetivação com múltiplos aprovadores

Nesta etapa, o compartilhamento de dados é efetivado e o usuário visualiza, no ambiente da IR, o resultado da solicitação realizada. O usuário recebe a confirmação de sucesso ou insucesso do compartilhamento e pode consultar o status do consentimento, assim como os principais detalhes da autorização concedida.

A IR deve comunicar o resultado da jornada de forma clara e, em caso de sucesso, apresentar um resumo com informações essenciais, como validade do consentimento, finalidade do uso dos dados e escopo compartilhado.

#F4F5F7

## Requisitos - IR

**Cenário: Caso de aprovação adicional, na tela do solicitante**

`REQ.DC-13300` Assim que o solicitante retornar da IT, apresentar uma tela informando o sucesso ou o insucesso da confirmação da solicitação.

`REQ.DC-13400` Assim que o solicitante retornar da IT, informar que a solicitação está pendente de aprovação e que, após a atuação do aprovador, a funcionalidade, finalidade ou benefício terão continuidade no ambiente da Instituição Receptora de Dados.

`REQ.DC-13500` Em caso de erro, especificar o problema ao usuário e acrescentar uma orientação para resolução, se possível.

**Cenário: Mensagem de sucesso**

`REQ.DC-10810` Informar, com destaque, o caminho para acessar a área de gestão de compartilhamento de dados da IR.

`REQ.DC-10820` Informar, com destaque, que o compartilhamento de dados pode ser cancelado a qualquer momento tanto na IR quanto na IT.

`REQ.DC-10830` Se a IR oferecer alteração do compartilhamento de dados, informar, com destaque, que o compartilhamento de dados pode ser alterado a qualquer momento.

`REQ.DC-10840` Se a IR oferecer renovação (padrão ou simplificada) do compartilhamento de dados, no caso de vencimento determinado, informar, com destaque, que o compartilhamento de dados pode ser renovado a qualquer momento.

**Nota**

Como o consentimento ainda não foi efetivado, não é necessário apresentar o resumo da solicitação.

img 2000![image-20260623-030450.png](images/image-20260623-030450.png)

**Cenário: Consentimento recém confirmado**

`REQ.DC-11440` Em caso de sucesso, exibir um resumo da solicitação. (Ex.: botão "detalhes" ou "veja mais").

#F4F5F7

## Requisitos - IT

**Cenário: Caso de aprovação adicional, na tela do aprovador**

`REQ.DC-13600` Após a confirmação no ambiente de Instituição Transmissora da Dados, apresentar uma tela comunicando o sucesso (ou insucesso) da etapa de aprovação do compartilhamento.

`REQ.DC-13700` Em caso de erro, especificar o problema e acrescentar uma orientação para resolução, se possível.

![image-20260623-030646.png](images/image-20260623-030646.png)

**Cenário: Consentimento recém confirmado**

`REQ.DC-11440` Em caso de sucesso, exibir um resumo da solicitação. (Ex.: botão "detalhes" ou "veja mais").

#F4F5F7

## Recomendações - IR

**Cenário: Geral**

`REC.DC-02800` No resumo do compartilhamento, exibir o nome da instituição de origem dos dados.

`REC.DC-04100` Para casos com mais de um aprovador, é recomendado que a Receptora possibilite acesso rápido para a continuação da jornada pelo usuário, após a conclusão das aprovações na Transmissora.
