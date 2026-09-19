# Automatic

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic)
**Slug:** `FVP/EN/Automatic`

---

---
title: Automatic FVP
---

[← FVP](FVP/EN)

# Automatic FVP

The Automatic FVP runs daily against every Authorisation Server registered in the Directory, starting at 04:00 Z, and covers the checks that do not depend on a user journey, such as Dynamic Client Registration (DCR), FAPI conformance, functional tests and Directory registration. In other words, it is made up of test modules that do not reach the redirect step. When a server fails a check, a ticket is opened in the participant's Service Desk. The modules are organised into the three categories shown below:

## Categories
- [DCR tests](FVP/EN/Automatic/DCR)
- [Directory tests](FVP/EN/Automatic/Directory)
- [Product tests](FVP/EN/Automatic/Product)

## Spreadsheet
[Download the spreadsheet with all automatic modules](uploads/486703dbffe6f5f8418cb0693efeb399/FVP-Automatic-tests.xlsx)

## Change history

<details>
<summary>2026 - 12 changes</summary>

**21 Aug · Plans** - Payments v4 is no longer executed in the Automatic FVP

The ten payments scenarios that ran twice, once on version 4 and once on version 5, now run only on version 5: bad-logged user consent, scheduling dates, recurring consent limit, mismatched custom quantity, DICT, MANU, QRES, signature check, negative consent and JWT in the accept header. Coverage did not change, what went away was the duplication on version 4.

**13 Aug · Plans** - Credit portability invalid token module renamed

The credit portability invalid token module is now called fvp_credit-portability_api_invalid_token_test-module_v1. The previous name ended in v3-3 and did not match the API version the module tests.

**03 Aug · Plans** - Eight new Directory checks in the Automatic FVP

The automatic plan now runs eight Directory modules, each checking something that was not reported separately before: API family completeness, scope and family coverage in both directions, functional certification URI, mandatory scopes, presentation metadata, scope role and security certification. The result stops being one pass or fail and now points at which check failed.

**29 Jul · Behavior** - Optimised Journey skipped when the consents endpoint is absent

The Optimised Journey invalid permissions module is skipped when the holder does not publish the data consents endpoint.

**22 Jul · Behavior** - Credit portability skipped when the holder does not offer the product

The credit portability invalid token module is skipped before dynamic registration when the holder has no portability endpoint registered.

**13 Jul · Documentation** - FVP documentation restructured

The FVP documentation was reorganized into per-plan pages, in Portuguese and English, with one spreadsheet per plan.

**11 Jun · Plans** - Payments v5 modules in the Automatic FVP

Eleven payments v5 modules joined the automatic plan alongside their v4 counterparts: negative consent, DICT, MANU, QRES, scheduling dates, recurring payment limits, bad signature, JSON/JWT accept header, consent purpose validation and bad logged user. On the same day, the automatic payments v1 bad logged user module was removed from the plan.

**18 May · Plans** - Optimised Journey in the Automatic FVP

Added fvp-optimised-journey_invalid-permissions_test-module-v1, which verifies that an optimised journey consent created with an incorrect permission combination is rejected.

**07 Apr · Plans** - Duplicated automatic payments modules removed

Three automatic payments v1 modules that were duplicated in the plan were removed, keeping only the current versions.

**19 Feb · Plans** - Automatic payments updated to version 2.2

The automatic payments module family moved to version 2.2, replacing the previous one: invalid creditor in Automatic Pix, invalid parameters, negative consent, negative consents, rejected consent and invalid creditor in sweeping.

**05 Feb · Plans** - Enrollments invalid parameters on version 2.2

Added fvp-enrollments_api_invalid-parameters_test-module_v2-2, which verifies that an enrollment with an invalid header, signature or fields is rejected.

**14 Jan · Plans** - Credit Portability in the Automatic FVP

Added fvp_credit-portability_api_invalid_token_test-module_v3-3, which verifies that the portabilities endpoint responds in the Directory and rejects a client_credentials token.

</details>

<details>
<summary>2025 - 3 changes</summary>

**22 May · Plans** - Enrollments invalid parameters modules updated

The enrollments invalid parameters modules v1 and v2 were updated and renamed, with no change to what they verify.

**27 Mar · Plans** - Automatic payments v2.0.0-rc.1

Six automatic payments v2.0.0-rc.1 modules joined the plan, covering invalid creditor and invalid parameters in Automatic Pix, negative and rejected consent, and invalid creditor in sweeping.

