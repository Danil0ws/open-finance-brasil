# Certificação e Conformidade — Referência Completa

Documentação detalhada sobre certificação, testes de conformidade e homologação no Open Finance Brasil.

## Estrutura do Acervo de Certificação

O diretório `references/certification/` contém **~2.990 arquivos** organizados em:

### `wikis/` (133 arquivos Markdown)

Documentação técnica completa da **Conformance Suite** e procedimentos de certificação.

#### Procedimentos Gerais

- `certification-guide.md` - Guia completo de certificação
- `certification-automated-process.md` - Processo automatizado
- `running-the-conformance-suite-locally.md` - Setup local (Docker, Java, Maven, IDE)
- `release-notes.md` - Histórico de mudanças e breaking changes
- `code-and-execution-walkthrough.md` - Passo a passo de execução

#### FVP (Functional Verification Process)

Testes organizados por jornada e idioma:

**Automática (sem jornada do usuário):**
- `fvp-pt-automatica.md` - Versão PT
- `fvp-en-automatic.md` - Versão EN

**Manual Imediata (sem agendamento):**
- `fvp-pt-manual-immediate-jornada-otimizada.md`
- `fvp-pt-manual-immediate-pagamentos-automaticos.md`
- `fvp-pt-manual-immediate-credit-portability.md`
- `fvp-en-manual-immediate-*` - Versões em inglês

**Manual Agendada (com agendamento):**
- `fvp-pt-manual-scheduled-enrollments.md`
- `fvp-pt-manual-scheduled-portabilidade.md`
- `fvp-pt-manual-scheduled-pagamentos.md`
- `fvp-en-manual-scheduled-*` - Versões em inglês

**Jornada Otimizada:**
- Testes específicos de Pix e consentimentos

#### CIBA (Client Initiated Backchannel Authentication)

- `ciba.md` - Overview
- `ciba-customer-data.md` - Dados de cliente
- `ciba-flow-with-the-mock-bank.md` - Fluxo com mock bank (EN)
- `ciba-flow-with-the-mock-bank-pt.md` - Fluxo com mock bank (PT)

#### Portabilidade de Crédito

- `credit-portability.md` - Overview
- `credit-portability-mb.md` - Mortgage Backed
- `credit-portability-personal-v1-0-0.md` - Pessoal v1.0.0
- `credit-portability-personal-v1-1-0-rc-1.md` - Pessoal v1.1.0-rc.1
- `credit-portability-payroll-v1-0-0-rc-1.md` - Consignada v1.0.0-rc.1

#### Testes Especializados

- `dcr.md` - Dynamic Client Registration
- `alphanumeric-cnpj.md` - CNPJ Alfanumérico
- `customer-consent-and-authorisation.md` - Consentimento (EN)
- `customer-consent-and-authorisation-pt.md` - Consentimento (PT)
- `customer-data.md` - Dados de Cliente
- `automated-production-tests.md` - Testes em Produção

#### Conformance Suite — Configuração e Execução

- `discovery-and-onboarding-with-banks.md` - Discovery e onboarding
- `discovery-of-the-mock-bank.md` - Discovery do mock bank
- `browser-control.md` - Controle de navegador
- `executing-tests-against-an-as.md` - Executar contra Authorization Server
- `running-specific-tests-locally-against-your-own-api-responses.md` - Testes locais customizados
- `writing-test-plans-for-protected-resources.md` - Planos de teste para recursos protegidos

#### Documentação Complementar

- `mock-tpp-source-code.md` - Código-fonte do TPP mock
- `a-simplified-way-to-validate-json.md` - Validação JSON
- `condition.md` - Condições de teste
- `enable-fapi-unique.md` - Habilitar FAPI Unique
- `existing-functionalities.md` - Funcionalidades existentes
- Orienções de execução e outras guias

#### Release Notes

Histórico completo de mudanças:
- Breaking changes com data de corte (cut-off)
- Novas funcionalidades por versão
- Mudanças em planos de teste (FVP, CIBA, Portabilidade, DCR, etc.)

### `work-items/` (~2.810 arquivos)

Rastreadores de trabalho, issues e planejamento de testes.

**Conteúdo:**
- Issues do GitLab da Conformance Suite
- Matriz de testes por API e versão
- Planejamento de releases
- Testes pendentes, em andamento, concluídos
- Critério de aceitação

## Tipos de Teste e Cobertura

### Certificação Funcional (FVP)

