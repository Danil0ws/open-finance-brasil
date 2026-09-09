# v.23.00.00 Pix Saque e Pix Troco via hybrid flow

# Visão geral

A Jornada de Iniciação de Pagamento com **Pix Saque e Pix Troco** ocorre quando:

1.  O usuário lê o QR Code com as informações do pagamento e a Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para que o usuário realize uma transação de pagamento imediato com Pix via Open Finance com finalidade de saque ou troco.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida, com clareza sobre as próximas etapas.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, visualiza os dados da transação configurada na ITP e confirma o pagamento.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Por fim, a ITP informa o status da solicitação de pagamento, concluindo a jornada.
    

![image-20260306-134434.png](images/image-20260306-134434.png)

* * *

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela **Wiscredi** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%600

* * *

## Fluxo de telas

![image-20260623-142153.png](images/image-20260623-142153.png)![image-20260623-142233.png](images/image-20260623-142233.png)

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamento imediato com finalidade de saque e troco com Pix via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação
    

## Cenário de referência

-   Pagamento imediato com Pix Saque ou Pix Troco.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

> Jornadas que envolvam troca de dispositivo e transações temporizadas devem observar as regras específicas previstas nas páginas correspondentes.

wide760

**Atenção!**

A jornada de **Pix Saque e Pix Troco** não suporta pagamentos com múltiplos aprovadores.

Consulte a página **Casos de erro de Pix Saque e Pix Troco** para mais informações sobre os possíveis erros e como comunicá-los ao usuário durante a jornada.

Nota.Regulamentação e Arranjotrue

* * *

#   
Etapa 1: Solicitação

![image-20260306-135435.png](images/image-20260306-135435.png)760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento com Pix Saque e Pix Troco via Open Finance.
    
-   Escolhe a Instituição Detentora de Conta (ID) que será usada para realizar o pagamento.
    
-   Lê o QR Code fornecido pelo recebedor (agente de saque ou participante).
    
-   Define e revisa os dados da transação conforme as regras da forma de iniciação selecionada.
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-00100 a 00200true

![image-20260622-204554.png](images/image-20260622-204554.png)

REQ.PG-00300 a 00700true

![image-20260622-204757.png](images/image-20260622-204757.png)REQ.PG-00708 a 00710**Cenário: Onboarding de Pix Saque e Pix Troco**

-   `REQ.PG-00708` Se a ITP decidir disponibilizar onboarding, exibir as informações mínimas sobre o serviço de Pix Saque e Pix Troco via Open Finance conforme exigido pelo arranjo de pagamento.
    
-   `REQ.PG-00709` Além das informações mínimas exigidas pelo arranjo de pagamento para onboarding de Pix Saque e Pix Troco, informar que o pagamento pode estar sujeito a cobrança de tarifa pela ID.
    
-   `REQ.PG-00710` Além das informações mínimas exigidas pelo arranjo de pagamento para onboarding de Pix Saque e Pix Troco, informar que eventual tarifa cobrada pela ID pode ser consultada no comprovante do pagamento disponibilizado pela ID.  ![image-20260622-181612.png](images/image-20260622-181612.png)REQ.PG-00711

**Cenário: Consulta aos locais que ofertam o serviço de Pix Saque e Pix Troco**

-   `REQ.PG-00711` Se a ITP disponibilizar a funcionalidade de consulta aos locais que ofertam Pix Saque e Pix Troco, exibir as informações mínimas sobre a funcionalidade conforme exigido pelo arranjo de pagamento.
    

![image-20260622-181833.png](images/image-20260622-181833.png)

  
REQ.PG-00800true

REQ.PG-00900true

REQ.PG-01000true

![image-20260622-181700.png](images/image-20260622-181700.png)

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01300true

REQ.PG-01500true

![image-20260622-182733.png](images/image-20260622-182733.png)

REQ.PG-01700true

REQ.PG-01800true

Nota.Recebedortrue

![image-20260622-182951.png](images/image-20260622-182951.png)

REQ.PG-01900true

REQ.PG-02000true

![image-20260622-183032.png](images/image-20260622-183032.png)

REQ.PG-02100true

REQ.PG-02101 a 02102-   `REQ.PG-02101` Informar que o pagamento pode estar sujeito a cobrança de tarifa pela ID.
    
-   `REQ.PG-02102` Informar que eventual tarifa cobrada pela ID pode ser consultada no comprovante do pagamento disponibilizado pela ID.  

REQ.PG-02200 a 02400true

REQ.PG-02500true

![image-20260622-183255.png](images/image-20260622-183255.png)

REC.PG-00100true

![image-20260622-183533.png](images/image-20260622-183533.png)

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00501 a 00504

-   `REC.PG-00501` No onboarding, destacar visualmente a informação de que o agente de saque não pode cobrar taxa pela prestação do serviço.
    
-   `REC.PG-00502` No onboarding, destacar visualmente a informação de que a transação está sujeita a cobrança de tarifa pela ID.
    
-   `REC.PG-00503` No onboarding, destacar visualmente a informação de que a consulta de eventual tarifa cobrada pela ID pode ser feita no comprovante da transação disponibilizado pela ID.
    
