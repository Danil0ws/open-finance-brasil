# Documento de Requisitos do Produto - [PC] Portabilidade de Crédito - CPC

none

# Portabilidade de Crédito – Crédito Pessoal Clean (CPC)

**GT** **Responsável:** Portabilidade de Crédito  
**Responsável pela frente:** Mayara de Melo Santos  
**Status do Documento:** Aprovado  
**Data da Última Atualização:** 19/08/25

# 1\. Introdução

Este documento descreve os requisitos de produto para a implementação do serviço de solicitação de Portabilidade de Crédito no âmbito do Open Finance Brasil (OFB). A iniciativa visa aumentar a competitividade, reduzir o tempo de solicitação e simplificar o processo para o usuário final.

## 1.1 Contexto

A Portabilidade de Crédito permite que usuários transfiram suas operações de crédito e arrendamento mercantil entre instituições financeiras em busca de melhores condições. Atualmente, a solicitação de portabilidade pode ser feita via registradora. A implementação da solicitação de portabilidade, alinhada à agenda do Open Finance Brasil (OFB), visa agilizar e simplificar o processo.

## 1.2 Problema

O processo atual de solicitação de portabilidade de crédito pode ser demorado e complexo, o que desestimula a utilização do serviço por parte dos clientes. Além disso, o desconhecimento do público em relação à portabilidade de crédito limita o potencial de utilização desse serviço.

## 1.3 Objetivo

O objetivo deste projeto é viabilizar um serviço de portabilidade de crédito ágil e fácil no âmbito do OFB, tornando o processo mais competitivo e transparente, proporcionando aos clientes:

-   Aumento da competitividade entre instituições financeiras.
    
-   Redução do tempo de solicitação.
    
-   Simplificação do processo.
    

## 1.4 Solução

Para viabilizar a portabilidade de crédito, a solução utilizará de recursos do Open Finance para obter o consentimento dos dados transacionais do cliente e acessar as informações dos seus contratos elegíveis a portabilidade. Para as demais etapas do processo de portabilidade, será desenvolvida uma nova especificação.  
A primeira entrega da portabilidade será focada no produto **Crédito Pessoal Clean (CPC)**, enquanto o **Crédito Consignado Federal** será contemplado na fase seguinte.

# 2\. Escopo

## 2.1 Assuntos contemplados

Este PRD aborda os seguintes assuntos relacionados ao fluxo de portabilidade de crédito:

**Etapa de Solicitação:**

-   **Mapeamento dos dados:** Definição das informações necessárias para viabilizar o pedido de portabilidade de crédito.
    
-   **Consentimento e formalização do pedido:** Utilização do consentimento atual para dados de crédito e criação de um processo de formalização específico para validar o pedido.
    
-   **Mapeamento de adequações nos Dados Transacionais:** Adaptação da especificação de Empréstimos para o produto CPC.
    
-   **Gestão de simultaneidade:** Regra para lidar com múltiplas solicitações de portabilidade para o mesmo contrato.
    
-   **Notificações e alertas:** Definição das etapas e mensagens para notificar o cliente sobre o progresso da solicitação.
    
-   **Regra de limitação e avaliação da proposta:** Garantir o cumprimento da regra referente ao prazo da operação.
    

**Etapa de Efetivação:**

-   **Regra de envio da contraproposta:** Definição do prazo e regras para o envio e aceite da contraproposta pela instituição credora original.
    
-   **Desistência do pedido antes da efetivação:** Permitir que o cliente desista da portabilidade antes da liquidação.
    
-   **Motivos de recusa:** Definir os principais motivos de recusa da portabilidade.
    
-   **Cenários de disputa:** Elaboração de cenários de disputa específicos para portabilidade de crédito.
    

**Etapa de Liquidação:**

-   **Mapeamento dos dados necessários para liquidação:** Definição das informações necessárias para a transferência de recursos.
    
-   **Transferência de recursos:** Definição do processo de transferência de recursos entre as instituições.
    
-   **Confirmação de recebimento:** Confirmação do recebimento dos recursos pela instituição credora original.
    
-   **Confirmação da efetivação:** Confirmação da efetivação da portabilidade de crédito via API.
    
-   **Registro e armazenamento:** Definição do prazo e informações a serem armazenadas pelas instituições.
    

## 2.2 Assuntos a serem tratados futuramente

Os seguintes assuntos serão abordados em fases posteriores do projeto:

-   Início das discussões referente o produto Crédito Consignado Federal (abril/25).
    
-   Resolução referente ao ressarcimento do RCO (Custo de Originação) (outubro/25).
    
-   Inclusão de outros produtos de crédito no fluxo de portabilidade via OFB (segundo semestre de 2026).
    

# 3\. Funcionalidades

Esta seção detalha as funcionalidades a serem implementadas em cada etapa do fluxo de portabilidade de crédito.

## 3.1 Etapa de Solicitação

### 3.1.1 Mapeamento dos Dados Necessários para Pedido da Portabilidade

Os seguintes dados serão necessários para solicitar a portabilidade de crédito:

-   **Dados do Devedor:** CPF, telefone ou e-mail.
    
-   **Dados do Contrato:** Número do contrato, taxa anual, taxa nominal, taxa efetiva, custo efetivo Total - CET (com identificação se tem seguro contratado), prazo da operação, sistema de amortização e valor das prestações.
    
-   **Proposta da Instituição Proponente:** Taxa anual, taxa nominal, taxa efetiva, CET, prazo da operação, sistema de amortização, valor das prestações e o saldo devedor utilizado como base para construção da proposta.
    
-   **Índice de Preço:** Índice ou base de remuneração a ser utilizada (se aplicável).  
    Observação: Índice de Preço é calculado com base em indicadores previamente definidos, geralmente vinculados a índices oficiais de inflação, como o IPCA ou o IGP-M.
    
-   **Dados da Instituição Proponente:** CNPJ (opcional).
    

### 3.1.2 Consentimento e Formalização do Pedido

-   **Consentimento:** Se o cliente já consentiu o compartilhamento de dados de operações de crédito e o consentimento estiver ativo, não será necessário um novo. Caso contrário, será preciso obtê-lo.
    
    -   **Expiração do consentimento:** Para garantir a continuidade do processo de portabilidade pelo trilho do OFB, a instituição proponente deve assegurar que o consentimento esteja válido por, no mínimo, 15 dias corridos após a solicitação. Caso o consentimento esteja próximo da expiração, é necessário solicitar sua renovação antes do início do pedido, evitando contratempos no fluxo e garantir a continuidade do processo conforme o esperado.
        
    -   **Revogação do consentimento:** Caso o cliente revogue o consentimento após a solicitação de portabilidade de crédito já estar em andamento, o pedido deverá seguir normalmente. A revogação do consentimento de operação de crédito não implica o cancelamento automático da portabilidade. O cancelamento do pedido deve ocorrer somente mediante manifestação expressa do cliente, por meio da funcionalidade de cancelamento disponível no canal digital da instituição proponente ou credora, conforme descrito no item “Desistência do pedido de portabilidade antes da efetivação”.
        
    -   **Ponto importante:** Na etapa de liquidação, a instituição proponente poderá efetuar o pagamento com base no saldo devedor e nos dados contratuais previamente capturados. Caso a instituição credora identifique divergência no valor recebido, deverá atualizar a máquina de estados para refletir a ocorrência dessa inconsistência, conforme o fluxo previsto para este cenário.
        

