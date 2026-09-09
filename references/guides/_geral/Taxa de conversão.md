# Taxa de conversão

## item 2.6.2Purple

# Controle de versão

**Versão**

**Data**

**Resumo das alterações**

1

Versão inicial

2

Versão inicial – compilação das três taxas (Dados, Pagamentos e Vínculo), fontes informacionais (Planilha e PCM) e estados de conformidade (Conforme, Tolerância e Diagnóstico)

# Introdução e Objetivos

Esta métrica tem como propósito monitorar a eficiência das jornadas de compartilhamento de dados, iniciação de pagamentos e criação de vínculo dentro do ecossistema do Open Finance. O objetivo é assegurar padrões de conversão adequados, refletindo a qualidade e a eficácia dessas jornadas na facilitação de operações seguras e eficientes entre as instituições participantes e seus clientes.

# Sobre a Métrica

Esta métrica foca em três áreas principais, cada uma representando uma jornada distinta para o cliente:

I. Compartilhamento de dados: A Taxa de Criação de Consentimento de Dados de Clientes é calculada com base na proporção de consentimentos autorizados com sucesso em relação ao número de solicitações válidas de criação de consentimentos, direcionadas para a instituição transmissora de dados.

II. Iniciação de Transação de Pagamento: A Taxa de Criação de Consentimento de Pagamentos é calculada com base na proporção de consentimentos autorizados com sucesso em relação ao número de solicitações válidas de criação de consentimentos, direcionadas para a instituição detentora.

III. Vínculo: A Taxa de Criação de Vínculo é calculada pela quantidade de vínculos autorizados em relação ao volume de solicitações válidas de criação de vínculo, direcionadas para a instituição detentora de conta.

As três métricas acima são comparadas a partir de uma meta calculada a partir da performance do ecossistema (Interpretação dos Resultados)

Para mais detalhes acesse a página: 2.6.2 - Taxa de Conversão - Área do Desenvolvedor - Open Finance Brasil - Área do Desenvolvedor

# Critérios de Exclusão do Denominador (Solicitações válidas)

O denominador da taxa de conversão aplica três critérios obrigatórios de exclusão, independentes do produto ou da fonte informacional utilizada. Esses critérios garantem que somente as jornadas válidas — reportadas por ambas as pontas, processadas com sucesso e originadas por clientes legítimos da instituição — sejam computadas no cálculo.

1.  **Chamadas não pareadas (client e server)**
    

São excluídas do denominador as chamadas que não apresentam pareamento entre as pontas client (instituição iniciadora ou receptora) e server (instituição transmissora ou detentora de conta). O pareamento exige que ambas as instituições envolvidas na jornada reportem o mesmo evento.

Quando apenas uma das pontas reporta a ocorrência — seja por falha no envio, descarte da informação ou indisponibilidade temporária — a chamada é considerada não pareada e não entra no cálculo, pois ambas as partes possuem obrigações de reporte do fluxo, necessárias para garantir a integridade da informação.

2.  **Status code diferente de 2xx**
    

Dentre as chamadas pareadas, somente são computadas aquelas cujo status code HTTP pertence à família 2xx (200, 201, 204 e demais), indicando que a requisição foi processada com sucesso pela instituição.

Requisições cujo status code pertence às famílias 4xx (erros de cliente), 5xx (erros de servidor) ou demais respostas fora da faixa de sucesso são excluídas do denominador, pois indicam falhas técnicas, autorizações inválidas ou indisponibilidade que não representam uma jornada efetiva do cliente.

3.  **Exclusão de não clientes (DropReason)**
    

Excluem-se do denominador as ocorrências em que o CPF/CNPJ redirecionado não é cliente da instituição, identificadas por meio do campo DropReason. São computadas apenas as ocorrências cujo DropReason é igual a NONE ou NULL, conforme tabela abaixo:

**DropReason**

**Significado**

**Inclui no denominador?**

**NONE**

Cliente válido da instituição (sem descarte)

