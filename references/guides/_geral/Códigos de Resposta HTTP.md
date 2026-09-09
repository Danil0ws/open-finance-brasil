# Códigos de Resposta HTTP

## Códigos de resposta HTTP

Os códigos de resposta HTTP devem ser utilizados conforme tabela mais abaixo. Observação: com a implementação do cadastro por _endpoint_ no diretório de participantes e conforme orientação do regulador, as instituições participantes NÃO DEVEM cadastrar endpoints de produtos ou serviços que não ofertem. Neste caso específico - a consulta em um endpoint não cadastrado - o status code esperado na resposta é o _404 - NOT FOUND_.

### Códigos

Situação

Código HTTP

Notas

POST

GET

DELETE

PATCH

Consulta concluída com sucesso.

200 OK.

No caso de POST, retornar 200 apenas quando não acarretar alteração de recurso.

Nos casos em que a resposta da requisição não tem informações para retornar e o objeto "data" seja do tipo "array", a resposta deve ser uma lista vazia, considerando que a propriedade minLength seja igual a zero.

Sim

Sim

Não

Sim

Execução normal. A solicitação foi bem sucedida.

201 Created.

A operação resulta na criação de um novo recurso.

Sim

Não

Não

Não

Requisição aceita para processamento posterior

202 Accepted

Especificado para o Webhook e na consulta da API Recursos​.

Sim

Sim

Não

Não

Operação de exclusão concluída com sucesso.

204 No Content.

Não

Não

Sim

Não

A resposta não foi modificada desde a última chamada

304 Not Modified

Não

Sim

Não

Não

A requisição foi malformada, omitindo atributos obrigatórios, seja no _payload_ ou através de atributos na URL.

400 Bad Request.

A operação solicitada não será realizada.

Sim

Sim

Sim

Sim

Cabeçalho de autenticação ausente/inválido ou _token_ inválido.

401 Unauthorized.

A operação foi recusada devido a um problema de autenticação.

Sim

Sim

Sim

Sim

O _token_ tem escopo incorreto ou uma política de segurança foi violada.

403 Forbidden.

A operação foi recusada devido a falta de permissão para execução.

Sim

Sim

Sim

Sim

O recurso solicitado não existe ou não foi implementado.

404 Not Found.

Sim

Sim

Sim

Sim

O consumidor tentou acessar o recurso com um método não suportado.

405 Method Not Allowed.

Sim

Sim

Sim

Sim

A solicitação continha um cabeçalho Accept diferente dos tipos de mídia permitidos ou um conjunto de caracteres diferente de UTF-8.

406 Not Acceptable.

Sim

Sim

Sim

Sim

Indica que o recurso não está mais disponível.

410 Gone.

Sim

Sim

Sim

Não

A operação foi recusada porque o payload está em um formato não suportado pelo endpoint.

415 Unsupported Media Type.

Sim

Não

Não

Não

A solicitação foi bem formada, mas não pôde ser processada devido à lógica de negócios específica da solicitação.

422 Unprocessable Entity.

Se aplicável ao _endpoint_, espera-se que esse erro resulte em um _payload_ de erro.

Sim

Sim

Não

Sim

A operação foi recusada, pois muitas solicitações foram feitas dentro de um determinado período ou o limite global de requisições concorrentes foi atingido.

429 Too Many Requests.

A limitação é um Requisito Não Funcional. O titular dos dados deve incluir o cabeçalho `Retry-After` na resposta indicando quanto tempo o consumidor deve esperar antes de tentar novamente a operação.

Sim

Sim

Sim

Sim

Ocorreu um erro no _gateway_ da API ou no microsserviço.

500 Internal Server Error.

A operação falhou.

Sim

Sim

Sim

Sim

O serviço está indisponível no momento.

503 Service Unavailable.

Sim

Sim

Sim

Sim

O servidor não pôde responder em tempo hábil.

504 Gateway Timeout.

Retornado se ocorreu um tempo limite, mas um reenvio da solicitação original é viável (caso contrário, use 500 _Internal Server Error_).

Sim

Sim

Sim

Sim
