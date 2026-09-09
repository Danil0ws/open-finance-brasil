# Pix Automático e Transferências Inteligentes

## 1 - Histórico de versionamento

O Guia segue seu próprio versionamento. Cada versão do documento é salva com um numero incremental: 0.1, 0.2, 0.3 sucessivamente, até que a versão do documento seja aprovada e publicada. Com a publicação, passa a ser versão 1.0. Versões editadas subsequentemente a versão inicial publicada, passam a ser 1.1, 1.2, ..., 1.x. Sendo "x" um número que represente mudanças pequenas, conhecidas como _minor_. Se a mudança proposta for considerada uma _major_, mudamos a numeração completa, indo para 2.0, 3.0, etc.

O GT especificações e serviços será o responsável por definir o versionamento do documento para cada uma das alterações futuras.

## 2 - Introdução

Bem-vindo ao guia do Pix Automático e Transferências Inteligentes, exploraremos essas funcionalidades no cenário do Open Finance Brasil. Este guia destina-se a oferecer uma compreensão aprofundada de ambas as ferramentas, delineando como são implementadas no contexto do Open Finance Brasil e como podem transformar a maneira como usuários lidam com suas finanças.

**Pagamentos Automáticos:**

A funcionalidade de Pagamentos Automáticos foi projetada para simplificar a vida financeira, permitindo que o usuário agende débitos automáticos de serviços prestados por pessoas jurídicas. Seja o pagamento de contas de concessionárias de energia ou serviços de streaming, essa ferramenta oferece a conveniência de agendar pagamentos automáticos de forma flexível, mensal, semanal ou diária. Para clientes pessoa natural, o Pagamento Automático é obrigatório de ser ofertado, enquanto para pessoas jurídicas é opcional, proporcionando uma solução abrangente para suas necessidades de pagamento via Pix.

**Transferências Inteligentes:**

No universo do Open Finance Brasil, a funcionalidade de Transferências Inteligentes destaca-se como uma abordagem estratégica para a gestão inteligente de saldos em contas relacionadas. Seja para consumidores individuais ou empresas, essa ferramenta torna obrigatório aos detentores de conta oferecer uma solução que permita a transferência automática de fundos.

Ao explorar este guia, você terá uma visão detalhada das funcionalidades de Pagamentos Automáticos e Transferências Inteligentes, e como ambas podem aprimorar seus processos financeiros.

Essa funcionalidade está presente na API de pagamentos automáticos, a partir de sua versão 1.0.0. O link para a API pode ser encontrado abaixo.

-   Pagamentos automáticos
    

## 3 - Regras de negócios para _Pagamentos Automáticos_ e _Transferências Inteligentes_

No quadro abaixo, entraremos com mais detalhes sobre as regras de negócio de cada um dos produtos de pagamento automáticos, o que deve-se considerar quando consumir o serviço e quais são os parâmetros necessários para utilizar corretamente os tipos de pagamentos descritos e passíveis de realização em seus diferentes modelos.

**Pagamento Automático**

**Transferências Inteligentes**

**Casos de uso**  
(Sugestões BC)

Utilities/serviços públicos, assinaturas, escolas, academias, aluguel, seguros, cobranças de pagamento de operação de crédito

Transferências Inteligentes e similares (investimentos inteligentes, proteção contra uso desnecessário de cheque especial)

**Configurações de recorrência**

**Motor de recorrência**

Criação de um consentimento para recorrência com limites de quantidade, valores e prazos

Criação de um consentimento para recorrência com limites de quantidade, valores e prazos

**Valor**

Fixo ou variável

Fixo ou variável

**Modelo de recorrência, intervalos de pagamentos**

Diário, semanal, mensal ou anual, atentando-se aos dias úteis e regras dos feriados locais, considerar o dado do cadastro do pagador na detentora.

Restrito aos limites definidos no consentimento

**Gestão da Agenda**

Compartilhada: Iniciador tem visibilidade completa, PSP pagador tem visibilidade com antecedência de 2 a 10 dias das próximas incidências

Iniciador

**Comanda o pagamento**

Iniciador

Iniciador

**Recebedor**

PJ

PN ou PJ de mesma titularidade

**Primeiro pagamento**

Imediato ou Agendado

Imediato

**Demais pagamentos**

Agendado

Imediato

**Permite pagamentos imediatos**

Sim

Sim

**Definição do final do período da recorrência**

Opcional

Opcional

**Prazo máximo de duração para recorrência do consentimento**

Opcional

Opcional

**Permite a configurar data de início do consentimento?**

Sim

Sim

**Permite a configurar data de expiração do consentimento?**

Sim

Sim

**Permite limites globais do consentimento?¹**

Não

Não

**Permite limites periódicos por consentimento?**

Não

Sim

**Permite limites por transação?**

Sim

Sim

**Processo de adesão**

**Fluxo de adesão**

Consentimento FAPI _long-lived tokens_

Consentimento FAPI _long-lived tokens_

_**Role**_ **no diretório**

CONTA, PAGTO

CONTA, PAGTO

**Será possível editar configurações de recorrência no processo de adesão no Detentor?**

Não

Não

**Cancelamento do fluxo da adesão**

Via Iniciador ou Detentor

Via Iniciador ou Detentor

**Permite múltiplas alçadas?**

Sim

Sim

**Iniciador terá acesso aos status do processo de adesão via Webhook?**

Sim

Sim

**Adesão tem id de contrato?**

Sim

Não

**Gestão de adesão**

**Permite edição técnica dos dados do consentimento pós adesão²?**

Sim, verificar no link

Não

**Cancelamento da adesão**

Pelo pagador, no ambiente da iniciadora ou detentora

Pelo pagador, no ambiente da iniciadora ou detentora

**Revogação da adesão**

Iniciador ou Detentor poderão revogar a adesão por motivos de fraude

Iniciador ou Detentor poderão revogar a adesão por motivos de fraude

