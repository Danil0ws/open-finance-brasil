# v.23.00.00 Compartilhamento de Dados PF via CIBA

# Visão Geral

Visão geral CIBA

A jornada de compartilhamento de dados via CIBA PF inicia-se no ambiente da Instituição Receptora (IR), onde o usuário solicita o compartilhamento de dados, seleciona uma ou mais instituições transmissoras, define os dados e o prazo do consentimento e confirma a solicitação. Diferentemente do fluxo com redirecionamento imediato, a solicitação fica pendente para aprovação posterior nas instituições transmissoras escolhidas.

Após a conclusão da solicitação na IR, o usuário é orientado a acessar o ambiente de cada Instituição Transmissora (IT) selecionada para confirmar individualmente o compartilhamento. Nessa etapa, as instituições devem sinalizar a pendência de confirmação e notificar o usuário por canais digitais seguros. Ao acessar o ambiente da IT, o usuário realiza a autenticação conforme os padrões da instituição, revisa as informações do consentimento e confirma ou interrompe a autorização de compartilhamento.

Por fim, conforme as confirmações forem realizadas nas instituições transmissoras, a Instituição Receptora atualiza o status das solicitações no seu ambiente.

![image-20260727-172759.png](images/image-20260727-172759.png)

* * *

# Protótipo navegável (Jornada de Dados do usuário)

100%100%middle600

* * *

# Fluxo de telas (Jornada de Dados do usuário)

![image-20260727-182524.png](images/image-20260727-182524.png)

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

**Cenário: Seleção da IT**

`REQ.DC-05110` Quando a instituição disponibilizar seleção múltipla de instituições transmissoras, permitir que o usuário selecione até cinco instituições para a mesma solicitação de compartilhamento.

`REQ.DC-05120` Impedir que o usuário avance sem ter escolhido pelo menos uma instituição transmissora.

`REQ.DC-05130` Impedir que o usuário selecione mais de cinco instituições transmissoras.

REQ.DC-img 00110![image-20260727-183325.png](images/image-20260727-183325.png)

**Cenário: Seleção de dados**

`REQ.DC-05200` Disponibilizar a visualização e a configuração, quando aplicável, dos dados objeto do compartilhamento.

`REQ.DC-05300` Exibir as categorias de dados na tela principal da jornada, ocultando os agrupamentos, mas permitindo que eles permaneçam acessíveis a partir da interação dos usuários.

-   Ex.: menu agrupado ou botão de mais detalhes.
    

`REQ.DC-05400` Discriminar categorias obrigatórias e opcionais para dados ou agrupamentos, observando que a obrigatoriedade só é permitida em casos de relação direta com a finalidade de uso.

`REQ.DC-05500` Especificar o motivo da obrigatoriedade, quando houver dados obrigatórios.

`REQ.DC-05600` Permitir a remoção ou inclusão de categorias e agrupamentos de dados opcionais no consentimento.

`REQ.DC-05700` Em cenários de transações de crédito, investimento e/ou câmbio, informar ao usuário que novas operações ou contratações dessas categorias terão seus dados automaticamente incorporados ao consentimento vigente.

`REQ.DC-05710` Impedir que o usuário selecione dados diferentes para cada transmissora na mesma jornada.

`REQ.DC-05720` Exibir mensagem informando que todo o conjunto de dados selecionados será solicitado, de forma idêntica, a todas as transmissoras escolhidas. `REQ.DC-05730` Exibir mensagem informando que as instituições transmissoras não compartilharão dados entre si.

![image-20260825-184739.png](images/image-20260825-184739.png)

**Cenário: Prazo de consentimento**

`REQ.DC-05800` Exibir um campo que indique a duração ou o prazo do compartilhamento de dados.

`REQ.DC-05900` Preencher o campo de prazo por padrão, conforme entender mais adequado ao caso de uso.

