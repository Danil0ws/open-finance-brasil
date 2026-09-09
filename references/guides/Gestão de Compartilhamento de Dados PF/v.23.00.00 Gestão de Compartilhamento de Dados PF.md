# v.23.00.00 Gestão de Compartilhamento de Dados PF

A seção **Meus Compartilhamentos**, disponível no ambiente Open Finance das Instituições Receptoras e Transmissoras de Dados, permite consultar os dados recebidos e enviados, além dos detalhes e status dos compartilhamentos (ativos, cancelados ou expirados).

Nesse ambiente, também é possível realizar a gestão dos compartilhamentos, com opções para revogar, alterar ou renovar o compartilhamento de dados, conforme as diretrizes específicas de cada ação.

As **Instituições Receptoras de Dados** devem disponibilizar a ação de **revogação** do consentimento. Também podem disponibilizar, de forma opcional, as ações de **alteração e renovação** (padrão ou simplificada). Apesar de opcionais, quando implementadas, essas ações devem seguir os requisitos definidos neste Guia de UX.

As **Instituições Transmissoras de Dados** devem disponibilizar **apenas a ação de revogação** do consentimento. As ações de alteração e renovação devem ser realizadas exclusivamente nas Instituições Receptoras.

![image-20260727-185835.png](images/image-20260727-185835.png)

* * *

#F4F5F7

## Requisitos - IR

**Cenário: Acesso ao Open Finance**

`REQ.DC-00100` Disponibilizar o ambiente Open Finance nos seus canais, incluindo-o no primeiro nível do menu principal, para garantir acesso rápido e fácil ao usuário.

![image-20260727-185945.png](images/image-20260727-185945.png)

**Cenário: Histórico de consentimentos - Geral**

`REQ.DC-00200` Disponibilizar, no ambiente Open Finance, uma seção dedicada à exibição do histórico completo de compartilhamentos.

`REQ.DC-00300` Diferenciar claramente os consentimentos transmitidos e recebidos para fins de consulta.

`REQ.DC-00400` Diferenciar claramente os consentimentos conforme o status: ativos, pendentes e inativos (revogados ou expirados).

`REQ.DC-00500` Disponibilizar acesso aos detalhes de cada consentimento no histórico.

`REQ.DC-00600` Nos detalhes do consentimento, exibir a validade do consentimento com o prazo ou data final. No caso de prazo indeterminado, identificar para o usuário como “Indeterminado” ou termo similar.

`REQ.DC-00700` Nos detalhes do consentimento, exibir o escopo dos dados compartilhados, como dados cadastrais, contas, cartões de crédito, investimentos e operações de crédito etc.

`REQ.DC-00800` Nos detalhes do consentimento, exibir a finalidade do compartilhamento.

`REQ.DC-00900` Quando o consentimento tiver sido renovado por meio da jornada de renovação simplificada, nos detalhes do consentimento, exibir o histórico completo de prazos anteriores.

`REQ.DC-00950` No histórico de compartilhamento de dados, quando a solicitação estiver pendente, informar de forma explícita que há uma ação necessária do usuário indicando a instituição onde a ação deve ser realizada.

-   Ex.: Aguardando confirmação na Bratech.
    

`REQ.DC-00960` No histórico de compartilhamento de dados, exibir o nome da instituição que está transmitindo o compartilhamento.

`REQ.DC-00970` No histórico de compartilhamento de dados, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação da solicitação do compartilhamento de dados pendente, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

-   Ex.: Confirmar até: 12/12/2026 às 09:11.
    

`REQ.DC-00980` Nos detalhes do compartilhamento de dados, exibir o nome da instituição que está transmitindo o compartilhamento.

![image-20260727-191011.png](images/image-20260727-191011.png)

**Cenário: Cancelamento de consentimento pendente - Geral**

`REQ.DC-00990` Nos detalhes do compartilhamento de dados, permitir que o usuário cancele a solicitação pendente.

`REQ.DC-00995` Ao confirmar o cancelamento de uma solicitação pendente, exibir mensagem de sucesso informando que a solicitação foi cancelada.

Ex.: Solicitação cancelada com sucesso.​

**Cenário: Detalhes do consentimento - CIBA PF**

`REQ.DC-00996` Nos detalhes do compartilhamento de dados, quando a solicitação estiver pendente, orientar o usuário a acessar o ambiente Open Finance da IT para confirmar a solicitação.

