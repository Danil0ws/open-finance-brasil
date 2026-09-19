# Portabilidade

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Portabilidade](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Portabilidade)
**Slug:** `FVP/PT/Manual/Scheduled/Portabilidade`

---

---
title: Portabilidade de Crédito
---

[← FVP Manual / FVP Restrita](FVP/PT/Manual/Scheduled)

# FVP Manual - Portabilidade de Crédito

Esta página reúne os planos manuais da FVP para Portabilidade de Crédito. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Credit Portability API - v1.0.0 - Personal Scheduling - Restricted FVP
Nome técnico: `fvp-credit-portability_restricted_test-plan-v1`

Valida o fluxo completo de portabilidade de crédito pessoal (Credit Portability API v1.0.0) em ambiente restrito FVP, cobrindo criação de consentimento, submissão de portabilidade, cancelamento em status ACCEPTED_SETTLEMENT_IN_PROGRESS e verificação de elegibilidade pós-cancelamento ao longo de múltiplos dias agendados.

### Antes de começar
- Janela de execução: O Módulo 1 pode ser executado a qualquer horário. Os Módulos 2 e 3 são agendados automaticamente pela FVP: o Módulo 2 no próximo dia útil (D+1) às 10:10 (GMT-3) e o Módulo 3 no dia seguinte às 00:01 (GMT-3).
- Não aplicável: a portabilidade de crédito (CPC) não usa campos de conta credora.
- Não há requisito de saldo em conta. O pré-requisito é ter ao menos um contrato de crédito pessoal clean (CREDITO_PESSOAL_CLEAN) com concurrentManagement=DISPONIVEL e isEligible=TRUE, vinculado ao CPF/CNPJ configurado.
- Preencha apenas um dos campos de identificação: brazilCpf (PF, 11 dígitos) ou brazilCnpj (PJ, 14 dígitos).
- O campo authorizationServerId é obrigatório; alias, description, publish e as URLs de discovery são preenchidos automaticamente pela FVP.

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
| credit-portability_api_accepted_settlement_1-3_test-module_v1 | Cria o consentimento, submete a portabilidade (202) e a leva até o status Recebido (RECEIVED). |
| credit-portability_api_accepted_settlement_2-3_test-module_v1 | Acompanha a portabilidade até a liquidação em andamento (ACCEPTED_SETTLEMENT_IN_PROGRESS) e a cancela pelo cliente (CANCELADO_PELO_CLIENTE). |
| credit-portability_api_accepted_settlement_3-3_test-module_v1 | Verifica a elegibilidade da portabilidade (status DISPONIVEL, isEligible TRUE) e encerra o consentimento (DELETE 204). |

### Observações
- Os Módulos 2 e 3 são agendados automaticamente pela suite (Módulo 2 em D+1 às 10:10 (GMT-3); Módulo 3 no dia seguinte às 00:01 (GMT-3)); não os execute manualmente.
- Enquanto o status for PENDING, o Módulo 2 pode reagendar a si mesmo para o próximo dia.
- Saldo em conta não é necessário para a CPC; o participante precisa de um empréstimo pessoal clean (CREDITO_PESSOAL_CLEAN) com concurrentManagement=DISPONIVEL e isEligible=TRUE.
- Duração máxima esperada do ciclo: até 5 dias úteis (excluindo fins de semana e feriados). Se esgotar sem estado terminal, o teste é reportado como Not Completed / Expired e exige reexecução completa.
- Garanta que o servidor do participante esteja online e responsivo nos dias agendados; se ficar offline na janela, os Módulos 2 e 3 podem falhar.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2025-10-31 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/bd65cf1ed6375f8e34ca231322fa1980/FVP-Credit-Portability-API-v1.0.0-Personal-Scheduling-Restricted-FVP.xlsx)

---

[↑ FVP Restrita](FVP/PT/Manual/Scheduled) · [◀ Pagamentos Automáticos](FVP/PT/Manual/Scheduled/Pagamentos-Automaticos) · [Pagamentos ▶](FVP/PT/Manual/Scheduled/Pagamentos)


---

*Conteúdo baixado em 16/09/2026, 15:38:04*
