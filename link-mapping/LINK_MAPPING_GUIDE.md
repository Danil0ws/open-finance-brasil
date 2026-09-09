# 📋 Guia de Mapeamento de Links

Este documento demonstra como os links externos são remapeados para arquivos locais.

## 🔗 Mapeamentos Configurados

### 1. Swagger/OpenAPI

| URL Original | Mapeado Para |
|--------------|--------------|
| `https://openbanking-brasil.github.io/openapi/swagger-apis/accounts/?urls.primaryName=2.5.0` | `data/references/openapi/accounts-2.5.0.md` |
| `https://openbanking-brasil.github.io/openapi/swagger-apis/payments/3.0.0.yml` | `data/references/openapi/payments-3.0.0.md` |
| `https://openbanking-brasil.github.io/openapi/dictionary/getMetrics_v2.csv` | `data/references/openapi/dictionary-getMetrics_v2.md` |

### 2. BCB (Banco Central do Brasil)

| URL Original | Mapeado Para |
|--------------|--------------|
| `https://www.bcb.gov.br/estabilidadefinanceira/exibenormativo?tipo=Resolução%20BCB&numero=1` | `data/references/Resolução_BCB_1.md` |
| `https://www.bcb.gov.br/estabilidadefinanceira/exibenormativo?tipo=Instrução%20Normativa%20BCB&numero=6` | `data/references/Instrução_Normativa_BCB_6.md` |

### 3. Open Finance Atlassian

| URL Original | Mapeado Para |
|--------------|--------------|
| `https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/193658890/Orientações-Contas` | `data/references/guides/Orientações-Contas.md` |
| `https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379230/Glossário` | `data/references/guides/Glossário.md` |

### 4. GitHub Repositórios

| URL Original | Mapeado Para |
|--------------|--------------|
| `https://github.com/OpenBanking-Brasil/all-services-repo/blob/main/api_accounts_-_open_finance_brasil/2.5.0.yaml` | `data/references/openapi/api_accounts_-_open_finance_brasil-2.5.0.yaml.md` |

## ⚠️ Links NÃO Mapeados (Mantidos Externos)

Os seguintes tipos de links **não são remapeados** e permanecem como links externos:

### Especificações Técnicas (RFCs)
- `https://tools.ietf.org/html/rfc4122`
- `https://tools.ietf.org/html/rfc6749`
- `https://datatracker.ietf.org/doc/html/rfc3339`

### Especificações OpenID
- `https://openid.net/specs/openid-connect-core-1_0.html`
- `https://openid.net/specs/openid-financial-api-part-1-1_0.html`

### Exemplos de API
- `https://api.banco.com.br/open-banking/accounts/v1/accounts`
- `https://api.edbank.com.br/openbanking/consents/v1/consents`

### URLs de Desenvolvimento
- `http://localhost:8000/apidocs`

## 📝 Exemplos Práticos

### Antes do Remapeamento

```markdown
# API Accounts

Para mais informações, consulte:
- [Especificação OpenAPI](https://openbanking-brasil.github.io/openapi/swagger-apis/accounts/?urls.primaryName=2.5.0)
- [Download YAML](https://openbanking-brasil.github.io/openapi/swagger-apis/accounts/2.5.0.yml)
- [Dicionário de Dados](https://openbanking-brasil.github.io/openapi/dictionary/getAccounts_v2.csv)
- [Resolução BCB 1](https://www.bcb.gov.br/estabilidadefinanceira/exibenormativo?tipo=Resolução%20BCB&numero=1)
- [RFC 4122](https://tools.ietf.org/html/rfc4122)
```

### Depois do Remapeamento

```markdown
# API Accounts

Para mais informações, consulte:
- [Especificação OpenAPI](data/references/openapi/accounts-2.5.0.md)
- [Download YAML](data/references/openapi/accounts-2.5.0.md)
- [Dicionário de Dados](data/references/openapi/dictionary-getAccounts_v2.md)
- [Resolução BCB 1](data/references/Resolução_BCB_1.md)
- [RFC 4122](https://tools.ietf.org/html/rfc4122)  ← Link externo mantido
```

## 🚀 Como Executar o Remapeamento

### 1. Gerar Mapeamento de Links

```bash
node map-external-links.js
```

Isso cria os arquivos em `data/link-mapping/`:
- `link-mapping.json` - Dados completos
- `link-mapping.md` - Relatório legível
- `link-mapping.csv` - Para importação em outras ferramentas
- `mapping-config.json` - URLs únicas encontradas

### 2. Executar Remapeamento

```bash
node update-links-from-mapping.js
```

Isso:
- Processa todos os arquivos `.md` nos diretórios fonte
- Substitui links externos por caminhos locais
- Gera relatório de mudanças em `data/link-mapping/links-updated-report.md`

### 3. Verificar Resultados

```bash
# Ver relatório de mudanças
cat data/link-mapping/links-updated-report.md

# Ver estatísticas
cat data/link-mapping/mapping-config.json | jq '.statistics'
```

## 📊 Estrutura de Diretórios

```
auto-docs/
├── add/openfinance_markdown/    # Fonte: Guias Open Finance
│   └── *.md
├── bcb/markdown/                # Fonte: Documentação BCB
│   └── *.md
├── swagger/docs/                # Fonte: Swagger Docs
│   └── *.md
├── swagger/all-services-repo/   # Fonte: YAMLs OpenAPI
│   └── *.yaml
├── data/
│   ├── references/              # Destino: Todos os arquivos
│   │   ├── openapi/            # APIs e especificações
│   │   ├── guides/             # Guias e tutoriais
│   │   └── *.md                # Normativos BCB
│   └── link-mapping/           # Relatórios de mapeamento
│       ├── link-mapping.json
│       ├── link-mapping.md
│       ├── mapping-config.json
│       ├── links-updated-report.json
│       └── links-updated-report.md
├── run.js                       # Copia arquivos
├── map-external-links.js        # Mapeia links
└── update-links-from-mapping.js # Atualiza links
```

## ✅ Checklist de Uso

1. [ ] Execute `node run.js` para copiar arquivos para `data/references/`
2. [ ] Execute `node map-external-links.js` para gerar mapeamento
3. [ ] Revise `data/link-mapping/link-mapping.md`
4. [ ] Execute `node update-links-from-mapping.js` para atualizar links
5. [ ] Verifique `data/link-mapping/links-updated-report.md`
6. [ ] Commit das mudanças

## 🔧 Personalização

Para adicionar novos padrões de URL, edite o array `URL_MAPPINGS` em `update-links-from-mapping.js`:

```javascript
{
  pattern: /https?:\/\/seu-dominio\.com\/([\w-]+)/gi,
  resolve: (match, parametro) => `data/references/${parametro}.md`,
}
```

## 📞 Suporte

Para dúvidas sobre o mapeamento, consulte:
- `data/link-mapping/link-mapping.md` - Relatório completo
- `data/link-mapping/mapping-config.json` - URLs encontradas
- Logs de execução dos scripts

---

**Última atualização:** 09/09/2026
**Versão do script:** 1.0.0
