# v.23.00.00 Vinculação de Conta (JSR) via hybrid flow

#   
Visão geral

A Jornada de **Vinculação de Conta para pagamentos Sem Redirecionamento (JSR)** ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração de um vínculo entre a ITP, o dispositivo do usuário e a Instituição Detentora de Conta (ID) do usuário.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida, com clareza sobre as próximas etapas.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, configura dados do vínculo como prazo e limites, e confirma.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Na ITP, o usuário valida a chave de segurança para confirmar os pagamentos futuros e é informado sobre o resultado da solicitação do vínculo, concluindo a jornada.
    

* * *

# Jornada de Vinculação de Conta (JSR)

![image-20260713-143447.png](images/image-20260713-143447.png)

* * *

# Telas de exemplo

wide760

**Nota**

Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

# Protótipo navegável

100%600

* * *

# Fluxo de telas

![image-20260713-143731.png](images/image-20260713-143731.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à Jornada de Vinculação de Conta para a Jornada de pagamentos Sem Redirecionamento (JSR)

## Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação
    

## Cenário de referência

-   Vinculação de Conta imediata entre ITP, dispositivo e ID.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.  
    

> Jornadas que envolvam o compartilhamento de saldo e limite via Jornada Otimizada e troca de dispositivo devem observar as regras específicas previstas nas páginas correspondentes.

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de vinculação de conta na Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Escolhe a Instituição Detentora de Conta (ID) que será utilizada para realizar os pagamentos sem redirecionamento.  
    

A ITP deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultar informações sensíveis.
    
-   Preparar a solicitação de vinculação de conta para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.VC-00100 a 00600#F4F5F7

## Requisitos - ITP

**Cenário: Solicitação de vinculação de conta**

-   `REQ.VC-00100` Mencionar o Open Finance em algum ponto visível da interface.  
    Ex.: tooltip, selo, frase como "com a segurança do Open Finance”.
    
-   `REQ.VC-00200` Informar ao usuário que o vínculo de conta está sendo criado para realização de transações futuras.
    
-   `REQ.VC-00300` Se apresentar Termos e Condições, exibir o conteúdo de forma clara e objetiva.
    
-   `REQ.VC-00400` Se apresentar Termos e Condições, não utilizar _opt-in_.
    
-   `REQ.VC-00500` Se apresentar Termos e Condições, informar que, ao continuar, o usuário está concordando com esses termos.
    
-   `REQ.VC-00600` Informar ao usuário que ao continuar, ele será direcionado para a ID para confirmar a vinculação.
    

![image-20260610-183710.png](images/image-20260610-183710.png)

REQ.VC-01200 a 01700

**Cenário: Busca e seleção da ID**

-   `REQ.VC-01200` Exibir ferramenta de busca e seleção da ID.
    
-   `REQ.VC-01300` Exibir todas as Detentoras que ofereçam a JSR.
    
-   `REQ.VC-01400` Permitir que o usuário busque tanto pela marca da ID quanto por um participante associado, exibindo corretamente a marca correspondente nos resultados.
    
-   `REQ.VC-01500` Permitir que a seleção final da ID seja feita somente pela marca da instituição, e não pelo nome do participante associado.
    
-   `REQ.VC-01600` Exibir apenas marcas adequadas ao tipo de público identificado (PF ou PJ).
    
-   `REQ.VC-01700` Exibir cada marca uma única vez, mesmo que existam múltiplos registros para ela no Diretório de Participantes.
    

![image-20260610-184522.png](images/image-20260610-184522.png)REC.VC-00100 a 00700#F4F5F7

## Recomendações - ITP

**Cenário: Onboarding**

-   `REC.VC-00100` Disponibilizar, ao menos na primeira jornada de vinculação de conta, onboarding com informações claras sobre as principais regras do serviço.
    
-   `REC.VC-00200` No onboarding, informar o que é a vinculação de conta e suas vantagens.
    
-   `REC.VC-00300` No onboarding, informar sobre a possibilidade de definição de limite diário/por transação para o vínculo.
    
-   `REC.VC-00400` No onboarding, informar sobre a possibilidade de definição de um apelido para o dispositivo autorizado.
    
-   `REC.VC-00500` No onboarding, informar sobre a possibilidade de definição de prazo de validade do vínculo.
    
-   `REC.VC-00600` No onboarding, informar sobre a possibilidade de cancelamento do vínculo de conta a qualquer momento.
    
-   `REC.VC-00700` No onboarding, informar claramente os benefícios da jornada com Open Finance, destacando pontos como segurança, rapidez e praticidade.
    

![image-20260610-184929.png](images/image-20260610-184929.png)REC.VC-00800 a 01100

**Cenário: Geral**

-   `REC.VC-00800` Quando necessário, solicitar dados complementares da ID selecionada, como agência e número da conta, para facilitar a autenticação do usuário na ID.
    
-   `REC.VC-00900` Solicitar dados complementares para compor análises de prevenção à fraude, validade de identidade ou outras próprias de cada instituição.
    
-   `REC.VC-01000` Se apresentar Termos e Condições, exibir seu contéudo através de link, garantindo que o conteúdo seja compreensível e não redundante com o que já está presente na jornada.
    
-   `REC.VC-01100` Alertar sobre a possibilidade de falha na jornada em dispositivos com o recurso de ocultação de aplicativos ativado, orientando o usuário a desativar esse recurso se necessário.
    

![image-20260610-185248.png](images/image-20260610-185248.png)

* * *

# Etapa 2: Direcionamento

760Resumo

Nesta etapa, o usuário:

-   É direcionado da Iniciadora (ITP) para a sua Detentora de Conta (ID).
    

A ITP deve:

-   Orientar o usuário sobre o direcionamento.
    
-   Assegurar que a navegação ocorra de forma transparente, conforme o dispositivo utilizado.
    
-   Quando aplicável, exibir mensagens de erro claras ao usuário.
    

REQ.VC-01800 a 02300#F4F5F7

## **Requisitos - ITP**

**Cenário: Direcionamento hybrid flow**

-   `REQ.VC-01800` Direcionar o usuário para um canal digital seguro.
    
-   `REQ.VC-01900` Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador) e possuir o aplicativo da ID instalado, direcioná-lo para o aplicativo da ID (hybrid flow).
    
