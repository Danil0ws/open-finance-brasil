# Enrollments v2.3.0 rc.1

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Enrollments-v2.3.0-rc.1](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Enrollments-v2.3.0-rc.1)
**Slug:** `Phase-3-Services/Enrollments-v2.3.0-rc.1`

---

---
title: Enrollments API v2.3.0-rc.1
---

[← Phase 3 - Services](Phase-3-Services)

# Overview

Release candidate 1 of Enrollments version 2.3.0, the no-redirect journey. The
plans mirror the ones in version 2.2.0: the enrolment, payments over an
enrolment, automatic payments over an enrolment, and the payments webhook.

Version 2.2.0 remains published and has its own page.

# Before you start

- The Software Statement registered in the Participant Directory must carry the software_origin_uris the test plan uses.
- The test user needs a valid account in the sandbox able to receive and complete a payment.
- The enrolment has to be completed before the payment plans can run.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Enrollments API - v2.3.0-rc.1 - Conformance Suite | enrollment_test-plan_v2-3 | 22 | 28/08/2026 |
| Enrollments API - v2.3.0-rc.1 - Automatic Payments - Conformance Suite | no-redirect-automatic-payments_api_test-plan_v2-3 | 8 | 28/08/2026 |
| Enrollments API - v2.3.0-rc.1 - Payments - Conformance Suite | no-redirect-payments_api_test-plan_v2-3 | 11 | 28/08/2026 |
| Enrollments API - v2.3.0-rc.1 - Payments Webhook - Conformance Suite | no-redirect-payments-webhook_test-plan_v2-3 | 3 | 28/08/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Conformance Suite - 26 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |
| Other | resource.topOrigin<br>client.registration_client_uri<br>client.registration_access_token |