Observação: A instituição receptora dos dados deve garantir que o escopo dos dados acessados seja adequado à finalidade de uso, conforme a Resolução Conjunta nº 1.

-   **Formalização:** Cada instituição definirá seu mecanismo de autenticação para formalizar o pedido (senha, token SMS, token por e-mail etc.). A formalização deverá ser realizada exclusivamente por meio eletrônico, exceto nos casos ou estados onde houver regulamentação que exija obrigatoriamente a assinatura física.
    

### 3.1.3 Adequações na especificação de Dados Transacionais

As seguintes adequações serão implementadas na API de Empréstimos para viabilizar a solicitação de portabilidade de crédito para o produto CPC:

**Campos existentes:**

-   **Data de Vencimento (dueDate):** Deverá clarificar a descrição do campo para informar a data do último vencimento, especialmente útil para contratos repactuados
    
-   **Taxa de Juros (interestRates):** A documentação deverá ser atualizada para orientar os participantes que, para o produto CPC, devem ser informadas as taxas nominal e efetiva com a periodicidade anual (a.a.), podendo incluir valores em uma periodicidade diferente como adicional.
    
-   **Taxa de Juros/Taxa Pós fixada (interestRates.postFixedRate):** Ajustar a descrição para indicar que, se a taxa for pós-fixada, o indexador atrelado deverá ser informado.
    
-   **Data/Hora da Atualização do saldo (contractOutstandingBalance):** Deverá ser incluído a informação de data e hora referência do saldo devedor de um contrato, para que a instituição proponente tenha a informação correta para envio da proposta e liquidação do contrato.
    
-   **Subtipo do indexador de taxa referencial (referentialRateIndexerSubType):** Alteração na descrição do campo para informar que, caso o campo postFixedRate esteja preenchido, este campo deve ser enviado.
    

**Novos Campos:**

-   **Valor da Parcela (nextInstalmentAmount):** Inclusão do campo “Valor da parcela” no vencimento. Este campo será de preenchimento obrigatório somente para o produto CPC.
    
-   **Seguro (hasInsuranceContracted):** Inclusão do campo “Tem seguro?” para indicar se o contrato original possui seguro contratado ou não.
    
-   **Categorização dos subtipos de produto (productSubTypeCategory):** Inclusão do campo para identificar o subtipo do produto, como por exemplo Crédito Pessoal Clean (CPC).
    
-   **Saldo devedor (totalRemainingAmount):** Inclusão do campo para informar o valor total pendente para liquidação do contrato.
    
-   **Última atualização do saldo devedor do contrato (lastUpdatedContractOutstandingBalance):** Inclusão do campo para indicar a última atualização realizada no campo contractOutstandingBalance.
    

### 3.1.4 Gestão de Simultaneidade

Para evitar o envio de múltiplas solicitações de portabilidade para o mesmo contrato, as instituições devem implementar mecanismos que permitam: recusar solicitações simultâneas de portabilidade de crédito referentes ao mesmo contrato, seja por meio da registradora ou do Open Finance Brasil (OFB), priorizando sempre a solicitação mais antiga. A instituição credora original é responsável por atualizar o status do contrato diariamente.

-   **Consultar solicitações de portabilidade em andamento:** A instituição proponente deve consultar a API de Portabilidade de Crédito para verificar se um contrato de empréstimo já possui um pedido de portabilidade anterior, seja pelo fluxo da registradora ou pelo do OFB. A atualização dessas informações na API é de responsabilidade da instituição credora original.
    
-   **Recusar novas solicitações de portabilidade, caso já tenha uma em andamento:** Não será permitido registrar um novo pedido de portabilidade para um contrato que já possua uma solicitação em andamento, garantindo a prioridade para a primeira solicitação registrada.
    

### 3.1.5 Comunicações

As comunicações previstas devem ser compartilhadas com o cliente durante a solicitação da portabilidade, por meio de textos definidos na jornada ou por notificações, conforme a estratégia de negócio adotada por cada instituição.

**Evento**

**Gatilho**

**Origem**

**Casos de Uso**

**Resposta**

**Destinatário**

**Premissa da Notificação**

Fornecer o consentimento

Cliente informa a instituição credora

Canal digital proponente

Cliente deseja realizar o consentimento

Notificação de início do processo de consentimento

Cliente

Destacar a importância de realizar o consentimento para dar continuidade ao fluxo de solicitação da portabilidade.

Seleção do contrato

Cliente informa o contrato que deseja portar

Canal digital proponente

Cliente deseja portar o crédito para a instituição proponente

Confirmação de recebimento da solicitação e prazo estimado para análise

Cliente

Em casos de análise assíncrona, é essencial informar o prazo estimado para conclusão e apresentação da nova proposta.

Análise da proposta

Proposta de portabilidade recebida

Canal digital proponente

Cliente realiza avaliação das condições para seguir com o pedido da portabilidade

Confirmação de que a proposta foi aceita e seguirá para os próximos passos

Cliente

Destacar que a proposta apresentada foi aceita e que o processo de formalização do pedido terá continuidade.

Aceite do contrato

Contrato da nova operação é exibido

Canal digital proponente

Cliente realiza conferência das informações do contrato

Notificação para aceite do contrato

Cliente

Destacar que para dar continuidade ao pedido de portabilidade, é necessário que leia e aceite as condições contratuais, sinalizando que o valor da parcela pode sofrer alterações (essa informação deve ser apresentada no documento de formalização - CCB ou jornada de acordo com a estratégia da instituição).

Nesta etapa, é importante que o documento (CCB) seja exibido, para que o cliente tenha visibilidade do resumo da nova operação de crédito e do resumo contratual. O modelo e as cláusulas do documento serão definidos por cada instituição.

Autenticação do aceite

Autenticação/validação do aceite

Canal digital proponente

Cliente realiza a autenticação/validação do contrato

Notificação para confirmar a autenticação

Cliente

Ressaltar que o mecanismo de autenticação utilizado foi validado com sucesso.

Conclusão do aceite

Portabilidade concluída com sucesso

Canal digital proponente

Finalização do pedido de portabilidade de crédito

Confirmação de que o pedido da portabilidade foi concluído com sucesso

Cliente

Ressaltar que o pedido de portabilidade será enviado à instituição credora original e que o processo pode levar até 5 dias úteis.

