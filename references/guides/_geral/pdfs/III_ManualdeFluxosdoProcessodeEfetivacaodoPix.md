# **Manual de Fluxos do** **Processo de** **Efetivação do Pix**

## Versão 2.1

1  •  Manual de Fluxos do Processo de Efetivação do Pix




### **Sumário**

**1.** **INTRODUÇÃO.............................................................................................................................................. 4**


**2.** **FLUXOS DE GERAÇÃO DA ORDEM DE PAGAMENTO PELO USUÁRIO PAGADOR .......................................... 5**


2.1. GERAÇÃO DA ORDEM DE PAGAMENTO POR INSERÇÃO MANUAL DOS DADOS OU POR MEIO DE CHAVE PIX ........................ 5
_2.1.1._ _PSP do pagador com acesso direto ao Diretório de Identificadores de Contas Transacionais (DICT)_
_5_
_2.1.2._ _PSP do pagador com acesso indireto ao DICT ............................................................................... 7_
_2.1.3._ _Prestador de serviço de iniciação de transação de pagamento, com acesso direto ao DICT ....... 9_
2.2. GERAÇÃO DA ORDEM DE PAGAMENTO POR QR CODE ESTÁTICO ............................................................................ 11
2.3. GERAÇÃO DA ORDEM DE PAGAMENTO POR QR CODE DINÂMICO .......................................................................... 13
_2.3.1._ _Pix Cobrança para pagamento imediato .................................................................................... 13_
_2.3.2._ _Pix Cobrança para pagamento com vencimento ........................................................................ 15_
2.4. GERAÇÃO DA ORDEM DE PAGAMENTO DE UM PIX AGENDADO ÚNICO OU RECORRENTE POR INSERÇÃO MANUAL DE DADOS

OU POR MEIO DE CHAVE PIX ........................................................................................................................................ 18

_2.4.1._ _PSP do pagador com acesso direto ao DICT ................................................................................ 18_
_2.4.2._ _PSP do pagador com acesso indireto ao DICT ............................................................................. 20_
2.5. GERAÇÃO DA ORDEM DE PAGAMENTO PELO SERVIÇO DE INICIAÇÃO DE TRANSAÇÃO DE PAGAMENTO, NOS CASOS EM QUE O

PARTICIPANTE POSSUI TODAS AS INFORMAÇÕES DO USUÁRIO RECEBEDOR............................................................................. 23
2.6. GERAÇÃO DA ORDEM DE PAGAMENTO PELA INICIAÇÃO POR APROXIMAÇÃO DE UM DISPOSITIVO HABILITADO COM

TECNOLOGIA _NEAR FIELD COMMUNICATION_ (NFC) A OUTRO DISPOSITIVO COM MESMA TECNOLOGIA ....................................... 24

_2.6.1._ _Transação iniciada pelo PSP do pagador .................................................................................... 24_
_2.6.2_ _Transação iniciada pelo prestador de serviço de iniciação de transação de pagamento ........... 26_


**3.** **FLUXO DE EFETIVAÇÃO DO PIX ................................................................................................................. 29**


3.1. FLUXO DE TRANSAÇÕES ENTRE PARTICIPANTES DIRETOS ....................................................................................... 29
_3.1.1._ _Fluxo com liquidação imediata da ordem de pagamento........................................................... 30_
_3.1.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado, Pix Agendado_
_recorrente e Pix Cobrança com vencimento) ................................................................................................ 32_
3.2. FLUXO DE TRANSAÇÕES ENTRE PARTICIPANTES INDIRETOS .................................................................................... 34
_3.2.1._ _Fluxo com liquidação imediata da ordem de pagamento........................................................... 35_
_3.2.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado, Pix Agendado_
_recorrente e Pix Cobrança com vencimento) ................................................................................................ 38_
3.3. FLUXO DE TRANSAÇÕES NOS LIVROS DO PSP ..................................................................................................... 41
_3.3.1._ _Fluxo com liquidação imediata da ordem de pagamento........................................................... 42_
_3.3.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado, Pix Agendado_
_recorrente e Pix Cobrança com vencimento) ................................................................................................ 43_
3.4. FLUXO DE TRANSAÇÕES ENTRE PARTICIPANTES INDIRETOS COM MESMO LIQUIDANTE ................................................. 45
_3.4.1._ _Fluxo com liquidação imediata da ordem de pagamento........................................................... 46_
_3.4.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado e Pix Agendado_
_recorrente e Pix Cobrança com vencimento) ................................................................................................ 48_


**4.** **FLUXO DE DEVOLUÇÃO DO PIX ................................................................................................................. 50**


4.1. FLUXO DE DEVOLUÇÃO ENTRE PARTICIPANTES DIRETOS ........................................................................................ 51
4.2. FLUXO DE DEVOLUÇÃO ENTRE PARTICIPANTES INDIRETOS ..................................................................................... 54


**5.** **FLUXOS DO PIX AUTOMÁTICO .................................................................................................................. 57**


5.1. FLUXOS DE AUTORIZAÇÃO .............................................................................................................................. 57


2  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.1.1._ _Jornada 1 – Usuário pagador escolhe Pix Automático como forma de pagamento (interação_
_externa ao ecossistema) ............................................................................................................................... 57_
_5.1.2._ _Jornada 2 – Usuário pagador realiza adesão por meio do PSP do pagador (leitura de QR Code_
_contendo os dados da recorrência) .............................................................................................................. 63_
_5.1.3._ _Jornada 3 – Usuário pagador realiza adesão por meio da leitura de QR Code com primeiro_
_pagamento imediato .................................................................................................................................... 68_
_5.1.4._ _Jornada 4 – Usuário paga por meio de QR Code e recebe proposta de habilitação do Pix_
_Automático para pagamento de cobranças recorrentes futuras ................................................................. 76_
_5.1.5._ _Cancelamento da autorização pelo usuário pagador ................................................................. 84_
_5.1.6._ _Cancelamento da recorrência pelo usuário recebedor ............................................................... 87_
5.2. FLUXOS DE AGENDAMENTO DO DÉBITO ............................................................................................................ 90
_5.2.1._ _Agendamento do débito ............................................................................................................. 90_
_5.2.2._ _Novas tentativas intradia por erro no fluxo de liquidação.......................................................... 93_
_5.2.3._ _Cancelamento pelo usuário pagador de um débito agendado ................................................... 96_
_5.2.4._ _Cancelamento pelo usuário recebedor de um débito agendado ................................................ 99_


3  •  Manual de Fluxos do Processo de Efetivação do Pix




### **1. Introdução**

O processo de efetivação do Pix consiste em 3 tipos de fluxos, que serão descritos nas seções específicas
deste Manual:


  - **Seção 2:** fluxos de **geração da ordem de pagamento**, que corresponde aos procedimentos
executados, a partir do início da transação pelo usuário pagador, pelo prestador de serviços de
pagamento (PSP) do pagador para identificação do usuário recebedor;

  - **Seção 3:** fluxos de **efetivação do Pix**, iniciado pelo prestador de serviços de pagamento (PSP) do
pagador, após a geração da ordem de pagamento pelo usuário pagador;

  - **Seção 4:** fluxos de **devolução de transações**, onde o PSP recebedor (ou remetente)
operacionaliza a devolução de valores, a partir de solicitação do PSP do pagador (ou
destinatário), ou por iniciativa própria.

A **Seção 5** consiste nos fluxos que descrevem os processos relacionados ao Pix Automático:


  - **Fluxos de autorização** : a partir dos quais o usuário pagador permite o envio de cobranças
recorrentes pelo usuário recebedor e autoriza os pagamentos pelo seu prestador de serviços de
pagamento (PSP). Também estão descritos os fluxos de cancelamento da autorização pelo
usuário pagador e de cancelamento da permissão, por iniciativa do usuário recebedor;

  - **Fluxos de agendamento do débito** : descrição de como devem ser enviadas as instruções de
pagamento pelo usuário recebedor, conforme acordado na autorização. Adicionalmente, estão
descritos os processos de cancelamento de um débito agendado pelo usuário pagador ou pelo
usuário recebedor.


4  •  Manual de Fluxos do Processo de Efetivação do Pix




### **2. Fluxos de geração da ordem de pagamento pelo usuário pagador**

#### **2.1. Geração da ordem de pagamento por inserção manual dos dados ou por** **meio de chave Pix**

_2.1.1._ _PSP do pagador com acesso direto ao Diretório de Identificadores de Contas Transacionais (DICT)_
















|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador acessa canal de<br>pagamento (app ou internet banking) para realização de<br>transação de pagamento e insere os dados necessários à<br>realização do pagamento (chave Pix ou dados bancários do<br>recebedor).|
|2|Usuário pagador|Comunicação|Dados inseridos pelo usuário pagador são encaminhados ao<br>PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do pagamento informados<br>pelo usuário pagador.|
|4|PSP do pagador|Decisão|Se o usuário pagador houver informado a chave Pix do<br>recebedor na etapa 1, o fluxo segue para a etapa 5. Caso o<br>usuário pagador tenha inserido os dados bancários do<br>recebedor, a consulta ao DICT para validação dessas|



5  •  Manual de Fluxos do Processo de Efetivação do Pix




|Col1|Col2|Col3|informações não é necessária, devendo-se passar diretamente<br>à etapa 10.|
|---|---|---|---|
|5|PSP do pagador|Comunicação|PSP do pagador encaminha mensagem ao DICT para consulta<br>das informações de identificação do usuário recebedor a partir<br>da chave informada pelo usuário pagador.|
|6|DICT|Comunicação|DICT recebe a consulta de dados sobre o usuário recebedor.|
|7|DICT|Ação|DICT consulta a chave recebida, faz a validação e retorna os<br>dados de identificação encontrados.|
|8|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os dados de<br>identificação do usuário recebedor.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os dados de<br>identificação do usuário recebedor.|
|10|PSP do pagador|Ação|PSP do pagador valida os dados do usuário recebedor<br>informados por inserção manual.|
|11|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador com<br>os dados do usuário recebedor, solicitando confirmação.|
|12|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados sobre o<br>usuário recebedor, solicitando confirmação para o início do<br>processo de efetivação do pagamento.|
|13|Usuário pagador|Ação|Usuário pagador confere os dados do usuário recebedor e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo.|



6  •  Manual de Fluxos do Processo de Efetivação do Pix




_2.1.2._ _PSP do pagador com acesso indireto ao DICT_












|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador acessa canal de<br>pagamento (app ou internet banking) para realização de<br>transação de pagamento e insere os dados necessários à<br>realização do pagamento (chave Pix ou dados bancários do<br>recebedor).|
|2|Usuário pagador|Comunicação|Dados inseridos pelo usuário pagador são encaminhados<br>ao PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do pagamento informados<br>pelo usuário pagador.|



7  •  Manual de Fluxos do Processo de Efetivação do Pix




|4|PSP do pagador|Decisão|Se o usuário pagador houver informado a chave Pix do<br>recebedor na etapa 1, o fluxo segue para a etapa 5. Caso o<br>usuário pagador tenha inserido os dados bancários do<br>recebedor, a consulta ao DICT para validação dessas<br>informações não é necessária, devendo-se passar<br>diretamente à etapa 14.|
|---|---|---|---|
|5|PSP do pagador|Comunicação|PSP do pagador se comunica com o participante com<br>acesso direto ao DICT para consulta das informações de<br>identificação do usuário recebedor.|
|6|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante com acesso direto ao DICT recebe os dados do<br>pagamento encaminhados pelo PSP do pagador.|
|7|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante com acesso direto se comunica com o DICT<br>para consulta das informações de identificação do usuário<br>recebedor.|
|8|DICT|Comunicação|DICT recebe a consulta de dados sobre o usuário<br>recebedor.|
|9|DICT|Ação|DICT consulta a chave recebida, faz a validação e retorna os<br>dados de identificação encontrados.|
|10|DICT|Comunicação|DICT envia comunicação ao participante com acesso direto<br>ao DICT, informando os dados de identificação do usuário<br>recebedor.|
|11|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante<br>com<br>acesso<br>direto<br>ao<br>DICT<br>recebe<br>comunicação com os dados de identificação do usuário<br>recebedor.|
|12|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante com acesso direto ao DICT se comunica com o<br>PSP do pagador, informando os dados do usuário<br>recebedor.|
|13|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do participante com<br>acesso direto ao DICT com os dados de identificação do<br>usuário recebedor.|
|14|PSP do pagador|Ação|PSP do pagador valida os dados do usuário recebedor<br>informados por inserção manual.|
|15|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor, solicitando<br>confirmação.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com os dados do<br>usuário recebedor, solicitando confirmação para o início do<br>processo de efetivação do pagamento.|
|17|Usuário pagador|Ação|Usuário pagador confere os dados do usuário recebedor e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo.|


8  •  Manual de Fluxos do Processo de Efetivação do Pix






_2.1.3._ _Prestador de serviço de iniciação de transação de pagamento, com acesso direto ao DICT_












|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador acessa canal do PSI<br>para realização de transação de pagamento e insere os<br>dados necessários à realização do pagamento.|
|2|Usuário pagador|Comunicação|Dados inseridos pelo usuário pagador são encaminhados<br>ao PSI.|
|3|PSI|Comunicação|PSI recebe os dados do pagamento inseridos pelo usuário<br>pagador.|



9  •  Manual de Fluxos do Processo de Efetivação do Pix




|4|PSI|Decisão|Se o usuário pagador houver informado a chave Pix do<br>recebedor na etapa 1, o fluxo segue para a etapa 5. Caso o<br>usuário pagador tenha inserido os dados bancários do<br>recebedor, a consulta ao DICT para validação dessas<br>informações pelo PSI não é necessária, devendo-se passar<br>diretamente à etapa 10.|
|---|---|---|---|
|5|PSI|Comunicação|PSI encaminha mensagem ao DICT para consulta das<br>informações de identificação do usuário recebedor a partir<br>da chave informada pelo usuário pagador.|
|6|DICT|Comunicação|DICT recebe consulta de dados sobre usuário recebedor.|
|7|DICT|Ação|DICT consulta a chave recebida, faz a validação e retorna os<br>dados de identificação encontrados.|
|8|DICT|Comunicação|DICT envia comunicação ao PSI com os dados de<br>identificação do usuário recebedor.|
|9|PSI|Comunicação|PSI recebe comunicação do DICT com os dados de<br>identificação do usuário recebedor.|
|10|PSI|Ação|PSI valida os dados do usuário recebedor informados por<br>inserção manual.|
|11|PSI|Comunicação|PSI envia comunicação ao usuário pagador com os dados<br>do usuário recebedor, solicitando consentimento para<br>iniciar a transação.|
|12|Usuário pagador|Comunicação|Usuário pagador recebe solicitação de consentimento com<br>as informações do usuário recebedor.|
|13|Usuário pagador|Ação|Usuário pagador confere os dados e dá consentimento<br>para que a transação seja iniciada pelo PSI.|
|14|Usuário pagador|Comunicação|Usuário pagador envia o consentimento para que a<br>transação seja iniciada.|
|15|PSI|Comunicação|PSI recebe consentimento do usuário pagador para que a<br>transação seja iniciada.|
|16|PSI|Comunicação|PSI envia dados da transação ao PSP do pagador, por meio<br>da API do Open Finance.|
|17|PSP do pagador|Comunicação|PSP do pagador recebe os dados da transação.|
|18|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor, solicitando<br>autenticação e confirmação para o pagamento.|
|19|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com os dados do<br>usuário recebedor, solicitando autenticação e confirmação<br>para o início do processo de efetivação do pagamento.|
|20|Usuário pagador|Ação|Usuário pagador confere as informações recebidas e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo|


10  •  Manual de Fluxos do Processo de Efetivação do Pix






#### **2.2. Geração da ordem de pagamento por QR Code estático**













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ ou insere o “Pix Copia e Cola” disponibilizado pelo<br>usuário recebedor, no app do PSP do pagador.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ ou inseridos pelo “Pix Copia e Cola”<br>são encaminhados ao PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe dados do_QR Code_ou “Pix Copia e<br>Cola”.|
|4|PSP do pagador|Ação|PSP do pagador interpreta o_QR Code_ ou “Pix Copia e Cola”.|
|5|PSP do pagador|Comunicação|PSP do pagador encaminha mensagem ao DICT para<br>consulta das informações de identificação do usuário<br>recebedor, conforme informações contidas no QR Code ou<br>Pix Copia e Cola”.|
|6|DICT|Comunicação|DICT recebe a consulta de dados sobre o usuário<br>recebedor.|
|7|DICT|Ação|DICT consulta os dados recebidos, faz a validação e retorna<br>os dados de identificação encontrados.|
|8|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os dados<br>de identificação do usuário recebedor.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os dados<br>de identificação do usuário recebedor.|


11  •  Manual de Fluxos do Processo de Efetivação do Pix




|10|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor, solicitando<br>confirmação para efetivação da ordem de pagamento.|
|---|---|---|---|
|11|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados sobre o<br>usuário recebedor, solicitando confirmação para o início<br>do processo de efetivação do pagamento|
|12|Usuário pagador|Ação|Usuário pagador confere as informações recebidas e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo. Fim do processo.|


Caso o PSP do pagador tenha acesso indireto ao DICT, o fluxo segue a mesma lógica do fluxo descrito na
seção 2.1.2, no que se refere às ações tomadas pelo PSP com acesso direto e sua comunicação com o
DICT.


12  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **2.3. Geração da ordem de pagamento por QR Code dinâmico**