`REQ.DC-06000` Disponibilizar ao usuário a possibilidade de alterar o prazo para, no mínimo, uma opção adicional além do prazo padrão.

`REQ.DC-06100` No caso de prazo indeterminado, identificar para o usuário como Indeterminado ou termo similar.

`REQ.DC-06110` Impedir que o usuário selecione prazos de validade do compartilhamento diferentes para cada transmissora na mesma jornada.

`REQ.DC-06120` Exibir mensagem informando que todas as transmissoras escolhidas compartilharão os dados pelo mesmo período selecionado pelo usuário.

![image-20260728-003221.png](images/image-20260728-003221.png)

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

**Cenário: Conclusão da solicitação**

`REQ.DC-06610` Após a confirmação da solicitação de compartilhamento pelo usuário, exibir tela de Conclusão da solicitação.

`REQ.DC-06620` Na tela de Conclusão da solicitação, orientar o usuário a acessar o ambiente da(s) instituição(ões) transmissora(s).

`REQ.DC-06630` Na tela de Conclusão da solicitação, orientar o usuário a acessar a área de gestão Open Finance das instituições transmissoras para confirmar a solicitação de compartilhamento.

`REQ.DC-06640` Na tela de Conclusão da solicitação, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação, que deve ser feita em até 24 horas.

`REQ.DC-06650` Na tela de Conclusão da solicitação, exibir o nome de cada instituição transmissora escolhida.

`REQ.DC-06660` Na tela de Conclusão da solicitação, exibir o logotipo de cada instituição transmissora escolhida.

`REQ.DC-06670` Na tela de Conclusão da solicitação, exibir o status inicial da solicitação de cada instituição transmissora escolhida.

`REQ.DC-06680` Na tela de Conclusão da solicitação, antes que o usuário saia dessa tela, exibir alerta informando-o sobre a necessidade de acesso aos ambientes das instituições transmissoras escolhidas para confirmar a solicitação.

![image-20260728-003621.png](images/image-20260728-003621.png)

#F4F5F7

## Recomendações - IR

**Cenário: Onboarding**

REC.DC-01110

`REC.DC-01110` No início da jornada de compartilhamento de dados, ao menos no primeiro acesso do usuário, exibir onboarding para informar o usuário sobre o compartilhamento de dados.

REC.DC-01120

`REC.DC-01120` No onboarding, informar o usuário sobre a segurança do processo de compartilhamento de dados.

REC.DC-01131

`REC.DC-01130` No onboarding, quando a instituição oferecer a seleção múltipla de instituições transmissoras, informar o usuário que ele poderá selecionar até cinco instituições para compartilhamento de dados.

REC.DC-01140

`REC.DC-01140` No onboarding, informar o usuário sobre a possibilidade de escolha dos dados a serem compartilhados.

REC.DC-01150

`REC.DC-01150` No onboarding, informar o usuário sobre a possibilidade de definição do prazo de compartilhamento dos dados.

REC.DC-01161

`REC.DC-01160` No onboarding, informar o usuário sobre a necessidade de confirmação do compartilhamento individualmente em cada uma das instituições transmissoras escolhidas.

img 500![image-20260728-003817.png](images/image-20260728-003817.png)

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

**Cenário: Resumo da Solicitação**

💡 `REC.DC-02110` Exibir resumo da solicitação.

💡 `REC.DC-02120` No resumo da solicitação, informar todas as instituições transmissoras selecionadas.

💡 `REC.DC-02130` No resumo da solicitação, informar o objetivo do uso dos dados.

💡 `REC.DC-02140` No resumo da solicitação, informar o prazo do compartilhamento.

💡 `REC.DC-02150` No resumo da solicitação, informar os dados compartilhados.

![image-20260728-004100.png](images/image-20260728-004100.png)

**Cenário: Conclusão da solicitação**

💡 `REC.DC-02160` Na tela de conclusão da solicitação, exibir indicador visual indicando o status inicial de confirmação de cada instituição transmissora escolhida.

