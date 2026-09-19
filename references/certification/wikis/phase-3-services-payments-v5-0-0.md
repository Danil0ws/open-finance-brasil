# Payments v5.0.0

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Payments-v5.0.0](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Payments-v5.0.0)
**Slug:** `Phase-3-Services/Payments-v5.0.0`

---

---
title: Payments API v5.0.0
---

[← Phase 3 - Services](Phase-3-Services)

# Overview

Payment initiation, version 5.0.0. Seven plans: the core plan and six that each
take one part of the specification far enough to need its own run. QRDN and Change
QRDN for the dynamic QR code, APDN and APES for the payment arrangements, Timezone
for the date handling, and Withdraw.

Version 4.0.1 is also published and has its own page. Both are live in the suite
at the same time.

# Before you start

- The Software Statement registered in the Participant Directory must carry the software_origin_uris the test plan uses.
- The test user needs a valid account in the sandbox able to receive and complete a payment. Everything else in these plans depends on that account existing.
- The Timezone plan asserts behaviour around date boundaries. Run it aware of the UTC-3 offset, because a payment dated locally at 23:59 is a different day in UTC.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Payments API - v5.0.0 - Conformance Suite | payments_test-plan_v5 | 56 | 12/12/2025 |
| Payments API - v5.0.0 - APDN - Conformance Suite | payments-apdn_test-plan_v5 | 3 | 12/12/2025 |
| Payments API - v5.0.0 - APES - Conformance Suite | payments-apes_test-plan_v5 | 4 | 12/12/2025 |
| Payments API - v5.0.0 - Change QRDN - Conformance Suite | payments-change-qrdn_test-plan_v5 | 1 | 11/04/2026 |
| Payments API - v5.0.0 - QRDN - Conformance Suite | payments-qrdn_test-plan_v5 | 3 | 12/12/2025 |
| Payments API - v5.0.0 - Timezone - Conformance Suite | payments-timezone_test-plan_v5 | 4 | 12/12/2025 |
| Payments API - v5.0.0 - Withdraw - Conformance Suite | payments-withdraw_test-plan_v5 | 5 | 11/04/2026 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Payments API - v5.0.0 - Conformance Suite - 26 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl<br>server.authorisationServerId |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount<br>conditionalResources.brazilCpfTemporization<br>conditionalResources.brazilCnpjTemporization |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Payments API - v5.0.0 - APDN - Conformance Suite - 27 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.brazilApdnPaymentConsent<br>resource.brazilApdnCnpj<br>resource.transactionIdentifier<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Payments API - v5.0.0 - APES - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Payments API - v5.0.0 - Change QRDN - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.brazilQrdnPaymentConsent<br>resource.brazilQrdnCnpj<br>resource.transactionIdentifier<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Payments API - v5.0.0 - QRDN - Conformance Suite - 24 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.brazilQrdnPaymentConsent<br>resource.brazilQrdnCnpj<br>resource.transactionIdentifier<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Payments API - v5.0.0 - Timezone - Conformance Suite - 23 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Payments API - v5.0.0 - Withdraw - Conformance Suite - 29 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.paymentAmount<br>resource.brazilQresPaymentConsent<br>resource.brazilQrdnPaymentConsent1<br>resource.brazilQrdnPaymentConsent2<br>resource.transactionIdentifier<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Payments API - v5.0.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_preflight_test-module_v5 | Validates the test configuration before the other modules run, covering the consent URL, the mTLS certificate, the directory client_id and that the consent version is v5. |
| payments_api_no-debtor-account_test-module_v5 | Checks a DICT consent created without a debtorAccount still reaches ACSC, with the account chosen by the user during authorisation. |
| payments_api_account-type_test-module_v5 | Confirms a debtorAccount of type SLRY is refused with PARAMETRO_INVALIDO, and that a payment sent with authorisationFlow as HYBRID_FLOW still reaches ACSC. |
| payments_api_consents_rejection-reason_test-module_v5 | Checks a consent carries the right rejectionReason for identical creditor and debtor accounts, for a rejection by the user, and for an expired authorisation window. |
| payments_api_contenttype-jwt-refreshtoken_test-module_v5 | Checks the refresh token is not rotated, and that the consents and payments endpoints still return a JWT when the accept header is not application/jwt. |
| payments_api_e2eid_test-module_v5 | Verifies the endToEndId is validated before a payment is accepted, refusing a missing one with PARAMETRO_NAO_INFORMADO and a malformed one with PARAMETRO_INVALIDO. |
| payments_api_incorrect-cpf-proxy_test-module_v5 | Checks a DICT payment carrying an invalid CPF as the proxy key ends as RJCT with DETALHE_PAGAMENTO_INVALIDO or PAGAMENTO_RECUSADO_DETENTORA. |
| payments_api_inic-pix-response_test-module_v5 | Runs a payment with localInstrument INIC and a transaction identifier through to ACSC, validating the consent and payment responses along the way. |
| payments_api_invalid-token_test-module_v5 | Verifies each payments endpoint accepts only the right grant, refusing a client_credentials token on POST payments and an authorisation code token on GET, PATCH and POST consents. |
| payments_api_negative_test-module_v5 | Confirms a payment whose currency or amount differs from the consent ends as RJCT with PAGAMENTO_DIVERGENTE_CONSENTIMENTO, and that a matching one reaches ACSC. |
| payments_api_pixscheduling-dates-unhappy_test-module_v5 | Checks a scheduled consent is refused with DATA_PAGAMENTO_INVALIDA when the date is today, in the past, beyond D+740 or duplicated, and with PARAMETRO_NAO_INFORMADO when no date is sent. |
| payments_api_pixscheduling-endtoend-unhappy_test-module_v5 | Checks a scheduled payment whose endToEndId carries the wrong hour, 01 instead of 15 UTC, is refused with PARAMETRO_INVALIDO. |
| payments_api_pixscheduling-patch-detentora_test-module_v5 | Follows a scheduled payment cancelled at the holding institution from SCHD to CANC, with cancelledFrom as DETENTORA and reason CANCELADO_AGENDAMENTO. |
| payments_api_pixscheduling-patch-iniciadora_test-module_v5 | Checks a scheduled payment cancelled through PATCH by the initiator moves from SCHD to CANC, with cancelledFrom as INICIADORA and reason CANCELADO_AGENDAMENTO. |
| payments_api_pixscheduling-patch-unhappy_test-module_v5 | Confirms PATCH is refused with PAGAMENTO_NAO_PERMITE_CANCELAMENTO when cancelledBy carries an invalid rel, and when the payment is in a state that cannot be cancelled. |
| payments_api_pixscheduling-schd-accepted_test-module_v5 | Runs the core scheduled payment journey, with the payment dated 350 days ahead, through to SCHD. |
| payments_api_qres-good-email-proxy_test-module_v5 | Runs a QRES payment carrying a valid email address as the proxy key through to an accepted state, ACSC. |
| payments_api_qres-good-phone-number-proxy_test-module_v5 | Runs a QRES payment carrying a valid phone number as the proxy key through to an accepted state, ACSC. |
| payments_api_qres-mismatched-consent-payment_test-module_v5 | Checks a payment whose QR code differs from the one consented ends as RJCT with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| payments_api_qres-mismatched-proxy_test-module_v5 | Confirms a consent is refused when the Pix key inside the static QR code differs from the proxy sent in the payload, ending as REJECTED with QRCODE_INVALIDO. |
| payments_api_qres-with-transaction-identifier_test-module_v5 | Rejects a QRES payment that carries a transactionIdentification, ending as RJCT with DETALHE_PAGAMENTO_INVALIDO. |
| payments_api_qres-wrong-amount-proxy_test-module_v5 | Verifies a consent is refused when the amount inside the static QR code differs from the amount in the payload, ending as REJECTED with VALOR_INVALIDO. |
| payments_api_real-email-invalid-creditor-proxy_test-module_v5 | Checks a DICT payment sent to an invalid creditor account ends as RJCT with DETALHE_PAGAMENTO_INVALIDO or PAGAMENTO_RECUSADO_DETENTORA. |
| payments_api_fake-email-proxy_test-module_v5 | Checks a DICT payment carrying an unregistered email address as the proxy key ends as RJCT with DETALHE_PAGAMENTO_INVALIDO or PAGAMENTO_RECUSADO_DETENTORA. |
| payments_api_x-fapi_test-module_v5 | Requires x-fapi-interaction-id on the consents, payments and PATCH payments endpoints, refusing a request without it and echoing the value back when it is sent. |
| payments_api_dict-pix-response_test-module_v5 | Runs a payment with localInstrument DICT through to ACSC, validating the consent and payment responses against the specification. |
| payments_api_dict_test-module_v5 | Rejects a consent declaring localInstrument DICT while also carrying a qrCode, with DETALHE_PAGAMENTO_INVALIDO. |
| payments_api_manu-fail_test-module_v5 | Checks a consent declaring localInstrument MANU is refused with DETALHE_PAGAMENTO_INVALIDO when it carries a qrCode, and again when it carries a proxy. |
| payments_api_qres-code-enforcement_test-module_v5 | Requires the qrCode field on a consent declaring localInstrument QRES, refusing it with PARAMETRO_NAO_INFORMADO when the field is absent. |
| payments_api_force-check-signature_test-module_v5 | Confirms the consents endpoint accepts correctly signed requests and answers a badly signed one with 400. |
| payments_api_manu-pix-response_test-module_v5 | Runs a payment with localInstrument MANU, sent without a proxy or a qrCode, through to ACSC. |
| payments_api_consents_negative_test-module_v5 | Verifies the consents endpoint refuses an invalid payment type, person type, currency, date or x-fapi-interaction-id, and a missing additionalInformation field. |
| payments_api_phone-number-proxy_test-module_v5 | Runs a DICT payment addressed by a valid phone number as the proxy key through to an accepted state, ACSC. |
| payments_api_json-accept-header-jwt-returned_test-module_v5 | Confirms the consents endpoint answers a JSON accept header with either 406 or a 200 whose body is still a JWT. |
| payments_api_jti-reuse_test-module_v5 | Rejects a consent request that reuses the jti claim of an earlier request, answering it with 403. |
| payments_api_consumed-consent_test-module_v5 | Confirms a consent moves to CONSUMED after a payment attempt, whether that attempt failed or succeeded, and that reusing it is refused with CONSENTIMENTO_INVALIDO. |
| payments_api_idempotency_test-module_v5 | Verifies an invalid iss is refused with 403, and that reusing an idempotency key with a different payload returns ERRO_IDEMPOTENCIA on both POST and PATCH payments. |
| payments_api_nofunds_test-module_v5 | Confirms a consent for an amount beyond any available balance is rejected at authorisation with SALDO_INSUFICIENTE or VALOR_ACIMA_LIMITE. |
| payments_api_multiple-consents-conditional_test-module_v5 | Checks a consent needing more than one approval sits at PARTIALLY_ACCEPTED, refuses a payment until it completes, then reaches ACSC. Skipped when multiple accounts are unsupported. |
| payments_api_multiple-consents-no-funds-conditional_test-module_v5 | Checks a consent needing more than one approval, for an amount beyond any balance, is rejected with SALDO_INSUFICIENTE or VALOR_ACIMA_LIMITE. Skipped when unsupported. |
| payments_api_temporization-conditional_test-module_v5 | Checks a payment held for further verification at PDNG goes on to reach a final state, either ACSC or RJCT with NAO_INFORMADO. Skipped when temporisation is not configured. |
| payments_api_canc-temporization-conditional_test-module_v5 | Checks a payment cancelled while held at PDNG reaches CANC, with cancelledFrom as INICIADORA and reason CANCELADO_PENDENCIA. Skipped when temporisation is not configured. |
| payments_api_recurring-payments-consent-limit_test-module_v5 | Verifies recurring consents reaching beyond the two year window are refused with DATA_PAGAMENTO_INVALIDA, and that duplicate dates or more than 60 payments return PARAMETRO_INVALIDO. |
| payments_api_recurring-payments-custom-core_test-module_v5 | Runs a recurring consent carrying five custom dates and confirms all five payments are scheduled, each reaching SCHD. |
| payments_api_recurring-payments-daily-core_test-module_v5 | Runs a daily recurring consent for five payments and confirms every one of them reaches SCHD. |
| payments_api_recurring-payments-higher-quantity_test-module_v5 | Rejects a batch carrying more payments than the recurring consent allows, with PAGAMENTO_DIVERGENTE_CONSENTIMENTO, leaving the consent CONSUMED. |
| payments_api_recurring-payments-invalid-e2eid-startDate_test-module_v5 | Checks payments whose endToEndId dates do not match the weekly recurring consent are refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO, leaving the consent CONSUMED. |
| payments_api_recurring-payments-large-batch_test-module_v5 | Runs a daily recurring consent for the largest permitted batch, 60 payments, and confirms all of them reach SCHD. |
| payments_api_recurring-payments-monthly-core_test-module_v5 | Runs a monthly recurring consent due on the 31st and confirms the payments reach SCHD when short months are carried forward to the 1st. |
| payments_api_recurring-payments-unhappy-date-adjustment_test-module_v5 | Confirms monthly payments due on the 31st that move a short month backwards instead of forwards are refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| payments_api_recurring_payments_weekly_test-module_v5 | Runs a weekly recurring consent for five Monday payments and confirms every one of them reaches SCHD. |
| payments_api_recurring-payments-wrong-amount_test-module_v5 | Confirms a recurring batch in which one payment carries an amount different from the consent ends as RJCT with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| payments_api_recurring-payments-lower-quantity_test-module_v5 | Rejects a batch carrying fewer payments than the recurring consent allows, with PAGAMENTO_DIVERGENTE_CONSENTIMENTO, leaving the consent CONSUMED. |
| payments_api_recurring-payments-wrong-custom-quantity_test-module_v5 | Rejects a custom recurring consent carrying a single date, below the permitted minimum, with PARAMETRO_INVALIDO. |
| payments_api_unmatching-loggedUser_test-module_v5 | Confirms a consent authorised by someone other than the loggedUser it was created with is rejected with AUTENTICACAO_DIVERGENTE. |
| payments_api_consent-purpose-validation-unhappy-path-invalid-combination_test-module_v5 | Rejects a consent whose purpose does not match its date or schedule, for example IMMEDIATE with a future date, with PROPOSITO_INVALIDO. |

