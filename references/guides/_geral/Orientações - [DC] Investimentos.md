# Orientações - [DC] Investimentos

16falselistfalse

## Tempestividade dos dados para APIs de Investimentos

-   Até uma hora para as APIs Renda Fixa Bancária, Renda Fixa Crédito, Títulos do Tesouro Direto e Fundos de Investimento;
    
-   Para a API Renda Variável, devido a frequente alteração dos preços e a dinâmica de funcionamento do produto (ordens de compra e venda), serão expostas a posição e movimentações do fechamento do dia anterior (d-1). Porém, ressaltamos que ao consultar esses dados, os dados compartilhados ainda podem se referir a D-2, devido a janela de processamento das transações de renda variável pela transmissora, que foram recebidas da B3.
    

## Visão da API de Recursos (Resources) para os Produtos de Investimentos

O identificador único resourceId de cada recurso dos produtos de investimentos presentes na lista devolvida pela API Recursos, corresponde ao identificador único investimentId utilizado pelas APIs de Investimentos (Renda Fixa Crédito, Renda Fixa Bancária, Renda Fixa Variável, Títulos de Tesouro Direto e Fundos de Investimento).

### Regras de Negócio

**Código da Regra**

**Descrição da Regra**

**RN001**

É obrigatório que todos os recursos do tipo investimentos passíveis de compartilhamento retornem o identificador único independente do status a ser informado. As granularidades definidas para as APIs de cada produto de investimento encontra-se na definição dos mesmos.

**RN002**

É obrigatório o retorno de todos os investimentos passíveis de compartilhamento, independente de seus status. O investimento que já foi objeto de compartilhamento no Open Finance (que em algum momento teve seu status AVAILABLE) deve ter seu status alterado para UNAVAILABLE na data em que completa 12 meses do resgate, vencimento, transferência de custódia ou titularidade.

**RN003**

Caso a Transmissora ainda esteja preparando a listagem dos recursos autorizados da API de Recursos (Resources), deve ser retornado o código HTTP Status Code 202- accepted com o _body_ vazio, e a Receptora deverá seguir as recomendações de polling

**RN004**

É obrigatório que todos os investimentos elegíveis sejam compartilhados, ou seja, tenham seu resourceld corretamente expostos. Isso vale tanto para investimentos existentes no momento do consentimento, encerrados nos últimos 12 meses ou investimentos que venham a ser firmados após esse momento, desde que o consentimento esteja vigente.

**RN005**

Investimentos que estejam em processo de múltiplas alçadas para aprovação devem retornar o status PENDING\_AUTHORISATION

**RN006**

O método de listagem das APIs de Investimentos deve retornar apenas a lista de investimentos que estejam com o status de Resources como AVAILABLE

**RN007**

Cada recurso (investimento) autorizado no consentimento deve ter seu status tratado de forma independente

**RN008**

No caso em que um cliente tenha consentido a opção “investimentos” no compartilhamento de produtos, mas não possua nenhuma operação, a API Recursos deve retornar lista vazia, com HTTP Status Code 200

### Recomendação do uso de _polling_

É recomendado que a instituição receptora implemente um _retry_ exponencial (o tempo de espera entre a última chamada e a próxima chamada da API deve crescer exponencialmente), de forma a não sobrecarregar a API Recursos.

### Diagrama representacional do status da API de Recursos (Resources) para as APIs Renda Fixa Crédito, Renda Fixa Bancária e Títulos do Tesouro Direto

Produtos encerrados x Período de vigência do consentimento

**Consentimento (ex. 4 meses)**

**Cenários**

**DIA D**

**D+1M**

**D+2M**

**D+3M**

**D+4M**

**D+5M**

Produto encerrado\* em D-13M

Não é escopo de compartilhamento

Produto encerrado\* em D-11M

AVAILABLE

AVAILABLE

UNAVAILABLE

UNAVAILABLE

UNAVAILABLE

Acesso a API não autorizado

Produto encerrado\* em D+2M

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

Acesso a API não autorizado