**Consumação³ da adesão?**

Detentor

Detentor

**Processo de liquidação**

**Canal para liquidação**

Serão utilizados os canais primário e secundário (obedecendo as regras da trilha Pix, com liquidações em dias úteis). Quem deverá criar o E2EID com a data do próximo dia útil é o iniciador, com base no cadastro do usuário pagador no detentor

Primário  
(Seguir a utilização e regras do arranjo)

**Dispara o pagamento⁴**

Detentor

Iniciador

**Onde o cliente cancela o pagamento?**

Iniciadora ou Detentora

Não é possível

**Erros de saldo insuficiente modificam o status do consentimento?**

Se pagamento imediato falhar, sim.  
Se agendamento de cobrança, não.

Não

**Listagem das informações do pagamento**

Busca por id do consentimento

Busca por id do consentimento

**Iniciador é responsável pelo envio da ocorrência do pagamento?**

Sim, no prazo de 2 a 10 dias anteriores a data da ocorrência do pagamento

Sim, imediatamente

**Quem avisa o pagador sobre pagamento com falha?**

Iniciador e Detentor⁵. Detentor deverá notificar o iniciador e o iniciador decidir se e como notificar o pagador

Iniciador

**Responsável pela geração do endToEndId**

Iniciador

Iniciador

**A data agendada no consentimento e a data agendada do E2EID podem ser distintas?**

Sim, em casos de finais de semana e feriados as datas podem ser alteradas. Atenção aos dias 29, 30 de fevereiro, a liquidação ocorre no próximo dia útil.

Não

**Qual é o localInstrument utilizado na liquidação?**

MANU

DICT, INIC e MANU

**Outras informações**

**É possível habilitar crédito?**

Seguir a regra do arranjo. Habilitar na detentora no momento da adesão do consentimento. Na confirmação do consentimento é necessário um aviso ao cliente que o uso de linha de crédito pré-aprovada na instituição detentora de conta está habilitado e poderá ser alterado na detentora em ambiente de gestão do Pix Automático.

Sim - Conteúdo explicativo no header da API de pagamentos

**Retentativas**

Primeira tentativa das 0h – 8h. Segunda tentativa entre 15h – 17h. Não aplicável para o dia seguinte.

Não

**Funcionalidade de contestação**

Cliente deverá entrar em contato com o recebedor - **Discutir com o BC como adotar no Open Finance e se adotar.**

Não

#### **Legenda**

##### 1 - Limite específico para um determinado consentimento, por exemplo, limite de R$100 por dia (periódico) ou R$300 para o intervalo do consentimento (global)  
2 - O GT questionou o BC sobre o comportamento esperado quando houver a edição –se o usuário deverá ser redirecionado para a detentora ou não para confirmar os novos dados do consentimento  
3 - Entende-se como consumação a mudança do estado, por exemplo, após 10/10 parcelas o estado será alterado de aprovado para consumido  
4 - Responsável por garantir que no momento do agendamento a liquidação ocorra  
5 - GT está avaliando se existe alguma normativa que obrigue uma das partes avisar ao pagador

## 4 - Descrição da usabilidade para Pix Automático e Transferências Inteligentes

#### 4.1- Adesão aos produtos

Diferente dos pagamentos realizados via agendamento recorrente ou pagamentos imediatos, o Pix Automático e as Transferências Inteligentes possuem consentimentos de longa duração, os quais poderão ser editados ao longo da sua vida útil. Entraremos mais no detalhe do processo de adesão a seguir.

##### 4.1.1 - Fluxo da adesão

![Imagem: BPMN com fluxo da adesão recorrentes do Pix Automático e Transferências Inteligentes](images/AdesaoPixAutomatico-20231016-211347.png)

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

Comunicação

Solicita ao Detentor o access\_token para a criação do consentimento.

8

PSP Pagador (Detentor)

Comunicação

Recebe a solicitação de criação de access\_token para criação de consentimento de longa duração enviada pelo Iniciador.

9

PSP Pagador (Detentor)

Ação

Processa a solicitação de access\_token para criação de consentimento de longa duração enviada pelo Iniciador.

10

PSP Pagador (Detentor)

Comunicação

Retorna ao Iniciador o access\_token solicitado.

11

Iniciador

Comunicação

Recebe o access\_token enviado pelo Detentor.

12

Iniciador

Ação

Iniciador prepara o payload de envio do consentimento de longa duração atentando-se ao produto para o qual este consentimento está sendo criado.

13

Iniciador

Comunicação

Envia solicitação de criação de consentimento de longa duração para o Detentor.

14

PSP Pagador (Detentor)

Comunicação

Recebe a solicitação de criação de consentimento de longa duração enviada pelo Iniciador.

15

PSP Pagador (Detentor)

Ação

Processa a solicitação de consentimento de longa duração.

16

PSP Pagador (Detentor)

Comunicação

Retorna sucesso na criação do consentimento de longa duração para o Iniciador junto a URL de redirecionamento.

17

Iniciador

Comunicação

Recebe o sucesso na criação do consentimento de longa duração e URL de redirecionamento.

18

Iniciador

Ação

Processa o retorno da solicitação de criação do consentimento de longa duração.

19

Iniciador

Comunicação

Redireciona o pagador para autenticação no Detentor.

20

Usuário Pagador

Ação

Em ambiente do PSP Pagador: Realiza a autenticação.

21

Usuário Pagador

Ação

Em ambiente do PSP Pagador: Autoriza o consentimento.

22

Usuário Pagador

Ação

Em ambiente do PSP Pagador: PSP Pagador muda o consentimento para o status **AUTHORISED**.

23

Usuário Pagador

Ação

Em ambiente do PSP Pagador: PSP Pagador notifica os demais aprovadores solicitando a aprovação em caso de múltiplas alçadas.

24

Usuário Pagador

Comunicação

Redireciona o usuário para a aplicação do Iniciador.