_2.3.1._ _Pix Cobrança para pagamento imediato_













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ ou insere o “Pix Copia e Cola” disponibilizado pelo<br>usuário recebedor, no app do PSP do pagador.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ ou “Pix Copia e Cola” são<br>encaminhados ao PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do_QR Code_ ou “Pix Copia<br>e Cola”.|
|4|PSP do pagador|Ação|PSP do pagador interpreta o_QR Code_ ou “Pix Copia e Cola”e<br>identifica a_location_ contida nele.|


13  •  Manual de Fluxos do Processo de Efetivação do Pix




|5|PSP do pagador|Comunicação|PSP do pagador envia consulta da location ao PSP do<br>recebedor.|
|---|---|---|---|
|6|PSP do recebedor|Comunicação|PSP do recebedor recebe a requisição de consulta enviada<br>pelo PSP do pagador.|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança no<br>_payload_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite o_payload_ com os dados da<br>cobrança ao PSP do pagador.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe o_payload_ com os dados da<br>cobrança_._|
|10|PSP do pagador|Comunicação|PSP do pagador envia mensagem ao DICT para consulta das<br>informações de identificação do usuário recebedor,<br>conforme informações contidas no_QR Code_ ou no “Pix<br>Copia e Cola”.|
|11|DICT|Comunicação|DICT recebe a consulta de dados sobre o usuário<br>recebedor.|
|12|DICT|Ação|DICT consulta os dados recebidos, faz a validação e retorna<br>os dados de identificação encontrados.|
|13|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os dados<br>de identificação do usuário recebedor.|
|14|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os dados<br>de identificação do usuário recebedor.|
|15|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor e do_payload_, <br>solicitando confirmação para efetivação da ordem de<br>pagamento.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados do<br>usuário recebedor e do_payload_, solicitando confirmação<br>para efetivação do pagamento.|
|17|Usuário pagador|Ação|Usuário pagador confere as informações recebidas e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo.|


Caso o PSP do pagador tenha acesso indireto ao DICT, o fluxo segue a mesma lógica do fluxo descrito na
seção 2.1.2, no que se refere às ações tomadas pelo PSP com acesso direto e sua comunicação com o
DICT.


14  •  Manual de Fluxos do Processo de Efetivação do Pix




_2.3.2._ _Pix Cobrança para pagamento com vencimento_












|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ ou insere o “Pix Copia e Cola” disponibilizado pelo<br>usuário recebedor, no app do PSP do pagador.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ ou “Pix Copia e Cola” são<br>encaminhados ao PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do_QR Code_ou “Pix Copia<br>e Cola”.|



15  •  Manual de Fluxos do Processo de Efetivação do Pix




|4|PSP do pagador|Ação|PSP do pagador interpreta o QR Code ou “Pix Copia e Cola”<br>e identifica a location contida nele.|
|---|---|---|---|
|5|PSP do pagador|Comunicação|PSP do pagador envia consulta da_location_ ao PSP do<br>recebedor.|
|6|PSP do recebedor|Comunicação|PSP do recebedor recebe a requisição de consulta enviada<br>pelo PSP do pagador.|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança no<br>_payload_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite o_payload_ com os dados da<br>cobrança ao PSP do pagador.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe o_payload_ com os dados da<br>cobrança_._|
|10|PSP do pagador|Comunicação|PSP do pagador encaminha consulta sobre os dados da<br>chave Pix do usuário recebedor ao DICT, conforme<br>informações contidas no_QR Code_.|
|11|DICT|Comunicação|DICT recebe consulta de dados sobre usuário recebedor.|
|12|DICT|Ação|DICT consulta os dados recebidos, faz a validação e retorna<br>os dados de identificação encontrados.|
|13|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os dados<br>de identificação do usuário recebedor.|
|14|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os dados<br>de identificação do usuário recebedor.|
|15|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor e do_payload_, <br>solicitando confirmação para efetivação da ordem de<br>pagamento.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados do<br>usuário recebedor, o valor da cobrança e a data de<br>pagamento<br>sugerida, solicitando<br>confirmação<br>para<br>efetivação do pagamento.|
|17|Usuário pagador|Decisão|Se o usuário pagador optar por não alterar a data de<br>pagamento sugerida e esta for igual à “data corrente”, o<br>fluxo segue para a etapa 28. Caso o usuário pagador decida<br>alterar a data de pagamento sugerida e inserir uma data de<br>pagamento pretendida (DPP), o fluxo segue para a etapa<br>18.|
|18|Usuário pagador|Ação|Usuário pagador insere a data de pagamento pretendida<br>(DPP) no app do PSP do pagador.|
|19|Usuário pagador|Comunicação|Usuário pagador envia solicitação para alteração da data de<br>pagamento sugerida para a DPP ao PSP pagador.|
|20|PSP do pagador|Comunicação|PSP do pagador recebe a consulta com a DPP informada<br>pelo usuário pagador.|
|21|PSP do pagador|Comunicação|PSP do pagador envia a solicitação dos dados de<br>pagamento com a DPP para o PSP recebedor.|
|22|PSP do recebedor|Comunicação|PSP do recebedor recebe a solicitação dos dados da<br>cobrança para a DPP informada.|


16  •  Manual de Fluxos do Processo de Efetivação do Pix




|23|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança e os<br>cálculos de desconto, juros e/ou multa com base na DPP<br>informada no payload.|
|---|---|---|---|
|24|PSP do recebedor|Comunicação|PSP do recebedor envia o_payload_com os dados da<br>cobrança para a DPP informada ao PSP do pagador.|
|25|PSP do pagador|Comunicação|PSP do pagador recebe o_payload_ com os dados da<br>cobrança para a DPP informada.|
|26|PSP do pagador|Comunicação|PSP do pagador envia o_payload_ com os dados da cobrança<br>para a DPP informada ao usuário pagador, solicitando<br>confirmação para efetivação do pagamento.|
|27|Usuário pagador|Comunicação|Usuário pagador recebe, no app do PSP do pagador, as<br>informações sobre cobrança, a partir da DPP informada:<br>usuário recebedor, a data para pagamento e o valor a<br>pagar, com as informações sobre principal, multa, juros,<br>descontos e/ou abatimentos.|
|28|Usuário pagador|Ação|Usuário pagador confere as informações recebidas e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo.|


Caso o PSP do pagador tenha acesso indireto ao DICT, o fluxo segue a mesma lógica do fluxo descrito na
seção 2.1.2, no que se refere às ações tomadas pelo PSP com acesso direto e sua comunicação com o
DICT.


17  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **2.4. Geração da ordem de pagamento de um Pix Agendado único ou recorrente** **por inserção manual de dados ou por meio de chave Pix**

_2.4.1._ _PSP do pagador com acesso direto ao DICT_













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador acessa canal de<br>pagamento (app ou internet banking) para realização de<br>transação de pagamento e insere os dados necessários à<br>realização do pagamento (chave Pix ou dados bancários<br>do recebedor). A data de agendamento pode ser<br>requisitada nesta etapa, ou alternativamente, pode ser<br>solicitada na etapa 12, já com a disponibilização dos<br>dados do usuário recebedor e antes da confirmação da<br>transação.|
|2|Usuário pagador|Comunicação|Dados inseridos pelo usuário pagador são encaminhados<br>ao PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do pagamento<br>informados pelo usuário pagador.|
|4|PSP do pagador|Decisão|Se o usuário pagador houver informado a chave Pix do<br>recebedor na etapa 1, o fluxo segue para a etapa 5. Caso<br>o usuário pagador tenha inserido os dados bancários do|


18  •  Manual de Fluxos do Processo de Efetivação do Pix






|Col1|Col2|Col3|recebedor, a consulta ao DICT para validação dessas<br>informações não é necessária, devendo-se passar<br>diretamente à etapa 10.|
|---|---|---|---|
|5|PSP do pagador|Comunicação|Caso o usuário pagador tenha inserido uma chave Pix, o<br>PSP do pagador encaminha mensagem ao DICT para<br>consulta das informações de identificação do usuário<br>recebedor. O_EndToEndId_ gerado nesta etapa é usado<br>apenas para a consulta ao DICT.|
|6|DICT|Comunicação|DICT recebe consulta de dados sobre usuário recebedor.|
|7|DICT|Ação|DICT consulta a chave recebida, faz a validação e retorna<br>os dados de identificação encontrados.|
|8|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os dados<br>de identificação do usuário recebedor.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os<br>dados de identificação do usuário recebedor.|
|10|PSP do pagador|Ação|PSP do pagador valida os dados do usuário recebedor<br>informados por inserção manual.|
|11|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor, solicitando<br>confirmação.|
|12|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados sobre o<br>usuário recebedor, solicitando confirmação para o início<br>do processo de efetivação do pagamento. Caso a data de<br>agendamento não tenha sido solicitada na etapa 1, ela<br>deve ser solicitada nesta etapa, antes da confirmação da<br>transação.|
|13|Usuário pagador|Ação|Usuário pagador confere as informações do usuário<br>recebedor e confirma a transação, gerando a ordem de<br>pagamento. Fim do processo.|


19  •  Manual de Fluxos do Processo de Efetivação do Pix






_2.4.2._ _PSP do pagador com acesso indireto ao DICT_


20  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador acessa<br>canal de pagamento (app ou internet banking)<br>para realização de transação de pagamento e<br>insere os dados necessários à realização do<br>pagamento (chave Pix ou dados bancários do<br>recebedor). A data de agendamento pode ser<br>requisitada nesta etapa, ou alternativamente,<br>pode ser solicitada na etapa 16, já com a<br>disponibilização<br>dos<br>dados<br>do<br>usuário<br>recebedor<br>e <br>antes<br>da<br>confirmação<br>da<br>transação.|
|2|Usuário pagador|Comunicação|Dados inseridos pelo usuário pagador são<br>encaminhados ao PSP do pagador.|
|3|PSP do pagador|Comunicação|O PSP do pagador recebe os dados do<br>pagamento informados pelo usuário pagador.|
|4|PSP do pagador|Decisão|Se o usuário pagador tiver informado a chave<br>Pix do recebedor na etapa 1, o fluxo segue para<br>a etapa 5. Caso o usuário pagador tenha<br>inserido os dados bancários do recebedor, a<br>consulta ao DICT para validação dessas<br>informações não é necessária, devendo-se<br>passar diretamente à etapa 14.|
|5|PSP do pagador|Comunicação|PSP do pagador se comunica com o participante<br>com acesso direto ao DICT para consulta das<br>informações de identificação do usuário<br>recebedor.|
|6|Participante com<br>acesso direto ao<br>DICT|Comunicação|O participante com acesso direto ao DICT<br>recebe os dados do pagamento encaminhados<br>pelo PSP do pagador.|
|7|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante com acesso direto se comunica<br>com o DICT para consulta das informações de<br>identificação<br>do<br>usuário<br>recebedor.<br>O <br>_EndToEndId_ gerado nesta etapa é usado apenas<br>para a consulta ao DICT.|
|8|DICT|Comunicação|DICT recebe consulta de dados sobre usuário<br>recebedor.|
|9|DICT|Ação|DICT consulta a chave recebida, faz a validação<br>e <br>retorna<br>os<br>dados<br>de<br>identificação<br>encontrados.|
|10|DICT|Comunicação|DICT envia comunicação ao participante com<br>acesso direto, informando os dados de<br>identificação do usuário recebedor.|
|11|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante com acesso direto ao DICT recebe<br>comunicação com os dados de identificação do<br>usuário recebedor.|



21  •  Manual de Fluxos do Processo de Efetivação do Pix




|12|Participante com<br>acesso direto ao<br>DICT|Comunicação|Participante com acesso direto ao DICT se<br>comunica com o PSP do pagador, informando<br>os dados do usuário recebedor.|
|---|---|---|---|
|13|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do<br>participante com acesso direto com os dados de<br>identificação do usuário recebedor.|
|14|PSP do pagador|Ação|PSP do pagador valida os dados do usuário<br>recebedor informados por inserção manual.|
|15|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário<br>pagador com os dados do usuário recebedor,<br>solicitando confirmação.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com<br>dados sobre o usuário recebedor, solicitando<br>confirmação para o início do processo de<br>efetivação do pagamento. Caso a data de<br>agendamento não tenha sido solicitada na<br>etapa 1, ela deve ser solicitada nesta etapa,<br>antes da confirmação da transação.|
|17|Usuário pagador|Ação|Usuário pagador confere as informações do<br>usuário recebedor e confirma a transação,<br>gerando a ordem de pagamento. Fim do<br>processo.|


22  •  Manual de Fluxos do Processo de Efetivação do Pix






#### **2.5. Geração da ordem de pagamento pelo serviço de iniciação de transação de** **pagamento, nos casos em que o participante possui todas as informações do** **usuário recebedor**



|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSI|Ação|Início do processo. PSI gera as informações para a<br>cobrança com os dados do recebedor.|
|2|PSI|Comunicação|PSI envia os dados para pagamento ao usuário pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe os dados para pagamento.|
|4|Usuário pagador|Ação|Confere os dados e dá consentimento para que a<br>transação seja iniciada pelo PSI.|
|5|Usuário pagador|Comunicação|Usuário pagador envia o consentimento ao PSI para que<br>a transação seja iniciada.|
|6|PSI|Comunicação|PSI recebe consentimento do usuário pagador.|
|7|PSI|Comunicação|PSI envia dados da transação ao PSP do pagador, por<br>meio da API do Open Finance.|
|8|PSP do pagador|Comunicação|PSP do pagador recebe dados da transação.|
|9|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor, solicitando<br>autenticação e confirmação.|


23  •  Manual de Fluxos do Processo de Efetivação do Pix






|10|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados sobre o<br>usuário recebedor, solicitando autenticação e<br>confirmação para o início do processo de efetivação do<br>pagamento.|
|---|---|---|---|
|11|Usuário pagador|Ação|Usuário pagador confere as informações do usuário<br>recebedor e confirma a transação, gerando uma ordem<br>de pagamento.|


Os fluxos de jornadas de iniciação de transação de pagamento encontram-se detalhados no arcabouço
normativo do Open Finance.

#### **2.6. Geração da ordem de pagamento pela iniciação por aproximação de um** **dispositivo habilitado com tecnologia Near Field Communication (NFC) a** **outro dispositivo com mesma tecnologia**


_2.6.1._ _Transação iniciada pelo PSP do pagador_


24  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador obtém dados de<br>pagamento por meio da aproximação de um dispositivo ao<br>terminal compatível, utilizando tecnologia NFC.|
|2|Usuário pagador|Comunicação|Os dados de pagamento são encaminhados ao PSP do<br>pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados de pagamento.|
|4|PSP do pagador|Ação|PSP do pagador interpreta os dados de pagamento e<br>identifica a_location_ contida neles.|
|5|PSP do pagador|Comunicação|PSP do pagador envia consulta da_location_ ao PSP do<br>recebedor.|


25  •  Manual de Fluxos do Processo de Efetivação do Pix




|6|PSP do recebedor|Comunicação|PSP do recebedor recebe a requisição de consulta enviada<br>pelo PSP do pagador.|
|---|---|---|---|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança no<br>_payload_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite o_payload_ com os dados da<br>cobrança ao PSP do pagador.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe o_payload_ com os dados da<br>cobrança_._|
|10|PSP do pagador|Comunicação|PSP do pagador envia mensagem ao DICT para consulta das<br>informações de identificação do usuário recebedor,<br>conforme informações contidas nos dados de pagamento.|
|11|DICT|Comunicação|DICT recebe a consulta de dados sobre o usuário<br>recebedor.|
|12|DICT|Ação|DICT consulta os dados recebidos, faz a validação e retorna<br>os dados de identificação encontrados.|
|13|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os dados<br>de identificação do usuário recebedor.|
|14|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os dados<br>de identificação do usuário recebedor.|
|15|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao usuário pagador<br>com os dados do usuário recebedor e do_payload_, <br>solicitando confirmação para efetivação da ordem de<br>pagamento.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados do<br>usuário recebedor e do_payload_, solicitando confirmação<br>para efetivação do pagamento.|
|17|Usuário pagador|Ação|Usuário pagador confere as informações recebidas e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo.|


O fluxograma desta subseção reflete o processo de pagamento associado a um QR Code dinâmico
imediato, que é o modelo mais comum no varejo. Contudo, o processo também pode ser realizado
utilizando cobranças associadas a um QR Code dinâmico com vencimento ou a um QR Code estático.
Caso o PSP do pagador tenha acesso indireto ao DICT, o fluxo segue a mesma lógica do fluxo descrito na
seção 2.1.2, no que se refere às ações tomadas pelo PSP com acesso direto e sua comunicação com o
DICT.

_2.6.2_ _Transação iniciada pelo prestador de serviço de iniciação de transação de pagamento_


26  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador obtém dados de<br>pagamento por meio da aproximação de um dispositivo ao<br>terminal compatível, utilizando tecnologia NFC.|
|2|Usuário pagador|Comunicação|Os dados de pagamento são encaminhados ao PSI.|
|3|PSI|Comunicação|PSI recebe os dados de pagamento.|
|4|PSI|Ação|PSI interpreta os dados de pagamento e identifica a<br>_location_ contida neles.|
|5|PSI|Comunicação|PSI envia consulta da_location_ ao PSP do recebedor.|


27  •  Manual de Fluxos do Processo de Efetivação do Pix