### Diagrama representacional do status da API de Recursos (Resources) para as APIs de Fundos e Renda Variável

Produtos encerrados x Período de vigência do consentimento

**Consentimento (ex. 4 meses)**

**Cenários**

**DIA D**

**D+1M**

**D+2M**

**D+3M**

**D+4M**

**D+5M**

Produto encerrado\* em D-13M

Não é escopo de compartilhamento

Produto encerrado\* em D-11M

AVAILABLE

AVAILABLE

UNAVAILABLE

UNAVAILABLE

UNAVAILABLE

Acesso a API não autorizado

Nova movimentação (D+3M) em produto encerrado\* em D-11

AVAILABLE

AVAILABLE

UNAVAILABLE

AVAILABLE

AVAILABLE

Acesso a API não autorizado

Produto encerrado\* em D+2M

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

Acesso a API não autorizado

\*vencido, resgatado ou em casos de transferência de titularidade ou custódia

**Glossário:**

-   **Dia D** - dia do consentimento.
    
-   **Eixo X** - representa o tempo em meses.
    
-   **Eixo em Y** - representa o cenários que são produtos e suas vigências. Ex.: investimento resgatado há 13 meses.
    
-   O encontro dos eixos representa o **status** da API Recursos naquele tempo para aquele produto .
    

### Regras para o retorno das APIs de produtos de investimentos de acordo com o status do Recurso (PENDING\_AUTHORISATION, AVAILABLE, UNAVAILABLE E TEMPORARILY\_UNAVAILABLE) e a transição entre status

-   **PENDING\_AUTHORISATION**: indica a existência de pendências para o compartilhamento do recurso, em caso de múltiplas alçadas, quando é necessário consentimento de mais de um titular. Nesse caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:
    

{

"code": "STATUS\_RESOURCE\_PENDING\_AUTHORISATION",

"title": "Aguardando autorização de múltiplas alçadas",

"detail": "(uso a critério do transmissor)”

}

-   **AVAILABLE:** indica que o recurso do produto de investimentos escolhido encontra-se disponível para consulta nas APIs de investimentos através do identificador investmentId compartilhado. A Transmissora retorna os dados com status HTTP 200.
    
-   **UNAVAILABLE**: indica que o recurso (investimento) se encontra indisponível para consultas nas APIs de Investimentos. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:
    

{

"code": "STATUS\_RESOURCE\_UNAVAILABLE",

"title": "Recurso indisponível",

"detail": "(uso a critério do transmissor)”

}

-   **TEMPORARILY\_UNAVAILABLE**: indica que o recurso (investimento) se encontra temporariamente indisponível para consulta nas APIs de Investimentos do produto em questão. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:
    

{

"code": "STATUS\_RESOURCE\_TEMPORARILY\_UNAVAILABLE",

"title": "Recurso temporariamente indisponível",

"detail": "(uso a critério do transmissor)”

}

### Casos de uso de Investimentos e o respectivo status a ser informado pela API Recursos

-   Investimentos que se encontram em plena utilização e disponíveis nos canais de atendimento eletrônico devem ter seu status como AVAILABLE.
    
-   Investimentos vencidos, resgatados ou que tiveram sua titularidade ou custódia transferida nos últimos 12 meses anteriores a data consulta - considerando o consentimento vigente - devem ter seus status como AVAILABLE.
    
-   Investimentos vencidos, resgatados ou que tiveram sua titularidade ou custódia transferida a mais que 12 meses anteriores a data consulta - considerando o consentimento vigente - devem ter seus status como UNAVAILABLE.
    
-   Investimentos dos produtos de renda variável e fundos de investimento que tenham nova movimentação após já ter completado 12 meses de seu vencimento, resgate ou transferência devem ter seu identificador (investmentId) preservado, e o status do recurso alterado para AVAILABLE.
    
-   Investimentos que se encontram em bloqueios temporários, onde o cliente não possui acesso aos detalhes por meio dos canais de atendimento eletrônico, devem retornar o status TEMPORARILY\_UNAVAILABLE.
    
