# v.23.00.00 Transferências Inteligentes via hybrid flow

# Visão geral

A jornada de Transferências Inteligentes com Pix ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração de uma autorização de pagamentos automáticos com Pix entre contas de mesma titularidade via Open Finance.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida, com clareza sobre as próximas etapas.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, visualiza os dados da solicitação configurada na ITP e confirma.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Por fim, a ITP informa o status da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-174505.png](images/image-20260112-174505.png)

* * *

# Telas de exemplo

wide760

**Nota**  
Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Cloud Finance** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

true100%600

## Fluxo de telas

![image-20260623-174131.png](images/image-20260623-174131.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de Transferências Inteligentes com Pix via Open Finance

# Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação
    

## Cenário de referência

-   Autorização de Transferências Inteligentes com Pix
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

> Jornadas que envolvam o compartilhamento de saldo e limite via Jornada Otimizada, múltiplos aprovadores, troca de dispositivo e transações temporizadas devem observar as regras específicas previstas nas páginas correspondentes.

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de pagamento com Pix via Transferências Inteligentes no Open Finance.
    
-   Escolhe a Instituição Detentora da Conta (ID) que será usada para realizar o pagamento.
    
-   É informado sobre os gatilhos (manuais ou automáticos) que disparam as transferências conforme disponibilizado pela Instituição Iniciadora de Transação de Pagamento (ITP).
    
-   Se desejar, estabelece limites para as transferências .  
    
-   Revisa os dados da solicitação,
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

REQ.PG-00100 a 00200true

![image-20260623-183948.png](images/image-20260623-183948.png)

REQ.PG-00300 a 00700true

![image-20260623-144327.png](images/image-20260623-144327.png)

REQ.PG-00800true

REQ.PG-00801

-   `REQ.PG-00801` Exibir os gatilhos/objetivos de transferências com clareza.     
    Exs.:
    
    -   Para trazer dinheiro de outra conta.
        
    -   Para garantir saldo em suas outras contas. 
        
    -   Para o pagamento de lançamentos futuros que estiverem agendados. 
        
    -   Para programar investimentos em determinados produtos regularmente.
        

**Atenção!**

Os gatilhos/objetivos de transferências automáticas são definidos conforme a estratégia/casos de uso da ITP e não são enviados à ID.

REQ.PG-00802

-   `REQ.PG-00802` Para as transferências realizadas sem a presença do usuário no ambiente da ITP, ou seja, transferências automáticas, informar o usuário que as movimentações acontecerão automaticamente dentro dos parâmetros e limites estabelecidos para atender o caso de uso informado.
    

![image-20260623-184038.png](images/image-20260623-184038.png)

REQ.PG-00803

-   `REQ.PG-00803` Informar ao usuário que apenas contas de mesma titularidade serão definidas como contas recebedoras.
    
    -   Para pessoas físicas, as contas devem estar vinculadas ao mesmo nome e CPF. 
        
    -   Para pessoas jurídicas, as contas devem estar vinculadas à mesma razão social e à mesma raiz de CNPJ.
        

**Nota**  
O momento de definição das informações da instituição e das contas recebedoras fica a critério da ITP, com a possibilidade de utilização de chave Pix ou inserção manual dos dados transacionais da conta recebedora.

![image-20260623-144930.png](images/image-20260623-144930.png)REQ.PG-00804

-   `REQ.PG-00804` Permitir a definição de limites por transferência, por autorização e/ou por períodos (Diário, Semanal, Mensal ou Anual).
    

REQ.PG-00805

-   `REQ.PG-00805` Permitir definição de mais de um limite periódico ao mesmo tempo.   
    
    Ex.:  
    \- Limite por transferência de R$1000,00.  
    \- Llimite diário de R$5000,00.
    

REQ.PG-00806

-   `REQ.PG-00806` Permitir definição de limite total por valor e/ou número de transferências.
    

REQ.PG-00807

-   `REQ.PG-00807` Informar que os limites transacionais definidos na ID (conta pagadora) prevalecem sobre os limites definidos na ITP.  
    
    Ex.: Os limites definidos aqui estão sujeitos aos limites da sua conta.
    

![image-20260623-145033.png](images/image-20260623-145033.png)

REQ.PG-00808

-   `REQ.PG-00808` Exibir a descrição da autorização, em casos de uso em que as transferências sejam automáticas, ou seja, ocorram sem a presença do usuário e sejam disparadas a partir do(s) gatilho/objetivo(s) previamente definido(s)/selecionado(s).  
    Ex.: Gestão Financeira Inteligente.
    

![image-20260623-145248.png](images/image-20260623-145248.png)

REQ.PG-00809

-   `REQ.PG-00809` Permitir a definição da data de validade da autorização, inclusive com opção de prazo indeterminado.
    

REQ.PG-00810

-   `REQ.PG-00810` Se o usuário tiver definido um limite total para a autorização, informá-lo que a autorização irá expirar quando esse limite for atingido.    
    Ex.: Essa autorização irá expirar quando este valor/número de transferências for atingido.
    

![image-20260623-145351.png](images/image-20260623-145351.png)REQ.PG-00811

-   `REQ.PG-00811` Para casos de uso que prevejam transferências em datas específicas, informar ao usuário que pagamentos agendados para datas inexistentes (Ex.: Dias 29, 30 e 31 de determinados meses) poderão ser efetivados em data anterior ou posterior à data agendada.
    

![image-20260623-145423.png](images/image-20260623-145423.png)REQ.PG-00812

-   `REQ.PG-00812` Se a ITP limitar o número de transferências diárias, informar este limite ao usuário de forma clara.
    

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01900true

REQ.PG-02000true

![image-20260623-184154.png](images/image-20260623-184154.png)

REQ.PG-02200 a 02400true

REQ.PG-02500true

![image-20260623-150650.png](images/image-20260623-150650.png)

REC.PG-00100true

![image-20260623-161626.png](images/image-20260623-161626.png)

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260623-174049.png](images/image-20260623-174049.png)

