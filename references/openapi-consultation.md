# Consulta de Swagger/OpenAPI do Open Finance Brasil

## Objetivo

Orientar a seleção da especificação correta sem duplicar o script de coleta/download já utilizado pelo ambiente. A skill deve consultar primeiro o acervo local em `references/` e usar o repositório oficial somente como fallback.

## Ordem de resolução

| Ordem | Fonte | Uso |
|---|---|---|
| 1 | Arquivo `*.yaml`, `*.yml` ou `*.json` já coletado pelo ambiente | Análise detalhada e reprodutível do contrato |
| 2 | Markdown local da API/versão | Contexto e link OAS registrado no acervo |
| 3 | YAML raw do `all-services-repo` | Versão exata ausente ou confirmação remota |
| 4 | Portal do Desenvolvedor | Cronograma, status, comunicados e regras complementares |

O coletor existente não deve ser substituído nem duplicado dentro desta skill.

## Critérios de resolução local

O índice completo de diretórios está em [`INDEX.md`](INDEX.md). Use-o para resolver nomes exatos antes de montar caminhos manualmente.

| Área | Conteúdo | Prioridade |
|---|---|---:|
| `guide/` | Guias temáticos e complementares; `old/` identifica material histórico | 2 |
| `swagger/` | Contratos/documentos Swagger por API e versão | 1 |
| `informes/` | Informes numerados | 3 |
| `normativos/` | Instruções Normativas e Resoluções BCB | 3 |

Regras:

- Procure por **API + versão + prefixo**, e não apenas por substring do nome.
- Prefira `references/swagger/` para o contrato e `references/guide/` para contexto complementar.
- Não trate `guide/*/old/` como vigente sem confirmação explícita da versão solicitada.
- Preserve nomes com espaços, acentos, colchetes, parênteses, ponto final e **U+200B ZERO WIDTH SPACE**. O caminho visualmente parecido pode ser diferente do caminho real.
- Para links Markdown locais, use o caminho relativo real e faça percent-encoding somente quando a ferramenta de destino exigir.

## Localização no acervo

Faça a busca por API, versão, path ou termo técnico. Os grupos de `guide/` incluem os prefixos `[DC]`, `[DA]`, `[SV]`, `[PC]`, `[EN]`, `[PT]`, `[PCM]` e `[PRÉVIA SET-26]`, além de centenas de tópicos sem prefixo. A lista exata está no [`INDEX.md`](INDEX.md).

Os Markdown técnicos normalmente possuem uma seção `Especificação em OAS 3.0` com um link para o YAML oficial.

## Fallback para o repositório oficial

Repositório: https://github.com/OpenBanking-Brasil/all-services-repo

```text
# Listar pastas de APIs
https://api.github.com/repos/OpenBanking-Brasil/all-services-repo/contents/?ref=main

# Listar versões de uma pasta
https://api.github.com/repos/OpenBanking-Brasil/all-services-repo/contents/<pasta-da-api>?ref=main

# Baixar a versão exata
https://raw.githubusercontent.com/OpenBanking-Brasil/all-services-repo/refs/heads/main/<pasta-da-api>/<versao>.yaml
```

### Exemplo validado

API Contas de Dados Abertos, versão `1.1.0`:

```text
https://raw.githubusercontent.com/OpenBanking-Brasil/all-services-repo/refs/heads/main/api_contas_de_dados_abertos_do_open_finance_brasil/1.1.0.yaml
```

Antes de usar uma versão, valide no YAML:

- `openapi` — versão do padrão OpenAPI;
- `info.version` — versão do contrato;
- `paths` — endpoints publicados;
- `components.schemas` — modelos e regras de dados;
- `securitySchemes`/`security` — requisitos de autenticação, quando presentes.

## Critérios de resposta

Ao explicar um contrato, informe:

1. nome da API e versão exata;
2. origem do conteúdo: caminho local ou URL remota;
3. método e path analisados;
4. parâmetros, headers, body e respostas definidos no OAS;
5. lacunas ou diferenças entre o OAS e a documentação complementar;
6. se a versão é estável, candidata (`rc`) ou histórica (`old`), quando isso estiver indicado.

Nunca misture schemas ou endpoints de versões diferentes. Se o usuário pedir a versão mais atual, confirme no GitHub/Portal antes de responder; não use automaticamente o maior número encontrado no acervo local.