</details>

<details>
<summary>Payments API - v5.0.0 - APDN - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_apdn-mismatched-consent-payment_test-module_v5 | Checks a payment is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO when the consent was created with localInstrument APDN and the payment is then sent as QRDN. |
| payments_api_apdn-unhappy-path_test-module_v5 | Checks APDN payments missing qrCode or proxy, or carrying a transactionIdentification outside 26 to 35 characters, are refused with DETALHE_PAGAMENTO_INVALIDO. |
| payments_api_apdn-good-happy-path_test-module_v5 | Runs an APDN payment over the NFC dynamic QR code flow, with a transactionIdentification of 26 to 35 characters, through to ACSC. |

</details>

<details>
<summary>Payments API - v5.0.0 - APES - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_apes-good-happy-path-with-txid_test-module_v5 | Runs an APES payment over the NFC static QR code flow, carrying a transactionIdentification of up to 25 characters, through to ACSC. |
| payments_api_apes-good-happy-path-without-txid_test-module_v5 | Runs an APES payment over the NFC static QR code flow where the QR code holds no TxId and no transactionIdentification is sent, through to ACSC. |
| payments_api_apes-mismatched-consent-payment_test-module_v5 | Checks a payment is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO when the consent was created with localInstrument APES and the payment is then sent as QRES. |
| payments_api_apes-code-unhappy-path-required_test-module_v5 | Verifies APES payments without qrCode or proxy, or breaking the transactionIdentification rules for a static QR code, are refused with DETALHE_PAGAMENTO_INVALIDO. |

