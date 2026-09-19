# Directory

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic/Directory](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic/Directory)
**Slug:** `FVP/EN/Automatic/Directory`

---

---
title: Directory tests
---

[← Automatic FVP](FVP/EN/Automatic)

# Automatic FVP - Directory tests

This category gathers the modules that validate the participant's registration in the Participants Directory, confirming that the Authorisation Server and the required data are present and consistent. The list below describes each module and what it verifies.

## Modules and what to expect
| Test module | What it verifies |
| --- | --- |
| directory_api_server-registration_test_module_v2 | Certifies the authorisation server's registration in the Directory: security and functional certifications, metadata, logo, scopes versus API families and Domain ROLEs. |
| directory_api_server-security-certification_test-module | Certifies that the authorisation server has at least one active Security Certification in the Directory, including the required BR-OF Adv. OP w/ Private Key, PAR (FAPI-BR v2), and that the certification URI follows the expected structure for its start date. |
| directory_api_server-functional-certification-uri_test-module | Certifies that, for each of the server's API Resources with a certification URI, excluding Phase 1 open data families, the URI follows the functional submissions structure for that family and the declared major version, in accordance with the certification start date. |
| directory_api_server-family-completeness_test-module | Certifies that the mandatory endpoints of each API family are registered, with the FamilyComplete flag not set to False, accepting in the accounts family only the absence of the optional /accounts/{accountId}/reserved-balances endpoint. |
| directory_api_server-scope-family-coverage_test-module | Checks that each scope supported in the well-known, apart from openid and the mandatory scopes, has the corresponding API Family Type published by the server, reporting all failures together. |
| directory_api_server-family-scope-coverage_test-module | Checks that each API Family Type published by the server has the corresponding scope supported in the well-known, reporting all failures together. |
| directory_api_server-mandatory-scopes_test-module | Checks that, if the organisation holds the DADOS Domain ROLE, all mandatory scopes are present in the well-known. |
| directory_api_server-scope-role_test-module | Checks that, for each scope supported in the well-known, the organisation holds the corresponding Domain ROLE in the Directory. |
| directory_api_server-presentation-metadata_test-module | Checks that the server was registered with valid metadata by calling the registered CustomerFriendlyLogoUri and validating the logo against the UX Guidelines. |
| directory_api_certification-status_test-module | Checks that the certification status of each API Resource is correctly registered in the Directory. |

[Download this category spreadsheet](uploads/9e7bba58ac4f2c85a06ba2fe372a651e/FVP-Directory-tests.xlsx)

---

[↑ Automatic FVP](FVP/EN/Automatic) · [◀ DCR tests](FVP/EN/Automatic/DCR) · [Product tests ▶](FVP/EN/Automatic/Product)


---

*Conteúdo baixado em 16/09/2026, 15:37:35*