|6|PSP do recebedor|Comunicação|PSP do recebedor recebe a requisição de consulta enviada<br>pelo PSI.|
|---|---|---|---|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança no<br>_payload_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite o_payload_ com os dados da<br>cobrança ao PSI.|
|9|PSI|Comunicação|PSI recebe o_payload_ com os dados da cobrança_._|
|10|PSI|Comunicação|PSI envia mensagem ao DICT para consulta das<br>informações de identificação do usuário recebedor,<br>conforme informações contidas nos dados de pagamento.|
|11|DICT|Comunicação|DICT recebe a consulta de dados sobre o usuário<br>recebedor.|
|12|DICT|Ação|DICT consulta os dados recebidos, faz a validação e retorna<br>os dados de identificação encontrados.|
|13|DICT|Comunicação|DICT envia comunicação ao PSI com os dados de<br>identificação do usuário recebedor.|
|14|PSI|Comunicação|PSI recebe comunicação do DICT com os dados de<br>identificação do usuário recebedor.|
|15|PSI|Comunicação|PSI envia comunicação ao usuário pagador com os dados<br>do usuário recebedor e do_payload_, solicitando<br>confirmação para efetivação da ordem de pagamento.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe comunicação com dados do<br>usuário recebedor e do_payload_, solicitando confirmação<br>para efetivação do pagamento.|
|17|Usuário pagador|Ação|Usuário pagador confere as informações recebidas e<br>confirma a transação, gerando a ordem de pagamento. Fim<br>do processo.|


O fluxograma desta subseção reflete o processo de pagamento associado a um QR Code dinâmico
imediato, que é o modelo mais comum no varejo. Contudo, o processo também pode ser realizado
utilizando cobranças associadas a um QR Code dinâmico com vencimento ou a um QR Code estático. Os
fluxos de jornadas de iniciação de transação de pagamento envolvendo um PSI encontram-se detalhados
no arcabouço normativo do Open Finance. Para enviar a ordem de pagamento ao PSP do pagador, o PSI
deve utilizar as APIs do Open Finance.


28  •  Manual de Fluxos do Processo de Efetivação do Pix




### **3. Fluxo de efetivação do Pix**

#### **3.1. Fluxo de transações entre participantes diretos**

Nesta seção é apresentado o fluxo das ordens enviadas para o canal primário de transmissão de
mensagens ou para o canal secundário de transmissão de mensagens do Sistema de Pagamentos
Instantâneos (SPI), nos termos do Catálogo de Serviços do SFN e do Manual das Interfaces de
Comunicação, no caso em que tanto o prestador de serviços de pagamento (PSP) do pagador quanto do
recebedor são participantes diretos do SPI.

As ordens de pagamento referentes ao Pix Automático, Pix Agendado, Pix Agendado recorrente e ao Pix
Cobrança para pagamentos com vencimento, quando agendado, devem ser enviadas para o canal
secundário de transmissão de mensagens. Essas ordens correspondem às mensagens pacs.008
preenchidas com “NORM” no campo “prioridadePagamento” e com “PAGAGD” no campo
“tipoPrioridadePagamento”, bem como todas as mensagens do seu ciclo de liquidação (as demais
pacs.008 e pacs.002 relacionadas a uma ordem de pagamento iniciada no canal secundário de
transmissão de mensagens, assim como eventuais mensagens admi.002 derivadas dessas pacs.008 e
pacs.002) [1] .

Os fluxos referentes ao agendamento da instrução de pagamento e de liquidação do Pix Automático
também trafegam no canal secundário de mensagens.

Todas as demais ordens de pagamento devem ser enviadas para o canal primário de transmissão de
mensagens.

A tabela após o fluxo detalha cada etapa do processo.


1 Informações mais detalhadas a respeito das mensagens constam do Catálogo de Serviços do SFN, disponível em
[https://www.bcb.gov.br/estabilidadefinanceira/comunicacaodados.](https://www.bcb.gov.br/estabilidadefinanceira/comunicacaodados)


29  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.1.1._ _Fluxo com liquidação imediata da ordem de pagamento_


30  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Comunicação|Início do processo. PSP do pagador recebe ordem de<br>pagamento.|
|2|PSP do pagador|Ação|PSP do pagador realiza bloqueio do valor do<br>pagamento na conta do usuário pagador.|
|3|PSP do pagador|Mensagem|PSP do pagador envia mensagem ao SPI, solicitando<br>transferência de recursos da conta PI no montante<br>do pagamento em questão para prosseguimento do<br>pagamento.|
|4|SPI|Mensagem|SPI recebe mensagem enviada pelo PSP do pagador,<br>solicitando transferência de recursos na Conta PI<br>para prosseguimento do pagamento.|
|5|SPI|Ação|SPI efetua o bloqueio na Conta PI do PSP do pagador<br>no montante do pagamento em questão.|
|6|SPI|Mensagem|SPI envia mensagem ao PSP do recebedor,<br>informando os dados para transferência.|
|7|PSP do recebedor|Mensagem|PSP do recebedor recebe mensagem com os dados<br>para transferência.|
|8|PSP do recebedor|Ação|PSP do recebedor valida a conta do usuário<br>recebedor e faz anotação provisória de crédito nessa<br>conta.|
|9|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem ao SPI,<br>solicitando o prosseguimento do pagamento.|
|10|SPI|Mensagem|SPI recebe mensagem enviada pelo PSP do<br>recebedor,<br>solicitando<br>o <br>prosseguimento<br>do<br>pagamento.|
|11|SPI|Ação|SPI efetiva a transferência de recursos nas contas PI:<br>diminui o saldo da Conta PI do PSP do pagador no<br>valor do pagamento em questão, e aumenta o saldo<br>da Conta PI do PSP do recebedor no mesmo<br>montante.|
|12|SPI|Mensagem|SPI envia mensagem de confirmação de conclusão da<br>transação ao PSP do recebedor.|
|13|PSP do recebedor|Mensagem|PSP do recebedor recebe mensagem de confirmação<br>de conclusão da transação.|
|14|PSP do recebedor|Ação|PSP do recebedor efetiva o crédito na conta do<br>usuário recebedor, no valor da transação.|
|15|PSP do recebedor|Comunicação|PSP<br>do<br>recebedor<br>envia<br>comunicação<br>de<br>confirmação de conclusão da transação ao usuário<br>recebedor.|
|16|Usuário recebedor|Comunicação|Usuário recebedor recebe comunicação, informando<br>a conclusão da transação.|
|17|SPI|Mensagem|SPI envia mensagem de confirmação de conclusão da<br>transação ao PSP do pagador.|


31  •  Manual de Fluxos do Processo de Efetivação do Pix




|18|PSP do pagador|Mensagem|PSP do pagador recebe mensagem de confirmação<br>de conclusão da transação.|
|---|---|---|---|
|19|PSP do pagador|Ação|PSP do pagador efetiva o débito na conta do usuário<br>pagador, no valor da transação.|
|20|PSP do pagador|Comunicação|PSP do pagador envia comunicação de confirmação<br>de conclusão da transação ao usuário pagador.|
|21|Usuário pagador|Comunicação|Usuário pagador recebe a comunicação, informando<br>a conclusão da transação. Fim do processo.|


_3.1.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado, Pix Agendado_
_recorrente e Pix Cobrança com vencimento)_



|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Comunicação|Início do processo. Caso o usuário pagador tenha<br>informado uma chave Pix no momento do<br>agendamento da transação, o PSP do pagador<br>encaminha, previamente à data prevista para a|


32  •  Manual de Fluxos do Processo de Efetivação do Pix






|Col1|Col2|Col3|liquidação, mensagem ao DICT para nova consulta<br>das informações de identificação do usuário<br>recebedor.<br>O EndToEndId da transação gerado nesta etapa deve<br>ser informado na PACS.008 para que haja reposição<br>de fichas no balde2.|
|---|---|---|---|
|2|DICT|Comunicação|DICT recebe consulta de dados sobre usuário<br>recebedor.|
|3|DICT|Ação|DICT consulta a chave recebida, faz a validação e<br>retorna os dados de identificação encontrados.|
|4|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os<br>dados de identificação do usuário recebedor.|
|5|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os<br>dados de identificação do usuário recebedor.|
|6|PSP do pagador|Decisão|PSP do pagador verifica a existência da chave Pix<br>informada e se a titularidade da conta a ela vinculada<br>continua a mesma da consulta realizada no<br>momento do agendamento. Caso o resultado seja<br>positivo, o fluxo segue para o passo 7. Se a chave Pix<br>for verificada como inexistente, ou a titularidade for<br>diferente da obtida na consulta ao DICT realizada no<br>momento do agendamento, o fluxo segue para o<br>passo 8.|
|7|PSP do pagador|Ação|PSP do pagador efetiva a liquidação da ordem de<br>pagamento, conforme fluxos descritos nas seções<br>3.1.1, 3.2.1, 3.3.1 e 3.4.1, a depender da condição<br>dos PSPs envolvidos. Fim do processo.|
|8|PSP do pagador|Ação|PSP do pagador cancela a ordem de pagamento<br>agendada em seus sistemas internos.|
|9|PSP do pagador|Comunicação|PSP do pagador envia notificação de insucesso na<br>liquidação da ordem de pagamento agendada ao<br>usuário pagador.|
|10|Usuário pagador|Comunicação|Usuário pagador recebe notificação de insucesso na<br>liquidação da ordem de pagamento agendada,<br>enviada pelo PSP pagador. Fim do processo.|


Caso o usuário pagador tenha inserido os dados bancários do usuário recebedor no momento do
agendamento da transação, a nova consulta ao DICT não é necessária, devendo-se pular diretamente
para a etapa 7 e proceder ao pagamento, conforme fluxo descrito na seção 3.1.1 deste Manual.


