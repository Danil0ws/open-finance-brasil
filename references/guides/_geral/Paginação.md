# Paginação

Cada recurso de cada API pode possuir ou não paginação, caso a quantidade de registros retornados justifique a mesma. A paginação estará disponível e deverá funcionar independente se o recurso permite filtros por _query_ ou POST. Isso é, filtros e paginação são aplicados de forma independente.

## **Parâmetros de Requisição**

Quando existir paginação para o recurso deverão ser utilizados os parâmetros de query abaixo para a navegação dos resultados:

Parâmetro

Descrição

Valor Padrão

page

Número da página que está sendo requisitada (o valor da primeira página é 1).

1

page-size

Quantidade total de registros por páginas.

25

 **O valor padrão será assumido sempre que o parâmetro não estiver preenchido ou estiver nulo.**

> **Exemplo de query com paginação**

wide1800

### **Atributos de Resposta**

Além dos dados requisitados, as respostas paginadas também terão em sua estrutura dois objetos adicionais que incluirão parâmetros para facilitar a navegação das páginas:  

> **Exemplo de paginação**
> 
> **Apenas uma página**

wide1800

### **Links**

Os `links` devem sempre ser validados de acordo com o pattern publicado no swagger.

Quando preenchidos devem ter a mesma estrutura (schema, host, api, versão e recurso) do que esta sendo paginado.

No objeto `links`, serão retornadas hypermedia (referências para os recursos relacionados) de paginação conforme parâmetros abaixo:

Parâmetro

Descrição

Restrição

first

A URI para requisitar a primeira página.

Obrigatório se a resposta não for a primeira página.

last

A URI para requisitar a última página.

Obrigatório se a resposta não for a última página e quando este campo for especificado no endpoint.

prev

A URI para requisitar a página anterior.

Obrigatório quando houver página anterior. Não deve ser enviado quando for a primeira página.

next

A URI para requisitar a próxima página.

Obrigatório quando houver página posterior. Não deve ser enviado quando for a última página.

self

A URI para requisitar a própria página

-   Quando chamado o método GET deverá retornar o link para o próprio recurso consultado
    
-   Quando chamado o método POST deverá retornar o link para o recurso criado
    
-   Quando chamado método PATCH deverá retornar o link para o recurso alterado
    
-   Quando chamado o método GET com retornos paginados, o self deve refletir o link para o próprio recurso consultado e o atributo page-size que consta como parâmetro na url deve refletir o tamanho de página efetivamente aplicado pelo servidor
    

> **Primeira página**

wide1800

## **Meta**

No objeto `meta`, serão retornadas informações sobre o total de registros disponíveis

Parâmetro

Descrição

Restrição

totalRecords

O número total de registros da requisição.

Este atributo é obrigatório.

totalPages

O número total de páginas da requisição.

Este atributo é obrigatório. Se não possuir nenhum registro o valor deve ser 0.

 **Para cada um desses atributos o tamanho da página especificado na requisição deverá ser utilizado para o cálculo dos valores.**

> **Última Página**

wide1800

## **Regras Adicionais**

-   O tamanho máximo da página (`page-size`) é `1000` registros para qualquer endpoint (a menos que na API esteja especificado outros valores).
    
-   Caso a instituição transmissora/detentora defina um tamanho máximo de página (`page-size`) inferior, se for requisitado uma quantidade de registros maior do que seu limite operacional, e desde que o valor esteja de acordo o tamanho máximo permitido pela API, esta deverá responder entregando os dados e utilizando o `page-size` do seu limite operacional definido.
    
-   A instituição transmissora/detentora deve realizar os ajustes de paginação antes de efetivar a consulta:
    
    -   Ex: Ao solicitar a segunda pagina `1000` registros, para uma instituição que trabalha com max size `800`, a transmissora deve retornar os itens de `801` a `1600`.
        
-   A instituição transmissora/detentora pode definir um tamanho máximo da página (`page-size`) inferior ao tamanho máximo permitido pela API, caso entenda necessário diminuir o limite para atender o SLA de resposta:
    
    -   Para as APIs de Dados Cadastrais e Transacionais, o comportamento esperado da transmissora/detentora é que o page size mínimo é 25 e o máximo é 1000, exceções se aplicam a primeira página, quando for única, e a última página.
        
        -   Exemplo: A receptora solicita 5 registros por página, entretanto, a transmissora possui 47 registros. Pelo comportamento descrito, a transmissora retornará 25 registros na primeira página de 22 registros na segunda.
            
-   Para reduzir a quantidade de requisições para endpoints que possuem paginação, recomenda-se que a transmissora responda com o máximo de itens possíveis na página, porém, respeitando o SLA definido para o endpoint e o tamanho máximo da página.
    
-   Caso o valor informado em page exceda o total de páginas existentes para aquele conjunto de resultados, a API deve responder HTTP 422 unprocessable entity, com o erro PAGE\_NOT\_FOUND, exceto na primeira página, pois sempre existe.
