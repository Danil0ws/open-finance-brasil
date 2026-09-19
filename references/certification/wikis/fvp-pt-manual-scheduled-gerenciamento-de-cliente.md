# Gerenciamento de Cliente

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Gerenciamento-de-Cliente](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Gerenciamento-de-Cliente)
**Slug:** `FVP/PT/Manual/Scheduled/Gerenciamento-de-Cliente`

---

---
title: Gerenciamento de Cliente
---

[← FVP Manual / FVP Restrita](FVP/PT/Manual/Scheduled)

# FVP Manual - Gerenciamento de Cliente

Esta página reúne os planos manuais da FVP para Gerenciamento de Cliente. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Manual Client Deletion - Restricted FVP
Nome técnico: `fvp-manual-client-deletion_test-plan-v1`

Valida a exclusão dos clientes pré-registrados (pagamentos e portabilidade de crédito) de um servidor de autorização, removendo o cliente pelo endpoint de Client Management (DELETE) e apagando o registro do banco de dados.

### Campos do formulário de configuração
| Campo | Obrigatoriedade | Descrição |
| --- | --- | --- |
| Type | Opcional | Tipo de execução desta execução (opcional). Deixe em branco para executar normalmente. Selecionar 'Test' exige um Ciclo; selecionar 'Retest' exige um Ciclo e um Ticket de SD. Esses valores são anexados à descrição do teste. (Opções: —, Test, Retest) |
| Cycle | Opcional | Ciclo ao qual esta execução pertence. Obrigatório quando um Tipo (Test ou Retest) é selecionado. |
| SD Ticket | Opcional | Ticket de Service Desk para esta execução. Obrigatório quando o Tipo é 'Retest'. |
| Authorisation Server ID | Obrigatório | O ID do Servidor de Autorização é utilizado para buscar o OrganisationId e o OpenIDDiscoveryDocument no endpoint /participants. |
| brazilCpf | Obrigatório | Valor do CPF a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação do Usuário Logado (substitui o antigo campo loggedUser). |
| description | Opcional | Descrição livre desta execução. Opcional; pode ficar em branco. |

### Módulos e o que esperar
| Módulo de teste | O que faz |
| --- | --- |
| manual_client_deletion_payments_test-module_v1 | Exclui o cliente pré-registrado de pagamentos via DELETE no endpoint de Client Management (se o DCM falhar, a suite emite um aviso e prossegue). |
| manual_client_deletion_credit-portability_test-module_v1 | Exclui o cliente pré-registrado de portabilidade de crédito via DELETE no endpoint de Client Management (se o DCM falhar, a suite emite um aviso e prossegue). |

### Observações
- Se o endpoint de Client Management (DCM) retornar erro durante a exclusão, a suite emite um Warning mas continua a execução.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-03-03 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/cefc6bd4f661c00b0a240f18be3b210a/FVP-Manual-Client-Deletion-Restricted-FVP.xlsx)

---

[↑ FVP Restrita](FVP/PT/Manual/Scheduled) · [◀ Pagamentos](FVP/PT/Manual/Scheduled/Pagamentos) · [Notas de versão ▶](FVP/PT/Release-Notes)


---

*Conteúdo baixado em 16/09/2026, 15:38:02*