-   `REQ.VC-02000` Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app-only_, direcioná-lo para a loja de aplicativos.
    
-   `REQ.VC-02100` Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o ambiente da ID no navegador ou para a loja de aplicativos.
    
-   `REQ.VC-02200` Se o usuário iniciar a jornada na ITP em desktop e a ID for _app-only_, direcioná-lo para o aplicativo por meio de Hand-off (hybrid flow com Hand-off).
    
-   `REQ.VC-02300` Se o usuário iniciar a jornada na ITP em desktop e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o aplicativo da ID ou para o ambiente da ID no navegador.
    

REQ.VC-02400 a 02700

**Cenário: Tela de transição**

-   `REQ.VC-02400` Durante o direcionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o direcionamento.
    
-   `REQ.VC-02500` Na tela do direcionamento, informar que o direcionamento está em andamento.  
    Ex.: Estamos te direcionando para confirmar a operação.
    
-   `REQ.VC-02600` Na tela do direcionamento, informar que o direcionamento é seguro.  
    Ex.: Direcionamento com a segurança Open Finance.
    
-   `REQ.VC-02700` Na tela do direcionamento, informar que o usuário possui até 15 minutos para confirmar a vinculação de conta na ID.  
    Ex.: Você tem até 15 minutos para confirmar a operação.
    

REQ.VC-02800

-   `REQ.VC-02800` Em dispositivos móveis, direcionar o usuário diretamente para o aplicativo da ID, sem passar por navegadores intermediários.
    

![image-20260610-185619.png](images/image-20260610-185619.png)

REC.VC-01200 a 01300#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

-   `REC.VC-01200` Se a jornada for interrompida nesta etapa, permitir que o usuário retome-a facilmente através dos canais digitais da ITP.
    
-   `REC.VC-01300` Utilizar elementos visuais e textuais que reforcem o direcionamento, como loaders, animações, barras de progresso ou indicadores visuais.
    

![image-20260716-195220.png](images/image-20260716-195220.png)

