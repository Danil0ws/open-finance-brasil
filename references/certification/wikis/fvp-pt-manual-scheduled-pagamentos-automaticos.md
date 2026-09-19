# Pagamentos Automaticos

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Pagamentos-Automaticos](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Pagamentos-Automaticos)
**Slug:** `FVP/PT/Manual/Scheduled/Pagamentos-Automaticos`

---

---
title: Pagamentos Automáticos
---

[← FVP Manual / FVP Restrita](FVP/PT/Manual/Scheduled)

# FVP Manual - Pagamentos Automáticos

Esta página reúne os planos manuais da FVP para Pagamentos Automáticos. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Automatic Payments API - v2.2.0 - Automatic Pix Scheduling - Restricted FVP
Nome técnico: `fvp-automatic-pix-payments_restricted_test-plan-v2-2`

Valida o ciclo completo de pagamentos automáticos via Pix recorrente (sweeping scheduling) na API Automatic Payments v2.2.0, cobrindo criação e autorização de consentimento recorrente, agendamento de pagamento, polling de status e fluxos de retry, tanto com falha e reagendamento quanto com retry bem-sucedido.

### Antes de começar
**Saldo em conta**
- D+0: exatamente R$ 0,00 (obrigatório)
- D+1: exatamente R$ 0,00 (obrigatório)
- D+2: exatamente R$ 0,00 (obrigatório)
- D+3: mínimo R$ 1,00 (obrigatório)
- Janela de execução: 21:00 a 23:59 BRT nos dias agendados
- deve ser CNPJ (o Pix Automático não aceita CPF como identificador da conta credora)
- "D+N" refere-se a N dias corridos após a execução do Módulo 1, não dias úteis.
- Os testes de acompanhamento só são agendados se o Módulo 1 for concluído com sucesso; um erro no início não dispara as execuções seguintes.
- client_id, consent_id, payment_id e refresh_token são persistidos automaticamente pela suite entre as rodadas.

### Campos do formulário de configuração
| Campo | Obrigatoriedade | Descrição |
| --- | --- | --- |
| Type | Opcional | Tipo de execução desta execução (opcional). Deixe em branco para executar normalmente. Selecionar 'Test' exige um Ciclo; selecionar 'Retest' exige um Ciclo e um Ticket de SD. Esses valores são anexados à descrição do teste. (Opções: —, Test, Retest) |
| Cycle | Opcional | Ciclo ao qual esta execução pertence. Obrigatório quando um Tipo (Test ou Retest) é selecionado. |
| SD Ticket | Opcional | Ticket de Service Desk para esta execução. Obrigatório quando o Tipo é 'Retest'. |
| Authorisation Server ID | Obrigatório | O ID do Servidor de Autorização é utilizado para buscar o OrganisationId e o OpenIDDiscoveryDocument no endpoint /participants. |
| Recurring Payment consent - Contract Debtor Name | Obrigatório | Nome do devedor do contrato. Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento recorrente para todos os módulos de teste que enviam o campo firstPayment. |
| Recurring Payment consent - Contract Debtor Identification | Obrigatório | Identificação do devedor do contrato. Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento recorrente para todos os módulos de teste que enviam o campo firstPayment. |
| Payment consent - Creditor Account ISPB | Obrigatório | Deve ser preenchido com o ISPB da conta creditada no SPI. Somente números, 8 dígitos. |
| Payment consent - Creditor Account Issuer | Obrigatório | Código da agência emissora sem o dígito verificador. Somente números, até 4 dígitos. |
| Payment consent - Creditor Account Number | Obrigatório | Número da conta do usuário recebedor, incluindo o dígito verificador (se aplicável). Caracteres alfanuméricos devem ser convertidos para 0. Somente números, até 20 dígitos. |
| Payment consent - Creditor Account Type | Obrigatório | Tipos de conta utilizados para pagamento. Deve seguir os formatos definidos na documentação Swagger da API. |
| Payment consent - Creditor Account Name | Obrigatório | Nome da conta do credor. Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento para todos os módulos de teste, exceto o módulo qrdn e os módulos opcionais. |
| Payment consent - Creditor Account CPF / CNPJ | Obrigatório | CPF/CNPJ da conta do credor. Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento para todos os módulos de teste, exceto o módulo qrdn e os módulos opcionais. |
| brazilCpf | Obrigatório | Valor do CPF a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação do Usuário Logado (substitui o antigo campo loggedUser). |
| brazilCnpj | Opcional | Valor do CNPJ a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação da Pessoa Jurídica (substitui o antigo campo businessEntity). |
| description | Opcional | Descrição livre desta execução. Opcional; pode ficar em branco. |

### Módulos e o que esperar
| Módulo de teste | O que faz |
| --- | --- |
| automatic-payments_api_automatic-pix-scheduling_1-2_test-module_v2-2 | Cria e autoriza o consentimento recorrente e agenda um pagamento sem retry; após o polling, o pagamento fica Agendado (SCHD). |
| automatic-payments_api_automatic-pix-scheduling_2-2_test-module_v2-2 | Verificação do dia seguinte: confirma que o pagamento agendado sem retry foi liquidado (ACSC). |
| automatic-payments_api_automatic-pix-scheduling-retry_1-3_test-module_v2-2 | Cria e autoriza o consentimento com retry habilitado e agenda o pagamento (SCHD) para verificação posterior. |
| automatic-payments_api_automatic-pix-scheduling-retry_2-3_test-module_v2-2 | O pagamento original é rejeitado (RJCT) e um retry é agendado (SCHD) para o dia seguinte. |
| automatic-payments_api_automatic-pix-scheduling-retry_3-3_test-module_v2-2 | Confirma que, após a rejeição do pagamento original, o retry não permanece agendado (status diferente de SCHD). |
| automatic-payments_api_automatic-pix-scheduling-successful-retry_1-3_test-module_v2-2 | Cria e autoriza o consentimento com retry habilitado e agenda o pagamento (SCHD), preparando o cenário de retry bem-sucedido. |
| automatic-payments_api_automatic-pix-scheduling-successful-retry_2-3_test-module_v2-2 | O pagamento original é rejeitado (RJCT) e um novo pagamento de retry é emitido e agendado (SCHD). |
| automatic-payments_api_automatic-pix-scheduling-successful-retry_3-3_test-module_v2-2 | Confirma que o pagamento de retry foi liquidado com sucesso (ACSC) após a rejeição do original. |

### Observações
- Os módulos de retry (2-3 e 3-3 de cada sequência) devem ser executados entre 21:00 e 23:59 BRT nos dias agendados; fora dessa janela a suite interrompe o teste.
- Os módulos 2 e 3 de cada sequência de retry são agendados automaticamente pela Conformance Suite entre si, usando os dados salvos (consentID, paymentID, clientId, refresh_token) do módulo anterior. Não os execute manualmente.
- Mantenha o servidor do participante online e responsivo entre 21:00 e 23:59 BRT nos dias agendados (D+2 e D+3 da sequência de retry).

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2025-10-29 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/7233205e3bfbb928cd0020bccbbf49bf/FVP-Automatic-Payments-API-v2.2.0-Automatic-Pix-Scheduling-Restricted-FVP.xlsx)

---

[↑ FVP Restrita](FVP/PT/Manual/Scheduled) · [◀ Enrollments](FVP/PT/Manual/Scheduled/Enrollments) · [Portabilidade de Crédito ▶](FVP/PT/Manual/Scheduled/Portabilidade)


---

*Conteúdo baixado em 16/09/2026, 15:38:03*
