# Automatic Payments v2.2.0

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Automatic-Payments-v2.2.0](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Automatic-Payments-v2.2.0)
**Slug:** `Phase-3-Services/Automatic-Payments-v2.2.0`

---

---
title: Automatic Payments API v2.2.0
---

[← Phase 3 - Services](Phase-3-Services)

# Overview

Recurring payments authorised once and executed repeatedly. Two arrangements,
each with its own set of plans: sweeping, which moves money between accounts the
same customer owns, and automatic Pix, which pays a third party on a schedule.

Eight plans in total. Both arrangements carry a core plan, a webhook plan for the
notification endpoint and a timezone plan for the date handling. Automatic Pix
adds two more for the retry behaviour, one of which exists to create the data the
other needs.

# Before you start

- The Software Statement registered in the Participant Directory must carry the software_origin_uris the test plan uses.
- The test user needs a valid account in the sandbox able to receive and complete a payment.
- The retry plans need a data set prepared in advance, covering both the intraday and the extraday retry scenarios. The auxiliary retry plan exists to create it. You may build the data another way, as long as it meets what the retry modules expect.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Automatic Payments API - v2.2.0 - Sweeping - Conformance Suite | automatic-payments_test-plan_v2-2 | 17 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Sweeping Timezone - Conformance Suite | automatic-payments-timezone_test-plan_v2-2 | 1 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Sweeping Webhook - Conformance Suite | automatic-payments-webhook_test-plan_v2-2 | 4 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Automatic Pix - Conformance Suite | automatic-pix-payments_test-plan_v2-2 | 29 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Automatic Pix Retry - Conformance Suite | automatic-pix-payments-retry_test-plan_v2-2 | 5 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Automatic Pix Retry Auxiliary - Conformance Suite | automatic-pix-payments-retry-auxiliary_test-plan_v2-2 | 2 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Automatic Pix Timezone - Conformance Suite | automatic-pix-payments-timezone_test-plan_v2-2 | 3 | 05/08/2025 |
| Automatic Payments API - v2.2.0 - Automatic Pix Webhook - Conformance Suite | automatic-pix-payments-webhook_test-plan_v2-2 | 1 | 05/08/2025 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Automatic Payments API - v2.2.0 - Sweeping - Conformance Suite - 27 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Sweeping Timezone - Conformance Suite - 25 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Sweeping Webhook - Conformance Suite - 28 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Conditional Resources | conditionalResources.brazilCpfJointAccount<br>conditionalResources.brazilCnpjJointAccount |
| Resource | resource.webhookWaitTime<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType |
| Directory | directory.discoveryUrl<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix - Conformance Suite - 28 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Retry - Conformance Suite - 19 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.intradayOnePaymentConsentId<br>resource.intradayTwoPaymentsConsentId<br>resource.extradayRetryAcceptedConsentId<br>resource.extradayRetryUnacceptedConsentId<br>resource.extraday422ValidationConsentId<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Retry Auxiliary - Conformance Suite - 34 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.referenceStartDate<br>resource.expirationDateTime<br>resource.isRetryAccepted<br>resource.interval<br>resource.recurringPaymentAmount<br>resource.recurringPaymentDate<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Timezone - Conformance Suite - 28 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Webhook - Conformance Suite - 30 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.webhookWaitTime<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Automatic Payments API - v2.2.0 - Sweeping - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_expirationDateTime_test-module_v2-2 | Checks that a consent turns CONSUMED once its expirationDateTime passes, and that recurring payments and token refresh are refused afterwards. |
| automatic-payments_api_invalid-scope_test-module_v2-2 | Checks that an authorisation asking for a scope that does not match the recurringConsentId is refused, and that a token carrying the wrong scope gets 403 on the payment. |
| automatic-payments_api_multiple-consents-core_test-module_v2-2 | Checks that a consent needing several authorisations stays PARTIALLY_ACCEPTED, refuses payments with CONSENTIMENTO_PENDENTE_AUTORIZACAO, then settles one to ACSC once fully authorised. |
| automatic-payments_api_negative-consents_test-module_v2-2 | Rejects consent creation when recurringConfiguration.sweeping is missing, when the dates are inconsistent, and when x-fapi-interaction-id is absent or malformed. |
| automatic-payments_api_rejected-consent_test-module_v2-2 | Checks that a PATCH sent before authorisation drives the consent to REJECTED, with rejectedBy USUARIO, rejectedFrom INICIADORA and reason REJEITADO_USUARIO. |
| automatic-payments_api_revoked-consent_test-module_v2-2 | Checks that a PATCH sent after authorisation drives an open ended consent to REVOKED, and that recurring payments and token refresh are then refused. |
| automatic-payments_api_startDateTime_test-module_v2-2 | Checks that a payment sent before the consent's startDateTime is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO, and that the consent stays AUTHORISED. |
| automatic-payments_api_sweeping-accounts-consent-edition_test-module_v2-2 | Checks that consent edition is not available on a sweeping accounts consent, the PATCH returning CAMPO_NAO_PERMITIDO with no field updated. |
| automatic-payments_api_sweeping-accounts-consents-core_test-module_v2-2 | Checks that a sweeping accounts consent with every periodic limit filled can be created and authorised, and that it does not expire while awaiting authorisation. |
| automatic-payments_api_sweeping-accounts-core_test-module_v2-2 | Checks that two sweeping accounts payments settle to ACSC and that the consent becomes CONSUMED once the agreed amount is used up. |
| automatic-payments_api_sweeping-accounts-invalid-cnpj_test-module_v2-2 | Checks that a sweeping accounts consent naming two creditors from different companies is refused with DETALHE_PAGAMENTO_INVALIDO. |
| automatic-payments_api_sweeping-accounts-invalid-creditor_test-module_v2-2 | Checks that a sweeping accounts consent whose creditor account differs from the logged user is refused with DETALHE_PAGAMENTO_INVALIDO. |
| automatic-payments_api_sweeping-accounts-limits_test-module_v2-2 | Exercises the per transaction limit, the daily amount limit and the daily quantity limit of a sweeping consent, each excess ending in a 422 or in an RJCT payment. |
| automatic-payments_api_sweeping-accounts-root-cnpj_test-module_v2-2 | Checks that sweeping payments succeed for several creditor CNPJs sharing the same root, as registered on the consent. |
| automatic-payments_api_sweeping-accounts-totalAllowedAmount_test-module_v2-2 | Checks that a sweeping payment breaching totalAllowedAmount is refused with LIMITE_VALOR_TOTAL_CONSENTIMENTO_EXCEDIDO, the consent remaining AUTHORISED. |
| automatic-payments_api_sweeping-accounts-wrong-creditor_test-module_v2-2 | Checks that a sweeping payment to a document, proxy or creditorAccount other than the consented one is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| automatic-payments_api_negative-payment_test-module_v2-2 | Checks that a sweeping payment sent with a future date and localInstrument AUTO is refused with DETALHE_PAGAMENTO_INVALIDO. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Sweeping Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_timezone_test-module_v2-2 | Checks that a sweeping payment dated in UTC-3 still settles to ACSC when it is created between 9pm and midnight Brazilian time. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Sweeping Webhook - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_webhook-acsc_test-module_v2-2 | Checks the webhook endpoint is called when a sweeping payment reaches ACSC and its consent reaches CONSUMED. |
| automatic-payments_api_webhook-multiple-consents_test-module_v2-2 | Checks the webhook endpoint is called when a multiple authorisation consent leaves PARTIALLY_ACCEPTED for AUTHORISED and then CONSUMED. |
| automatic-payments_api_webhook-rejected_test-module_v2-2 | Checks the webhook endpoint is called when a consent is patched to REJECTED before it has been authorised. |
| automatic-payments_api_webhook-revoked_test-module_v2-2 | Checks the webhook endpoint is called when an already authorised consent is patched to REVOKED. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_automatic-pix-invalid-creditor_test-module_v2-2 | Checks that an automatic pix consent naming two PJ creditors, or a single PF creditor, is refused with DETALHE_PAGAMENTO_INVALIDO. |
| automatic-payments_api_automatic-pix-invalid-parameters_test-module_v2-2 | Checks that an automatic pix consent with fixedAmount sent as a string is refused with PARAMETRO_INVALIDO, and one with a firstPayment dated D-1 with DATA_PAGAMENTO_INVALIDA. |
| automatic-payments_api_automatic-pix-negative-consent_test-module_v2-2 | Checks that an automatic pix consent combining fixedAmount with a variable amount, or a minimum above the maximum, is refused with DETALHE_PAGAMENTO_INVALIDO. |
| automatic-payments_api_automatic-pix-semanal-core_test-module_v2-2 | Runs a SEMANAL automatic pix consent end to end, the firstPayment settling to ACSC and a later scheduled payment cancelled to CANC. |
| automatic-payments_api_automatic-pix-mensal-core_test-module_v2-2 | Runs the same end to end flow at the MENSAL interval, the firstPayment settling to ACSC and a later scheduled payment cancelled to CANC. |
| automatic-payments_api_automatic-pix-trimestral-core_test-module_v2-2 | Covers the TRIMESTRAL interval, authorising the consent, settling the firstPayment to ACSC and cancelling a scheduled payment to CANC. |
| automatic-payments_api_automatic-pix-semestral-core_test-module_v2-2 | Covers the SEMESTRAL interval, authorising the consent, settling the firstPayment to ACSC and cancelling a scheduled payment to CANC. |
| automatic-payments_api_automatic-pix-anual-core_test-module_v2-2 | Covers the ANUAL interval, authorising the consent, settling the firstPayment to ACSC and cancelling a scheduled payment to CANC. |
| automatic-payments_api_automatic-pix-no-limits_test-module_v2-2 | Checks that a consent carrying no amount limits and no firstPayment still accepts two recurring payments, both reaching SCHD. |
| automatic-payments_api_automatic-pix-revoked_test-module_v2-2 | Checks that revoking the consent cancels the payment already scheduled, moving it to CANC with reason CANCELADO_AGENDAMENTO while the settled one stays ACSC. |
| automatic-payments_api_automatic-pix-failed-firstPayment_test-module_v2-2 | Checks that a recurring payment can still be scheduled to SCHD after the consent's firstPayment was rejected. |
| automatic-payments_api_automatic-pix-wrong-creditor_test-module_v2-2 | Checks that a firstPayment whose creditorAccount does not belong to the named creditor ends RJCT with TITULARIDADE_INCONSISTENTE or PAGAMENTO_RECUSADO_SPI. |
| automatic-payments_api_automatic-pix-firstPayment-invalid-creditor_test-module_v2-2 | Checks that a firstPayment sent with a creditorAccount number other than the one held on the consent is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| automatic-payments_api_automatic-pix-scheduled-firstPayment_test-module_v2-2 | Checks that a firstPayment dated in the future reaches SCHD, and that the server returns a debtorAccount after authorisation when none was sent at consent creation. |
| automatic-payments_api_automatic-pix-invalid-dates-sooner_test-module_v2-2 | Checks that a recurring payment scheduled sooner than D+2 is refused with FORA_PRAZO_PERMITIDO. |
| automatic-payments_api_automatic-pix-invalid-firstPayment-localInstrument_test-module_v2-2 | Checks that a firstPayment with paymentReference zero is refused with DETALHE_PAGAMENTO_INVALIDO when localInstrument is AUTO instead of MANU. |
| automatic-payments_api_automatic-pix-invalid-recurring-localInstrument_test-module_v2-2 | Checks that a scheduled recurring payment is refused with DETALHE_PAGAMENTO_INVALIDO when localInstrument is MANU instead of AUTO. |
| automatic-payments_api_automatic-pix-invalid-dates-later_test-module_v2-2 | Checks that a recurring payment scheduled later than D+10 is refused with FORA_PRAZO_PERMITIDO. |
| automatic-payments_api_automatic-pix-fixedAmount_test-module_v2-2 | Checks that a recurring payment whose amount differs from the consent's fixedAmount is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| automatic-payments_api_automatic-pix-minimumVariableAmount_test-module_v2-2 | Checks that a payment below the consent's minimumVariableAmount is still accepted and reaches SCHD, and that lowering the maximum under it by edition returns DETALHE_EDICAO_INVALIDO. |
| automatic-payments_api_automatic-pix-maximumVariableAmount_test-module_v2-2 | Checks that a payment above the consent's maximumVariableAmount is refused with LIMITE_VALOR_TRANSACAO_CONSENTIMENTO_EXCEDIDO. |
| automatic-payments_api_automatic-pix-referenceStartDate_test-module_v2-2 | Checks that a recurring payment whose paymentReference falls before the consent's referenceStartDate is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| automatic-payments_api_automatic-pix-unmatching-creditor_test-module_v2-2 | Checks that a scheduled recurring payment is still accepted when the creditorAccount does not belong to the creditor, since that only fails at settlement with the SPI. |
| automatic-payments_api_automatic-pix-scheduling-before-firstPayment_test-module_v2-2 | Checks that a recurring payment dated before the consent's firstPayment is refused with PAGAMENTO_DIVERGENTE_CONSENTIMENTO. |
| automatic-payments_api_automatic-pix-consent-edition-permissive_test-module_v2-2 | Checks that edition may loosen a consent, creditor name, maximumVariableAmount and expirationDateTime each updating on their own with updatedAtDateTime moving every time. |
| automatic-payments_api_automatic-pix-consent-edition-restrictive_test-module_v2-2 | Checks that shortening expirationDateTime by edition cancels the payment already scheduled beyond it to CANC, and that a new one is refused with FORA_PRAZO_PERMITIDO. |
| automatic-payments_api_automatic-pix-consent-edition-account-holder_test-module_v2-2 | Checks that an edition made by the account holder reaches the consent, setting maximumVariableAmount and turning useOverDraftLimit off, with a payment above the new limit refused. |
| automatic-payments_api_automatic-pix-consent-edition-negative_test-module_v2-2 | Rejects consent edition when the new expirationDateTime is in the past, when a maximumVariableAmount is added to a fixed amount consent, and when loggedUser or riskSignals are missing. |
| automatic-payments_api_automatic-pix-unmatching-loggedUser_test-module_v2-2 | Checks that a consent authorised by someone other than the loggedUser named at creation ends REJECTED with AUTENTICACAO_DIVERGENTE. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Retry - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_automatic-pix-intraday-core_test-module_v2-2 | Checks an intraday retry of a rejected payment, a fresh endToEndId for D+0 reaching SCHD, and passes only when run before midday UTC-3. |
| automatic-payments_api_automatic-pix-intraday-timezone_test-module_v2-2 | Checks that an intraday retry attempted after midday UTC-3, on a consent that already holds two rejected payments, is refused with FORA_PRAZO_PERMITIDO. |
| automatic-payments_api_automatic-pix-extraday-core_test-module_v2-2 | Checks an extraday retry on a consent with isRetryAccepted true, the D+1 attempt reaching SCHD and cancellation then refused with PAGAMENTO_NAO_PERMITE_CANCELAMENTO. |
| automatic-payments_api_automatic-pix-extraday-retry-unaccepted_test-module_v2-2 | Checks that an extraday retry is refused with LIMITE_TENTATIVAS_EXCEDIDO when the consent carries isRetryAccepted false. |
| automatic-payments_api_automatic-pix-retry-422-validation_test-module_v2-2 | Covers field validation on the retry endpoint, a missing endToEndId, an invalid date format and an endToEndId encoding D-1 each returning their own 422 code. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Retry Auxiliary - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_automatic-pix_auxiliary-one-payment_test-module_v2-2 | Auxiliary module that authorises an automatic pix consent from the configured values and creates one payment, logging the ids the retry tests need. |
| automatic-payments_api_automatic-pix_auxiliary-two-payments_test-module_v2-2 | Auxiliary module that authorises an automatic pix consent from the configured values and creates two payments, logging the ids the retry tests need. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Timezone - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_automatic-pix-scheduled-firstPayment-timezone_test-module_v2-2 | Checks that a firstPayment created between 9pm and midnight UTC-3 still settles to ACSC on the same Brazilian day. |
| automatic-payments_api_automatic-pix-receiver-revoked-consent-timezone_test-module_v2-2 | Checks that a revocation by the receiver late in the UTC-3 evening cancels a payment scheduled from D+2, CANCELADO_AGENDAMENTO naming the creditor as canceller. |
| automatic-payments_api_automatic-pix-user-revoked-consent-timezone_test-module_v2-2 | Checks that a revocation requested by the user late in the UTC-3 evening cancels a payment scheduled from D+2, CANCELADO_AGENDAMENTO naming the loggedUser as canceller. |

</details>

<details>
<summary>Automatic Payments API - v2.2.0 - Automatic Pix Webhook - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| automatic-payments_api_automatic-pix-webhook_test-module_v2-2 | Checks the webhook endpoint is called once for each automatic pix status change, one message for ACSC, one for SCHD and one for CANC. |

</details>

# Spreadsheet

[CS-Automatic-Payments-API-v2.2.0.xlsx](uploads/66718605716d3030cccad16b1a6069cd/CS-Automatic-Payments-API-v2.2.0.xlsx)

# Change history

<details>
<summary>2026 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |

</details>

<details>
<summary>2025 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 05/08/2025 | Version 2.2.0 released, with all eight plans: sweeping and automatic Pix, each with its core, webhook and timezone plans, plus the two retry plans. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*8 plans, 62 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:21*