* * *

# Etapa 3: Confirmação

760ResumoNesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Em caso de múltiplas contas de débito, pode escolher a que deseja vincular.
    
-   Revisa as informações do vínculo enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma a vinculação.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo da vinculação.
    
-   Permitir a edição da conta de débito, em caso de múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Quando aplicável, exibir mensagens de erro claras ao usuário.
    
-   Comunicar o resultado da autorização à ITP.
    
-   Enviar notificações ao usuário e, quando aplicável, aos demais aprovadores — em casos de múltiplas alçadas ou falha na conclusão da autorização. REQ.VC-02900 a 03200#F4F5F7

## Requisitos - ID

**Cenário: Autenticação na Detentora**

-   `REQ.VC-02900` Solicitar a autenticação do usuário conforme os padrões já definidos pela própria ID para operações fora do Open Finance, em conformidade com a regulação vigente.
    
-   `REQ.VC-03000` Permitir que o usuário siga o fluxo padrão da instituição para recuperação ou criação de acesso.
    
-   `REQ.VC-03100` Não exibir etapas adicionais ou utilizar métodos mais rigorosos de autenticação não contemplados em seu canal digital afim de desincentivar a transação, conforme a regulação vigente.
    
-   `REQ.VC-03200` Impedir que um usuário com CPF diferente daquele declarado pela ITP acesse a tela de autorização do vínculo de conta, informando com clareza sobre o motivo do impedimento.
    

![image-20260610-185916.png](images/image-20260610-185916.png)REQ.VC-03300

**Cenário: Seleção da conta de débito**

-   `REQ.VC-03300` Se o usuário tiver múltiplas contas na ID e ele tiver especificado a conta para pagamento na ITP e esta conta estiver válida e disponível após o login, exibi-la já selecionada por padrão.
    

REQ.VC-03400 a 03800

-   `REQ.VC-03400` Se houver múltiplas contas na ID, permitir que o usuário altere a conta de débito antes de confirmar a transação.
    
-   `REQ.VC-03500` Se houver múltiplas contas na ID, exibir todas as contas aptas para seleção.
    
-   `REQ.VC-03600` Se houver múltiplas contas na ID, indicar visualmente as contas que não estiverem aptas, com indicação clara do motivo.  
    Ex.: desabilitação visual da conta inapta com _tag_ indicando o motivo.
    
-   `REQ.VC-03700` Impedir a continuidade da jornada sem que uma conta válida seja selecionada.
    
-   `REQ.VC-03800` Manter o texto da opção de confirmação consistente, mesmo se a conta ainda não tiver sido selecionada.
    

![image-20260616-143702.png](images/image-20260616-143702.png)

Fluxograma ITP > IDtrue

REC.VC-03900 a 04400

**Cenário: Revisão e confirmação da vinculação de conta**

Após se autenticar, o usuário deve visualizar, na ID, todas as informações do vínculo de conta informadas pela ITP.

-   `REQ.VC-03900` Para titular da conta pessoa física, exibir nome e CPF do usuário de forma mascarada.
    
-   `REQ.VC-04000` Para titular da conta pessoa jurídica, exibir a razão social e CNPJ do usuário.
    
-   `REQ.VC-04100` Exibir números da agência e conta da conta de débito selecionada para o vínculo.
    
-   `REQ.VC-04200` Permitir a definição da data de validade do vínculo, com prazo padrão preenchido de 5 anos.
    
-   `REQ.VC-04300` Permitir que o usuário altere a data de validade do vínculo, inclusive para prazo indeterminado.
    
-   `REQ.VC-04400` Exibir o nome da instituição responsável pela iniciação da transação de pagamento.
    

![image-20260713-145052.png](images/image-20260713-145052.png)REQ.VC-04500 a 05000

-   `REQ.VC-04500` Permitir a definição dos limites diário e por transação para pagamentos com o vínculo de conta.
    
-   `REQ.VC-04600` Manter o limite diário não preenchido por padrão e permitir que o usuário insira um valor. ​
    
-   `REQ.VC-04700` Manter o limite por transação não preenchido por padrão e permitir que o usuário insira um valor.
    