`REQ.DC-00997` Nos detalhes do compartilhamento de dados, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação da solicitação de compartilhamento de dados pendente, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

`REQ.DC-00998` Nos detalhes do compartilhamento de dados, quando o prazo para confirmação expirar, informar claramente que a solicitação foi encerrada e orientar o usuário sobre como iniciar uma nova solicitação.

-   Ex.:O prazo para confirmação foi encerrado. Solicite um novo compartilhamento para continuar.​
    

![image-20260727-191750.png](images/image-20260727-191750.png)

**Cenário: Revogação do consentimento - Geral**

`REQ.DC-01000` No histórico e nos detalhes dos consentimentos, disponibilizar ao usuário a opção de revogar qualquer consentimento ativo, seja transmitido ou recebido.

`REQ.DC-01100` Antes da efetivação da revogação, exibir uma tela de confirmação, informando de forma clara as consequências da ação.

`REQ.DC-01200` Garantir que a revogação do consentimento contemple todos os dados objeto do compartilhamento.

**Nota**

Fica a cargo das Instituições Receptoras de Dados tratar e/ou excluir os dados de acordo com a legislação vigente, incluindo a LGPD.

`REQ.DC-01300` Respeitar, no processo de revogação, as regras de poderes já estabelecidas nas instituições.

`REQ.DC-01400` Após a revogação, manter o consentimento e seus detalhes acessíveis no histórico, com status e informações devidamente atualizados.

`REQ.DC-01500` Notificar a outra instituição quando o usuário realizar a revogação do consentimento.

![image-20260826-140754.png](images/image-20260826-140754.png)

**Cenário: Alteração do consentimento - Geral**

> A **alteração do consentimento** é uma experiência facilitada para criação de um novo consentimento com base nos dados de um consentimento prévio. Alterar um consentimento ativo implica revogar o consentimento existente para criar um novo em seu lugar.

**Atenção**

A jornada de alteração do consentimento é opcional para as receptoras. No entanto, uma vez que ofereça essa jornada, a IR deve seguir os requisitos abaixo.

`REQ.DC-01900` Se oferecer a jornada de alteração disponibilizá-la apenas para consentimentos ativos.

`REQ.DC-01600` Se oferecer a jornada de alteração, informar claramente ao usuário que será necessária uma nova confirmação na Instituição Transmissora de Dados, conforme protocolo escolhido pela Instituição Receptora de Dados.

`REQ.DC-01700` Aplicar à jornada de alteração os mesmos requisitos de todas as etapas da jornada de criação de consentimento, excetuando-se as limitações de configuração dos parâmetros inerentes a esses tipos de jornada. Dessa forma, não é necessário apresentar possibilidade de seleção da Instituição Transmissora de Dados nessas jornadas.

`REQ.DC-02000` Se oferecer a jornada de alteração, durante a jornada, apresentar, além das informações do consentimento previstas nos requisitos do Ambiente de Gestão de Consentimentos, ao menos um dos elementos a seguir para caracterizar a jornada como alteração, e não como renovação:

-   Possibilidade de alteração dos dados (inclusão ou exclusão).
    
-   Possibilidade de redução do prazo.
    
-   Possibilidade de alteração da finalidade, para casos em que a Instituição Receptora de Dados tiver mais de uma opção vigente.
    

`REQ.DC-02100` Se oferecer jornada de alteração, quando houver apenas uma finalidade do consentimento, exibi-la explicitamente ao usuário, mesmo que a finalidade utilizada no consentimento anterior não esteja mais vigente na Instituição Receptora de Dados.

`REQ.DC-02200` Após a efetivação da jornada, manter acessíveis no histórico os detalhes do consentimento revogado (pré-alteração) e do novo consentimento (pós-alteração), com status e informações devidamente atualizados.

**Cenário: Renovação padrão do consentimento - Geral**

> A **renovação padrão do consentimento** é uma experiência facilitada para criação de um novo consentimento com base nos dados de um consentimento prévio. Caso o consentimento prévio esteja ativo, renová-lo implica revogar o consentimento existente para criar um novo em seu lugar.

**Atenção**

A jornada de renovação padrão do consentimento é opcional para as receptoras. No entanto, uma vez que ofereça essa jornada, a IR deve seguir os requisitos abaixo.

`REQ.DC-01800` Aplicar à jornada de renovação os mesmos requisitos de todas as etapas da jornada de criação de consentimento, excetuando-se as limitações de configuração dos parâmetros inerentes a esses tipos de jornada. Dessa forma, não é necessário apresentar possibilidade de seleção da Instituição Transmissora de Dados nessas jornadas.

