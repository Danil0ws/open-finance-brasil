# MQD - Fluxo de Validação

Este fluxo representa o processo de validação executado na aplicação MQD Client.

![fluxo\_Validation.png](images/fluxo_Validation.png)

## Passos

f8d47fed-2938-4f22-8acb-3d15ea601d12a5e1e728-f3cf-410b-ba71-509c87ff3f24

Passo

Participante

Descrição

VALIDATOR

O componente de validação carrega regras de validação com base nos JSON Schemas obtidos na configuração

1., 2. e 3.

MESSAGE\_PROCESS\_WORKER

O componente Message Process Worker verifica a Fila e solicita/recebe a lista de tarefas enfileiradas

MESSAGE\_PROCESS\_WORKER

Para cada mensagem encontrada, o Worker envia a mensagem para o componente Validação

VALIDATOR

O componente verifica se o endpoint está na lista de endpoints válidos para a versão configurada

VALIDATOR

O componente desserializa as informações do payload

VALIDATOR

O componente valida o objeto usando o JSON Schema correspondente ao endpoint e versão

VALIDATOR

Retorna a resposta de validação ao Worker (válido/inválido + lista de erros)

MESSAGE\_PROCESS\_WORKER

As informações do resultado são salvas na fila de resultados

wide1800

## Seleção de Versão

O VALIDATOR seleciona o JSON Schema com base na seguinte prioridade:

1.  Se o header `versionHeader` foi informado → usa a versão especificada
    
2.  Se não informado → usa a versão mais recente configurada para aquele endpoint
    

## O que é validado

Aspecto

Validado?

Tipos de dados (string, number, boolean, array, object)

✅ Sim

Campos obrigatórios (required)

✅ Sim

Padrões regex (pattern)

✅ Sim

Limites de tamanho (maxLength, minLength, minItems, maxItems)

✅ Sim

Valores permitidos (enum)

✅ Sim

Propriedades não permitidas (additionalProperties: false)

✅ Sim

Regras de negócio (ex: data vencimento > data atual)

❌ Não

Consistência entre campos

❌ Não

Validação de valores numéricos contra limites de negócio

❌ Não
