# Enrollments v2.2.0

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Enrollments-v2.2.0](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Enrollments-v2.2.0)
**Slug:** `Phase-3-Services/Enrollments-v2.2.0`

---

---
title: Enrollments API v2.2.0
---

[← Phase 3 - Services](Phase-3-Services)

# Overview

Enrollments is the no-redirect journey. The customer enrols a device once, and
after that a payment is authorised on that device instead of through a browser
redirect.

Four plans: the enrolment itself, payments over an enrolment, automatic payments
over an enrolment, and the webhook that notifies the receiver of a payment status
change.

Version 2.3.0-rc.1 is also published and has its own page.

# Before you start

- The Software Statement registered in the Participant Directory must carry the software_origin_uris the test plan uses.
- The test user needs a valid account in the sandbox able to receive and complete a payment.
- The enrolment has to be completed before the payment plans can run. They act on an enrolment that already exists, not on one they create.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Enrollments API - v2.2.0 - Conformance Suite | enrollment_test-plan_v2-2 | 17 | 27/09/2025 |
| Enrollments API - v2.2.0 - Automatic Payments - Conformance Suite | no-redirect-automatic-payments_api_test-plan_v2-2 | 8 | 02/10/2025 |
| Enrollments API - v2.2.0 - Payments - Conformance Suite | no-redirect-payments_api_test-plan_v2-2 | 11 | 27/09/2025 |
| Enrollments API - v2.2.0 - Payments Webhook - Conformance Suite | no-redirect-payments-webhook_test-plan_v2-2 | 3 | 23/08/2025 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Enrollments API - v2.2.0 - Conformance Suite - 23 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Enrollments API - v2.2.0 - Automatic Payments - Conformance Suite - 32 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.paymentAmount<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Enrollments API - v2.2.0 - Payments - Conformance Suite - 26 fields</summary>

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
<summary>Enrollments API - v2.2.0 - Payments Webhook - Conformance Suite - 24 fields</summary>

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
<summary>Enrollments API - v2.2.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_api_preflight_test-module_v2n2 | Validates the mTLS certificate, obtains an access token with the configured Directory client_id, generates an SSA and checks the mandatory configuration fields before the plan runs. |
| enrollments_api_expired-postauthorisation-enrollment_test-module_v2-2 | Checks an enrollment left at AWAITING_ENROLLMENT expires after five minutes, reaching REJECTED with cancelledFrom DETENTORA and rejectionReason REJEITADO_TEMPO_EXPIRADO_ENROLLMENT. |
| enrollments_api_expired-preauthorisation-enrollment_test-module_v2-2 | Checks an enrollment left at AWAITING_ACCOUNT_HOLDER_VALIDATION expires after fifteen minutes, reaching REJECTED with REJEITADO_TEMPO_EXPIRADO_ACCOUNT_HOLDER_VALIDATION. |
| enrollments_api_expired-prerisksignal-enrollment_test-module_v2-2 | Checks an enrollment left at AWAITING_RISK_SIGNALS expires after five minutes, reaching REJECTED with rejectionReason REJEITADO_TEMPO_EXPIRADO_RISK_SIGNALS. |
| enrollments_api_invalid-parameters_test-module_v2-2 | Checks POST enrollments refuses a missing x-fapi-interaction-id and a wrongly signed body with 400, and missing or invalid fields with PARAMETRO_NAO_INFORMADO or PERMISSOES_INVALIDAS. |
| enrollments_api_invalid-public-key_test-module_v2-2 | Checks FIDO registration is refused with PUBLIC_KEY_INVALIDA when the attestation carries an unusable credentialPublicKey, leaving the enrollment REJECTED. |
| enrollments_api_invalid-status-options_test-module_v2-2 | Checks fido-registration-options is refused with 401 while the enrollment is still at AWAITING_ACCOUNT_HOLDER_VALIDATION, and that the status is unchanged afterwards. |
| enrollments_api_rejected-postauthorisation-enrollment_test-module_v2-2 | Checks an enrollment at AWAITING_ENROLLMENT can be rejected through PATCH, reaching REJECTED with REJEITADO_MANUALMENTE, after which fido-registration-options no longer works. |
| enrollments_api_rejected-preauthorisation-enrollment_test-module_v2-2 | Checks an enrollment still at AWAITING_ACCOUNT_HOLDER_VALIDATION can be rejected through PATCH, reaching REJECTED with cancelledFrom INICIADORA and REJEITADO_MANUALMENTE. |
| enrollments_api_invalid-origin_test-module_v2-2 | Checks FIDO registration is refused with ORIGEM_FIDO_INVALIDA when clientDataJSON.origin is not the origin published on the SSA, leaving the enrollment REJECTED with REJEITADO_FALHA_FIDO. |
| enrollments_api_invalid-challenge_test-module_v2-2 | Checks FIDO registration is refused with CHALLENGE_INVALIDO when clientDataJSON.challenge is not the issued one, leaving the enrollment REJECTED with REJEITADO_FALHA_FIDO. |
| enrollments_api_core-enrollment_test-module_v2-2 | Runs a device enrollment end to end, from POST enrollments through risk signals, account holder authorisation and FIDO registration, to an AUTHORISED enrollment keeping its enrollmentName. |
| enrollments_api_invalid-rpid_test-module_v2-2 | Checks fido-registration-options is refused with RP_INVALIDA when the rp field names a domain that is not the institution's, leaving the enrollment REJECTED with REJEITADO_FALHA_FIDO. |
| enrollments_api_risk-signals_test-module_v2-2 | Checks an enrollment carrying every risk signal reaches AUTHORISED with an expirationDateTime returned, and that a payment consent can then be signed and authorised with the same signals. |
| enrollments_api_max-challenges_test-module_v2-2 | Checks fido-registration-options returns the same challenge for a repeated idempotency key and fails with MAXIMO_CHALLENGES_ATINGIDO for a new one on the same enrollmentId. |
| enrollments_api_rejected-holder-mismatch_test-module_v2-2 | Checks an enrollment is rejected with REJEITADO_TITULARIDADE_DIVERGENTE when the account holder who authorises it differs from the one declared on the request. |
| enrollments_api_missing-required-risk-signals_test-module_v2-2 | Checks POST risk-signals fails with PARAMETRO_NAO_INFORMADO when the mandatory deviceId is absent, and the enrollment moves to REJECTED with cancelledFrom DETENTORA. |

