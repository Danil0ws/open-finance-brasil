# Jornada Otimizada

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Jornada-Otimizada](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Jornada-Otimizada)
**Slug:** `FVP/PT/Manual/Immediate/Jornada-Otimizada`

---

---
title: Jornada Otimizada
---

[← FVP Manual / FVP Aberta](FVP/PT/Manual/Immediate)

# FVP Manual - Jornada Otimizada

Esta página reúne os planos manuais da FVP para Jornada Otimizada. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Optimised Journey - v1.0 - Automatic Payments API - v2.2.0 - Open FVP
Nome técnico: `fvp-optimised-journey_automatic-payments_test-plan_v1`

Valida a Jornada Otimizada com pagamentos automáticos via sweeping, cobrindo criação e autorização de consentimentos vinculados, execução e polling de pagamentos, revogação de consentimentos de dados e de pagamentos, e cenários de falha no PAR e no objeto journey.

### Antes de começar
- Janela de execução: Plano imediato: sem janela de horário. Mantenha o servidor do participante online durante toda a execução.
- Deve ser PF, de mesma titularidade de quem executa o teste (os testes de sweeping exigem uma conta credora do mesmo titular do devedor).
- Saldo mínimo recomendado: R$ 2,00 na conta devedora no início da execução. Dois pagamentos de R$ 1,00 são executados (módulos payments-balances e revoked-consent_payments); os demais módulos não pagam.
- Todos os pagamentos da Jornada Otimizada são fixados em R$ 1,00 pela FVP, mesmo que outro paymentAmount seja enviado no JSON.

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
| fvp-optimised-journey_sweeping_payments-balances_test-module-v1 | Jornada Otimizada com sweeping: executa um pagamento vinculado (liquidado, ACSC), confirma a redução do saldo e revoga o consentimento. |
| fvp-optimised-journey_sweeping_revoked-consent_payments_test-module-v1 | Revoga o consentimento de dados antes do pagamento e confirma que o consentimento recorrente permanece e o pagamento é liquidado (ACSC). |
| fvp-optimised-journey_sweeping_revoked-recurring-consent_test-module-v1 | Revoga o consentimento recorrente via PATCH e confirma que tanto o consentimento recorrente quanto o de dados são atualizados corretamente. |
| fvp-optimised-journey_sweeping_invalid-par_test-module-v1 | PAR sem o recurringConsentId faz a autorização falhar; tanto o consentimento de dados quanto o recorrente são rejeitados. |
| fvp-optimised-journey_sweeping_invalid-request_test-module-v1 | Consentimento recorrente sem o objeto journey é aceito (201) mas rejeitado na autorização por falta de linkId. |

### Observações
- Todos os 5 módulos deste plano são imediatos: não há agendamento nem execução assíncrona. Mantenha o servidor do participante online durante toda a execução; se ficar indisponível no meio, os módulos seguintes falham e o plano precisa ser reexecutado do início.
- Para os testes de sweeping, todos os dados da conta credora (ISPB, agência, número, tipo, nome, CPF/CNPJ) devem ser da mesma titularidade de quem executa o teste; não use conta de terceiros.
- Todos os pagamentos da Jornada Otimizada são fixados em R$ 1,00 pela FVP, mesmo que outro paymentAmount seja enviado no JSON.
- Configure este plano com um creditor PF (mesma titularidade do devedor).

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-04-20 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/38ce1faf3ab955edec44547f566d41de/FVP-Optimised-Journey-v1.0-Automatic-Payments-API-v2.2.0-Open-FVP.xlsx)

## ⚙️ 2) Optimised Journey - v1.0 - Enrollments API - v2.2.0 - Open FVP
Nome técnico: `fvp-optimised-journey_no-redirect-payments_test-plan_v1`

Valida a Jornada Otimizada na Jornada Sem Redirecionamento (Enrollments API v2.2.0), cobrindo o ciclo completo de enrollment com FIDO, pagamento via FIDO_FLOW, revogação de consentimento, revogação de enrollment e cenários de falha por requisição inválida.

### Antes de começar
- Janela de execução: Plano imediato: sem janela de horário. Execute a qualquer momento com o servidor do participante online.
- A conta credora pode ser PF ou PJ (ambos aceitos neste plano).
- Saldo mínimo recomendado: R$ 2,00 na conta devedora no início da execução (dois pagamentos de R$ 1,00 são debitados: módulos enrollments-balances e enrollments_revoked-consent_payments).
- Diferente do plano de Pagamentos Automáticos (que exige a mesma titularidade), este plano aceita qualquer configuração de creditor.
- Todos os pagamentos da Jornada Otimizada são fixados em R$ 1,00 pela FVP, mesmo que outro paymentAmount seja enviado no JSON.

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
| brazilCpf | Obrigatório | Valor do CPF a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação do Usuário Logado (substitui o antigo campo loggedUser). |
| brazilCnpj | Opcional | Valor do CNPJ a ser utilizado na requisição de criação de consentimento. Também é usado como Identificação da Pessoa Jurídica (substitui o antigo campo businessEntity). |
| description | Opcional | Descrição livre desta execução. Opcional; pode ficar em branco. |

