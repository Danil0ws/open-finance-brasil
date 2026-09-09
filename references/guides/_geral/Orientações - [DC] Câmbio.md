# Orientações - [DC] Câmbio

## Tempestividade dos dados para API de Câmbio

-   A defasagem máxima em relação ao canal deve ser de até uma hora, devido ao fato da API de Câmbio não possuir atualizações tempestivas.
    

## Definição das regras dos recursos de compartilhamento

**Consentimento**

**Modelo:**

**Compartilha todos os recursos elegíveis**

**Período de vigência máximo**

**12 meses**

Recursos incluídos no compartilhamento

-   Operações de câmbio ainda em aberto em um período de até 12 meses anterior ao inicio da vigência do consentimento e todos os seus eventos (caso existam), mesmo que contratadas em um período superior a 12 meses;
    
-   Operações de câmbio canceladas ou liquidadas em um período de até 12 meses anterior ao inicio da vigência do consentimento e todos os seus eventos (caso existam), mesmo que contratadas em um período superior a 12 meses;
    
-   Operações de câmbio contratadas, canceladas ou liquidadas e todos os seus eventos (caso existam) durante o período de vigência do consentimento, mesmo que contratadas em um período superior a 12 meses;
    

Recursos não incluídos no compartilhamento

-   Operações de câmbio canceladas ou liquidadas em um período maior que 12 meses anterior ao inicio da vigência do consentimento;
    
-   Operações de câmbio que pertencem a clientes que estão sob algum tipo de bloqueio conforme políticas internas das instituições;
    
-   Operações de câmbio anuladas.
    

## Visão da API Recursos para os Produtos de Câmbio

O identificador único resourceId de cada recurso das operações de câmbio presentes na lista devolvida pela API Recursos, corresponde ao identificador único operationId utilizado pela API de Câmbio.

### Regras de Negócio

**Código da Regra**

**Descrição da Regra**

**RN001**

É obrigatório que todos os recursos do tipo câmbio passíveis de compartilhamento retornem o identificador único independente do status a ser informado.

**RN002**

É obrigatório o retorno de todas as operações passíveis de compartilhamento, independente de seus status. A operação de câmbio que já foi objeto de compartilhamento no Open Finance (que em algum momento teve seu status AVAILABLE) deve ter seu status alterado para UNAVAILABLE na data em que completa 12 meses de sua data de liquidação ou do cancelamento.

**RN003**

Caso a Transmissora ainda esteja preparando a listagem dos recursos autorizados da API Recursos, deve ser retornado o código HTTP Status Code 202 - accepted com o _body_ vazio, e a Receptora deverá seguir as recomendações de _polling._

**RN004**

É obrigatório que todos as operações de câmbio elegíveis sejam compartilhadas, ou seja, tenham seu resourceId corretamente expostos. Isso vale tanto para operações contratadas, liquidadas ou canceladas nos últimos 12 meses em relação ao início de vigência do consentimento ou operações que venham a ser contratadas, liquidadas ou canceladas após esse momento, desde que o consentimento esteja vigente.

**RN005**

Operações de câmbio que estejam em processo de múltiplas alçadas para aprovação devem retornar o status PENDING\_AUTHORISATION.

**RN006**

O método de listagem das API de Câmbio deve retornar apenas a lista de operações de câmbio que estejam com o status de Resources como AVAILABLE.

**RN007**

Cada recurso (operação) autorizado no consentimento deve ter seu status tratado de forma independente.

**RN008**

No caso em que um cliente tenha consentido a opção “câmbio” no compartilhamento de produtos, mas não possua nenhuma operação, a API Recursos deve retornar lista vazia, com HTTP Status Code 200.

### Recomendação do uso de _polling_

É recomendado que a instituição receptora implemente um _retry_ exponencial (o tempo de espera entre a última chamada e a próxima chamada da API deve crescer exponencialmente), de forma a não sobrecarregar a API Recursos.

### Diagrama representacional do status da API Recursos

Produtos encerrados x Período de vigência do consentimento.

**Consentimento (ex. 4 meses)**

**Cenários**

**DIA D**

**D+1M**

**D+2M**

**D+3M**

**D+4M**

**D+5M**

Operação ocorrida\* em D -13M

Não é escopo de compartilhamento

Operação ocorrida\* em D -11M

AVAILABLE

AVAILABLE

UNAVAILABLE

UNAVAILABLE

UNAVAILABLE

Acesso a API não autorizado

Operação ocorrida\* em D +2M

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

AVAILABLE

Acesso a API não autorizado

\*cancelada ou liquidada

**Glossário:**

-   **Dia D** - dia do consentimento.
    
-   **Eixo X** - representa o tempo em meses.
    
-   **Eixo em Y** - representa o cenários que são produtos e suas vigências. Ex.: operação cancelada há 13 meses.
    
-   O encontro dos eixos representa o **status** da API Recursos naquele tempo para aquele produto.
    

### Regras para o retorno da API de produtos de câmbio de acordo com o status do Recurso (PENDING\_AUTHORISATION, AVAILABLE, UNAVAILABLE E TEMPORARILY\_UNAVAILABLE) e a transição entre status

-   **PENDING\_AUTHORISATION**: indica a existência de pendências para o compartilhamento do recurso, em caso de múltiplas alçadas, quando é necessário o consentimento de mais de um titular. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:
    

{

"code": "STATUS\_RESOURCE\_PENDING\_AUTHORISATION",

"title": "Aguardando autorização de múltiplas alçadas",

"detail": "(uso a critério do transmissor)”

}

