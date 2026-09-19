# Open Finance Brasil — Agentic Skill

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![AgenticSkills](https://img.shields.io/badge/AgenticSkills-Compatible-brightgreen.svg)](https://agenticskills.io)
[![Category](https://img.shields.io/badge/category-API%20Documentation-informational.svg)](https://agenticskills.io/browse)

Skill para agentes de IA consultarem especificações OpenAPI/Swagger, guias técnicos, normativos BCB, informes, segurança (FAPI, DCR, mTLS), certificação e requisitos não-funcionais do **Open Finance Brasil**.

## Instalação

### Todos
```bash
npx skills add Danil0ws/open-finance-brasil -a opencode
```

### Hermes
```bash
hermes skills tap add Danil0ws/open-finance-brasil
```

### Claude Code
```bash
npx skills add https://github.com/danil0ws/open-finance-brasil \
  --skill security-audit
```


### Outros agentes

Qualquer agente compatível com o padrão [AgenticSkills.io](https://agenticskills.io)/[agentskills.io](https://agentskills.io/) pode usar esta skill. Consulte a documentação do seu agente para o caminho correto de instalação.

## O que esta skill faz

Consulta o acervo local completo do Portal do Desenvolvedor do Open Finance Brasil:

- ✅ **Especificações OpenAPI/Swagger** - Endpoints, schemas, request/response
- ✅ **Guias técnicos** - Jornadas, fluxos, UX, casos de erro
- ✅ **Segurança** - FAPI Brasil, DCR, mTLS, certificados, assinatura
- ✅ **Normativos BCB** - Instruções Normativas e Resoluções
- ✅ **Informes oficiais** - Comunicados do ecossistema
- ✅ **Certificação** - Conformance Suite, FVP, testes, homologação, jornadas
- ✅ **Requisitos não-funcionais** - SLA, limites operacionais

## Quando usar

Use esta skill quando:

- 📋 Precisar de endpoints, schemas ou exemplos de request/response de APIs do Open Finance
- 🔐 Consultar requisitos de segurança (FAPI, DCR, consentimento, certificados)
- 📊 Verificar SLA, limites operacionais ou requisitos não-funcionais
- 📝 Precisar de normativos BCB ou informes oficiais
- 🧪 Implementar, integrar, revisar ou depurar código que consome APIs do Open Finance
- ✅ Verificar requisitos de certificação funcional ou de segurança
- 🚀 Preparar para homologação (Conformance Suite, FVP, testes de conformidade)

## Estrutura

```
open-finance-brasil/
├── SKILL.md                          # Skill para agentes (este diretório)
├── README.md                         # Documentação para humanos
├── AGENTS.md                         # Configuração de agentes
├── references/                       # Acervo local completo
│   ├── guides/                       # Guias técnicos (4.696 arquivos)
│   ├── openapi/                      # Especificações OpenAPI (53 arquivos)
│   ├── regulatory/                   # Normativos BCB (267 arquivos)
│   ├── reports/                      # Informes (845 arquivos)
│   ├── certification/                # Conformance Suite & testes (~2.990 arquivos)
│   │   ├── wikis/                    # Procedimentos (133 docs)
│   │   └── work-items/               # Issues & planejamento (~2.810 registros)
│   ├── INDEX.md                      # Índice completo do acervo
│   ├── REFERENCE.md                  # Referência técnica detalhada
│   └── openapi-consultation.md       # Procedimento de fallback GitHub
└── link-mapping/                     # Mapeamento de links externos
```

## Estatísticas do acervo

| Tipo | Quantidade |
|------|------------|
| Total de arquivos | 5.864+ |
| Certificação (wikis + work-items) | ~2.990 |
| Guias técnicos | 4.696 |
| Especificações OpenAPI | 53 |
| Documentos regulatórios | 267 |
| Informes | 845 |
| Links externos mapeados | 12.590 |

## Uso rápido

### Consultar endpoint específico

```
Qual o endpoint para criar consentimento no Open Finance?
Qual o schema de request para iniciação de pagamento Pix?
```

### Verificar requisitos de segurança

```
Quais os requisitos de mTLS para APIs do Open Finance?
Como funciona o DCR no Open Finance Brasil?
```

### Consultar normativos

```
O que diz a Instrução Normativa BCB 170 sobre Open Finance?
Quais os prazos da Resolução BCB 135?
```

## Fontes oficiais

| Recurso | URL |
|---------|-----|
| Portal do Desenvolvedor | https://openfinancebrasil.atlassian.net/wiki/spaces/OF |
| Repositório de Especificações | https://github.com/OpenBanking-Brasil/all-services-repo |
| Estrutura de Governança | https://openfinancebrasil.org.br/governanca/ |
| Repositório de Certificações | https://gitlab.com/raidiam-conformance/open-finance/certification |

## Compatibilidade

Esta skill segue o padrão [AgenticSkills.io](https://agenticskills.io)/[agentskills.io](https://agentskills.io/)  e funciona em:

- ✅ Claude Code (Anthropic)
- ✅ OpenAI Codex
- ✅ Cursor
- ✅ Gemini CLI (Google)
- ✅ GitHub Copilot
- ✅ Windsurf
- ✅ Roo Code
- ✅ Amp
- ✅ Goose
- ✅ Qualquer agente compatível com SKILL.md

## Licença

Apache License 2.0

## Contribuindo

Contribuições são bem-vindas! Esta skill é mantida pela comunidade Open Finance Brasil.

---

**Última atualização:** 09/09/2026 | **Versão:** 2.1.0 | **Fonte:** Portal do Desenvolvedor do Open Finance Brasil