Contraproposta

Estímulo/oferta da contraproposta

Canal credora

Credora aciona o cliente para envio da contraproposta

Notificação para informar o envio da contraproposta

Cliente

Sinalizar que o acionamento foi necessário pelo pedido de portabilidade de crédito com o banco XPTO, e que o aceite da proposta deve ser feito em até 3 dias úteis, caso contrário, o pedido será automaticamente sequenciado.

Contraproposta

Aceite da contraproposta

Canal digital credora

Cliente realiza aceite da contraproposta

Confirmação de que o pedido da portabilidade foi cancelado

Cliente

Informar que o pedido de portabilidade foi cancelado.

Conclusão do pedido

Não aceite da contraproposta

Canal digital proponente

Cliente não aceita a contraproposta enviada

Notificação para informar que a portabilidade foi efetivada.

Cliente

Ressaltar que o pedido de portabilidade foi concluído com sucesso.

Problemas no processo

Erro durante o processo de portabilidade

Canal digital proponente e credora

Interrupção do processo devido a erro

Notificação de erro e instruções para resolução

Cliente

Não exibir erros no formato 4xx, 5xx (ex.:403, 404, 409 e 422). A API deve retornar o erro, que deve ser interpretado e, se necessário, exibir ao cliente uma mensagem clara do que precisa ser feito para resolução.

### 3.1.6 Regra de Limitação e Avaliação da Proposta

A instituição proponente deve exibir os contratos elegíveis para solicitação de portabilidade do produto CPC, considerando que a proposta pode incluir carência, conforme a estratégia da instituição financeira. A validação do percentual de comprometimento de renda é responsabilidade da instituição. Além disso, deve estabelecer um processo que assegure a exibição do comparativo entre o contrato original e a nova proposta, destacando as informações listadas a seguir:

-   **Saldo devedor.**
    
-   **Para** (indicando a instituição de destino).
    
-   **De** (indicando a instituição de origem).
    
-   **Diferença das parcelas** (indicando o valor de redução/aumento em relação ao contrato de origem).
    
-   **Diferença total do somatório das parcelas** (indicando o valor de redução/aumento total em relação ao contrato de origem).
    
-   **Novo prazo** (indicando a quantidade de parcelas remanescentes até o fim do novo contrato).
    
-   **Prazo remanescente** (indicando a quantidade de parcelas remanescentes até o fim do contrato de origem).
    
-   **Nova parcela** (indicando o valor da parcela do novo contrato).
    
-   **Parcela atual** (indicando o valor da parcela do contrato de origem).
    
-   **Nova taxa de juros** (indicando a taxa de juros do novo contrato).
    
-   **Taxa de juros atual** (indicando a taxa de juros do contrato de origem).
    
-   **Novo CET** (indicando o Custo Efetivo Total do novo contrato).
    
-   **CET atual** (indicando o Custo Efetivo Total do contrato de origem).
    
-   **Data da primeira parcela do novo contrato.**
    
-   **Data da última parcela do novo contrato.**
    

Além da exibição da tela comparativa, é necessário garantir o cumprimento das seguintes regras:

-   **Prazo remanescente da operação:** A nova proposta deverá estabelecer um prazo igual ou inferior ao do contrato original, propostas que não sigam essa regra devem ser bloqueadas automaticamente pela instituição proponente e não ser exibida ao cliente.
    
-   **Saldo devedor:** O valor da operação da nova proposta não deve exceder o saldo devedor do contrato original.
    
-   **Periodicidade:** Não deve haver mudança de periodicidade entre o novo contrato e o contrato original.
    

**Ponto importante:** Conforme orientação do regulador transmitida na reunião bilateral realizada em 05/12, não será mais necessária a aplicação de uma regra para o valor da parcela a maior, conforme previsto inicialmente. Ainda assim, é fundamental manter a comunicação sobre as condições operacionais nessa etapa.

**Fluxograma da Regra de Limitação e Avaliação da Proposta:**

-   O fluxograma detalhado está apresentado na imagem abaixo.
    