-   Investimentos que se encontram em bloqueios definitivos onde o cliente não possui acesso por meio dos canais de atendimento eletrônico, devem retornar o status UNAVAILABLE.
    
-   Investimentos com saldo bloqueado (total ou parcialmente) devem retornar o status AVAILABLE.
    
-   Investimentos bloqueado, como por exemplo nos casos de investimentos dados como garantia, devem retornar o status AVAILABLE.
    
-   Investimentos vencidos, resgatados ou que tiveram sua titularidade ou custódia transferida em situações nas quais o cliente não mais possua acesso aos canais de atendimento eletrônico da instituição, devem retornar o status UNAVAILABLE.
    
-   Casos de uso que um cliente final efetue um consentimento para investimentos para o qual um dos recursos (respeitando a RN001) exija a aprovação de múltiplas alçadas (PENDING\_AUTHORISATION) e outro recurso esteja disponível para consulta (AVAILABLE), o comportamento esperado e que cada recurso tenha seu status representado de forma independente, disponibilizando imediatamente os recursos já aprovados.
    

### Tabela descritiva das possibilidades de interação entre API Recursos e as APIs de Investimentos

**Cenário**

**Status do recurso na transmissora**

**API Recursos (…/resources/v1/resources)**

**API de listagem de Produto (/bank-fixed-incomes)¹**

**APIs de Dados de Produtos (/bank-fixed-incomes/{investmentId})²**

Sem consentimento

\-

401 unauthorized

401 unauthorized

401 unauthorized

Com consentimento não autorizado

\-

401 unauthorized

401 unauthorized

401 unauthorized

Com consentimento autorizado (pendente múltipla alçada)

\-

200 - Retorna recurso com status PENDING\_AUTHORISATION

200 Não retorna

403 forbidden

Com consentimento autorizado (aprovado múltipla alçada)

OK

200 - Retorna recurso com status AVAILABLE

200 retorna o recurso na lista

200 retorna dados para o recurso

Com consentimento autorizado (aprovado múltipla alçada)

Bloqueio temporário

200 - Retorna recurso com status TEMPORARILY\_UNAVAILABLE

200 não retorna na lista o recurso “bloqueado”

403 forbidden

Com consentimento autorizado (aprovado múltipla alçada)

Vencido a menos de 12 meses

200 - Retorna o recurso como status AVAILABLE

200 retorna o recurso na lista

200 retorna o recurso na lista

Com consentimento autorizado (aprovado múltipla alçada)

Vencido a mais de 12 meses (recurso nunca compartilhado na vigência do consentimento)

200 - Não retorna o recurso

200 - Não retorna o recurso

403 forbidden

Com consentimento autorizado (aprovado múltipla alçada)

Liquidado a mais de 12 meses (recurso já compartilhado na vigência do consentimento)

200 - Retorna o recurso como status UNAVAILABLE

200 - Não retorna o recurso

403 forbidden

Com consentimento autorizado (aprovado múltipla alçada)

\-

200 - Retorna recurso com status UNAVAILABLE

200 - Não retorna o recurso recusado na lista

403 forbidden

Com consentimento autorizado (recurso inexistente)

\-

200 - Não retorna o recurso

200 - Não retorna o recurso

403 forbidden

Com Consentimento revogado ou expirado³

\-

401 unauthorized

401 unauthorized

401 unauthorized

**Legenda**:

1 - Válido para a listagem de todos os produtos de investimentos.

2 - Válido para todos os endpoints de produtos de investimentos.

3 - Para os cenários de consentimento revogado ou expirado, conforme determinado na especificação de segurança o _access token_ associado ao mesmo é invalidado impossibilitando a consulta às APIs de Investimentos por parte da Receptora.

### Regras quanto a interpretação pelas receptoras do status da API Recursos para os recursos de investimentos

-   **PENDING\_AUTHORISATION**: neste caso a recomendação e que a Receptora aguarde a alteração desse status para um dos demais status executando _polling_ na API Recursos (vide recomendações de _polling_).
    
