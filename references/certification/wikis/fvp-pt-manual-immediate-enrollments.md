# Enrollments

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Enrollments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Manual/Immediate/Enrollments)
**Slug:** `FVP/PT/Manual/Immediate/Enrollments`

---

---
title: Enrollments
---

[← FVP Manual / FVP Aberta](FVP/PT/Manual/Immediate)

# FVP Manual - Enrollments

Esta página reúne os planos manuais da FVP para Enrollments. Cada seção descreve um plano: o que ele verifica, o que preparar antes da execução e os campos que devem ser preenchidos.

## ⚙️ 1) Enrollments API - v2.2.0 - Automatic Payments - Open FVP
Nome técnico: `fvp-no-redirect-automatic-pix-payments_open_test-plan-v2-2`

Valida o fluxo de pagamentos automáticos via Pix na Enrollments API v2.2.0 (Open FVP), cobrindo cadastro de dispositivo (enrollment), autorização de consentimento recorrente, execução do primeiro pagamento, agendamento dos pagamentos seguintes e cenários negativos de limite de valor e de produto não suportado.

### Antes de começar
**Saldo em conta**
- D+0: mínimo R$ 1,50 (obrigatório) - Cobre os dois pagamentos do plano: R$ 1,00 (primeiro) e R$ 0,50 (segundo, agendado).
- Janela de execução: Plano imediato: sem janela horária restrita. Execute a qualquer horário e mantenha o servidor do participante online durante toda a execução.
- O CPF/CNPJ da conta credora deve ser um CNPJ para o Pix Automático.
- loggedUserIdentification é sempre um CPF (11 dígitos), mesmo para devedor PJ.
- Para devedor PJ, preencha businessEntityIdentification e brazilCnpj (14 dígitos). Para devedor PF, preencha apenas brazilCpf (11 dígitos). Não envie brazilCpf e brazilCnpj ao mesmo tempo.

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
| fvp-enrollments_automatic-payments_authorised-executed-scheduled-successfully_v2-2 | Fluxo principal de pagamento automático sem redirecionamento: o primeiro pagamento é liquidado (ACSC) e o segundo é agendado (SCHD). |
| fvp-enrollments_api_automatic-payment_enrollment-limits_negative_test-module_v2-2 | Pagamento acima do limite por transação do enrollment é rejeitado (LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO). |
| fvp-enrollments_api_automatic-payments_enrollment-limits_v2-2 | Executa o primeiro pagamento no limite por transação (liquidado, ACSC) e agenda o pagamento seguinte (SCHD). |
| fvp-enrollments_automatic-payments_sweeping-consent-not-authorised_v2-2 | Consentimento com dados de sweeping accounts não é autorizado no fluxo sem redirecionamento (422 PARAMETRO_INVALIDO; rejeição FLUXO_NAO_SUPORTADO_PRODUTO). |

### Observações
- No módulo authorised-executed-scheduled-successfully, na etapa de redirecionamento é obrigatório selecionar prazo indeterminado para que o teste seja bem-sucedido.
- Este é um plano imediato (não agendado): os módulos executam numa única sessão, sem módulos agendados automaticamente. Não confunda com o plano No Redirect Automatic Pix Payments Scheduling (de longa duração, com Módulo 2 automático).
- Para o Pix Automático, o CPF/CNPJ da conta credora (Creditor Account CPF/CNPJ) deve ser um CNPJ.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-01-29 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/0b56b7b2771ef7fa92b9aa219d270885/FVP-Enrollments-API-v2.2.0-Automatic-Payments-Open-FVP.xlsx)

## ⚙️ 2) Enrollments API - v2.2.0 - Payments - Open FVP
Nome técnico: `fvp-no_redirect_payments_open_test-plan-v2-2`

Valida a jornada de pagamentos sem redirecionamento (JSR) via Enrollments API v2.2.0, incluindo o fluxo completo com FIDO (enrollment, sign-options, autorização e pagamento), cenários de erro em challenge, origin, chave pública, rp_id e campos inválidos, e tentativas de pagamento com o enrollment em estado inválido.

