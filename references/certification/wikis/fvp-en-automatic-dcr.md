# DCR

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic/DCR](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic/DCR)
**Slug:** `FVP/EN/Automatic/DCR`

---

---
title: DCR tests
---

[← Automatic FVP](FVP/EN/Automatic)

# Automatic FVP - DCR tests

This category gathers the modules that validate Dynamic Client Registration, that is, the registration, update and removal of clients on the participant's authorization server. The list below describes each module and what it verifies.

## Modules and what to expect
| Test module | What it verifies |
| --- | --- |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow_test-module | DCR happy flow without browser interaction: obtains the software statement from the Directory and registers a new client on the authorisation server. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow-1_test-module | Performs the DCR with the 'grant_types' members in a different order from the standard happy flow and including the optional 'scope' parameter; the registration must be accepted. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow-2_test-module | Performs the DCR with the 'scope' string members in a different order from the other happy-flow variant; the registration must be accepted. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-delete_test-module | Registers a client and checks the behaviour of the GET and DELETE operations after the client is deleted. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-registration-accesstoken_test-module | Registers a client and checks the behaviour of the GET and DELETE operations when a bad access token is used. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-ss-signature_test-module | Performs the DCR with a software statement whose signature is invalid; the server must reject the registration attempt. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_no-software-statement_test-module | Performs the DCR without including the software statement (its values are placed in the request body); the server must reject the registration. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_no-mtls_test-module | Performs the DCR without presenting a TLS client certificate; the server must reject the registration and also the GET and DELETE calls made without a certificate. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_bad-mtls_test-module | Performs the DCR presenting an untrusted TLS client certificate; the server must reject the registration and also the GET and DELETE calls made with the bad certificate. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-config_test-module | Registers a client and changes the redirect uri via an RFC7592 PUT (both present in the software statement), which must succeed; PUTs with invalid authentication must be rejected and the redirect uri must stay unchanged. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client_config-bad-jwks-uri_test-module | Registers a client and attempts to change the jwks_uri to an invalid value via PUT; the server must return an 'invalid_client_metadata' error. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-config-invalid-jwks-value_test-module | Registers a client and attempts to add a jwks by value via PUT; the server must return an 'invalid_client_metadata' error. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_client-config-invalid-redirect-uri_test-module | Registers a client and attempts to add via PUT a redirect uri not present in the software statement; the server must return an 'invalid_client_metadata' error. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_no-redirect-uri_test-module | Performs the DCR without including the redirect uri in the request body; the server must reject the registration. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-redirect-uri_test-module | Performs the DCR requesting a redirect uri not present in the software statement; the server must reject the registration. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-jwks-uri_test-module | Performs the DCR requesting a jwks uri not hosted on the Open Finance Brasil Directory; the server must reject the registration. |
| dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_invalid-jwks-value_test-module | Performs the DCR passing a jwks by value; the server must reject the registration. |
| dcr_api_fvp-unhappy-tls-client-auth_test_module | Attempts to register a client with 'token_endpoint_auth_method':'tls_client_auth'; the server must reject with HTTP 400 (or, if it returns 201, have updated the method to 'private_key_jwt' per RFC 7591). |
| dcr_api_fvp-sandbox-credentials_test-module | Confirms Sandbox credentials are rejected during DCR: the server must not accept the registration (201) with certificates from another environment. |
| dcr_api_fvp-no-subject-type_test-module | Registers a client and performs an RFC7592 PUT without the optional subject_type and sector_identifier_uri fields, which must be accepted. |
| dcr_api_fvp-multiple-clients_test-module | Checks the server does not allow two clients with the same credentials: the first DCR returns 201 and the second, 400. |
| dcr_api_fvp-revoked-certificate_test-module | Runs the DCR flow presenting a revoked certificate. The server must refuse the registration and answer 400. |

[Download this category spreadsheet](uploads/e4af4028e10a68181c365f691f8819e9/FVP-DCR-tests.xlsx)

---

[↑ Automatic FVP](FVP/EN/Automatic) · [◀ Automatic FVP](FVP/EN/Automatic) · [Directory tests ▶](FVP/EN/Automatic/Directory)


---

*Conteúdo baixado em 16/09/2026, 15:37:35*
