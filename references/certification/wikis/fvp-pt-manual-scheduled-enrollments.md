# Enrollments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Enrollments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Scheduled/Enrollments)
**Slug:** `FVP/PT/Manual/Scheduled/Enrollments`

---

---
title: Enrollments
---

[← FVP Manual / FVP Restrita](FVP/PT/Manual/Scheduled)

# FVP Manual - Enrollments

Esta página reúne os planos manuais da FVP para Enrollments. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Enrollments API - v2.2.0 - Automatic Payments Scheduling - Restricted FVP
Nome técnico: `fvp-no-redirect-automatic-pix-payments_restricted_test-plan-v2-2`

Valida o agendamento de pagamento automático Pix pela jornada No Redirect (JSR), cobrindo o fluxo completo de enrollment, criação e autorização de consentimento recorrente, disparo do pagamento e verificação do status agendado (SCHD), seguido da revogação do consentimento e do enrollment.

### Antes de começar
**Saldo em conta**
- D+0: indiferente R$ 0,00 - Recomenda-se saldo mínimo de R$ 1,00 para iniciar o teste.
- D+1: indiferente R$ 0,00
- D+2: mínimo R$ 1,00 (obrigatório)
- D+3: indiferente R$ 0,00
- Janela de execução: O Módulo 1 pode ser executado a qualquer horário. O Módulo 2 executa automaticamente às 21:00 BRT em D+3.
- O CPF/CNPJ da conta credora (recebedor) deve ser um CNPJ para o Pix Automático.
- D+N refere-se a N dias corridos após a execução do Módulo 1.
- Duração máxima do ciclo completo: 3 dias corridos (inclui dias não úteis).

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
| enrollments_api_automatic-payments_automatic-pix-scheduling_1-2_test-module_v2-2 | Cria o enrollment e o consentimento recorrente, autoriza e agenda o pagamento (SCHD) para verificação posterior. |
| enrollments_api_automatic-payments_automatic-pix-scheduling_2-2_test-module_v2-2 | Verifica que o pagamento agendado foi liquidado (ACSC) e revoga o consentimento e o enrollment (204). |

### Observações
- O Módulo 2 é agendado automaticamente pela suite para D+3 às 21:00 BRT, usando o consentId, paymentId, clientId e refresh_token guardados pelo Módulo 1; não o execute manualmente.
- Executar o Módulo 2 manualmente abre um ticket indevido contra a instituição, com link incorreto do Test Manager.
- O servidor do participante deve estar online e responsivo a partir das 21:00 BRT em D+3; se estiver offline na janela, o Módulo 2 falha e é preciso reexecutar desde o Módulo 1.
- Para o Pix Automático, o CPF/CNPJ da conta credora (Creditor Account CPF/CNPJ) deve ser um CNPJ.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-01-29 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/55b4b3274be99849b38be158d8f03c95/FVP-Enrollments-API-v2.2.0-Automatic-Payments-Scheduling-Restricted-FVP.xlsx)

## ⚙️ 2) Enrollments API - v2.2.0 - Payments Scheduling - Restricted FVP
Nome técnico: `fvp-no_redirect_payments_restricted_test-plan-v2-2`

Valida o agendamento e a liquidação de pagamentos Pix pela Jornada Sem Redirecionamento (Enrollments API v2.2.0): criação de consentimento com agendamento diário, autorização FIDO, emissão de pagamentos em D+1 e D+2 e confirmação de liquidação (ACSC) em execução posterior agendada.

### Antes de começar
**Saldo em conta**
- D+0: indiferente - Recomenda-se saldo mínimo de R$ 2,00 para iniciar o teste.
- D+1: mínimo R$ 1,00 (obrigatório)
- D+2: mínimo R$ 1,00 (obrigatório)
- D+3: indiferente
- Janela de execução: O Módulo 1 pode ser executado a qualquer horário. O Módulo 2 executa automaticamente às 05:00 BRT em D+3.
- A conta credora pode ser CPF ou CNPJ.
- Os dados de consentimento, pagamento e enrollment são persistidos automaticamente pela suite entre os Módulos 1 e 2.

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
| enrollments_api_payments_scheduled-pix-verification_1-2_test-module_v5 | Cria o enrollment com FIDO e agenda dois pagamentos Pix diários (D+1 e D+2), que ficam Agendados (SCHD). |
| enrollments_api_payments_scheduled-pix-verification_2-2_test-module_v5 | Verifica que os dois pagamentos agendados foram liquidados (ACSC). |

### Observações
- O Módulo 2 é agendado automaticamente pela Conformance Suite após a conclusão bem-sucedida do Módulo 1; não o execute diretamente (isso abre um ticket indevido contra a instituição, com link incorreto no Test Manager).
- Garanta que o servidor do participante esteja online e responsivo no horário agendado (05:00 BRT de D+3); se estiver offline, o Módulo 2 falha.
- D+N refere-se a N dias corridos após a execução do Módulo 1 (não dias úteis).

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-01-29 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |
| 2026-08-21 | Os dois módulos do plano passaram a validar a API de Pagamentos v5. | Os nomes dos módulos terminam em v5, e o consentimento e o pagamento passaram a ser conferidos contra a versão 5. |

[Baixar a planilha deste plano](uploads/5c954ae2ac9d9b9da4d1b906365c406c/FVP-Enrollments-API-v2.2.0-Payments-Scheduling-Restricted-FVP.xlsx)

---

[↑ FVP Restrita](FVP/PT/Manual/Scheduled) · [◀ FVP Restrita](FVP/PT/Manual/Scheduled) · [Pagamentos Automáticos ▶](FVP/PT/Manual/Scheduled/Pagamentos-Automaticos)


---

*Conteúdo baixado em 16/09/2026, 15:38:01*