**26 Feb · Plans** - Consents updated to version 3.2

The four consent modules moved to version 3.2: incompatible consents, extension with invalid status, negative scenarios and permission groups.

</details>

<details>
<summary>2024 - 13 changes</summary>

**01 Nov · Plans** - Enrollments 2.0.0

Added the enrollments invalid parameters module on version 2, following the 2.0.0 API release.

**04 Oct · Plans** - Enrollments modules moved to the Manual FVP

Three enrollments modules that depend on the user journey left the automatic plan and now run only in the Manual FVP: invalid status options, payment keys swap and unmatching payment fields.

**23 Sep · Plans** - Automatic plan expanded

The plan nearly doubled in size, from 25 to 46 modules. It gained the consent v3 modules, the payments v4 ones (DICT, MANU, QRES, scheduling, recurrence limits, signature and accept header), the automatic payments v1 ones, DCR with tls_client_auth and the certification status check.

**24 Aug · Plans** - Enrollments in the Automatic FVP

The first enrollments modules started running in the Automatic FVP, covering invalid parameters and invalid status options.

**29 Jul · Plans** - Directory registration updated to version 2

The Directory registration module moved to directory_api_server-registration_test_module_v2, replacing the previous version.

**24 Jun · Plans** - New payments v3 scenarios

Added payments v3 test modules to the execution plan: fvp-payments_api_dict_test-module_v3, fvp-payments_api_manu-fail_test-module_v3, fvp-payments_api_pixscheduling-dates-unhappy_test-module_v3 and fvp-payments_api_qres-code-enforcement_test-module_v3.

**23 May · Frequency** - Daily execution

The execution routine changed to run daily, with tickets updated accordingly.

**23 May · Plans** - Happy consent scenarios

Added a happy scenario for consents v2 and v3, payments v3 and v4 and automatic payments v1; the modules run the DCR flow and a POST to the respective APIs: fvp_consents_api_bad-logged_test-module_v2, fvp_consents_api_bad-logged_test-module_v3, fvp_payments_consents_api_bad-logged_test-module_v3, fvp_payments_consents_api_bad-logged_test-module_v4 and fvp_automatic_payments_consents_api_bad-logged_test-module_v1.

**16 Apr · Certificates** - Signing certificate updated

Updated the signing certificate used by the tool for the private_key_jwt authentication method and the phase 3 flow.

**15 Apr · Behavior** - FAPI Unique and new DCR scenario

All servers are now tested using only private_key_jwt when verifying the well-known, regardless of support. Added dcr_api_fvp-unhappy-tls-client-auth_test_module, which attempts a DCR using tls_client_auth and expects the server to reject it.

**25 Mar · Behavior** - DCR with private_key_jwt for all

The DCR tests now use private_key_jwt for all servers regardless of support, plus execution with tls_client_auth for those that support that method.

**22 Jan · Plans** - Negative payments consent v3 scenarios

Added payments_api_consents_negative_no_redirect_test-module_v3, which runs 5 negative payments-consent v3 scenarios and 1 positive scenario.

**11 Jan · Plans** - Revoked-certificate test re-added

The dcr_api_fvp-revoked-certificate_test-module was added back to the execution and to institution notifications.

</details>

<details>
<summary>2023 - 16 changes</summary>

**13 Oct · Plans** - Negative payments consent v2 scenarios

Added payments_api_consents_negative_no_redirect_test-module_v2, which runs 5 negative payments-consent scenarios and 1 positive scenario.

**21 Sep · Plans** - Certification-status check

Added directory_api_certification-status_test-module, which verifies each API's certification status after the weekly automatic certification.

**08 Sep · Plans** - Revoked-certificate test removed

Removed dcr_api_fvp-revoked-certificate_test-module from the execution, at the Security WG's request.

**31 Aug · Behavior** - Server-selection criterion

The routine now includes all published Authorization Servers with a correctly formatted well-known, including duplicated well-knowns; previously only one server per well-known was tested.

**31 Aug · Certificates** - Happy DCR certificate updated (SERPRO)

The dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow_test-module now uses a BRCAC issued by CA SERPRO SSLv1, ensuring organizations accept this new certificate type.

**17 Aug · Certificates** - Revoked certificate and SERASA update

Added dcr_api_fvp-revoked-certificate_test-module, which runs the DCR flow presenting a revoked certificate and expects the server to reject it. The dcm-subject-dn-test-fvp and dcr-brcac2022-support-fvp tests now use a BRCAC issued by CA SERASA SSL EV V4.

