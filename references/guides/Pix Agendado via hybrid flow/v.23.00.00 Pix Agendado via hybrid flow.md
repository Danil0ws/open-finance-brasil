# v.23.00.00 Pix Agendado via hybrid flow

# Visão geral

A Jornada de Iniciação de Pagamento com Pix Agendado ocorre quando:

1.  A Instituição Iniciadora de Transação de Pagamento (ITP) coleta as informações necessárias para configuração do agendamento único ou recorrente com Pix via Open Finance.
    
2.  Após revisar os dados, o usuário é informado sobre o direcionamento para o ambiente da Instituição Detentora de Conta (ID) escolhida, com clareza sobre as próximas etapas.
    
3.  No ambiente da ID, o usuário se autentica conforme os padrões de segurança da instituição, visualiza os dados da transação configurada na ITP e confirma o pagamento.
    
4.  Em seguida, o usuário é redirecionado para a ITP com segurança e agilidade.
    
5.  Por fim, a ITP informa o status da solicitação de pagamento, concluindo a jornada.
    

![image-20260112-173259.png](images/image-20260112-173259.png)

* * *

# Telas de exemplo

wide760

**Nota**

Nas interfaces ilustrativas, a Instituição Iniciadora de Transação de Pagamento (ITP) é representada pela marca **Wiscredi** e a Instituição Detentora de Conta (ID) é representada pela marca **Bratech**.

## Protótipo navegável

100%600

## Fluxo de telas

![image-20260413-140843.png](images/image-20260413-140843.png)

* * *

# Requisitos e recomendações

Esta seção reúne os requisitos e recomendações aplicáveis à jornada de pagamento agendado (único ou recorrente) com Pix via Open Finance.

## Etapas da jornada

1.  Solicitação
    
2.  Direcionamento
    
3.  Confirmação
    
4.  Redirecionamento
    
5.  Efetivação
    

## Cenário de referência

-   Agendamento (único ou recorrente) com Pix.
    
-   Alçada simples.
    
-   Redirecionamento entre instituições no mesmo dispositivo.
    

Variações da jornadatrue

Nota.Regulamentação e Arranjotrue

* * *

# Etapa 1: Solicitação

760Resumo

Nesta etapa, o usuário:

-   Inicia a jornada de agendamento com Pix via Open Finance.
    
-   Escolhe a Instituição Detentora de Conta (ID) que será usada para realizar o pagamento.
    
-   Insere e revisa os dados da solicitação conforme as regras da forma de iniciação selecionada. 
    

A Instituição Iniciadora de Transação de Pagamento (ITP) deve:

-   Garantir uma experiência clara, segura e informativa.
    
-   Indicar, em algum ponto da jornada, que o serviço é baseado em Open Finance.
    
-   Permitir a seleção eficiente da ID.
    
-   Validar os dados inseridos, ocultando informações sensíveis.
    
-   Preparar a solicitação de iniciação de pagamento para envio à ID.
    
-   Se houver erro, exibir mensagens claras e orientativas ao usuário.
    

###   
Métodos de iniciação com Pix

![image-20260319-194816.png](images/image-20260319-194816.png)

REQ.PG-00100 a 00200true

![image-20260618-202536.png](images/image-20260618-202536.png)

REQ.PG-00300 a 00700true

![image-20260618-202944.png](images/image-20260618-202944.png)

REQ.PG-00800true

REQ.PG-00900true

REQ.PG-01000true

REQ.PG-01100true

REQ.PG-01200true

REQ.PG-01201 a 01202

-   `REQ.PG-01201` Permitir que o usuário insira a data do agendamento único ou escolha a recorrência dos agendamentos.
    
-   `REQ.PG-01202` Informar ao usuário que pagamentos agendados para datas inexistentes (Ex.: Dias 29, 30 e 31 de determinados meses) poderão ser efetivados em data anterior ou posterior à data agendada.
    

![image-20260618-203551.png](images/image-20260618-203551.png)

REQ.PG-01203 a 01204

-   `REQ.PG-01203` Para agendamentos únicos, permitir que o usuário insira a data do pagamento dentro do período de até 24 meses a partir da data da solicitação.
    
-   `REQ.PG-01204` Exibir a data definida pelo usuário para execução do pagamento no agendamento único.
    