</details>

<details>
<summary>Enrollments API - v2.2.0 - Automatic Payments - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_automatic-payments_authorised-executed-scheduled-successfully_v2-2 | Runs weekly automatic Pix over an authorised enrollment, checking the adhesion payment settles as ACSC and the following recurring payment is scheduled as SCHD. |
| enrollments_api_automatic-payment_enrollment-limits_negative_test-module_v2-2 | Checks a first automatic Pix payment above the enrollment transactionLimit is refused, at the request or later as RJCT with LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO. |
| enrollments_api_debit-account-mismatch_test-module_v2-2 | Checks a recurring consent whose debtorAccount differs from the account linked to the enrollment fails authorisation with CONTA_DEBITO_DIVERGENTE_CONSENTIMENTO_VINCULO and ends RJCT. |
| enrollments_api_automatic_payments-unmatching-fields_test-module_v2-2 | Checks a recurring payment is refused with DETALHE_PAGAMENTO_INVALIDO when authorisationFlow is sent as HYBRID_FLOW, and again when recurringConsentId is left out. |
| enrollments_automatic-payments_sweeping-consent-not-authorised_v2-2 | Checks a recurring consent for sweeping accounts cannot be signed, sign-options failing with PARAMETRO_INVALIDO and the consent ending RJCT with FLUXO_NAO_SUPORTADO_PRODUTO. |
| enrollments_api_automatic-payments_enrollment-limits_v2-2 | Checks an automatic Pix payment above the enrollment transactionLimit is still accepted while it respects the consent limits, one payment settling as ACSC and a later one as SCHD. |
| enrollments_api_automatic-payment_sign-options-invalid-permission_test-module_v2-2 | Checks fido-sign-options fails with PERMISSAO_INVALIDA_VINCULO_CONSENTIMENTO when the enrollment holds only PAYMENTS_INITIATE and the consent is for automatic Pix. |
| enrollments_api_recurring-initiate_unhappy-missing-permission_sign-options-422_test-module_v2-2 | Checks authorisation of a recurring consent is refused with ORIGEM_FIDO_INVALIDA when the FIDO assertion carries an origin that cannot be verified. |

