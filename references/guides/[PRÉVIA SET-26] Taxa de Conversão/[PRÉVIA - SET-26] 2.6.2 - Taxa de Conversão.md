# [PRÉVIA - SET/26] 2.6.2 - Taxa de Conversão

:warning:atlassian-warning#FFBDADwide1032

As alterações apresentadas nesta documentação entrarão em vigência **somente a partir do fechamento de setembro de 2026.**

Até lá, deve ser considerada a documentação atualmente vigente, disponível no link: 2.6.2 - Taxa de Conversão

:info:atlassian-info#F4F5F7wide1800none

# 1\. Controle de Versão

**Versão**

**Data**

**Resumo das Alterações**

1 

09/06/2026 

Versão inicial – compilação das três taxas (Dados, Pagamentos e Vínculo), fontes informacionais (Planilha e PCM) e estados de conformidade (Conforme, Tolerância e Diagnóstico) 

2 

13/07/2026 

Ajustes metodológicos em Pagamentos, alinhados com o BACEN: (i) remoção dos fluxos sem redirecionamento (FIDO Flow / JSR) do cálculo; (ii) adição dos Pagamentos Automáticos via PCM, com cálculo por média ponderada entre com redirecionamento e Automáticos. 

3

24/08/2026

A partir do fechamento de **setembro de 2026**, consolidado em **outubro de 2026**, as taxas de conversão de consentimento para Compartilhamento de Dados e Iniciação de Pagamento passam a ser calculadas exclusivamente a partir da **PCM (Plataforma de Coleta de Métricas)** para todos os conglomerados.

# 2\. Introdução e Objetivos

Esta métrica tem como propósito monitorar a eficiência das jornadas de compartilhamento de dados, iniciação de pagamentos e criação de vínculo dentro do ecossistema do Open Finance. O objetivo é assegurar padrões de conversão adequados, refletindo a qualidade e a eficácia dessas jornadas na facilitação de operações seguras e eficientes entre as instituições participantes e seus clientes.

wide1034

O painel nasce com a metodologia vigente calculada retroativamente, de forma a assegurar a comparabilidade da série histórica, considerando as alterações metodológicas comunicadas por meio do Informa [\[Open Finance\] Informa #908](https://us5.campaign-archive.com/?u=49f5ff8910ce85bdb1d9a7864&id=52eb5be1eb).

wide1030

Nenhuma métrica apresentada neste painel utiliza os dados de instituições marcadas como ambiente de teste (FVP). As instituições desconsideradas correspondem aos seguintes `orgid`'s:

-   d7384bd0-842f-43c5-be02-9d2b2d5efc2c
    

-   1dbfe32a-5f1e-4841-a30c-9f1b5f24ad36
    
-   b2a8233c-eda6-4c46-8263-813d71508f1b
    

# 3\. Sobre a Métrica

Esta métrica foca em três produtos, cada um representando uma jornada distinta para o cliente. As três métricas são comparadas a partir de uma meta calculada a partir da performance do ecossistema.

**I. Compartilhamento de dados:** A Taxa de Criação de Consentimento de Dados de Clientes é calculada com base na proporção de consentimentos autorizados com sucesso em relação ao número de solicitações válidas de criação de consentimentos, direcionadas para a instituição transmissora de dados.

**II. Iniciação de Transação de Pagamento:** A Taxa de Criação de Consentimento de Pagamentos é calculada com base na proporção de consentimentos autorizados com sucesso em relação ao número de solicitações válidas de criação de consentimentos, direcionadas para a instituição detentora.

**III. Vínculo:** A Taxa de Criação de Vínculo é calculada pela quantidade de vínculos autorizados em relação ao volume de solicitações válidas de criação de vínculo, direcionadas para a instituição detentora de conta.

## 3.1. **Fontes informacionais**

A apuração das taxas de conversão e o cálculo correspondente da meta (descrito na [**seção 6.1**](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/edit-v2/2080112653#6.1.-C%C3%A1lculo-das-Metas-\(TOP-3\))) utilizam como fonte exclusiva de dados a **Plataforma de Coleta de Métricas (PCM)**, uma plataforma centralizada da Estrutura de Governança do Open Finance que coleta as métricas a partir das chamadas de API entre os participantes. 

Vale ressaltar que no produto **Pagamentos**, a taxa é composta pela média ponderada entre **Pagamentos com redirecionamento** e **Pagamentos Automáticos (Pix Automático e Transferências Inteligentes)**, tendo como peso o **volume de solicitações de consentimento válidas** (Detalhado na seção 5.2.1). Ainda para Pagamentos, ficam **excluídos do cálculo os fluxos sem redirecionamento** (FIDO Flow / JSR), considerando-se exclusivamente pagamentos com redirecionamento. Adicionalmente, são considerados como sucesso não apenas os consentimentos reportados como autorizados, mas também aqueles **efetivamente utilizados pelo** _**client**_ **em APIs de consumo**, garantindo que a métrica reflita o uso real do consentimento. 

# 4\. Total de Solicitações de Criação de Consentimentos

O Total de Solicitações de Consentimento representa a volumetria de intenções de consentimento registradas via API antes de qualquer ação direta de autenticação pelo cliente final no ambiente da instituição financeira.

Para operacionalizar o cálculo do total de solicitações de consentimentos, apresentamos a seguir a lógica de códigos aplicável a cada produto:

Dados de Clientes1800true is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint = '/open-banking/consents/v3/consents' -- endpoint específico para dados de clientes and orgid = clientorgid\]\]>Vínculo1800true is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint = '/open-banking/enrollments/v2/enrollments' -- endpoint específico para vínculo and orgid = clientorgid\]\]>Pagamentos1800Pagamento com Redirecionamentotrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint = '/open-banking/payments/v4/consents' -- endpoint específico para pagamentos and ( coalesce(additionalinfo\_authorisationflowintent, additionalinfo\_authorisationflow) <> 'fido\_flow' or coalesce(additionalinfo\_authorisationflowintent, additionalinfo\_authorisationflow) is null ) -- additionalinfo específico para pagamentos and orgid = clientorgid\]\]>Pix Automáticotrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint like '%/automatic-payments/v2/recurring-consents' -- endpoint específico para pix and additionalinfo\_paymenttype = 'AUTOMATIC' --additionalinfo específico para pix and orgid = clientorgid\]\]>Transferências Inteligentestrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint like '%/automatic-payments/v2/recurring-consents' and (additionalinfo\_paymenttype = 'SWEEPING' or additionalinfo\_paymenttype is null) and orgid = clientorgid\]\]>

