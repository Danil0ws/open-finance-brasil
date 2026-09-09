# v.23.00.00 Pix via hybrid flow

# Visão geral

A Jornada de Iniciação de Pagamento Com Redirecionamento com **Pix** ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do pagamento imediato com Pix via Open Finance.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, revisa os dados da transação configurada na ITP e confirma o pagamento.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Por fim, a ITP informa o status da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-172705.png](images/image-20260112-172705.png)

* * *

# Telas de exemplo

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pelas marcas **Wiscredi** e **Cloud Finance**, sendo esta última utilizada como **solução whitelabel pelo recebedor Seu Lar**.  
A Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%600

* * *

## Fluxo de telas

![image-20260616-185145.png](images/image-20260616-185145.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamento imediato com Pix via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação  
    

## Cenário de referência

-   Pagamento imediato com Pix.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

Variações da jornada

> Jornadas que envolvam múltiplos aprovadores, troca de dispositivo e transações temporizadas devem observar as regras específicas previstas nas páginas correspondentes.

Nota.Regulamentação e Arranjo

**Nota**  
Além dos requisitos e recomendações previstos nesta jornada de pagamento, aplicam-se aqueles descritos em:

-   Regulamentação e documentos do arranjo de pagamento vigentes.
    

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento com Pix via Open Finance.
    
-   Escolhe a Instituição Detentora de Conta (ID) que será usada para realizar o pagamento.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada. 
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

![image-20260331-182228.png](images/image-20260331-182228.png)

###   
Métodos de iniciação com Pix

![image-20260319-194816.png](images/image-20260319-194816.png)

REQ.PG-00100 a 00200#F4F5F7

## Requisitos - ITP

**Cenário: Geral**

-   `REQ.PG-00100` Não comparar arranjos de pagamento de forma a desqualificar um deles.
    
-   `REQ.PG-00200` Mencionar o Open Finance em algum ponto visível da interface.  
    Ex.: Tooltip, selo, frase como "com a segurança do Open Finance”.
    

![image-20260609-125710.png](images/image-20260609-125710.png)

REQ.PG-00300 a 00700

**Cenário: Busca e seleção da ID**

-   `REQ.PG-00300` Exibir ferramenta de busca e seleção da ID.
    
-   `REQ.PG-00400` Permitir que o usuário busque tanto pela marca da instituição quanto por um participante associado, exibindo corretamente a marca correspondente nos resultados.
    
-   `REQ.PG-00500` Permitir que a seleção final da ID seja feita somente pela marca da instituição, e não pelo nome do participante associado.
    
-   `REQ.PG-00600` Exibir apenas marcas adequadas ao tipo de público identificado (PF ou PJ).
    
-   `REQ.PG-00700` Exibir cada marca uma única vez, mesmo que existam múltiplos registros para ela no Diretório de Participantes.
    

![image-20260609-125751.png](images/image-20260609-125751.png)

REQ.PG-00800

**Cenário: Solicitação de transação de pagamento**

Nesse momento, o usuário insere e/ou revisa as informações da transação conforme a forma de iniciação de pagamento selecionada e as regras do arranjo de pagamento.

-   `REQ.PG-00800` Além das informações descritas nesta etapa, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para solicitação de pagamento.
    

REQ.PG-00900

-   `REQ.PG-00900` Permitir que o usuário preencha ou altere o valor quando permitido pelo recebedor.
    

REQ.PG-01000

-   `REQ.PG-01000` Exibir o valor automaticamente sem possibilidade de alteração quando determinado pelo recebedor.
    

![image-20260609-134035.png](images/image-20260609-134035.png)

REQ.PG-01100

-   `REQ.PG-01100` Se a ITP cobrar tarifa pelo serviço, exibir o valor da tarifa cobrada.
    

REQ.PG-01200-   `REQ.PG-01200` Exibir a forma de pagamento. REQ.PG-01300

-   `REQ.PG-01300` Exibir a data do pagamento.
    

wide760

**Nota**

Para permitir o agendamento do pagamento, consulte a página **Pix Agendado**.

REQ.PG-01400

-   `REQ.PG-01400` Permitir preenchimento opcional da descrição do pagamento conforme a forma de iniciação do pagamento.
    

Ex.: Pix via chave Pix ou inserção manual dos dados transacionais do recebedor.

![image-20260615-175141.png](images/image-20260615-175141.png)

REQ.PG-01500

-   `REQ.PG-01500` Exibir a descrição automaticamente conforme a forma de iniciação do pagamento.
    

Ex.: Pix via QR Code.

![image-20260615-175214.png](images/image-20260615-175214.png)

REQ.PG-01600

-   `REQ.PG-01600` Permitir que o usuário insira os dados do recebedor como instituição, agência, conta e CPF/CNPJ em pagamentos via inserção manual de dados transacionais.
    

![image-20260615-175401.png](images/image-20260615-175401.png)

REQ.PG-01700

-   `REQ.PG-01700` Exibir os dados do recebedor automaticamente em pagamentos via chave Pix, Pix Copia e Cola e Pix via QR Code.
    

REQ.PG-01800

-   `REQ.PG-01800` Exibir nome e CPF (mascarado)/CNPJ do recebedor.
    

Nota.Recebedor

**Nota**  
Nesta etapa, a exibição do nome da instituição de destino do recebedor é opcional e fica a critério do participante.

REQ.PG-01900

-   `REQ.PG-01900` Exibir o nome da ID selecionada pelo usuário, se essa etapa tiver sido apresentada antes da revisão da transação.
    

REQ.PG-02000

-   `REQ.PG-02000` Exibir o nome da instituição responsável pela iniciação da transação de pagamento.
    

**Nota**  
Se o usuário já estiver no ambiente da própria ITP, a exibição do nome da ITP não é obrigatória, pois a identificação já é evidente no contexto.

REQ.PG-02100

-   `REQ.PG-02100` Informar ao usuário que a transação será concluída apenas se houver saldo e limite transacional disponíveis na conta de débito.
    

REQ.PG-02200 a 02400

**Atenção!**

De acordo com a regulação vigente, a exibição de “Termos e Condições” ou recurso similar é **facultativa** para as Instituições Iniciadoras de Transação de Pagamento (ITP) nesta etapa da jornada de iniciação de pagamento. No entanto, uma vez exibidos, devem obedecer aos requisitos a seguir.

-   `REQ.PG-02200` Se apresentar Termos e Condições, exibir o conteúdo de forma clara e objetiva.
    
-   `REQ.PG-02300` Se apresentar Termos e Condições, não utilizar _opt-in_.
    
-   `REQ.PG-02400` Se apresentar Termos e Condições, informar que, ao continuar, o usuário está concordando com esses termos.
    

REQ.PG-02500

-   `REQ.PG-02500` Informar ao usuário que, ao continuar, ele será direcionado para a ID para confirmar a solicitação.
    

![image-20260615-175727.png](images/image-20260615-175727.png)

REC.PG-00100#F4F5F7

## Recomendações - ITP

**Cenário: Geral**

-   `REC.PG-00100` Ao exibir ao usuário a opção de realizar pagamentos utilizando uma conta de outra instituição, utilizar linguagem pessoal e natural.
    
    -   “Pagar com minha conta”.
        
    -   “Transferir com meu banco”.
        
    -   “Usar minha Instituição”.
        
    -   “Pagar com outro banco”.
        

**Nota**  
Esses exemplos foram baseados no [teste de usabilidade feito pelo GT UX](https://ob-public-files.s3.amazonaws.com/20221024_Teste+de+etiquetas.pdf) realizado em outubro de 2022 e não contemplam todas as formas de abordar o usuário.

![image-20260609-140122.png](images/image-20260609-140122.png)

**Cenário: Onboarding**

REC.PG-00200

-   `REC.PG-00200` Exibir onboarding para informar o usuário sobre a oferta do serviço pela ITP.
    

REC.PG-00300 a 00500

-   `REC.PG-00300` No onboarding, informar sobre o fluxo completo da jornada, incluindo o direcionamento para a ID e o retorno à ITP.
    
-   `REC.PG-00400` No onboarding, explicar os benefícios da jornada com Open Finance, destacando pontos como segurança, rapidez e praticidade.
    
-   `REC.PG-00500` Quando o serviço for gratuito, informar sobre a gratuidade da operação.
    

REC.PG-00600

-   `REC.PG-00600` Exibir informações do serviço através de opções como “Saiba mais”.
    

![image-20260609-140454.png](images/image-20260609-140454.png)

REC.PG-00700

**Cenário: Solicitação de vinculação de conta via jornada de pagamento**

**Se a ITP oferecer a jornada de Vinculação de Conta para JSR a partir do pagamento**

-   `REC.PG-00700` Se o usuário não possuir nenhuma conta vinculada, informar que é necessário fazer um vínculo previamente e direcioná-lo para a jornada de Vinculação de Conta.
    

![image-20260624-181828.png](images/image-20260624-181828.png)REC.PG-00800 a 00900

**Cenário: Solicitação de transação de pagamento**

-   `REC.PG-00800` Permitir que o usuário altere facilmente os dados editáveis antes da continuação da jornada.
    
-   `REC.PG-00900` Posicionar os campos editáveis na parte superior da tela.
    

REC.PG-01000

-   `REC.PG-01000` Quando necessário, solicitar dados complementares da ID selecionada, como agência e número da conta, para facilitar a autenticação do usuário na ID.
    

REc.PG-01100

-   `REC.PG-01100` Exibir a data do pagamento preenchida com a data da solicitação.
    

REC.PG-01200

-   `REC.PG-01200` Alertar sobre a possibilidade de falha na jornada em dispositivos com o recurso de ocultação de aplicativos ativado, orientando o usuário a desativar esse recurso se necessário.
    

REC.PG-01300

-   `REC.PG-01300` Se apresentar Termos e Condições, exibir seu contéudo através de link, garantindo que o conteúdo seja compreensível e não redundante com o que já está presente na jornada.
    

![image-20260609-141056.png](images/image-20260609-141056.png)

* * *

# **Etapa 2:** Direcionamento

760Resumo

Nesta etapa, o usuário:

-   É direcionado da Iniciadora (ITP) para a sua Detentora de Conta (ID).
    

A ITP deve:

-   Orientar o usuário sobre o direcionamento.
    
-   Assegurar que a navegação ocorra de forma transparente, conforme o dispositivo utilizado.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-02600 a 03100#F4F5F7

## **Requisitos - ITP**

**Cenário: Direcionamento hybrid flow**

-   `REQ.PG-02600` Direcionar o usuário para um canal digital seguro.
    
-   `REQ.PG-02700` Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador) e possuir o aplicativo da ID instalado, direcioná-lo para o aplicativo da ID (hybrid flow).
    
-   `REQ.PG-02800` Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app-only_, direcioná-lo para a loja de aplicativos.
    
-   `REQ.PG-02900` Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o ambiente da ID no navegador ou para a loja de aplicativos.
    
-   `REQ.PG-03000` Se o usuário iniciar a jornada na ITP em desktop e a ID for _app-only_, direcioná-lo para o aplicativo por meio de Hand-off (hybrid Flow com hand-off).
    
-   `REQ.PG-03100` Se o usuário iniciar a jornada na ITP em desktop e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o aplicativo da ID ou para o ambiente da ID no navegador.
    

REQ.PG-03200 a 03400

**Cenário: Tela de transição**

-   `REQ.PG-03200` Durante o direcionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o direcionamento.
    
-   `REQ.PG-03300` Na tela do direcionamento, informar que o direcionamento está em andamento.  
    Ex.: Estamos te direcionando para confirmar a operação.
    
-   `REQ.PG-03400` Na tela do direcionamento, informar que o direcionamento é seguro.  
    Ex.: Direcionamento com a segurança Open Finance.
    

REQ.PG-03500

-   `REQ.PG-03500` Na tela do direcionamento, informar que o usuário possui até 5 minutos para confirmar a solicitação de autorização de pagamento na ID.  
    Ex.: Você tem até 5 minutos para confirmar a operação.
    

REQ.PG-03600

-   `REQ.PG-03600` Em dispositivos móveis, direcionar o usuário diretamente para o aplicativo da ID, sem passar por navegadores intermediários.
    

![image-20260625-121935.png](images/image-20260625-121935.png)

  

wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01400

-   `REC.PG-01400` Se a jornada for interrompida nesta etapa, permitir que o usuário retome-a facilmente através dos canais digitais da ITP.
    

REC.PG-01500

-   `REC.PG-01500` Utilizar elementos visuais e textuais que reforcem o direcionamento, como _loaders_, animações, barras de progresso ou indicadores visuais.
    

![image-20260609-141507.png](images/image-20260609-141507.png)

* * *

# Etapa 3: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Pode escolher a conta que deseja usar para fazer o pagamento se ele possuir mais de uma conta na ID.
    
-   Revisa as informações da solicitação enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma a solicitação.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo da solicitação.
    
-   Permitir a edição da conta de débito, se o usuário possuir múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    
-   Comunicar o resultado da solicitação à ITP.
    
-   Enviar notificações ao usuário e aos demais aprovadores nos cenários de múltiplos aprovadores.
    

![image-20260616-184640.png](images/image-20260616-184640.png)

REQ.PG-03700 a 03900#F4F5F7

## Requisitos - ID

**Cenário: Autenticação na Detentora**

-   `REQ.PG-03700` Solicitar a autenticação do usuário conforme os padrões já definidos pela própria ID para operações fora do Open Finance, em conformidade com a regulação vigente.
    
-   `REQ.PG-03800` Permitir que o usuário siga o fluxo padrão da instituição para recuperação ou criação de acesso.
    
-   `REQ.PG-03900` Não exibir etapas adicionais ou utilizar métodos mais rigorosos de autenticação não contemplados em seu canal digital a fim de desincentivar a transação, conforme a regulação vigente.
    

![image-20260615-180041.png](images/image-20260615-180041.png)

REQ.PG-04000 a 04500

**Cenário: Seleção da conta de débito**

-   `REQ.PG-04000` Se o usuário tiver múltiplas contas na ID, tiver especificado a conta para pagamento na ITP e esta conta estiver válida e disponível após o login, exibi-la já selecionada por padrão.
    
-   `REQ.PG-04100` Se o usuário tiver múltiplas contas na ID, permitir que o usuário altere a conta de débito antes de confirmar a transação.
    
-   `REQ.PG-04200` Se o usuário tiver múltiplas contas na ID, exibir todas as contas aptas para seleção.
    
-   `REQ.PG-04300` Se o usuário tiver múltiplas contas na ID, indicar visualmente as contas que não estiverem aptas, com indicação clara do motivo.  
    Ex.: desabilitação visual da conta inapta com _tag_ indicando o motivo.
    
-   `REQ.PG-04400` Impedir a continuidade da jornada sem que uma conta válida seja selecionada.
    
-   `REQ.PG-04500` Manter o texto da opção de confirmação consistente, mesmo se a conta ainda não tiver sido selecionada.
    

![image-20260615-175951.png](images/image-20260615-175951.png)Fluxograma ITP > ID

Digite ou cole algo aqui para o transformar em um trecho.

![image-20251010-134700.png](images/image-20251010-134700.png)

**Atenção!**

Se resposta for negativa para alguma das perguntas do fluxograma apresentado, a Detentora não conseguirá utilizar o dado da conta de débito para facilitar a jornada.

REQ.PG-04600

**Cenário: Revisão e confirmação de transação de pagamento**

Após se autenticar, o usuário visualiza, na ID, os dados da transação informados pela ITP.

-   `REQ.PG-04600` Além das informações descritas nesta etapa, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para confirmação da transação.
    

REQ.PG-04700

-   `REQ.PG-04700` Exibir o valor do pagamento conforme informado pela ITP.
    

REQ.PG-04800

-   `REQ.PG-04800` Exibir número da agência e número da conta da conta de débito selecionada.
    

REQ.PG-04900

-   `REQ.PG-04900` Exibir a descrição do pagamento quando informada pela ITP.
    

REQ.PG-05000

-   `REQ.PG-05000` Exibir nome e CPF (mascarado ou não)/CNPJ do recebedor.
    

Nota.Recebedortrue

REQ.PG-05100

-   `REQ.PG-05100` Exibir a data do pagamento conforme informado pela ITP.
    

REQ.PG-05200

-   `REQ.PG-05200` Exibir a forma de pagamento conforme informado pela ITP.
    

REQ.PG-05300 a 05800

-   `REQ.PG-05300` Se a ID cobrar tarifa pelo serviço, exibir o valor da tarifa cobrada.
    
-   `REQ.PG-05400` À exceção de limites de crédito previamente contratados e disponíveis, não exibir ofertas de crédito durante a jornada, conforme regulação.  
    Ex.: cheque especial.
    
-   `REQ.PG-05500` Informar ao usuário que, após a confirmação, ele será redirecionado para a ITP.
    
-   `REQ.PG-05600` Permitir que, após se autenticar e revisar os dados da transação, o usuário conclua a operação com uma única confirmação.
    
-   `REQ.PG-05700` Se a instituição utilizar um método adicional de confirmação da transação, seguir o mesmo padrão utilizado fora do Open Finance.
    
-   `REQ.PG-05701` Exibir o nome da instituição responsável pela iniciação da transação de  
    pagamento.
    
-   `REQ.PG-05800` Não exibir Termos e Condições durante a confirmação de pagamento.
    

**Nota**  
Os Termos e Condições podem ser exibidos no ambiente de gestão Open Finance da ID.

![image-20260625-122054.png](images/image-20260625-122054.png)

REQ.PG-05900 a 06000

**Cenário: Interrupção da jornada**

-   `REQ.PG-05900` Permitir que o usuário interrompa a jornada antes da confirmação.
    
-   `REQ.PG-06000` Garantir que a opção de interrupção da jornada não seja visualmente mais proeminente do que a opção de prosseguir.
    

REQ.PG-06100 a 06200

-   `REQ.PG-06100` Redirecionar o usuário para a ITP se ele cancelar a operação.
    
-   `REQ.PG-06200` Redirecionar o usuário para a ITP se ele retornar manualmente à etapa anterior da jornada (por meio de botão do ambiente digital, botão do dispositivo, link clicável etc.) e não seja possível exibir a tela imediatamente anterior.
    

![image-20260616-184821.png](images/image-20260616-184821.png)

REC.PG-01600#F4F5F7

## Recomendações - ID

**Cenário: Seleção da conta de débito**

-   `REC.PG-01600` Se a ITP capturar os dados de conta do usuário, utilizá-los para facilitar a autenticação na ID, contanto que não haja prejuízo dos protocolos de segurança para autenticação seguidos pelas instituições.
    

![image-20260615-182239.png](images/image-20260615-182239.png)

REC.PG-01700

**Cenário: Exibição do saldo e limite**

-   `REC.PG-01700`Exibir o saldo da conta e, se houver limite de crédito pré-aprovado, exibir também o limite disponível para que o usuário possa avaliar a viabilidade do pagamento.
    

![image-20260616-184854.png](images/image-20260616-184854.png)REC.PG-01800 a 01900

**Cenário: Cancelamento de transação de pagamento**

-   `REC.PG-01800` Se o usuário tentar cancelar a transação, exibir uma mensagem de confirmação.    
    Ex.: Tem certeza que deseja cancelar a transação?
    
-   `REC.PG-01900` Informar ao usuário que, se a transação não puder ser concluída, ele será redirecionado ao ambiente da ITP.
    

![image-20260616-184943.png](images/image-20260616-184943.png)

* * *

# Etapa 4: Redirecionamento

760Resumo

Nesta etapa, o usuário:

-   É redirecionado da Instituição Detentora de Conta (ID) para o ambiente da Iniciadora de Transação de Pagamento (ITP).
    

A ID deve:

-   Garantir um redirecionamento seguro, automático e sem fricções.
    
-   Redirecionar o usuário para o mesmo ambiente (app ou browser) em que iniciou a jornada.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

wide760#F4F5F7

## Requisitos - ID

**Cenário: Tela de transição**

REQ.PG-06300 a 06600

-   `REQ.PG-06300` Durante o redirecionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o redirecionamento.
    
-   `REQ.PG-06400` Na tela do redirecionamento, informar que o redirecionamento está em andamento.  
    Ex.: Aguarde enquanto te redirecionamos para concluir a operação.
    
-   `REQ.PG-06500` Na tela do redirecionamento, informar que o redirecionamento é seguro.  
    Ex.: Redirecionamento com a segurança Open Finance.
    
-   `REQ.PG-06600` Na tela do redirecionamento, informar que o redirecionamento é necessário para efetivação da operação.  
    Ex.: Aguarde enquanto te redirecionamos para concluir a operação.
    

REQ.PG-06700

-   `REQ.PG-06700` Em dispositivos móveis, redirecionar o usuário diretamente para o aplicativo da ITP, sem passar por navegadores intermediários.
    

REQ.PG-06800

-   `REQ.PG-06800` Redirecionar o usuário ao mesmo ambiente da ITP utilizado no início da jornada.
    

![image-20260617-175249.png](images/image-20260617-175249.png)REC.PG-02000#F4F5F7

## Recomendações - ID

**Cenário: Tela de transição**

-   `REC.PG-02000` Utilizar elementos visuais e textuais que reforcem o direcionamento, como _loaders_, animações, barras de progresso ou indicadores visuais.
    

![image-20260609-173932.png](images/image-20260609-173932.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da transação.   
    

A ITP deve:

-   Apresentar com clareza o resultado da solicitação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da solicitação.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

![image-20260316-144316.png](images/image-20260316-144316.png)REQ.PG-06900#F4F5F7

## Requisitos - ITP

**Cenário: Efetivação de transação de pagamento**

-   `REQ.PG-06900` Além das informações descritas nesta etapa, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para efetivação da transação.
    

REQ.PG-07000

-   `REQ.PG-07000` Exibir data e hora/minuto/segundo da liquidação (horário de Brasília).
    

REQ.PG-07100

-   `REQ.PG-07100` Exibir o Id (código de identificação) do pagamento.
    

REQ.PG-07200

-   `REQ.PG-07200` Exibir o valor do pagamento.
    

REQ.PG-07300

-   `REQ.PG-07300` Exibir os dados do pagador: nome completo, CPF (mascarado)/CNPJ, nome da ID e números da agência e conta.
    

REQ.PG-07400

-   `REQ.PG-07400` Exibir os dados do recebedor: nome, CPF (mascarado ou não)/CNPJ e instituição de destino do recebedor.
    

REQ.PG-07500

-   `REQ.PG-07500` Exibir a descrição do pagamento, quando preenchida.
    

REQ.PG-07600

-   `REQ.PG-07600` Exibir a forma de pagamento.
    

REQ.PG-07700

-   `REQ.PG-07700` Se a instituição cobrar tarifa pelo serviço, exibir o valor da tarifa cobrada.
    

REQ.PG-07800

-   `REQ.PG-07800` Exibir o nome da instituição responsável pela iniciação da transação de pagamento.
    

Nota.ITP

**Nota**  
Se o usuário já estiver no ambiente da própria ITP, a exibição do nome da ITP não é obrigatória, pois a identificação já é evidente no contexto.

![image-20260615-182701.png](images/image-20260615-182701.png)

**Cenário: Interrupção da jornada**

REQ.PG-07900

-   `REQ.PG-07900` Se o usuário tiver cancelado a solicitação, exibir mensagem confirmando o cancelamento da solicitação.
    

REQ.PG-08000

-   `REQ.PG-08000` Se o usuário tiver cancelado a solicitação, exibir os dados da solicitação cancelada.
    

![image-20260316-144804.png](images/image-20260316-144804.png)REC.PG-02100#F4F5F7

## Recomendações - ITP

**Cenário: Efetivação de transação de pagamento**

-   `REC.PG-02100` Exibir o resultado da transação em tela ou através de, por exemplo, um botão. Ex.: “Ver comprovante”, “Detalhes”, “Saiba mais” etc.
    

![image-20260625-122631.png](images/image-20260625-122631.png)

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-00100`

**Texto**

Não comparar arranjos de pagamento de forma a desqualificar um deles.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-00200`

**Texto**

Mencionar o Open Finance em algum ponto visível da interface.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-00300`

**Texto**

Exibir ferramenta de busca e seleção da ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-00400`

**Texto**

Permitir que o usuário busque tanto pela marca da instituição quanto por um participante associado, exibindo corretamente a marca correspondente nos resultados.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-00500`

**Texto**

Permitir que a seleção final da ID seja feita pela marca da instituição, e não pelo nome do participante associado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-00600`

**Texto**

Exibir apenas marcas adequadas ao tipo de público identificado (PF ou PJ).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

**ID**

`REQ.PG-00700`

**Texto**

Exibir cada marca uma única vez, mesmo que existam múltiplos registros para ela no Diretório de Participantes.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Automático, Pix Saque e Pix Troco e Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-00800`

**Texto**

Além das informações descritas nesta etapa, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para solicitação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-00900`

**Texto**

Permitir que o usuário preencha ou altere o valor quando permitido pelo recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01000`

**Texto**

Exibir o valor automaticamente sem possibilidade de alteração quando determinado pelo recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-01100`

**Texto**

Se a ITP cobrar tarifa pelo serviço, exibir o valor da tarifa cobrada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01200`

**Texto**

Exibir a forma de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01300`

**Texto**

Exibir a data do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix Automático (Pagamento inicial avulso), Pix Agendado

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01400`

**Texto**

Permitir preenchimento opcional da descrição do pagamento conforme a forma de iniciação do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático (Pagamento inicial avulso), Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01500`

**Texto**

Exibir a descrição automaticamente conforme a forma de iniciação do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix Agendado, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01600`

**Texto**

Permitir que o usuário insira os dados do recebedor como instituição, agência, conta e CPF/CNPJ em pagamentos via inserção manual de dados transacionais.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01700`

**Texto**

Exibir os dados do recebedor automaticamente em pagamentos via chave Pix, Pix Copia e Cola e Pix via QR Code.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01800`

**Texto**

Exibir nome e CPF (mascarado)/CNPJ do recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Segurança e Privacidade, Transparência e Clareza- IN BCB 760

**ID**

`REQ.PG-01900`

**Texto**

Exibir o nome da ID selecionada pelo usuário, se essa etapa tiver sido apresentada antes da revisão da transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e Clareza - IN BCB 760

**ID**

`REQ.PG-02000`

**Texto**

Exibir o nome da instituição responsável pela iniciação da transação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e Clareza - IN BCB 760

**ID**

`REQ.PG-02100`

**Texto**

Informar o usuário que a transação será concluída apenas se houver saldo e limite transacional disponíveis na conta de débito.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e Clareza - IN BCB 760

**ID**

`REQ.PG-02200`

**Texto**

Se apresentar Termos e Condições, exibir o conteúdo de forma clara e objetiva.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-02300`

**Texto**

Se apresentar Termos e Condições, não utilizar _opt-in_.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA e JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e Clareza - IN BCB 760

**ID**

`REQ.PG-02400`

**Texto**

Se apresentar Termos e Condições, informar que, ao continuar, o usuário está concordando com esses termos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-02500`

**Texto**

Informar o usuário que ao continuar, ele será direcionado para a ID para confirmar a solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-02600`

**Texto**

Direcionar o usuário para um canal digital seguro.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-02700`

**Texto**

Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador) e possuir o aplicativo da ID instalado, direcioná-lo para o aplicativo da ID (hybrid flow).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-02800`

**Texto**

Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app-only_, direcioná-lo para a loja de aplicativos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-02900`

**Texto**

Se o usuário iniciar a jornada na ITP em dispositivo móvel (aplicativo ou navegador), não possuir o aplicativo da ID instalado e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o ambiente da ID no navegador ou para a loja de aplicativos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03000`

**Texto**

Se o usuário iniciar a jornada na ITP em desktop e a ID for _app-only_, direcioná-lo para o aplicativo por meio de hand-off (hybrid flow com hand-off).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03100`

**Texto**

Se o usuário iniciar a jornada na ITP em desktop e a ID for _app+browser_ ou _browser-only_, direcioná-lo para o aplicativo da ID ou para o ambiente da ID no navegador.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03200`

**Texto**

Durante o direcionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o direcionamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03300`

**Texto**

Na tela do direcionamento, informar que o direcionamento está em andamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03400`

**Texto**

Na tela do direcionamento, informar que o direcionamento é seguro.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760, Open Finance

**ID**

`REQ.PG-03500`

**Texto**

Na tela do direcionamento, informar que o usuário possui até 5 minutos para confirmar a solicitação de autorização de pagamento na ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760, Open Finance

**ID**

`REQ.PG-03600`

**Texto**

Em dispositivos móveis, direcionar o usuário diretamente para o aplicativo da ID, sem passar por navegadores intermediários.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03700`

**Texto**

Solicitar a autenticação do usuário conforme os padrões já definidos pela própria ID para operações fora do Open Finance, em conformidade com a regulação vigente.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03800`

**Texto**

Permitir que o usuário siga o fluxo padrão da  
instituição para recuperação ou criação de acesso.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-03900`

**Texto**

Não exibir etapas adicionais ou utilizar métodos mais rigorosos de autenticação não contemplados em seu canal digital a fim de desincentivar a transação, conforme a regulação vigente.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Agilidade - IN BCB 760

**ID**

`REQ.PG-04000`

**Texto**

Se o usuário tiver múltiplas contas na ID, tiver especificado a conta para pagamento na ITP e esta conta estiver válida e disponível após o login, exibi-la já selecionada por padrão.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-04100`

**Texto**

Se o usuário tiver múltiplas contas na ID, permitir que o usuário altere a conta de débito antes de confirmar a transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Agilidade, Conveniência e Controle - IN BCB 760

**ID**

`REQ.PG-04200`

**Texto**

Se o usuário tiver múltiplas contas na ID, exibir todas as contas aptas para seleção.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Agilidade, Conveniência e Controle - IN BCB 760, Prevenção de erro

**ID**

`REQ.PG-04300`

**Texto**

Se o usuário tiver múltiplas contas na ID, indicar visualmente as contas que não estiverem aptas, com indicação clara do motivo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Agilidade, Conveniência e Controle - IN BCB 760, Prevenção de erro

**ID**

`REQ.PG-04400`

**Texto**

Impedir a continuidade da jornada sem que uma conta válida seja selecionada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-04500`

**Texto**

Manter o texto da opção de confirmação consistente, mesmo se a conta ainda não tiver sido selecionada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-04600`

**Texto**

Além das informações descritas nesta etapa, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para confirmação da transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-04700`

**Texto**

Exibir o valor do pagamento conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04800`

**Texto**

Exibir número da agência e número da conta da conta de débito selecionada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático (Pagamento inicial avulso), Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-04900`

**Texto**

Exibir a descrição do pagamento quando informada pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05000`

**Texto**

Exibir nome, CPF (mascarado ou não)/CNPJ do recebedor.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático (Pagamento inicial avulso), Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05100`

**Texto**

Exibir a data do pagamento conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05200`

**Texto**

Exibir a forma de pagamento conforme informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05300`

**Texto**

Se a ID cobrar tarifa pelo serviço, exibir o valor da tarifa cobrada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-05400`

**Texto**

À exceção de limites de crédito previamente contratados e disponíveis, não exibir ofertas de crédito durante a jornada, conforme regulação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-05500`

**Texto**

Informar ao usuário que, após a confirmação, ele será redirecionado para a ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-05600`

**Texto**

Permitir que, após se autenticar e revisar os dados da transação, o usuário conclua a operação com uma única confirmação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-05700`

**Texto**

Se a instituição utilizar um método adicional de confirmação da transação, seguir o mesmo padrão utilizado fora do Open Finance.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-05701`

**Texto**

Exibir o nome da instituição responsável pela iniciação da transação de  
pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-05800`

**Texto**

Não exibir Termos e Condições durante a confirmação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05900`

**Texto**

Permitir que o usuário interrompa a jornada antes da confirmação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-06000`

**Texto**

Garantir que a opção de interrupção da jornada não seja visualmente mais proeminente do que a opção de prosseguir.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Agilidade - IN BCB 760

**ID**

`REQ.PG-06100`

**Texto**

Redirecionar o usuário para a ITP se ele cancelar a operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Agilidade - IN BCB 760

**ID**

`REQ.PG-06200`

**Texto**

Redirecionar o usuário para a ITP se ele retornar manualmente à etapa anterior da jornada (por meio de botão do ambiente digital, botão do dispositivo, link clicável etc.) e não seja possível exibir a tela imediatamente anterior.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06300`

**Texto**

Durante o redirecionamento, exibir uma tela informativa, sem exigir ação adicional do usuário para confirmar o redirecionamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06400`

**Texto**

Na tela do redirecionamento, informar que o redirecionamento está em andamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06500`

**Texto**

Na tela do redirecionamento, informar que o redirecionamento é seguro.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06600`

**Texto**

Na tela do redirecionamento, informar que o redirecionamento é necessário para efetivação da operação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06700`

**Texto**

Em dispositivos móveis, redirecionar o usuário diretamente para o aplicativo da ITP, sem passar por navegadores intermediários.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06800`

**Texto**

Redirecionar o usuário ao mesmo ambiente da ITP utilizado no início da jornada (aplicativo móvel ou ambiente desktop).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-06900`

**Texto**

Além das informações descritas nesta etapa, exibir quaisquer outras informações exigidas pelo arranjo de pagamento para efetivação da transação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático (Pagamento inicial avulso), Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07000`

**Texto**

Exibir data e hora/minuto/segundo da liquidação (horário de Brasília).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07100`

**Texto**

Exibir o Id (código de identificação) do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07200`

**Texto**

Exibir o valor do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07300`

**Texto**

Exibir os dados do pagador: nome completo, CPF (mascarado)/CNPJ, nome da ID e números da agência e conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07400`

**Texto**

Exibir os dados do recebedor: nome, CPF (mascarado)/CNPJ, nome da ID e números da agência e conta.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático (Pagamento inicial avulso), Pix Agendado, Pix Saque e Pix Troco

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07500`

**Texto**

Exibir a descrição do pagamento, quando preenchida.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07600`

**Texto**

Exibir a forma de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07700`

**Texto**

Se a instituição cobrar tarifa pelo serviço, exibir o valor da tarifa cobrada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP, ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07800`

**Texto**

Exibir o nome da instituição responsável pela iniciação da transação de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07900`

**Texto**

Se o usuário tiver cancelado a solicitação, exibir confirmação do cancelamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix, Pix com vencimento através de QR Code dinâmico, Pix Automático, Pix Agendado, Pix Saque e Pix Troco, Transferências Inteligentes

**Jornada**

Hybrid flow, hybrid flow com hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-08000`

**Texto**

Se o usuário tiver cancelado a solicitação, exibir os dados da solicitação cancelada.