</details>

<details>
<summary>Enrollments API - v2.2.0 - Payments - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_api_invalid-status-sign-options_test-module_v2-2 | Checks fido-sign-options for a payment consent is refused with STATUS_VINCULO_INVALIDO while the enrollment is still at AWAITING_ENROLLMENT. |
| enrollments_api_payments-pre-account-holder-validation_test-module_v2-2 | Checks a payment consent cannot be authorised while the enrollment sits at AWAITING_ACCOUNT_HOLDER_VALIDATION, the authorise call failing and the consent staying AWAITING_AUTHORISATION. |
| enrollments_api_payments-pre-enrollment_test-module_v2-2 | Checks a payment consent cannot be authorised while the enrollment sits at AWAITING_ENROLLMENT, the authorise call failing with STATUS_VINCULO_INVALIDO and the consent ending REJECTED. |
| enrollments_api_payments-core_test-module_v2-2 | Runs a no-redirect payment end to end over an authorised enrollment with an indefinite term consent, through to a payment accepted in ACSC. |
| enrollments_api_revoked-enrollment_test-module_v2-2 | Checks an AUTHORISED enrollment can be revoked through PATCH, reaching REVOKED with revocationReason REVOGADO_MANUALMENTE, after which a payment consent can no longer be signed. |
| enrollments_api_payments-keys-swap_test-module_v2-2 | Checks a consent signed with a private key other than the one registered at enrollment is refused with 422 RISCO, and stays REJECTED when signed again with the matching key. |
| enrollments_api_payments-unmatching-fields_test-module_v2-2 | Checks a Pix payment is refused with DETALHE_PAGAMENTO_INVALIDO when authorisationFlow is sent as HYBRID_FLOW, and again when consentId is left out. |
| enrollments_api_excessive-transactionLimit_test-module_v2-2 | Checks a payment above the enrollment transactionLimit is refused, at the request or later as RJCT with rejectionReason VALOR_ACIMA_LIMITE. |
| enrollments_api_excessive-dailyLimit_test-module_v2-2 | Checks payments stop once the enrollment dailyLimit is exhausted, the payment beyond it ending RJCT with VALOR_ACIMA_LIMITE and its consent reaching CONSUMED. |
| enrollments_api_excessive-dailyLimit-schd_test-module_v2-2 | Checks payments dated for future days are still accepted and left in SCHD once the enrollment dailyLimit for the current day has been exhausted. |
| enrollments_api_multiple-consents-core_test-module_v2-2 | Runs a no-redirect payment on an account that needs more than one authorisation, checking the consent moves from PARTIALLY_ACCEPTED to AUTHORISED and the payment settles as ACSC. |

</details>

<details>
<summary>Enrollments API - v2.2.0 - Payments Webhook - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| enrollments_api_webhook-rejected_test-module_v2-2 | Checks the institution's webhook endpoint is called over mTLS when an enrollment is rejected before authorisation, carrying x-webhook-interaction-id and a timestamp within the test window. |
| enrollments_api_webhook-revoked_test-module_v2-2 | Checks the webhook endpoint is called with eventType STATE_CHANGED when an AUTHORISED enrollment is revoked, the enrollment ending REVOKED with revocationReason REVOGADO_MANUALMENTE. |
| enrollments_api_webhook_event-type_test-module_v2-2 | Checks a webhook with eventType DATA_CHANGED is sent when the account holder changes transactionLimit, dailyLimit or expirationDateTime on an AUTHORISED enrollment. |

</details>

# Spreadsheet

[CS-Enrollments-API-v2.2.0.xlsx](uploads/e94d7d41c55cb431d5ffb9f8671aa79c/CS-Enrollments-API-v2.2.0.xlsx)

# Change history

<details>
<summary>2026 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |

</details>

<details>
<summary>2025 - 3 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 02/10/2025 | The automatic payments plan over an enrolment was released. | No |  |
| 27/09/2025 | The enrolment plan and the payments plan were released. | No |  |
| 23/08/2025 | The payments webhook plan was released. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*4 plans, 39 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:22*