</details>

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Automatic Payments - Conformance Suite - 32 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.paymentAmount<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Payments - Conformance Suite - 26 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Payments Webhook - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.authorisationServerId |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.brazilOrganizationId<br>resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_api_preflight_test-module_v2-3 | Validates the mTLS certificate, obtains an access token with the Directory client_id, generates an SSA and checks the mandatory fields are present. |
| enrollments_api_expired-postauthorisation-enrollment_test-module_v2-3 | Checks an enrollment left at AWAITING_ENROLLMENT expires after five minutes and is rejected with REJEITADO_TEMPO_EXPIRADO_ENROLLMENT. |
| enrollments_api_expired-preauthorisation-enrollment_test-module_v2-3 | Checks an enrollment left at AWAITING_ACCOUNT_HOLDER_VALIDATION expires after fifteen minutes and is rejected with REJEITADO_TEMPO_EXPIRADO_ACCOUNT_HOLDER_VALIDATION. |
| enrollments_api_expired-prerisksignal-enrollment_test-module_v2-3 | Checks an enrollment left at AWAITING_RISK_SIGNALS expires after five minutes and is rejected with REJEITADO_TEMPO_EXPIRADO_RISK_SIGNALS. |
| enrollments_api_invalid-parameters_test-module_v2-3 | Checks enrollment creation is refused when the headers, the signature or the payload are wrong, covering PARAMETRO_NAO_INFORMADO, PERMISSOES_INVALIDAS and PARAMETRO_INVALIDO. |
| enrollments_api_invalid-public-key_test-module_v2-3 | Refuses a FIDO registration whose attestation carries an invalid credentialPublicKey, returning PUBLIC_KEY_INVALIDA and leaving the enrollment REJECTED. |
| enrollments_api_invalid-status-options_test-module_v2-3 | Refuses fido-registration-options while the enrollment is still at AWAITING_ACCOUNT_HOLDER_VALIDATION, and confirms the status is unchanged afterwards. |
| enrollments_api_rejected-postauthorisation-enrollment_test-module_v2-3 | Checks the initiator can reject an enrollment at AWAITING_ENROLLMENT, giving cancelledFrom INICIADORA and REJEITADO_MANUALMENTE, after which FIDO registration is refused. |
| enrollments_api_rejected-preauthorisation-enrollment_test-module_v2-3 | Checks the initiator can reject an enrollment still at AWAITING_ACCOUNT_HOLDER_VALIDATION, with cancelledFrom INICIADORA and rejectionReason REJEITADO_MANUALMENTE. |
| enrollments_api_invalid-origin_test-module_v2-3 | Rejects a FIDO registration whose clientDataJSON.origin is not the origin registered on the software statement, with ORIGEM_FIDO_INVALIDA and REJEITADO_FALHA_FIDO. |
| enrollments_api_invalid-challenge_test-module_v2-3 | Rejects a FIDO registration built over a challenge the server never issued, returning CHALLENGE_INVALIDO and REJEITADO_FALHA_FIDO. |
| enrollments_api_core-enrollment_test-module_v2-3 | Runs the enrollment journey end to end, from creation through risk signals and FIDO registration to AUTHORISED, keeping the enrollmentName that was sent. |
| enrollments_api_invalid-rpid_test-module_v2-3 | Rejects a fido-registration-options request naming a relying party outside the registered domain, returning RP_INVALIDA and REJEITADO_FALHA_FIDO. |
| enrollments_api_risk-signals_test-module_v2-3 | Runs an enrollment carrying every risk signal and a limited expirationDateTime, then authorises a payment consent through it. |
| enrollments_api_max-challenges_test-module_v2-3 | Checks fido-registration-options reuses the same challenge under one idempotency key and returns MAXIMO_CHALLENGES_ATINGIDO when a different key asks for another. |
| enrollments_api_rejected-holder-mismatch_test-module_v2-3 | Checks the enrollment is rejected with REJEITADO_TITULARIDADE_DIVERGENTE when the account holder who authorises differs from the one it was opened for. |
| enrollments_api_missing-required-risk-signals_test-module_v2-3 | Rejects the enrollment when a mandatory risk signal is missing, returning PARAMETRO_NAO_INFORMADO and cancelledFrom DETENTORA. |
| enrollments_api_embedded-cross-origin-flow_test-module_v2-3 | Completes an enrollment from inside an iframe, with clientDataJSON.crossOrigin true and a topOrigin already registered on the software statement. |
| enrollments_api_embedded-revoked-top-origin-rejection_test-module_v2-3 | Checks a credential stops being usable once its topOrigin is removed from the software statement, so consent authorisation then fails with ORIGEM_FIDO_INVALIDA. |
| enrollments_api_embedded-untrusted-top-origin-rejection_test-module_v2-3 | Rejects FIDO registration when the hosting topOrigin is not registered on the software statement, with ORIGEM_FIDO_INVALIDA and REJEITADO_FALHA_FIDO. |
| enrollments_api_optional-limit-absence_test-module_v2-3 | Confirms transactionLimit is absent from an AUTHORISED enrollment when no custom limit was set during authorisation. |
| enrollments_api_custom-high-transaction-limit_test-module_v2-3 | Checks a transactionLimit set above 500.00 during authorisation is accepted and returned unchanged on the AUTHORISED enrollment. |

</details>

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Automatic Payments - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_automatic-payments_authorised-executed-scheduled-successfully_v2-3 | Runs automatic Pix over an enrollment, with the first payment reaching ACSC and the following weekly payment left scheduled as SCHD. |
| enrollments_api_automatic-payment_enrollment-limits_negative_test-module_v2-3 | Checks the first automatic Pix payment fails when its amount is above the enrollment transactionLimit, with LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO. |
| enrollments_api_debit-account-mismatch_test-module_v2-3 | Checks an automatic Pix consent naming a debtor account other than the enrolled one is refused with CONTA_DEBITO_DIVERGENTE_CONSENTIMENTO_VINCULO. |
| enrollments_api_automatic_payments-unmatching-fields_test-module_v2-3 | Checks a recurring payment fails with DETALHE_PAGAMENTO_INVALIDO when authorisationFlow does not match the consent or recurringConsentId is left out. |
| enrollments_automatic-payments_sweeping-consent-not-authorised_v2-3 | Refuses a sweeping recurring consent through the FIDO flow, with 422 PARAMETRO_INVALIDO at sign-options, leaving it RJCT with rejection.reason FLUXO_NAO_SUPORTADO_PRODUTO. |
| enrollments_api_automatic-payments_enrollment-limits_v2-3 | Checks a recurring payment above the enrollment transactionLimit still runs while it stays within the consent limits, reaching ACSC and then SCHD. |
| enrollments_api_automatic-payment_sign-options-invalid-permission_test-module_v2-3 | Refuses fido-sign-options with PERMISSAO_INVALIDA_VINCULO_CONSENTIMENTO when the enrollment does not carry RECURRING_PAYMENTS_INITIATE. |
| enrollments_api_recurring-initiate_unhappy-missing-permission_sign-options-422_test-module_v2-3 | Checks a recurring consent cannot be authorised when the FIDO assertion carries an unrecognised origin, returning ORIGEM_FIDO_INVALIDA. |

