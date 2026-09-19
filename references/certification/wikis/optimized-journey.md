# Optimized Journey

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Optimized-Journey](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Optimized-Journey)
**Slug:** `Optimized-Journey`

---

---
title: Optimised Journey v1.0
---

# Overview

The Optimised Journey lets a customer authorise a payment and a data consent in
a single pass, instead of authorising each one separately. The test plans check
that the journey is accepted where the specification allows it, refused where it
does not, and that revoking one of the two consents has the right effect on the
other.

Three plans cover it. Two are the journeys themselves, one over Automatic
Payments sweeping and one over Enrollments, which is the no-redirect flow. The
third is the core plan, whose job is the opposite: it proves the journey is
refused on the APIs that must not accept it, Payments and Automatic Pix, and
when the consent carries the wrong permissions.

# Certification cut-off

A test plan created **before** the date below no longer counts for certification. Re-run it.

| Test plan | From | Why |
|---|---|---|
| optimised-journey_automatic-payments_test-plan_v1 | 11/05/2026 | Breaking change, [issue](https://gitlab.com/raidiam-conformance/open-finance/certification/-/issues/2691) |

# Before you start

- The Software Statement registered in the Participant Directory must carry the software_origin_uris the test plan uses.
- The test user needs one account in the sandbox able to receive and complete a payment, the same requirement the base Payments tests set.
- The revocation modules need a consent that can be revoked by hand during the run, and they check the effect on the other consent, so the pair must be genuinely linked rather than created separately.

# Test plans

| Plan | Technical name | Modules | Released |
|---|---|---|---|
| Optimised Journey - v1.0 - Automatic Payments API - v2.2.0 - Conformance Suite | optimised-journey_automatic-payments_test-plan_v1 | 5 | 04/11/2025 |
| Optimised Journey - v1.0 - Enrollments API - v2.2.0 - Conformance Suite | optimised-journey_no-redirect-payments_test-plan_v1 | 5 | 04/11/2025 |
| Optimised Journey - v1.0 - Core - Conformance Suite | optimised-journey_test-plan_v1 | 3 | 08/12/2025 |

# Configuration form

The fields each plan asks for, in the order the form presents them.

<details>
<summary>Optimised Journey - v1.0 - Automatic Payments API - v2.2.0 - Conformance Suite - 25 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.creditorName<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Optimised Journey - v1.0 - Enrollments API - v2.2.0 - Conformance Suite - 23 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.enrollmentsUrl<br>resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.discoveryUrl<br>directory.apibase<br>directory.client_id<br>directory.keystore |

</details>

<details>
<summary>Optimised Journey - v1.0 - Core - Conformance Suite - 29 fields</summary>

| Section | Fields |
|---|---|
| Server | server.discoveryUrl |
| Client | client.client_id<br>client.jwks<br>client.org_jwks |
| TLS certificates for client (used to make MTLS connections) | mtls.cert<br>mtls.key<br>mtls.ca |
| Resource | resource.loggedUserIdentification<br>resource.businessEntityIdentification<br>resource.debtorAccountIspb<br>resource.debtorAccountIssuer<br>resource.debtorAccountNumber<br>resource.debtorAccountType<br>resource.contractDebtorName<br>resource.contractDebtorIdentification<br>resource.creditorAccountIspb<br>resource.creditorAccountIssuer<br>resource.creditorAccountNumber<br>resource.creditorAccountAccountType<br>resource.paymentAmount<br>resource.creditorName<br>resource.creditorCpfCnpj<br>resource.consentUrl<br>resource.brazilCpf<br>resource.brazilCnpj<br>consent.productType<br>resource.brazilOrganizationId |
| Directory | directory.client_id<br>directory.keystore |

</details>

# Test modules

<details>
<summary>Optimised Journey - v1.0 - Automatic Payments API - v2.2.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| optimised-journey_sweeping_payments-core_test-module-v1 | Runs an optimised journey end to end with an automatic payments sweeping consent, and checks account balances can still be read afterwards. |
| optimised-journey_sweeping_invalid-request_test-module-v1 | Checks a recurring consent sent without the journey object fails authorisation, leaving the data consent REJECTED for INTERNAL_SECURITY_REASON and the recurring one for FLUXO_NAO_SUPORTADO_PRODUTO. |
| optimised-journey_sweeping_invalid-par_test-module-v1 | Checks the pushed authorisation request is refused when it does not carry the scope for the linked recurring consent. |
| optimised-journey_sweeping_revoked-consent_test-module-v1 | Checks that revoking the data consent leaves the recurring consent authorised while blocking access to account data. |
| optimised-journey_sweeping_revoked-recurring-consent_test-module-v1 | Checks that revoking the payments consent is reflected on both resources and leaves the journey link in place. |

</details>

<details>
<summary>Optimised Journey - v1.0 - Enrollments API - v2.2.0 - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| optimised-journey_enrollments-core_test-module-v1 | Runs an optimised journey end to end through the no-redirect enrollments flow. |
| optimised-journey_enrollments-invalid-request_test-module-v1 | Checks that an enrollment sent without the journey object fails authorisation, leaving the data consent REJECTED for INTERNAL_SECURITY_REASON and the enrollment for REJEITADO_SEGURANCA_INTERNA. |
| optimised-journey_enrollments-invalid_par_test-module-v1 | Checks the pushed authorisation request is refused when it does not carry the scope for the linked enrollment. |
| optimised-journey_enrollments_revoked-consent_test-module-v1 | Checks that revoking the data consent is reflected on the consent, on the enrollment and on access to account data. |
| optimised-journey_enrollments_revoked-enrollment_test-module-v1 | Checks that revoking the enrollment is reflected on both the enrollment and the data consent linked to it. |

</details>

<details>
<summary>Optimised Journey - v1.0 - Core - Conformance Suite</summary>

| Test module | What it does |
|---|---|
| optimised-journey_automatic-pix_test-module-v1 | Checks an optimised journey cannot be created for automatic pix payments. |
| optimised-journey_invalid-permissions_test-module-v1 | Checks a consent asking for a permission outside the accounts group is refused with COMBINACAO_PERMISSOES_INCORRETA. |
| optimised-journey_payments_test-module-v1 | Checks an optimised journey cannot be created for the payments API. |

</details>

# Spreadsheet

[CS-Optimised-Journey-v1.0.xlsx](uploads/bd5cd173fbb9bfa54d5fe079aa566570/CS-Optimised-Journey-v1.0.xlsx)

# Change history

<details>
<summary>2026 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |
| 11/05/2026 | The sweeping core module was extended: it now polls the Resources API, validates the self endpoint and checks the payment reaches ACSC, and it requires exactly one resource with status AVAILABLE. | Yes. A run that passed before this date does not prove the same thing. If the test user holds more than one resource in status AVAILABLE the module now fails, so the data has to be adjusted and the plan re-run. | [#2691](https://gitlab.com/raidiam-conformance/open-finance/certification/-/issues/2691) |

</details>

<details>
<summary>2025 - 2 changes</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 08/12/2025 | The core plan was released. It proves the journey is refused where the specification does not allow it: on the Payments and Automatic Pix APIs, and when the consent carries the wrong permissions. | No |  |
| 04/11/2025 | The Automatic Payments sweeping journey and the Enrollments no-redirect journey were both released, each with its core flow plus the invalid-PAR, missing-journey-object and revocation checks. | No |  |

</details>

# Notes

- The core plan is expected to fail the journey. A module there reporting a refusal is the pass condition, not a defect in your implementation.

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*3 plans, 13 modules. Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:38:13*