`REQ.DC-01650` Se oferecer jornada de renovação padrão, informar claramente ao usuário que será necessária uma nova confirmação na instituição Transmissora de Dados, conforme protocolo escolhido pela Instituição Receptora de Dados.

`REQ.DC-02300` Não permitir a alteração do escopo de dados compartilhados ou a alteração da Instituição Transmissora de Dados.

`REQ.DC-02400` Permitir a alteração da finalidade apenas nos casos em que houver necessidade de atualização por parte da Instituição Receptora de Dados.

`REQ.DC-02500` Calcular a nova data de validade do consentimento a partir da data em que ocorrer a renovação, permitindo ao usuário modificá-la apenas para uma data posterior à data de expiração vigente.

-   Ex.: Caso um consentimento tenha vigência de 01/01/2023 a 01/01/2024 (prazo de 12 meses), em qualquer opção de prazo apresentada ao usuário e independentemente do momento da renovação, a data final do consentimento renovado deve ser sempre posterior à data final do consentimento original.
    

`REQ.DC-02600` Após a efetivação da jornada, manter acessíveis no histórico os detalhes do consentimento revogado (pré-renovação) e do novo consentimento (pós-renovação), com status e informações devidamente atualizados.

![image-20260622-035642.png](images/image-20260622-035642.png)

**Nota**

As jornadas de alteração e de renovação padrão são uma forma de otimizar etapas, criando um consentimento com base em informações de outro já existente. São ações tecnicamente idênticas, logo cabe à interface da Instituição Receptora de Dados desenhar cada jornada com a narrativa condizente com as opções de edição oferecidas, como permitir apenas incrementos de prazo em jornadas apresentadas como renovação ou permitir inclusão de mais escopo em jornadas apresentadas como alteração.

**Cenário: Renovação simplificada do consentimento - Geral**

> A **renovação simplificada** é uma ação complementar similar à renovação padrão, porém restrita a consentimentos ativos, já que trata da atualização do prazo, sem a substituição do consentimento atual por um novo. É dita simplificada pois dispensa a necessidade de redirecionamento e confirmação na Instituição Transmissora de Dados.

**Aviso**

A jornada de renovação simplificada do consentimento é opcional para as receptoras. No entanto, uma vez que ofereça essa jornada, a IR deve seguir os requisitos abaixo.

`REQ.DC-02700` Se oferecer a renovação simplificada, disponibilizá-la apenas para os consentimentos ativos.

`REQ.DC-02800` Para atualização do prazo de vigência do consentimento, realizar a comunicação entre a Instituição Receptora de Dados e a Instituição Transmissora de Dados exclusivamente via _backend_, sem direcionar o usuário para confirmação no ambiente da Instituição Transmissora de Dados.

`REQ.DC-02900` Não alterar o escopo de dados compartilhados, ou a Instituição Transmissora de Dados.

`REQ.DC-03000` Alterar a finalidade apenas quando houver necessidade de atualização por parte da Instituição Receptora de Dados, desde que não resulte em alteração do escopo de dados, comunicando de forma clara ao usuário o novo objetivo do compartilhamento.

`REQ.DC-03100` Calcular a nova data de validade do consentimento a partir da data em que ocorrer a renovação, permitindo ao usuário modificá-la apenas para uma data posterior à data de expiração vigente, inclusive para prazo indeterminado.

-   Ex.: Caso um consentimento tenha vigência de 01/01/2023 a 01/01/2024 (prazo de 12 meses), em qualquer opção de prazo apresentada ao usuário e independentemente do momento da renovação, a data final do consentimento renovado deve ser sempre posterior à data final do consentimento original.
    

`REQ.DC-03200` Não oferecer a renovação simplificada de consentimentos que envolvam múltiplas alçadas.

`REQ.DC-03300` Ao final do processo exibir uma tela de sucesso ou insucesso com a resposta da IT, em padrão visual semelhante ao da tela de efetivação, reforçando ao usuário se a renovação foi concluída ou não com sucesso.

`REQ.DC-03400` Em caso de insucesso da renovação de forma simplificada, exibir mensagens conforme o motivo do erro retornado, conforme exemplos a seguir:

-   `DEPENDE_MULTIPLA_ALCADA`: “O compartilhamento de dados não pôde ser renovado pois depende de múltipla alçada.”.
    