**Nota**  
No agendamento único, a data definida para execução do pagamento corresponde ao prazo de validade da autorização. Portanto, não se deve criar um campo adicional para exibição da validade da autorização.

![image-20260618-203749.png](images/image-20260618-203749.png)

REQ.PG-01205 a 01209

-   `REQ.PG-01205` Para agendamentos recorrentes, permitir que o usuário agende até 60 recorrências de pagamentos em uma única autorização, dentro do período de até 24 meses a partir da data de solicitação, independentemente do modelo de recorrência definido na autorização (diário, semanal, mensal ou customizado).
    
-   `REQ.PG-01206` Se o usuário definir uma data final para a recorrência, impedir a edição do número de recorrências.
    
-   `REQ.PG-01207` Se o usuário definir um número de recorrências, exibir automaticamente a data do último pagamento.
    
-   `REQ.PG-01208` Exibir a periodicidade dos agendamentos escolhida pelo usuário.
    
-   `REQ.PG-01209` Exibir as datas que definem o período da recorrência, incluindo a data de início e a data do último pagamento da recorrência.
    

**Nota**  
No agendamento recorrente, a data do último pagamento da recorrência corresponde ao prazo de validade da autorização. Portanto, não se deve criar um campo adicional para exibição da validade da autorização.

![image-20260827-133039.png](images/image-20260827-133039.png)

REQ.PG-01210

-   `REQ.PG-01210` Seguir o padrão seguinte para informar a data de encerramento e/ou número de recorrências do agendamento: 
    

**TIPO**

**ENCERRAMENTO**

**PADRÃO DE CAMPO DE TEXTO**

**EXEMPLO**

**Mensal**

Encerra após uma data.

Mensal, todo dia {número}, até {dd/mm/aa}.

Periodicidade da recorrência: Mensal, até 18/10/2024.

**Mensal**

Encerra após um número de ocorrências.