-   `REC.PG-00504` No onboarding, destacar visualmente a informação de que a consulta aos limites de saques gratuitos deve ser feita no ambiente da ID.
    

![image-20260622-183829.png](images/image-20260622-183829.png)

REC.PG-00600true

![image-20260622-184017.png](images/image-20260622-184017.png)REC.PG-00601

**Cenário: Consulta aos locais que ofertam o serviço de Pix Saque e Pix Troco**

-   `REC.PG-00601` Nos detalhes dos locais que ofertam Pix Saque e Pix Troco, informar com destaque que o agente de saque não pode cobrar taxa pela prestação do serviço.  
    Ex.: Nenhuma taxa adicional pode ser cobrada pelo serviço.
    

![image-20260622-184120.png](images/image-20260622-184120.png)

REC.PG-00602 a 00606

**Cenário: Solicitação de transação de pagamento**

-   `REC.PG-00602` Na solicitação do pagamento, destacar visualmente a informação de que o agente de saque não pode cobrar taxa pela prestação do serviço.
    
-   `REC.PG-00603` Na solicitação do pagamento, destacar visualmente a informação de que a transação está sujeita a cobrança de tarifa pela ID.
    
-   `REC.PG-00604` Na solicitação do pagamento, destacar visualmente a informação de que a consulta de eventual tarifa cobrada pela ID pode ser feita no comprovante da transação disponibilizado pela ID.
    
-   `REC.PG-00605` Na solicitação do pagamento, destacar visualmente a informação de que a consulta aos limites de saques gratuitos deve ser feita no ambiente da ID.
    
-   `REC.PG-00606` Na solicitação do pagamento com a finalidade de troco, exibir com destaque:
    
    -   Valor da compra.
        
    -   Valor do troco.
        
    -   Valor total (compra + troco)
        

![image-20260622-184855.png](images/image-20260622-184855.png)

REC.PG-00700true

![image-20260624-181233.png](images/image-20260624-181233.png)

REC.PG-00800 a 00900true

REC.PG-01000true

REc.PG-01100true

![image-20260622-185150.png](images/image-20260622-185150.png)

REC.PG-01200true

![image-20260623-171626.png](images/image-20260623-171626.png)

REC.PG-01300true

![image-20260622-185350.png](images/image-20260622-185350.png)

* * *

# Etapa 2: Direcionamento

760Resumo

Nesta etapa, o usuário:

-   É direcionado da Iniciadora (ITP) para a sua Detentora de Conta (ID).
    

A ITP deve:

-   Orientar o usuário sobre o direcionamento.
    
-   Assegurar que a navegação ocorra de forma transparente, conforme o dispositivo utilizado.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-02600 a 03100true

REQ.PG-03200 a 03400true

REQ.PG-03500true

REQ.PG-03600true

![image-20260622-185911.png](images/image-20260622-185911.png)

wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01400true

REC.PG-01500true

![image-20260622-190053.png](images/image-20260622-190053.png)

* * *

# Etapa 3: Confirmação

760Resumo

Nesta etapa, o usuário:

-   Se autentica na Instituição Detentora de Conta (ID).
    
-   Em caso de múltiplas contas de débito, pode escolher a que deseja usar para fazer o pagamento.
    
-   Revisa as informações do pagamento enviadas pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Confirma a solicitação.  
    

A ID deve:

-   Garantir um ambiente seguro para autenticação.
    
-   Exibir o resumo da solicitação.
    
-   Permitir a edição da conta de débito, em caso de múltiplas contas.
    
-   Viabilizar a confirmação com o mínimo de fricção.   
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    
-   Comunicar o resultado da solicitação à ITP.
    
-   Enviar notificações ao usuário e aos demais aprovadores nos cenários de múltiplos aprovadores.
    

![image-20260622-193616.png](images/image-20260622-193616.png)

REQ.PG-03700 a 03900true

![image-20260615-180041.png](images/image-20260615-180041.png)

REQ.PG-04000 a 04500true

![image-20260622-193337.png](images/image-20260622-193337.png)

Fluxograma ITP > IDtrue

REQ.PG-04600true

REQ.PG-04700true

REQ.PG-04800true

REQ.PG-04900true

REQ.PG-05000true

Nota.Recebedortrue

![image-20260622-193821.png](images/image-20260622-193821.png)

REQ.PG-05100true

REQ.PG-05200true

REQ.PG-05300 a 05800true

![image-20260622-194007.png](images/image-20260622-194007.png)

REQ.PG-05900 a 06000true

![image-20260622-194110.png](images/image-20260622-194110.png)

REQ.PG-06100 a 06200true

REC.PG-01600true

![image-20260615-182239.png](images/image-20260615-182239.png)

REC.PG-01700true

![image-20260622-194327.png](images/image-20260622-194327.png)REC.PG-01703 a 01707

**Cenário: Revisão e confirmação da transação de pagamento**

-   `REC.PG-01703` Na revisão do pagamento, destacar visualmente a informação de que o agente de saque não pode cobrar taxa pela prestação do serviço.
    