-   `DATA_EXPIRACAO_INVALIDA`: “O compartilhamento de dados não pôde ser renovado pois a data final ficou anterior à data de requisição do pedido de renovação ou igual à data de expiração atual ou diferente de prazo indeterminado e maior que 12 meses da data de requisição do pedido de renovação.”
    
-   `REFRESH_TOKEN_JWT`: “O compartilhamento de dados não pôde ser renovado com esta Instituição Transmissora.”
    
-   `ESTADO_CONSENTIMENTO_INVALIDO`: “O compartilhamento de dados não pôde ser renovado pois está encerrado ou foi cancelado.”
    
-   `ERRO GENÉRICO`: “O compartilhamento de dados não pôde ser renovado devido a problemas técnicos. Tente novamente mais tarde.”
    

![image-20260622-035746.png](images/image-20260622-035746.png)

#F4F5F7

## Requisitos - IT

**Cenário: Acesso ao Open Finance**

`REQ.DC-00100` Disponibilizar o ambiente Open Finance nos seus canais, incluindo-o no primeiro nível do menu principal, para garantir acesso rápido e fácil ao usuário.

![image-20260826-142905.png](images/image-20260826-142905.png)

`REQ.DC-00101` Quando aplicável disponibilizar termos e condições de uso somente na área de gestão.

![image-20260826-143300.png](images/image-20260826-143300.png)

**Cenário: Histórico de consentimentos - Geral**

`REQ.DC-00200` Disponibilizar, no ambiente Open Finance, uma seção dedicada à exibição do histórico completo de compartilhamentos.

`REQ.DC-00300` Diferenciar claramente os consentimentos transmitidos e recebidos para fins de consulta.

`REQ.DC-00400` Diferenciar claramente os consentimentos conforme o status: ativos, pendentes e inativos (revogados ou expirados).

`REQ.DC-00500` Disponibilizar acesso aos detalhes de cada consentimento no histórico.

`REQ.DC-00600` Nos detalhes do consentimento, exibir a validade do consentimento com o prazo ou data final. No caso de prazo indeterminado, identificar para o usuário como “Indeterminado” ou termo similar.

`REQ.DC-00700` Nos detalhes do consentimento, exibir o escopo dos dados compartilhados, como dados cadastrais, contas, cartões de crédito, investimentos e operações de crédito etc.

`REQ.DC-00710` Nos detalhes do consentimento, exibir a identificação do usuário solicitante em consentimentos com múltiplos aprovadores.

`REQ.DC-00720` No histórico de compartilhamento de dados, exibir o nome da instituição que está recebendo o compartilhamento.

`REQ.DC-00730` Nos detalhes do compartilhamento de dados, exibir o nome da instituição que está recebendo o compartilhamento.

![image-20260826-145106.png](images/image-20260826-145106.png)

**Cenário: Cancelamento de consentimento pendente - Geral**

`REQ.DC-00990` Nos detalhes do compartilhamento de dados, permitir que o usuário cancele a solicitação pendente.

`REQ.DC-00995` Ao confirmar o cancelamento de uma solicitação pendente, exibir mensagem de sucesso informando que a solicitação foi cancelada.

Ex.: Solicitação cancelada com sucesso.​

**Cenário: Histórico dos consentimentos - CIBA PF**

`REQ.DC-00760` No histórico de compartilhamento de dados, quando a solicitação estiver pendente, informar de forma explícita que há uma ação necessária do usuário.

-   Ex.: Aguardando confirmação.
    

`REQ.DC-00770` No histórico de compartilhamento de dados, quando a solicitação estiver pendente, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação do compartilhamento, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

-   Ex.: Confirmar até: 12/12/2026 às 09:11.
    

**Cenário: Detalhes do consentimento - CIBA PF**

`REQ.DC-00780` Nos detalhes do compartilhamento de dados, quando a solicitação estiver pendente, informar a data, contendo dia, mês e ano e o horário limite contendo horas e minutos para a confirmação do compartilhamento, que deve ser feita em até 24 horas a partir da conclusão da solicitação.

`REQ.DC-00790` Nos detalhes do compartilhamento de dados, permitir que o usuário confirme a solicitação pendente.

`REQ.DC-00795` Nos detalhes do compartilhamento de dados, após a confirmação da solicitação pendente, direcionar o usuário para a etapa de Efetivação do compartilhamento de dados.

![image-20260818-194210.png](images/image-20260818-194210.png)

**Cenário: Revogação do consentimento - Geral**