![Portabilidade\_Credito\_v1 (1).png](https://openfinancebrasil.atlassian.net/wiki/rest/api/content/1183023105/child/attachment/att1183023125/download)

**Abandono e Retomada da jornada:**

-   Em caso de abandono da jornada na etapa de avaliação da proposta, a retomada poderá ocorrer em dois momentos, definidos pela instituição proponente:
    

1\. Cliente retoma a jornada na etapa de seleção dos contratos.

2\. Cliente retoma a jornada na etapa de apresentação da proposta.

2.1 Para que o cliente possa retomar a jornada na etapa de apresentação da proposta, as condições operacionais apresentadas inicialmente precisam estar ativas.

**Ponto importante:** O pedido de portabilidade de crédito só será efetivado na etapa de autenticação.

## 3.2 Etapa de Efetivação

### 3.2.1 Regra de Envio da Contraproposta

A instituição credora original terá até 3 dias úteis para enviar uma contraproposta ao cliente, contados a partir do primeiro dia útil após a solicitação de portabilidade. A instituição credora pode enviar quantas propostas entenderem aderente à sua estratégia dentro do prazo estabelecido, desde que a máquina de estados não tenha sido atualizada. As regras mencionadas no item “Regra de Limitação e Avaliação da Proposta” também devem ser consideradas para a oferta da contraproposta.

Na contagem dos dias, devem ser considerados dias úteis somente os dias de segunda a sexta-feira, exceto os feriados nacionais.

**Regras Detalhadas:**

Para garantir o cumprimento do prazo de 3 dias úteis, foram definidas as seguintes regras:

-   **Início do Prazo de Portabilidade:** A contagem do prazo de 3 dias úteis inicia no primeiro dia útil após a solicitação de portabilidade.
    
-   **Notificação de Retenção:** A instituição credora original deverá informar a instituição proponente sobre a retenção ou não da operação e atualizar a máquina de estados até as 10 horas da manhã, independentemente do dia útil.
    

**Ponto importante:** Conforme orientação do regulador transmitida na reunião bilateral realizada em 05/12, o horário para a instituição credora original informar a instituição proponente deve ser o mesmo, independentemente de a operação ter sido retida ou não.

-   **Aceite da Contraproposta:** O cliente poderá aceitar a contraproposta até às 9h do terceiro dia útil.
    

**Ponto importante:** Após a disponibilização da contraproposta ao cliente em seu canal digital, a instituição credora original não poderá removê-la ou bloqueá-la antes do prazo previsto para aceite. A partir das 9h do terceiro dia, a contraproposta não poderá mais ser aceita. Nesse momento, a instituição credora original poderá removê-la do canal digital ou bloqueá-la para impedir o aceite.

**Procedimentos:**

-   A instituição credora original, caso tenha interesse em reter a operação, poderá contatar o cliente por meio do canal de sua escolha (físico ou digital) para apresentar a contraproposta.
    
-   A oferta da contraproposta deve estar disponível no canal digital da instituição credora original, pois o aceite do cliente deverá ocorrer exclusivamente por esse canal.
    

**Ponto importante:** Nesta etapa, deve ser exibida uma tela comparativa no canal digital da instituição credora original para evidenciar as condições operacionais das propostas da instituição proponente e da instituição credora original (ex.: CET). O objetivo é permitir que o cliente compare as condições com facilidade e escolha a proposta mais vantajosa. As regras mencionadas no item “Regra de Limitação e Avaliação da Proposta” devem ser consideradas esta etapa.

-   Se o cliente aceitar a contraproposta dentro do prazo previsto na regra “Aceite da Contraproposta”, a instituição credora original deve informar à instituição proponente que a operação foi retida, atualizando o status do pedido de portabilidade na máquina de estados até às 10h da manhã.
    
-   Caso o cliente não aceite ou não responda à contraproposta dentro do prazo previsto em regra, a instituição credora original deve comunicar à instituição proponente que o pedido de portabilidade pode prosseguir, atualizando o status do pedido de portabilidade na máquina de estados até às 10h da manhã.
    

**Exemplo:** Caso a credora receba o pedido de portabilidade entre 10h e 23h59 e opte por liberar imediatamente o contrato para a proponente, a atualização da máquina de estados para "accepted\_settlement\_in\_progress" deve ocorrer apenas entre 0h e 10h do próximo dia útil. Essa prática garante que a proponente tenha tempo hábil para efetuar o pagamento ainda no mesmo dia em que a máquina de estados for atualizada.

### 3.2.2 Desistência do pedido de portabilidade antes da efetivação

O cliente poderá desistir do pedido de portabilidade de crédito a qualquer momento antes de ocorrer a liquidação da operação, tanto no canal digital da instituição proponente quanto no canal digital da instituição credora original.

**Ponto importante:** O prazo final para desistência do pedido será às 9h do terceiro dia útil após a solicitação ou até a atualização da máquina de estados pela instituição credora original.

**Procedimentos:**

-   Na jornada de portabilidade de crédito via OFB, nos canais digitais da instituição proponente e da instituição credora original, o cliente deve ter uma opção clara para cancelar o pedido a qualquer momento antes da liquidação.
    
-   Se o cliente desistir do pedido de portabilidade através do canal digital da instituição proponente, esta deve comunicar a desistência à instituição credora original. Da mesma forma, se a desistência ocorrer no canal digital da instituição credora original, esta deve comunicar a desistência à instituição proponente. A comunicação de ambas deve ocorrer por meio da atualização da máquina de estados.
    
-   O contrato original deve permanecer disponível para um novo pedido de portabilidade no futuro, após o cancelamento.
    

**Interface do Cliente:**

-   Tanto a jornada da instituição proponente, como a jornada da instituição credora original devem contemplar uma interface/menu que permita ao cliente visualizar o status do pedido de portabilidade e acessar a opção de cancelamento.
    

**Serviço de Comunicação:**

● Para gerenciar as desistências do devedor, será criado um serviço de comunicação (endpoint – API Portabilidade de Crédito) baseado em eventos.

● O serviço comunicará a instituição envolvida sobre mudanças no estado do pedido de portabilidade de crédito, incluindo a desistência.

**Diagrama do Serviço de Comunicação:**

### 3.2.3 Motivos de Recusa

Motivos padronizados de recusa e inconsistências que possam impedir a conclusão de um pedido de portabilidade na jornada do OFB.

O manual deve:

-   Justificar a não aceitação do pedido de portabilidade.
    
-   Assegurar a conformidade do processo.
    

**Motivos de Cancelamento pela Instituição Proponente:**

**Motivo de Recusa**

**Detalhamento**

**Etapa**

Cancelado pelo cliente

Cliente desiste do pedido da portabilidade

Após solicitação do pedido de portabilidade

Valor do saldo devedor atualizado substancialmente divergente do valor informado inicialmente

Saldo devedor atualizado divergente (superior a 15%) do informado inicialmente

Liquidação

Política de crédito

Proponente desiste da oferta ao cliente por políticas internas

Liquidação

**Motivos de Recusa pela Instituição Credora:**

**Motivo de Recusa**

**Detalhamento**

**Etapa**

**Considerações**

Retenção do Cliente

Cliente aceitou contraproposta da instituição credora original (dentro do prazo).

Aceite da contraproposta

Deve ocorrer monitoramento para assegurar que a contraproposta foi aceita pelo cliente no canal digital da instituição credora, mediante apresentação de evidências.

Contrato já liquidado

Contrato liquidado pelo  
cliente.

Liquidação

Sem considerações.

Divergência de dados referente ao pagamento efetuado

Proponente realizou a liquidação com valor divergente e retentativas não foram satisfatórias

Confirmação do recebimento

Sem considerações.

Portabilidade cancelada por falta de liquidação

Proponente não realizou a liquidação da portabilidade

Confirmação do recebimento

Sem considerações.

Portabilidade em andamento

Posteriormente à efetivação do pedido de portabilidade, a IF credora original identificou que o cliente já possui outro pedido de portabilidade em andamento para o mesmo contrato.

Formalização/antes do envio da contraproposta

Sem considerações.

Cliente com ação judicial

Possui ação judicial

Liquidação

Avaliar a possibilidade de quando for selecionado este motivo, o cliente seja orientado de como resolver a situação.

Modalidade da operação incompatível

Modalidade divergente da indicada pela instituição proponente

Liquidação

Sem considerações.

Cancelado pelo cliente

Cliente desiste do pedido da portabilidade

Após solicitação do pedido de portabilidade

Sem considerações.

### 3.2.4 Cenários de Disputa

Cenários de disputa relacionados ao fluxo de portabilidade de crédito no trilho do Open Finance.

Esses cenários visam:

-   Atualizar o manual de cenários de disputa do OFB.
    
-   Incluir fluxos padronizados que detalhem o processo de portabilidade de crédito.
    
-   Permitir que as instituições consultem e sigam as orientações de forma consistente.
    

Os cenários definidos serão incorporados ao manual existente em uma seção específica dedicada ao fluxo de portabilidade de crédito.

**Cenários de Disputa:**

**Cenário Macro**

**Cenário**

**Categorias**

**Responsável Inicial**

Informações para pagamento

Saldo devedor atualizado com valor muito superior ao esperado

Saldo devedor com valores inconsistentes, em um percentual muito maior do que o esperado (sugestão inicial conforme ciclo da registradora de 15%), devido a uma inconsistência no sistema e/ou benefício para a credora original, que deseja que a portabilidade seja cancelada pela proponente.

Credora

Informações para pagamento

Dados bancários inconsistentes

Dados bancários incorretos por culpa ou dolo da credora original.

Credora

Informações para pagamento

Dados bancários indisponíveis

Dados bancários indisponíveis, devido a uma inconsistência no sistema no ambiente da credora original.

Credora

Liquidação

Liquidação não identificada

Pagamento não identificado na data pela credora original sem uma mensagem de cancelamento do pedido de Portabilidade de Crédito.

Proponente

Confirmação do pagamento

Pagamento a menor

Pagamento inferior ao saldo devedor atualizado estipulado, devido a uma inconsistência no sistema.

Proponente

Confirmação do pagamento

Pagamento a maior

Pagamento superior ao saldo devedor atualizado estipulado.

Proponente

Liquidação

Liquidação fora do prazo

O pagamento efetuado pela Proponente não ocorreu no mesmo dia do recebimento da mensagem de continuação da portabilidade pela credora original.

Proponente

Informações para pagamento

Dados bancários inconsistentes

O pagamento realizado não foi liquidado pela proponente devido a dados incorretos imputados por culpa ou dolo da proponente.

Proponente

## 3.3 Etapa de Liquidação

### 3.3.1 Mapeamento de Dados Necessários e Transferência de Recursos

A instituição credora original deverá fornecer os dados listados a seguir à instituição proponente para viabilizar a liquidação da operação, que deve ocorrer no mesmo dia em que houver a comunicação de que a operação não foi retida. A liquidação deve ser realizada via STR0052, respeitando a grade horária da STR.

-   Saldo devedor da operação de crédito na data do envio das informações.
    
-   Prazo remanescente.
    
-   Data de vencimento da última parcela.
    
-   Dados bancários para a transferência de recursos via TED.
    

**Procedimento:**

-   Após a instituição credora original informar que a operação não foi retida e compartilhar as informações necessárias para a liquidação, a instituição proponente deverá também consultar as APIs de Operações de Crédito para consultar o saldo devedor atualizado.
    
-   Com todas as informações em posse, a instituição proponente realiza a transferência de recursos via STR0052 para a quitação do contrato original.
    
-   Após ocorrer a transferência de recurso via STR0052, a instituição proponente deve notificar a instituição credora original por meio de endpoint específico, para que a máquina de estados seja atualizada e o fluxo tenha sequência.
    

**Ponto importante**: Caso a Instituição Proponente não notifique a Instituição Credora, após transferência do recurso via STR0052, a Instituição Credora não deverá cancelar o Pedido de Portabilidade pela falta dessa notificação, dado que a STR0052 possui informações que ajudam a identificar o referido Pedido de Portabilidade.

### 3.3.2 Confirmação de Recebimento e Confirmação da Efetivação

A instituição credora original terá até 2 dias úteis para confirmar o recebimento dos recursos referentes à liquidação da operação, atestando a efetivação da portabilidade. O prazo será contado a partir do próximo dia útil, independentemente do horário em que o pagamento seja realizado.

Na contagem dos dias, devem ser considerados dias úteis somente os dias de segunda a sexta-feira, exceto os feriados nacionais.

**Comunicação:**

-   A confirmação do recebimento dos recursos e a efetivação do contrato devem ser comunicadas através do serviço de notificação, baseado em eventos.
    

**Contestação de valores:**

-   Em caso de contestação de valores, as instituições devem se comunicar por meio da atualização da máquina de estados. Se a instituição credora original identificar inconsistência na liquidação, a máquina de estados deverá ser atualizada para indicar a existência da inconsistência no pagamento. Após a resolução, antes de realizar a nova transferência de recursos, a instituição proponente deve realizar uma nova consulta ao saldo devedor, a fim de garantir a transferência do valor correto. Após o recebimento do recurso, a instituição credora original deve atualizar o estado do pedido e confirmar a efetivação da portabilidade via API. Caso a inconsistência não seja resolvida, a máquina de estados também deve ser atualizada.
    
-   Se não houver consenso entre as instituições em até 2 dias úteis, o pedido de portabilidade será cancelado ou a instituição proponente buscará uma resposta da credora original dentro do prazo.
    

**Ponto importante:** Nos casos em que for necessário realizar o estorno, este deve ocorrer de forma integral e exclusivamente via STR0010 (motivo 85) para o fluxo de portabilidade de crédito no OFB.

### 3.3.3 Registro e armazenamento

**Prazo de Armazenamento:**

-   Instituição Proponente: mínimo de 5 anos, sem limite máximo.
    
-   Instituição Credora original: mínimo de 5 anos após a solicitação de portabilidade, sem limite máximo.
    

Todas as informações trafegadas pelas APIs do OFB devem ser armazenadas, incluindo as seguintes:

-   **Para todos os pedidos de portabilidade:**
    
    -   Código identificador do pedido de portabilidade (ex.: UUID). gerado pela instituição
        
        credora original.
        
    -   Modalidade da operação.
        
    -   Identificador da instituição proponente e da instituição credora original.
        
    -   Data e hora da solicitação do pedido.
        
    -   Data e hora do retorno da instituição credora original.
        
    -   Status do pedido de portabilidade.
        
-   **Para pedidos cancelados ou não efetivados:**
    
    -   Data e hora do cancelamento da portabilidade.
        
    -   Motivo do cancelamento.
        
-   **Para pedidos concluídos:**
    
    -   Data e hora da liquidação do contrato.
        
    -   Valor pago para a liquidação do contrato.
        
    -   Data e hora da confirmação de recebimento do recurso pela instituição credora original.
        

# 4\. Obrigatoriedade de participação

Esta seção apresenta as regras que estabelecem a obrigatoriedade de participação das instituições na oferta do serviço de portabilidade de crédito no âmbito do OFB, conforme as informações disponibilizadas no escopo do BCB.

-   Participação somente de instituições financeiras, no papel de Instituição Credora Original e/ou Instituição Proponente.
    
-   Obrigatoriedade vinculada à participação no Compartilhamento de Dados:
    
    -   instituições do S1 e S2.
        
    -   instituições com +5 milhões de clientes.
        
    -   obrigatoriedade apenas no papel de Instituição Credora Original – como Instituição Proponente é sempre voluntário.
        
-   Instituições do S3 a S5: voluntárias com reciprocidade - se atuar como Proponente, deve atuar como Credora Original.
    
-   Instituição financeira que participar do compartilhamento de dados no Open Finance deve participar da portabilidade como Instituição Credora Original, e vice-versa.
    
-   Conforme atualizações recentes na regulamentação do Open Finance, a participação voluntária no compartilhamento de dados e, consequentemente, na portabilidade, implica a participação de todas as instituições do conglomerado.
    

# 5\. Métricas e monitoramento

Esta seção apresenta os indicadores do produto que devem ser monitorados pelas ferramentas da estrutura.

-   **Categoria: Taxa de adoção**
    
    -   Quantidade/Percentual de instituições que implementaram o serviço de PC via OFB
        
    -   Número de solicitações de portabilidade realizadas, através dos filtros de Proponente e Credora
        
    -   Número de solicitações de portabilidade realizadas por tipo de contrato, através dos filtros de Proponente e Credora
        
    -   Incidência de múltiplas solicitações para o mesmo contrato
        
    -   Proporção de propostas aceitas versus propostas enviadas/efetivadas
        
    -   Frequência de recusas por modelo de contrato
        
    -   Número de pedidos concluídos com sucesso, através dos filtros de Proponente e Credora
        
    -   Percentual de crescimento da adesão das instituições financeiras que utilizam a API de Portabilidade
        
    -   Percentual de crescimento da utilização do serviço de portabilidade de crédito
        
-   **Categoria: Indicadores técnicos**
    
    -   Percentual de tempo em que a API está operacional e disponível
        
    -   Número de respostas de erro (HTTP 408 e 5xx) em relação ao total de requisições
        
    -   Tempo médio de resposta para requisições à API
        
    -   Tempo que uma requisição leva para ir do cliente para o servidor e vice-versa
        
    -   Número de tentativas de acesso não autorizado detectadas
        
    -   Capacidade da API de lidar com picos de carga sem degradação de desempenho
        
    -   Número de chamadas que funcionam sem problemas em diferentes versões da API
        
    -   Percentual de chamadas bem-sucedidas (2XX e 422) em relação às tentativas
        
    -   Feedback dos desenvolvedores sobre a clareza e utilidade da documentação
        
    -   Tempo médio que um desenvolvedor leva para implementar a API pela primeira vez
        
    -   Qualidade dos dados trafegados entre as APIs
        
-   **Categoria: Tempo médio de solicitação e prazos**
    
    -   Tempo médio para conclusão do pedido de portabilidade por situação do pedido de portabilidade, considerando a máquina de estados
        
    -   Número de pedidos de portabilidade não finalizados dentro do prazo regulatório
        
-   **Categoria: Variações das operações retidas**
    
    -   Número de solicitações de portabilidade retidas pela credora
        
    -   Média da taxa de juros das operações retidas após a solicitação de portabilidade
        
    -   Percentual de solicitações de portabilidade retidas pela credora
        
-   **Categoria: Taxa de sucesso**
    
    -   Portabilidade efetivadas + retenções
        

# 6\. Perguntas e respostas

Esta seção reúne as principais dúvidas sobre o fluxo de portabilidade de crédito via OFB para o produto Crédito Pessoal Clean (empréstimo sem consignação). As perguntas e respostas foram organizadas por tema para facilitar a consulta.

-   **Tema: Obrigatoriedade de Participação**
    

1.  **O comitê Gestor do Sistema de Autorregulação da Portabilidade de Operações de Crédito será mantido?** Sim, será mantido.
    
2.  **Os novos entrantes na fase de compartilhamento estão dispensados dos marcos?** Sim. Os novos entrantes estão dispensados dos marcos intermediários de certificação, mas serão cobrados pelo ticket de certificação e pela publicação das APIs nas datas definidas no cronograma vigente.
    
3.  **Quais são exatamente as datas que os novos entrantes na fase de compartilhamento de dados devem seguir?** Devem seguir os prazos de certificação e publicação definidos no cronograma oficial.
    
4.  **Se uma instituição passar a ser obrigatória para o compartilhamento de dados apenas em outubro de 2025, quais marcos de portabilidade essa instituição deverá cumprir?** Os novos entrantes estão dispensados dos marcos intermediários de certificação, mas devem realizar a certificação e a publicação das APIs nas datas definidas no cronograma vigente.
    
5.  **A participação de instituições classificadas como S3 a S5 na portabilidade de crédito é obrigatória?** Para instituições classificadas como S3 a S5, a participação no serviço de portabilidade de crédito é opcional, mas condicionada à reciprocidade. Isso significa que se uma instituição S3, S4 ou S5 quiser atuar como proponente, ela também deverá atuar como credora original.
    
6.  **Instituições S3, S4 e S5 que participam do compartilhamento de dados são obrigadas a ofertar portabilidade de crédito?** Sim. Os requisitos se complementam. Mesmo que a instituição seja classificada como S3, S4 ou S5, se ela participa da fase de compartilhamento de dados, estará obrigada a implementar a API Portabilidade de Crédito. Além disso, a obrigatoriedade se estende às demais instituições pertencentes ao mesmo conglomerado financeiro.
    
7.  **Instituições com mais de 5 milhões de clientes precisam participar?** Sim. A obrigatoriedade é definida de forma complementar, com base em dois critérios:
    
    -   A classificação prudencial (ex.: S3, S4);
        
    -   A participação no compartilhamento de dados, especialmente no caso de instituições com mais de 5 milhões de clientes.
        
8.  **Se uma instituição S4 não participa do compartilhamento de dados e possui menos de 5 milhões de clientes, ela é obrigada a ofertar portabilidade de crédito?** Não. Nesse caso, a participação é considerada voluntária. Caso decida oferecer o serviço, a instituição deverá cumprir todos os requisitos técnicos e operacionais definidos.
    
9.  **Em caso de cessão de contrato para um FIDC, a instituição deixa de ter responsabilidade sobre a portabilidade?** Esse ponto ainda não possui definição formal. Casos assim devem ser submetidos à Associação para análise e eventual posicionamento do Banco Central.
    

-   **Tema: Referências / Dúvidas Técnicas**
    

10.  **Há previsão de custo para chamada de API?** Não haverá custo.
     
11.  **A API de empréstimo poderá ser aproveitada?** Sim, com as devidas adaptações. Uma API específica de Portabilidade de Crédito também será criada.
     
12.  **O RCO deverá ser considerado nas especificações para a cobrança?** Sim, mas a discussão do tema não é foco do grupo de trabalho.
     
13.  **Como será feito o aviso à proponente sobre a não retenção?** A comunicação ocorrerá por meio da consulta ao pedido de portabilidade de crédito. A instituição credora deve atualizar o estado da máquina de estados desse pedido, enquanto a instituição proponente acompanhará a evolução do processo por meio de consultas periódicas ao endpoint correspondente.
     
14.  **A máquina de estados deve ser atualizada para qual valor? REJECTED ou CANCELLED?** Deve ser atualizada para Cancelled, estado utilizado quando o cliente cancela o pedido de portabilidade de crédito antes de a instituição credora sinalizar a não retenção ou de a instituição proponente realizar a liquidação da operação.
     
15.  **Após os 3 dias, se o cliente não aceitar a contraproposta, o status muda para ACCEPTED\_SETTLEMENT\_IN\_PROGRESS. Se a instituição proponente não consultar os dados de pagamento nem efetuar o pagamento, o que deve acontecer? Será considerado decurso de prazo? A portabilidade será cancelada?** Sim, conforme previsto na documentação técnica (descrição do endpoint GET /portabilities/{portabilityId}), as instituições devem consultar periodicamente o estado do pedido. Caso a instituição proponente não realize a liquidação, a instituição credora poderá atualizar o status para "Portabilidade cancelada por falta de liquidação", conforme previsto nos motivos de recusa mencionados no documento de requisitos do produto (PRD).
     
16.  **É possível incluir o campo portabilityId na API GET /account-data, de modo que a credora possa utilizar mais de uma conta, a depender do tipo de produto?** Foi solicitada uma alteração no endpoint account-data, uma vez que se identificou que as contas podem variar por tipo de produto, e não por pedido de portabilidade. A especificação será atualizada para refletir essa possibilidade de múltiplas contas por produto.
     
17.  **Quando é mencionado “tipo do produto”, isso inclui os campos productType e productSubTypeCategory?** Sim. Com a diferenciação de contas baseada na localidade e no produto, será possível ter uma conta específica para cada pagamento, identificada pelo portabilityId. Caberá à credora identificar o produto e a localidade, quando aplicável, para exibir corretamente os dados bancários.
     
18.  **Existe um prazo para que o productType e productSubTypeCategory seja incluído na API?** O tema foi pautado no GT Portabilidade e será rediscutido na versão Beta 1 do produto Consignado Federal. Entendeu-se que, em um primeiro momento, a identificação do produto será feita pela API Empréstimos. Quando o segundo produto (Consignado Federal) estiver disponível, uma nova análise será realizada para avaliar a necessidade de inclusão de um campo específico na API Portabilidade de Crédito.
     
19.  **Se já houver um pedido de portabilidade em andamento, a chamada à API POST /portabilities deve retornar um erro ou criar uma portabilidade com status REJECTED?** Deve retornar o erro 422 com a mensagem "EM\_ANDAMENTO".
     
20.  **Existe algum SLA regulamentado para a notificação da instituição credora sobre a liquidação do contrato?** Sim. O prazo é de 2 dias úteis, conforme descrito no PRD.
     
21.  **A instituição precisa obrigatoriamente implementar os dois fluxos (síncrono e assíncrono)?** Não. A instituição é obrigada a implementar apenas os requisitos do fluxo que adotar. Caso opte pelos dois, deve implementar ambos.
     
22.  **Os motivos de rejeição são padronizados ou o campo rejectionReason é livre?** A justificativa é feita pelo campo type dentro de rejectionReason. Caso não esteja mapeada, informar type = "Outros" e preencher typeAdditionalInfo.
     
23.  **Como é validada a retenção de cliente durante o processo de portabilidade de crédito?** A instituição precisa registrar formalmente a ação? Sim. É necessário registro formal e evidência do aceite do cliente, além da atualização de status e assinatura digital.
     
24.  **A instituição credora aciona ativamente a proponente após o período de retenção do cliente?** Não. A comunicação ocorre via atualização de status no pedido de portabilidade, e a proponente deve consultar a API periodicamente.
     
25.  **No fluxo de cancelamento ou retenção, a instituição credora precisa notificar ativamente a proponente via API ou apenas alterar o status do pedido?** Apenas altera o status. A comunicação é feita por mudança de estado e consulta periódica pela proponente.
     
26.  **Existe risco de duplicidade em pedidos de portabilidade?** Não. Há um mecanismo de gestão de simultaneidade que impede pedidos duplicados para o mesmo contrato.
     

-   **Tema: Regras do Produto**
    

27.  **Haverá limitação da quantidade de pedidos de portabilidade?** E existirá alguma carência de um pedido para outro? Não haverá limite de quantidade ou carência entre pedidos.
     
28.  **Será possível a troca de modalidade?** Não será possível neste primeiro momento. A portabilidade será limitada de CPC para CPC, mas a possibilidade de troca de modalidade será avaliada futuramente.
     
29.  **Como será realizado o cálculo do saldo devedor?** O cálculo seguirá o método utilizado atualmente pelas instituições financeiras.
     
30.  **Como ficará o fluxo de comparação caso o cliente tenha vários contratos do produto CPC na mesma proponente?** A solicitação de portabilidade será feita individualmente para cada operação.
     
31.  **A portabilidade de crédito do produto CPC no OFB será voltada para Pessoa Física (PF) e Pessoa Jurídica (PJ)?** Apenas para Pessoa Física.
     
32.  **O cancelamento da portabilidade pelo cliente no aplicativo da credora é obrigatório?** Sim, é obrigatório.
     
33.  **Quais modalidades de Crédito Pessoal não estão inclusas nesta primeira entrega?** Empréstimos com antecipação (Ex.: FGTS, 13º salário, Imposto de Renda, etc), empréstimos com qualquer tipo de garantia, empréstimos atrelados a limite de crédito e empréstimos com fluxo de pagamento irregular.
     
34.  **Com a disponibilização do fluxo de PC no OFB, ainda será possível realizar a solicitação de PC via registradora (Núclea)?** Sim, será possível, porém será necessário que a instituição credora implemente políticas para impedir simultaneidade.
     
35.  **A oferta de contraproposta diminuirá as chances de a instituição credora ofertar a melhor taxa na adesão do contrato? Existirá limite de contraproposta?** Não, desde que as contrapropostas ocorram dentro de 3 dias úteis.
     
36.  **O que acontecerá se a instituição credora original não responder dentro de 3 dias úteis?** Trata-se de uma inconformidade da credora. O pedido ficará pendente de liquidação até atualização obrigatória de status pela credora original. Além disso, casos de inconformidade serão notificados ao Banco Central.
     
37.  **Para uma operação ser portada, ela precisa estar em dia?** Não há regulamentação específica. A decisão de portar ou não operações em atraso caberá à instituição proponente.
     
38.  **Para operações portadas via OFB, é necessário que a Núclea seja notificada ao término do processo?** Não, exceto em casos de simultaneidade.
     
39.  **Qual o procedimento se o cliente solicitar a portabilidade por diferentes IFs para o mesmo contrato em vias distintas?** A regra de simultaneidade será por ordem de solicitação.
     
40.  **Durante a jornada de portabilidade, se o cliente falecer, como será tratada a contraproposta?** O prazo de 3 dias úteis para a contraproposta será respeitado, a menos que haja manifestação para aceitá-la ou cancelar o pedido original.
     
41.  **Se a proponente faz uma proposta ao cliente com base no saldo devedor em D0, o cliente assina concordando com essa proposta e, em D3, o saldo devedor é atualizado, como ficam os valores pactuados com o cliente e o valor a ser enviado à credora original?** No momento da assinatura do contrato, o cliente deve ser informado sobre a possibilidade de atualização/oscilação no saldo devedor. Dessa forma, ele estará ciente de que poderá haver alterações nos valores pactuados inicialmente, decorrentes da variação do saldo na data da liquidação.
     
42.  **Há algum horário limite para o pagamento da proponente no caso de conquista de um contrato?** Para viabilizar o pagamento no mesmo dia, a instituição credora deve atualizar o status do pedido até às 10h. No exemplo apresentado, como a atualização ocorreu às 23h (fora do horário previsto), o prazo para o pagamento será o dia útil seguinte.
     
43.  **E se o cliente decidir não prosseguir com a portabilidade, mesmo sem receber uma contraproposta?** É necessário registrar o aceite do cliente? Para casos de desistência, a única ação da instituição (credora ou proponente) é registrar o desejo do cliente por meio da mudança de estado para Cancelled.
     
44.  **Sobre a simultaneidade: caso o cliente já esteja com um pedido de portabilidade em andamento, a instituição proponente terá acesso ao saldo devedor?** A instituição proponente terá acesso aos dados do contrato, incluindo o saldo devedor. No entanto, não será permitida uma nova solicitação de portabilidade para o mesmo contrato enquanto houver outro pedido em andamento
     
45.  **Quando o contrato está vinculado a um FIDC, a norma de Portabilidade de Crédito também se aplica?** Não. A portabilidade no OFB é apenas para CPC (Crédito Pessoal Clean) neste momento.
     
46.  **O cliente precisa cancelar manualmente o pedido de portabilidade após aceitar uma contraproposta da credora?** Não. A aceitação da contraproposta implica atualização automática do status pelo credor.
     
47.  **A nova proposta deve replicar o número original de parcelas do contrato ou considerar apenas o saldo remanescente?** Deve considerar apenas as parcelas restantes, nunca ultrapassando o contrato original.
     
48.  **A periodicidade da nova proposta pode ser alterada?** Não. Deve ser mantida exatamente como no contrato original.
     
49.  **O que acontece se houver variação no saldo devedor?** Se a variação for superior a 15%, a proponente pode cancelar a portabilidade. A tolerância não se aplica à quantidade de parcelas.
     
50.  **Será possível realizar “troca de modalidade” nos pedidos de portabilidade?** Não. Apenas CPC para CPC.
     
51.  **Haverá cobrança por parte do OFB sobre os pedidos de portabilidade?** A adesão ao OFB é gratuita. Outras taxas estão em análise.
     
52.  **O prazo de 3 dias úteis para a etapa de contraproposta se aplica a todos os produtos?** Inicialmente apenas para CPC, mas deve ser aplicado ao Consignado Federal.
     
53.  **O fluxo do Open Finance será integrado ao da Núclea?** Não. Os fluxos são independentes. A Núclea será informada apenas para visibilidade institucional.
     
54.  **Está circulando um cronograma do Open Finance 2025–2026 que apresenta datas diferentes para testes e go live. Essas datas estão corretas?** Sim, refletem as datas do escopo inicial do projeto.
     

-   **Tema: UX**
    

55.  **Em relação à área de gestão de contratos, onde o cliente pode consultar status e valores: a credora também precisa disponibilizar essa visualização?** Sim. A credora deverá exibir comparativo entre contrato original, proposta e contraproposta.
     
56.  **Existe uma jornada de retenção válida mesmo sem oferta de melhores condições para o cliente?** Sim. Direciona para a jornada de cancelamento por desistência.
     
57.  **As recomendações de cancelamento pelo usuário nos canais da credora, bem como o envio de notificações descritas no guia de UX, são obrigatórias? E como será feita a homologação dessas experiências?** Sim, algumas são obrigatórias conforme escopo regulatório. O cancelamento deve estar disponível nos canais da credora e da proponente. A homologação de UX será comunicada posteriormente.
     
58.  **O guia de UX define como deve ser a tela ou apenas o conteúdo apresentado?** Define apenas as informações obrigatórias, não o design.
     
59.  **Em relação ao guia de UX, a última atualização incluiu como requisito que a instituição proponente e a instituição credora notifiquem o cliente a cada mudança de status do pedido de portabilidade. Isso não pode impactar negativamente a experiência do cliente?** Cada instituição é responsável pelas notificações relativas às suas próprias ofertas.
     
60.  **O cancelamento da portabilidade pelo cliente no aplicativo da credora é obrigatório?** Sim, é obrigatório.
     
61.  **Existe uma jornada de retenção válida mesmo sem oferta de melhores condições?** Sim. Está previsto no guia como possibilidade válida.
     
62.  **Ainda sobre a jornada de retenção, será considerada válida uma contraproposta com refinanciamento?** Não. O escopo atual contempla apenas portabilidade de crédito.
     
63.  **O cliente precisa cancelar manualmente o pedido após aceitar uma contraproposta?** Não. A aceitação e o cancelamento são eventos distintos. O sistema atualiza automaticamente.
     
64.  **As recomendações de cancelamento pelo usuário nos canais da credora, bem como o envio de notificações descritas no guia de UX, são obrigatórias?** Sim. O cancelamento deve estar disponível nos canais digitais da proponente e da credora. Algumas notificações são obrigatórias. O formato é flexível, mas o conteúdo é obrigatório.
     
65.  **A definição sobre quais informações devem estar visíveis na tela principal ou em detalhes também é livre?** Não. A nova versão do guia trará definição obrigatória para garantir consistência.
     

# 7\. Glossário

● **API:** Interface de Programação de Aplicações.

● **BCB:** Banco Central do Brasil.

● **CCB:** Cédula de Crédito Bancário.

● **CET:** Custo Efetivo Total.

● **CPC:** Crédito Pessoal Clean.

● **GT:** Grupo de Trabalho.

● **IF:** Instituição Financeira.

● **Núclea:** Plataforma de registro de operações de crédito.

● **OFB:** Open Finance Brasil.

● **PC:** Portabilidade de Crédito.

● **PRD:** Documento de Requisitos de Produto.

● **RCO:** Ressarcimento de Custo de Originação.

● **STR:** Sistema de Transferência de Reservas.

● **TED:** Transferência Eletrônica Disponível.

● **UUID:** Universally Unique Identifier.

● **IPCA:** Índice Nacional de Preços ao Consumidor Amplo

● **IGP-M:** Índice Geral de Preços – Mercado

# 8\. Apêndice

Escopo Portabilidade de crédito: Material fornecido pelo regulador com o escopo da portabilidade de crédito.

# 9\. Referências

Relatórios de economia bancária (Edição de [2019](https://www.bcb.gov.br/content/publicacoes/relatorioeconomiabancaria/REB_2019.pdf), [2020](https://www.bcb.gov.br/content/publicacoes/relatorioeconomiabancaria/REB_2020.pdf), [2021](https://www.bcb.gov.br/content/publicacoes/relatorioeconomiabancaria/REB_2021.pdf) e [2022](https://www.bcb.gov.br/publicacoes/relatorioeconomiabancaria)) indicam um alto potencial de operações para portabilidade, assim como uma falta de conhecimento do público sobre esse serviço).