**✅  Sim**

**NULL**

Informação não reportada (tratado como cliente válido)

**✅  Sim**

**Outro valor**

Não cliente (CPF/CNPJ sem vínculo com a instituição)

**❌  Não**

Essa exclusão é fundamental para que o indicador reflita apenas a eficiência da jornada para o público-alvo correto. Usuários redirecionados que não possuem vínculo com a instituição não têm como concluir o fluxo de autenticação, e sua inclusão no denominador distorceria o resultado.

# Período de apuração

As taxas são apuradas mensalmente, considerando as semanas de sábado a sexta-feira. A semana é considerada para o mês de referência caso a sexta-feira se encontre naquele mês.

![image-20260624-141330.png](images/image-20260624-141330.png)

# Fontes Informacionais

A apuração das taxas utiliza duas fontes informacionais distintas, a depender do produto e do conglomerado da instituição participante:

-   **Planilha autoreportada:** arquivos enviados diretamente pelas próprias instituições, contendo os volumes apurados internamente de solicitações e autorizações.
    

-   **PCM (Plataforma de Coleta de Métricas):** plataforma centralizada da Estrutura de Governança do Open Finance que coleta as métricas a partir das chamadas de API entre os participantes.
    

Para os produtos de Dados de Clientes e de Pagamentos, a fonte informacional adotada na apuração da taxa varia conforme o conglomerado: os _19 maiores conglomerados**\***_ são monitorados pela Planilha autoreportada, enquanto os demais pela PCM.

O cálculo da meta para esses dois produtos, contudo, é realizado exclusivamente a partir das Planilhas autoreportadas, tomando como base as taxas dos conglomerados que dispõem dessa fonte.

Para o produto Vínculo, tanto a apuração da taxa quanto o cálculo da meta são realizados integralmente via PCM, sem uso de Planilhas autoreportadas, independentemente do conglomerado.

_\*19 maiores conglomerados: BMG, BTG, Banco do Brasil, Bradesco, C6, Caixa, Digio, Inter, Itaú, Mercado Pago, Neon, Nubank, PagBank, Pan, PicPay, Santander, Sicoob, Sicredi, XP_

## Quadro Consolidado de Fontes Informacionais 

**Produto**

**Conglomerado**

**Fonte da Taxa**

**Fonte da Meta**

**Dados de Clientes**

19 conglomerados

**Planilha**

**Planilha**

**Dados de Clientes**

Demais conglomerados

**PCM**

**Planilha**

**Pagamentos**

19 conglomerados

**Planilha**

**Planilha**

**Pagamentos**

Demais conglomerados

**PCM**

**Planilha**

**Vínculo**

Todos os conglomerados

**PCM**

**PCM**

# Interpretação dos Resultados (Meta)

Para compreender a taxa de conversão no contexto do Open Finance, utilizam-se os dados fornecidos pelas instituições participantes ao longo de três meses, incluindo o mês de referência.

## Cálculo do Top 3

A meta é calculada a partir da seguinte logica:

-   Calcula-se a taxa de conversão em uma janela de 3 meses incluindo o mês de referência para cada conglomerado;
    

-   Dentre os 19 maiores conglomerados, identificam-se as instituições com as três maiores taxas e calcula-se a taxa ponderada para a meta;
    

-   Esse valor serve de referência para a definição dos demais limiares.
    

## Cálculo da Taxa de Tolerância

A Taxa de Tolerância é o piso de conformidade. Instituições cuja taxa de conversão se mantiver acima dela são consideradas conformes. Ela é obtida tomando-se 80% da Taxa Top 3 e subtraindo-se 3 pontos percentuais, para acomodar pequenas variações operacionais:

**Taxa de Tolerância = (80% × Taxa Top 3) − 3 p.p.**

## Cálculo da Taxa de Diagnóstico