Mensal, todo dia {número}, {número ocorrências, até {dd/mm/aa}.

Periodicidade da recorrência: Mensal, todo dia 10, 2 ocorrências, até 18/12/2023.

**Semanal**

Encerra após uma data.

Semanal, toda(o) {dia da semana}, até {dd/mm/ aa}.

Periodicidade da recorrência: Semanal, toda terça-feira, até 31/12/2023.

**Semanal**

Encerra após um número de ocorrências.

Semanal, toda(o) {dia da semana}, {número} ocorrências, até {dd/mm/aa}.

Periodicidade da recorrência: Semanal, toda terça-feira, 4 ocorrências, até 31/12/2023.

**Diário**

Encerra após uma data.

Diário, até {dd/mm/aa}.

Periodicidade da recorrência: Diário, até 31/12/2023.

**Diário**

Encerra após um número de ocorrências.

Diário, {número} ocorrências, até {dd/mm/aa}.

Periodicidade da recorrência: Diário, 5 ocorrências, até 31/12/2023.

REQ.PG-01211

-   `REQ.PG-01211` Seguir o padrão seguinte para informar a data de encerramento e/ou número de recorrências do agendamento:
    

**TIPO**

**ENCERRAMENTO**

**PADRÃO DE CAMPO DE TEXTO**

**EXEMPLO**

**Customizado anual**

Encerra após uma data.

A cada {número} ano(s), até {dd/mm/aa}.

Periodicidade da recorrência: A cada 1 ano(s), até 18/10/2024. 

**Customizado anual**

Encerra após um número de ocorrências.

A cada {número} ano(s), {número} ocorrências, até {dd/mm/aa}. 

Periodicidade da recorrência: A cada 1 ano(s), 2 ocorrências, até 18/10/2024. 

**Customizado mensal**

Encerra após uma data.

A cada {número} mês(es), todo dia {número, ...}, até {dd/mm/aa}.

Periodicidade da recorrência: A cada 2 mês(es), todo dia 10 e 20, até 18/10/2024.

**Customizado mensal**

Encerra após um número de ocorrências.

A cada {número} mês(es), todo dia {número, ...}, {número} ocorrências, até {dd/mm/aa}.

Periodicidade da recorrência: A cada 2 mês(es), todo dia 10 e 20, 6 ocorrências, até 18/10/2024.

**Customizado semanal**

Encerra após uma data.

Semanalmente na {dia da semana, ...}, até {dd/ mm/aa}.

Periodicidade da recorrência: Semanalmente na terça-feira e quinta-feira, até 31/12/2023.

**Customizado semanal**

Encerra após um número de ocorrências.

Semanalmente na {dia da semana, ...}, {número} ocorrências, até {dd/mm/aa}.

Periodicidade da recorrência: Semanalmente na terça-feira e quinta-feira, 4 ocorrências, até 31/12/2023.

**Customizado diário**

Encerra após uma data.

A cada {número} dia(s), até {dd/mm/aa}.

Periodicidade da recorrência: A cada 2 dia(s), até 31/12/2023.

**Customizado diário**

Encerra após um número de ocorrências.

A cada {número} dia(s), {número} ocorrências, até {dd/mm/aa}.

Periodicidade da recorrência: A cada 2 dia(s), 5 ocorrências, até 31/12/2023.

REQ.PG-01400true

REQ.PG-01500true

REQ.PG-01600true

REQ.PG-01700true

REQ.PG-01800true

Nota.Recebedortrue

REQ.PG-01900true

REQ.PG-02000true

REQ.PG-02200 a 02400true

REQ.PG-02500true

![image-20260827-133139.png](images/image-20260827-133139.png)

REC.PG-00100true

![image-20260619-142156.png](images/image-20260619-142156.png)

**Cenário: Onboarding**

REC.PG-00200true

REC.PG-00300 a 00500true

REC.PG-00600true

![image-20260619-142423.png](images/image-20260619-142423.png)

REC.PG-00700true

![image-20260619-142631.png](images/image-20260619-142631.png)

REC.PG-00800 a 00900true

REC.PG-01000true

REc.PG-01100true

REC.PG-01200true

REC.PG-01300true

![image-20260827-133425.png](images/image-20260827-133425.png)

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

![image-20260619-143041.png](images/image-20260619-143041.png)

wide760#F4F5F7

## Recomendações - ITP

**Cenário: Tela de transição**

REC.PG-01400true

REC.PG-01500true

![image-20260619-143156.png](images/image-20260619-143156.png)

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
    

![image-20260827-133750.png](images/image-20260827-133750.png)

REQ.PG-03700 a 03900true

![image-20260619-144006.png](images/image-20260619-144006.png)

REQ.PG-04000 a 04500true

![image-20260619-144108.png](images/image-20260619-144108.png)

Fluxograma ITP > IDtrue

REQ.PG-04600true

REQ.PG-04700true

REQ.PG-04800true

REQ.PG-04900true

REQ.PG-05000true

Nota.Recebedortrue

REQ.PG-05001 a 05004

-   `REQ.PG-05001` Exibir a data do agendamento único ou do primeiro pagamento da recorrência conforme informado pela ITP.
    
-   `REQ.PG-05002` Exibir a data de validade da autorização (mesma data do agendamento único ou do último pagamento da recorrência).
    

**Nota**  
No agendamento, a data definida para execução do pagamento único ou do último pagamento da recorrência corresponde ao prazo de validade da autorização. Portanto, não se deve criar um campo adicional para exibição da validade da autorização.

-   `REQ.PG-05003` Para agendamentos recorrentes, exibir a periodicidade da recorrência (Diária, Semanal, Mensal ou Customizado).
    
-   `REQ.PG-05004` Para agendamentos recorrentes, exibir o número de recorrências, se informado pela ITP.
    

REQ.PG-05200true

REQ.PG-05201true

REQ.PG-05300 a 05800true

![image-20260827-134417.png](images/image-20260827-134417.png)

REQ.PG-05900 a 06000true

REQ.PG-06100 a 06200true

![image-20260619-181939.png](images/image-20260619-181939.png)

REC.PG-01600true

![image-20260619-182020.png](images/image-20260619-182020.png)

REC.PG-01700true

![image-20260619-182602.png](images/image-20260619-182602.png)

REQ.PG-01701 a 01702

-   `REC.PG-01701` Informar ao usuário, com destaque, que o limite disponível é inferior ao valor do pagamento agendado.
    
-   `REC.PG-01702` Se o limite disponível for inferior ao valor do pagamento agendado, orientar o usuário a ajustar o limite para garantir a efetivação do pagamento.
    
    Ex.: **Limite diário Pix Agendado: 50,00**  
    Ajuste seu limite para garantir o pagamento na data agendada.
    

![image-20260619-183248.png](images/image-20260619-183248.png)

REC.PG-01800 a 01900true

![image-20260619-183756.png](images/image-20260619-183756.png)

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

![image-20260619-185033.png](images/image-20260619-185033.png)

REC.PG-02000true

![image-20260619-185151.png](images/image-20260619-185151.png)

* * *

# Etapa 5: Efetivação

760Resumo

Nesta etapa final da jornada, o usuário:

-   É recebido no ambiente da Instituição Iniciadora de Transação de Pagamento (ITP) onde visualiza o resultado do agendamento.   
    

A ITP deve:

-   Apresentar com clareza o resultado da transação, com mensagens claras de sucesso ou falha.
    
-   Disponibilizar os detalhes da transação e acesso ao comprovante.  
    
-   Se houver erros ou pendências, como solicitações com múltiplos aprovadores ou indisponibilidade momentânea dos sistemas, exibir mensagens claras e orientativas.
    

REQ.PG-06900true

REQ.PG-06901

-   `REQ.PG-06901` Exibir data e hora/minuto/segundo da efetivação da solicitação (horário de Brasília).
    

REQ.PG-06902 a 06903

-   `REQ.PG-06902` Para agendamentos únicos, exibir o Id (código de identificação) do pagamento.
    
-   `REQ.PG-06903` Para agendamentos recorrentes, exibir o Id (código de identificação) da autorização (número final do `consentId`, excluindo o prefixo `urn:instituicao:`)
    

REQ.PG-07200true

REQ.PG-07300 true

REQ.PG-07400true

REQ.PG-07500true

REQ.PG-07501

-   `REQ.PG-07501` Exibir a data do agendamento único ou do primeiro pagamento da recorrência.
    

REQ.PG-07600true

REQ.PG-07700true

REQ.PG-07800true

Nota.ITPtrue

REQ.PG-07801

-   `REQ.PG-07801` Informar ao usuário que a transação estará sujeita à disponibilidade de saldo e limites transacionais da conta de débito no momento da efetivação do pagamento.      
    Ex.: O pagamento está sujeito à disponibilidade de saldo e limites da sua conta no momento da cobrança.
    

REQ.PG-07809

-   `REQ.PG-07809` Informar, com destaque, o caminho para acessar a autorização de pagamento na ITP.
    

REQ.PG-07810

-   `REQ.PG-07810` Informar, com destaque, que a autorização de pagamento pode ser cancelada tanto na ITP quanto na ID.
    

REQ.PG-07811

-   `REQ.PG-07811` Se a ITP oferecer alteração da autorização de pagamento, informar, com destaque, que a autorização pode ser alterada.
    

wide760

**Nota**

A experiência de alteração permite que o usuário altere parâmetros como data, recebedor ou ID, embora, no backend, esteja cancelando o agendamento vigente e criando uma nova autorização de agendamento.

Consulte a página **Gestão de Pix Agendado** para mais informações.

![image-20260826-135107.png](images/image-20260826-135107.png)

**Cenário: Interrupção da jornada**

REQ.PG-07900true

REQ.PG-08000true

![image-20260619-190302.png](images/image-20260619-190302.png)

REC.PG-02100true

REC.PG-02101

-   `REC.PG-02101` Informar que a efetivação apresentada nesta etapa refere-se à configuração do agendamento, e não à execução dos pagamentos agendados.  
    Ex.: Pagamentos agendados com sucesso!
    

REC.PG-02102-   `REC.PG-02102` Informar o horário limite para cancelamento conforme definido pelo arranjo de pagamento.   

Ex.: Você pode cancelar o agendamento até às 23:59 do dia anterior à data agendada.

![image-20260826-135312.png](images/image-20260826-135312.png)

* * *

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01201`

**Texto**

Permitr que o usuário insira a data do agendamento único ou escolha a recorrência dos agendamentos.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-01202`

**Texto**

Informar ao usuário que pagamentos agendados para datas inexistentes (Ex.: Dias 29, 30 e 31 de determinados meses) poderão ser efetivados em data anterior ou posterior à data agendada.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Especificação técnica

**ID**

`REQ.PG-01203`

**Texto**

Para agendamentos únicos, permitir que o usuário insira a data do pagamento dentro do período de até 24 meses a partir da data da solicitação.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

PUX - 282

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01204`

**Texto**

Exibir a data definida pelo usuário para execução do pagamento no agendamento único.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Especificação técnica

**ID**

`REQ.PG-01205`

**Texto**

Para agendamentos recorrentes, permitir que o usuário agende até 60 recorrências de pagamentos em uma única autorização, dentro do período de até 24 meses a partir da data de solicitação, independentemente do modelo de recorrência definido na autorização (diário, semanal, mensal ou customizado).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

PUX - 282

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-01206`

**Texto**

Se o usuário definir uma data final para a recorrência, impedir a edição do número de recorrências.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-01207`

**Texto**

Se o usuário definir um número de recorrências, exibir automaticamente a data do último pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

IN BCB 760

**ID**

`REQ.PG-01208`

**Texto**

Exibir a periodicidade dos agendamentos escolhida pelo usuário.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-01209`

**Texto**

Exibir as datas que definem o período da recorrência, incluindo a data de início e a data do último pagamento da recorrência.

trueListe as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, A padronização da terminologia utilizada pelas instituições participantes durante a jornada do compartilhamento, IN BCB 760

**ID**

`REQ.PG-01210`

**Texto**

Seguir o padrão seguinte para informar a data de encerramento e/ou número de recorrências do agendamento: true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, A padronização da terminologia utilizada pelas instituições participantes durante a jornada do compartilhamento, IN BCB 760

**ID**

`REQ.PG-01211`

**Texto**

Seguir o padrão seguinte para informar a data de encerramento e/ou número de recorrências do agendamento:

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05001`

**Texto**

Exibir a data do agendamento único ou do primeiro pagamento da recorrência.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05002`

**Texto**

Exibir a data de validade da autorização (mesma data do agendamento único ou do último pagamento da recorrência).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05003`

**Texto**

Para agendamentos recorrentes, exibir a periodicidade da recorrência (Diária, Semanal, Mensal ou Customizado).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA

**Proposta**

**Instituição**

ID

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-05004`

**Texto**

Para agendamentos recorrentes, exibir o número de recorrências, se informado pela ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-06901`

**Texto**

Exibir data e hora/minuto/segundo da efetivação da solicitação (horário de Brasília).

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Especificação técnica

**ID**

`REQ.PG-06902`

**Texto**

Para agendamentos únicos, exibir o Id (código de identificação) do pagamento.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Especificação técnica

**ID**

`REQ.PG-06903`

**Texto**

Para agendamentos recorrentes, exibir o Id (código de identificação) da autorização (número final do `consentId`, excluindo o prefixo `urn:instituicao:`)

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Arranjo de pagamento, IN BCB 760

**ID**

`REQ.PG-07501`

**Texto**

Exibir a data do agendamento único ou do primeiro pagamento da recorrência.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-07801`

**Texto**

Informar ao usuário que a transação estará sujeita à disponibilidade de saldo e limites transacionais da conta de débito no momento da efetivação do pagamento.      
Ex.: O pagamento está sujeito à disponibilidade de saldo e limites da sua conta no momento da cobrança.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-07809`

**Texto**

Informar, com destaque, o caminho para acessar a autorização de pagamento na ITP.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado, Pix Automático, Transferências Inteligentes

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-07810`

**Texto**

Informar, com destaque, que a autorização de pagamento pode ser cancelada tanto na ITP quanto na ID.

true

Liste as "chaves" nesta coluna — elas vão ser os títulos das colunas na tabela de relatório

Liste o "valor" de cada chave nesta coluna — eles vão preencher as linhas na tabela de relatório

**Produto**

Pix Agendado

**Jornada**

Hybrid Flow, Hybrid Flow com Hand-off, CIBA, JSR e Gestão

**Proposta**

**Instituição**

ITP

**Justificativa**

Experiência do usuário, Conveniência e controle - IN BCB 760

**ID**

`REQ.PG-07811`

**Texto**

Se a ITP oferecer alteração da autorização de pagamento, informar, com destaque, que a autorização pode ser alterada.
