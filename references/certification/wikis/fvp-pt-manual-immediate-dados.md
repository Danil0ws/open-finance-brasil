# Dados

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Dados](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Dados)
**Slug:** `FVP/PT/Manual/Immediate/Dados`

---

---
title: Dados do Cliente
---

[← FVP Manual / FVP Aberta](FVP/PT/Manual/Immediate)

# FVP Manual - Dados do Cliente

Esta página reúne os planos manuais da FVP para Dados do Cliente. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Customer Data APIs - v2/v3 - Happy Path - Open FVP
Nome técnico: `fvp-customer-data-happy-path_open_test-plan_v3`

Valida a conformidade estrutural das APIs de dados do cliente (consentimentos, recursos, contas, cartão de crédito, financiamentos, empréstimos, adiantamento a depositantes e dados cadastrais pessoais e empresariais) nas versões V2/V3, cobrindo o fluxo completo de criação e autorização de consentimento até as chamadas GET em cada endpoint registrado no Diretório.

### Antes de começar
- Janela de execução: Plano imediato: sem janela de execução, pode ser executado a qualquer horário.
- Não há requisito de saldo em conta: os módulos validam a estrutura de resposta das APIs de dados e nenhum pagamento é iniciado.
- Não há conta credora: este plano não tem fluxo de pagamento.
- Antes de executar, garanta que o usuário de teste (CPF informado em brazilCpf) tenha ao menos uma conta ativa em cada produto testado (Accounts, Credit Cards, Loans, Financings, Invoice Financings, Unarranged Overdraft, Customer Personal/Business).
- O módulo Resources pode exigir que recursos indisponíveis sejam configurados manualmente para o usuário de teste antes da execução.

### Campos do formulário de configuração
| Campo | Obrigatoriedade | Descrição |
| --- | --- | --- |
| Type | Opcional | Tipo de execução desta execução (opcional). Deixe em branco para executar normalmente. Selecionar 'Test' exige um Ciclo; selecionar 'Retest' exige um Ciclo e um Ticket de SD. Esses valores são anexados à descrição do teste. (Opções: —, Test, Retest) |
| Cycle | Opcional | Ciclo ao qual esta execução pertence. Obrigatório quando um Tipo (Test ou Retest) é selecionado. |
| SD Ticket | Opcional | Ticket de Service Desk para esta execução. Obrigatório quando o Tipo é 'Retest'. |
| Authorisation Server ID | Obrigatório | O ID do Servidor de Autorização é utilizado para buscar o OrganisationId e o OpenIDDiscoveryDocument no endpoint /participants. |
| brazilCpf | Obrigatório | Valor do CPF a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação do Usuário Logado (substitui o antigo campo loggedUser). |
| brazilCnpj | Opcional | Valor do CNPJ a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação da Pessoa Jurídica (substitui o antigo campo businessEntity). |
| description | Opcional | Descrição livre desta execução. Opcional; pode ficar em branco. |