-   Ex.: 1 de 5.
    

💡 `REC.DC-02170` Permitir que o usuário retorne à tela inicial do ambiente da IR.

💡 `REC.DC-02180` Na tela de conclusão da solicitação, orientar o usuário sobre a notificação enviada por cada instituição transmissora selecionada para aprovação do compartilhamento.

![image-20260728-004435.png](images/image-20260728-004435.png)

* * *

# Etapa 2: Notificação

Nesta etapa, após a conclusão da solicitação no ambiente da Instituição Receptora, o usuário passa a ter pendências de confirmação nas instituições transmissoras escolhidas. As instituições devem dar visibilidade sobre essas pendências por meio de notificações e indicadores visuais em seus ambientes digitais, orientando o usuário a acessar o fluxo necessário para confirmar o compartilhamento de dados.

A Instituição Transmissora deve notificar ativamente o usuário por canais digitais seguros, sinalizar a pendência no Ambiente Open Finance e manter essa informação disponível até que a ação seja concluída.

Essa etapa tem como objetivo garantir que o usuário compreenda que a solicitação ainda depende de confirmação individual nas instituições transmissoras para que o compartilhamento seja efetivado.

#F4F5F7

## Requisitos - IT

**Cenário: Notificação para aprovação**

`REQ.DC-06690` Notificar ativamente o usuário, no mínimo uma vez, sobre a existência de pendência de confirmação. (Ex.: notificação via push)

`REQ.DC-06695` Não utilizar SMS ou e-mail para notificação de pendência de confirmação.

`REQ.DC-06710` Enviar a notificação em até 20 segundos a partir da confirmação da solicitação.

`REQ.DC-06720` Na notificação, exibir informações claras sobre a pendência do compartilhamento.

`REQ.DC-06730` No ambiente de cada instituição transmissora escolhida, exibir indicador visual sinalizando a existência de pendência de confirmação no Ambiente Open Finance, localizado no primeiro nível de navegação do aplicativo.

`REQ.DC-06740` Exibir a pendência de confirmação no Ambiente Open Finance até que o usuário conclua a ação.

`REQ.DC-06750` Enquanto a solicitação de confirmação estiver pendente, imediatamente após a autenticação do usuário, exibir, na tela inicial, alerta através de um componente visual de alta prioridade (ex.: bottom sheet ou modal), informando o usuário sobre a pendência de confirmação da solicitação e do prazo para confirmação no Open Finance.

`REQ.DC-06760` No alerta, apresentar um botão de ação claro que direcione o usuário diretamente para o fluxo de confirmação do consentimento.

`REQ.DC-06770` Permitir que o usuário feche ou ignore o alerta sem cancelar a solicitação.

![image-20260824-194906.png](images/image-20260824-194906.png)#F4F5F7

## Requisitos - IR

**Cenário: Notificação para aprovação**

`REQ.DC-06780` No Ambiente Open Finance, localizado no primeiro nível do menu principal de navegação da instituição, exibir indicador visual sinalizando a existência de pendência de confirmação do compartilhamento de dados.

`REQ.DC-06790` Exibir a pendência no Ambiente Open Finance até que o usuário conclua a ação.

`REQ.DC-06810` Caso a IR notifique o usuário sobre a existência de pendência de confirmação, não utilizar SMS ou e-mail para notificação de pendência de confirmação.

![image-20260728-004728.png](images/image-20260728-004728.png)#F4F5F7

## Recomendações - IT

**Cenário: Notificação para aprovação**

REC.DC-02210

-   💡 `REC.DC-02210` Disponibilizar, na notificação, deeplink com acesso direto ao fluxo necessário para tratamento da pendência.
    

REC.DC-02220

-   💡 `REC.DC-02220` Caso o sistema operacional tenha essa função, exibir um indicador visual (_badge_) sobre o ícone do aplicativo da(s) transmissora(s) no dispositivo do usuário sempre que houver notificações ou ações pendentes não lidas.
    