-   `REQ.VC-04800` Impedir que o usuário defina um valor máximo por transação superior ao valor máximo diário.
    
-   `REQ.VC-04900` Informar o usuário que os limites do Pix serão considerados.
    
-   `REQ.VC-05000` Para conta conjunta de pessoas físicas, permitir que cada titular autorize seu próprio dispositivo.
    

REQ.VC-05100 a 05500

-   `REQ.VC-05100` Informar ao usuário que, após a confirmação, ele será redirecionado para a ITP.
    
-   `REQ.VC-05200` Permitir que, após se autenticar e revisar os dados da vinculação de conta, o usuário conclua a operação com uma única confirmação.
    
-   `REQ.VC-05300` Se a instituição utilizar um método adicional de confirmação da transação, seguir o mesmo padrão utilizado fora do Open Finance.
    
-   `REQ.VC-05400` Não exibir Termos e Condições durante a jornada de vinculação de conta.
    
-   `REQ.VC-05500` Não exibir qualquer aspecto que desvie o foco do usuário em confirmar a vinculação de conta, como, por exemplo link, botão, imagem, texto, entre outros.
    

![image-20260713-145956.png](images/image-20260713-145956.png)

REQ.VC-05800 a 06100

**Cenário: Interrupção da jornada**

-   `REQ.VC-05800` Permitir que o usuário interrompa a jornada antes da confirmação.
    
-   `REQ.VC-05900` Garantir que a opção de interrupção da jornada não seja visualmente mais proeminente do que a opção de prosseguir.
    
-   `REQ.VC-06000` Redirecionar o usuário para a ITP se ele cancelar a operação.
    
-   `REQ.VC-06100` Redirecionar o usuário para a ITP se ele retornar manualmente à etapa anterior da jornada (por meio de botão do ambiente digital, botão do dispositivo, link clicável etc.) e não seja possível exibir a tela imediatamente anterior.
    

![image-20260616-143923.png](images/image-20260616-143923.png)REC.VC-01400#F4F5F7

## Recomendações - ID

**Cenário: Seleção da conta de débito**

-   `REC.VC-01400` Se a ITP capturar os dados de conta do usuário, utilizá-los para facilitar a autenticação na ID, contanto que não haja prejuízo dos protocolos de segurança para autenticação seguidos pelas instituições.
    

![image-20260610-201803.png](images/image-20260610-201803.png)REC.VC-01500

**Cenário: Revisão e confirmação da vinculação de conta**

-   `REC.VC-01500` Permitir a definição de um nome/apelido para o dispositivo autorizado.
    

![image-20260616-143942.png](images/image-20260616-143942.png)REC.VC-01600**Cenário: Cancelamento da vinculação de conta**

-   `REC.VC-01600` Se o usuário tentar cancelar a vinculação de conta, exibir uma mensagem de confirmação.    
    Ex.: Tem certeza que deseja cancelar a vinculação? ![image-20260616-143959.png](images/image-20260616-143959.png)

* * *

# Etapa 4: Redirecionamento

760Resumo

Nesta etapa, o usuário:

-   É redirecionado da Instituição Detentora de Conta (ID) para o ambiente da Iniciadora de Transação de Pagamento (ITP).
    

A ID deve:

-   Garantir um redirecionamento seguro, automático e sem fricções.
    
-   Redirecionar o usuário para o mesmo ambiente (app ou browser) em que iniciou a jornada.  
    
-   Quando aplicável, exibir mensagens de erro ou pendências, como autorizações em múltiplas alçadas ou indisponibilidade momentânea dos sistemas.
    

wide760#F4F5F7

## Requisitos - ID

**Cenário: Tela de transição**

REQ.VC-06200 a 06500

-   `REQ.VC-06200` Durante o redirecionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o redirecionamento.
    
-   `REQ.VC-06300` Na tela do redirecionamento, informar que o redirecionamento está em andamento.  
    Ex.: Aguarde enquanto te redirecionamos para concluir a vinculação.
    
-   `REQ.VC-06400` Na tela do redirecionamento, informar que o redirecionamento é seguro.  
    Ex.: Redirecionamento com a segurança Open Finance.
    