# 5\. Cálculo da Taxa de Conversão

#F4F5F7wide1800

**TAXA DE CONVERSÃO = ( QTD DE CONSENTIMENTOS AUTORIZADOS ) / ( QTD DE SOLICITAÇÕES DE CONSENTIMENTO VÁLIDAS )**

wide1540

A Taxa de Conversão também pode ser obtida por meio da análise do _funil de conversão (detalhado na_ _seção 9.5.__)_ disponível no painel de produtos, utilizando as etapas do funil na relação a seguir.

**TAXA DE CONVERSÃO = Consentimentos autorizados / (Consentimentos não autorizados visão negócio e /token + Consentimentos autorizados)**

## **5.1. Período de apuração**

Antes de detalhar o numerador e o denominador da taxa, é necessário definir o critério de apuração temporal do indicador. As taxas são calculadas **mensalmente**, com base em ciclos semanais que se iniciam aos **sábados** e encerram-se às **sextas-feiras**. Para fins de consolidação, uma semana pertence ao mês de referência quando a sua respectiva **sexta-feira** estiver contida dentro daquele mês. Na prática, a apuração de **junho/2026**, por exemplo, não considera o mês exato (01/06/2026 a 30/06/2026), mas o ciclo operacional compreendido entre **30/05/2026 e 26/06/2026.**

EXEMPLO ILUSTRATIVO1800![ChatGPT Image 3 de ago. de 2026, 17\_44\_32-20260803-204608.png](images/ChatGPT%20Image%203%20de%20ago.%20de%202026,%2017_44_32-20260803-204608.png)

Definição das semanas de um mês de referência:

-   **Maio**: semana 1 (25/04 a 01/05), semana 2 (02/05 a 08/05), semana 3 (09/05 a 15/05), semana 4 (16/05 a 22/05) e semana 5 (23/05 a 29/05).
    
-   **Junho**: semana 1 (30/05 a 05/06), semana 2 (06/06 a 12/06), semana 3 (13/06 a 19/06) e semana 4 (20/06 a 26/06).
    