25

Iniciador

Comunicação

Recebe informações do redirecionamento.

26

Iniciador

Ação

Valida informações recebidas.

27

Iniciador

Ação

Consulta status do consentimento.

28

Iniciador

Comunicação

Notifica o recebedor do sucesso na adesão.

29

PSP Recebedor

Comunicação

Recebe notificação do sucesso da adesão.

30

Iniciador

Comunicação

Notifica o pagador do sucesso na adesão.

31

Usuário Pagador

Comunicação

Recebe a notificação de sucesso.

Agora, precisamos detalhar melhor o comportamento esperado tanto do Iniciador quanto do Detentor em alguns dos passos descritos acima, são eles:

12 - "Cria o consentimento (POST /recurring-consents)"note

Regras, restrições e orientações de preenchimento dos campos podem ser encontrados na especificação da API.

Regras, restrições e orientações de preenchimento dos campos podem ser encontrados na especificação da API.

1.  Diferentes produtos, mesma api, diferentes maneiras de utilizar
    

-   Pagamentos automáticos e Transferências Inteligentes (Assim como o VRP) vão utilizar o mesmo endpoint de criação de consentimentos de longa duração, o `POST /recurring-consents`;
    
-   O payload de criação do consentimento contém o objeto `"recurringConfiguration"`, o qual atende ao conceito de `oneOf`, onde cada uma das possibilidades de preenchimento representam um produto e cada um dos produtos estarão associados a um único consentimento de longa duração;
    
-   Agora, pensando em casos de uso e em como utilizar o endpoint de criação de consentimentos de longa duração, vamos considerar dois casos de uso. O primeiro, para exemplificar o Pagamento Automático, é a adesão de um usuário a um serviço de assinatura de _streaming_ qualquer. Já o segundo caso de uso que abordaremos aqui, para exemplificar Transferências Inteligentes, será o investimento inteligente, entraremos nos detalhes de cada um a seguir.
    

2.  No exemplo de pagamento mensal de streaming via API de Pagamento automático onde o usuário aplica valor máximo de R$100,00 para o consentimento, precisamos antes definir alguns pontos, são eles:
    

-   Produtos dessa natureza comumente exigem um pagamento imediato para permitir o consumo do serviço pelo usuário Pagador imediatamente, caso o pagamento imediato seja necessário, o payload precisará ser preenchido de acordo, como veremos mais a frente. Abaixo, vamos descriminar algumas definições necessárias para o entendimento do preenchimento do payload.
    
    -   O valor base da assinatura será R$50,00.
        
        -   Esse valor não é enviado na criação do consentimento de longa duração.
            
        -   O campo “`/data/recurringConfiguration/automatic/amount`" representa que é um valor fixo de cobrança mensal.
            
        -   O campo “`/data/recurringConfiguration/automatic/transactionLimit`" representa que é um valor de cobrança mensal com um limite máximo por cobrança definido pelo usuário.
            
    -   O cliente pode comprar produtos dentro da plataforma que aumentem o valor da cobrança, assim como mudar seu plano para valores maiores ou menores e continuar com seu consentimento válido;
        
    -   Há um pagamento imediato também no valor de R$ 50,00;
        
    -   O usuário determinou que o consentimento irá durar um ano, a partir da data de criação, aqui definida como por exemplo 22/09/2023;
        
    -   No payload abaixo, iremos exemplificar como ficaria a solicitação de criação de consentimento de longa duração que respeite esses critérios:
        

Notem que: O objeto `"recurringConfiguration"` recebeu as informações necessárias exclusivamente para o Pix Automático.

3.  Considerem agora o caso de uso mencionado para Transferências Inteligentes, o investimento inteligente, onde o usuário, mensalmente, envia uma transferência entre diferentes instituições para realização de investimentos.
    

-   Como no caso de uso anterior, precisamos definir algumas regras para entendermos a aplicação;
    
    -   O investimento ocorrerá semanalmente, todas as quinta-feiras, a partir do dia 22/09/2023;
        
    -   O valor de investimento fixo foi definido como R$150,00, observem no payload abaixo que este valor não aparece em canto nenhum, isto se dá devido ao fato do campo “`/data/recurringConfiguration/sweeping/amount`" ser o valor máximo total permitido para ser transacionado via este consentimento, enquanto o campo "`/data/recurringConfiguration/sweeping/transactionLimit`" representa o limite máximo por transação, independente de qualquer limite periódico, sendo os outros campos de "transactionLimit", pertencentes ao objeto "periodicLimits", abaixo do "`/data/recurringConfiguration/sweeping/transactionLimit`" em ordem de validação.
        
    -   Podem ocorrer ofertas de investimentos que aumentem o valor investido durante o mês, por isso o usuário definiu um limite de R$1000,00;
        
    -   Para facilitar a gestão de quantos investimentos ele tem, o usuário decidiu que, por mês, ele vai fazer no máximo dez investimentos;
        
    -   O usuário também definiu que esse investimento em um ano, valor total investido por ele chegue até a R$5000,00.
        
    -   A duração do consentimento, ou seja, sua data de expiração (que também foi definida pelo usuário) é de um ano.
        

**Importante:**

-   Como podem observar, temos um campo do tipo array presente na criação do consentimento, o “`/data/creditors/`" Para o produto Pix Automático, não há a possibilidade de mais de um item nesse array, uma vez que este campo representa as contas que irão receber a transação, a cada consentimento, para o Pix Automático que pode possuir apenas uma conta como destino.
    
    -   Agora, quando falamos de Transferências Inteligentes, esse campo pode ser preenchido com quantos itens forem necessários, de acordo com a solicitação do cliente de com quantas e quais contas ele deseja habilitar a funcionalidade. O Iniciador deverá solicitar ao usuário a lista de _creditors accounts_.
        
        -   Usuários PJ podem cadastrar contas com CNPJ de mesma raiz (8 primeiros dígitos do CNPJ), como em casos de empresas com matriz e filial
            
            -   O PSP pagador deverá validar se os CNPJs que constam no payload possuem a mesma raiz e as permissões necessárias para fazer as movimentações.
                