### Módulos e o que esperar
| Módulo de teste | O que faz |
| --- | --- |
| fvp-preflight-check-test-v3 | Confere as pré-condições: token retorna 200, servidor registrado no Diretório e famílias consents v3 e resources v3 publicadas. |
| fvp_consents_api_core_test-module_v3-3-1 | Cria e autoriza um consentimento de dados e confirma o GET Consents (200, x-v 3.3.1). |
| resources_api_core_test-module_v3-1 | Autoriza o consentimento e valida o GET Resources (200, com polling até 200), encerrando com DELETE Consents (204). |
| accounts_api_core_consents_v3_test-module_v2-5-1 | Valida os endpoints da API Accounts (listagem, conta, saldos, transações, limites e saldos reservados), todos retornando 200. |
| credit-cards_api_core_consents_v3-3_test-module_v2-4 | Valida os endpoints da API Credit Cards (contas, limites, transações e faturas), todos retornando 200. |
| financings_api_core_consents_v3-3_test-module_v2-4 | Valida os endpoints da API Financings (contratos, garantias, pagamentos e parcelas), todos retornando 200. |
| customer-business_api_core_consents_v3-3_test-module_v2-3 | Valida os endpoints de dados cadastrais de pessoa jurídica (qualificações, identificações e relações financeiras) e encerra o consentimento (204). |
| customer-personal_api_core_consents_v3-3_test-module_v2-3 | Valida os endpoints de dados cadastrais de pessoa física (qualificações, identificações e relações financeiras) e encerra o consentimento (204). |
| invoice-financings_api_core_consents_v3-2_test-module_v2-4 | Valida os endpoints da API Invoice Financings (contratos, garantias, pagamentos e parcelas), todos retornando 200. |
| loans_api_core_consents_v3-3_test-module_v2-6 | Valida os endpoints da API Loans (contratos, garantias, pagamentos e parcelas), todos retornando 200 (x-v 2.6.0). |
| unarranged-accounts-overdraft_api_core_consents_v3-3_test-module_v2-5 | Valida os endpoints da API Unarranged Accounts Overdraft (contratos, garantias, pagamentos e parcelas), todos retornando 200. |
| fvp-accounts_api_core_consents_all_permissions_v3-3_test-module_v2-5-1 | Cria um consentimento sem data de expiração e com todas as permissões, e valida os endpoints da API Accounts (200), encerrando com DELETE (204). |
| fvp-customer_data_unique_happy_path_test-module | Fluxo único de dados do cliente: com um só consentimento sem expiração, faz GET em todos os endpoints das APIs registradas no Diretório (todos 200) e encerra com DELETE (204). |

### Observações
- Este plano é imediato (não agendado): todos os módulos executam na mesma sessão, sem dependência de datas ou janelas BRT. Não há pagamentos, portanto nenhum saldo mínimo é necessário.
- Se brazilCnpj for informado, selecione "Business Personal Permission" no formulário da FVP; caso contrário, use "Customer Personal Permission". Envie apenas uma das opções (CPF, ou CPF+CNPJ): enviar ambos sem selecionar o perfil correto pode causar falha no consentimento.
- O Operational Limits verifica permissões pela Consents API: se o servidor retornar as permissões com 201, os recursos são testados; se não retornar, o teste é pulado com WARNING (a instituição não controla esses recursos).

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2024-10-18 | Plano de teste criado na FVP. |  |
| 2025-02-27 | Validadores atualizados. | Consentimentos 3.1, empréstimos 2.4, financiamentos 2.3, direitos creditórios descontados 2.3 e adiantamento a depositantes 2.4. |
| 2025-09-02 | Empréstimos atualizados para 2.5. |  |
| 2025-12-02 | Consentimentos atualizados para 3.3. |  |
| 2026-01-12 | Consentimentos passam a exigir o cabeçalho x-v. | Além da estrutura da resposta, o módulo passou a verificar a presença do x-v com a versão 3.3.1. |
| 2026-01-29 | Validadores atualizados. | Direitos creditórios descontados 2.4, financiamentos 2.4, recursos 3.1 e adiantamento a depositantes 2.5. |
| 2026-05-12 | Dados cadastrais atualizados para 2.3. | Pessoa natural e pessoa jurídica. |
| 2026-05-26 | Empréstimos atualizados para 2.6. |  |
| 2026-06-08 | Contas 2.5 e cartão de crédito 2.4. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |
| 2026-07-22 | Contas atualizadas para 2.5.1. |  |

[Baixar a planilha deste plano](uploads/91dc4404d7185e822dd84e290723de8a/FVP-Customer-Data-APIs-v2-v3-Happy-Path-Open-FVP.xlsx)

---

[↑ FVP Aberta](FVP/PT/Manual/Immediate) · [◀ Portabilidade de Crédito](FVP/PT/Manual/Immediate/Portabilidade) · [Pagamentos ▶](FVP/PT/Manual/Immediate/Pagamentos)


---

*Conteúdo baixado em 16/09/2026, 15:37:55*
