---
name: open-finance-brasil
description: Consulte especificações OpenAPI/Swagger, guias técnicos, normativos BCB, informes, segurança (FAPI, DCR, mTLS), certificação e requisitos não-funcionais do Open Finance Brasil. Use quando precisar de endpoints, schemas, consentimento, jornada, SLA, homologação, integração ou implementação de APIs financeiras brasileiras.
license: Apache-2.0
compatibility: Funciona em qualquer agente compatível com SKILL.md (Claude Code, Codex, Cursor, Gemini CLI, Windsurf, etc). Requer acesso ao diretório references/ local.
metadata:
  author: Danil0Ws
  version: "2.1.0"
  category: api-documentation
  tags: open-finance, open-banking, brazil, api, swagger, openapi, fapi, bcb, banking, certification, conformance-suite, homologacao, fvp
  repository: https://github.com/Danil0Ws/open-finance-brasil
  portal: https://openfinancebrasil.atlassian.net/wiki/spaces/OF
  certification-wiki: https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis
---

# Open Finance Brasil — Skill de Referência

Skill para consultar o acervo local do **Portal do Desenvolvedor do Open Finance Brasil**, regulamentado pelo Banco Central do Brasil.

## Como usar esta skill

1. **Classifique a solicitação**: contrato OAS/Swagger, segurança, jornada, certificação, diretriz operacional, informe ou normativo
2. **Consulte o índice**: Use [`references/INDEX.md`](references/INDEX.md) para localizar o domínio correto
3. **Prefira fontes locais**: Leia primeiro arquivos em `references/guides/`, `references/openapi/` e `references/regulatory/`
4. **Preserve versões exatas**: Nunca substitua automaticamente versões `rc`, `beta` ou `old` pela versão vigente
5. **Valide na fonte oficial**: Para cronogramas, comunicados ou vigência normativa, consulte o Portal ou GitHub oficial

## Estrutura do acervo local

O diretório `references/` contém o acervo completo:

| Diretório | Conteúdo | Quando usar |
|-----------|----------|-------------|
| `references/guides/` | Guias técnicos, jornadas, segurança, UX, certificação | Contexto de negócio, fluxos, regras |
| `references/openapi/` | Especificações OpenAPI/Swagger (178 arquivos) | Endpoints, schemas, request/response |
| `references/regulatory/` | Instruções Normativas e Resoluções BCB (1.113 arquivos) | Normativos, regulação, compliance |
| `references/reports/` | Informes numerados do ecossistema | Comunicados oficiais |
| `references/certification/` | Wiki de certificação, Conformance Suite, testes e homologação | Procedimentos de certificação, testes, FVP, CIBA, portabilidade |
| `references/INDEX.md` | Inventário completo (522 diretórios) | Navegação e descoberta |

**Total**: 5.864+ arquivos markdown organizados em 357+ subpastas, incluindo ~2.990 arquivos de certificação.

## Fluxo para consultar APIs (OpenAPI/Swagger)

Quando precisar de endpoint, request, response, parâmetro ou schema:

1. **Identifique API e versão** solicitadas (não complete a versão por suposição)
2. **Busque no acervo local**: `references/openapi/[pasta-api]/[versao].yaml` ou `references/guides/[API]/`
3. **Use fallback GitHub** se não existir localmente: [procedimento detalhado](references/openapi-consultation.md)
4. **Informe fonte e versão** na resposta (arquivo local ou URL do repositório oficial)

### Fallback para repositório oficial

```
Repositório: https://github.com/OpenBanking-Brasil/all-services-repo
Raw file: https://raw.githubusercontent.com/OpenBanking-Brasil/all-services-repo/refs/heads/main/<pasta-api>/<versao>.yaml
API listing: https://api.github.com/repos/OpenBanking-Brasil/all-services-repo/contents/<pasta-api>?ref=main
```

Exemplo - **API Contas de Dados Abertos v1.1.0**:
```text
https://raw.githubusercontent.com/OpenBanking-Brasil/all-services-repo/refs/heads/main/api_contas_de_dados_abertos_do_open_finance_brasil/1.1.0.yaml
```

