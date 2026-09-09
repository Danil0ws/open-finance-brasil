# Open Finance Brasil — Referência Técnica Completa

Este documento contém o mapa detalhado do Portal do Desenvolvedor e informações técnicas complementares para uso avançado da skill.

## Mapa do Portal do Desenvolvedor

| Seção | Conteúdo | URL Path |
|-------|----------|----------|
| Comunicados & Eventos Técnicos | Avisos oficiais e mudanças de cronograma | `/wiki/spaces/OF/pages/17367092` |
| Especificações de APIs | Versões atuais/candidatas por grupo | `/wiki/spaces/OF/pages/17367659` |
| Especificações de Integração | Padrões de integração entre participantes | `/wiki/spaces/OF/pages/17377794` |
| Segurança | FAPI Brasil, DCR, certificados e mTLS | `/wiki/spaces/OF/pages/240648193` |
| Diretrizes Técnicas e Operacionais | Limites, versionamento e diretrizes | `/wiki/spaces/OF/pages/17378512` |
| Certificação de Conformidade | Certificação funcional e de segurança | `/wiki/spaces/OF/pages/17378880` |
| Requisitos não Funcionais | SLA e frequência dos endpoints | `/wiki/spaces/OF/pages/17956981` |
| Problemas | Erros e problemas conhecidos | `/wiki/spaces/OF/pages/17379123` |
| Suporte | Service Desk e canais de dúvida | `/wiki/spaces/OF/pages/17379146` |
| Histórico de Alterações | Changelog do portal | `/wiki/spaces/OF/pages/17379274` |

**URL Base:** `https://openfinancebrasil.atlassian.net`

## Mapa Completo do Acervo Local

### `references/guides/`

Contém os guias temáticos do Portal, documentos técnicos, jornadas, diagramas, casos de erro, UX, segurança, certificação, testes e histórico.

**358 tópicos de primeiro nível** e **134 subpastas `old/`** organizados em:

#### APIs e Domínios

- Contas
- Dados Cadastrais
- Cartão de Crédito
- Crédito
- Empréstimos
- Financiamento
- Investimentos
- Seguros
- Câmbio
- Previdência
- Produtos e Serviços

#### Pagamentos e Pix

- Pagamentos
- Pagamentos Automáticos
- Pix
- Pix Agendado
- Pix Automático
- Transferências Inteligentes
- Transações Temporizadas
- Webhook

#### Segurança e Identidade

- FAPI (Financial-grade API)
- DCR (Dynamic Client Registration)
- CIBA (Client Initiated Backchannel Authentication)
- Certificados
- Criptografia
- Assinatura digital
- Idempotência
- Validações

#### Processos e Experiência

- Compartilhamento de Dados
- Consentimento
- JSR (JSON Signature Request)
- Hybrid Flow
- Redirecionamento
- UX
- Diagramas
- Máquinas de estados
- Fluxogramas

#### Grupos Prefixados

- `[DC]` - Documentação Complementar
- `[DA]` - Dados Abertos
- `[SV]` - Serviços
- `[PC]` - Pagamentos de Conta
- `[EN]` - English version
- `[PT]` - Português
- `[PCM]` - Pagamentos de Conta Mensal
- `[PRÉVIA SET-26]` - Prévias

#### Áreas Especiais

- `_geral`
- `_changelogs`
- `sem-contexto`
- `e Resiliência de APIs`

### `references/openapi/`

Contém a documentação Swagger/OpenAPI organizada em **26 famílias de diretórios**:

- UI
- API Contas
- API Serviços de Credenciamento
- API Pagamentos Automáticos
- API Títulos de Capitalização
- API Consentimentos
- API Contas de Dados Abertos
- API Cartões
- API Portabilidade
- API Clientes
- API Enrollments
- API Câmbio
- API Investimentos
- API Empréstimos
- APIs OpenData
- API Iniciação de Pagamentos
- API Portabilidade Consignada
- API Previdência
- API Seguros
- API Webhook

**Inclui:** versões estáveis, `beta` e `rc`

### `references/regulatory/`

Contém **1.113 arquivos** de Instruções Normativas e Resoluções BCB em Markdown.

**Nomenclatura:**
- `Instrucao_Normativa_BCB_<número>.md`
- `Resolucao_BCB_<número>.md`

**Sempre confirme a vigência** no Banco Central ou no Portal do Desenvolvedor.

### `references/reports/`

Contém os informes numerados do ecossistema.

**Nomenclatura:** `informe_<número>.md`

**Sempre confirme data, assunto e validade** na fonte oficial antes de tratar como vigente.

## Arquivos Auxiliares

### `references/INDEX.md`

Inventário completo e fonte de verdade estrutural do acervo.

**522 diretórios** listados com caminhos exatos.

**Uso:**
- Navegação e descoberta de conteúdo
- Verificação de existência de documentos
- Localização de versões específicas

### `references/llms.txt` e `references/llms-full.txt`

Índices textuais para consumo por LLMs:

- `llms.txt` - Versão resumida
- `llms-full.txt` - Versão completa

### `references/openapi-consultation.md`

Procedimento detalhado de:
- Resolução local de especificações
- Fallback para repositório GitHub
- Validação de conteúdo OpenAPI

## Regras para Referências Históricas e Caminhos

### Identificadores de Material Não-Vigente

- `old/` - Versões anteriores
- `beta` - Versões beta
- `rc` - Release candidates
- `Legada` - APIs legadas

**Sempre confirme** antes de promover a referência atual.

### Preservação de Nomes

**Não normalize silenciosamente:**
- Acentos
- Colchetes e parênteses
- Pontos finais
- Caracteres invisíveis (ex: U+200B ZERO WIDTH SPACE)

**O índice preserva** a grafia original do filesystem.

### Construção de Caminhos

1. **Copie o nome do índice** - Não reconstrua por aproximação
2. **Preserve caminhos relativos** - Use `references/...`
3. **Percent-encoding apenas na apresentação** - Não altere identidade no filesystem

### Inventario como Snapshot

O inventário é um **snapshot local**, não:
- Prova de vigência normativa
- Garantia de versão mais recente
- Substituto de consulta oficial

## Fontes de Verdade por Tipo de Informação

| Tipo | Fonte de Verdade |
|------|------------------|
| Estrutura do contrato | OAS exato (versão solicitada) |
| Cronogramas | Portal do Desenvolvedor (vivo) |
| Comunicados oficiais | Portal do Desenvolvedor (vivo) |
| Texto normativo | BCB / Portal do Desenvolvedor |
| Status de comunicado | Portal do Desenvolvedor (vivo) |
| Correções recentes | Repositório GitHub oficial |

## Limitações do Acervo Local

O acervo local **não é fonte definitiva** para:

- Versão atual ou candidata de uma API
- Prazo, cronograma ou data de entrada em vigor
- Texto exato de cláusula normativa
- Status de comunicado técnico
- Correções recentes do Swagger/OpenAPI

**Quando a pergunta depender desses pontos:**
1. Consulte a fonte oficial viva
2. Registre a URL consultada
3. Não afirme dados de memória

## Links Importantes

| Recurso | URL |
|---------|-----|
| Portal do Desenvolvedor | https://openfinancebrasil.atlassian.net/wiki/spaces/OF |
| Repositório de Especificações | https://github.com/OpenBanking-Brasil/all-services-repo |
| Estrutura de Governança | https://openfinancebrasil.org.br/governanca/ |
| Service Desk | https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17379146 |

---

**Versão:** 2.0.0 | **Última atualização:** 09/09/2026