REC.DC-02230

-   💡 `REC.DC-02230` Exibir a pendência de confirmação até que o usuário clique no ícone do aplicativo da(s) transmissora(s) no dispositivo.
    

REC.DC-02240

-   💡 `REC.DC-02240` Quando disponível, priorizar notificações via push.
    

![image-20260728-004854.png](images/image-20260728-004854.png)#F4F5F7

## Recomendações - IR

**Cenário: Notificação para aprovação**

REC.DC-02250

-   💡 `REC.DC-02250` Notificar o usuário sobre a existência de pendência de confirmação.
    
    -   Ex.: notificação via push.
        

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

![image-20260728-010004.png](images/image-20260728-010004.png)

Digite ou cole algo aqui para o transformar em um trecho.

**Cenário: Seleção de origem**

**Nota**

Caso o login do usuário na Instituição Transmissora de Dados utilize o número da conta (acesso a uma conta por vez), não é esperado que haja multiplicidade de origem para a categoria Dados da Conta.

`REQ.DC-08400` Em casos de multiplicidade de origem/produto para as categorias de dados, permitir a seleção conforme o escopo de dados disponível no canal digital da Instituição Transmissora de Dados.

`REQ.DC-08500` Em casos de multiplicidade de origem/produto para as categorias de dados, apresentar todas as opções de origem/produto pré-selecionadas, com possibilidade de desmarcação para redução do escopo, mantendo no mínimo uma origem selecionada.

`REQ.DC-08600` Em casos de multiplicidade de origem/produto para as categorias de dados, quando uma mesma marca contemplar diferentes instituições percebidas pelo usuário de forma segregada, deixar claro a qual instituição cada opção de origem pertence.

`REQ.DC-08700` Disponibilizar multiplicidade de origem/produto somente para as seguintes categorias: Dados de contas (contas de depósito à vista, de poupança e de pagamento pré-pagas ou pós-pagas) e Cartões de crédito.

`REQ.DC-08800` Não disponibilizar seleção de origem para as demais categorias de dados, como dados cadastrais, investimentos, operações de crédito e câmbio. Para esses casos, compartilhar todos os dados existentes na Instituição Transmissora de Dados.

`REQ.DC-08900` Compartilhar as sub-modalidades dos produtos contratados ou distribuídos pela Instituição Transmissora de Dados, bem como as operações de câmbio contratadas, canceladas ou liquidadas por essa instituição. O acesso a essas sub-modalidades acontece em seus canais digitais.

`REQ.DC-09000` Em cenários de transações de crédito, investimento e/ou câmbio, informar ao usuário que novas operações ou contratações dessas categorias terão seus dados automaticamente incorporados ao consentimento vigente.

**Nota**

Os dados transacionais, operações de crédito, investimentos e de operações de câmbio serão compartilhados por até 12 meses retroativos, conforme [Resolução Conjunta nº1](data/references/Resolução_Conjunta_1.md).

img 1400![image-20260728-010457.png](images/image-20260728-010457.png)

**Cenário: Detalhes dos dados compartilhados**

`REQ.DC-09100` Não exibir de forma detalhada informações secundárias como o nome dos agrupamentos.

-   Ex.: saldo, limites e extratos.
    

`REQ.DC-09200` Não exibir de forma detalhada informações secundárias como informações da tabela de dados.

-   Ex.: transações de cartões de crédito - informações do cartão, identificação de transação, valor da transação, datas, identificação do estabelecimento.
    

**Nota**

Para apresentar os detalhamentos que a Instituição Transmissora de Dados julgar como necessários, deve-se utilizar recursos de User Experience conforme padrões da instituição, por exemplo: pequenos botões de informação (tooltips) (?) (+), expandir informação ao passar o mouse (mouseover), link do tipo “Mostrar mais” etc.