-   **AVAILABLE:** indica que o recurso do produto de câmbio escolhido encontra-se disponível para consulta nas API de Câmbio através do identificador operationId compartilhado. A Transmissora retorna os dados com status HTTP 200.
    
-   **UNAVAILABLE**: indica que o recurso (câmbio) se encontra indisponível para consulta na API Câmbio. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:
    

{

"code": "STATUS\_RESOURCE\_UNAVAILABLE",

"title": "Recurso indisponível",

"detail": "(uso a critério do transmissor)”

}

-   **TEMPORARILY\_UNAVAILABLE**: indica que o recurso (câmbio) se encontra temporariamente indisponível para consulta nas API de Câmbio do produto em questão. Neste caso a Transmissora deve retornar um erro HTTP Status Code 403 - Forbidden com o conteúdo abaixo:
    

{

"code": "STATUS\_RESOURCE\_TEMPORARILY\_UNAVAILABLE",

"title": "Recurso temporariamente indisponível",

"detail": "(uso a critério do transmissor)”

}

### Casos de uso de Câmbio e o respectivo status a ser informado pela API Recursos

-   Operações de câmbio que se encontram em aberto devem ter seus status exibido como AVAILABLE.
    
-   Operações de Câmbio liquidadas ou canceladas nos últimos 12 meses anteriores a data da consulta – considerando o consentimento vigente - devem ter seus status como AVAILABLE.
    
-   Operações de câmbio liquidadas ou canceladas a mais que 12 meses anteriores a data consulta – considerando o consentimento vigente - devem ter seus status como UNAVAILABLE.
    
-   Operações de câmbio que se encontram em bloqueio temporário, onde o cliente não possui acesso aos detalhes por meio dos canais de atendimento eletrônico, devem retornar o status TEMPORARILY\_UNAVAILABLE.
    
-   Operações de câmbio que se encontram em bloqueio definitivo onde o cliente não possui acesso por meio dos canais de atendimento eletrônico, devem retornar o status UNAVAILABLE.
    
-   Operações de câmbio liquidadas ou canceladas em situações nas quais o cliente não mais possua acesso aos canais de atendimento eletrônico da instituição, devem retornar o status UNAVAILABLE.
    
-   Casos de uso em que o cliente final efetue um consentimento para operações de câmbio para o qual um dos recursos (respeitando a RN001) exija a aprovação de múltiplas alçadas (PENDING\_AUTHORISATION) e outro recurso esteja disponível para consulta (AVAILABLE), o comportamento esperado é que cada recurso tenha seu status representado de forma independente, disponibilizando imediatamente os recursos já aprovados.
    
-   Operações de câmbio anuladas não são escopo de compartilhamento na API Recursos.
    

### Tabela descritiva das possibilidades de interação entre API Recursos e a API Câmbio

**Cenário**

**Status do recurso na transmissora**

**API Recursos (…/resources/v1/resources)**

**API de listagem de Produto (/exchanges)¹**

**APIs de Dados de Produtos (/exchanges/{operationId})²**

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

Liquidado a menos de 12 meses

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

Com consentimento autorizado (recusado múltipla alçada)

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

API

**Legenda**:

1 - Válido para a listagem de todos os produtos de câmbio.

2 - Válido para todos os endpoints de produtos de câmbio.

3 - Para os cenários de consentimento revogado ou expirado, conforme determinado na especificação de segurança o access token associado ao mesmo é invalidado impossibilitando a consulta às API de Câmbio por parte da Receptora.

### Regras quanto a interpretação pelas receptoras do status da API Recursos para os recursos de câmbio

-   **PENDING\_AUTHORISATION**: neste caso a recomendação e que a Receptora aguarde a alteração desse status para um dos demais status executando _polling_ na API Recursos (vide recomendações de _polling_).
    
-   **AVAILABLE:** indica que o recurso encontra-se disponível para consulta na API de Câmbio correspondente ao produto em questão, através do identificador operationId compartilhado.
    
-   **UNAVAILABLE**: neste status a recomendação é que a Receptora não consulte a API de Câmbio em função do dado não estar disponível para esse operationId.
    
-   **TEMPORARILY\_UNAVAILABLE**: neste status a recomendação é que a Receptora aguarde a alteração desse status para um dos demais status executando polling na API Recursos (vide recomendações de polling).
    

### Regras de busca na API Recursos em relação aos recursos das API de Câmbio

-   Recomenda-se que a Receptora consulte a API Recursos logo após identificar que o consentimento se encontra autorizado de modo a obter todos as operações de produtos de câmbio consentida pelo cliente e seus respectivos identificadores – lembrando que para câmbio pode não haver nenhuma operação no momento da primeira consulta, e posteriormente novas operações podem aparecer.
    
-   Recomenda-se que a Receptora implemente uma rotina de consulta de novas operações consumindo a API de Recursos de forma periódica. Cabe a Instituição Receptora definir a periodicidade que melhor atende às suas necessidades.
    
-   Recomenda-se que a Receptora, caso obtenha um erro HTTP Status Code 403 - Forbidden nas API de Câmbio avalie o JSON retornado no body da requisição para identificar as informações adicionais referentes ao erro, como o status específico da API Recursos que impede o consumo da informação.
    
-   Recomenda-se que a Receptora consulte a API Recursos caso obtenha um erro na API de produtos de câmbio, de modo a identificar uma possível alteração de status do recurso.