### Módulos e o que esperar
| Módulo de teste | O que faz |
| --- | --- |
| fvp-optimised-journey_enrollments-balances_test-module-v1 | Jornada Otimizada sem redirecionamento: conclui o enrollment com FIDO, executa um pagamento vinculado (liquidado, ACSC) e confirma a redução do saldo. |
| fvp-optimised-journey_enrollments_revoked-consent_payments_test-module-v1 | Revoga o consentimento de dados e confirma que o enrollment permanece autorizado e o pagamento seguinte é liquidado (ACSC). |
| fvp-optimised-journey_enrollments_revoked-enrollment_test-module-v1 | Revoga o enrollment e confirma que o consentimento de dados vinculado é rejeitado. |
| fvp-optimised-journey_enrollments-invalid-request_test-module-v1 | Enrollment sem o objeto journey faz a autorização falhar; o consentimento e o enrollment são rejeitados por segurança interna. |
| fvp-optimised-journey_enrollments-invalid_par_test-module-v1 | PAR apenas com o consentId (sem enrollmentId) faz a autorização falhar; o consentimento e o enrollment são rejeitados por segurança interna. |

### Observações
- Todos os módulos deste plano são imediatos: sem agendamento nem execução assíncrona. Mantenha o servidor do participante online durante a execução; se ficar indisponível no meio, os módulos seguintes falham e o plano precisa ser reexecutado do início.
- Dois pagamentos de R$ 1,00 são executados neste plano: enrollments-balances e enrollments_revoked-consent_payments. Os demais módulos não executam pagamento.
- Nos campos da conta credora (ISPB, agência, número, tipo, nome, CPF/CNPJ), use os dados da conta que receberá os pagamentos; pode ser PF ou PJ conforme a configuração.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-04-20 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/a5f4fe0e615dbe770f6876e161e0e9e9/FVP-Optimised-Journey-v1.0-Enrollments-API-v2.2.0-Open-FVP.xlsx)

## ⚙️ 3) Optimised Journey - v1.0 - Core - Open FVP
Nome técnico: `fvp-optimised-journey_test-plan_v1`

Valida que a Jornada Otimizada (journey.isLinked=true) não pode ser executada com a API de pagamentos automáticos via Pix nem com a API de pagamentos avulsos, confirmando a rejeição do consentimento em ambos os fluxos.

### Antes de começar
- Janela de execução: Plano imediato: sem janela de horário. Execute a qualquer momento com o servidor do participante online.
- Configure este plano com um creditor PJ (CNPJ).
- Nenhum pagamento é executado (todos os módulos são fluxos de rejeição): o saldo da conta devedora é indiferente, basta que a conta exista, esteja ativa e seja elegível para autorizar o consentimento.
- Todos os pagamentos da Jornada Otimizada são fixados em R$ 1,00 pela FVP, mesmo que outro paymentAmount seja enviado no JSON.

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
| fvp-optimised-journey_automatic-pix_test-module-v1 | Confirma que a Jornada Otimizada não pode ser usada com pagamentos automáticos via Pix: o consentimento recorrente e o de dados são rejeitados. |
| fvp-optimised-journey_payments_test-module-v1 | Confirma que a Jornada Otimizada não pode ser usada com pagamentos avulsos: o consentimento de pagamento expira e é rejeitado, junto com o de dados. |

### Observações
- O módulo de pagamentos avulsos instrui a suite a aguardar 5 minutos (sleep) antes de consultar o status do pagamento.
- Todos os módulos deste plano são fluxos de rejeição: nenhum pagamento é debitado.
- Configure este plano com um creditor PJ (CNPJ).
- Todos os módulos são imediatos: não há agendamento nem execução assíncrona; basta manter o servidor do participante online durante a execução.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-04-20 | Plano de teste criado na FVP. |  |
| 2026-05-18 | Módulo de permissões inválidas movido para a FVP Automática. | O módulo passou a ser executado no plano automático. |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/4e9b620e201e4a4085f598f3d5d9fe8a/FVP-Optimised-Journey-v1.0-Core-Open-FVP.xlsx)

---

[↑ FVP Aberta](FVP/PT/Manual/Immediate) · [◀ FVP Aberta](FVP/PT/Manual/Immediate) · [Enrollments ▶](FVP/PT/Manual/Immediate/Enrollments)


---

*Conteúdo baixado em 16/09/2026, 15:37:57*