REC.PG-00800 a 00900true

![image-20260623-161834.png](images/image-20260623-161834.png)

REC.PG-01000true

REC.PG-01200true

REC.PG-01300true

![image-20260623-171223.png](images/image-20260623-171223.png)

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

REQ.PG-03401true

REQ.PG-03600true

![image-20260623-162446.png](images/image-20260623-162446.png)

wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01400true

REC.PG-01500true

![image-20260623-162655.png](images/image-20260623-162655.png)

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
    
-   Comunicar o resultado da autorização à ITP.
    
-   Enviar notificações ao usuário e aos demais aprovadores nos cenários de múltiplos aprovadores.
    

![image-20260623-204701.png](images/image-20260623-204701.png)

REQ.PG-03700 a 03900true

![image-20260615-180041.png](images/image-20260615-180041.png)

REQ.PG-04000 a 04500true

![image-20260623-164310.png](images/image-20260623-164310.png)

Fluxograma ITP > IDtrue

REQ.PG-04600true

REQ.PG-04601 a 04602

-   `REQ.PG-04601` Exibir a descrição da autorização, quando informada pela ITP.
    
-   `REQ.PG-04602` Exibir os limites transacionais, quando informados pela ITP.
    

REQ.PG-04603

-   `REQ.PG-04603` Exibir a data de início e a data de validade da autorização de acordo com o parâmetro definido pelo usuário, seja por uma data específica, por prazo indeterminado ou pela condição de atingimento de um limite previamente estabelecido.
    

![image-20260624-143715.png](images/image-20260624-143715.png)

REQ.PG-04604 a 04605

-   `REQ.PG-04604` Se os limites definidos na ITP forem superiores aos limites da conta na ID, exibir mensagem informando que a efetivação das transferências estará condicionada ao ajuste dos limites.     
    Ex.: Esse limite é maior que seu limite Pix diário. Acesse a área “Limites Pix” para ajustar e garantir a transferência.
    