-   `REQ.VC-06500` Na tela do redirecionamento, informar que o redirecionamento é necessário para efetivação da operação.  
    Ex.: Aguarde enquanto te redirecionamos para concluir a vinculação.
    

REQ.VC-06600 a 06700

-   `REQ.VC-06600` Em dispositivos móveis, redirecionar o usuário diretamente para o aplicativo da ITP, sem passar por navegadores intermediários.
    
-   `REQ.VC-06700` Redirecionar o usuário ao mesmo ambiente da ITP utilizado no início da jornada.
    

![image-20260611-143857.png](images/image-20260611-143857.png)

REC.VC-01700#F4F5F7

## Recomendações - ID

**Cenário: Tela de transição**

-   `REC.VC-01700` Utilizar elementos visuais e textuais que reforcem o direcionamento, como _loaders_, animações, barras de progresso ou indicadores visuais.
    

![image-20260611-144209.png](images/image-20260611-144209.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Valida a chave de autenticação que será utilizada para confirmar as transações com o vínculo de conta.
    
-   Visualiza o resultado da solicitação de vinculação de conta.  
    

A ITP deve:

-   Apresentar com clareza o resultado da vinculação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da vinculação.  
    
-   Quando aplicável, exibir mensagens de erro ou pendências, como autorizações em múltiplas alçadas, transações temporizadas ou indisponibilidade momentânea dos sistemas.
    

REQ.VC-06800#F4F5F7

## Requisitos - ITP

**Cenário: Criação de chaves no dispositivo**

-   `REQ.VC-06800` Solicitar que o usuário valide a geração da chave de autenticação utilizada para confirmar pagamentos realizados por meio do vínculo de conta, utilizando o mesmo mecanismo de autenticação empregado para desbloquear o dispositivo.  
    Ex.: biometria, senha ou PIN de desbloqueio do dispositivo.
    

![image-20260611-145108.png](images/image-20260611-145108.png)REQ.VC-06900 a 07400

**Cenário: Efetivação da vinculação de conta**

-   `REQ.VC-06900` Exibir mensagem informando sobre o resultado (sucesso ou falha) da solicitação de vinculação de conta.
    
-   `REQ.VC-07000` Em caso de sucesso, informar sobre a possibilidade de acesso aos detalhes do vínculo através da área de gestão.
    

![image-20260611-145618.png](images/image-20260611-145618.png)

* * *

REC.VC-01800#F4F5F7

## Recomendações - ITP

**Cenário: Efetivação da vinculação de conta**

-   `REC.VC-01800` Exibir os detalhes do vínculo através de, por exemplo, um botão ou link que direcione para área de gestão.  
    Exs.: “Ver comprovante”, “Detalhes”, “Saiba mais” etc.
    

![image-20260611-150033.png](images/image-20260611-150033.png)

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00100`

**Texto**

Mencionar o Open Finance em algum ponto visível da interface.  
Ex.: tooltip, selo, frase como "com a segurança do Open Finance”.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00200`

**Texto**

Informar ao usuário que o vínculo de conta está sendo criado para realização de transações futuras.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00300`

**Texto**

Se apresentar Termos e Condições, exibir o conteúdo de forma clara e objetiva.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00400`

**Texto**

Se apresentar Termos e Condições, não utilizar _opt-in_.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00500`

**Texto**

Se apresentar Termos e Condições, informar que, ao continuar, o usuário está concordando com esses termos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.VC-00600`

**Texto**

Informar ao usuário que ao continuar, ele será direcionado para a ID para confirmar a vinculação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-00700`

**Texto**

Permitir que o usuário compartilhe, de forma opcional, o saldo e limite da conta de débito a partir da Jornada Otimizada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-00800`

**Texto**

Apresentar a opção de compartilhamento de saldo e limite da conta de débito desabilitada por padrão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-00900`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta de débito, exibir na tela de solicitação, informação de que o saldo e o limite da conta estão sendo compartilhados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01000`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta de débito, exibir o escopo de cada dado compartilhado.​

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01100`

**Texto**

Não exibir qualquer aspecto que desvie o foco do usuário de confirmar o compartilhamento de saldo e limite da conta de débito, como, por exemplo link, botão, imagem, texto, entre outros.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01200`

**Texto**

Exibir ferramenta de busca e seleção da ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01300`

**Texto**

Exibir todas as Detentoras que ofereçam a JSR.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01400`

**Texto**

Permitir que o usuário busque tanto pela marca da ID quanto por um participante associado, exibindo corretamente a marca correspondente nos resultados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01500`

**Texto**

Permitir que a seleção final da ID seja feita somente pela marca da instituição, e não pelo nome do participante associado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01600`

**Texto**

Exibir apenas marcas adequadas ao tipo de público identificado (PF ou PJ).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01700`

**Texto**

Exibir cada marca uma única vez, mesmo que existam múltiplos registros para ela no Diretório de Participantes.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01700`

**Texto**

Garantir que cada marca seja exibida uma única vez, mesmo que existam múltiplos registros para ela no Diretório de Participantes.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01800`

**Texto**

Direcionar o usuário para um canal digital seguro.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-01900`

**Texto**

Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador) e possuir o aplicativo da ID instalado, direcioná-lo para o aplicativo da ID (Hybrid Flow).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02000`

**Texto**

Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app-only_, direcioná-lo para a loja de aplicativos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02100`