`REQ.DC-01000` No histórico e nos detalhes dos consentimentos, disponibilizar ao usuário a opção de revogar qualquer consentimento ativo, seja transmitido ou recebido.

`REQ.DC-01100` Antes da efetivação da revogação, exibir uma tela de confirmação, informando de forma clara as consequências da ação.

`REQ.DC-01200` Garantir que a revogação do consentimento contemple todos os dados objeto do compartilhamento.

`REQ.DC-01300` Respeitar, no processo de revogação, as regras de poderes já estabelecidas nas instituições.

`REQ.DC-01400` Após a revogação, manter o consentimento e seus detalhes acessíveis no histórico, com status e informações devidamente atualizados.

`REQ.DC-01500` Notificar a outra instituição quando o usuário realizar a revogação do consentimento.

**Cenário: Alteração do consentimento - Geral**

`REQ.DC-03500` Não oferecer jornada de alteração do consentimento.

**Cenário: Renovação padrão do consentimento - Geral**

`REQ.DC-03600` Não oferecer jornada de renovação padrão do consentimento.

**Cenário: Renovação simplificada do consentimento - Geral**

`REQ.DC-03700` Não oferecer jornada de renovação simplificada do consentimento.

#F4F5F7

## Recomendações - IR

**Cenário: Onboarding Open Finance**

`REC.DC-00100` Na primeira utilização do usuário, realizar onboarding objetivo, apresentando as funcionalidades disponibilizadas pela instituição no ambiente Open Finance. Disponibilizar, também, link de acesso à **Área do Cidadão** para consulta de informações relacionadas ao Open Finance.

![image-20260727-204605.png](images/image-20260727-204605.png)

**Cenário: Ambiente Open Finance**

`REC.DC-00200` Disponibilizar ao usuário o acesso aos consentimentos logo após o usuário acessar a opção **Open Finance** ou por meio de **Meus compartilhamentos**, acessado pela **Open Finance**.

`REC.DC-00300` Disponibilizar o ambiente Open Finance em áreas dedicadas aos produtos nos canais da instituição para facilitar o acesso do usuário.

`REC.DC-00301` Na tela inicial da área de gestão do Open Finance, exibir opções como “O que é o Open Finance?” e “Ler Termos de Uso” facilitando o acesso a informações essenciais sobre o funcionamento e os direitos do usuário no Open Finance.

`REC.DC-00400` Permitir, de forma opcional para cada instituição, a seleção de mais de um consentimento para revogação, com o objetivo de facilitar a experiência do usuário.

`REC.DC-00500` Disponibilizar, de forma opcional para cada instituição, filtros de busca para facilitar a localização dos consentimentos.

![image-20260622-040104.png](images/image-20260622-040104.png)

**Cenário: Histórico dos consentimentos - Geral**

`REC.DC-00650` No histórico e nos detalhes de compartilhamento de dados, quando a solicitação estiver pendente, exibir contador regressivo do prazo para confirmação da solicitação de compartilhamento de dados.

**Cenário: Renovação padrão do consentimento - Geral**

`REC.DC-00700` No caso de renovação padrão**,** comunicar o usuário sobre a proximidade da data de vencimento do consentimento, considerando a proporcionalidade em relação ao prazo total do compartilhamento.

`REC.DC-00800` No caso de renovação padrão, permitir a revogação do consentimento anterior após a renovação, caso ele ainda esteja vigente.

**Cenário: Renovação simplificada do consentimento - Geral**

`REC.DC-00900` No caso de renovação simplificada, comunicar o usuário sobre a proximidade da data de vencimento do consentimento, considerando a proporcionalidade em relação ao prazo total do compartilhamento.

#F4F5F7

## Recomendações - IT

**Cenário: Onboarding Open Finance**

`REC.DC-00100` Na primeira utilização do usuário, realizar onboarding objetivo, apresentando as funcionalidades disponibilizadas pela instituição no ambiente Open Finance. Disponibilizar, também, link de acesso à **Área do Cidadão** para consulta de informações relacionadas ao Open Finance.

**Cenário: Ambiente Open Finance**

`REC.DC-00200` Disponibilizar ao usuário o acesso aos consentimentos logo após o usuário acessar a opção **Open Finance** ou por meio de **Meus compartilhamentos**, acessado pela **Open Finance**.

`REC.DC-00300` Disponibilizar o ambiente Open Finance em áreas dedicadas aos produtos nos canais da instituição para facilitar o acesso do usuário.