2 Informações relacionadas aos mecanismos adotados para prevenção a ataques de leitura ao DICT podem ser encontradas
[de forma mais detalhada na seção 13 do Manual Operacional do DICT.](https://www.bcb.gov.br/content/estabilidadefinanceira/pix/Regulamento_Pix/X_ManualOperacionaldoDICT.pdf)


33  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **3.2. Fluxo de transações entre participantes indiretos**

Nesta seção são apresentados os fluxos das ordens enviadas para o canal primário de transmissão de
mensagens ou para o canal secundário de transmissão de mensagens do SPI, nos termos do Catálogo de
Serviços do SFN e do Manual das Interfaces de Comunicação, no caso em que tanto o PSP do pagador
quanto do recebedor são participantes indiretos do SPI.

As ordens de pagamento referentes ao Pix Agendado, Pix Agendado recorrente e ao Pix Cobrança para
pagamentos com vencimento, quando agendado, devem ser enviadas para o canal secundário de
transmissão de mensagens. Essas ordens correspondem às mensagens pacs.008 preenchidas com
“NORM” no campo “prioridadePagamento” e com “PAGAGD” no campo “tipoPrioridadePagamento”,
bem como todas as mensagens do seu ciclo de liquidação (as demais pacs.008 e pacs.002 relacionadas
a uma ordem de pagamento iniciada no canal secundário de transmissão de mensagens, assim como
eventuais mensagens admi.002 derivadas dessas pacs.008 e pacs.002) [3] .

Os fluxos referentes ao agendamento da instrução de pagamento e de liquidação do Pix Automático
também trafegam no canal secundário de mensagens.

Todas as demais ordens de pagamento devem ser enviadas para o canal primário de transmissão de
mensagens.

A tabela após o fluxo detalha cada etapa do processo.


3 Informações mais detalhadas a respeito das mensagens constam do Catálogo de Serviços do SFN, disponível em
[https://www.bcb.gov.br/estabilidadefinanceira/comunicacaodados.](https://www.bcb.gov.br/estabilidadefinanceira/comunicacaodados)


34  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.2.1._ _Fluxo com liquidação imediata da ordem de pagamento_


35  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Comunicação|Início do processo. PSP do pagador recebe ordem<br>de pagamento.|
|2|PSP do pagador|Ação|PSP do pagador realiza bloqueio do valor do<br>pagamento na conta do usuário pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao seu<br>liquidante, solicitando transferência de recursos<br>da conta PI no montante do pagamento em<br>questão para prosseguimento do pagamento.|
|4|Liquidante do PSP<br>do pagador|Comunicação|Liquidante<br>do<br>PSP<br>do<br>pagador<br>recebe<br>comunicação,<br>solicitando<br>transferência<br>de<br>recursos na Conta PI para prosseguimento do<br>pagamento.|
|5|Liquidante do PSP<br>do pagador|Mensagem|Liquidante do PSP do pagador envia mensagem ao<br>SPI, solicitando transferência de recursos na Conta<br>PI para prosseguimento do pagamento.|
|6|SPI|Mensagem|SPI recebe mensagem enviada pelo liquidante do<br>PSP do pagador, solicitando transferência de<br>recursos na Conta PI para prosseguimento do<br>pagamento.|
|7|SPI|Ação|SPI efetua o bloqueio na Conta PI do liquidante do<br>PSP do pagador no montante do pagamento em<br>questão.|
|8|SPI|Mensagem|SPI envia mensagem ao liquidante do PSP do<br>recebedor, informando os dados da transferência.|
|9|Liquidante do PSP<br>do recebedor|Mensagem|Liquidante do PSP do recebedor recebe mensagem<br>com os dados da transferência.|
|10|Liquidante do PSP<br>do recebedor|Comunicação|Liquidante<br>do<br>PSP<br>do<br>recebedor<br>envia<br>comunicação ao PSP do recebedor com os dados<br>da transferência.|
|11|PSP do recebedor|Comunicação|PSP do recebedor recebe comunicação com os<br>dados da transferência.|
|12|PSP do recebedor|Ação|PSP do recebedor valida a conta do usuário<br>recebedor e faz anotação provisória de crédito<br>nessa conta.|
|13|PSP do recebedor|Comunicação|PSP do recebedor envia comunicação ao seu<br>liquidante, solicitando o prosseguimento do<br>pagamento.|
|14|Liquidante do PSP<br>do recebedor|Comunicação|Liquidante<br>do<br>PSP<br>do<br>recebedor<br>recebe<br>comunicação enviada pelo PSP do recebedor,<br>solicitando o prosseguimento do pagamento.|
|15|Liquidante do PSP<br>do recebedor|Mensagem|Liquidante do PSP do recebedor envia mensagem<br>ao<br>SPI,<br>solicitando<br>o <br>prosseguimento<br>do<br>pagamento.|
|16|SPI|Mensagem|SPI recebe mensagem enviada pelo liquidante do<br>PSP do recebedor, solicitando o prosseguimento<br>do pagamento.|


36  •  Manual de Fluxos do Processo de Efetivação do Pix






|17|SPI|Ação|SPI efetiva a troca de saldos nas contas PI: diminui<br>o saldo da Conta PI do liquidante do PSP do<br>pagador no valor do pagamento em questão e<br>aumenta o saldo da Conta PI do liquidante do PSP<br>do recebedor no mesmo montante.|
|---|---|---|---|
|18|SPI|Mensagem|SPI envia confirmação de conclusão da transação<br>ao liquidante do PSP do recebedor.|
|19|Liquidante do PSP<br>do recebedor|Mensagem|Liquidante do PSP do recebedor recebe mensagem<br>de confirmação de conclusão da transação enviada<br>pelo SPI.|
|20|Liquidante do PSP<br>do recebedor|Comunicação|Liquidante<br>do<br>PSP<br>do<br>recebedor<br>envia<br>comunicação de confirmação de conclusão da<br>transação ao PSP do recebedor ao PSP do<br>recebedor.|
|21|PSP do recebedor|Comunicação|PSP do recebedor recebe comunicação de<br>confirmação de conclusão da transação.|
|22|PSP do recebedor|Ação|PSP do recebedor efetiva o crédito na conta do<br>usuário recebedor, no valor da transação.|
|23|PSP do recebedor|Comunicação|PSP do recebedor envia comunicação de<br>confirmação de conclusão da transação ao usuário<br>recebedor.|
|24|Usuário recebedor|Comunicação|Usuário<br>recebedor<br>recebe<br>a <br>comunicação<br>informando a conclusão da transação. Fim do<br>processo.|
|25|SPI|Mensagem|SPI envia confirmação de conclusão da transação<br>ao liquidante do PSP do pagador.|
|26|Liquidante do PSP<br>do pagador|Mensagem|Liquidante do PSP do pagador recebe mensagem<br>de confirmação de conclusão da transação enviada<br>pelo SPI.|
|27|Liquidante do PSP<br>do pagador|Comunicação|Liquidante do PSP do pagador envia comunicação<br>de confirmação de conclusão da transação ao PSP<br>do pagador.|
|28|PSP do pagador|Comunicação|PSP<br>do<br>pagador<br>recebe<br>comunicação<br>de<br>confirmação de conclusão da transação.|
|29|PSP do pagador|Ação|PSP do pagador efetiva o débito na conta do<br>usuário pagador no valor da transação.|
|30|PSP do pagador|Comunicação|PSP<br>do<br>pagador<br>envia<br>comunicação<br>de<br>confirmação de conclusão da transação ao usuário<br>pagador.|
|31|Usuário pagador|Comunicação|Usuário<br>pagador<br>recebe<br>a <br>comunicação,<br>informando a conclusão da transação.|


37  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.2.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado, Pix Agendado_
_recorrente e Pix Cobrança com vencimento)_



|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Comunicação|Início do processo. Caso o usuário pagador<br>tenha informado uma chave Pix no<br>momento do agendamento da transação,<br>o <br>PSP<br>do<br>pagador<br>encaminha,<br>previamente à data prevista para a<br>liquidação, mensagem ao participante<br>com acesso direto ao DICT para nova<br>consulta das informações de identificação<br>do usuário recebedor.|


38  •  Manual de Fluxos do Processo de Efetivação do Pix






|2|Participante com<br>acesso direto ao DICT|Comunicação|O participante com acesso direto ao DICT<br>recebe os dados do pagamento<br>encaminhados pelo PSP do pagador.|
|---|---|---|---|
|3|Participante com<br>acesso direto ao DICT|Comunicação|Participante<br>com<br>acesso<br>direto<br>se<br>comunica com o DICT para consulta das<br>informações de identificação do usuário<br>recebedor. O_EndToEndId_ da transação<br>gerado nesta etapa deve ser informado na<br>PACS.008 para que haja reposição de<br>fichas no balde4.|
|4|DICT|Comunicação|DICT recebe consulta de dados sobre<br>usuário recebedor.|
|5|DICT|Ação|DICT consulta a chave recebida, faz a<br>validação<br>e <br>retorna<br>os<br>dados<br>de<br>identificação encontrados.|
|6|DICT|Comunicação|DICT envia comunicação ao participante<br>com acesso direto, informando os dados<br>de identificação do usuário recebedor.|
|7|Participante com<br>acesso direto ao DICT|Comunicação|Participante com acesso direto ao DICT<br>recebe comunicação com os dados de<br>identificação do usuário recebedor.|
|8|Participante com<br>acesso direto ao DICT|Comunicação|Participante com acesso direto ao DICT se<br>comunica com o PSP do pagador,<br>informando<br>os<br>dados<br>do<br>usuário<br>recebedor.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do<br>participante com acesso direto com os<br>dados<br>de<br>identificação<br>do<br>usuário<br>recebedor.|
|10|PSP do pagador|Decisão|PSP do pagador verifica a existência da<br>chave Pix informada e se a titularidade da<br>conta a ela vinculada continua a mesma<br>da consulta realizada no momento do<br>agendamento. Caso o resultado seja<br>positivo, o fluxo segue para o passo 11. Se<br>a <br>chave<br>Pix<br>for<br>verificada<br>como<br>inexistente, ou a titularidade for diferente<br>da obtida na consulta ao DICT realizada no<br>momento do agendamento, o fluxo segue<br>para o passo 12.|
|11|PSP do pagador|Ação|PSP do pagador efetiva a liquidação da<br>ordem de pagamento, conforme fluxos<br>descritos nas seções 3.1.1, 3.2.1, 3.3.1 e|



4 Informações relacionadas aos mecanismos adotados para prevenção a ataques de leitura ao DICT podem ser encontradas
[de forma mais detalhada na seção 13 do Manual Operacional do DICT.](https://www.bcb.gov.br/content/estabilidadefinanceira/pix/Regulamento_Pix/X_ManualOperacionaldoDICT.pdf)


39  •  Manual de Fluxos do Processo de Efetivação do Pix




|Col1|Col2|Col3|3.4.1, a depender da condição dos PSPs<br>envolvidos. Fim do processo.|
|---|---|---|---|
|12|PSP do pagador|Ação|PSP do pagador cancela a ordem de<br>pagamento agendada em seus sistemas<br>internos.|
|13|PSP do pagador|Comunicação|PSP do pagador envia notificação de<br>insucesso na liquidação da ordem de<br>pagamento agendada ao usuário pagador.|
|14|Usuário pagador|Comunicação|Usuário pagador recebe notificação de<br>insucesso na liquidação da ordem de<br>pagamento agendada, enviada pelo PSP<br>pagador. Fim do processo.|


Caso o usuário pagador tenha inserido os dados bancários do usuário recebedor no momento do
agendamento da transação, a nova consulta ao DICT não é necessária, devendo-se pular diretamente
para a etapa 11 e proceder ao pagamento, conforme fluxo descrito na seção 3.2.1 deste Manual.


40  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **3.3. Fluxo de transações nos livros do PSP**

Nesta seção são apresentados os fluxos das ordens enviadas para liquidação, no caso em que o PSP do
pagador e o PSP do recebedor são a mesma instituição, independentemente de o PSP ser participante
direto ou indireto do SPI.


A tabela após o fluxo detalha cada etapa do processo.


41  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.3.1._ _Fluxo com liquidação imediata da ordem de pagamento_







|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP|Comunicação|Início do processo. PSP recebe ordem de<br>pagamento.|
|2|PSP|Ação|PSP verifica se há saldo na conta do usuário<br>pagador e valida a conta do usuário recebedor.|
|3|PSP|Ação|Caso as verificações de saldo e conta sejam<br>positivas, PSP debita a conta do usuário pagador e<br>credita a conta do usuário recebedor, efetivando a<br>transação em seus livros.|
|4|PSP|Comunicação|PSP envia notificação de confirmação de conclusão<br>da transação ao usuário recebedor.|
|5|Usuário recebedor|Comunicação|Usuário<br>recebedor<br>recebe<br>a <br>notificação,<br>informando a conclusão da transação.|
|6|PSP|Comunicação|PSP envia notificação de confirmação de conclusão<br>da transação ao usuário pagador.|
|7|Usuário pagador|Comunicação|Usuário<br>pagador<br>recebe<br>a <br>comunicação<br>informando a conclusão da transação.|


42  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.3.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado, Pix Agendado_
_recorrente e Pix Cobrança com vencimento)_



|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP|Ação|Início do processo. Caso o usuário pagador tenha<br>informado uma chave Pix no momento do<br>agendamento da transação, na data prevista para<br>liquidação, o PSP verifica se há saldo na conta do<br>usuário pagador e valida a conta do usuário<br>recebedor.|
|2|PSP|Decisão|PSP verifica se a chave Pix informada no<br>momento<br>do<br>agendamento<br>permanece<br>cadastrada na instituição. Caso o resultado seja<br>positivo, fluxo segue para o passo 8. Se houve<br>portabilidade ou reinvindicação da chave Pix e ela<br>não estiver mais cadastrada no PSP, fluxo segue<br>para o passo 3.|


43  •  Manual de Fluxos do Processo de Efetivação do Pix






|3|PSP|Comunicação|PSP comunica-se com o DICT para consulta das<br>informações de identificação do usuário<br>recebedor.|
|---|---|---|---|
|4|DICT|Comunicação|DICT recebe consulta de dados sobre usuário<br>recebedor.|
|5|DICT|Ação|DICT consulta a chave recebida, faz a validação e<br>retorna os dados de identificação encontrados.|
|6|DICT|Comunicação|DICT envia comunicação ao PSP, informando os<br>dados de identificação do usuário recebedor.|
|7|PSP|Comunicação|PSP recebe comunicação com os dados de<br>identificação do usuário recebedor.|
|8|PSP|Decisão|PSP verifica a existência da chave Pix informada e<br>se a titularidade da conta a ela vinculada continua<br>a mesma da consulta realizada no momento do<br>agendamento. Caso o resultado seja positivo,<br>fluxo segue para o passo 9. Se a titularidade for<br>diferente da obtida na consulta ao DICT realizada<br>no momento do agendamento, fluxo segue para<br>o passo 10.|
|9|PSP|Ação|PSP do pagador efetiva a liquidação da ordem de<br>pagamento, conforme fluxos descritos nas seções<br>3.1.1, 3.2.1, 3.3.1 e 3.4.1, a depender da condição<br>dos PSPs envolvidos. Fim do processo.|
|10|PSP|Ação|PSP cancela a ordem de pagamento agendada em<br>seus sistemas internos.|
|11|PSP|Comunicação|PSP do pagador envia notificação de insucesso na<br>liquidação da ordem de pagamento agendada ao<br>usuário pagador.|
|12|Usuário pagador|Comunicação|Usuário pagador recebe notificação de insucesso<br>na liquidação da ordem de pagamento agendada,<br>enviada pelo PSP pagador. Fim do processo.|


44  •  Manual de Fluxos do Processo de Efetivação do Pix






#### **3.4. Fluxo de transações entre participantes indiretos com mesmo liquidante**

Nesta seção é apresentado o fluxo das ordens enviadas para liquidação, no caso em que o PSP do
pagador e o PSP do recebedor são participantes indiretos do SPI e mantêm relacionamento com o
mesmo liquidante.


A tabela após o fluxo detalha cada etapa do processo.


45  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.4.1._ _Fluxo com liquidação imediata da ordem de pagamento_



|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Comunicação|Início do processo. PSP do pagador recebe ordem de<br>pagamento.|
|2|PSP do pagador|Ação|PSP do pagador realiza bloqueio do valor do<br>pagamento na conta do usuário pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador envia comunicação ao liquidante,<br>solicitando troca de saldo na Conta PI para<br>prosseguimento do pagamento.|


46  •  Manual de Fluxos do Processo de Efetivação do Pix






|4|Liquidante|Comunicação|Liquidante recebe solicitação de troca de saldo na<br>Conta PI, enviada pelo PSP do pagador, para<br>prosseguimento do pagamento.|
|---|---|---|---|
|5|Liquidante|Comunicação|Liquidante, ao identificar que também é liquidante do<br>PSP do recebedor, envia comunicação ao PSP do<br>recebedor informando os dados da transferência.|
|6|PSP do recebedor|Comunicação|PSP do recebedor recebe comunicação com os dados<br>da transferência.|
|7|PSP do recebedor|Ação|PSP do recebedor valida a conta do usuário recebedor<br>e faz anotação provisória de crédito nessa conta.|
|8|PSP do recebedor|Comunicação|PSP do recebedor envia comunicação ao liquidante,<br>solicitando o prosseguimento do pagamento.|
|9|Liquidante|Comunicação|Liquidante recebe comunicação enviada pelo PSP do<br>recebedor,<br>solicitando<br>o <br>prosseguimento<br>do<br>pagamento.|
|10|Liquidante|Ação|Liquidante efetiva ajuste no controle interno de saldos:<br>diminui o saldo da conta interna do PSP do pagador no<br>valor do pagamento em questão, e aumenta o saldo da<br>conta interna do PSP do recebedor no mesmo<br>montante.|
|11|Liquidante|Comunicação|Liquidante envia confirmação de conclusão da<br>transação ao PSP do recebedor.|
|12|PSP do recebedor|Comunicação|PSP do recebedor recebe comunicação de confirmação<br>de conclusão da transação.|
|13|PSP do recebedor|Ação|PSP do recebedor efetiva o crédito na conta do usuário<br>recebedor|
|14|PSP do recebedor|Comunicação|PSP do recebedor envia comunicação de confirmação<br>de conclusão da transação ao usuário recebedor.|
|15|Usuário recebedor|Comunicação|Usuário recebedor recebe a comunicação informando<br>a conclusão da transação.|
|16|Liquidante|Comunicação|Liquidante envia confirmação de conclusão da<br>transação ao PSP do pagador.|
|17|PSP do pagador|Comunicação|PSP do pagador recebe comunicação de confirmação<br>de conclusão da transação.|
|18|PSP do pagador|Ação|PSP do pagador efetiva o débito na conta do usuário<br>pagador no valor da transação.|
|19|PSP do pagador|Comunicação|PSP do pagador envia comunicação de confirmação de<br>conclusão da transação ao usuário pagador.|
|20|Usuário pagador|Comunicação|Usuário pagador recebe a comunicação, informando a<br>conclusão da transação.|


47  •  Manual de Fluxos do Processo de Efetivação do Pix




_3.4.2._ _Fluxo com liquidação agendada da ordem de pagamento (Pix Agendado e Pix Agendado_
_recorrente e Pix Cobrança com vencimento)_







|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Comunicação|Início do processo. Caso o usuário pagador tenha<br>informado uma chave Pix no momento do<br>agendamento da transação, o PSP do pagador<br>encaminha, previamente à data prevista para a<br>liquidação, mensagem ao DICT para nova consulta<br>das informações de identificação do usuário<br>recebedor. O_EndToEndId_ da transação gerado nesta<br>etapa deve ser informado na PACS.008, para que<br>haja reposição de fichas no balde5.|
|2|DICT|Comunicação|DICT recebe consulta de dados sobre usuário<br>recebedor.|


5 Informações relacionadas aos mecanismos adotados para prevenção a ataques de leitura ao DICT podem ser encontradas
[de forma mais detalhada na seção 13 do Manual Operacional do DICT.](https://www.bcb.gov.br/content/estabilidadefinanceira/pix/Regulamento_Pix/X_ManualOperacionaldoDICT.pdf)


48  •  Manual de Fluxos do Processo de Efetivação do Pix




|3|DICT|Ação|DICT consulta a chave recebida, faz a validação e<br>retorna os dados de identificação encontrados.|
|---|---|---|---|
|4|DICT|Comunicação|DICT envia comunicação ao PSP do pagador com os<br>dados de identificação do usuário recebedor.|
|5|PSP do pagador|Comunicação|PSP do pagador recebe comunicação do DICT com os<br>dados de i/dentificação do usuário recebedor.|
|6|PSP do pagador|Ação|PSP do pagador verifica a existência da chave Pix<br>informada e se a titularidade da conta a ela vinculada<br>continua a mesma da consulta realizada no<br>momento do agendamento. Caso o resultado seja<br>positivo, fluxo segue para o passo 7. Se a chave Pix<br>for verificada como inexistente, ou a titularidade for<br>diferente da obtida na consulta ao DICT realizada no<br>momento do agendamento, fluxo segue para o passo<br>8.|
|7|PSP do pagador|Ação|PSP do pagador efetiva a liquidação da ordem de<br>pagamento, conforme fluxos descritos nas seções<br>3.1.1, 3.2.1, 3.3.1 e 3.4.1, a depender da condição<br>dos PSPs envolvidos. Fim do processo.|
|8|PSP do pagador|Ação|PSP do pagador cancela a ordem de pagamento<br>agendada em seus sistemas internos.|
|9|PSP do pagador|Comunicação|PSP do pagador envia notificação de insucesso na<br>liquidação da ordem de pagamento agendada ao<br>usuário pagador.|
|10|Usuário pagador|Comunicação|Usuário pagador recebe notificação de insucesso na<br>liquidação da ordem de pagamento agendada,<br>enviada pelo PSP pagador. Fim do processo.|


49  •  Manual de Fluxos do Processo de Efetivação do Pix






### **4. Fluxo de devolução do Pix**

Nos fluxos de devolução, o usuário recebedor da transação original é identificado como usuário
remetente e o usuário pagador da transação original é identificado como usuário destinatário.


50  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **4.1. Fluxo de devolução entre participantes diretos**

51  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do<br>remetente|Comunicação|Início do processo. PSP do remetente recebe ordem de<br>devolução.|
|2|PSP do<br>remetente|Ação|PSP do remetente realiza bloqueio do valor da devolução<br>na conta do usuário remetente.|
|3|PSP do<br>remetente|Mensagem|PSP do remetente envia mensagem ao SPI, solicitando<br>troca de saldo na Conta PI para prosseguimento da<br>devolução.|
|4|SPI|Mensagem|SPI recebe mensagem enviada pelo PSP do remetente,<br>solicitando<br>troca<br>de<br>saldo<br>na<br>Conta<br>PI<br>para<br>prosseguimento da devolução.|
|5|SPI|Ação|SPI efetua o bloqueio na Conta PI do PSP do remetente no<br>montante da devolução em questão.|
|6|SPI|Mensagem|SPI envia mensagem ao PSP do destinatário, informando<br>os dados da devolução.|
|7|PSP do<br>destinatário|Mensagem|PSP do destinatário recebe mensagem com os dados da<br>devolução.|
|8|PSP do<br>destinatário|Ação|PSP do destinatário da devolução recupera, com base no<br>_EndToEndId_, a data do pagamento, o valor da transação e<br>os dados da conta transacional do destinatário da<br>devolução.|
|9|PSP do<br>destinatário|Ação|PSP do destinatário valida a devolução: verifica se atende<br>ao prazo de noventa dias, se o destinatário é seu cliente,<br>se o valor está adequado e se a conta do usuário<br>destinatário está ativa.|
|10|PSP do<br>destinatário|Ação|PSP do destinatário faz anotação provisória de crédito na<br>conta do usuário destinatário.|
|11|PSP do<br>destinatário|Mensagem|PSP do destinatário envia mensagem ao SPI, solicitando o<br>prosseguimento da devolução.|
|12|SPI|Mensagem|SPI recebe mensagem enviada pelo PSP do destinatário,<br>solicitando o prosseguimento da devolução.|
|13|SPI|Ação|SPI efetiva a troca de saldos nas contas PI: diminui o saldo<br>da Conta PI do PSP do remetente no valor da devolução<br>em questão e aumenta o saldo da Conta PI do PSP do<br>destinatário no mesmo montante.|
|14|SPI|Mensagem|SPI envia mensagem, confirmando a conclusão da<br>transação ao PSP do destinatário.|
|15|PSP do<br>destinatário|Mensagem|PSP do destinatário recebe mensagem de confirmação de<br>conclusão da devolução.|
|16|PSP do<br>destinatário|Ação|PSP do destinatário efetiva o crédito na conta do usuário<br>destinatário.|
|17|PSP do<br>destinatário|Comunicação|PSP do destinatário envia comunicação de confirmação<br>de conclusão da devolução ao usuário destinatário.|
|18|Usuário<br>destinatário|Comunicação|Usuário destinatário recebe a comunicação informando a<br>conclusão da devolução.|
|19|SPI|Mensagem|SPI envia mensagem, confirmando a conclusão da<br>transação ao PSP do remetente.|


52  •  Manual de Fluxos do Processo de Efetivação do Pix




|20|PSP do<br>remetente|Mensagem|PSP do remetente recebe mensagem de confirmação de<br>conclusão da devolução.|
|---|---|---|---|
|21|PSP do<br>remetente|Ação|PSP do remetente efetiva o débito na conta do usuário<br>remetente no valor da devolução.|
|22|PSP do<br>remetente|Comunicação|PSP do remetente envia comunicação de confirmação de<br>conclusão da devolução ao usuário remetente.|
|23|Usuário<br>remetente|Comunicação|Usuário remetente recebe a comunicação informando a<br>conclusão da devolução.|


53  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **4.2. Fluxo de devolução entre participantes indiretos**

54  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do<br>remetente|Comunicação|Início do processo. PSP do remetente recebe ordem de<br>devolução.|
|2|PSP do<br>remetente|Ação|PSP do remetente realiza bloqueio do valor da devolução<br>na conta do usuário remetente.|
|3|PSP do<br>remetente|Comunicação|PSP do remetente envia comunicação ao seu liquidante,<br>solicitando<br>troca<br>de<br>saldo<br>na<br>Conta<br>PI<br>para<br>prosseguimento da devolução.|
|4|Liquidante do<br>PSP do<br>remetente|Comunicação|Liquidante do PSP do remetente recebe comunicação,<br>solicitando<br>troca<br>de<br>saldo<br>na<br>Conta<br>PI<br>para<br>prosseguimento da devolução.|
|5|Liquidante do<br>PSP do<br>remetente|Mensagem|Liquidante do PSP do envia mensagem ao SPI, solicitando<br>troca de saldo na Conta PI para prosseguimento da<br>devolução.|
|6|SPI|Mensagem|SPI recebe mensagem, solicitando troca de saldo na Conta<br>PI para prosseguimento da devolução.|
|7|SPI|Ação|SPI efetua o bloqueio na Conta PI do liquidante do PSP do<br>remetente no montante da devolução em questão.|
|8|SPI|Mensagem|SPI envia mensagem ao liquidante do PSP do destinatário,<br>informando os dados da devolução.|
|9|Liquidante do<br>PSP do<br>destinatário|Mensagem|Liquidante do PSP do destinatário recebe mensagem com<br>os dados da devolução.|
|10|Liquidante do<br>PSP do<br>destinatário|Comunicação|Liquidante do PSP do destinatário envia comunicação ao<br>PSP do destinatário com os dados da devolução.|
|11|PSP do<br>destinatário|Comunicação|PSP do destinatário recebe comunicação com os dados da<br>devolução.|
|12|PSP do<br>destinatário|Ação|PSP do destinatário da devolução recupera, com base no<br>_EndToEndId_, a data do pagamento, o valor da transação e<br>os dados da conta transacional do destinatário da<br>devolução.|
|13|PSP do<br>destinatário|Ação|PSP do destinatário valida a devolução: verifica se atende<br>ao prazo de noventa dias, se o destinatário é seu cliente,<br>se o valor está adequado e se a conta do usuário<br>destinatário está ativa.|
|14|PSP do<br>destinatário|Ação|PSP do destinatário faz anotação provisória de crédito na<br>conta do usuário destinatário.|
|15|PSP do<br>destinatário|Comunicação|PSP do destinatário envia comunicação ao liquidante do<br>PSP do destinatário, solicitando o prosseguimento da<br>devolução.|
|16|Liquidante do<br>PSP do<br>destinatário|Comunicação|Liquidante do PSP do destinatário recebe comunicação<br>enviada pelo PSP do destinatário, solicitando o<br>prosseguimento da devolução.|
|17|Liquidante do<br>PSP do<br>destinatário|Mensagem|Liquidante do PSP do destinatário envia mensagem ao SPI,<br>solicitando o prosseguimento da devolução.|



55  •  Manual de Fluxos do Processo de Efetivação do Pix




|18|SPI|Mensagem|SPI recebe mensagem enviada pelo liquidante do PSP do<br>destinatário solicitando o prosseguimento da devolução|
|---|---|---|---|
|19|SPI|Ação|SPI efetiva a troca de saldos nas contas PI: diminui o saldo<br>da Conta PI do liquidante do PSP do remetente no valor<br>da devolução em questão e aumenta o saldo da Conta PI<br>do liquidante do PSP do destinatário no mesmo<br>montante.|
|20|SPI|Mensagem|SPI envia confirmação de conclusão da devolução ao<br>liquidante do PSP do destinatário.|
|21|Liquidante do<br>PSP do<br>destinatário|Mensagem|Liquidante do PSP do destinatário recebe mensagem de<br>confirmação de conclusão da devolução enviada pelo SPI.|
|22|Liquidante do<br>PSP do<br>destinatário|Comunicação|Liquidante do PSP do destinatário envia comunicação de<br>confirmação de conclusão da devolução ao PSP do<br>destinatário.|
|23|PSP do<br>destinatário|Comunicação|PSP do destinatário recebe comunicação de confirmação<br>de conclusão da devolução.|
|24|PSP do<br>destinatário|Ação|PSP do destinatário efetiva o crédito na conta do usuário<br>destinatário|
|25|PSP do<br>destinatário|Comunicação|PSP do destinatário envia comunicação de confirmação de<br>conclusão da devolução ao usuário destinatário.|
|26|Usuário<br>destinatário|Comunicação|Usuário destinatário recebe a comunicação informando a<br>conclusão da devolução.|
|27|SPI|Mensagem|SPI envia confirmação de conclusão da devolução ao<br>liquidante do PSP do remetente.|
|28|Liquidante do<br>PSP do<br>remetente|Mensagem|Liquidante do PSP do remetente recebe mensagem de<br>confirmação de conclusão da devolução enviada pelo SPI.|
|29|Liquidante do<br>PSP do<br>remetente|Comunicação|Liquidante do PSP do remetente envia comunicação de<br>confirmação de conclusão da devolução ao PSP do<br>remetente.|
|30|PSP do<br>remetente|Comunicação|PSP do remetente recebe comunicação de confirmação<br>de conclusão da devolução.|
|31|PSP do<br>remetente|Ação|PSP do remetente efetiva o débito na conta do usuário<br>remetente no valor da devolução.|
|32|PSP do<br>remetente|Comunicação|PSP do remetente envia comunicação de confirmação de<br>conclusão da devolução ao usuário remetente.|
|33|Usuário<br>remetente|Comunicação|Usuário remetente recebe a comunicação informando a<br>conclusão da devolução.|


56  •  Manual de Fluxos do Processo de Efetivação do Pix




### **5. Fluxos do Pix Automático**

Nesta seção são apresentados os fluxos de autorização, concedida no ambiente do PSP do pagador pelo
usuário pagador, para realização de pagamentos de cobranças recorrentes, os fluxos de agendamento
dos pagamentos recorrentes e os fluxos de cancelamento tanto de pagamentos já agendados quanto da
própria recorrência.

Os fluxos referentes às jornadas de autorização e de cancelamento de autorização (correspondentes às
mensagens PAIN.009, PAIN.011 e PAIN.012), além daqueles referentes ao cancelamento dos
agendamentos (e que correspondem às mensagens CAMT.029 e CAMT.055) ocorrem pelo canal
primário de mensagens. Enquanto isso, os fluxos referentes ao agendamento da instrução de
pagamento (correspondentes às mensagens PAIN.013 e PAIN.014) e de liquidação (mensagens
PACS.008 e PACS.002) do Pix Automático ocorrem no canal secundário de mensagens.

#### **5.1. Fluxos de autorização**


_5.1.1._ _Jornada 1 – Usuário pagador escolhe Pix Automático como forma de pagamento (interação_
_externa ao ecossistema)_


5.1.1.1. _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


_**Etapa em que o usuário recebedor cria uma recorrência junto ao seu PSP e solicita confirmação**_
_**ao usuário pagador:**_


57  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor envia os dados da<br>recorrência ao PSP do recebedor.|
|2|PSP do recebedor|Comunicação|PSP do recebedor recebe os dados da recorrência enviados<br>pelo usuário recebedor.|
|3|PSP do recebedor|Ação|PSP do recebedor armazena os dados da recorrência em<br>seus sistemas internos.|
|4|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.009 com os dados<br>da recorrência.|
|5|ICOM|Mensagem|ICOM recebe mensagem PAIN.009 com os dados da<br>recorrência.|
|6|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.009 ao PSP do<br>pagador.|
|7|PSP do pagador|Mensagem|PSP do pagador recebe a mensagem PAIN.009 com os<br>dados da recorrência.|


58  •  Manual de Fluxos do Processo de Efetivação do Pix




|8|PSP do pagador|Ação|PSP do pagador armazena os dados da recorrência em seus<br>sistemas internos.|
|---|---|---|---|
|9|PSP do pagador|Mensagem|PSP do pagador envia mensagem PAIN.012, em resposta à<br>mensagem PAIN.009.|
|10|ICOM|Mensagem|ICOM recebe a mensagem PAIN.012, em resposta à<br>mensagem PAIN.009.|
|11|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>recebedor.|
|12|PSP do recebedor|Mensagem|PSP do recebedor recebe a mensagem PAIN.012, em<br>resposta à mensagem PAIN.009.|
|13|PSP do pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>solicitando autorização para pagamento de cobranças<br>recorrentes futuras por Pix Automático.|
|14|Usuário pagador|Comunicação|Usuário pagador recebe solicitação de autorização do PSP<br>para pagamento de cobranças recorrentes futuras por Pix<br>Automático. Fim do processo.|


59  •  Manual de Fluxos do Processo de Efetivação do Pix






_**Etapa de confirmação da recorrência pelo usuário pagador:**_













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador confere os dados da<br>recorrência e autoriza o Pix Automático como forma de<br>pagamento de cobranças recorrentes futuras.|
|2|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do<br>Pix Automático ao PSP do pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe a confirmação da autorização do<br>Pix<br>Automático<br>para<br>pagamentos<br>de<br>cobranças<br>recorrentes futuras.|
|4|PSP do pagador|Ação|PSP do pagador atualiza o status da recorrência em seus<br>sistemas internos.|


60  •  Manual de Fluxos do Processo de Efetivação do Pix




|5|PSP do pagador|Mensagem|PSP do pagador envia mensagem PAIN.012 de<br>confirmação da recorrência.|
|---|---|---|---|
|6|ICOM|Mensagem|ICOM recebe mensagem PAIN.012 de confirmação da<br>recorrência.|
|7|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 de confirmação<br>da recorrência ao PSP do recebedor.|
|8|PSP do recebedor|Mensagem|PSP do recebedor recebe mensagem PAIN.012 de<br>confirmação da recorrência.|
|9|PSP do recebedor|Ação|PSP do recebedor atualiza o status da recorrência em seus<br>sistemas internos.|
|10|PSP do recebedor|Comunicação|PSP do recebedor envia ao usuário recebedor a<br>notificação de confirmação do Pix Automático como<br>forma de pagamento de cobranças recorrentes futuras.|
|11|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação<br>do Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|12|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|13|ICOM|Mensagem|ICOM recebe mensagem PAIN.012.|
|14|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>pagador.|
|15|PSP do pagador|Mensagem|PSP do pagador recebe mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|16|PSP do Pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>confirmando a autorização para que o pagamento de<br>cobranças recorrentes futuras seja realizado por Pix<br>Automático.|
|17|Usuário pagador|Comunicação|Usuário pagador recebe a confirmação de que a<br>autorização para o Pix Automático foi concluída com<br>sucesso. Fim do processo.|


61  •  Manual de Fluxos do Processo de Efetivação do Pix






_5.1.1.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor envia os dados da<br>recorrência ao PSP.|
|2|PSP|Comunicação|PSP recebe os dados da recorrência enviados pelo usuário<br>recebedor.|
|3|PSP|Ação|PSP armazena os dados da recorrência em seus sistemas<br>internos.|
|4|PSP|Comunicação|PSP envia notificação ao usuário pagador, solicitando<br>autorização para pagamento de cobranças recorrentes<br>futuras por Pix Automático.|
|5|Usuário pagador|Comunicação|Usuário pagador recebe solicitação de autorização do PSP<br>para pagamento de cobranças recorrentes futuras por Pix<br>Automático.|
|6|Usuário pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|7|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do<br>Pix Automático ao PSP.|
|8|PSP|Comunicação|PSP recebe a confirmação da autorização do Pix<br>Automático para pagamentos de cobranças recorrentes<br>futuras.|
|9|PSP|Ação|PSP atualiza o status da recorrência em seus sistemas<br>internos.|


62  •  Manual de Fluxos do Processo de Efetivação do Pix




|10|PSP|Comunicação|PSP envia ao usuário recebedor a notificação de<br>confirmação do Pix Automático como forma de<br>pagamento de cobranças recorrentes futuras.|
|---|---|---|---|
|11|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação<br>do Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|12|PSP|Comunicação|PSP envia notificação ao usuário pagador, confirmando a<br>autorização para que o pagamento de cobranças<br>recorrentes futuras seja realizado por Pix Automático.|
|13|Usuário pagador|Comunicação|Usuário pagador recebe a confirmação de que a<br>autorização para o Pix Automático foi concluída com<br>sucesso. Fim do processo.|


_5.1.2._ _Jornada 2 – Usuário pagador realiza adesão por meio do PSP do pagador (leitura de QR Code_
_contendo os dados da recorrência)_


_5.1.2.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


_**Etapa de envio dos dados da recorrência pelo usuário recebedor ao usuário pagador:**_

|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Ação|Início do processo. Usuário recebedor gera o_QR Code_ com<br>os dados da recorrência.|
|2|Usuário recebedor|Comunicação|Usuário recebedor envia, por fora do ecossistema Pix, o_QR_<br>_Code_ com os dados da recorrência ao usuário pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe o_QR Code_ para leitura no app do<br>PSP do pagador. Fim do processo.|



63  •  Manual de Fluxos do Processo de Efetivação do Pix




_**Etapa de confirmação da recorrência pelo usuário pagador:**_


64  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ disponibilizado pelo usuário recebedor por fora do<br>ecossistema Pix.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ são encaminhados ao PSP do<br>pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do_QR Code_.|
|4|PSP do pagador|Ação|PSP do pagador interpreta o_QR Code_ e identifica a<br>_location_ contida nele.|
|5|PSP do pagador|Comunicação|PSP do pagador envia a consulta da_location_ ao PSP do<br>recebedor.|
|6|PSP do recebedor|Comunicação|PSP do recebedor recebe a requisição de consulta<br>enviada pelo PSP do pagador.|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da recorrência no<br>_payload_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite o_payload_ com os dados da<br>recorrência ao PSP do pagador.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe o_payload_ com os dados da<br>recorrência.|
|10|PSP do pagador|Comunicação|PSP do pagador envia os dados da recorrência ao usuário<br>pagador, para confirmação.|
|11|Usuário pagador|Comunicação|Usuário pagador recebe os dados da recorrência para<br>confirmação, no app do PSP do pagador.|
|12|Usuário pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|13|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do<br>Pix Automático ao PSP do pagador.|
|14|PSP do pagador|Comunicação|PSP do pagador recebe a confirmação da autorização do<br>Pix<br>Automático<br>para<br>pagamentos<br>de<br>cobranças<br>recorrentes futuras.|
|15|PSP do pagador|Ação|PSP do pagador atualiza o status da recorrência em seus<br>sistemas internos.|
|16|PSP do pagador|Comunicação|PSP do pagador envia mensagem PAIN.012 de<br>confirmação da recorrência.|
|17|ICOM|Mensagem|ICOM recebe mensagem PAIN.012 de confirmação da<br>recorrência.|
|18|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 de confirmação<br>da recorrência ao PSP do recebedor.|
|19|PSP do recebedor|Mensagem|PSP do recebedor recebe mensagem PAIN.012 de<br>confirmação da recorrência.|
|20|PSP do recebedor|Ação|PSP do recebedor atualiza o status da recorrência em seus<br>sistemas internos.|
|21|PSP do recebedor|Comunicação|PSP do recebedor envia ao usuário recebedor a<br>notificação de confirmação do Pix Automático como<br>forma de pagamento de cobranças recorrentes futuras.|


65  •  Manual de Fluxos do Processo de Efetivação do Pix






|22|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação<br>do Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|---|---|---|---|
|23|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|24|ICOM|Mensagem|ICOM recebe mensagem PAIN.012.|
|25|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>pagador.|
|26|PSP do pagador|Mensagem|PSP do pagador recebe mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|27|PSP do Pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>confirmando a autorização para que o pagamento de<br>cobranças recorrentes futuras seja realizado por Pix<br>Automático.|
|28|Usuário pagador|Comunicação|Usuário pagador recebe a confirmação de que a<br>autorização para o Pix Automático foi concluída com<br>sucesso. Fim do processo.|



_5.1.2.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_


_**Etapa de envio dos dados da recorrência pelo usuário recebedor ao usuário pagador:**_








|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Ação|Início do processo. Usuário recebedor gera o_QR Code_ <br>com os dados da recorrência.|
|2|Usuário recebedor|Comunicação|Usuário recebedor envia, por fora do ecossistema Pix, o<br>_QR Code_com os dados da recorrência ao usuário<br>pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe o_QR Code_para leitura no app do<br>PSP. Fim do processo.|



66  •  Manual de Fluxos do Processo de Efetivação do Pix




_**Etapa de confirmação da recorrência pelo usuário pagador:**_














|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ disponibilizado pelo usuário recebedor por fora do<br>ecossistema Pix.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ são encaminhados ao PSP.|
|3|PSP|Comunicação|PSP recebe os dados do_QR Code_.|
|4|PSP|Ação|PSP carrega os dados da recorrência.|
|5|PSP|Comunicação|PSP envia os dados da recorrência ao usuário pagador, para<br>confirmação.|
|6|Usuário Pagador|Comunicação|Usuário pagador recebe os dados da recorrência para<br>confirmação, no app do PSP.|
|7|Usuário Pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|8|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do Pix<br>Automático ao PSP.|



67  •  Manual de Fluxos do Processo de Efetivação do Pix




|9|PSP|Comunicação|PSP recebe a confirmação da autorização do Pix<br>Automático para pagamentos de cobranças recorrentes<br>futuras.|
|---|---|---|---|
|10|PSP|Ação|PSP atualiza o status da recorrência em seus sistemas<br>internos.|
|11|PSP|Comunicação|PSP envia ao usuário recebedor a notificação de<br>confirmação do Pix Automático como forma de pagamento<br>de cobranças recorrentes futuras.|
|12|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação do<br>Pix Automático como forma de pagamento de cobranças<br>recorrentes futuras.|
|13|PSP|Comunicação|PSP envia notificação ao usuário pagador, confirmando a<br>autorização para que o pagamento de cobranças<br>recorrentes futuras seja realizado por Pix Automático.|
|14|Usuário pagador|Comunicação|Usuário pagador recebe a confirmação de que a<br>autorização para o Pix Automático foi concluída com<br>sucesso. Fim do processo.|


_5.1.3._ _Jornada 3 – Usuário pagador realiza adesão por meio da leitura de QR Code com primeiro_
_pagamento imediato_


_5.1.3.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


_**Etapa de envio dos dados da recorrência pelo usuário recebedor ao usuário pagador:**_








|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Ação|Início do processo. Usuário recebedor gera o_QR Code_ com<br>os dados da cobrança imediata e da recorrência.|
|2|Usuário recebedor|Comunicação|Usuário recebedor envia, por fora do ecossistema Pix, o_QR_<br>_Code_ com os dados da cobrança imediata e da recorrência<br>ao usuário pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe o_QR Code_ para leitura no app do<br>PSP do pagador. Fim do processo.|



68  •  Manual de Fluxos do Processo de Efetivação do Pix




_**Etapa de pagamento da primeira cobrança e autorização da recorrência pelo usuário pagador:**_


69  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ disponibilizado pelo usuário recebedor por fora do<br>ecossistema Pix.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ são encaminhados ao PSP do<br>pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do_QR Code_.|
|4|PSP do pagador|Ação|PSP do pagador interpreta o_QR Code_ e identifica as<br>_locations_ contidas nele.|
|5|PSP do pagador|Comunicação|PSP do pagador envia as consultas das_locations_ ao PSP<br>do recebedor.|
|6|PSP do recebedor|Comunicação|PSP do recebedor recebe as requisições de consultas<br>enviadas pelo PSP do pagador.|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança imediata<br>e da recorrência nos_payloads_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite os_payloads_ com os dados da<br>cobrança imediata e da recorrência ao PSP do pagador.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe os_payloads_ com os dados da<br>cobrança imediata e da recorrência_._|
|10|PSP do pagador|Comunicação|PSP do pagador apresenta jornada simultânea de<br>pagamento imediato de uma cobrança e de autorização<br>de pagamento de cobranças recorrentes futuras por Pix<br>Automático.|
|11|Usuário pagador|Comunicação|Usuário pagador recebe solicitação de autorização do PSP<br>do pagador para a realização de pagamento de cobranças<br>recorrentes futuras por Pix Automático, conforme dados<br>contidos na recorrência, com aviso de que o primeiro<br>pagamento ocorrerá imediatamente após a autorização.|
|12|Usuário pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de<br>cobranças<br>recorrentes<br>futuras,<br>confirmando<br>simultaneamente o pagamento da primeira cobrança.|
|13|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do<br>Pix Automático ao PSP do pagador, juntamente com a<br>confirmação do pagamento imediato da primeira<br>cobrança.|
|14|PSP do pagador|Comunicação|PSP do pagador recebe a confirmação da autorização do<br>Pix<br>Automático<br>para<br>pagamentos<br>de<br>cobranças<br>recorrentes futuras, juntamente com a confirmação do<br>pagamento imediato da primeira cobrança.|
|15|PSP do pagador|Ação|PSP do pagador procede ao pagamento da primeira<br>cobrança, que segue o fluxo usual de efetivação de um<br>Pix, conforme descrito na seção 3 deste Manual. A<br>notificação de confirmação do pagamento ao usuário<br>pagador pode ser enviada na etapa 32, juntamente com<br>a confirmação da autorização. A ordem de pagamento é|


70  •  Manual de Fluxos do Processo de Efetivação do Pix






|Col1|Col2|Col3|imediata e deve cursar no canal primário de transmissão<br>de mensagens do SPI.|
|---|---|---|---|
|16|PSP do pagador|Decisão|PSP do pagador verifica se o pagamento da primeira<br>cobrança foi concluído com sucesso. Caso o resultado seja<br>positivo, o fluxo segue para o passo 20. Se o pagamento<br>da primeira cobrança não se concretizou, o fluxo segue<br>para o passo 17.|
|17|PSP do pagador|Ação|PSP do pagador interrompe o processo de autorização.|
|18|PSP do pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>informando que o primeiro pagamento da cobrança e a<br>autorização para que o pagamento de cobranças<br>recorrentes futuras seja realizado por Pix Automático não<br>se efetivaram.|
|19|Usuário pagador|Comunicação|Usuário pagador recebe a notificação, informando que o<br>primeiro pagamento da cobrança e a autorização para<br>que o pagamento de cobranças recorrentes futuras seja<br>realizado por Pix Automático não se efetivaram. Fim do<br>processo.|
|20|PSP do pagador|Ação|PSP do pagador atualiza o status da recorrência em seus<br>sistemas internos.|
|21|PSP do pagador|Comunicação|PSP do pagador envia mensagem PAIN.012 de<br>confirmação da recorrência.|
|22|ICOM|Mensagem|ICOM recebe mensagem PAIN.012 de confirmação da<br>recorrência.|
|23|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 de confirmação<br>da recorrência ao PSP do recebedor.|
|24|PSP do recebedor|Mensagem|PSP do recebedor recebe mensagem PAIN.012 de<br>confirmação da recorrência.|
|25|PSP do recebedor|Ação|PSP do recebedor atualiza o status da recorrência em seus<br>sistemas internos. Ressalta-se que o PSP do Recebedor<br>deve aguardar a conclusão do fluxo de liquidação do<br>primeiro<br>pagamento<br>imediato<br>antes<br>de<br>dar<br>prosseguimento a esta etapa.|
|26|PSP do recebedor|Comunicação|PSP do recebedor envia ao usuário recebedor a<br>notificação de confirmação do Pix Automático como<br>forma de pagamento de cobranças recorrentes futuras. A<br>confirmação do pagamento imediato da primeira<br>cobrança segue o fluxo descrito na seção 3 deste Manual.|
|27|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação<br>do Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras. A notificação de<br>confirmação do pagamento imediato da primeira<br>cobrança segue fluxo descrito na seção 3 deste Manual.|
|28|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|29|ICOM|Mensagem|ICOM recebe mensagem PAIN.012.|


71  •  Manual de Fluxos do Processo de Efetivação do Pix




|30|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>pagador.|
|---|---|---|---|
|31|PSP do pagador|Mensagem|PSP do pagador recebe mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|32|PSP do Pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>confirmando a autorização para que o pagamento de<br>cobranças recorrentes futuras seja realizado por Pix<br>Automático.|
|33|Usuário pagador|Comunicação|Usuário pagador recebe a notificação de confirmação de<br>pagamento (caso não tenha sido enviada no passo 15) e<br>de que a autorização para o Pix Automático foi concluída<br>com sucesso. Fim do processo.|



_5.1.3.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_


_**Etapa de envio dos dados da recorrência pelo usuário recebedor ao usuário pagador:**_








|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Ação|Início do processo. Usuário recebedor gera o_QR Code_ com<br>os dados da cobrança imediata e da recorrência.|
|2|Usuário recebedor|Comunicação|Usuário recebedor envia, por fora do ecossistema Pix, o_QR_<br>_Code_ com os dados da cobrança imediata e da recorrência<br>ao usuário pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe o_QR Code_para leitura no app do<br>PSP. Fim do processo.|



72  •  Manual de Fluxos do Processo de Efetivação do Pix




_**Etapa de pagamento da 1ª cobrança e autorização da recorrência pelo usuário pagador:**_













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ disponibilizado pelo usuário recebedor por fora do<br>ecossistema Pix.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_são encaminhados ao PSP.|
|3|PSP|Comunicação|PSP recebe os dados do_QR Code_.|
|4|PSP|Ação|PSP carrega os dados da cobrança imediata e da<br>recorrência.|
|5|PSP|Comunicação|PSP apresenta jornada simultânea de pagamento<br>imediato de uma cobrança e de autorização de<br>pagamento das cobranças recorrentes futuras por Pix<br>Automático.|
|6|Usuário pagador|Comunicação|Usuário pagador recebe solicitação de autorização do PSP<br>para a realização de pagamento de cobranças recorrentes<br>futuras por Pix Automático, conforme dados contidos na<br>recorrência, com aviso de que o primeiro pagamento<br>ocorrerá imediatamente após a autorização.|
|7|Usuário pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de|


73  •  Manual de Fluxos do Processo de Efetivação do Pix




|Col1|Col2|Col3|cobranças recorrentes futuras, confirmando<br>simultaneamente o pagamento da primeira cobrança.|
|---|---|---|---|
|8|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do<br>Pix Automático ao PSP, juntamente com a confirmação do<br>pagamento imediato da primeira cobrança.|
|9|PSP|Comunicação|PSP recebe a confirmação da autorização do Pix<br>Automático para pagamentos de cobranças recorrentes<br>futuras, juntamente com a confirmação do pagamento<br>imediato da primeira cobrança.|
|10|PSP|Ação|PSP procede ao pagamento imediato da primeira<br>cobrança, que segue o fluxo usual de efetivação de um<br>Pix, conforme descrito na seção 3.3 deste Manual. O<br>envio da notificação de confirmação do pagamento ao<br>usuário pagador pode ser feito na etapa 18, juntamente<br>com a confirmação da autorização.|
|11|PSP|Decisão|PSP verifica se o pagamento da primeira cobrança foi<br>concluído com sucesso. Caso o resultado seja positivo, o<br>fluxo segue para o passo 15. Se o pagamento da primeira<br>cobrança não se concretizou, o fluxo segue para o passo<br>12.|
|12|PSP|Ação|PSP interrompe o processo de autorização.|
|13|PSP|Comunicação|PSP envia notificação ao usuário pagador, informando<br>que o primeiro pagamento da cobrança e a autorização<br>para que o pagamento de cobranças recorrentes futuras<br>seja realizado por Pix Automático não se efetivaram.|
|14|Usuário pagador|Comunicação|Usuário pagador recebe a notificação, informando que o<br>primeiro pagamento da cobrança e a autorização para<br>que o pagamento de cobranças recorrentes futuras seja<br>realizado por Pix Automático não se efetivaram. Fim do<br>processo.|
|15|PSP|Ação|PSP atualiza o status da recorrência em seus sistemas<br>internos.|
|16|PSP|Comunicação|PSP envia ao usuário recebedor a notificação de<br>confirmação do Pix Automático como forma de<br>pagamento de cobranças recorrentes futuras. A<br>confirmação do pagamento imediato da primeira<br>cobrança segue o fluxo descrito na seção 3.3 deste<br>Manual.|
|17|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação<br>do Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras. A notificação de<br>confirmação do pagamento imediato da primeira<br>cobrança segue o fluxo descrito na seção 3.3 deste<br>Manual.|


74  •  Manual de Fluxos do Processo de Efetivação do Pix






|18|PSP|Comunicação|PSP envia notificação ao usuário pagador, confirmando a<br>autorização para que o pagamento de cobranças<br>recorrentes futuras seja realizado por Pix Automático.|
|---|---|---|---|
|19|Usuário pagador|Comunicação|Usuário pagador recebe a notificação de confirmação de<br>pagamento (caso não tenha sido enviada no passo 10) e<br>de que a autorização para o Pix Automático foi concluída<br>com sucesso. Fim do processo.|


75  •  Manual de Fluxos do Processo de Efetivação do Pix






_5.1.4._ _Jornada 4 – Usuário paga por meio de QR Code e recebe proposta de habilitação do Pix_
_Automático para pagamento de cobranças recorrentes futuras_


5.1.4.1. _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


_**Etapa de envio dos dados da recorrência pelo usuário recebedor ao usuário pagador:**_








|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Ação|Início do processo. Usuário recebedor gera o_QR Code_ com<br>os dados da cobrança e da recorrência.|
|2|Usuário recebedor|Comunicação|Usuário recebedor envia, por fora do ecossistema Pix, o_QR_<br>_Code_ com os dados da cobrança e da recorrência ao usuário<br>pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe o_QR Code_ para leitura no app do<br>PSP do pagador. Fim do processo.|



76  •  Manual de Fluxos do Processo de Efetivação do Pix




_**Etapa de pagamento da cobrança e confirmação da recorrência pelo usuário pagador:**_


77  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_ disponibilizado pelo usuário recebedor por fora do<br>ecossistema Pix.|
|2|Usuário pagador|Comunicação|Dados lidos do_QR Code_ são encaminhados ao PSP do<br>pagador.|
|3|PSP do pagador|Comunicação|PSP do pagador recebe os dados do_QR Code_.|
|4|PSP do pagador|Ação|PSP do pagador interpreta o_QR Code_6 e identifica as<br>_locations_ contidas nele.|
|5|PSP do pagador|Comunicação|PSP do pagador envia as consultas das_locations_ ao PSP do<br>recebedor.|
|6|PSP do recebedor|Comunicação|PSP do recebedor recebe as requisições de consultas<br>enviadas pelo PSP do pagador.|
|7|PSP do recebedor|Ação|PSP do recebedor carrega os dados da cobrança e da<br>recorrência nos_payloads_.|
|8|PSP do recebedor|Comunicação|PSP do recebedor transmite os_payloads_ com os dados da<br>cobrança e da recorrência ao PSP do pagador.|
|9|PSP do pagador|Comunicação|PSP do pagador recebe os_payload_s com os dados da<br>cobrança e da recorrência.|
|10|PSP do pagador|Comunicação|PSP<br>do<br>pagador<br>envia<br>solicitação<br>de<br>pagamento/agendamento<br>da<br>cobrança<br>ao<br>usuário<br>pagador.|
|11|Usuário pagador|Comunicação|Usuário<br>pagador<br>recebe<br>a <br>solicitação<br>de<br>pagamento/agendamento da cobrança por meio do app do<br>PSP do pagador.|
|12|Usuário pagador|Ação|Usuário pagador confirma o pagamento/agendamento da<br>cobrança.|
|13|Usuário pagador|Comunicação|Usuário<br>pagador<br>envia<br>confirmação<br>do<br>pagamento/agendamento da cobrança ao PSP do pagador.|
|14|PSP do pagador|Comunicação|PSP<br>do<br>pagador<br>recebe<br>a <br>confirmação<br>do<br>pagamento/agendamento da cobrança.|
|15|PSP do pagador|Decisão|Caso o usuário pagador tenha optado pela liquidação<br>imediata da cobrança, o fluxo segue para a etapa 16. Se<br>tiver escolhido agendar o pagamento da cobrança, deve-se<br>passar à etapa 17.|
|16|PSP do pagador|Ação|PSP do pagador procede ao pagamento da cobrança, que<br>segue o fluxo usual de efetivação de um Pix, conforme<br>seção 3 deste Manual.|
|17|PSP do pagador|Ação|PSP do pagador agenda o pagamento da cobrança para a<br>data escolhida pelo usuário pagador no momento da|


6 O fluxo representa o caso em que o _QR Code_ contém duas _locations_ : uma com os dados da cobrança e outra com
os dados da recorrência. Caso os dados da cobrança estejam contidos no próprio _QR Code_ (dinâmica semelhante à
do _QR Code_ estático), apenas os dados da recorrência devem ser obtidos utilizando-se a _location_ do _QR Code_ para
acessar o _payload_ fornecido pelo PSP do recebedor.


78  •  Manual de Fluxos do Processo de Efetivação do Pix




|Col1|Col2|Col3|confirmação do agendamento, que deverá seguir o fluxo<br>usual de efetivação de um Pix Agendado, conforme seção<br>3 deste Manual.|
|---|---|---|---|
|18|PSP do pagador|Comunicação|PSP do pagador envia notificação de confirmação do<br>pagamento da cobrança (ou de agendamento da cobrança)<br>e oferece o Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|19|Usuário pagador|Comunicação|Usuário pagador recebe a notificação e a oferta do Pix<br>Automático como forma de pagamento de cobranças<br>recorrentes futuras.|
|20|Usuário pagador|Ação|Usuário pagador manifesta seu interesse pelo Pix<br>Automático como forma de pagamento de cobranças<br>recorrentes futuras.|
|21|Usuário pagador|Comunicação|Usuário pagador envia a manifestação de interesse pelo Pix<br>Automático ao PSP do pagador.|
|22|PSP do pagador|Comunicação|PSP do pagador recebe a manifestação de interesse Pix<br>Automático enviada pelo usuário pagador.|
|23|PSP do pagador|Comunicação|PSP do pagador envia os dados da recorrência ao usuário<br>pagador, para confirmação.|
|24|Usuário pagador|Comunicação|Usuário pagador recebe os dados da recorrência para<br>confirmação, no app do PSP do pagador.|
|25|Usuário pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|26|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do Pix<br>Automático ao PSP do pagador.|
|27|PSP do pagador|Comunicação|PSP do pagador recebe a confirmação da autorização do Pix<br>Automático para pagamentos de cobranças recorrentes<br>futuras.|
|28|PSP do pagador|Ação|PSP do pagador atualiza o status da recorrência em seus<br>sistemas internos.|
|29|PSP do pagador|Comunicação|PSP do pagador envia mensagem PAIN.012 de confirmação<br>da recorrência.|
|30|ICOM|Mensagem|ICOM recebe mensagem PAIN.012 de confirmação da<br>recorrência.|
|31|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 de confirmação<br>da recorrência ao PSP do recebedor.|
|32|PSP do recebedor|Mensagem|PSP do recebedor recebe mensagem PAIN.012 de<br>confirmação da recorrência.|
|33|PSP do recebedor|Ação|PSP do recebedor atualiza o status da recorrência em seus<br>sistemas internos.|
|34|PSP do recebedor|Comunicação|PSP do recebedor envia ao usuário recebedor a notificação<br>de confirmação do Pix Automático como forma de<br>pagamento de cobranças recorrentes futuras.|
|35|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação do<br>Pix Automático como forma de pagamento de cobranças<br>recorrentes futuras.|


79  •  Manual de Fluxos do Processo de Efetivação do Pix






|36|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.012 em resposta<br>à mensagem PAIN.012 de confirmação da recorrência.|
|---|---|---|---|
|37|ICOM|Mensagem|ICOM recebe mensagem PAIN.012.|
|38|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>pagador.|
|39|PSP do pagador|Mensagem|PSP do pagador recebe mensagem PAIN.012 em resposta à<br>mensagem PAIN.012 de confirmação da recorrência.|
|40|PSP do Pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>confirmando a autorização para que o pagamento de<br>cobranças recorrentes futuras seja realizado por Pix<br>Automático.|
|41|Usuário pagador|Comunicação|Usuário pagador recebe a confirmação de que a<br>autorização para o Pix Automático foi concluída com<br>sucesso. Fim do processo.|



_5.1.4.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_


_**Etapa de envio dos dados da recorrência pelo usuário recebedor ao usuário pagador:**_








|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Ação|Início do processo. Usuário recebedor gera o_QR Code_ com<br>os dados da cobrança e da recorrência.|
|2|Usuário recebedor|Comunicação|Usuário recebedor envia, por fora do ecossistema Pix, o_QR_<br>_Code_ com os dados da cobrança e da recorrência ao usuário<br>pagador.|
|3|Usuário pagador|Comunicação|Usuário pagador recebe o_QR Code_ para leitura no app do<br>PSP. Fim do processo.|



80  •  Manual de Fluxos do Processo de Efetivação do Pix




_**Etapa de pagamento da cobrança e confirmação da recorrência pelo usuário pagador:**_






|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Ação|Início do processo. Usuário pagador faz a leitura do_QR_<br>_Code_7 disponibilizado pelo usuário recebedor por fora do<br>ecossistema Pix.|



7 O fluxo representa o caso em que o _QR Code_ contém duas _locations_ : uma com os dados da cobrança e outra com
os dados da recorrência. Caso os dados da cobrança estejam contidos no próprio _QR Code_ (dinâmica semelhante à
do _QR Code estático_ ), apenas os dados da recorrência devem ser obtidos utilizando-se a _location_ do _QR Code_ para
acessar os sistemas internos do PSP.


81  •  Manual de Fluxos do Processo de Efetivação do Pix




|2|Usuário pagador|Comunicação|Dados lidos do QR Code são encaminhados ao PSP.|
|---|---|---|---|
|3|PSP|Comunicação|PSP recebe os dados do_QR Code_.|
|4|PSP|Ação|PSP carrega os dados da cobrança e da recorrência.|
|5|PSP|Comunicação|PSP envia solicitação de pagamento/agendamento da<br>cobrança ao usuário pagador.|
|6|Usuário pagador|Comunicação|Usuário<br>pagador<br>recebe<br>a <br>solicitação<br>de<br>pagamento/agendamento da cobrança por meio do app do<br>PSP.|
|7|Usuário pagador|Ação|Usuário pagador confirma o pagamento/agendamento da<br>cobrança.|
|8|Usuário pagador|Comunicação|Usuário<br>pagador<br>envia<br>confirmação<br>do<br>pagamento/agendamento da cobrança ao PSP.|
|9|PSP|Comunicação|PSP recebe a confirmação do pagamento da cobrança.|
|10|PSP|Decisão|Caso o usuário pagador tenha optado pela liquidação<br>imediata da cobrança, o fluxo segue para a etapa 11. Se<br>tiver escolhido agendar o pagamento da cobrança, deve-se<br>passar à etapa 12.|
|11|PSP|Ação|PSP procede ao pagamento/agendamento da cobrança,<br>que segue o fluxo usual de efetivação de um Pix, conforme<br>seção 3.3 deste Manual.|
|12|PSP|Ação|PSP agenda o pagamento da cobrança para a data<br>escolhida pelo usuário pagador no momento da<br>confirmação do agendamento, que deverá seguir o fluxo<br>usual de efetivação de um Pix Agendado, conforme seção<br>3 deste Manual.|
|13|PSP|Comunicação|PSP envia notificação de confirmação do pagamento/<br>agendamento da cobrança e oferece o Pix Automático<br>como forma de pagamento de cobranças recorrentes<br>futuras.|
|14|Usuário pagador|Comunicação|Usuário pagador recebe a notificação de confirmação do<br>pagamento e a oferta do Pix Automático como forma de<br>pagamento de cobranças recorrentes futuras.|
|15|Usuário pagador|Ação|Usuário pagador manifesta seu interesse pelo Pix<br>Automático como forma de pagamento de cobranças<br>recorrentes futuras.|
|16|Usuário pagador|Comunicação|Usuário pagador envia a manifestação de interesse pelo Pix<br>Automático ao PSP.|
|17|PSP|Comunicação|PSP recebe a manifestação de interesse pelo Pix<br>Automático enviada pelo usuário pagador.|
|18|PSP|Comunicação|PSP envia os dados da recorrência ao usuário pagador, para<br>confirmação.|
|19|Usuário Pagador|Comunicação|Usuário pagador recebe os dados da recorrência para<br>confirmação, no app do PSP.|



82  •  Manual de Fluxos do Processo de Efetivação do Pix




|20|Usuário Pagador|Ação|Usuário pagador confere os dados da recorrência e<br>autoriza o Pix Automático como forma de pagamento de<br>cobranças recorrentes futuras.|
|---|---|---|---|
|21|Usuário pagador|Comunicação|Usuário pagador envia a confirmação da autorização do Pix<br>Automático ao PSP.|
|22|PSP|Comunicação|PSP recebe a confirmação da autorização do Pix<br>Automático para pagamentos de cobranças recorrentes<br>futuras.|
|23|PSP|Ação|PSP atualiza o status da recorrência em seus sistemas<br>internos.|
|24|PSP|Comunicação|PSP envia ao usuário recebedor a notificação de<br>confirmação do Pix Automático como forma de pagamento<br>de cobranças recorrentes futuras.|
|25|Usuário recebedor|Comunicação|Usuário recebedor recebe a notificação de confirmação do<br>Pix Automático como forma de pagamento de cobranças<br>recorrentes futuras.|
|26|PSP|Comunicação|PSP envia notificação ao usuário pagador, confirmando a<br>autorização para que o pagamento de cobranças<br>recorrentes futuras seja realizado por Pix Automático.|
|27|Usuário pagador|Comunicação|Usuário pagador recebe a confirmação de que a<br>autorização para o Pix Automático foi concluída com<br>sucesso. Fim do processo.|


83  •  Manual de Fluxos do Processo de Efetivação do Pix






_5.1.5._ _Cancelamento da autorização pelo usuário pagador_


_5.1.5.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_

|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Comunicação|Início<br>do<br>processo.<br>Usuário<br>pagador<br>solicita<br>o <br>cancelamento da autorização ao PSP do pagador.|
|2|PSP do pagador|Comunicação|PSP do pagador recebe a solicitação de cancelamento da<br>autorização do usuário pagador.|
|3|PSP do pagador|Ação|PSP do pagador cancela a autorização em seus sistemas<br>internos.|
|4|PSP do pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>confirmando o cancelamento da autorização.|



84  •  Manual de Fluxos do Processo de Efetivação do Pix




|5|Usuário pagador|Comunicação|Usuário pagador recebe notificação de confirmação do<br>cancelamento da autorização.|
|---|---|---|---|
|6|PSP do pagador|Mensagem|PSP do pagador envia mensagem PAIN.011 para informar o<br>cancelamento da recorrência associada à autorização<br>cancelada.|
|7|ICOM|Mensagem|ICOM<br>recebe mensagem<br>PAIN.011<br>informando o<br>cancelamento da recorrência.|
|8|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.011 ao PSP do<br>recebedor.|
|9|PSP do recebedor|Mensagem|PSP do recebedor recebe a mensagem PAIN.011<br>informando o cancelamento da recorrência.|
|10|PSP do recebedor|Ação|PSP do recebedor registra o cancelamento em seus<br>sistemas internos e atualiza o status da recorrência.|
|11|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.012, em resposta<br>à mensagem PAIN.011.|
|12|ICOM|Mensagem|ICOM recebe mensagem PAIN.012, em resposta à<br>mensagem PAIN.011.|
|13|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>pagador.|
|14|PSP do pagador|Mensagem|PSP do pagador recebe mensagem PAIN.012, em resposta<br>à mensagem PAIN.011.|
|15|PSP do recebedor|Comunicação|PSP do recebedor envia notificação do cancelamento da<br>recorrência ao usuário recebedor.|
|16|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação do cancelamento da<br>recorrência. Fim do processo.|


Após o cancelamento da recorrência, caso existam agendamentos pendentes a serem cancelados, o
fluxo a ser seguido a partir da etapa 3 é o fluxo de cancelamento de um débito agendado pelo usuário
pagador, descrito na seção 5.2.3 deste Manual.


85  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.1.5.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_

|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Comunicação|Início<br>do<br>processo.<br>Usuário<br>pagador<br>solicita<br>o <br>cancelamento da autorização ao PSP.|
|2|PSP|Comunicação|PSP recebe a solicitação de cancelamento da autorização<br>do usuário pagador.|
|3|PSP|Ação|PSP cancela a autorização em seus sistemas internos e<br>atualiza o status da recorrência.|
|4|PSP|Comunicação|PSP envia notificação ao usuário pagador, confirmando o<br>cancelamento da autorização.|
|5|Usuário pagador|Comunicação|Usuário pagador recebe notificação de confirmação do<br>cancelamento da autorização.|
|6|PSP|Comunicação|PSP envia notificação do cancelamento da recorrência ao<br>usuário recebedor.|
|7|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação do cancelamento da<br>recorrência. Fim do processo.|



Após o cancelamento da recorrência, caso existam agendamentos pendentes a serem cancelados, o
fluxo a ser seguido a partir da etapa 3 é o fluxo de cancelamento de um débito agendado pelo usuário
pagador, descrito na seção 5.2.3 deste Manual.


86  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.1.6._ _Cancelamento da recorrência pelo usuário recebedor_


_5.1.6.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


87  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor solicita o<br>cancelamento da recorrência ao PSP do recebedor.|
|2|PSP do recebedor|Comunicação|PSP do recebedor recebe a solicitação de cancelamento da<br>recorrência do usuário recebedor.|
|3|PSP do recebedor|Ação|PSP do recebedor cancela a recorrência em seus sistemas<br>internos.|
|4|PSP do recebedor|Comunicação|PSP do recebedor envia notificação ao usuário recebedor,<br>confirmando o cancelamento da recorrência.|
|5|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação de confirmação do<br>cancelamento da recorrência.|
|6|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.011 para informar<br>o cancelamento da recorrência.|
|7|ICOM|Mensagem|ICOM<br>recebe<br>mensagem PAIN.011<br>informando o<br>cancelamento da recorrência.|
|8|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.011 ao PSP do<br>pagador.|
|9|PSP do pagador|Mensagem|PSP do pagador recebe a mensagem PAIN.011 informando<br>o cancelamento da recorrência.|
|10|PSP do pagador|Ação|PSP do pagador registra o cancelamento em seus sistemas<br>internos e atualiza o status da recorrência.|
|11|PSP do pagador|Mensagem|PSP do pagador envia mensagem PAIN.012, em resposta à<br>mensagem PAIN.011.|
|12|ICOM|Mensagem|ICOM recebe mensagem PAIN.012, em resposta à<br>mensagem PAIN.011.|
|13|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.012 ao PSP do<br>recebedor.|
|14|PSP do pagador|Mensagem|PSP do recebedor recebe mensagem PAIN.012, em<br>resposta à mensagem PAIN.011.|
|15|PSP do pagador|Comunicação|PSP do pagador envia notificação do cancelamento da<br>autorização associada à recorrência cancelada ao usuário<br>pagador.|
|16|Usuário pagador|Comunicação|Usuário pagador recebe notificação do cancelamento da<br>autorização associada à recorrência cancelada. Fim do<br>processo.|


Este fluxo também deve ser utilizado na eventualidade do usuário recebedor e/ou do PSP recebedor
identificarem a necessidade de cancelar uma solicitação de recorrência enviada por meio da Jornada 1
e que ainda esteja pendente de resposta pelo usuário pagador, como por exemplo, no caso da solicitação
de recorrência já ter sido aceita paralelamente pelo usuário pagador por meio de outra jornada.

Após o cancelamento da recorrência, caso existam agendamentos pendentes a serem cancelados, o
fluxo a ser seguido a partir da etapa 3 é o fluxo de cancelamento de um débito agendado pelo usuário
pagador, descrito na seção 5.2.3 deste Manual.


88  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.1.6.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_

|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor solicita o<br>cancelamento da recorrência ao PSP.|
|2|PSP|Comunicação|PSP recebe a solicitação de cancelamento da recorrência<br>do usuário recebedor.|
|3|PSP|Ação|PSP atualiza o status da recorrência e cancela a respectiva<br>autorização em seus sistemas internos.|
|4|PSP|Comunicação|PSP envia notificação ao usuário recebedor, confirmando o<br>cancelamento da recorrência.|
|5|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação de confirmação do<br>cancelamento da recorrência.|
|6|PSP|Comunicação|PSP envia notificação do cancelamento da autorização<br>associada à recorrência cancelada ao usuário pagador.|
|7|Usuário pagador|Comunicação|Usuário pagador recebe notificação do cancelamento da<br>autorização associada à recorrência cancelada. Fim do<br>processo.|



Após o cancelamento da recorrência, caso existam agendamentos pendentes a serem cancelados, o
fluxo a ser seguido a partir da etapa 3 é o fluxo de cancelamento de um débito agendado pelo usuário
pagador, descrito na seção 5.2.3 deste Manual.


89  •  Manual de Fluxos do Processo de Efetivação do Pix




#### **5.2. Fluxos de agendamento do débito**

_5.2.1._ _Agendamento do débito_

_5.2.1.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


90  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor envia os dados da<br>cobrança ao PSP do recebedor.|
|2|PSP do recebedor|Comunicação|PSP do recebedor recebe os dados da cobrança enviados<br>pelo usuário recebedor.|
|3|PSP do recebedor|Ação|PSP do recebedor valida os dados da cobrança com as<br>informações da recorrência armazenada em seus sistemas<br>internos.|
|4|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem PAIN.013 contendo os<br>dados da cobrança.|
|5|ICOM|Mensagem|ICOM recebe mensagem PAIN.013 com os dados da<br>cobrança.|
|6|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.013 ao PSP do<br>pagador.|
|7|PSP do pagador|Mensagem|PSP do pagador recebe a mensagem PAIN.013 com os<br>dados da cobrança.|
|8|PSP do pagador|Ação|PSP do pagador compara os dados da cobrança com as<br>informações da autorização concedida e agenda a ordem<br>de pagamento para a data prevista.|
|9|PSP do pagador|Mensagem|PSP do pagador envia mensagem PAIN.014, em resposta à<br>mensagem PAIN.013.|
|10|ICOM|Mensagem|ICOM recebe mensagem PAIN.014, em resposta à<br>mensagem PAIN.013.|
|11|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.014 ao PSP do<br>recebedor.|
|12|PSP do recebedor|Mensagem|PSP do recebedor recebe a mensagem PAIN.014, em<br>resposta à mensagem PAIN.013.|
|13|PSP do recebedor|Ação|PSP do recebedor armazena as informações do<br>agendamento em seus sistemas internos.|
|14|PSP do recebedor|Comunicação|PSP do recebedor notifica o usuário recebedor de que o<br>agendamento foi realizado com sucesso.|
|15|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação sobre o sucesso do<br>agendamento.|
|16|PSP do pagador|Comunicação|PSP do pagador envia notificação do agendamento do<br>débito ao usuário pagador8.|
|17|Usuário pagador|Comunicação|Usuário pagador recebe notificação do agendamento do<br>débito. Fim do processo.|


8 O usuário pagador pode, a qualquer momento, desabilitar a opção de notificação do agendamento, conforme
previsto no manual de Requisitos Mínimos para a Experiência do Usuário. Nesse caso, as etapas 16 e 17 do fluxo
não devem ser efetivadas.


91  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.2.1.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_
















|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor envia os dados da<br>cobrança ao PSP.|
|2|PSP|Comunicação|PSP recebe os dados da cobrança enviados pelo usuário<br>recebedor.|
|3|PSP|Ação|PSP compara os dados da cobrança com as informações da<br>autorização concedida e agenda a ordem de pagamento<br>para a data prevista.|
|4|PSP|Comunicação|PSP notifica o usuário recebedor de que o agendamento foi<br>realizado com sucesso.|
|5|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação sobre o sucesso do<br>agendamento.|
|6|PSP|Comunicação|PSP envia notificação do agendamento do débito ao<br>usuário pagador9.|
|7|Usuário pagador|Comunicação|Usuário pagador recebe notificação do agendamento do<br>débito. Fim do processo.|



9 O usuário pagador pode, a qualquer momento, desabilitar a opção de notificação do agendamento, conforme
previsto no manual de Requisitos Mínimos para a Experiência do Usuário. Nesse caso, as etapas 6 e 7 do fluxo não
devem ser efetivadas.


92  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.2.2._ _Novas tentativas intradia por erro no fluxo de liquidação_


_5.2.2.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_













|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP do pagador|Ação|Início do processo. PSP do pagador constata que a<br>liquidação da ordem de pagamento não ocorreu por erro<br>no fluxo de liquidação.|
|2|PSP do pagador|Ação|PSP do pagador registra que a ordem de pagamento não foi<br>liquidada em seus sistemas internos.|
|3|PSP do pagador|Mensagem|PSP do pagador envia mensagem CAMT.055 de<br>cancelamento da instrução de pagamento, cuja liquidação<br>da ordem de pagamento não ocorreu.|
|4|ICOM|Mensagem|ICOM recebe mensagem CAMT.055 de cancelamento da<br>instrução de pagamento.|


93  •  Manual de Fluxos do Processo de Efetivação do Pix




|5|ICOM|Mensagem|ICOM retransmite a mensagem CAMT.055 de<br>cancelamento da instrução de pagamento.|
|---|---|---|---|
|6|PSP do recebedor|Mensagem|PSP do recebedor recebe a CAMT.055 de cancelamento da<br>instrução de pagamento.|
|7|PSP do recebedor|Ação|PSP do recebedor registra o cancelamento da instrução de<br>pagamento em seus sistemas internos.|
|8|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem CAMT.029, em<br>resposta à mensagem CAMT.055.|
|9|ICOM|Mensagem|ICOM recebe mensagem CAMT.029, em resposta à<br>mensagem CAMT.055.|
|10|ICOM|Mensagem|ICOM retransmite a mensagem CAMT.029 ao PSP do<br>pagador.|
|11|PSP do pagador|Mensagem|PSP do pagador recebe a mensagem CAMT.029, em<br>resposta à mensagem CAMT.055.|
|12|PSP do pagador|Ação|PSP do pagador armazena o cancelamento da instrução de<br>pagamento em seus sistemas internos.|
|13|PSP do recebedor|Ação|PSP do recebedor valida novamente os dados da cobrança<br>com as informações da recorrência armazenada em seus<br>sistemas internos.|
|14|PSP do recebedor|Comunicação|PSP do recebedor envia mensagem PAIN.013 contendo os<br>dados da cobrança.|
|15|ICOM|Comunicação|PSP do recebedor envia mensagem PAIN.013 contendo os<br>dados da cobrança.|
|16|ICOM|Comunicação|ICOM retransmite a mensagem PAIN.013 ao PSP do<br>pagador.|
|17|PSP do pagador|Comunicação|PSP do pagador recebe a mensagem PAIN.013 com os<br>dados da cobrança.|
|18|PSP do pagador|Ação|PSP do pagador compara os dados da cobrança com as<br>informações da autorização concedida e agenda nova<br>ordem de pagamento para o mesmo dia.|
|19|PSP do pagador|Mensagem|PSP do pagador envia mensagem PAIN.014, em resposta à<br>mensagem PAIN.013.|
|20|ICOM|Mensagem|ICOM recebe mensagem PAIN.014, em resposta à<br>mensagem PAIN.013.|
|21|ICOM|Mensagem|ICOM retransmite a mensagem PAIN.014 ao PSP do<br>recebedor.|
|22|PSP do recebedor|Mensagem|PSP do recebedor recebe a mensagem PAIN.014, em<br>resposta à mensagem PAIN.013.|
|23|PSP do recebedor|Ação|PSP do recebedor armazena as informações do<br>agendamento em seus sistemas internos. Fim do processo.|


Quando uma transação originada de uma instrução de pagamento previamente enviada não é liquidada
(ex.: por indisponibilidade do SPI, ou do PSP do recebedor, ou mesmo por rejeição da PACS.008 pelo SPI
ou pelo PSP do recebedor), o E2EId daquela mensagem não pode ser utilizado novamente. Assim,
primeiramente é necessário que o PSP do pagador cancele a mensagem PAIN.013 original conforme
descrito no item 5.2.3 desde Manual (neste caso, não se aplicam as etapas de notificação ao usuário
pagador), ou seja, por meio do envio de uma mensagem CAMT.055 ao PSP do recebedor, que, ao recebê

94  •  Manual de Fluxos do Processo de Efetivação do Pix




la, deve confirmar o cancelamento do agendamento com o envio de uma mensagem CAMT.029 ao PSP
do pagador. Em seguida, o PSP do recebedor deve enviar nova PAIN.013 para o PSP do pagador, com os
dados da cobrança, a fim de que o PSP do pagador possa gerar nova PACS.008 com o novo E2EID, a ser
liquidada na mesma data.

Para o processo de novas tentativas após o vencimento (neste caso, por insuficiência de saldo na data
prevista para liquidação da cobrança, por exemplo), o PSP do recebedor que não identificar a liquidação
do agendamento na data prevista encaminha nova PAIN.013 ao PSP do pagador, para que realize novo
agendamento e possa efetuar o pagamento.


_5.2.2.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_









|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|PSP|Ação|Início do processo. PSP do pagador constata que a<br>liquidação da ordem de pagamento não ocorreu por erro<br>no fluxo de liquidação.|
|2|PSP|Ação|PSP do pagador registra que a ordem de pagamento não foi<br>liquidada em seus sistemas internos.|
|3|PSP|Ação|PSP do pagador compara os dados da cobrança com as<br>informações da autorização concedida e agenda nova<br>ordem de pagamento para o mesmo dia. Fim do processo.|


95  •  Manual de Fluxos do Processo de Efetivação do Pix






_5.2.3._ _Cancelamento pelo usuário pagador de um débito agendado_


_5.2.3.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


96  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Comunicação|Início do processo. Usuário pagador solicita<br>o <br>cancelamento do débito agendado ao PSP do pagador.|
|2|PSP do pagador|Comunicação|PSP do pagador recebe a solicitação de cancelamento do<br>débito agendado.|
|3|PSP do pagador|Ação|PSP do pagador cancela o débito agendado em seus<br>sistemas internos.|
|4|PSP do pagador|Comunicação|PSP do pagador envia notificação ao usuário pagador,<br>confirmando o cancelamento do débito agendado.|
|5|Usuário pagador|Comunicação|Usuário pagador recebe notificação de confirmação do<br>cancelamento do débito agendado.|
|6|PSP do pagador|Mensagem|PSP do pagador envia mensagem CAMT.055 para<br>informar o cancelamento do débito agendado.|
|7|ICOM|Mensagem|ICOM recebe mensagem CAMT.055 informando o<br>cancelamento do débito agendado.|
|8|ICOM|Mensagem|ICOM retransmite a mensagem CAMT.055 ao PSP do<br>recebedor.|
|9|PSP do recebedor|Mensagem|PSP do recebedor recebe a mensagem CAMT.055<br>informando o cancelamento do débito agendado.|
|10|PSP do recebedor|Ação|PSP do recebedor registra o cancelamento do<br>agendamento do débito em seus sistemas internos.|
|11|PSP do recebedor|Mensagem|PSP do recebedor envia mensagem CAMT.029, em<br>resposta à mensagem CAMT.055.|
|12|ICOM|Mensagem|ICOM recebe mensagem CAMT.029, em resposta à<br>mensagem CAMT.055.|
|13|ICOM|Mensagem|ICOM retransmite a mensagem CAMT.029 ao PSP do<br>pagador.|
|14|PSP do pagador|Mensagem|PSP do pagador recebe a mensagem CAMT.029, em<br>resposta à mensagem CAMT.055.|
|15|PSP do recebedor|Comunicação|PSP do recebedor comunica o cancelamento do débito<br>agendado ao usuário recebedor.|
|16|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação do cancelamento<br>do débito agendado. Fim do processo.|


97  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.2.3.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_

|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário pagador|Comunicação|Início<br>do<br>processo.<br>Usuário<br>pagador<br>solicita<br>o <br>cancelamento do débito agendado ao PSP.|
|2|PSP|Comunicação|PSP recebe a solicitação de cancelamento do débito<br>agendado.|
|3|PSP|Ação|PSP cancela o débito agendado em seus sistemas internos.|
|4|PSP|Comunicação|PSP envia notificação ao usuário pagador, confirmando o<br>cancelamento do débito agendado.|
|5|Usuário pagador|Comunicação|Usuário pagador recebe notificação de confirmação do<br>cancelamento do débito agendado.|
|6|PSP|Comunicação|PSP comunica o cancelamento do débito agendado ao<br>usuário recebedor.|
|7|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação do cancelamento do<br>débito agendado. Fim do processo.|



98  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.2.4._ _Cancelamento pelo usuário recebedor de um débito agendado_


_5.2.4.1._ _Quando o PSP do pagador e o PSP do recebedor são instituições diferentes_


99  •  Manual de Fluxos do Processo de Efetivação do Pix




|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor solicita o<br>cancelamento da cobrança ao PSP do recebedor.|
|2|PSP do recebedor|Comunicação|PSP do recebedor recebe a solicitação de cancelamento da<br>cobrança.|
|3|PSP do recebedor|Ação|Se os dados da cobrança para agendamento ainda não<br>tiverem sido enviados ao PSP do pagador, segue para o<br>passo 4. Se já tiverem sido enviados, passa para o passo 7.|
|4|PSP do recebedor|Ação|PSP do recebedor cancela a cobrança em seus sistemas<br>internos.|
|5|PSP do recebedor|Comunicação|PSP do recebedor envia notificação ao usuário recebedor,<br>confirmando o cancelamento da cobrança.|
|6|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação de confirmação do<br>cancelamento da cobrança. Fim do processo.|
|7|PSP do recebedor|Mensagem|Se os dados da cobrança já tiverem sido enviados, PSP do<br>recebedor envia mensagem CAMT.055 para informar o<br>cancelamento da cobrança.|
|8|ICOM|Mensagem|ICOM recebe mensagem CAMT.055 informando o<br>cancelamento da cobrança.|
|9|ICOM|Mensagem|ICOM retransmite a mensagem CAMT.055 ao PSP do<br>pagador.|
|10|PSP do pagador|Mensagem|PSP do pagador recebe a mensagem CAMT.055<br>informando o cancelamento da cobrança.|
|11|PSP do pagador|Ação|PSP do pagador cancela o agendamento do débito<br>referente à cobrança cancelada em seus sistemas internos.|
|12|PSP do pagador|Comunicação|PSP do pagador comunica o cancelamento do débito<br>agendado ao usuário pagador.|
|13|Usuário pagador|Comunicação|Usuário pagador recebe notificação do cancelamento do<br>débito agendado. Fim do processo.|
|14|PSP do pagador|Mensagem|PSP do pagador envia mensagem CAMT.029, em resposta<br>à mensagem CAMT.055.|
|15|ICOM|Mensagem|ICOM recebe mensagem CAMT.029, em resposta à<br>mensagem CAMT.055.|
|16|ICOM|Mensagem|ICOM retransmite a mensagem CAMT.029 ao PSP do<br>recebedor.|
|17|PSP do recebedor|Mensagem|PSP do recebedor recebe a mensagem CAMT.029, em<br>resposta<br>à <br>mensagem<br>CAMT.055,<br>confirmando o<br>cancelamento do agendamento do débito referente à<br>cobrança cancelada.|
|18|PSP do recebedor|Ação|PSP do recebedor cancela a cobrança em seus sistemas<br>internos.|
|19|PSP do recebedor|Comunicação|PSP do recebedor envia notificação ao usuário recebedor,<br>confirmando o cancelamento da cobrança.|
|20|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação de confirmação do<br>cancelamento da cobrança. Fim do processo.|


100  •  Manual de Fluxos do Processo de Efetivação do Pix




_5.2.4.2._ _Quando o PSP do pagador e o PSP do recebedor são a mesma instituição_

|#|Camada|Tipo|Descrição|
|---|---|---|---|
|1|Usuário recebedor|Comunicação|Início do processo. Usuário recebedor solicita o<br>cancelamento da cobrança ao PSP.|
|2|PSP|Comunicação|PSP recebe a solicitação de cancelamento da cobrança.|
|3|PSP|Ação|PSP cancela a cobrança e o respectivo débito agendado em<br>seus sistemas internos.|
|4|PSP|Comunicação|PSP envia notificação ao usuário recebedor, confirmando o<br>cancelamento da cobrança.|
|5|Usuário recebedor|Comunicação|Usuário recebedor recebe notificação de confirmação do<br>cancelamento da cobrança.|
|6|PSP|Comunicação|PSP comunica o cancelamento do débito agendado ao<br>usuário pagador.|
|7|Usuário pagador|Comunicação|Usuário pagador recebe notificação do cancelamento do<br>débito agendado. Fim do processo.|



101  •  Manual de Fluxos do Processo de Efetivação do Pix




### **Histórico de revisão**

|Data|Versão|Descrição das alterações|
|---|---|---|
|11/8/2020|1.0|Versão inicial.|
|10/9/2020|1.1|Ajuste no fluxo 2.3, sobre a geração da ordem de pagamento por QR<br>Code dinâmico. Fluxo é exatamente igual ao fluxo de geração da ordem<br>de pagamento por QR Code estático. Após o usuário pagador ler o QR<br>Code dinâmico, PSP do pagador envia a chave contida no_payload_ do<br>QR para o DICT. Após retorno do DICT, PSP do pagador apresenta as<br>informações do_payload_ e as informações do usuário recebedor para o<br>usuário pagador, solicitando confirmação do pagamento.|
|22/7/2021|1.2|Estrutura: inserção da subseção 2.1.3 “Prestador de serviço de iniciação<br>de transação de pagamento, com acesso direto ao DICT”.<br> <br>Estrutura: inserção da subseção 2.4 “Geração da ordem de pagamento<br>pelo serviço de iniciação de transação de pagamento, nos casos em que<br>o participante possui todas as informações do usuário recebedor”.<br> <br>Seção 2.3: detalhamento da tabela de passo a passo, para explicitar<br>melhor o processo de geração da ordem por QR Code dinâmico.|
|29/9/2021|1.3|Ajuste no fluxo 2.2 “Geração da ordem de pagamento por QR Code<br>estático” e na tabela. <br> <br>Estrutura: inserção da subseção 2.3.1 “Pix Cobrança para pagamento<br>imediato”. <br> <br>Estrutura: inserção da subseção 2.3.2 “Pix Cobrança para pagamento<br>com vencimento”. <br> <br>Estrutura: inserção da seção 2.4 “Geração da ordem de pagamento de<br>um Pix Agendado por inserção manual de dados ou por meio de chave<br>Pix”. <br> <br>Estrutura: ajustes de numeração na subseção subsequente 2.5.<br>“Geração da ordem de pagamento pelo serviço de iniciação de<br>transação de pagamento, nos casos em que o participante possui todas<br>as informações do usuário recebedor.”|
|29/10/2023|1.4|Seção 3.1: ajuste no texto explicativo e no fluxo para definição das<br>ordens de pagamento que devem ser enviadas para o canal primário<br>de transmissão de mensagens do SPI e para o canal secundário de<br>transmissão de mensagens do SPI.<br> <br>Seção 3.2: ajuste no texto explicativo e no fluxo para definição das<br>ordens de pagamento que devem ser enviadas para o canal primário<br>de transmissão de mensagens do SPI e para o canal secundário de<br>transmissão de mensagens do SPI.<br>|



102  •  Manual de Fluxos do Processo de Efetivação do Pix




|Col1|Col2|Seção 3.3: ajuste no texto explicativo e no fluxo em razão da criação do<br>canal secundário de transmissão de mensagens do SPI.<br>Seção 3.4: ajuste no texto explicativo e no fluxo em razão da criação do<br>canal secundário de transmissão de mensagens do SPI.|
|---|---|---|
|30/08/2024|2.0|Seção 3: inclusão de fluxos com liquidação agendada da ordem de<br>pagamento (Pix Agendado e Pix Agendado recorrente e Pix Cobrança<br>com vencimento).<br> <br>Estrutura: inserção da seção 5 – Fluxos do Pix Automático.<br> <br>Estrutura: revisão geral dos fluxos e textos explicativos.|
|05/06/2025|2.1|Estrutura: inserção da subseção 2.6 “Geração da ordem de pagamento<br>por aproximação (NFC)”.<br> <br>Seção 3.1: ajuste no texto explicativo para inclusão do Pix Automático<br>entre as ordens de pagamento que devem ser enviadas para o canal<br>secundário de transmissão de mensagens do SPI.<br> <br>Seção 5: ajuste no texto explicativo para indicação dos fluxos do Pix<br>Automático que ocorrem no canal primário de transmissão de<br>mensagens do SPI e no canal secundário de transmissão de mensagens<br>do SPI.<br> <br>Seção 5.1.3.1: ajuste no texto explicativo para ressaltar que o PSP do<br>Recebedor deve aguardar a conclusão do fluxo de liquidação do<br>primeiro pagamento imediato antes de dar prosseguimento a etapa de <br>atualização do status da recorrência.<br> <br>Seção 5.1.5.1: ajuste no texto explicativo para pontuar que após o<br>cancelamento da recorrência, caso existam agendamentos pendentes<br>a serem cancelados, a responsabilidade pelo seu cancelamento é do<br>PSP do usuário pagador.<br> <br>Seção 5.1.5.2: ajuste no texto explicativo para pontuar que após o<br>cancelamento da recorrência, caso existam agendamentos pendentes<br>a serem cancelados, a responsabilidade pelo seu cancelamento é do<br>PSP do usuário pagador.|


103  •  Manual de Fluxos do Processo de Efetivação do Pix