A Taxa de Diagnóstico é o limiar inferior de severidade. Se a taxa de conversão de uma instituição cair abaixo dela, será necessária uma avaliação independente por empresa especializada para diagnosticar e corrigir os problemas subjacentes da jornada. Ela corresponde a 60% do valor base da Taxa Top 3 (80% da Taxa Top 3):

**Taxa de Diagnóstico = 60% × (80% × Taxa Top 3) = 48% × Taxa Top 3**

## Limiares estabelecidos

Com base nas duas taxas calculadas acima, a instituição participante pode se enquadrar em um de três estados de conformidade:

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

## Levantamento dos Números (Operacional)

O objetivo dessa seção é explicar o cálculo das métricas de maneira operacional, com exemplos para cada uma das fontes de dados utilizadas.

## PCM

As regras utilizadas como filtro para numerador e denominador estão no bloco de código abaixo:

 **Vínculo**

 **Denominador Vínculo:**

wide1011 serverorgid -- Tratamento de possíveis erros.\]\]>

**Numerador Vínculo:**

wide1011 serverorgid AND statuscode LIKE '2%' -- Seção "Critérios de Exclusão do Denominador (Solicitações válidas)" AND additionalinfo\_enrollmentid IS NOT NULL -- Chave de Cruzamento para Vínculo AND endpoint = '/open-banking/enrollments/v2/enrollments/{enrollmentId}/fido-registration'\]\]>

### **Dados de Clientes** 

**Denominador Dados de Clientes:**

wide1011 serverorgid -- Tratamento de possíveis erros. \]\]>

 **Numerador Dados de Clientes:**

wide1011 serverorgid AND statuscode LIKE '2%' -- Seção "Critérios de Exclusão do Denominador (Solicitações válidas)" AND additionalinfo\_consentid IS NOT NULL -- Chave de Cruzamento para Dados de Clientes AND endpoint = '/token' AND additionalinfo\_granttype = 'AUTHORIZATION\_CODE' AND ( is\_missing\_security = 1 AND endpoint = '/open-banking/resources/v3/resources' – Dados de Clientes ) -- Busca por uso de Negócio\]\]>

### **Pagamentos**

**Denominador de Pagamentos:**

wide1011 'FIDO\_FLOW' OR COALESCE(additionalinfo\_authorisationflowintent, additionalinfo\_authorisationflow) IS NULL ) AND clientorgid <> serverorgid -- Tratamento de possíveis erros.\]\]>

**Numerador de Pagamentos:**

wide1011 serverorgid AND additionalinfo\_consentid IS NOT NULL -- Chave de Cruzamento para Pagamentos AND ( is\_in\_security = 1 AND endpoint = '/token' AND additionalinfo\_granttype = 'AUTHORIZATION\_CODE' ) -- Busca para Conversão de Pagamentos AND ( is\_missing\_security = 1 AND endpoint IN ( '/open-banking/payments/v4/pix/payments' -- Pagamentos ) -- Busca por uso de Negócio\]\]>

## Planilhas

As colunas utilizadas nas planilhas estão dispostas nas imagens abaixo, com o produto de acordo com a planilha:

 **Planilha:** Fase 2 e 4b – Dados de Clientes

**Aba:** Consentimento Transmissor

![image-20260615-202926.png](images/image-20260615-202926.png)

**Planilha:** Fase 3 – Pagamentos

**Aba:** Funil API Pagam

![image-20260615-203100.png](images/image-20260615-203100.png)

# Referências Normativas

-   Instrução Normativa BCB nº 706, de 29 de janeiro de 2026 – Manual de Monitoramento do Open Finance, versão 3.0
    

-   Resolução Conjunta nº 1, de 4 de maio de 2020 – Disposições gerais sobre implementação do Open Finance
    

-   Resolução BCB nº 32, de 29 de outubro de 2020 – Requisitos técnicos e procedimentos operacionais do Open Finance
    

-   Guia de Itens Monitorados – Taxa de Conversão (Área do Desenvolvedor do Open Finance Brasil, item 2.6.2)