**Texto**

Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o ambiente da ID no navegador ou para a loja de aplicativos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02200`

**Texto**

Se o usuário iniciar a jornada na ITP em desktop e a ID for _app-only_, direcioná-lo para o aplicativo por meio de Hand-off (Hybrid Flow com Hand-off).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02300`

**Texto**

Se o usuário iniciar a jornada na ITP em desktop e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o aplicativo da ID ou para o ambiente da ID no navegador.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02400`

**Texto**

Durante o direcionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o direcionamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02500`

**Texto**

Na tela do direcionamento, informar que o direcionamento está em andamento.  
Ex.: Estamos te direcionando para confirmar a operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02600`

**Texto**

Na tela do direcionamento, informar que o direcionamento é seguro.  
Ex.: Direcionamento com a segurança Open Finance.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02700`

**Texto**

Na tela do direcionamento, informar que o usuário possui até 15 minutos para confirmar a vinculação de conta na ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-02800`

**Texto**

Em dispositivos móveis, direcionar o usuário diretamente para o aplicativo da ID, sem passar por navegadores intermediários.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-02900`

**Texto**

Solicitar a autenticação do usuário conforme os padrões já definidos pela própria ID para operações fora do Open Finance, em conformidade com a regulação vigente.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03000`

**Texto**

Permitir que o usuário siga o fluxo padrão da instituição para recuperação ou criação de acesso.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03100`

**Texto**

Não exibir etapas adicionais ou utilizar métodos mais rigorosos de autenticação não contemplados em seu canal digital afim de desincentivar a transação, conforme a regulação vigente.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03200`

**Texto**

Impedir que um usuário com CPF diferente daquele declarado pela ITP acesse a tela de autorização do vínculo de conta, informando com clareza sobre o motivo do impedimento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03300`

**Texto**

Se o usuário tiver múltiplas contas na ID e ele tiver especificado a conta para pagamento na ITP e esta conta estiver válida e disponível após o login, exibi-la já selecionada por padrão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03400`

**Texto**

Se houver múltiplas contas na ID, permitir que o usuário altere a conta de débito antes de confirmar a transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03500`

**Texto**

Se houver múltiplas contas na ID, exibir todas as contas aptas para seleção.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03600`

**Texto**

Se houver múltiplas contas na ID, indicar visualmente as contas que não estiverem aptas, com indicação clara do motivo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03700`

**Texto**

Impedir a continuidade da jornada sem que uma conta válida seja selecionada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03800`

**Texto**

Manter o texto da opção de confirmação consistente, mesmo se a conta ainda não tiver sido selecionada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-03900`

**Texto**

Para titular da conta pessoa física, exibir nome e CPF do usuário de forma mascarada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04000`

**Texto**

Para titular da conta pessoa juridica, exibir a razão social e CNPJ do usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04100`

**Texto**