-   **AVAILABLE:** indica que o recurso encontra-se disponível para consulta na API de Investimentos correspondente ao produto em questão, através do identificador investmentld compartilhado.
    
-   **UNAVAILABLE**: neste status a recomendação é que a Receptora não consulte a API de Investimentos em função do dado não estar disponível para esse investmentld.
    
-   **TEMPORARILY\_UNAVAILABLE**: neste status a recomendação e que a Receptora aguarde a alteração desse status para um dos demais status executando _polling_ na API Recursos (vide recomendações de _polling)._
    

### Regras de busca na API Recursos em relação aos recursos das APIs de Investimentos

-   Recomenda-se que a Receptora consulte a API Recursos logo após identificar que o consentimento se encontra autorizado de modo a obter todas as operações de produtos de investimentos consentida pelo cliente e seus respectivos identificadores - lembrando que para investimentos pode não haver nenhuma operação no momento da primeira consulta, e posteriormente novas operações podem aparecer.
    

-   Recomenda-se que a Receptora implemente uma rotina de consulta de novas operações consumindo a API de Recursos de forma periódica. Cabe a lnstituição Receptora definir a periodicidade que melhor atende as suas necessidades.
    

-   Recomenda-se que a Receptora, caso obtenha um erro HTTP Status Code 403 - Forbidden nas APls de Investimentos avalie o JSON retornado no _body_ da requisição para identificar as informações adicionais referentes ao erro, como o status específico da API Recursos que impede o consumo da informação.
    
-   Recomenda-se que a Receptora consulte a API Recursos caso obtenha um erro na API de produtos de investimentos, de modo a identificar uma possível alteração de status do recurso.
    

##  Definição das regras dos recursos de compartilhamento

**Consentimento**

**Modelo:**

**Compartilha todos os recursos elegíveis**

**Período de vigência máximo**

**12 meses**

Recursos incluídos no compartilhamento

-   Investimentos ativos em um período de até 12 meses anterior ao inicio da vigência do consentimento;
    
-   Investimentos que venceram, foram resgatados ou tiveram sua titularidade ou custódia transferida em um período de até 12 meses anterior ao inicio da vigência do consentimento;
    
-   Investimento contratados durante o período de vigência do consentimento;
    
-   Investimentos que venceram, foram resgatados ou tiveram sua titularidade ou custódia transferida durante o período de vigência do consentimento;
    

Recursos não incluídos no compartilhamento

-   Investimentos que venceram ou foram resgatados em um período maior que 12 meses anterior ao inicio da vigência do consentimento;
    
-   Investimentos que pertencem a clientes que estão sob algum tipo de bloqueio conforme políticas internas das instituições;
    
-   Investimentos com aplicação e resgate automático;
    

## Regras de Exposição de Movimentações de Investimentos

-   Nas APIs de Investimentos, todas as movimentações devem ser reportadas com consistência dos campos type e transactionType.
    
-   O campo type reflete o sentido financeiro da movimentação (ENTRADA ou SAÍDA). O campo transactionType identifica sua natureza (por exemplo: APLICACAO, RESGATE, VENCIMENTO, EVENTO\_PROGRAMADO).
    
-   A seguir, o mapeamento padrão deve ser observado:
    

**Cenário**

**type**

**transactionType**

Resgate total/parcial

SAIDA

RESGATE

Vencimento de título

SAIDA

VENCIMENTO

Pagamento de juros/cupom

ENTRADA

PAGAMENTO\_JUROS

Amortização programada

ENTRADA

AMORTIZACAO

Outro evento não previsto

—

OUTROS

## Orientações de preenchimento para dados das APIs de Investimentos

-   Os campos **/data/remuneration/preFixedRate e /data/remuneration/postFixedIndexerPercentage**, do endpoint **GET** **investments/{investmentId**}, passam a ser de envio obrigatório quando se tratar de produto com remuneração híbrida, a partir da versão 1.1.0. Não é necessário o reprocessamento de históricos de contratos cuja posição seja igual a zero para atender à nova regra.