-   `REQ.PG-04605` Se a autorização incluir um valor fixo (Ex. Transferir R$ 500,00 da conta X para a conta Y todo dia 10), e no momento da confirmação, a ID identificar insuficiência de saldo na conta selecionada, exibir mensagem informando que a efetivação das transferências estará condicionada à recomposição do saldo.   
    
    Ex.: Você não possui saldo suficiente na sua conta. Adicione saldo até a data programada para garantir a transferência.
    

![image-20260623-163823.png](images/image-20260623-163823.png)

REQ.PG-04702true

REQ.PG-04800true

REQ.PG-04801true

REQ.PG-05200true

REQ.PG-05300 a 05800true

REQ.PG-05801

-   `REQ.PG-05801` Impossibilitar a alteração de parâmetros da autorização configurados na ITP.
    

![image-20260623-164209.png](images/image-20260623-164209.png)

REC.PG-01600true

REC.PG-01700true

![image-20260623-164508.png](images/image-20260623-164508.png)

REC.PG-01800 a 01900true

![image-20260623-165022.png](images/image-20260623-165022.png)

* * *

# Etapa 4: Redirecionamento

760Resumo

Nesta etapa, o usuário:

-   É redirecionado da Instituição Detentora de Conta (ID) para o ambiente da Iniciadora de Transação de Pagamento (ITP).
    

A ID deve:

-   Garantir um redirecionamento seguro, automático e sem fricções.
    
-   Redirecionar o usuário para o mesmo ambiente (app ou browser) em que iniciou a jornada.  
    
-   Quando aplicável, exibir mensagens de erro ou pendências, como autorizações em múltiplas alçadas ou indisponibilidade momentânea dos sistemas.
    

REQ.PG-06300 a 06600true

REQ.PG-06700true

REQ.PG-06800true

![image-20260623-165243.png](images/image-20260623-165243.png)

REC.PG-02000true