**13 Jul · Plans** - Directory registration test and new ticket

Added directory_api_server-registration_test-module, which checks that institutions registered their servers correctly per the Directory Operation Guide (security and functional certifications present and valid metadata). A dedicated ticket now opens for failures in this test, for two possible tickets per server: one for the DCR tests and one for the Directory registration.

**06 Jul · Plans** - Server endpoint certificate test

Added fvp-payments-consents-server-certificate-v2, which confirms the certificate used on the server endpoints is aligned with the Brazilian certificate standards.

**29 Jun · Certificates** - Certificate update (SOLUTI G4)

The FAPI-DCR tests now use a BRCAC issued by CA SOLUTI SSL EV G4, ensuring organizations accept this new certificate type.

**15 Jun · Behavior** - x-fapi-interaction-id header in consents

Added the x-fapi-interaction-id header to the POST payments-consents request.

**01 Jun · Platform** - Log zip download on the result page

A button was added to the page sent to institutions when they fail the tests, allowing them to download logs as on the regular Conformance Suite.

**10 Mar · Messages** - Error details on the Service Desk ticket

The Service Desk notification now includes, alongside the failed tests, the identified failure hypothesis for the test.

**09 Mar · Behavior** - Server-selection criterion

The routine now includes all published Authorization Servers with a correctly formatted well-known; previously only servers with published consents or payments-consents endpoints were tested.

**02 Feb · Certificates** - Certificate update (SOLUTI G3)

The dcm-subject-dn-test-fvp and dcr-brcac2022-support-fvp tests now use a BRCAC issued by CA SOLUTI SSL EV G3.

**13 Jan · Certificates** - Certificate update (SERASA V3)

The dcm-subject-dn-test-fvp and dcr-brcac2022-support-fvp tests now use a BRCAC issued by CA SERASA SSL EV V3.

**12 Jan · Plans** - Three new DCR scenarios

Added the modules dcr-subjectdn-fvp (checks tls_subject_dn parsing across formats), dcr-brcac2022-support-fvp (acceptance of the new and old Brazilian transport certificate formats) and dcm-subject-dn-test-fvp (acceptance of a PUT that changes tls_subject_dn to a new certificate).

</details>

<details>
<summary>2022 - 8 changes</summary>

**22 Dec · Behavior** - Multiple-clients test

The dcr-multiple-clients module now returns a failure, instead of a warning, when the server accepts a DCR with a client_id already created for the same Software Statement.

**30 Nov · Behavior** - DCR delete test behaviour

The fapi1-advanced-final-brazildcr-client-delete-no-authorization-flow test now waits 1 minute between deleting the client and issuing a token.

**15 Nov · Platform** - Multiple servers support and mtls.ca fix

Fixed the issue, introduced in the 2022-11-08 release, where the leaf certificate was being sent in the intermediate CA chain. Implemented the ability to test multiple servers from the same organization registered in the Directory.

**08 Nov · Certificates** - mtls.ca chain adjusted

The intermediate certificate chain now sends only the intermediate and root certificates, removing unrelated intermediates, per RFC 5246.

**25 Oct · Platform** - Support for additional CAs

Implemented the ability to use multiple certificates in the same test plan, enabling tests that require more than one issued certificate.

**16 Aug · Platform** - New optional test and results page

Added dcr-test-multiple-clients (returns a warning if the server supports more than one client per server, during the adaptation period). Implemented the results page, with a unique link per institution to access results after the weekly execution.

**04 Aug · Plans** - Phase 3 tests support and removals

consents-bad-logged now calls both the payments-consents (phase 3) and consents (phase 2) endpoints. Removed dcr-subjectdn and dcr-test-attempt-client-takeover at the Security WG's request. The routine now obtains the payments-consents endpoint in addition to the phase 2 consents endpoint.

**01 Jul · Platform** - Platform release

Platform created with 23 test plans, including the 18 original FAPI-DCR tests and 5 specific functional tests (consents-bad-logged, dcr-test-sandbox-credentials, dcr_no_subject_type, dcr-subjectdn and dcr-test-attempt-client-takeover). Communication with institutions moved to the Service Desk (SysAid), with results delivered in a .zip file.

</details>

---

[↑ FVP](FVP/EN) · [◀ FVP](FVP/EN) · [DCR tests ▶](FVP/EN/Automatic/DCR)


---

*Conteúdo baixado em 16/09/2026, 15:37:33*
