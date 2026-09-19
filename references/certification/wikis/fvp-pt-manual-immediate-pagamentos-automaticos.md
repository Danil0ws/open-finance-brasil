# Pagamentos Automaticos

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Pagamentos-Automaticos](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Pagamentos-Automaticos)
**Slug:** `FVP/PT/Manual/Immediate/Pagamentos-Automaticos`

---

---
title: Pagamentos Automáticos
---

[← FVP Manual / FVP Aberta](FVP/PT/Manual/Immediate)

# FVP Manual - Pagamentos Automáticos

Esta página reúne os planos manuais da FVP para Pagamentos Automáticos. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Automatic Payments API - v2.2.0 - Sweeping - Open FVP
Nome técnico: `fvp-automatic-sweeping-payments_open_test-plan-v2-2`

Valida a criação, autorização e execução de consentimentos e pagamentos recorrentes do tipo Sweeping Accounts (varredura de conta), incluindo expiração por prazo e por valor total, revogação, rejeição por credora divergente, bloqueio por startDateTime futuro e validação de scope.

### Antes de começar
- Janela de execução: Plano imediato: todos os módulos executam na mesma sessão, sem janela noturna. Mantenha o servidor do participante online durante a execução.
- Deve ser CNPJ (o Pix Automático não aceita CPF como conta credora).
- A conta devedora precisa de saldo suficiente para os pagamentos executados na sessão: os módulos core liquidam até R$ 1,00 no total, e o módulo wrong-creditor tenta pagamentos de R$ 300,00 cada.
- Se brazilCpf/brazilCnpj não estiverem configurados, os módulos core usam o CPF de fallback 99991111140.

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
| brazilCpf | Obrigatório | Valor do CPF a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação do Usuário Logado (substitui o antigo campo loggedUser). |
| brazilCnpj | Opcional | Valor do CNPJ a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação da Pessoa Jurídica (substitui o antigo campo businessEntity). |
| description | Opcional | Descrição livre desta execução. Opcional; pode ficar em branco. |

### Módulos e o que esperar
| Módulo de teste | O que faz |
| --- | --- |
| fvp_automatic-payments_api_revoked-consent_test-module_v2-2 | Consentimento sem prazo de expiração é revogado; após a revogação, tentativas de pagamento são bloqueadas (401/422) e o refresh token deixa de ser válido. |
| fvp_automatic-payments_api_sweeping-accounts-consent-edition_test-module_v2-2 | Tentativa de editar o consentimento de sweeping via PATCH é recusada (CAMPO_NAO_PERMITIDO) e os campos permanecem inalterados. |
| fvp_automatic-payments_api_sweeping-accounts-core_test-module_v2-2 | Fluxo principal de sweeping: dois pagamentos somando o valor total do consentimento (1,00 BRL) são liquidados (ACSC) e o consentimento é consumido. |
| fvp_automatic-payments_api_sweeping-accounts-totalAllowedAmount_test-module_v2-2 | Pagamento que ultrapassa o valor total permitido do consentimento é rejeitado (LIMITE_VALOR_TOTAL_CONSENTIMENTO_EXCEDIDO). |
| fvp_automatic-payments_api_expirationDateTime_test-module_v2-2 | Confirma que o consentimento expira na data definida (expirationDateTime) e que pagamentos após a expiração são bloqueados (401/422). |
| fvp_automatic-payments_api_invalid-scope_test-module_v2-2 | Consentimento autorizado com escopo incorreto falha no redirect ou tem o pagamento bloqueado (403). |
| fvp_automatic-payments_api_startDateTime_test-module_v2-2 | Pagamento emitido antes da data de início (startDateTime) do consentimento é rejeitado (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_sweeping-accounts-consents-core_test-module_v2-2 | Confirma que o consentimento de sweeping não expira em 5 minutos enquanto aguarda autorização (a suite espera 7 minutos antes de validar). |
| fvp_automatic-payments_api_sweeping-accounts-wrong-creditor_test-module_v2-2 | Diversas tentativas de pagamento com credora divergente (documento, proxy, conta) são rejeitadas (PAGAMENTO_DIVERGENTE_CONSENTIMENTO / PARAMETRO_NAO_INFORMADO). |

### Observações
- O módulo expirationDateTime aguarda 2 minutos (sleep da suite) para verificar a expiração do consentimento; reserve tempo extra na execução.
- O módulo sweeping-accounts-consents-core aguarda 7 minutos (sleep da suite) para validar que o consentimento não expira prematuramente.
- A conta credora (Creditor Account CPF/CNPJ) deve ser um CNPJ para planos de Pix Automático (incluindo Sweeping Accounts); CPF não é aceito como credora.
- Preencha brazilCpf OU brazilCnpj conforme o tipo do devedor (PF ou PJ); nunca os dois ao mesmo tempo.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2025-10-29 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/07e33112b5dcadbed4436436d24eefe8/FVP-Automatic-Payments-API-v2.2.0-Sweeping-Open-FVP.xlsx)

## ⚙️ 2) Automatic Payments API - v2.2.0 - Automatic Pix - Open FVP
Nome técnico: `fvp-automatic-pix-payments_open_test-plan-v2-2`

Valida o ciclo completo de pagamentos automáticos via Pix recorrente (v2.2.0) na modalidade Open FVP, cobrindo autorização e execução de consentimentos recorrentes, agendamento de parcelas, edição de limites do consentimento, revogação e rejeição por divergência de valores, datas ou credora.

