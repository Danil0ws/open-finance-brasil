# Pagamentos

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Pagamentos](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Pagamentos)
**Slug:** `FVP/PT/Manual/Scheduled/Pagamentos`

---

---
title: Pagamentos
---

[← FVP Manual / FVP Restrita](FVP/PT/Manual/Scheduled)

# FVP Manual - Pagamentos

Esta página reúne os planos manuais da FVP para Pagamentos. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Payments API - v5.0.0 - Scheduling - Restricted FVP
Nome técnico: `fvp-payments-e2e_restricted_test-plan-v5`

Valida o fluxo de pagamentos agendados em produção (API v5): criação e autorização do consentimento, agendamento de dois pagamentos para D+1 e D+2 e a verificação posterior de que ambos foram liquidados com sucesso.

### Antes de começar
**Saldo em conta**
- D+0: exatamente R$ 2,00 (obrigatório)
- D+1: exatamente R$ 2,00 (obrigatório)
- D+2: exatamente R$ 1,00 (obrigatório)
- Janela de execução: 05:00 a 06:59 BRT nos dias agendados (Módulo 2, automático)
- A conta credora pode ser CPF ou CNPJ (diferente do Pix Automático, que exige CNPJ).
- O Módulo 1 (agendar os dois pagamentos Pix, para D+1 e D+2) é manual; o Módulo 2 (verificar o ACSC de ambos) é agendado automaticamente pela suite.
- O consentID, os paymentIDs e o refreshToken são persistidos pela suite entre os módulos.
- Se o Módulo 1 falhar, o Módulo 2 não é agendado.

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
| payments_api_scheduled-pix-verification_1-2_test-module_v5 | Cria e autoriza o consentimento e agenda dois pagamentos Pix para D+1 e D+2, que ficam Agendados (SCHD). |
| payments_api_scheduled-pix-verification_2-2_test-module_v5 | Verifica que os dois pagamentos agendados foram liquidados (ACSC). |

### Observações
- O Módulo 2 é agendado automaticamente pela suite, reutilizando o consentID, os paymentIDs e o refreshToken salvos pelo Módulo 1; não o execute manualmente.
- Janela de disponibilidade do servidor: 05:00 a 06:59 BRT nos dias agendados (Módulo 2).
- Os saldos exatos são necessários: R$ 2,00 em D+0 e em D+1, e R$ 1,00 em D+2. Saldo insuficiente causa falha no Módulo 2.
- A conta credora pode ser CPF ou CNPJ neste plano (diferente do Pix Automático, que exige CNPJ).

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-07-03 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/067b39f242f01c59725b5d0be800cb7c/FVP-Payments-API-v5.0.0-Scheduling-Restricted-FVP.xlsx)

---

[↑ FVP Restrita](FVP/PT/Manual/Scheduled) · [◀ Portabilidade de Crédito](FVP/PT/Manual/Scheduled/Portabilidade) · [Gerenciamento de Cliente ▶](FVP/PT/Manual/Scheduled/Gerenciamento-de-Cliente)


---

*Conteúdo baixado em 16/09/2026, 15:38:02*