note

Se uma instituição desejar implementar algum caso de uso que precise da informação de saldo de contas do usuário em outra(s) instituição(ões), como por exemplo, cobertura automática de saldo negativo via API de pagamentos automáticos (Ex. aplicativos de gestão financeira pessoal - _PFM_), precisa também de um consentimento de fase 2 (Dados do cliente), o qual permite a consulta do saldo pela instituição. O consentimento de longa duração exclusivo de fase 3 (Serviços - Pagamentos) não da acesso a essa informação.

Se uma instituição desejar implementar algum caso de uso que precise da informação de saldo de contas do usuário em outra(s) instituição(ões), como por exemplo, cobertura automática de saldo negativo via API de pagamentos automáticos (Ex. aplicativos de gestão financeira pessoal - _PFM_), precisa também de um consentimento de fase 2 (Dados do cliente), o qual permite a consulta do saldo pela instituição. O consentimento de longa duração exclusivo de fase 3 (Serviços - Pagamentos) não da acesso a essa informação.

15 - "Processa solicitação de consentimento de longa duração"

-   A partir do sucesso da chamada deste passo, iniciam-se as validações assíncronas do consentimento.
    
-   Detentor precisa realizar as validações assíncronas levando em consideração os momentos descritos no quadro abaixo.
    

**Etapa Fluxograma do Pagamento Automático**

**Erros possíveis**

**Observações sobre os erros**

19.  Redireciona usuário para aplicação do detentor
     

FALHA\_INFRAESTRUTURA

Ocorreu um problema na infraestrutura interna do Detentor

NAO\_INFORMADO

Validações internas realizadas pelo Detentor (ex. análise de fraudes)

TEMPO\_EXPIRADO\_AUTORIZACAO

Usuário não concluiu a autorização do consentimento

20.  Realiza Autenticação
     

FALHA\_INFRAESTRUTURA

Ocorreu um problema na infraestrutura interna do Detentor

TEMPO\_EXPIRADO\_AUTORIZACAO

Usuário não concluiu a autorização do consentimento

REJEITADO\_USUARIO

Usuário, enquanto visualizava a tela de autenticação, resolveu cancelar a transação.

NAO\_INFORMADO

Validações internas realizadas pelo Detentor (ex. análise de fraudes)

21.  Autoriza o consentimento
     

FALHA\_INFRAESTRUTURA

Ocorreu um problema na infraestrutura interna do Detentor

CONTAS\_ORIGEM\_DESTINO\_IGUAIS

As contas definidas como recebedora e pagadora são as mesmas

CONTA\_NAO\_PERMITE\_PAGAMENTO

O tipo de conta recebedora não permite o crédito do pagamento.

SALDO\_INSUFICIENTE

Caso exista um pagamento imediato declarado na criação do consentimento e o mesmo não possa ocorrer por falta de saldo

VALOR\_ACIMA\_LIMITE

Caso exista um pagamento imediato declarado na criação do consentimento e o mesmo não possa ocorrer por exceder o limite definido pelo usuário na instituição, no arranjo ou qualquer outro considerado pelo Detentor

REJEITADO\_USUARIO

O usuário, na tela de autorização do consentimento, não o autorizou.

VALOR\_INVALIDO

O valor enviado pelo Iniciador não é válido para o pagamento solicitado.

NAO\_INFORMADO

Validações internas realizadas pelo Detentor (ex. análise de fraudes)

25.  Retorna access\_token
     

FALHA\_INFRAESTRUTURA

Ocorreu um problema na infraestrutura interna do Detentor

TEMPO\_EXPIRADO\_CONSUMO

Iniciador não concluiu o pagamento com consentimento aprovado

NAO\_INFORMADO

Validações internas realizadas pelo Detentor (ex. análise de fraudes)

-   A instituição Detentora precisa estar atenta durante o processamento da solicitação de consentimento referente a presença do objeto “**/data/recurringConfiguration/automatic/immediatePayment**”. Caso esse campo esteja preenchido, o detentor deverá, em momento posterior a criação do consentimento permitir uma solicitação de pagamento imediata que siga os parâmetros definidos dentro do objeto.
    
-   Serviços dessa natureza, geralmente exigem esse pagamento para que a assinatura seja válida. Para não gerar inconsistência entre consentimentos de longa duração aprovados e quais realmente estarão em uso, caso um consentimento de longa duração possua, na sua criação, uma declaração de pagamento imediato e o cliente não possuir saldo ou limite no momento da adesão, o PSP do pagador deve rejeitar assincronamente o consentimento e utilizar o “`rejection/reason/code`" cabível:
    
    -   Caso o cliente tenha limite habilitado na conta selecionada mas o valor cobrado seja superior ao limite disponível, preencher o “`rejection/reason/code`" com **VALOR\_ACIMA\_LIMITE**;
        
    -   Caso o cliente não tenha limite e o saldo disponível em conta não é suficiente, preencher o “`rejection/reason/code`" com o valor **SALDO\_INSUFICIENTE**.
        

27 - "Consulta status do consentimento"

-   Na situação onde o iniciador possui o mecanismo de Webhook, não há necessidade de realizar as consultas (GET /recurring-consents/{recurringConsentId}) durante esse passo, basta aguardar a notificação de alteração de status que virá do detentor e realizar uma única consulta já com a informação atualizada. Caso não possua Webhook, pode realizar o polling normalmente.
    
-   O atingimento de limites periódicos **não** move o consentimento para o status “**CONSUMED**”, apenas impede que outra transação ocorra dentro do período estipulado no preenchimento dos campos. Os casos que movem o consentimento para “**CONSUMED**” são:
    
    -   Ele ter chego na sua data de expiração;
        
    -   Atingir o valor definido no campo “`/data/recurringConfiguration/sweeping/amount`";
        