![image-20260624-193452.png](images/image-20260624-193452.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado da solicitação.   
    

A ITP deve:

-   Apresentar com clareza o resultado da solicitação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar um comprovante com os principais dados da solicitação.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

![image-20260623-205224.png](images/image-20260623-205224.png)

REQ.PG-06900true

REQ.PG-06901true

REQ.PG-06904true

REQ.PG-07203true

REQ.PG-07300 true

REQ.PG-07400true

wide760

**Nota**

Como as Transferências Inteligentes ocorrem exclusivamente entre contas de mesma titularidade, a ITP pode, se desejar, exibir as informações de identificação do pagador e do recebedor de forma consolidada no comprovante.

Ex.:  
Titular  
Maria da Silva

\*\*\*.222.333-\*\*.

REQ.PG-07600true

REQ.PG-07601

-   `REQ.PG-07601` Exibir informações referentes às contas recebedoras e/ou ao acesso ao ambiente de gestão de contas recebedoras para a autorização específica, quando aplicável.
    

REQ.PG-07602

-   `REQ.PG-07602` Exibir a descrição dos gatilhos/objetivos de transferência.
    

REQ.PG-07603

-   `REQ.PG-07603` Exibir os limites transacionais, quando preenchidos.
    

REQ.PG-07604

-   `REQ.PG-07604` Exibir a data de início e data de validade da autorização conforme o parâmetro definido pelo usuário, seja por uma data específica, por prazo indeterminado ou pela condição de atingimento de um limite previamente estabelecido.
    

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

REQ.PG-07802true

REQ.PG-07803true

REQ.PG-07812true

REQ.PG-07810true

![image-20260826-190717.png](images/image-20260826-190717.png)

**Cenário: Interrupção da jornada**

REQ.PG-07900true

REQ.PG-08000true

![image-20260623-170837.png](images/image-20260623-170837.png)

REC.PG-02100true

REC.PG-02102true

Ex.: Você pode cancelar essa autorização a qualquer momento.

![image-20260826-190841.png](images/image-20260826-190841.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-00801`

**Texto**

Exibir os gatilhos/objetivos de transferências com clareza.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-00802`

**Texto**

Para as transferências realizadas sem a presença do usuário no ambiente da ITP, ou seja, transferências automáticas, informar o usuário que as movimentações acontecerão automaticamente dentro dos parâmetros e limites estabelecidos para atender o caso de uso informado.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza - IN BCB 760

**ID**

`REQ.PG-00803`

**Texto**

Informar ao usuário que apenas contas de mesma titularidade serão definidas como contas recebedoras.

-   Para pessoas físicas, as contas devem estar vinculadas ao mesmo nome e CPF. 
    
-   Para pessoas jurídicas, as contas devem estar vinculadas à mesma razão social e à mesma raiz de CNPJ.
    

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-00804`

**Texto**

Permitir a definição de limites por transferência, por autorização e/ou por períodos (Diário, Semanal, Mensal ou Anual).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-00805`

**Texto**

Permitir definição de mais de um limite periódico ao mesmo tempo.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-00806`

**Texto**

Permitir definição de limite total por valor e/ou número de transferências.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-00807`

**Texto**

Informar que os limites transacionais definidos na ID (conta pagadora) prevalecem sobre os limites definidos na ITP.  true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-00808`

**Texto**

Exibir a descrição da autorização, em casos de uso em que as transferências sejam automáticas, ou seja, ocorram sem a presença do usuário e sejam disparadas a partir do(s) gatilho/objetivo(s) previamente definido(s)/selecionado(s).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-00809`

**Texto**

Permitir a definição da data de validade da autorização, inclusive com opção de prazo indeterminado.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-00810`

**Texto**

Se o usuário tiver definido um limite total para a autorização, informá-lo que a autorização irá expirar quando esse limite for atingido.  true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-00811`

**Texto**

Para casos de uso que prevejam transferências em datas específicas, informar ao usuário que pagamentos agendados para datas inexistentes (Ex.: Dias 29, 30 e 31 de determinados meses) poderão ser efetivados em data anterior ou posterior à data agendada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-00812`

**Texto**

Se a ITP limitar o número de transferências diárias, informar este limite ao usuário de forma clara.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-04601`

**Texto**

Exibir a descrição da autorização quando informada pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-04602`

**Texto**

Exibir os limites transacionais quando informados pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-04603`

**Texto**

Exibir a data de início e a data de validade da autorização de acordo com o parâmetro definido pelo usuário, seja por uma data específica, por prazo indeterminado ou pela condição de atingimento de um limite previamente estabelecido.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-04604`

**Texto**

Se os limites definidos na ITP forem superiores aos limites da conta na ID, exibir mensagem informando que a efetivação das transferências estará condicionada ao ajuste dos limites.   trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-04605`

**Texto**

Se a autorização incluir um valor fixo (Ex. Transferir R$ 500,00 da conta X para a conta Y todo dia 10), e no momento da confirmação, a ID identificar insuficiência de saldo na conta selecionada, exibir mensagem informando que a efetivação das transferências estará condicionada à recomposição do saldo.   true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow e Hybrid Flow com Hand-off

**Proposta**

**Instituição**

ID

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-05801`

**Texto**

Impossibilitar a edição de parâmetros da autorização configurados na ITP.  
Ex.: Limites transacionais.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07601`

**Texto**

Exibir informações referentes às contas recebedoras e/ou ao acesso ao ambiente de gestão de contas recebedoras para a autorização específica, quando aplicável.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07603`

**Texto**

Exibir os limites transacionais, quando preenchidos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Transferências Inteligentes

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Transparência e clareza, Conveniência e controle, Segurança e privacidade - IN BCB 760

**ID**

`REQ.PG-07604`

**Texto**

Exibir a data de início e data de validade da autorização conforme o parâmetro definido pelo usuário, seja por uma data específica, por prazo indeterminado ou pela condição de atingimento de um limite previamente estabelecido