</details>

<details>
<summary>Payments API - v5.0.0 - Change QRDN - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_pix-change-qrdn_test-module_v5 | Runs a Pix Troco payment where the consent carries a change object and the amount equals the purchase value plus the change value, through to ACSC. |

</details>

<details>
<summary>Payments API - v5.0.0 - QRDN - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_qrdn-good-proxy_test-module_v5 | Runs a payment from a valid dynamic QR code through to ACSC, then checks that reusing the same QRDN is refused with DETALHE_PAGAMENTO_INVALIDO or rejected with QRCODE_INVALIDO. |
| payments_api_qrdn-code-enforcement_test-module_v5 | Confirms a QRDN consent sent without the qrCode field is refused with PARAMETRO_NAO_INFORMADO, and that ibgeTownCode is mandatory for a COBV QR code. |
| payments_api_qrdn-with-qres-code_test-module_v5 | Rejects a consent declaring QRDN while carrying a static QR code, ending as REJECTED with QRCODE_INVALIDO. |

</details>

<details>
<summary>Payments API - v5.0.0 - Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_timezone_test-module_v5 | Confirms a payment created late in the evening, between 21:00 and 23:59 UTC-3, still reaches ACSC with the date handled in local time. |
| payments_api_multiple-consents-timezone-conditional_test-module_v5 | Checks a consent left at PARTIALLY_ACCEPTED overnight is rejected at midnight with TEMPO_EXPIRADO_AUTORIZACAO. Skipped when multiple accounts are unsupported. |
| payments_api_consent-bulk-cancel_negative_timezone_test-module_v5 | Confirms the bulk cancel endpoint answers 202 and cancels only what it may, leaving the D+1 payment at SCHD while the other four move to CANC. |
| payments_api_recurring-payments-patch_timezone_test-module_v5 | Confirms cancelling one scheduled payment by PATCH moves it to CANC with cancelledFrom as INICIADORA, and that the consent level bulk cancel then moves all five to CANC. |