**Escopo:**
- Endpoints obrigatórios estão presentes
- Schemas de request/response estão corretos
- Códigos de HTTP status apropriados
- Tratamento de erros conforme especificação
- Fluxos de consentimento e autenticação funcionam

**Modalidades:**
1. **Automática** - Testes sem jornada do usuário (DCR, FAPI, Diretório)
2. **Manual Imediata** - Transações sem agendamento (Pix, Portabilidade)
3. **Manual Agendada** - Transações agendadas (Pagamentos recorrentes)
4. **Jornada Otimizada** - Fluxo simplificado de consentimento

### Certificação de Segurança

**Tópicos:**
- FAPI Brasil compliance
- DCR (Dynamic Client Registration)
- mTLS
- Assinatura de mensagem (JWS)
- Criptografia (JWE)
- Validação de certificados

## Procedimento de Certificação

### Pré-requisitos

1. Authorization Server implementado conforme especificação OAS
2. APIs conformes com a versão alvo
3. Certificados de segurança válidos (se aplicável)
4. Conta no Conformance Suite
5. Acesso ao Diretório do Open Finance

### Passos

1. **Registrar no Conformance Suite** - Criar conta e empresa
2. **Configurar Authorization Server** - Informar endpoints
3. **DCR (se aplicável)** - Registrar cliente dinamicamente
4. **Executar Testes Automáticos** - FVP Automática diariamente
5. **Executar Testes Manuais** - FVP Manual por jornada
6. **Revisar Resultados** - Conferir conformidade
7. **Submeter para Homologação** - Documento de conformidade

### Cronograma

- **FVP Automática** - Execução diária (04:00 Z)
- **FVP Manual** - Sob demanda ou em batch
- **Certificação** - Válida por período definido
- **Recertificação** - Anual ou conforme mudanças de versão

## Versões de API e Certificação

Cada versão de API tem seu próprio plano de teste:

- **v1.x** - Versões legadas (ainda certificadas)
- **v2.x** - Versões atuais principais
- **v3.x** - Novas versões em rollout
- **rc/beta** - Release candidates (teste antecipado)

**Release Notes** detalha quais testes foram adicionados/modificados em cada versão.

## Quando Consultar Certificação

### Use Certificação quando:

- ✅ Precisar implementar uma API do Open Finance
- ✅ Preparar para homologação em produção
- ✅ Debugar falha em teste de conformidade
- ✅ Entender a jornada de consentimento esperada
- ✅ Validar versão de API contra certificação vigente
- ✅ Configurar Conformance Suite localmente
- ✅ Consultar breaking changes recentes

### Quando usar Guias Técnicos em vez de Certificação:

- Entender conceito (use `guides/`)
- Ler especificação completa (use `openapi/`)
- Saber requisitos de segurança (use `guides/Segurança/`)

## Conformance Suite — Local vs. Hosted

| Aspecto | Local | Hosted |
|--------|-------|--------|
| **Setup** | Docker Compose / IDE | Nenhum |
| **Privacidade** | Dados sensíveis retidos localmente | Logs podem expor dados |
| **Recomendado para** | Desenvolvimento, pré-produção | Testes iniciais |
| **Produção** | ✅ Recomendado | ❌ Não recomendado |
| **Debugging** | ✅ Fácil (IDE, Debugger Java) | ❌ Difícil (web UI) |

**Referência:** `running-the-conformance-suite-locally.md`

## Links Importantes

| Recurso | URL |
|---------|-----|
| Conformance Suite (Hosted) | https://web.conformance.directory.openbankingbrasil.org.br/ |
| Conformance Suite (Repositório) | https://gitlab.com/obb1/certification/ |
| Documentação Wiki | https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis |
| Portal do Desenvolvedor | https://openfinancebrasil.atlassian.net/wiki/spaces/OF |
| Diretório do Open Finance | https://directory.openbankingbrasil.org.br/ |

## Limitações do Acervo Local

O acervo de certificação é um **snapshot** e:

- ❌ Não reflete issues atuais (use GitLab para issues abertas)
- ❌ Não reflete releases futuras (use Release Notes para histórico recente)
- ❌ Pode ter defasagem em relação à Conformance Suite live
- ✅ Útil para referência histórica e aprendizado offline

**Quando depender de informação atual:**
1. Consulte o repositório GitLab oficial
2. Verifique a Conformance Suite hosted
3. Contate o Service Desk se necessário

---

**Versão:** 2.1.0 | **Última atualização:** 09/09/2026
