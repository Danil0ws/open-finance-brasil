# Pagamentos

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Pagamentos](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Pagamentos)
**Slug:** `FVP/PT/Manual/Immediate/Pagamentos`

---

---
title: Pagamentos
---

[← FVP Manual / FVP Aberta](FVP/PT/Manual/Immediate)

# FVP Manual - Pagamentos

Esta página reúne os planos manuais da FVP para Pagamentos. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Payments API - v5.0.0 - Open FVP
Nome técnico: `fvp-payments-e2e_open_test-plan-v5`

Valida o fluxo completo de pagamentos Pix (E2E) em produção na API v5, do pre-flight de configuração do servidor à seleção de conta devedora, proxy inválido e pagamentos recorrentes nos formatos custom, diário e mensal, com criação, autorização, agendamento e cancelamento de consentimentos e pagamentos.

### Antes de começar
**Saldo em conta**
- D+0: exatamente R$ 2,00 (obrigatório)
- D+1: exatamente R$ 2,00 (obrigatório)
- D+2: exatamente R$ 1,00 (obrigatório)
- Janela de execução: 05:00 a 06:59 BRT nos dias agendados (Módulo 2, automático)
- A conta credora pode ser CPF ou CNPJ.
- Módulo 1 (manual): agenda dois pagamentos Pix, o primeiro para D+1 e o segundo para D+2. Fluxo esperado: Aguardando autorização → Autorizado → Agendado.
- Módulo 2 (automático): a suite verifica que ambos os pagamentos agendados foram concluídos com status ACSC.
- D+N refere-se a N dias corridos após a execução do Módulo 1.

### Campos do formulário de configuração
| Campo | Obrigatoriedade | Descrição |
| --- | --- | --- |
| Type | Opcional | Tipo de execução desta execução (opcional). Deixe em branco para executar normalmente. Selecionar 'Test' exige um Ciclo; selecionar 'Retest' exige um Ciclo e um Ticket de SD. Esses valores são anexados à descrição do teste. (Opções: —, Test, Retest) |
| Cycle | Opcional | Ciclo ao qual esta execução pertence. Obrigatório quando um Tipo (Test ou Retest) é selecionado. |
| SD Ticket | Opcional | Ticket de Service Desk para esta execução. Obrigatório quando o Tipo é 'Retest'. |
| Authorisation Server ID | Obrigatório | O ID do Servidor de Autorização é utilizado para buscar o OrganisationId e o OpenIDDiscoveryDocument no endpoint /participants. |
| Payment consent - Creditor Account ISPB | Obrigatório | Deve ser preenchido com o ISPB da conta creditada no SPI. Somente números, 8 dígitos. |
| Payment consent - Creditor Account Issuer | Obrigatório | Código da agência emissora sem o dígito verificador. Somente números, até 4 dígitos. |
| Payment consent - Creditor Account Number | Obrigatório | Número da conta do usuário recebedor, incluindo o dígito verificador (se aplicável). Caracteres alfanuméricos devem ser convertidos para 0. Somente números, até 20 dígitos. |
| Payment consent - Creditor Account Type | Obrigatório | Tipos de conta utilizados para pagamento. Deve seguir os formatos definidos na documentação Swagger da API. |
| Payment consent - Creditor Account Name | Obrigatório | Nome da conta do credor. Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento para todos os módulos de teste, exceto o módulo qrdn e os módulos opcionais. |
| Payment consent - Creditor Account CPF / CNPJ | Obrigatório | CPF/CNPJ da conta do credor. Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento para todos os módulos de teste, exceto o módulo qrdn e os módulos opcionais. |
| Payment consent - Creditor Account Proxy | Obrigatório | Proxy da conta do credor (ex.: chave Pix). Utilizado no corpo da requisição enviada ao endpoint de consentimento de pagamento para todos os módulos de teste, exceto o módulo qrdn e os módulos opcionais. |
| brazilCpf | Obrigatório | Valor do CPF a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação do Usuário Logado (substitui o antigo campo loggedUser). |
| brazilCnpj | Opcional | Valor do CNPJ a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação da Pessoa Jurídica (substitui o antigo campo businessEntity). |
| description | Opcional | Descrição livre desta execução. Opcional; pode ficar em branco. |

### Módulos e o que esperar
| Módulo de teste | O que faz |
| --- | --- |
| fvp-preflight-cert-check-payments-test-v5 | Confere, antes do fluxo, que o servidor publicou no Diretório os endpoints de pagamento na versão 5.0.0. |
| payments_api_no-debtor-account_open_test-module_v5 | Paga um Pix sem informar a conta devedora na requisição, deixando a escolha para o detentor; o pagamento é liquidado normalmente (ACSC). |
| payments_api_fake-email-proxy_open_test-module_v5 | Pagamento com e-mail inválido como chave proxy é rejeitado (RJCT) ou recusado de imediato (422 DETALHE_PAGAMENTO_INVALIDO / PAGAMENTO_RECUSADO_DETENTORA). |
| fvp-payments_api_recurring-payments-custom-core_open_test-module_v5 | Cria um consentimento recorrente personalizado (5 datas) e confirma os 5 pagamentos agendados (SCHD). |
| fvp-payments_api_recurring-payments-patch_open_test-module_v5 | Cria um consentimento recorrente de 5 pagamentos diários e valida o cancelamento pela iniciadora, primeiro de um pagamento avulso e depois de todos. |
| fvp-payments_api_recurring-payments-monthly-core_open_test-module_v5 | Cria um consentimento recorrente mensal (dia 31, com ajuste para meses mais curtos) e confirma os 5 pagamentos agendados (SCHD). |
| fvp-payments_api_recurring-payments-custom-not-cancelled_open_test-module_v5 | Cria um consentimento recorrente personalizado de 2 pagamentos e confirma que ambos ficam agendados (SCHD). |

### Observações
- O Módulo 2 é agendado automaticamente pela Conformance Suite; não o execute manualmente.
- Mantenha o servidor do participante online e responsivo entre 05:00 e 06:59 BRT nos dias agendados.
- D+N refere-se a N dias corridos após a execução do Módulo 1.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-07-03 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/47c61c6cc4319d6bf6ab8904d67b5e9e/FVP-Payments-API-v5.0.0-Open-FVP.xlsx)

---

[↑ FVP Aberta](FVP/PT/Manual/Immediate) · [◀ Dados do Cliente](FVP/PT/Manual/Immediate/Dados) · [FVP Restrita ▶](FVP/PT/Manual/Scheduled)


---

*Conteúdo baixado em 16/09/2026, 15:37:58*