-   Demais dias de Junho (27-30) entram para a referência de **Julho** 

## **5.2. Fonte PCM**

### **5.2.1. Denominador: Quantidade de solicitações de consentimentos válidas**

O denominador da taxa de conversão aplica critérios obrigatórios de exclusão, **independentes do produto.** Esses critérios garantem que somente as jornadas válidas reportadas por ambas as pontas, processadas com sucesso e originadas por clientes legítimos da instituição sejam computadas no cálculo.

Critérios de Exclusão do Denominador (Solicitações Válidas)4000

**Regra**

**Descrição**

1.  **StatusCode diferente de 2xx**
    

Somente são computadas as solicitações cujo _statuscode HTTP_ pertence à família 2xx (200, 201, 204 e demais), indicando que a requisição foi processada com sucesso pela instituição.

Requisições cujo _statuscode_ pertence às famílias 4xx (erros de cliente), 5xx (erros de servidor) ou demais respostas fora da faixa de sucesso são excluídas do denominador, pois indicam falhas técnicas, autorizações inválidas ou indisponibilidade que não representam uma jornada efetiva do cliente.

2.  **Chamadas não pareadas (**_**client**_ **e** _**server**_**)**
    

São excluídas do denominador as chamadas que não apresentam pareamento entre as pontas _client_ (instituição iniciadora ou receptora) e _server_ (instituição transmissora ou detentora de conta). O pareamento exige que ambas as instituições envolvidas na jornada reportem o mesmo evento para garantir a integridade da informação.

Quando apenas uma das pontas reporta a ocorrência — seja por falha no envio, descarte da informação ou indisponibilidade temporária — a chamada é considerada não pareada e não entra no cálculo.

3.  **Identificadores (ID’s) nulos**
    

Para garantir a rastreabilidade e a integridade da jornada, são desconsiderados do denominador os registros sem a devida identificação de consentimento. Essa exclusão é aplicada removendo todas as requisições em que o campo `ADDITIONALINFO_CONSENTID` é nulo

4.  **Exclusão de não clientes (DropReason)**
    

Excluem-se do denominador as ocorrências em que o CPF/CNPJ redirecionado não é cliente da instituição, identificadas por meio do campo DropReason. São computadas apenas as ocorrências cujo DropReason (`ADDITIONALINFO_DROPREASON`) é igual a NONE ou NULL, conforme tabela abaixo:

**DropReason**

**Descrição**

**Inclui no Denominador?**

**NONE**

Cliente válido da instituição (sem descarte)

**✅  Sim**

**NULL**

Informação não reportada (tratado como cliente válido)

**✅  Sim**

**Outro valor**

Não cliente (CPF/CNPJ sem vínculo com a instituição)

**❌  Não**

Para operacionalizar o cálculo do denominador, apresentamos a seguir a lógica de códigos aplicável a cada produto:

Denominador para Dados de Clientes1800true seção "período de apuração" and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint = '/open-banking/consents/v3/consents' -- endpoint específico para dados de clientes and orgid = clientorgid and statuscode like '2%' -- seção "critérios de exclusão do denominador (solicitações válidas)" and is\_unpaired\_server = 0 -- seção "critérios de exclusão do denominador (solicitações válidas)" and ( additionalinfo\_dropreason = 'NONE' or additionalinfo\_dropreason is null ) -- seção "critérios de exclusão do denominador (solicitações válidas)" and additionalinfo\_consentid is not null\]\]>Denominador para Vínculo1800true seção "período de apuração" and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint = '/open-banking/enrollments/v2/enrollments' -- endpoint específico para vínculo and orgid = clientorgid and statuscode like '2%' -- seção "critérios de exclusão do denominador (solicitações válidas)" and is\_unpaired\_server = 0 -- seção "critérios de exclusão do denominador (solicitações válidas)" and ( additionalinfo\_dropreason = 'NONE' or additionalinfo\_dropreason is null ) -- seção "critérios de exclusão do denominador (solicitações válidas)" and additionalinfo\_enrollmentid is not null     \]\]>Denominador Pagamentos1800Pagamento com Redirecionamentotrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint = '/open-banking/payments/v4/consents' -- endpoint específico para pagamentos and ( coalesce(additionalinfo\_authorisationflowintent, additionalinfo\_authorisationflow) <> 'fido\_flow' or coalesce(additionalinfo\_authorisationflowintent, additionalinfo\_authorisationflow) is null ) -- additionalinfo específico para pagamentos and orgid = clientorgid and statuscode like '2%' -- seção "critérios de exclusão do denominador (solicitações válidas)" and is\_unpaired\_server = 0 -- seção "critérios de exclusão do denominador (solicitações válidas)" and ( additionalinfo\_dropreason = 'NONE' or additionalinfo\_dropreason is null ) -- seção "critérios de exclusão do denominador (solicitações válidas)" and additionalinfo\_consentid is not null\]\]>Pix Automáticotrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint like '%/automatic-payments/v2/recurring-consents' -- endpoint específico para pix and additionalinfo\_paymenttype = 'AUTOMATIC' --additionalinfo específico para pix and orgid = clientorgid and statuscode like '2%' -- seção "critérios de exclusão do denominador (solicitações válidas)" and is\_unpaired\_server = 0 -- seção "critérios de exclusão do denominador (solicitações válidas)" and ( additionalinfo\_dropreason = 'NONE' or additionalinfo\_dropreason is null ) -- seção "critérios de exclusão do denominador (solicitações válidas)" and coalesce(additionalinfo\_recurringconsentid, additionalinfo\_consentid) is not null\]\]>Transferências Inteligentestrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid -- tratamento de possíveis erros. and httpmethod = 'POST' and endpoint like '%/automatic-payments/v2/recurring-consents' and (additionalinfo\_paymenttype = 'SWEEPING' or additionalinfo\_paymenttype is null) and orgid = clientorgid and statuscode like '2%' -- seção "critérios de exclusão do denominador (solicitações válidas)" and is\_unpaired\_server = 0 -- seção "critérios de exclusão do denominador (solicitações válidas)" and ( additionalinfo\_dropreason = 'NONE' or additionalinfo\_dropreason is null ) -- seção "critérios de exclusão do denominador (solicitações válidas)" and coalesce(additionalinfo\_recurringconsentid, additionalinfo\_consentid) is not null\]\]>wide1302

O denominador da Taxa de Conversão também pode ser obtido por meio da análise do _funil de conversão (detalhado na_ _seção 9.5.__)_ disponível no painel de produtos, somando as solicitações de consentimento das etapas “Consentimentos não autorizados visão negócio e /token” e “Consentimentos autorizados”.

### **5.2.2. Numerador: Quantidade de consentimentos autorizados**

A identificação do volume de consentimentos autorizados para composição do numerador adota uma abordagem combinada de duas fontes (com exceção de vínculo, que usa apenas APIs de negócio):

-   **a) Endpoint** `/token` **(Base de Segurança):** Registra os `consentId`s autorizados capturados diretamente na camada de segurança. Como essa base não contém a totalidade das ocorrências autorizadas, faz-se necessária a complementação via item **b**.
    
-   **b) Visão Negócio (APIs de Negócio):** Identifica os consentimentos consumidos e registrados nas APIs de negócio, garantindo a captura integral dos consentimentos autorizados.
    

Para operacionalizar o cálculo do numerador, apresentamos a seguir a lógica de códigos aplicável a cada produto:

Numerador para Dados de Clientes1800sqltrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and organisationid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and endpoint = '/token' and additionalinfo\_granttype = 'AUTHORIZATION\_CODE' ), apis\_negocio as ---- busca por uso de negócio ( select ... from where 1=1 and ts\_to\_date\_gmt between init\_date and end\_date and httpmethod = 'POST' and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and orgid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and is\_missing\_security = 1 --> consentid's que não estão na base de security and endpoint = '/open-banking/resources/v3/resources' –- dados de clientes ) select ... from where 1=1 and -- numerador final (is\_in\_security = 1 --> consentimentos autorizados na base de security or is\_in\_apis\_negocio = 1) --> consentimentos autorizados nas apis de negócio\]\]>Numerador para Vínculo1800sqltrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and orgid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and endpoint = '/open-banking/enrollments/v2/enrollments/{enrollmentId}/fido-registration' --vinculo \]\]>Numerador Pagamentos1800Pagamento com redirecionamentosqltrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and organisationid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and endpoint = '/token' and additionalinfo\_granttype = 'AUTHORIZATION\_CODE' ), apis\_negocio as ---- busca por uso de negócio ( select ... from where 1=1 and ts\_to\_date\_gmt between init\_date and end\_date and httpmethod = 'POST' and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and orgid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and is\_missing\_security = 1 --> consentid's que não estão na base de security and endpoint = '/open-banking/payments/v4/pix/payments' ) select ... from where 1=1 and -- numerador final (is\_in\_security = 1 --> consentimentos autorizados na base de security or is\_in\_apis\_negocio = 1) --> consentimentos autorizados nas apis de negócio \]\]>Transferências Inteligentessqltrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and organisationid = clientorgid and httpmethod = 'POST' and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and endpoint = '/token' and additionalinfo\_granttype = 'AUTHORIZATION\_CODE' ), apis\_negocio\_post as ---- busca por uso de negócio ( select ... from where 1=1 and ts\_to\_date\_gmt between init\_date and end\_date and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and statuscode like '2%' and additionalinfo\_consentid is not null and orgid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and is\_missing\_security = 1 --> consentid's que não estão na base de security and httpmethod in ('POST') and endpoint like '%/pix%' and (additionalinfo\_paymenttype = 'SWEEPING' or additionalinfo\_paymenttype is null) ), apis\_negocio\_get\_patch as ---- busca por uso de negócio ( select ... from where 1=1 and ts\_to\_date\_gmt between init\_date and end\_date and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and statuscode like '2%' and orgid = clientorgid and additionalinfo\_originalrecurringpaymentid is null and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and is\_missing\_security = 1 --> consentid's que não estão na base de security and httpmethod in ('GET', 'PATCH') and endpoint like '%recurring-consents%' and (additionalinfo\_paymenttype = 'SWEEPING' or additionalinfo\_paymenttype is null) and additionalinfo\_status = 'AUTHORISED' ) select ... from where 1=1 and -- numerador final (is\_in\_security = 1 --> consentimentos autorizados na base de security or is\_in\_apis\_negocio\_post = 1 or is\_in\_apis\_negocio\_get\_patch = 1) --> consentimentos autorizados nas apis de negócio\]\]>Pix automáticosqltrue is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and additionalinfo\_consentid is not null and statuscode like '2%' and organisationid = clientorgid and httpmethod = 'POST' and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and endpoint = '/token' and additionalinfo\_granttype = 'AUTHORIZATION\_CODE' ), apis\_negocio\_post as ---- busca por uso de negócio ( select ... from where 1=1 and ts\_to\_date\_gmt between init\_date and end\_date and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and statuscode like '2%' and additionalinfo\_consentid is not null and orgid = clientorgid and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and is\_missing\_security = 1 --> consentid's que não estão na base de security and httpmethod in ('POST') and endpoint like '%/pix%' and additionalinfo\_paymenttype = 'AUTOMATIC' ), apis\_negocio\_get\_patch as ---- busca por uso de negócio ( select ... from where 1=1 and ts\_to\_date\_gmt between init\_date and end\_date and is\_fvp = 0 --> is\_fvp é uma flag que indica se o orgid é do teste de fvp ou não (descrito na introdução deste documento) and clientorgid <> serverorgid and statuscode like '2%' and orgid = clientorgid and additionalinfo\_originalrecurringpaymentid is null and is\_in\_denominador = 1 --> consentid's que estão no denominador da taxa and is\_missing\_security = 1 --> consentid's que não estão na base de security and httpmethod in ('GET', 'PATCH') and endpoint like '%recurring-consents%' and additionalinfo\_paymenttype = 'AUTOMATIC' and additionalinfo\_status = 'AUTHORISED' ) select ... from where 1=1 and -- numerador final (is\_in\_security = 1 --> consentimentos autorizados na base de security or is\_in\_apis\_negocio\_post = 1 or is\_in\_apis\_negocio\_get\_patch = 1) --> consentimentos autorizados nas apis de negócio\]\]>wide1302

O numerador da Taxa de Conversão também pode ser obtido por meio da análise do _funil de conversão (detalhado na_ _seção 9.5.__)_ disponível no painel de produtos, utilizando a etapa de “Consentimentos Autorizados”.

## **5.4. Exemplo Taxa de Conversão unificada para pagamentos**

Conforme mencionado anteriormente, o monitoramento contempla três produtos: **Dados de Clientes**, **Vínculo** e **Pagamentos**.

Nesta seção, apresentamos um exemplo de como é calculada a **taxa de conversão do produto Pagamentos**. Esse produto é composto pelas modalidades **Pagamento com Redirecionamento**, **Pix Automático** e **Transferências Inteligentes**.

Como cada modalidade possui um volume diferente de solicitações de consentimento válidas, a taxa de conversão do produto **Pagamentos** não é obtida pela média simples das taxas individuais. Em vez disso, é calculada por meio de uma **média ponderada**, em que o peso de cada modalidade corresponde à sua quantidade de solicitações de consentimento válidas (denominador da taxa).

No exemplo a seguir, considere uma instituição **X**, com as respectivas taxas de conversão e quantidades de solicitações de consentimento válidas para cada modalidade:

**Produto**

**Taxa de Conversão**

**Solicitações Válidas (Peso)**

Pagamento com Redirecionamento

59,7%

44.303

Pix Automático

47,3%

1.300

Transferências Inteligentes

61,8%

16.212

**Total**

—

**61.815**

Nesse cenário, a taxa final de conversão do produto Pagamentos é calculada por meio da seguinte média ponderada:

![image-20260806-192040.png](images/image-20260806-192040.png)

# 6\. Interpretação dos Resultados (Meta)

Tendo estabelecido a metodologia de apuração da taxa de conversão, torna-se necessário definir os parâmetros que determinam se o desempenho do participante está adequado aos padrões do ecossistema. Esse acompanhamento é estruturado a partir de três métricas de referência: **a Meta (ou Top 3), a Taxa de Tolerância e a Taxa de Diagnóstico**, detalhadas a seguir.

## 6.1. Cálculo das Metas (TOP 3)

Essa métrica define o benchmark de excelência do mercado e é calculado da seguinte forma:

1.  Calcula-se a taxa de conversão em uma janela de 3 meses, incluindo o mês de referência, para cada conglomerado;
    
2.  Dentre os maiores conglomerados, identificam-se as instituições com as três maiores taxas de conversão;
    
3.  Calcula-se a taxa ponderada dessas três maiores taxas, definindo-se a meta Top 3;
    
4.  Esse valor serve de referência para a definição dos demais limiares
    

## 6.2. Taxa de Tolerância

A Taxa de Tolerância é o piso de conformidade. Instituições cuja taxa de conversão se mantiver acima dela são consideradas conformes. Ela é obtida tomando-se 80% da Taxa Top 3 e subtraindo-se 3 pontos percentuais, para acomodar pequenas variações operacionais.

#F4F5F7wide1800

**TAXA DE TOLERÂNCIA = (80% × TAXA TOP 3) − 3 p.p**

## 6.3 Taxa de Diagnóstico

A Taxa de Diagnóstico é o limiar inferior de severidade. Se a taxa de conversão de uma instituição cair abaixo dela, será necessária uma avaliação independente por empresa especializada para diagnosticar e corrigir os problemas subjacentes da jornada.

#F4F5F7wide1800

**TAXA DE DIAGNÓSTICO= 60% × (80% × TAXA TOP 3) = 48% × TAXA TOP 3**

## 6.4. Limiares Estabelecidos

Com base nas taxas calculadas acima, a instituição participante pode se enquadrar em um de três estados de conformidade apresentados abaixo.

**Estado**

**Condição**

**Tratamento**

**Conforme**

Taxa da instituição ≥ Taxa de Tolerância

Nenhuma ação regulatória é disparada

**Desconforme**

Taxa de Diagnóstico ≤ Taxa da instituição < Taxa de Tolerância

A instituição deve justificar porque se encontra nessa situação

**Diagnóstico**

Taxa da instituição < Taxa de Diagnóstico

A instituição deve adotar ações corretivas para retornar ao patamar de conformidade

# 7\. Referências Normativas

-   Instrução Normativa BCB nº 706, de 29 de janeiro de 2026 – Manual de Monitoramento do Open Finance, versão 3.0
    

-   Resolução Conjunta nº 1, de 4 de maio de 2020 – Disposições gerais sobre implementação do Open Finance
    

-   Resolução BCB nº 32, de 29 de outubro de 2020 – Requisitos técnicos e procedimentos operacionais do Open Finance
    

-   Guia de Itens Monitorados – Taxa de Conversão (Área do Desenvolvedor do Open Finance Brasil, item 2.6.2)
