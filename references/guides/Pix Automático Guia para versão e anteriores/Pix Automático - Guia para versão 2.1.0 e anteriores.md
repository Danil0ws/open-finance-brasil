# Pix Automático - Guia para versão 2.1.0 e anteriores

## 1 - Introdução

### 1.1 - Sobre o documento

Este guia auxiliará os implementadores a compreenderem as funcionalidades de criação do consentimento com pagamento de adesão ou sem no momento da contratação do serviço. Para o processo de liquidação dos pagamentos, abordaremos o funcionamento da primeira ordem de pagamento de um ciclo de cobrança, das tentativas no mesmo dia e das tentativas em dias subsequentes. Além disso, também temos as regras de negócio que compõe o produto no âmbito do Open Finance.

Não é o objetivo que a leitura deste documento substitua a leitura de outros documentos de igual importância. Recomendamos a leitura de todos os documentos relacionados para permitir o correto entendimento sobre a operação deste produto. Alguns exemplos de documentos importantes:

**Normativo/Manual/Documento**

**Tema**

[Resolução Conjunta Nº 1, Versão vigente compilada (v7)](https://normativos.bcb.gov.br/Lists/Normativos/Attachments/51028/Res_Conj_0001_v7_L.pdf)

Dispõe sobre a implementação do Open Finance.

[Instrução Normativa BCB Nº 512](data/references/Instrução_Normativa_BCB_512.md)

Dispõe sobre os limites de valor para as transações no âmbito do Pix.

[Instrução Normativa BCB Nº 513](data/references/Instrução_Normativa_BCB_513.md)

Estabelece os procedimentos operacionais relativos ao Pix Automático.

Diretrizes Técnicas e Operacionais do Open Finance

Dispõe sobre procedimentos técnicos e operacionais aos quais as instituições devem adotar (Inclui orientações para reportes à PCM, o Guia De Experiencia, entre outros).

### **1.2 - Pix Automático**

É uma solução que permite o recebedor solicitar o pagamento de cobranças recorrentes de maneira automatizada. Isso ocorre após o usuário pagador conceder permissão ao recebedor, no contexto do serviço contratado. A funcionalidade possibilita que o recebedor PJ, através de seu PSI, envie regularmente os detalhes das cobranças recorrentes ao PSP do Pagador (dentro de uma periodicidade previamente definida) este, por sua vez, agenda o débito e efetua a liquidação automaticamente na data programada, conforme o contrato de serviços estabelecido entre usuário pagador e recebedor. A implementação do Pix Automático é obrigatória para as detentoras que atendem clientes PF e PJ, porém, instituições que atendem apenas clientes PJ ou que não desejem ofertar o produto para o público PJ, podem realizar o _optout_ junto ao BCB, conforme especificado na IN BCB 581, de 30/12/2024.

Essa funcionalidade está presente na API de pagamentos automáticos, a partir de sua versão 2.0.0. O link para a API pode ser encontrado abaixo.

-   Pagamentos automáticos
    

## 2 - Regras para _Pix Automático_ no _OFB_

### 2.1 - Regras de negócio:

No quadro abaixo podemos observar as regras de negócio definidas para o produto Pix Automático no âmbito do Open Finance.

 **Cenários**

**Pix Automático**

**Casos de uso**  
(Sugestões BC)

Utilities/serviços públicos, assinaturas, escolas, academias, aluguel, seguros, cobranças de pagamento de operação de crédito

**Configurações de recorrência**

**Motor de recorrência**

Criação de um consentimento para recorrência com limites de valores e prazos, e definição de periodicidade

**Valor**

Fixo ou variável

**Modelo de recorrência, intervalos de pagamentos**

Semanal, mensal, trimestral, semestral e anual

**Gestão da Agenda**

Compartilhada: Iniciador tem visibilidade completa, PSP pagador tem visibilidade com antecedência de 2 a 10 dias das próximas incidências

**Comanda o pagamento**

Iniciador

**Recebedor**

PJ

**Primeiro pagamento**

Imediato ou Agendado

**Demais pagamentos**

Agendado

**Permite pagamentos imediatos**

Sim, para adesão

**Definição do final do período da recorrência**

Opcional

**Prazo máximo de duração para recorrência do consentimento**

Opcional

**Permite a configurar data de início do consentimento?**

Sim

**Permite a configurar data de expiração do consentimento?**

Sim

**Permite limites globais do consentimento?¹**

Não

**Permite limites periódicos por consentimento?**

Sim, uma transação liquidada com sucesso por período de recorrência.

**Permite limites por transação?**

Sim. Recebedor pode definir valor mínimo. Pagador pode definir um valor máximo. O valor definido pelo Pagador não pode ser menor que o valor definido pelo Recebedor.

**Processo de adesão**

**Fluxo de adesão**

Consentimento FAPI _long-lived tokens_

_**Role**_ **no diretório**

CONTA, PAGTO

**Será possível editar configurações de recorrência no processo de adesão no Detentor?**

Não

**Cancelamento do fluxo da adesão**

Via Iniciador ou Detentor

**Permite múltiplas alçadas?**

Sim

**Iniciador terá acesso aos status do processo de adesão via Webhook?**

Sim

**Adesão tem id de contrato?**

Sim

**Gestão de adesão**

**Permite edição técnica dos dados do consentimento pós adesão²?**

Sim, verificar no link

**Cancelamento da adesão**

Pelo pagador, no ambiente da iniciadora ou detentora. Recebedor pode acionar o Iniciador para o cancelamento.

**Revogação da adesão**

Iniciador ou Detentor poderão revogar a adesão por motivos de fraude

**Consumação³ da adesão?**

Detentor, apenas para recorrências com data de expiração definidas.

**Processo de liquidação**

**Canal para liquidação**

Serão utilizados os canais primário e secundário (obedecendo as regras da trilha Pix). Quem deverá criar o E2EID com a data da liquidação é o Iniciador.

**Dispara o pagamento⁴**

Detentor

**Onde o cliente cancela o pagamento?**

Iniciadora ou Detentora

**Erros de saldo insuficiente modificam o status do consentimento?**

Não, sendo o pagamento imediato (da adesão) ou agendado (da adesão ou recorrência). Diferente do arranjo Pix, onde, em algumas das jornadas, a falha no pagamento da adesão resulta no cancelamento da autorização

**Listagem das informações do pagamento**

Busca por id do consentimento e por id de pagamento

**Iniciador é responsável pelo envio da ocorrência do pagamento?**

Sim, no prazo de 2 a 10 dias anteriores a data de vencimento da cobrança

**Quem avisa o pagador sobre pagamento com falha?**

Iniciador e Detentor¹. Detentor deverá notificar o iniciador e o iniciador decidir se e como notificar o pagador

**Responsável pela geração do endToEndId**

Iniciador

**Podem ocorrer liquidação em dias não úteis?**

Sim, em casos em que a data de vencimento ocorra durante finais de semana, feriados e dias inexistentes(29, 30, 31), a data pode ser alterada, a critério do recebedor, para o dia útil seguinte.

**Qual é o localInstrument utilizado na liquidação?**

MANU

**A data do primeiro pagamento (agendado ou imediata) da contratação do serviço (adesão) pode ser posterior ou igual à data do agendamento da primeira recorrência?**

A data da primeira ocorrência de um pagamento associado a um ciclo de cobrança deve ser **posterior** a data de liquidação do pagamento da adesão ao serviço. Em outras palavras, só pode haver cobrança de recorrência após a data de liquidação da adesão.

**Outras informações**

**É possível habilitar crédito?**

Seguir a regra do arranjo. Habilitar na detentora no momento da adesão do consentimento. Na confirmação do consentimento é necessário um aviso ao cliente que o uso de linha de crédito pré-aprovada na instituição detentora de conta está habilitado e poderá ser alterado na detentora em ambiente de gestão do Pix Automático.

**Tentativas para pagamentos que falharam**

Detentor realiza primeira tentativa das 0h – 8h. Segunda tentativa entre 18h – 21h. Caso de falha, recebedor pode solicitar ao iniciador envio de novas tentativas (contando que o pagador tenha aceito e o motivo do erro permita). Novas tentativas de liquidação devem ocorrer em até 7 dias corridos após a primeira tentativa. São permitidas no máximo 3 retentativas, totalizando 4 tentativas de liquidação para um mesmo pagamento. Iniciador deve informar ao detentor que o recebedor deseja ativar as retentativas, pagador deve autorizar em momento de consentimento.

**Funcionalidade de contestação**

Contestação está disponível no arranjo Pix automático, conforme pode ser visto na Página 84, Requisito 4, Requisitos Mínimos para Experiencia do Usuário, versão 7.0

#### **Legenda**

##### 1 - GT está avaliando se existe alguma normativa que obrigue uma das partes avisar ao pagador

### 2.2 Regras de notificação:

-   Notificações ao usuário pagador relacionadas ao consentimento (ou seja à permissão/autorização) devem, obrigatoriamente, ser enviadas pela ITP, não podendo ser desabilitadas pelo usuário.
    
    -   É opcional para a detentora o envio dessas notificações, exceto nos casos relacionados a alteração de valor máximo e utilização do limite de crédito, quando também deverá obrigatoriamente notificar o cliente em caso de alteração.
        
-   Notificações ao usuário pagador relacionadas a agendamento e liquidação de pagamentos deverão estar habilitadas por padrão na detentora de conta, de acordo com o especificado nas regras do arranjo.
    
-   Apenas notificações de sucesso de agendamento poderão ser desabilitadas pelos usuários na detentora de conta. As demais permanecerão ativas, também seguindo o definido pelo arranjo.
    
-   O envio de notificações ao usuário pagador sobre agendamento e liquidações por parte da ITP é opcional. Se implementadas, deve ser permitido que possam ser desabilitadas pelo usuário.
    
-   A detentora de conta deverá comunicar todas as ocorrências de sucesso/não sucesso de agendamentos e pagamentos à ITP, para que esta avalie se deseja ou não notificar também o cliente.
    
    -   A comunicação será realizada via Webhook e o ITP precisará consultar o recurso antes de realizar a avaliação.
        
-   É **vedado** à ITP o encaminhamento ao recebedor de mensagens de erro e motivos de rejeição que especifiquem que houve falha no pagamento por insuficiência de saldo ou de limites. Nesses casos, a comunicação ao recebedor sobre o não processamento do pagamento deve ser feita de modo genérico, com a orientação de que o usuário pagador busque informações em sua detentora de conta.
    
-   É **vedado** à ITP permitir ao recebedor o acesso a informações sobre valor máximo definido pelo cliente, bem como suas alterações.
    

## 3 - Descrição de fluxos

### 3.1- Para criação do consentimento:

Diferente dos pagamentos realizados via agendamento recorrente ou pagamentos imediatos, o Pix Automático possui consentimentos de longa duração, os quais poderão ter alguns parâmetros editados ao longo da sua vida útil. Entraremos mais no detalhe do processo de criação do consentimento a seguir.

### 3.1.1 - Jornada 1 - Fluxo da criação do consentimento sem pagamento de adesão

Serviços que não possuem pagamento de adesão são aqueles que, geralmente, paga-se pelo consumo, como serviços de energia elétrica, água e gás. Esta jornada trata desde a solicitação de autorização até a sua conclusão.

![ConsentimentoPixAutomaticoSemAdesao\_Novo-20250226-164135.png](images/ConsentimentoPixAutomaticoSemAdesao_Novo-20250226-164135.png)

**ID**

**CAMADA**

**TIPO**

**DESCRIÇÃO**

1

Usuário Pagador

Ação

Pagador acessa ambiente do recebedor e manifesta a intenção de contratar um dos serviços ofertados.

2

Usuário Pagador

Ação

Em ambiente do Recebedor: Pagador seleciona Pix Automático via Open Finance como forma de pagamento pelo serviço.

3

Usuário Pagador

Ação

Em ambiente do Recebedor: Pagador informa seus dados de pagamento e, opcionalmente, configura parâmetros de limite para a transação.

4

Usuário Pagador

Comunicação

Em ambiente do Recebedor: Dados são repassados ao Iniciador.

5

Iniciador

Comunicação

Recebe os dados enviados do Recebedor e inicia o processo de criação do consentimento.

6

Iniciador

Ação

Valida as informações recebidas do Recebedor.

7

Iniciador

Ação

Iniciador prepara o payload de envio do consentimento de longa duração atentando-se ao produto para o qual este consentimento está sendo criado.  
Antes do envio o iniciador deve realizar a solicitação de token de acesso. Grant-type e scopes podem ser encontrado na especificação da API.

8

Iniciador

Comunicação

Envia solicitação de criação de consentimento de longa duração para o Detentor.

9

PSP Pagador (Detentor)

Comunicação

Recebe a solicitação de criação de consentimento de longa duração enviada pelo Iniciador.

10

PSP Pagador (Detentor)

Ação

Processa a solicitação de consentimento recorrente.

11

PSP Pagador (Detentor)

Comunicação

Retorna sucesso na criação do consentimento de longa duração para o Iniciador junto a URL de redirecionamento.

12

Iniciador

Comunicação

Recebe o sucesso na criação do consentimento de longa duração e URL de redirecionamento.

13

Iniciador

Ação

Processa o retorno da solicitação de criação do consentimento de longa duração.

14

Iniciador

Comunicação

Redireciona o pagador para autenticação no Detentor.

15

Usuário Pagador

Ação

Em ambiente do PSP Pagador: Realiza a autenticação.

16

Usuário Pagador

Ação

Em ambiente do PSP Pagador: Autoriza o consentimento.

17

Usuário Pagador

Ação

Em ambiente do PSP Pagador: PSP Pagador muda o consentimento para o status **AUTHORISED**.

18

Usuário Pagador

Ação

Em ambiente do PSP Pagador: PSP Pagador notifica os demais aprovadores solicitando a aprovação em caso de múltiplas alçadas.

19

Usuário Pagador

Comunicação

Em ambiente do PSP Pagador: PSP Pagador redireciona o usuário pagador para o ambiente do Iniciador.

20

Iniciador

Comunicação

Recebe informações do redirecionamento.

21

Iniciador

Ação

Valida informações recebidas.

22

Iniciador

Ação

Realiza consulta ao PSP do Pagador para verificar o estado do consentimento. AUTHORISED indica que o consentimento foi autorizado pelo cliente. Porém, caso a consulta retorne o valor REJECTED, deve-se abortar o processo de consentimento e pagador e recebedor devem ser comunicados da falha.

23

Iniciador

Comunicação

Notifica o pagador do resultado do processo de consentimento (do pagador ao serviço de cobranças recorrentes).

24

Pagador

Comunicação

Recebe notificação do resultado do processo de consentimento/autorização

25

Iniciador

Comunicação

Aguarda até que o(s) usuário pagador tenha realizado a aprovação do consentimento para notifica-lo do sucesso no processo de adesão.

26

Recebedor

Comunicação

Notifica o recebedor do resultado da adesão/consentimento

### 3.1.2 - Jornada 2 - Fluxo da criação do consentimento com pagamento de adesão

A adesão ao serviço é considerado como o primeiro pagamento relacionado aquela contratação do serviço, em outras palavras, é o pagamento inicial para utilização de algum serviço contratado. Alguns exemplos de serviços que possuem essa característica são os de streaming, alugueis de bens e matrículas. Esta jornada trata desde a solicitação de autorização até a sua conclusão.

![ConsentimentoPixAutomaticoComAdesao-20250226-162538.png](images/ConsentimentoPixAutomaticoComAdesao-20250226-162538.png)

**ID**

**CAMADA**

**TIPO**

**DESCRIÇÃO**

1

Usuário Pagador

Ação

Pagador acessa ambiente do recebedor e manifesta a intenção de contratar um dos serviços ofertados.

2

Usuário Pagador

Ação

Em ambiente do Recebedor: Pagador seleciona Pix Automático via Open Finance como forma de pagamento pelo serviço.

3

Usuário Pagador

Ação

Em ambiente do Recebedor: Pagador informa seus dados de pagamento e, opcionalmente, configura parâmetros de limite para a transação.

4

Usuário Pagador

Comunicação

Em ambiente do Recebedor: Dados são repassados ao Iniciador.

5

Iniciador

Comunicação

Recebe os dados enviados do Recebedor e inicia o processo de criação do consentimento.

6

Iniciador

Ação

Valida as informações recebidas do Recebedor.

7

Iniciador

Ação

Iniciador prepara o payload de envio do consentimento de longa duração atentando-se ao produto para o qual este consentimento está sendo criado.

8

Iniciador

Comunicação

Envia solicitação de criação de consentimento de longa duração para o Detentor (**POST** /consents).  
Deve possuir o objeto “/data/recurringConfiguration/automatic/firstPayment” preenchido.  
Antes do envio o iniciador deve realizar a solicitação de token de acesso. “Grant-type” e “scopes” podem ser encontrado na especificação da API.

9

PSP Pagador (Detentor)

Comunicação

Recebe a solicitação de criação de consentimento de longa duração enviada pelo Iniciador.

10

PSP Pagador (Detentor)

Ação

Processa a solicitação de consentimento de longa duração.

11

PSP Pagador (Detentor)

Comunicação

Retorna sucesso na criação do consentimento de longa duração para o Iniciador junto a URL de redirecionamento.

12

Iniciador

Comunicação

Recebe o sucesso na criação do consentimento de longa duração e URL de redirecionamento.

13

Iniciador

Ação

Processa o retorno da solicitação de criação do consentimento de longa duração.

14

Iniciador

Comunicação

Redireciona o pagador para autenticação no Detentor.

15

Usuário Pagador

Ação

Em ambiente do PSP Pagador: Realiza a autenticação.

16

Usuário Pagador

Ação

Em ambiente do PSP Pagador: Autoriza o consentimento. É vetada a edição dos dados da recorrência pelo usuário pagador. Os dados que podem ser editados durante a autorização podem ser encontrados no guia de experiência do usuário do Open Finance Brasil

17

Usuário Pagador

Ação

Em ambiente do PSP Pagador: PSP Pagador muda o consentimento para o status **AUTHORISED**.

18

Usuário Pagador

Ação

Em ambiente do PSP Pagador: PSP Pagador notifica os demais aprovadores solicitando a aprovação em caso de múltiplas alçadas.

19

Usuário Pagador

Comunicação

Em ambiente do PSP Pagador: PSP Pagador redireciona o usuário pagador ambiente do Iniciador.

20

Iniciador

Comunicação

Recebe informações do redirecionamento.

21

Iniciador

Ação

Valida informações recebidas.

22

Iniciador

Ação

Realiza consulta ao PSP do Pagador para verificar o estado do consentimento. AUTHORISED indica que o consentimento foi autorizado pelo cliente. Porém, caso a consulta retorne o valor REJECTED, deve-se abortar o processo de consentimento e o recebedor deve ser comunicado da falha.

23

Iniciador

Comunicação

Notifica o pagador do resultado da etapa de concessão da autorização de cobranças para o recebedor(consentimento).

24

Usuário Pagador

Comunicação

Recebe a notificação do resultado da etapa de concessão da autorização de cobranças para o recebedor(consentimento).

25

Iniciador

Ação

Monta o payload com a ordem de pagamento que faz parte da adesão ao serviço.  
O payload deve conter os dados do pagamento da adesão com os mesmos valores declarados no objeto “`/data/recurringConfiguration/automatic/firstPayment`”.  
A consistência de titularidade será realizada pelo arranjo Pix, exceto para os casos em que o PSP do Pagador e PSP do recebedor sejam a mesma instituição, nesses casos, a detentora deve garantir a titularidade do recebedor sobre a conta de crédito.

26

Iniciador

Comunicação

Envia requisição para criação da ordem de pagamento (**POST** /pix/recurring-payments)

27

PSP Pagador (Detentor)

Comunicação

Recebe solicitação para criação da ordem de pagamento

28

PSP Pagador (Detentor)

Ação

Valida solicitação de pagamento recebida pelo Iniciador.

29

PSP Pagador (Detentor)

Ação

Cria a solicitação de pagamento conforme solicitado pelo Iniciador e autorizado pelo usuário pagador durante o processo de autorização do consentimento recorrente.

30

PSP Pagador (Detentor)

Comunicação

Notifica o pagador do resultado. Se for um pagamento imediato, deve ser informado o resultado da tentativa de liquidação. Caso seja agendado, deve-se notificar sobre o agendamento. Independente do resultado do pagamento imediato ou da solicitação de agendamento, o consentimento não deve ser revogado pelo PSP do Pagador.

31

Usuário Pagador

Comunicação

Recebe a notificação do resultado da solicitação de pagamento da adesão

32

PSP Pagador (Detentor)

Comunicação

Retorna para o iniciador o resultado da solicitação de pagamento da adesão

33

Iniciador

Comunicação

Recebe o resultado da criação do pagamento

34

Iniciador

Comunicação

Notifica o recebedor do resultado da solicitação de pagamento da adesão

35

Recebedor

Comunicação

Recebe a notificação do resultado. Caso o resultado não atenda as expectativas para o serviço sendo contratado, o recebedor pode solicitar o cancelamento do pagamento agendado (quando aplicável) e/ou a revogação do consentimento.

### 3.2 - Para edição do consentimento:

A edição deverá ser feita via _endpoint_ `PATCH /recurring-consents/{recurringConsentId}`. As regras para edição podem ser encontradas na descrição do _endpoint_ e no _header_ da API . Atentem que os campos que permitem edição poderão ser modificados, cabendo a cada instituições acompanhar a página referenciada na descrição do _endpoint_ `PATCH /recurring-consents/{recurringConsentId}`.

A maneira de preencher os campos do payload de edição é de crucial importância, uma vez que, a critério do usuário pagador, será possível a edição tanto do valor máximo permitido por transação quanto do prazo de expiração para indeterminados. Para permitir o correto entendimento de solicitações nesse cenário, onde o usuário pagador desejar alterar os mencionados parâmetros para “inderterminado”, os campos `"/data/recurringConfiguration/automatic/maximumVariableAmount"` e `"/data/expirationDateTime"` devem ser omitidos no payload de requisição ao endpoint `PATCH /recurring-consents/{recurringConsentId}`. Caso um dos dois, ou os dois campos, não sejam informados, o detentor de contas deve considerar que a solicitação também envolve a alteração desses valores para “indeterminado”. A partir do momento que a requisição de edição for processada com sucesso pelo detentor de contas, os campos `"/data/recurringConfiguration/automatic/maximumVariableAmount"` e `"/data/expirationDateTime"` também não retornaram nas consultas do consentimento, uma vez que não há um valor definido para representar “indeterminado”.

### 3.3 - Para revogação do consentimento:

Tratando agora dos motivos de revogação, uma regra é que: Para um consentimento de longa duração ser revogado, primeiro ele precisou ser aprovado. Apenas consentimentos no status “AUTHORISED”, são passíveis de revogação, vamos trazer os motivos de revogação e como eles se aplicam.

-   REVOGADO\_RECEBEDOR: O recebedor pode solicitar, via Iniciador, a revogação de um consentimento. Um exemplo seria o termino de um contrato de streaming, onde o provedor do serviço de streaming (recebedor) poderia solicitar a revogação quando o usuário logado em algum de seus canais solicitar o cancelamento do serviço.
    
-   REVOGADO\_USUARIO: Por definição, toda primeira solicitações de cobrança de uma recorrência, no Pix Automático, precisam ser agendadas com 2 a 10 dias de antecedência e o usuário pagador pode cancelar qualquer pagamento agendado na sua conta até as 23h59 do dia anterior ao dia definido para liquidação. Sendo assim, caso um usuário solicite a revogação um consentimento e este possua um pagamento associado já agendado para ocorrer, deve-se então validar a data de solicitação da revogação e a data de liquidação do pagamento. Caso a data de revogação do consentimento seja a mesma de liquidação do pagamento, o pagamento será liquidado normalmente e o consentimento de longa duração será revogado, não permitindo novos agendamentos de cobrança e qualquer pagamento agendado para datas posteriores devem ser cancelados.
    
-   NAO\_INFORMADO: Deve ser utilizado para motivos de revogação que envolvam informações que não devem ser compartilhadas no ecossistema por respeito a privacidade do usuário. Ex: Suspeita de Fraude, Bloqueio Judicial.
    

#### 3.4 - Do processo de liquidação

Neste capítulo, veremos como fica o fluxo de liquidação para o Pix Automático. Serão dois fluxos, um tratando da criação do primeiro agendamento por ciclo de cobrança, enquanto o segundo tratará das novas tentativas de liquidação, caso o pagamento original do ciclo falhe.

#### 3.4.1 - Fluxo para criação da primeira ordem de pagamento de um ciclo de cobrança

![LiquidacaoPixAutomatico-20250107-212431.png](images/LiquidacaoPixAutomatico-20250107-212431.png)

**ID**

**CAMADA**

**TIPO**

**DESCRIÇÃO**

1

Empresa Recebedora

Ação

Inicia processo de cobrança.

2

Empresa Recebedora

Ação

Busca informações de pagamento do usuário dentro da sua base.

3

Empresa Recebedora

Comunicação

Envia cobrança para o Iniciador.

4

Iniciador

Comunicação

Recebe solicitação de cobrança.

5

Iniciador

Ação

Valida informações recebidas.

6

Iniciador

Ação

Cria a solicitação de pagamento.

7

Iniciador

Comunicação

Envia solicitação de pagamento.

8

PSP Pagador (Detentor)

Comunicação

Recebe solicitação de pagamento.

9

PSP Pagador (Detentor)

Ação

Processa a solicitação de pagamento.

10

PSP Pagador (Detentor)

Ação

Agenda o pagamento futuro conforme solicitado. Deve validar as regras aplicáveis para primeira tentativa de um ciclo, como, por exemplo, o prazo mínimo de agendamento, 10 a 2 dias de antecedência, conforme IN BCB 513.

11

PSP Pagador (Detentor)

Comunicação

Retorna sucesso na solicitação de agendamento de pagamento.

12

Iniciador

Comunicação

Recebe sucesso na solicitação de agendamento de pagamento.

13

Iniciador

Ação

Processa o retorno da criação de pagamento.

14

Iniciador

Ação

Consulta informações do pagamento até que ele esteja no status ACSC. Consideramos aqui o sucesso do pagamento como o estado objetivo de finalização da operação de pagamento. Caso deseje notificar o sucesso do agendamento, o Iniciador pode considerar o estado SCHD e proceder com a notificação junto ao recebedor.

15

Iniciador

Comunicação

Notifica ao recebedor sucesso no pagamento.

16

Empresa Recebedora

Comunicação

Recebe notificação de sucesso no pagamento.

17

Empresa Recebedora

Comunicação

Notifica pagador do sucesso no pagamento.

18

Usuário Pagador

Comunicação

Recebe notificação de sucesso no pagamento via comunicação do Recebedor. Essa comunicação não é padronizada pelo Open Finance Brasil.

19

PSP Pagador (Detentor)

Comunicação

Notifica o pagador de novo agendamento na sua conta.

20

Usuário Pagador

Comunicação

Recebe notificação de sucesso no agendamento.

#### 3.4.2 - Fluxo para criação de novas tentativas de liquidação para uma cobrança original que falhou

Foi criado um mecanismo que permite a realização de novas tentativas de liquidação para um pagamento original de um ciclo que falhou. Detalhes deste mecanismo podem ser encontrados na página que trata exclusivamente desse tema, presente na parte de informações gerais da API Pagamentos Automáticos. O fluxo abaixo representa desde a identificação da falha da cobrança original até a realização da primeira nova tentativa que exija um novo endToEndId.

![FluxoRetentativasPixAutomatico-20250115-011248.png](images/FluxoRetentativasPixAutomatico-20250115-011248.png)

**ID**

**CAMADA**

**TIPO**

**DESCRIÇÃO**

1

Empresa Recebedora

Ação

Identifica que o pagamento original ou uma nova tentativa não foi liquidada com sucesso

2

Empresa Recebedora

Comunicação

Notifica o Iniciador para iniciar uma nova tentativa de pagamento para liquidação da cobrança

3

Iniciador

Comunicação

Recebe a notificação da Empresa Recebedora para uma nova tentativa de liquidação para a cobrança

4

Iniciador

Ação

Para decidir como prosseguir, o Iniciador precisa se atentar a três pontos.  
1 - Caso o erro seja referente a primeira tentativa de liquidação realizada pelo detentor entre 00h~08h, o Iniciador deve conferir qual o motivo de rejeição associado ao pagamento solicitado. Se o motivo de rejeição for algum dos que, conforme a tabela presente na página “Tentativas Intradia e Extradia para Pix Automático”, exige um novo endToEndId, este deve ser enviado através de um novo pagamento até as 12h do mesmo dia;  
2 - Caso o erro não exija um novo endToEndId, o ITP deve aguardar a nova tentativa de liquidação que será realizada pelo detentor sem necessidade de sensibilização do detentor pelo ITP;  
3 - Caso o erro seja relacionado a segunda tentativa de liquidação prevista para o dia (independente de ter sido criada pelo Iniciador até as 12h daquele dia ou ser a cobrança original que falhou), se permitido pelo usuário em seu consentimento e a critério do recebedor, o Iniciador pode criar uma nova tentativa de liquidação em até 7 dias posteriores a falha da cobrança original. Essa cobrança deve ocorrer, obrigatoriamente, com a data de liquidação sendo D+1, onde D é o dia da solicitação.

A partir da análise dos pontos acima, o Iniciador pode montar o _payload_ de requisição que será repassado ao detentor, onde deve ser informado, no campo `originalRecurringPaymentId`, o identificador(`recurringPaymentId`) da tentativa original de pagamento que não foi liquidada com sucesso. Além de que, caso ocorra o descrito no item 2, não há ação prevista para o Iniciador e o fluxo não deve prosseguir.

5

Iniciador

Ação

Cria a solicitação de pagamento agendado para a nova tentativa de liquidação.

6

Iniciador

Comunicação

Realiza a chamada ao endpoint `POST /pix/recurring-payments`, passando o payload montado na etapa 4.

7

PSP Pagador (Detentor)

Comunicação

Recebe a solicitação de criação de uma nova tentativa de pagamento agendado

8

PSP Pagador (Detentor)

Ação

Avalia as informações recebidas no payload. Deve identificar que é uma nova tentativa, uma vez que o campo `originalRecurringPaymentId` esta preenchido. Também realiza as validações síncronas previstas na criação de pagamentos.

9

PSP Pagador (Detentor)

Ação

Processa o pedido de agendamento realizando as validações assíncronas

10

PSP Pagador (Detentor)

Decisão

Detentor deve avaliar se o caso informado é uma tentativa intradia ou extradia. Para as tentativas intradia, além de possuir o item no campo `originalRecurringPaymentId`, o pagamento recebido terá a data do dia atual, do recebimento da requisição. Já as tentativas em dias diferente devem possuir a data de liquidação D+1, ou seja, além do campo `originalRecurringPaymentId` estar presente, a data de liquidação é para um dia posterior ao dia atual. Independente de ser tentativa intradia ou extradia, o detentor deverá mover o pagamento para SCHD antes de seguir as demais etapas da máquina.

11

PSP Pagador (Detentor)

Ação

Aplica as validações para pagamentos intradia - Valida se o payload possui as mesmas informações da solicitação original, exceto endToEndId e, possível, `originalRecurringPaymentId`

12

PSP Pagador (Detentor)

Ação

Aplica as validações para agendamento de pagamentos extradia - Valida se o payload possui as mesmas informações da solicitação original, exceto endToEndId, data e `originalRecurringPaymentId`

13

PSP Pagador (Detentor)

Ação

Cria o débito na conta do usuário pagador

14

PSP Pagador (Detentor)

Ação

Prepara notificação para o pagador, informando que um novo débito foi agendado na sua conta.

15

PSP Pagador (Detentor)

Comunicação

Envia a notificação para o usuário pagador sobre o novo débito agendado na sua conta.

16

Usuário Pagador

Comunicação

Recebe a notificação com a informação do débito agendado na sua conta

17

PSP Pagador (Detentor)

Comunicação

Retorna HTTP 201 de criação da ordem de pagamento ao iniciador

18

Iniciador

Comunicação

Recebe o sucesso na criação da nova tentativa de pagamento para a cobrança

19

Iniciador

Ação

Processa o retorno da solicitação, recuperando o `recurringPaymentId`

20

Iniciador

Ação

Loop para consulta do estado do pagamento na instituição detentora até que o mesmo encontre-se em SCHD

21

Iniciador

Comunicação

Envia notificação ao recebedor informando-o sobre o sucesso do agendamento do pagamento solicitado

22

Empresa Recebedora

Comunicação

Recebe notificação do ITP/PSP Recebedor informando o sucesso do agendamento do pagamento solicitado

23

Iniciador

Comunicação

Envia notificação ao recebedor informando-o sobre a falha do agendamento do pagamento solicitado

24

Empresa Recebedora

Comunicação

Recebe notificação do ITP/PSP Recebedor informando a falha do agendamento do pagamento solicitado

Maiores detalhes sobre o fluxo de novas tentativas para um mesmo ciclo podem ser encontrados na página Tentativas Intradia e Extradia para Pix automático - v2.0.0-beta.1 - \[SV\] Pagamentos Automáticos .