### Antes de começar
- Janela de execução: Plano imediato: sem janela de horário. Execute a qualquer momento e mantenha o servidor online durante a execução.
- A conta credora pode ser CPF ou CNPJ.
- Recomenda-se saldo suficiente na conta devedora para o pagamento de R$ 0,50 do módulo payments-core.
- loggedUserIdentification é sempre um CPF (11 dígitos), independentemente de o devedor ser PF ou PJ.
- Para devedor PJ, businessEntityIdentification e brazilCnpj devem ser CNPJ (14 dígitos).
- Os campos contractDebtorName e contractDebtorIdentification não são exigidos neste plano; são exclusivos dos planos de Pagamentos Automáticos.
- A instituição precisa ter um Software Statement registrado no Diretório com os software_origin_uris usados no plano.

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
| fvp-enrollments-api-pre-flight-test-v2 | Confere o registro do servidor no Diretório para as famílias enrollments (v2), payments-consents (v4.0.0) e payments-pix (v4.0.0). |
| fvp-enrollments_api_payments-core_open_test-module_v2-2 | Fluxo principal com FIDO: cria o enrollment, o consentimento e o sign-options, e conclui o pagamento até a liquidação (ACSC). |
| fvp-enrollments_api_invalid-challenge_open_test-module_v2-2 | Registro FIDO com challenge inválido é recusado (422 CHALLENGE_INVALIDO) e o enrollment é rejeitado por falha de FIDO. |
| fvp-enrollments_api_invalid-origin_open_test-module_v2-2 | Registro FIDO com origin inválida é recusado (422 ORIGEM_FIDO_INVALIDA) e o enrollment é rejeitado por falha de FIDO. |
| fvp-enrollments_api_invalid-public-key_open_test-module_v2-2 | Registro FIDO com chave pública inválida é recusado (422 PUBLIC_KEY_INVALIDA) e o enrollment é rejeitado. |
| fvp-enrollments_api_invalid-rpid_open_test-module_v2-2 | Registro FIDO com rp_id inválido é recusado (422 RP_INVALIDA) e o enrollment é rejeitado por falha de FIDO. |
| fvp-enrollments_api_invalid-status-sign-options_open_test-module_v2-2 | Chamada de sign-options com o enrollment em status inválido é recusada (422 STATUS_VINCULO_INVALIDO). |
| fvp-enrollments_api_payments-pre-enrollment_open_test-module_v2-2 | Autorização de consentimento antes de concluir o enrollment é recusada (422 STATUS_VINCULO_INVALIDO) e o consentimento é rejeitado. |
| fvp-enrollments_api_payments-unmatching-fields_open_test-module_v2-2 | Pagamentos com campos divergentes (authorisationFlow HYBRID_FLOW ou consentId ausente) são recusados ou rejeitados (DETALHE_PAGAMENTO_INVALIDO). |
| fvp-enrollments_api_payments-keys-swap_open_test-module_v2-2 | Consentimento assinado com chave diferente da registrada no enrollment é recusado (422 RISCO) e rejeitado. |

### Observações
- Este é um plano imediato (sem testes agendados): todos os módulos executam na mesma sessão manual, sem janela de horário específica.
- Apenas o módulo payments-core gera um pagamento bem-sucedido (R$ 0,50). Os módulos de erro (invalid-challenge, invalid-origin, invalid-public-key, invalid-rpid, invalid-status-sign-options, payments-keys-swap) não executam pagamento; payments-pre-enrollment e payments-unmatching-fields tentam pagar mas não devem ter sucesso.
- Para devedor PJ, preencha businessEntityIdentification e brazilCnpj. Para devedor PF, preencha brazilCpf. Nunca preencha PF e PJ ao mesmo tempo; a execução pode ser rejeitada.

### Histórico de alterações
| Data | Resumo do ajuste | Observações |
| --- | --- | --- |
| 2026-01-28 | Plano de teste criado na FVP. |  |
| 2026-07-13 | Documentação do plano reformulada. | Página própria com resumo, campos do formulário, módulos, avisos e histórico, em português e inglês. |

[Baixar a planilha deste plano](uploads/5186918b38ac15a8909d7f8e833b4ccc/FVP-Enrollments-API-v2.2.0-Payments-Open-FVP.xlsx)

---

[↑ FVP Aberta](FVP/PT/Manual/Immediate) · [◀ Jornada Otimizada](FVP/PT/Manual/Immediate/Jornada-Otimizada) · [Pagamentos Automáticos ▶](FVP/PT/Manual/Immediate/Pagamentos-Automaticos)


---

*Conteúdo baixado em 16/09/2026, 15:37:56*