</details>

<details>
<summary>Payments API - v5.0.0 - Withdraw - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| payments_api_pix-withdraw-qres_test-module_v5 | Runs a Pix Saque payment from a static QR code, with the amount matching the withdrawal value exactly, through to ACSC. |
| payments_api_pix-withdraw-exceeds-limit_test-module_v5 | Confirms a Pix Saque within the daytime withdrawal limit reaches ACSC, while one above it is rejected at authorisation with VALOR_ACIMA_LIMITE. |
| payments_api_pix-withdraw-change-invalid-date_test-module_v5 | Rejects a Pix Saque consent dated D+1 with DATA_PAGAMENTO_INVALIDA, since a withdrawal cannot be scheduled. |
| payments_api_pix-consents-multi-authorization-permission_test-module_v5 | Checks a WITHDRAW consent authorised from an account that needs full approval powers is rejected with PERMISSAO_INSUFICIENTE. Skipped when multiple authorisation levels are unsupported. |
| payments_api_pix-withdraw-invalid-amount_test-module_v5 | Confirms a Pix Saque consent whose amount exceeds the withdrawal value is refused, ending as REJECTED with VALOR_INVALIDO. |

</details>

# Spreadsheet

[CS-Payments-API-v5.0.0.xlsx](uploads/d7efe52b3ee4f6cbc37ef6dd44388cbe/CS-Payments-API-v5.0.0.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 11/04/2026 | The Change QRDN and Withdraw plans were added to version 5.0.0. | No |  |

</details>

<details>
<summary>2025 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 12/12/2025 | Version 5.0.0 released: the core plan plus APDN, APES, QRDN and Timezone. | No |  |

</details>

# Previous versions

These versions no longer run in the suite. Their test plans were removed.

| Version | Retired | Test plans |
|---|---|---|
| v3.0.0 | 12/06/2026 | [Spreadsheet](uploads/72e22bae7c4c23c22d8b7cfdbbf93afb/230801_Phase3V3.xlsx) |

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*7 plans, 76 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:24*