`REC.DC-00301` Na tela inicial da área de gestão do Open Finance, exibir opções como “O que é o Open Finance?” e “Ler Termos de Uso” facilitando o acesso a informações essenciais sobre o funcionamento e os direitos do usuário no Open Finance.

![image-20260727-205519.png](images/image-20260727-205519.png)

`REC.DC-00400` Permitir, de forma opcional para cada instituição, a seleção de mais de um consentimento para revogação, com o objetivo de facilitar a experiência do usuário.

`REC.DC-00500` Disponibilizar, de forma opcional para cada instituição, filtros de busca para facilitar a localização dos consentimentos.

`REC.DC-00600` As ITs poderão, a seu critério, disponibilizar termos e condições referentes ao serviço de compartilhamento de dados, no Ambiente de Gestão de consentimento.

**Cenário: Histórico dos consentimentos - Geral**

`REC.DC-00650` No histórico e nos detalhes de compartilhamento de dados, quando a solicitação estiver pendente, exibir contador regressivo do prazo para confirmação da solicitação de compartilhamento de dados.

* * *

# Status do Compartilhamento de dados

Para padronizar e facilitar o entendimento do usuário nas Jornadas de Compartilhamento de Dados e Iniciação de Pagamento, são apresentados a seguir os status que devem ser apresentados ao usuário.

As tabelas têm como objetivo deixar claro o De/Para entre o status apresentados para o usuário e os status técnicos das APIs.

![image-20260826-151906.png](images/image-20260826-151906.png)

#F4F5F7

## Requisitos - IR

**Cenário: Geral**

`REQ.DC-03800` O status do compartilhamento deve estar relacionado com a combinação do status do consentimento e, conforme aplicável, das `resources` associadas a ele e do efetivo compartilhamento de dados cadastrais.  
`PENDING AUTHORISATION` > `AVAILABLE` \> `TEMPORARILY UNAVAILABLE` > `UNAVAILABLE`

-   Por exemplo: se um consentimento vigente está compartilhando normalmente dados de cadastro e transacionais, mas tem algum recurso com status `UNAVAILABLE`, o status para o usuário deve ser **Ativo**, pois status `AVAILABLE` na ordem de precedência, vem antes do status `UNAVAILABLE` . Por outro lado, se algum recurso está com status `PENDING AUTHORISATION`, então o status para o usuário final deve ser **Pendente de autorização**.  
    Confira outros exemplos para casos de API com diferentes status a seguir.
    

**STATUS PARA USUÁRIO FINAL**

**CONSENTIMENTO**

**RECURSO DE SELEÇÃO AGRUPADA (OPERAÇÃO DE CRÉDITO, INVESTIMENTO, CÂMBIO)**

**RECURSOS DE SELEÇÃO INDIVIDUAL (CONTA OU CARTÃO)**

**PERMISSÃO PARA DADOS CADASTRAIS**

Ativo

AUTHORISED

AVAILABLE

UNAVAILABLE

SIM/NÃO

Ativo

AUTHORISED

UNAVAILABLE

AVAILABLE

SIM/NÃO

Ativo

AUTHORISED

AVAILABLE

TEMPORARILY UNAVAILABLE

SIM/NÃO

Ativo

AUTHORISED

NÃO SOLICITOU PERMISSÕES¹

NÃO SOLICITOU PERMISSÕES¹

SIM

Ativo²

AUTHORISED

UNAVAILABLE

UNAVAILABLE

SIM/NÃO

Ativo

AUTHORISED

TEMPORARILY UNAVAILABLE

UNAVAILABLE

SIM

Temporariamente indisponível

AUTHORISED

TEMPORARILY UNAVAILABLE

UNAVAILABLE

NÃO

Aguardando aprovação

AUTHORISED

PENDING AUTHORISATION

AVAILABLE

SIM/NÃO

Aguardando aprovação

AUTHORISED

PENDING AUTHORISATION

TEMPORARILY UNAVAILABLE

SIM/NÃO

Aguardando aprovação

AUTHORISED

PENDING AUTHORISATION

UNAVAILABLE

SIM/NÃO

#F4F5F7

1 Usuário não solicitou permissões dos produtos

2 Considerando que o usuário manteve relacionamento com a instituição transmissora

`REQ.DC-03900` Caso haja diferentes status de recursos em um mesmo consentimento (`AVAILABLE`, `PENDING_AUTHORISATION`, `TEMPORARILY UNAVAILABLE` e `UNAVAILABLE`) e considerando, também, se há ou não impedimento no tráfego de dados cadastrais (pois não geram recursos listáveis na API Resources) , o peso de cada status para consolidação e demonstração do status do consentimento deve observar o seguinte:

**STATUS PARA USUÁRIO FINAL**

**CONSENTIMENTO**

**RECURSO DE SELEÇÃO AGRUPADA (OPERAÇÃO DE CRÉDITO, INVESTIMENTO, CÂMBIO)**

**RECURSOS DE SELEÇÃO INDIVIDUAL (CONTA OU CARTÃO)**

**PERMISSÃO PARA DADOS CADASTRAIS**

Aguardando aprovação

AUTHORISED

AVAILABLE

PENDING AUTHORISATION

SIM/NÃO

Aguardando aprovação

AUTHORISED

TEMPORARILY UNAVAILABLE

PENDING AUTHORISATION

SIM/NÃO

Aguardando aprovação

AUTHORISED

UNAVAILABLE

PENDING AUTHORISATION

SIM/NÃO

Aguardando aprovação

AWAITING\_AUTHORISATION

NÃO SE APLICA

NÃO SE APLICA

NÃO SE APLICA

Vencido

REJECTED

NÃO SE APLICA

NÃO SE APLICA

NÃO SE APLICA

Encerrado

REJECTED

NÃO SE APLICA

NÃO SE APLICA

NÃO SE APLICA

`REQ.DC-03950` Os `rejections_reasons` podem ser utilizados para mostrar detalhes sobre os status. Para três deles, temos os seguintes requisitos:

1.  `INTERNAL_SECURITY_REASON`: por se tratar de um consentimento rejeitado devido às políticas de segurança aplicadas pela Instituição Transmissora (prevenção a fraudes), não deverão ser utilizados, na consulta do detalhamento do consentimento, termos que afirmem se tratar de fraude.
    
2.  `CONSENT_MAX_DATE_REACHED`: deve ser mostrado ao usuário com o status **Vencido.**
    
3.  `CONSENT_EXPIRED`, `CUSTOMER_MANUALLY_REJECTED` e `CONSENT_ TECHNICAL_ISSUE`: não precisam ser demonstrados na consulta dos consentimentos, pois o usuário não chegou a concluir sua solicitação.
    
4.  `CUSTOMER_MANUALLY_REVOKED`: deve ser mostrado ao usuário com o status **Encerrado**.
    

**Nota**

Mais detalhes e informações técnicas sobre os status das APIs de dados cadastrais e transacionais do usuário podem ser encontrados na Área do Desenvolvedor.

#F4F5F7

## Requisitos - IT

**Cenário: Geral**

`REQ.DC-03800` O status do compartilhamento deve estar relacionado com a combinação do status do consentimento e, conforme aplicável, das `resources` associadas a ele e do efetivo compartilhamento de dados cadastrais.  
`PENDING AUTHORISATION` > `AVAILABLE` \> `TEMPORARILY UNAVAILABLE` > `UNAVAILABLE`

-   Por exemplo: se um consentimento vigente está compartilhando normalmente dados de cadastro e transacionais, mas tem algum recurso com status `UNAVAILABLE`, o status para o usuário deve ser **Ativo**, pois status `AVAILABLE` na ordem de precedência, vem antes do status `UNAVAILABLE` . Por outro lado, se algum recurso está com status `PENDING AUTHORISATION`, então o status para o usuário final deve ser **Pendente de autorização**.  
    Confira outros exemplos para casos de API com diferentes status a seguir.
    

**STATUS PARA USUÁRIO FINAL**

**CONSENTIMENTO**

**RECURSO DE SELEÇÃO AGRUPADA (OPERAÇÃO DE CRÉDITO, INVESTIMENTO, CÂMBIO)**

**RECURSOS DE SELEÇÃO INDIVIDUAL (CONTA OU CARTÃO)**

**PERMISSÃO PARA DADOS CADASTRAIS**

Ativo

AUTHORISED

AVAILABLE

UNAVAILABLE

SIM/NÃO

Ativo

AUTHORISED

UNAVAILABLE

AVAILABLE

SIM/NÃO

Ativo

AUTHORISED

AVAILABLE

TEMPORARILY UNAVAILABLE

SIM/NÃO

Ativo

AUTHORISED

NÃO SOLICITOU PERMISSÕES¹

NÃO SOLICITOU PERMISSÕES¹

SIM

Ativo²

AUTHORISED