### Antes de começar
**Saldo em conta**
- D+0: exatamente R$ 0,00 (obrigatório)
- D+1: exatamente R$ 0,00 (obrigatório)
- D+2: exatamente R$ 0,00 (obrigatório)
- D+3: mínimo R$ 1,00 (obrigatório) - Saldo mínimo para a execução do retry agendado (Módulo 3).
- Janela de execução: 21:00 a 23:59 BRT nos dias agendados (Módulos 2 e 3 de scheduling/retry)
- deve ser CNPJ (o Pix Automático não suporta CPF como credora)
- D+N refere-se a N dias corridos após a execução do Módulo 1.
- Os módulos de acompanhamento (Módulo 2 e Módulo 3) são iniciados automaticamente pela FVP no horário programado; não os execute manualmente.

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
| fvp_automatic-payments_api_automatic-pix-semanal-core_open_test-module_v2-2 | Fluxo principal de pagamento automático semanal: o primeiro pagamento é liquidado (ACSC) e a segunda parcela é agendada e depois cancelada. |
| fvp_automatic-payments_api_automatic-pix-scheduled-firstPayment_open_test-module_v2-2 | Primeiro pagamento sem conta devedora; valida que o servidor devolve a conta devedora após a autorização e agenda a parcela seguinte. |
| fvp_automatic-payments_api_automatic-pix-consent-edition-permissive_open_test-module_v2-2 | Edita o consentimento via PATCH (nome da credora, limite de valor, expiração) e confirma que o pagamento seguinte é agendado normalmente. |
| fvp_automatic-payments_api_automatic-pix-failed-firstPayment_open_test-module_v2-2 | Primeiro pagamento com valor divergente do consentimento é recusado (RJCT / PAGAMENTO_DIVERGENTE_CONSENTIMENTO); a parcela seguinte é agendada (SCHD). |
| fvp_automatic-payments_api_automatic-pix-revoked_open_test-module_v2-2 | Após liquidar o primeiro pagamento (ACSC), revoga o consentimento via PATCH; a parcela seguinte é cancelada ou rejeitada por consentimento revogado. |
| fvp_automatic-payments_api_automatic-pix-consent-edition-negative_open_test-module_v2-2 | Quatro tentativas inválidas de edição do consentimento via PATCH, todas recusadas com 422 (DETALHE_EDICAO_INVALIDO / PARAMETRO_NAO_INFORMADO). |
| fvp_automatic-payments_api_automatic-pix-firstPayment-invalid-creditor_open_test-module_v2-2 | Pagamento com conta credora diferente da do consentimento é rejeitado (RJCT / PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_automatic-pix-maximumVariableAmount_open_test-module_v2-2 | Parcela acima do valor máximo variável do consentimento é rejeitada (LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO). |
| fvp_automatic-payments_api_automatic-pix-no-limits_test-module_v2-2 | Consentimento sem limites de valor nem primeiro pagamento definido; as duas parcelas são agendadas (SCHD) normalmente. |
| fvp_automatic-payments_api_automatic-pix-invalid-dates-later_test-module_v2-2 | Parcela agendada além do prazo permitido é rejeitada (FORA_PRAZO_PERMITIDO). |
| fvp_automatic-payments_api_automatic-pix-referenceStartDate_test-module_v2-2 | Parcela com data anterior à data de início de referência do consentimento é rejeitada (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_automatic-pix-scheduling-before-firstPayment_test-module_v2-2 | Parcela agendada antes da data do primeiro pagamento é rejeitada (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |
| fvp_automatic-payments_api_automatic-pix-invalid-dates-sooner_test-module_v2-2 | Parcela agendada antes do prazo mínimo permitido é rejeitada (FORA_PRAZO_PERMITIDO). |
| fvp_automatic-payments_api_automatic-pix-unmatching-creditor_test-module_v2-2 | Pagamento com credora de ISPB do Banco Central e conta aleatória é aceito pela detentora (a falha é esperada apenas na liquidação no SPI). |
| fvp_automatic-payments_api_automatic-pix-fixedAmount_test-module_v2-2 | Parcela com valor diferente do valor fixo do consentimento é rejeitada (PAGAMENTO_DIVERGENTE_CONSENTIMENTO). |

### Observações
- Os módulos de acompanhamento (scheduling/retry) são agendados automaticamente pela Conformance Suite; não os execute manualmente.
- Mantenha o servidor do participante online e responsivo entre 21:00 e 23:59 BRT nos dias agendados para os módulos de retry.
- O Pix Automático é destinado exclusivamente a pagamentos para pessoas jurídicas (CNPJ). A conta credora deve pertencer a uma empresa; pagamentos para CPF não são válidos neste fluxo.
- O campo creditorCpfCnpj (Creditor Account CPF/CNPJ) deve ser preenchido com CNPJ para o Pix Automático; CPF não é aceito neste plano.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2025-10-29 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/42857dfedda1a19cadeb99a92b15635c/FVP-Automatic-Payments-API-v2.2.0-Automatic-Pix-Open-FVP.xlsx)

---

[↑ FVP Aberta](FVP/PT/Manual/Immediate) · [◀ Enrollments](FVP/PT/Manual/Immediate/Enrollments) · [Portabilidade de Crédito ▶](FVP/PT/Manual/Immediate/Portabilidade)


---

*Conteúdo baixado em 16/09/2026, 15:37:59*