-   Caso seja interesse do usuário, ao utilizar o produto "Sweeping accounts" ele pode definir alguns dos limites, seja limite global de valor total (“`/data/recurringConfiguration/sweeping/totalAllowedAmount`"), limite de valor máximo por transação ("`/data/recurringConfiguration/sweeping/transactionLimit`") ou periódico (objeto "`/data/recurringConfiguration/sweeping/periodicLimits`").
    

##### 4.1.2 - Possibilidade de edição de consentimentos de longa duração para o Pix Automático

Instruções recebidas na consulta pública do Pix Automático deixaram claro a necessidade de permissão da edição de alguns parâmetros do consentimento tanto no ambiente do iniciador quanto no ambiente do PSP Pagador. A edição deverá ser feita via _endpoint_ `PATCH /recurring-consents/{recurringConsentId}`. As regras para edição podem ser encontradas na descrição do _endpoint_. Atentem que os campos que permitem edição poderão ser modificados a qualquer hora, sem a necessidade de versionamento da API, cabendo a cada instituições acompanhar a página referenciada também na descrição do _endpoint_ `PATCH /recurring-consents/{recurringConsentId}`.

##### 4.1.3 - Sobre rejeição e revogação de consentimentos de longa duração.

Existem algumas pequenas divergências de regras na revogação e rejeição do consentimento de longa duração entre os produtos Pix Automático e Transferências Inteligentes, vamos trazer primeiro os motivos de rejeição que possuem particularidades entre os produtos e explicar como trata-los.

-   SALDO\_INSUFICIENTE: Quando criado um consentimento de longa duração para o Pix Automático, é possível que o recebedor tenha estipulado um pagamento imediato para ocorrer neste consentimento. Sendo assim, apenas para este produto(Pix Automático) e no cenário do usuário não possuir saldo para o pagamento imediato, este erro poderá ser retornado. Consentimentos de longa duração criados para Transferências Inteligentes não possuem essa característica de cobranças imediatas declaradas no consentimento, portanto não há como fazer essa validação.
    
-   VALOR\_ACIMA\_LIMITE: O comportamento é semelhante ao do erro anterior (SALDO\_INSUFICIENTE). Pela regra do arranjo do Pix Automático, o limite definido pelo usuário pagador no PSP do pagador (que sempre estará habilitado para uso) em uma solicitação de criação de consentimento de longa duração. Caso exista um pagamento imediato, e essa solicitação de pagamento ultrapassa algum dos limites definidos pelo usuário, este erro deverá ser retornado. Transferências Inteligentes não possui essa validação para o consentimento, uma vez que não há declaração imediata de cobrança.
    
-   Os outros motivos de rejeição, tanto síncronos como assíncronos do consentimento de longa duração, seguem o mesmo comportamento para ambos os produtos e não necessitam de maiores explicações.
    

Tratando agora dos motivos de revogação, uma regra comum para ambos os produtos (Pix Automático e Transferências Inteligentes) é que para um consentimento de longa duração ser revogado, primeiro ele precisou ser aprovado. Apenas consentimentos no status “AUTHORISED”, independente do produto, são passíveis de revogação, vamos trazer os motivos de revogação e como eles se aplicam para cada produto.

-   REVOGADO\_RECEBEDOR: Aplicável apenas para o produto Pix Automático, uma vez que o recebedor pode solicitar, via Iniciador, a revogação de um consentimento. Um exemplo seria o termino de um contrato de streaming, onde o provedor do serviço de streaming (recebedor) poderia solicitar a revogação quando o usuário logado em algum de seus canais solicitar o cancelamento do serviço. Como Transferências Inteligentes caracteriza uma transferência de fundos de mesma titularidade, não há a figura do recebedor, apenas do usuário(que também pode ser considerado o recebedor), portanto tal motivo de revogação não se aplica.
    
-   REVOGADO\_USUARIO: Aplicável para ambos os produtos, porém com pequena particularidade para o produto Pix Automático. Por definição, todas as solicitações de cobrança no Pix Automático precisam ser agendadas com 2 a 10 dias de antecedência e o usuário pagador pode cancelar qualquer pagamento agendado na sua conta até as 23h59 do dia anterior ao dia definido para liquidação. Sendo assim, caso um usuário solicite a revogação um consentimento e este possua um pagamento associado já agendado para ocorrer, deve-se então validar a data de solicitação da revogação e a data de liquidação do pagamento. Caso a data de revogação do consentimento seja a mesma de liquidação do pagamento, o pagamento será liquidado normalmente e o consentimento de longa duração será revogado, não permitindo novos agendamentos de cobrança.
    
-   NAO\_INFORMADO: Deve ser utilizado para motivos de revogação que envolvam informações que não devem ser compartilhadas no ecossistema por respeito a privacidade do usuário. Ex: Suspeita de Fraude, Bloqueio Judicial.
    

#### 4.2 - Processo de liquidação

Apesar de ambos os produtos utilizarem-se dos mesmos endpoints, tanto para criação do consentimento quanto para a liquidação de um pagamento, as regras aplicadas a cada um deles são diferentes. Neste capítulo, veremos como fica o fluxo de liquidação para os casos de uso apresentados anteriormente.

#### 4.2.1 - Fluxo para liquidação do Pix Automático

![Imagem: BPMN com fluxo da liquidação de Transferências Inteligentes](images/LiquidacaoPixAutomatico-20231016-195026.png)

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

Busca informações de pagamento do usuário.

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

Comunicação

Envia solicitação de access\_token.

7

PSP Pagador (Detentor)

Comunicação

Recebe solicitação de access\_token.

8

Detentor

Ação

Processa solicitação de access\_token.

9

Detentor

Comunicação

Retorna acess\_token.

10

Iniciador

Comunicação

Recebe access\_token.

11

Iniciador

Ação

Processa retorno da solicitação de access\_token.

12

Iniciador

Ação

Cria a solicitação de pagamento.

13

Iniciador

Comunicação

Envia solicitação de pagamento.

14

PSP Pagador (Detentor)

Comunicação

Recebe solicitação de pagamento.

15

PSP Pagador (Detentor)

Ação

Processa a solicitação de pagamento.

16

PSP Pagador (Detentor)

Ação

Realiza a cobrança na conta de débito do pagador.

17

PSP Pagador (Detentor)

Ação

Agenda o pagamento futuro conforme solicitado.

18

PSP Pagador (Detentor)

Comunicação

Retorna sucesso na solicitação de pagamento e/ou agendamento de pagamento.

19

Iniciador

Comunicação

Recebe sucesso na solicitação de pagamento e/ou agendamento de pagamento.

20

Iniciador

Ação

Processa o retorno da criação de pagamento.

21

Iniciador

Ação

Consulta informações do pagamento.

22

Iniciador

Comunicação

Notifica ao recebedor sucesso na transferência.

23

Empresa Recebedora

Comunicação

Recebe notificação de sucesso na transferência.

24

Empresa Recebedora

Ação

Processamento interno do pagamento.

25

Empresa Recebedora

Comunicação

Notifica pagador do sucesso na transferência.

26

Usuário Pagador

Comunicação

Recebe notificação de sucesso na transferência.

Agora, precisamos detalhar melhor o comportamento esperado tanto do Iniciador quanto do Detentor em alguns dos passos descritos acima, são eles:

12 - "Cria solicitação de pagamento"

-   Sobre o access\_token que será utilizado na iniciação de pagamentos para o Pix Automático. Temos basicamente dois cenários possíveis:
    
    -   Primeiro caso: Considerado o mais simples, onde o iniciador possui um authorization\_code ainda válido, recebido durante o processo de adesão, o qual poderá utilizar para trocar por um access\_token e realizar a transação.
        
    -   Segundo caso: O iniciador está agendando uma transação quando o access\_token da adesão não é mais válido. Nesse cenário, o iniciador deve antes de criar uma solicitação de pagamento, realizar uma solicitação de _refresh\_token_ ao PSP do pagador. Informações sobre o mecanismo de _refresh\_token_ podem ser encontrados em \[PT\] Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3.
        
-   Considerando o primeiro caso de uso, “Pagamento mensal de streaming via API de Pagamento automático onde o usuário aplica valor máximo de R$100,00 para o consentimento”:
    
    -   Uma vez que há a presença do pagamento imediato, o iniciador pode gerar imediatamente uma cobrança na conta do usuário no PSP Pagador.
        
    -   Após 30 dias da adesão, ocorre novamente uma cobrança. A data dessa cobrança precisa ser agendada seguindo a regra do arranjo do Pix Automático, ou seja, 2 a 10 dias antes da sua data de liquidação o recebedor deve enviar a cobrança ao Iniciador, que por sua vez encaminha ao PSP do pagador. Além disso, temos mais algumas regras que são necessárias, sendo elas:
        
        -   A geração do endToEndId deve seguir a data de cadastro do usuário no PSP pagador. O campo “`/data/ibgeTownCode` “ será retornado obrigatoriamente na consulta do consentimento de longa duração(`GET /recurring-consents/{recurringConsentId}`) quando o consentimento estiver com status "AUTHORISED".
            
        -   Para o Pix Automático, pagamentos podem ocorrer apenas em dias úteis. Caso a data de liquidação caia em um dia que não seja considerado dia útil, o pagamento deve ser agendado para ocorrer no dia útil mais próximo, assim como o endToEndId também precisa ser ajustado para esse dia.
            
        -   Pagamentos imediatos declarados na criação do consentimento de longa duração podem ocorrer via canal primário e em qualquer horário.
            
    -   Uma vez que o recebedor exigiu uma cobrança imediata e o usuário autorizou essa cobrança, o iniciador precisa enviar o payload de pagamento:
        
    -   As cobranças subsequentes, como já mencionado, devem ocorrer entre 2 a 10 dias antes da data de liquidação.
        
    -   Caso exista a necessidade de enviar a solicitação de cobrança imediata e uma solicitação de cobrança agendada, para o mesmo consentimento de longa duração, devem ser feitas duas chamadas a API de pagamentos automáticos, no _endpoint_ `POST /pix/recurring-payments`, a primeira para o pagamento imediato, seguida de uma segunda requisição responsável por realizar o agendamento da cobrança na data especificada e seguindo todas as regras já mencionadas até aqui.
        

15 - "Processa solicitação de pagamento"

-   Nesta etapa, o PSP do pagador precisa validar as informações recebidas do iniciador e verificar se elas estão condizentes com as regras definidas na criação do consentimento de longa duração, alguns pontos a serem observados são:
    
    -   Valor da cobrança x Limite transacional: Caso o usuário tenha definido um limite transacional no iniciador no momento de adesão e a solicitação de cobrança ultrapasse esse limite, o detentor deve retornar o erro **VALOR\_ACIMA\_LIMITE**;
        
    -   Se a data enviada para liquidação condiz com as configurações de período aceitas pelo usuário pagador no momento da autorização;
        
    -   Além de todos os erros síncronos e assíncronos que podem ocorrer durante as validações e listados na especificação da API.
        

16 - "Realiza cobrança na conta de débito do pagador"

-   Quando, na criação do consentimento de longa duração, for declarada a necessidade de um pagamento imediato associado a este consentimento(objeto “`/data/recurringConfiguration/automatic/immediatePayment`" preenchido), é necessário que o detentor aceite uma requisição de pagamento com liquidação imediata. Pensando em casos de uso de serviços de streaming, seria a cobrança inicial para permissão de utilização do serviço até o próximo ciclo de fechamento.
    

17 - "Agenda pagamento futuro conforme solicitado"

-   Caso o serviço não possua uma cobrança imediata, caberá ao PSP do pagador validar se o agendamento segue as regras do arranjo Pix Automático, além das outras validações necessárias descritas no header da API de pagamentos automáticos.
    

21 - "Consulta informações do pagamento"

-   O iniciador, com posse do `recurringPaymentId`, precisa consultar o PSP do pagador, via _polling_ e no _endpoint_ GET `/pix/recurring-payments/{recurringPaymentId}`, o status da sua solicitação. Caso seja um pagamento imediato necessário à consolidação de um contrato, deve realizar a consulta até o atingimento do status final da liquidação, **ACSC**, confirmando assim a finalização da transação.
    
-   Para pagamentos automáticos agendados, deve-se consultar até que o mesmo possua o status **SCHD**.
    
-   Caso ocorra algum erro dentro do PSP Pagador durante o processamento da liquidação, também pode ser recuperado via chamada ao _endpoint_ supracitado.
    
-   Caso o iniciador queria consultar todos os pagamentos associados a um consentimento de longa duração específico, pode fazer via _endpoint_ `GET /pix/recurring-payments`, onde precisa passar um parâmetro do tipo query, o `recurringConsentId`, além de poder especificar períodos específicos de cobranças através dos campos `startDate` e `endDate`, também passados como parâmetros do tipo query.
    
-   Caso o Iniciador possua implementado o mecanismo de Webhook, não há necessidade de realizar consultas periódicas no PSP do pagador (_polling)_ para verificar o status do pagamento, basta aguardar a notificação via Webhook e realizar a consulta para verificar as alterações.
    

#### 4.2.2- Fluxo de liquidação de Transferências Inteligentes

![Imagem: BPMN com fluxo da liquidação de Transferências Inteligentes](images/LiquidacaoSweepingAccount-20231016-203039.png)

**ID**

**CAMADA**

**TIPO**

**DESCRIÇÃO**

1

Iniciador

Ação

Dispara processo de transferência

2

Iniciador

Ação

Busca informações de contas de usuário habilitadas por ele para realização da transferência

3

Iniciador

Ação

Analisa as regras definidas pelo usuário pagador no momento da criação do consentimento de longa duração

4

Iniciador

Comunicação

Envia solicitação de access\_token

5

PSP Pagador

Comunicação

Recebe solicitação de access\_token

6

PSP Pagador

Ação

Processa solicitação de access\_token

7

PSP Pagador

Comunicação

Retorna access\_token

8

Iniciador

Comunicação

Recebe access\_token

9

Iniciador

Ação

Processa retorno da solicitação de access\_token

10

Iniciador

Ação

Cria solicitação de transferência

11

Iniciador

Comunicação

Envia a solicitação de transferência

12

PSP Pagador

Comunicação

Recebe solicitação de transferência

13

PSP Pagador

Ação

Processa solicitação de transferência

14

PSP Pagador

Ação

Realiza a transferência de fundo

15

PSP Pagador

Comunicação

Retorna sucesso na solicitação de transferência

16

Iniciador

Comunicação

Recebe sucesso na transferência

17

Iniciador

Ação

Processa o retorno da transferência

18

Iniciador

Ação

Consulta informações da transferência

19

Iniciador

Comunicação

Notifica usuário contratante do sucesso na transferência

20

Iniciador

Comunicação

Notifica PSP recebedor do sucesso na transferência de fundos

21

Usuário contratante

Comunicação

Recebe notificação de sucesso na transferência

22

PSP Recebedor

Comunicação

Recebe notificação de sucesso na transferência

Entraremos em detalhes sobre alguns passos mencionado e o comportamento esperado pelos agentes envolvidos na transação

2 - "Busca informações de conta de usuário habilitadas"

-   As contas habilitadas são aquelas as quais o usuário possui um consentimento de longa duração válido entre o PSP Pagador e o Iniciador e que tenham sido liberadas para esta funcionalidade pelo usuário contratante do serviço.
    

3 - "Analisa as regras definidas pelo usuário pagador"

-   Usuário pagador ou usuário contratante, representam a mesma figura.
    
-   As regras aqui mencionadas nada mais são que os parâmetros definidos no corpo da mensagem de criação do consentimento de longa duração, caso necessário o Iniciador pode consultar essas regras/parâmetros realizando `GET /recurring-consents/{recurringConsentId}` no PSP do Pagador.
    
-   Para o caso de uso que vamos trabalhar como exemplo, também criamos essas regras, elas podem ser conferidas expandindo o tópico _12 - "Cria o consentimento (POST /recurring-consents)"_ item **3**, presente na etapa de adesão.
    

10 - "Cria solicitação de transferência"

-   Sobre o access\_token que será utilizado na iniciação de pagamentos para Transferências Inteligentes. Temos basicamente dois cenários possíveis:
    
    -   Primeiro caso: Considerado o mais simples, onde o iniciador possui um authorization\_code ainda válido, recebido durante o processo de adesão, o qual poderá utilizar para trocar por um access\_token e realizar a transação.
        
    -   Segundo caso: O iniciador está agendando uma transação quando o access\_token da adesão não é mais válido. Nesse cenário, o iniciador deve antes de criar uma solicitação de pagamento, realizar uma solicitação de _refresh\_token_ ao PSP do pagador. Informações sobre o mecanismo de _refresh\_token_ podem ser encontrados em \[PT\] Open Finance Brasil Financial-grade API Security Profile 1.0 Implementers Draft 3
        
-   Sinais de risco:
    
    -   Por se tratar de uma transferência automática entre instituições, por mais que exista a checagem de titularidade, entende-se que mais algumas informações podem ser necessárias para autorizar ou não a iniciação de pagamentos automáticos. A API de pagamentos automáticos, como o próprio nome deixa claro, poderá comandar solicitações de pagamento e transferências entre instituições de maneira automática, ou seja, pode ou não estar na presença do usuário. A API de pagamentos automáticos hoje possui, devido a necessidade do arranjo Pix, o mecanismo de temporização no qual as instituições utilizam para poder realizar algumas validações de antifraude, podendo o PSP do pagador aprovar ou negar a solicitação de pagamento advinda do iniciador.
        
    -   Para minimizar os riscos, foi colocado dentro do `POST /pix/recurring-payments` um objeto para receber informações sobre o usuário, seu dispositivo e sua conexão, aqui chamados de _Sinais de risco._
        
    -   O objeto que contem os sinais de risco é o “`/data/riskSignals`", sendo os sinais de risco divididos em duas categorias, uma representa o usuário online no ambiente do iniciador (o que será indicado pela preenchimento do objeto "`/data/riskSignals/manual`" e seus campos) ou sem a presença do usuário no ambiente do iniciador (indicado pelo preenchimento do objeto "`/data/riskSignals/automatic`" e seus campos).
        
-   Transferências automáticas entre contas de mesma titularidade podem ocorrer todos os dias da semana, em qualquer horário, devem ser liquidadas via canal primário e seguir as regras do arranjo.
    
-   Para o caso de uso que estamos tratando aqui, na primeira quinta-feira após o dia 22/09/2023, o iniciador deverá enviar uma requisição de pagamento automático (`POST /pix/recurring-payments`), contendo a primeira solicitação de transferência, assim como definido pelo usuário e sem a presença dele:
    
-   Agora, vamos fazer uma conta simples, se o usuário autorizou R$ 150,00 por semana, em 4 semanas são R$ 600,00. Após 33 semanas apenas de movimentações planejadas, sem nenhum investimento inteligente, teremos então um total de R$ 4.950,00 investidos, muito próximo do valor total especificado pelo usuário no momento de consentimento, que é de R$ 5.000,00 por ano. Sendo assim, o PSP Pagador (Detentor), na 34ª solicitação irá retornar um erro para o iniciador, informando que o limite definido pelo usuário foi atingindo.
    
-   Um outro limite possível de ser atingido é o limite de quantidades de transações, que por sua vez também é definido pelo usuário. No nosso exemplo, quando criamos o consentimento, definimos o limite de quantidade de investimentos por dia em 2, ou seja, a partir da terceira tentativa de investimento no mesmo dia, que esteja dentro do valor total permitido também por dia (R$ 500,00), um erro também será retornado.
    
-   Abaixo temos dois possíveis erros relacionados aos limites acima citados, são eles:
    
    -   `LIMITE_PERIODO_VALOR_EXCEDIDO`: É o erro aplicável no primeiro exemplo citado. Uma vez que a transação seria negada porque o limite que foi atingido foi o limite anual de valor definido pelo usuário (campo “`/data/recurringConfiguration/sweeping/periodicLimits/year/amount`" preenchido na criação do consentimento), impossibilitando novas transações. Importante salientar que, caso o Iniciador, ao invés de tentar fazer o valor de investimento com o valor predefinido pelo usuário fosse fazer um investimento inteligente, também consentido pelo usuário, no valor de R$ 50,00, seria aceito normalmente, pois não passaria o valor máximo definido para o período (1 ano).
        
    -   `LIMITE_PERIODO_QUANTIDADE_EXCEDIDO`: É o erro aplicável ao segundo exemplo. A transação seria negada não por ter atingindo uma quantidade pré definida de valores, mais sim uma quantidade pre definida de investimentos realizados em um determinado periodo definido pelo usuário (campo “`/data/recurringConfiguration/sweeping/periodicLimits/day/quantityLimit`" preenchido na criação do consentimento). Se o Iniciador tentar novamente no próximo dia e caso essa seja a única regra que estava impedindo-o de realizar a transferência, a transferência poderá ser realizada.
        

13 - "Processa solicitação de transferência"

-   Nesta etapa, o PSP do pagador precisa validar as informações recebidas do iniciador e verificar se elas estão condizentes com as regras definidas na criação do consentimento de longa duração, alguns pontos a serem observados são:
    
    -   Valor da transferência x Limite transacional: Caso o usuário tenha definido um limite transacional no iniciador no momento de adesão e a solicitação de transferência ultrapasse esse limite, o detentor deve retornar o erro **VALOR\_ACIMA\_LIMITE**;
        
    -   Se a data enviada para liquidação condiz com as configurações de período aceitas pelo usuário pagador no momento da autorização do consentimento;
        
    -   Além de todos os erros síncronos e assíncronos que podem ocorrer durante as validações e listados na especificação da API.
        

18 - "Consulta informações da transferência"

-   O iniciador, com posse do recurringPaymentId, precisa consultar o PSP do pagador, via _polling_ e no _endpoint_ GET `/pix/recurring-payments/{recurringPaymentId}`, o status da sua solicitação. Deve realizar a consulta até o atingimento do status final da liquidação, **ACSC** (caso tenha sido completada com sucesso) ou **RJCT** (caso tenha ocorrido algum problema na liquidação), confirmando assim a finalização da transação.
    
-   Caso ocorra algum erro dentro do PSP Pagador durante o processamento da liquidação, também pode ser recuperado via chamada ao _endpoint_ citado acima, observando os motivos de rejeição.
    
-   Caso o iniciador queria consultar todos os pagamentos associados a um consentimento de longa duração específico, pode fazer via _endpoint_ `GET /pix/recurring-payments`, onde precisa passar um parâmetro do tipo query, o `recurringConsentId`, além de poder especificar períodos específicos de cobranças através dos campos `startDate` e `endDate`, também passados como parâmetros do tipo query.
    
-   Caso o Iniciador possua implementado o mecanismo de Webhook, não há necessidade de realizar consultas periódicas no PSP do pagador (_polling)_ para verificar o status do pagamento, basta aguardar a notificação via Webhook e realizar a consulta para verificar as alterações.