Exibir número da agência e conta da conta de débito selecionada para o vínculo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04200`

**Texto**

Permitir a definição da data de validade do vínculo, com prazo padrão preenchido de 5 anos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04300`

**Texto**

Permitir que o usuário altere a data de validade do vínculo, inclusive para prazo indeterminado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04400`

**Texto**

Exibir o nome da instituição responsável pela iniciação da transação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04500`

**Texto**

Permitir a definição dos limites diário e por transação para pagamentos com o vínculo de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04600`

**Texto**

Manter o limite diário não preenchido por padrão e permitir que o usuário insira um valor. ​

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

PJR-158

**Instituição**

ID

**Justificativa**

Alteração a partir da IN 746

**ID**

`REQ.VC-04700`

**Texto**

Manter o limite por transação não preenchido por padrão e permitir que o usuário insira um valor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04800`

**Texto**

Impedir que o usuário defina um valor máximo por transação superior ao valor máximo diário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-04900`

**Texto**

Informar o usuário que os limites do Pix serão considerados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05000`

**Texto**

Para conta conjunta de pessoas físicas, permitir que cada titular autorize seu próprio dispositivo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05100`

**Texto**

Informar ao usuário que, após a confirmação, ele será redirecionado para a ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05200`

**Texto**

Permitir que, após se autenticar e revisar os dados da vinculação de conta, o usuário conclua a operação com uma única confirmação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05300`

**Texto**

Se a instituição utilizar um método adicional de confirmação da transação, seguir o mesmo padrão utilizado fora do Open Finance.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05400`

**Texto**

Não exibir Termos e Condições durante a confirmação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05500`

**Texto**

Não exibir qualquer aspecto que desvie o foco do usuário em confirmar a vinculação de conta, como, por exemplo link, botão, imagem, texto, entre outros.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05800`

**Texto**

Permitir que o usuário interrompa a jornada antes da confirmação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-05900`

**Texto**

Garantir que a opção de interrupção da jornada não seja visualmente mais proeminente do que a opção de prosseguir.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06000`

**Texto**

Redirecionar o usuário para a ITP se ele cancelar a operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06100`

**Texto**

Redirecionar o usuário para a ITP se ele retornar manualmente à etapa anterior da jornada (por meio de botão do ambiente digital, botão do dispositivo, link clicável etc.) e não seja possível exibir a tela imediatamente anterior.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06200`

**Texto**

Durante o redirecionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o redirecionamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06300`

**Texto**

Na tela do redirecionamento, informar que o redirecionamento está em andamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06400`

**Texto**

Na tela do redirecionamento, informar que o redirecionamento é seguro.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06500`

**Texto**

Na tela do redirecionamento, informar que o redirecionamento é necessário para efetivação da operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid Flow

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06600`

**Texto**

Em dispositivos móveis, redirecionar o usuário diretamente para o aplicativo da ITP, sem passar por navegadores intermediários.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

**ID**

`REQ.VC-06700`

**Texto**

Redirecionar o usuário ao mesmo ambiente da ITP utilizado no início da jornada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-06800`

**Texto**

Solicitar que o usuário valide a geração da chave de autenticação utilizada para confirmar pagamentos realizados por meio do vínculo de conta, utilizando o mesmo mecanismo de autenticação empregado para desbloquear o dispositivo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-06900`

**Texto**

Exibir mensagem informando sobre o resultado (sucesso ou falha) da solicitação de vinculação de conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-07000`

**Texto**

Em caso de sucesso, informar sobre a possibilidade de acesso aos detalhes do vínculo através da área de gestão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-07100`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta de débito através da Jornada Otimizada, informar que o cancelamento do vínculo também cancela o compartilhamento de saldo e limite.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-07200`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta de débito através da Jornada Otimizada, informar que o compartilhamento de saldo e limite pode ser cancelado a qualquer momento através da área de gestão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Vinculação de Conta

**Jornada**

Hybrid flow e Hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.VC-07300`

**Texto**

Se o usuário tiver compartilhado o saldo e limite da conta de débito através da Jornada Otimizada, informar que o cancelamento do compartilhamento de saldo e limite não cancela o vínculo de conta.