## Certificação e Conformidade (Novo)

Para consultas sobre **certificação**, **testes de conformidade** e **homologação**:

### Wikis de Certificação (~180 documentos)

A pasta `references/certification/wikis/` contém:

- **FVP (Functional Verification Process)**: Procedimentos de teste automático (PT/EN)
  - Automática (diária, sem jornada do usuário)
  - Manual Imediata (portabilidade, pagamentos, inscrições)
  - Manual Agendada (pagamentos recorrentes, etc.)
  - Jornada Otimizada (Pix, consentimentos)

- **CIBA (Client Initiated Backchannel Authentication)**: Fluxo de autenticação
  - Dados de cliente
  - Configurações de teste

- **Conformance Suite**: Instruções de execução local
  - Requisitos (Java, Maven, Docker)
  - Setup com Docker Compose ou IDE
  - Debugging e desenvolvimento

- **Módulos de Teste**: Portabilidade, Pagamentos, Consentimentos, Diretório, DCR, etc.
  - Especificações de testes por versão de API
  - Casos de falha e validações
  - Release notes com histórico de mudanças

### Work Items (~2.810 registros)

Rastreadores de trabalho, issues e planejamento de testes.

### Quando usar certificação
- Preparar para certificação de produto ou serviço
- Entender a Conformance Suite e executar localmente
- Consultar mudanças recentes em testes (breaking changes, novas verificações)
- Validar compatibilidade com versões específicas de APIs
- Preparar testes manuais ou automáticos de jornada do usuário

## Análise de especificação OAS

Siga esta ordem para explicar uma API:

1. `info` - título, versão, descrição, contato
2. `servers` - URL base e ambiente
3. `tags` - agrupamento funcional
4. `paths` - métodos, parâmetros, request/response, códigos de erro
5. `components.schemas` - modelos, enums, formatos, relacionamentos
6. `components.securitySchemes` - autenticação, requisitos de segurança
7. Extensões Open Finance - idempotência, paginação, assinatura, headers regulatórios, certificação requerida

## Fontes oficiais

| Recurso | URL |
|---------|-----|
| Portal do Desenvolvedor | https://openfinancebrasil.atlassian.net/wiki/spaces/OF |
| Repositório de Especificações | https://github.com/OpenBanking-Brasil/all-services-repo |
| Estrutura de Governança | https://openfinancebrasil.org.br/governanca/ |

## Regras de referência

- **Referência local** = snapshot versionado, útil para respostas reprodutíveis
- **Especificação remota** = arquivo oficial no GitHub, use para confirmar versão/schema ausente
- **Fonte normativa viva** = Portal/Confluence, necessária para cronogramas e comunicados atuais
- **Versões históricas** (`old/`, `beta`, `rc`, `Legada`) = podem não ser vigentes, confirme antes de usar

## Referências detalhadas

Para informações mais profundas, consulte:

- [REFERÊNCIA COMPLETA](references/REFERENCE.md) - Mapa detalhado do Portal do Desenvolvedor
- [CERTIFICAÇÃO](references/CERTIFICATION.md) - Documentação especializada sobre conformidade e testes (novo)
- [CONSULTA OPENAPI](references/openapi-consultation.md) - Procedimento completo de fallback GitHub
- [ÍNDICE LOCAL](references/INDEX.md) - Inventário exaustivo de todos os diretórios
- [CERTIFICATION INDEX](references/certification/wikis/) - Wikis de certificação (133 docs)
- [WORK ITEMS](references/certification/work-items/) - Rastreadores (~2.810 registros)

## Fora do escopo

- **Regras societárias de adesão**: Direcione para https://openfinancebrasil.org.br/governanca/
- **Suporte a incidentes de produção**: Direcione para Service Desk oficial
- **Acesso a Jira/Confluence privado**: A skill fornece snapshots locais (wikis de certificação); para issues atuais, consulte o repositório GitLab oficial da Conformance Suite
