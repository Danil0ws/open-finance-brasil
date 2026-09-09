# Informações Gerais - [DC] Câmbio - 1.1.0

**Visão Geral**

API de informações de operações de Câmbio Open Finance Brasil – Fase 4. API que retorna informações de operações de Câmbio realizadas nas instituições transmissoras por seus clientes, incluindo dados como informações da operação contratada, valor da operação em moeda nacional e moeda estrangeira, classificação da operação, forma de entrega, VET e, quando aplicável, valor a liquidar.

## **Product List:** (GET /exchanges/v1/operations)

**Visão Geral**

Obtém a lista de operações de Câmbio mantidas pelo cliente na instituição transmissora e para as quais ele tenha fornecido consentimento.

**Visão de alto de nível das estruturas de dados**

![image-20230530-162058.png](images/image-20230530-162058.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230530-162148.png](images/image-20230530-162148.png)

-   DER Lógico
    

![image-20230530-162216.png](images/image-20230530-162216.png)

## **Product Identification:** (GET /exchanges/v1/operations/{operationId})

**Visão Geral**

Obtém os dados da operação de Câmbio identificada por operationId.

**Visão de alto de nível das estruturas de dados**

![image-20230530-162300.png](images/image-20230530-162300.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230530-162323.png](images/image-20230530-162323.png)

-   DER Lógico
    

![image-20230530-162413.png](images/image-20230530-162413.png)

## **Events:** (GET /exchanges/v1/operations/{operationId}/events)

**Visão Geral**

Obtém os dados dos eventos da operação de Câmbio identificada por operationId.

**Visão de alto de nível das estruturas de dados**

![image-20230530-162447.png](images/image-20230530-162447.png)

**DER - Diagramas de Entidade e Relacionamento**

-   DER Conceitual
    

![image-20230530-162509.png](images/image-20230530-162509.png)

-   DER Lógico
    

![image-20230530-162605.png](images/image-20230530-162605.png)
