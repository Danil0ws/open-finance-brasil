# Produto

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica/Produto](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/PT/Automatica/Produto)
**Slug:** `FVP/PT/Automatica/Produto`

---

---
title: Testes de Produto
---

[← FVP Automática](FVP/PT/Automatica)

# FVP Automática - Testes de Produto

Esta categoria reúne os módulos funcionais por API que percorrem o fluxo até a autorização do consentimento e se encerram nesse ponto, razão pela qual dispensam interação do usuário. A lista abaixo descreve cada módulo e o que ele verifica.

## Módulos e o que esperar
| Módulo de teste | O que verifica |
| --- | --- |
| fvp-payments-consents-server-certificate-v2 | Valida que os certificados dos endpoints do servidor seguem o padrão brasileiro (cadeia RFC5246-7.4.2, CA OPF) no token, no registration e em até 12 endpoints funcionais. |
| fvp_payments_consents_api_bad-logged_test-module_v5 | Usa um cliente recém-registrado para criar um consentimento de pagamento com payload válido porém fictício; espera 201 e valida a assinatura do JWT. |
| fvp_consents_api_bad-logged_test-module_v3-3-1 | Usa um cliente recém-registrado para criar um consentimento de dados com payload válido porém fictício; espera 201 e valida a resposta. |
| fvp-payments_api_pixscheduling-dates-unhappy_test-module_v5 | Cinco cenários negativos de datas no consentimento de pagamento (data e agendamento juntos, hoje, passado, futuro distante, sem data); espera 422 (DATA_PAGAMENTO_INVALIDA / PARAMETRO_NAO_INFORMADO). |
| fvp-payments_api_recurring-payments-consent-limit_test-module_v5 | Verifica que consentimentos de pagamento recorrente que violam as regras de limite (datas fora da janela, quantidade acima do permitido) são recusados com 422. |
| fvp-payments_api_recurring-payments-wrong-custom-quantity_test-module_v5 | Verifica que um consentimento recorrente personalizado com menos pagamentos que o mínimo permitido é recusado com 422 PARAMETRO_INVALIDO. |
| fvp-payments_api_dict_test-module_v5 | Verifica erro quando o localInstrument é DICT e um QR Code é enviado; espera 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp-payments_api_manu-fail_test-module_v5 | Verifica erro quando o localInstrument é MANU e um QR Code ou proxy é enviado; espera 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp-payments_api_qres-code-enforcement_test-module_v5 | Verifica que um QR Code é obrigatório quando o localInstrument é QRES; sem o qrcode, espera 422 PARAMETRO_NAO_INFORMADO. |
| fvp-payments_api_force-check-signature_test-module_v5 | Verifica que uma requisição de consentimento com assinatura inválida é recusada com 400 (e que uma assinatura válida retorna 201). |
| fvp-payments_api_consents_negative_test-module_v5 | Cinco cenários inconsistentes no consentimento de pagamento (tipo de pagamento, tipo de pessoa, moeda, data e x-fapi-interaction-id inválidos); espera 400/422 PARAMETRO_INVALIDO. |
| fvp-payments_api_json-accept-header-jwt-returned_test-module_v5 | Verifica que, ao enviar um cabeçalho Accept JSON no GET de consentimento, o servidor retorna 200 (com JWT) ou 406. |
| fvp-payments_api_consent-purpose-validation-unhappy-path-invalid-combination_test-module_v5 | Verifica que o consentimento é recusado (422 PROPOSITO_INVALIDO) quando o propósito do pagamento é incompatível com a data ou o agendamento informado. |
| fvp-consents_api_extension-invalid-status_test-module_v3-3-1 | Verifica que um consentimento não pode ser estendido enquanto está em AWAITING_AUTHORISATION; a chamada de extensão retorna 401 ou 403. |
| fvp-consents_api_negative_test-module_v3-3-1 | Diversos cenários negativos de combinação de permissões e de datas no consentimento de dados; espera 422 (COMBINACAO_PERMISSOES_INCORRETA, DATA_EXPIRACAO_INVALIDA) ou 400. |
| fvp-consents_api_bad-consents_test-module_v3-3-1 | Verifica que consentimentos incompatíveis são recusados: permissões PF e PJ juntas (422 PERMISSAO_PF_PJ_EM_CONJUNTO) e x-fapi-interaction-id ausente ou inválido (400). |
| fvp-consents_api_permission-groups_test-module_v3-3-1 | Verifica que a API de consentimento aceita todos os grupos de permissão válidos, retornando 201 com as permissões correspondentes ou 422 SEM_PERMISSOES_FUNCIONAIS_RESTANTES quando o servidor não suporta o grupo. |
| fvp-enrollments_api_invalid-parameters_test-module_v2-2 | Verifica que uma inscrição (enrollment) com parâmetros inválidos é recusada: cabeçalho ou assinatura incorretos (400) e campos ausentes ou inválidos (422 PARAMETRO_NAO_INFORMADO / PARAMETRO_INVALIDO / PERMISSOES_INVALIDAS). |
| fvp_dcr_automatic-payments_api_automatic-pix-invalid-creditor_open_test-module_v2-2 | Verifica que um consentimento de Pix Automático com dados de credor inválidos (duas contas PJ, ou uma PF) é recusado com 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp_dcr_automatic-payments_api_automatic-pix-invalid-parameters_open_test-module_v2-2 | Verifica que um consentimento de Pix Automático com campos inválidos (fixedAmount como texto, primeira data no passado) é recusado com 422 (PARAMETRO_INVALIDO / DATA_PAGAMENTO_INVALIDA). |
| fvp_dcr_automatic-payments_api_automatic-pix-negative-consent_open_test-module_v2-2 | Verifica que um consentimento de Pix Automático com valores que violam as regras de negócio (limites fixo/variável incoerentes) é recusado com 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp_dcr_automatic-payments_api_negative-consents_test-module_v2-2 | Verifica as validações do POST de consentimento recorrente: campo sweeping ausente, datas incoerentes e x-fapi-interaction-id ausente ou inválido; espera 422/400. |
| fvp_dcr_automatic-payments_api_rejected-consent_test-module_v2-2 | Verifica que um consentimento recorrente é REJECTED quando o PATCH é chamado antes da aprovação, com rejectedBy USUARIO, rejectedFrom INICIADORA e motivo REJEITADO_USUARIO. |
| fvp_dcr_automatic-payments_api_sweeping-accounts-invalid-creditor_test-module_v2-2 | Verifica que um consentimento de sweeping com conta de credor inválida (diferente do usuário logado) é recusado com 422 DETALHE_PAGAMENTO_INVALIDO. |
| fvp_credit-portability_api_invalid_token_test-module_v1 | Verifica que o endpoint POST /portabilities da Portabilidade de Crédito responde no Diretório e recusa um token de client_credentials com 401 ou 403. |
| fvp-optimised-journey_invalid-permissions_test-module-v1 | Verifica falha quando um consentimento de jornada otimizada é criado com combinação de permissões incorreta; espera 422 COMBINACAO_PERMISSOES_INCORRETA. |

[Baixar a planilha desta categoria](uploads/3740a0139b5f3c92944ea40db49aa197/FVP-Product-tests.xlsx)

---

[↑ FVP Automática](FVP/PT/Automatica) · [◀ Testes de Diretório](FVP/PT/Automatica/Diretorio) · [FVP Manual ▶](FVP/PT/Manual)


---

*Conteúdo baixado em 16/09/2026, 15:37:53*