UNAVAILABLE

UNAVAILABLE

SIM/NÃO

Ativo

AUTHORISED

TEMPORARILY UNAVAILABLE

UNAVAILABLE

SIM

Temporariamente indisponível

AUTHORISED

TEMPORARILY UNAVAILABLE

UNAVAILABLE

NÃO

Aguardando aprovação

AUTHORISED

PENDING AUTHORISATION

AVAILABLE

SIM/NÃO

Aguardando aprovação

AUTHORISED

PENDING AUTHORISATION

TEMPORARILY UNAVAILABLE

SIM/NÃO

Aguardando aprovação

AUTHORISED

PENDING AUTHORISATION

UNAVAILABLE

SIM/NÃO

#F4F5F7

1 Usuário não solicitou permissões dos produtos

2 Considerando que o usuário manteve relacionamento com a instituição transmissora

`REQ.DC-03900` Caso haja diferentes status de recursos em um mesmo consentimento (`AVAILABLE`, `PENDING_AUTHORISATION`, `TEMPORARILY UNAVAILABLE` e `UNAVAILABLE`) e considerando, também, se há ou não impedimento no tráfego de dados cadastrais (pois não geram recursos listáveis na API Resources) , o peso de cada status para consolidação e demonstração do status do consentimento deve observar o seguinte:

**STATUS PARA USUÁRIO FINAL**

**CONSENTIMENTO**

**RECURSO DE SELEÇÃO AGRUPADA (OPERAÇÃO DE CRÉDITO, INVESTIMENTO, CÂMBIO)**

**RECURSOS DE SELEÇÃO INDIVIDUAL (CONTA OU CARTÃO)**

**PERMISSÃO PARA DADOS CADASTRAIS**

Aguardando aprovação

AUTHORISED

AVAILABLE

PENDING AUTHORISATION

SIM/NÃO

Aguardando aprovação

AUTHORISED

TEMPORARILY UNAVAILABLE

PENDING AUTHORISATION

SIM/NÃO

Aguardando aprovação

AUTHORISED

UNAVAILABLE

PENDING AUTHORISATION

SIM/NÃO

Aguardando aprovação

AWAITING\_AUTHORISATION

NÃO SE APLICA

NÃO SE APLICA

NÃO SE APLICA

Vencido

REJECTED

NÃO SE APLICA

NÃO SE APLICA

NÃO SE APLICA

Encerrado

REJECTED

NÃO SE APLICA

NÃO SE APLICA

NÃO SE APLICA

`REQ.DC-03950` Os `rejections_reasons` podem ser utilizados para mostrar detalhes sobre os status. Para três deles, temos os seguintes requisitos:

1.  `INTERNAL_SECURITY_REASON`: por se tratar de um consentimento rejeitado devido às políticas de segurança aplicadas pela Instituição Transmissora (prevenção a fraudes), não deverão ser utilizados, na consulta do detalhamento do consentimento, termos que afirmem se tratar de fraude.
    
2.  `CONSENT_MAX_DATE_REACHED`: deve ser mostrado ao usuário com o status **Vencido.**
    
3.  `CONSENT_EXPIRED`, `CUSTOMER_MANUALLY_REJECTED` e `CONSENT_ TECHNICAL_ISSUE`: não precisam ser demonstrados na consulta dos consentimentos, pois o usuário não chegou a concluir sua solicitação.
    
4.  `CUSTOMER_MANUALLY_REVOKED`: deve ser mostrado ao usuário com o status **Encerrado**.
    

**Nota**

Mais detalhes e informações técnicas sobre os status das APIs de dados cadastrais e transacionais do usuário podem ser encontrados na Área do Desenvolvedor.

#F4F5F7

## Recomendações - IR

**Cenário: Geral**

`REC.DC-01000` Para consentimentos encerrados, apresentar o detalhamento do motivo do encerramento, conforme o `rejection_reason` associado.

`REC.DC-01100` Caso o compartilhamento esteja com status ativo, porém, com algum recurso não acessível, a Instituição Receptora dos Dados pode, a seu critério, sinalizar a existência da pendência na lista de consentimento e sugerir que o usuário verifique o detalhamento do consentimento. Fica a critério da instituição apresentar o status isolado por `resource` na consulta do usuário.

#F4F5F7

## Recomendações - IT

**Cenário: Geral**

`REC.DC-01000` Para consentimentos encerrados, apresentar o detalhamento do motivo do encerramento, conforme o `rejection_reason` associado.