-   `REC.PG-01704` Quando o valor da tarifa não puder ser apresentado antes da confirmação, informar com destaque as condições que podem gerar cobrança.  
    Ex.: Caso essa transação seja passível de tarifação, será cobrada uma tarifa de R$ 0,20. Consulte o comprovante na área de gestão.
    
-   `REC.PG-01705` Na revisão do pagamento, quando possível, informar com destaque a quantidade de saques gratuitos restantes no mês vigente.  
    Ex.: Você ainda tem 1 de 4 saques gratuitos esse mês. A partir do 5º saque, será cobrada uma taxa de R$ 0,20 por saque.
    
-   `REC.PG-01706` Na revisão do pagamento, orientar o usuário a consultar o valor efetivamente cobrado no comprovante disponibilizado pela ID.  
    Ex.: Consulte o comprovante do pagamento para visualizar a (eventual) cobrança
    
-   `REC.PG-01707` Na revisão do pagamento com a finalidade de troco, exibir com destaque:
    
    -   Valor da compra.
        
    -   Valor do troco.
        
    -   Valor total (compra + troco)
        

![image-20260622-194938.png](images/image-20260622-194938.png)

REC.PG-01800 a 01900true

![image-20260624-181635.png](images/image-20260624-181635.png)

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

REQ.PG-06300 a 06600true

REQ.PG-06700true

REQ.PG-06800true

![image-20260622-195354.png](images/image-20260622-195354.png)

REC.PG-02000true

![image-20260622-195428.png](images/image-20260622-195428.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da transação.   
    

A ITP deve:

-   Apresentar com clareza o resultado da transação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar os detalhes da transação e acesso ao comprovante.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

![image-20260623-210656.png](images/image-20260623-210656.png)

REQ.PG-06900true

REQ.PG-07000true

REQ.PG-07100true

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07301 a 07302

-   `REQ.PG-07301` Informar que a transação pode ter sido tarifada pela ID.  
    
-   `REQ.PG-07302` Informar que eventual tarifa cobrada pela ID pode ser consultada no comprovante do pagamento disponibilizado pela ID. 
    
    Ex.: Se o limite de saques gratuitos foi ultrapassado, seu banco pode ter cobrado uma taxa. Consulte o comprovante no app do seu banco.
    

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

![image-20260623-142008.png](images/image-20260623-142008.png)

**Cenário: Interrupção da jornada**

REQ.PG-07900true

REQ.PG-08000true

![image-20260622-200313.png](images/image-20260622-200313.png)

REC.PG-02100true

REC.PG-02103 a 02104

-   `REC.PG-02103` Destacar visualmente a informação de que o pagamento pode ter sido tarifado pela ID.
    
-   `REC.PG-02104` Destacar visualmente a informação de que a consulta de eventual tarifa cobrada pela ID pode ser feita no comprovante do pagamento disponibilizado pela ID.
    

![image-20260622-201144.png](images/image-20260622-201144.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR

**Proposta**

PUX - 275

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 637

**ID**

`REQ.PG-00708`

**Texto**

Se a ITP decidir disponibilizar onboarding, exibir as informações mínimas sobre o serviço de Pix Saque e Pix Troco via Open Finance conforme exigido pelo arranjo de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR

**Proposta**

PUX - 275

**Instituição**

ITP

**Justificativa**

Teste de usabilidade, Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 637

**ID**

`REQ.PG-00709`

**Texto**

Além das informações mínimas exigidas pelo arranjo de pagamento para onboarding de Pix Saque e Pix Troco, informar que o pagamento pode estar sujeito a cobrança de tarifa pela ID.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR

**Proposta**

PUX - 275

**Instituição**

ITP

**Justificativa**

Teste de usabilidade, Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 637

**ID**

`REQ.PG-00710`

**Texto**

Além das informações mínimas exigidas pelo arranjo de pagamento para onboarding de Pix Saque e Pix Troco, informar que eventual tarifa cobrada pela ID pode ser consultada no comprovante do pagamento disponibilizado pela ID. true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR

**Proposta**

PUX - 275

**Instituição**

ITP

**Justificativa**

Teste de usabilidade, Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 637

**ID**

`REQ.PG-00711`

**Texto**

Se a ITP disponibilizar a funcionalidade de consulta aos locais que ofertam Pix Saque e Pix Troco, exibir as informações mínimas sobre a funcionalidade conforme exigido pelo arranjo de pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR e Gestão

**Proposta**

PUX - 275

**Instituição**

ITP

**Justificativa**

Teste de usabilidade, Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 637

**ID**

`REQ.PG-07301`

**Texto**

Informar que a transação pode ter sido tarifada pela ID.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Saque e Pix Troco

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA e JSR e Gestão

**Proposta**

PUX - 275

**Instituição**

ITP

**Justificativa**

Teste de usabilidade, Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 637

**ID**

`REQ.PG-07302`

**Texto**

Informar que eventual tarifa cobrada pela ID pode ser consultada no comprovante do pagamento disponibilizado pela ID.
