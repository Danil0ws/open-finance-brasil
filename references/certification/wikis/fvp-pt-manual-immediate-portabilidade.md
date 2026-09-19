# Portabilidade

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Portabilidade](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Portabilidade)
**Slug:** `FVP/PT/Manual/Immediate/Portabilidade`

---

---
title: Portabilidade de Crédito
---

[← FVP Manual / FVP Aberta](FVP/PT/Manual/Immediate)

# FVP Manual - Portabilidade de Crédito

Esta página reúne os planos manuais da FVP para Portabilidade de Crédito. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Credit Portability API - v1.0.0 - Personal - Open FVP
Nome técnico: `fvp-credit-portability_open_test-plan-v1`

Valida o fluxo de portabilidade de crédito pessoal (CREDITO_PESSOAL_CLEAN) na API Credit Portability v1, cobrindo rejeições por termos inválidos, a progressão até o status RECEIVED e o cancelamento, além das validações de grant type, x-fapi-interaction-id e idempotência nos endpoints de portabilidade.

### Antes de começar
- Janela de execução: Os três módulos deste plano são imediatos e podem ser executados a qualquer horário.
- Não aplicável: a portabilidade de crédito (CPC) não usa campos de conta credora.
- Não há requisito de saldo em conta. O pré-requisito é ter ao menos um contrato de crédito pessoal clean (CREDITO_PESSOAL_CLEAN) vinculado ao CPF/CNPJ configurado, com portability-eligibility DISPONIVEL e isEligible=TRUE.
- O campo authorizationServerId é obrigatório; alias, description, publish e as URLs de discovery são preenchidos automaticamente pela FVP a partir do authorizationServerId.

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
| fvp-credit-portability_api_invalid-contract-terms_test-module_v1 | Propostas de portabilidade com termos divergentes do contrato original são recusadas (422: CAMPO_INCONSISTENTE, PERIODICIDADE_INVALIDA, PRAZO_ACIMA_LIMITE, NAO_INFORMADO). |
| fvp-credit-portability_api_received-portability_test-module_v1 | Portabilidade com termos iguais aos do contrato original é criada (202), chega ao status RECEIVED e é cancelada pelo cliente (CANCELADO_PELO_CLIENTE). |
| fvp-credit-portability_api_invalid_grant_type_invalid_x-fapi_invalid_idempodency_test-module_v1 | Cenários de erro de protocolo: grant type incorreto (401/403), x-fapi-interaction-id ausente ou inválido (400) e reuso de idempotency-key com payload diferente (422 ERRO_IDEMPOTENCIA). |

### Observações
- Nenhuma conta credora é configurada para este plano: a CPC não exige campos de Payment consent (ISPB, Issuer, Number, Type, Name, CPF/CNPJ do recebedor). Não preencha esses campos.
- Saldo em conta não é requisito. O pré-requisito é ter ao menos um contrato CREDITO_PESSOAL_CLEAN com concurrentManagement=DISPONIVEL e isEligible=TRUE vinculado ao CPF/CNPJ configurado.
- Os três módulos deste plano são executados manualmente e de forma independente; não há agendamento automático entre eles.
- Preencha apenas um dos campos de identificação: brazilCpf (PF, 11 dígitos) ou brazilCnpj (PJ, 14 dígitos). Enviar ambos pode causar rejeição da execução.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2025-10-31 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/0e619f797a91486e13e5e424258579bb/FVP-Credit-Portability-API-v1.0.0-Personal-Open-FVP.xlsx)

---

[↑ FVP Aberta](FVP/PT/Manual/Immediate) · [◀ Pagamentos Automáticos](FVP/PT/Manual/Immediate/Pagamentos-Automaticos) · [Dados do Cliente ▶](FVP/PT/Manual/Immediate/Dados)


---

*Conteúdo baixado em 16/09/2026, 15:37:59*
