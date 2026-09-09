# Convenções de Payload

Esta seção do padrão descreve as estruturas padrões de requisição e resposta para todos os _endpoints_ das APIs, assim como as convenções de nomenclatura para os atributos.

## **Estrutura de requisição**

Cada requisição deve ser um objeto JSON contendo um objeto `data` para armazenar os dados primários da requisição.

No mesmo nível do objeto `data`, poderá existir um objeto `meta` se assim for especificado pelo _endpoint_. O objeto `meta` é usado para fornecer informações adicionais ao _endpoint_, como parâmetros de paginação, contagens de paginação ou outros propósitos complementares ao funcionamento da API.

A definição do conteúdo para o objeto `data` será definida separadamente para cada _endpoint_.

> **Estrutura da requisição**

## **Estrutura de resposta**

Cada endpoint retornará um objeto JSON contendo os atributos abaixo.

-   Se a resposta for bem-sucedida (200 OK), o objeto JSON irá conter:
    
    -   obrigatoriamente um objeto `data`;
        
    -   obrigatoriamente um objeto `links`;
        
    -   opcionalmente um objeto `meta`, se necessário pela definição do endpoint requisitado.
        
-   Se a resposta for malsucedida (não 200 OK), o objeto JSON poderá conter:
    
    -   um objeto `errors` (conforme a definição específica do endpoint).
        

A definição do conteúdo para os objetos `data` e `meta` será definida separadamente para cada _endpoint_.

O objeto `links` irá conter hypermedia (referências para recursos relacionados) para outros recursos da API requisitada.

O objeto de `links` sempre irá conter o atributo `self` que irá apontar para a URI da solicitação atual.

-   O objeto `errors` será um array de zero ou mais objetos. Os atributos deste objeto serão os descritos abaixo:
    
    -   obrigatoriamente o atributo `code` contendo um código de erro específico do _endpoint_;
        
    -   obrigatoriamente o atributo `title` contendo um título legível por humanos do erro deste erro específico;
        
    -   obrigatoriamente o atributo `detail` contendo uma descrição legível por humanos deste erro específico;
        
    -   opcionalmente o objeto `meta` contendo dados adicionais sobre o _endpoint_ que seja relevante para o erro.
        

> **Estrutura de resposta**

> **Estrutura de resposta de erros**

## **Convenções de nomenclatura de atributos**

### Caracteres válidos em nomes de atributos

Todos os nomes de objetos e atributos definidos nos objetos JSON de requisição e resposta devem ser nomeados seguindo o padrão camelCase, tendo seu nome composto apenas por letras (a-z, A-Z) e números (0-9).

Qualquer outro caractere não deve ser usado nos nomes dos objetos e atributos, com exceção do caractere `-` (hífen), que poderá ser utilizado apenas conforme descrito na seção Extensibilidade.

### Estilo de nomeação de atributos

Os nomes dos objetos e atributos devem ser nomes significativos e em língua inglesa. Quando houver diferença entre inglês americano e inglês britânico no termo a ser utilizado, deverá ser utilizado o termo em inglês britânico. P. ex: utilizar o termo _Post Code_ (Reino Unido) ao invés de _Zip Code_ (Estados Unidos).

_Arrays_ devem ser nomeados no plural. Demais atributos deverão ser nomeados no singular.

### Convenções de propriedade dos atributos

#### Tipos de dados dos atributos

Cada atributo deverá estar associado a um tipo de dado. A lista de tipos de dados válidos está definida na seção tipos de dados comuns. Se um tipo de dado personalizado é necessário para um atributo, o mesmo deverá ser classificado como uma string com uma descrição clara de como o valor da propriedade deve ser interpretado.