</details>

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Payments - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_api_invalid-status-sign-options_test-module_v2-3 | Refuses fido-sign-options for a payment consent with STATUS_VINCULO_INVALIDO while the enrollment is still at AWAITING_ENROLLMENT. |
| enrollments_api_payments-pre-account-holder-validation_test-module_v2-3 | Checks a payment consent cannot be authorised while the enrollment sits at AWAITING_ACCOUNT_HOLDER_VALIDATION, leaving it at AWAITING_AUTHORISATION. |
| enrollments_api_payments-pre-enrollment_test-module_v2-3 | Checks a payment consent authorised while the enrollment is at AWAITING_ENROLLMENT is refused with STATUS_VINCULO_INVALIDO and ends REJECTED. |
| enrollments_api_payments-core_test-module_v2-3 | Runs a payment end to end through the no-redirect flow, over a consent with no expiry, until the payment reaches ACSC. |
| enrollments_api_revoked-enrollment_test-module_v2-3 | Revokes an AUTHORISED enrollment, giving REVOKED with revocationReason REVOGADO_MANUALMENTE, after which fido-sign-options returns STATUS_VINCULO_INVALIDO. |
| enrollments_api_payments-keys-swap_test-module_v2-3 | Checks a consent signed with a key other than the one registered at enrollment is refused with RISCO, and cannot be authorised again with the right key. |
| enrollments_api_payments-unmatching-fields_test-module_v2-3 | Checks a payment fails with DETALHE_PAGAMENTO_INVALIDO when authorisationFlow does not match the consent or consentId is left out. |
| enrollments_api_excessive-transactionLimit_test-module_v2-3 | Refuses a payment whose amount is above the enrollment transactionLimit, returning VALOR_ACIMA_LIMITE on the request or on the payment itself. |
| enrollments_api_excessive-dailyLimit_test-module_v2-3 | Checks payments that take the enrollment past its dailyLimit are refused with VALOR_ACIMA_LIMITE, and that the consent ends CONSUMED. |
| enrollments_api_excessive-dailyLimit-schd_test-module_v2-3 | Checks payments dated for future days are still accepted beyond the enrollment dailyLimit, each of them reaching SCHD. |
| enrollments_api_multiple-consents-core_test-module_v2-3 | Runs a no-redirect payment over a consent that passes through PARTIALLY_ACCEPTED before AUTHORISED, until the payment reaches ACSC. |

</details>

<details>
<summary>Enrollments API - v2.3.0-rc.1 - Payments Webhook - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_api_webhook-rejected_test-module_v2-3 | Confirms the webhook endpoint is called over mTLS when an enrollment is rejected before the account holder has authorised it. |
| enrollments_api_webhook-revoked_test-module_v2-3 | Confirms the webhook endpoint is called with eventType STATE_CHANGED when an already AUTHORISED enrollment is revoked. |
| enrollments_api_webhook_event-type_test-module_v2-3 | Checks a webhook with eventType DATA_CHANGED is sent when transactionLimit, dailyLimit or expirationDateTime changes on an AUTHORISED enrollment. |

</details>

# Spreadsheet

[CS-Enrollments-API-v2.3.0-rc.1.xlsx](uploads/672bfa32ed0da74e271964ea67e2d764/CS-Enrollments-API-v2.3.0-rc.1.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 28/08/2026 | Release candidate 1 of version 2.3.0 released, with all four plans. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*4 plans, 44 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:22*