`REQ.DC-09300` Para situações nas quais o usuário compartilha uma categoria de produtos ou de contratos por meio de seleção única (ex.: operações de crédito, investimento e/ou câmbio), considerar todas as permissões para os produtos da mesma categoria, ainda que não os comercialize no momento da confirmação.

img 1500![image-20260728-010623.png](images/image-20260728-010623.png)

**Cenário: Detalhes para a confirmação**

`REQ.DC-09400` Apresentar ao usuário um indicativo da próxima etapa da jornada.

`REQ.DC-09500` Permitir que o usuário continue a transmissão dos dados com apenas uma única confirmação. Reduzir cliques desnecessários após a autenticação, admitindo apenas cliques adicionais para seleção de origens e digitação de credenciais, quando aplicável.

`REQ.DC-09600` Não apresentar Termos e Condições nesta etapa, mesmo que por meio de link, ainda que não se exija aceite e/ou leitura.

**Nota**

Conforme regulação vigente, etapas adicionais ou utilização de métodos mais rigorosos de autenticação não contempladas atualmente no canal digital da Instituição Transmissora de Dados serão interpretadas como mecanismos que desincentivam o compartilhamento de dados.

img 1600![image-20260728-010815.png](images/image-20260728-010815.png)

`REQ.DC-09700` Possibilitar que o usuário interrompa a jornada antes da confirmação.

`REQ.DC-09800` Garantir que a opção de interrupção da jornada não seja visualmente mais proeminente do que a opção de prosseguir.

img 1700![image-20260728-010930.png](images/image-20260728-010930.png)

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

# Etapa 5: Efetivação em CIBA

Etapa 5 Efetivação CIBA

Nesta etapa, após a confirmação do compartilhamento pelo usuário, a efetivação ocorre no ambiente da Instituição Transmissora. A IT deve dar visibilidade ao usuário sobre o resultado da confirmação realizada, considerando a solicitação recebida anteriormente da Instituição Receptora.

Diferentemente do hybrid flow, em que a efetivação é apresentada no retorno ao ambiente da Instituição Receptora, no fluxo CIBA a conclusão acontece na própria Instituição Transmissora, pois o usuário acessa individualmente cada transmissora para aprovar a pendência de compartilhamento. Assim, cabe à IT comunicar a confirmação do consentimento, apresentar as informações essenciais do compartilhamento e permitir que o usuário consulte o consentimento recém confirmado no Ambiente de gestão Open Finance.

#F4F5F7

## Requisitos - IT

**Cenário: Mensagem de sucesso**

`REQ.DC-11410` Na tela de efetivação, informar o usuário sobre o sucesso ou insucesso do compartilhamento de dados.

`REQ.DC-11420` Na tela de efetivação, exibir mensagem neutra e sem estímulo ou indicação de cancelamento do compartilhamento de dados.

`REQ.DC-11430` Na tela de efetivação, informar o usuário sobre a possibilidade de gerenciamento do compartilhamento de dados na Área de Gestão do Open Finance.

REQ.DC-img 11441![image-20260728-011221.png](images/image-20260728-011221.png)

**Cenário: Detalhes do consentimento**

`REQ.DC-11440` Em caso de sucesso, exibir um resumo da solicitação. (Ex.: botão "detalhes" ou "veja mais").

`REQ.DC-11450` No resumo da solicitação, apresentar o prazo e a data final. Em caso de prazo indeterminado, identificar como "Indeterminado" ou termo equivalente.

`REQ.DC-11460` No resumo da solicitação, apresentar os tipos de dados compartilhados, como dados cadastrais, contas, cartões de crédito, investimentos e operações de crédito.

REQ.DC-img 11442![image-20260728-011423.png](images/image-20260728-011423.png)

**Cenário: Consentimento recém confirmado**

`REQ.DC-11400` Incluir no ambiente de gestão do Open Finance nos canais digitais as informações e o status do consentimento recém confirmado.
