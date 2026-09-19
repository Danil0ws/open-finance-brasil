# Automated Production Tests

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Automated-Production-Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Automated-Production-Tests)
**Slug:** `Automated-Production-Tests`

---

# Objective

The Production Conformance Suite - Also called _Ferramenta de Validação em Produção_ (FVP) is a tool that has been commissioned on behalf of the Open Finance initial structure and is set to execute different Conformance Tests against the Authorisation Servers that have been registered on the [OPB Participant Directory](https://web.directory.openbankingbrasil.org.br/organisations).

The tool will execute conformance tests on a periodic basis against selected servers and will report back with the outcome of those results to both the tests institution, using the SysAid Service Desk, and to the Initial Structure.

The tests are executed inside a protected environment that can only be accessed by selected personnel, however, all the tests that are present inside the protected environment can be accessed inside the regular [Open Finance Conformance Suite](https://web.conformance.directory.openbankingbrasil.org.br/).

# Testing Schedule

The FVP testing routine has Currently been set to execute tests against all conglomerates that have [Certified and published Phase 2 and 3 Consents APIs](https://openbankingbrasil.org.br/certificado-de-conformidade/) on the participant directory. From 09/03/23 all well-known correctly formatted started being tested

Those tests will be executed on a daily basis against all Authorization Servers registered on the participant Directory unless defined by the Regulator or the Initial Structure

Every day at around 1 am all the institutions will have the automated routine executed against their servers. Evidence and ticket updates will be provided by the end of the day

# Release Notes

All notable changes in how the platform interacts with the authorisation servers or changes to any tests on the testing scope will be documented in this file. Changes in the number of tested servers are not included in the list below, instead, this point is noted in the testing schedule section above

### \[Updated Release Notes\] - 2026-02-21

[20260221_Automatic_FVP_Tests_Available.xlsx](uploads/47e8a5ab28c1321c03aed9a51e67b940/20260221_Automatic_FVP_Tests_Available.xlsx)

### \[Updated Release Notes\] - 2025-08-05

[fvp-automatica-tests_available.xlsx](uploads/60730b19909736f18e5bc9e530607bbd/fvp-automatica-tests_available.xlsx)

### \[Include Test Scenario\] - 2024-06-24

- Included new test modules for payments v3 in the execution plan. For more information on the summary of the test modules, please see the [test plan list](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Automated-Production-Tests#test-plan-list):
  - fvp-payments_api_dict_test-module_v3
  - fvp-payments_api_manu-fail_test-module_v3
  - fvp-payments_api_pixscheduling-dates-unhappy_test-module_v3
  - fvp-payments_api_qres-code-enforcement_test-module_v3

### \[Updated Execution Periodicity\] - 2024-05-23

- The execution routine has been changed to run on a daily basis, and tickets are updated accordingly

### \[Include Test Scenario\] - 2024-05-23

- Added one happy test scenario for the consents v2, consents v3, payments v3, payments v4, and automatic payments v1. The test modules will do the dcr flow and make a POST request to the respective APIs
  - fvp_consents_api_bad-logged_test-module_v2
  - fvp_consents_api_bad-logged_test-module_v3
  - fvp_payments_consents_api_bad-logged_test-module_v3
  - fvp_payments_consents_api_bad-logged_test-module_v4
  - fvp_automatic_payments_consents_api_bad-logged_test-module_v1

### \[Certificate Update\] - 2024-04-16

- Updated signing certificate used by the tool for the private_key_jwt authentication method and phase 3 flow

### \[FAPI Unique and new Test Scenario\] - 2024-04-15

- All servers testes using method private_key_jwt only regardless if it supported by the server or not when verifying the well-known configuration
- Added dcr_api_fvp-unhappy-tls-client-auth_test_module which will try to perform a dcr using the method tls_client_auth and expects the server to reject the request\`

### \[FAPI Unique\] - 2024-03-25

- Execute the DCR tests using the private_key_jwt authentication methods for all servers regardless if it is supported by the server or not. And execution with tls_client_auth method for those who support this method

### \[Include Test Scenario\] - 2024-01-22

- Added payments_api_consents_negative_no_redirect_test-module_v3. The test executes 5 negative scenarios of payments consents v3, and 1 positive scenario

### \[Include Test Scenario\] - 2024-01-11

- dcr_api_fvp-revoked-certificate_test-module was added back to the execution and notification of institutions

### \[Add new Test Scenario\] - 2023-10-13

- Added payments_api_consents_negative_no_redirect_test-module_v2. The test executes 5 negative scenarios of payments consents, and 1 positive scenario

### \[Add new Test Scenario\] - 2023-09-21

- Added directory_api_certification-status_test-module. The test aims to verify the certification status of each API after the weekly automatic certification

### \[Remove Test Scenario \] - 2023-09-08

- Removed dcr_api_fvp-revoked-certificate_test-module from the execution, per request from Security WG.

### \[Update the criterion to choose the Servers being tested \] - 2023-08-31

- Execution routine now includes all Authorization Servers published that contains a correctly formatted well-known, including duplicated well-knowns. Previously, tests were only executed against one server per well-known, and duplicated ones we skipped.

### \[Update certificate used on Happy DCR Test\] - 2023-08-31

- Update test dcr_api_fvp-fapi1-advanced-final-brazil-dcr-no-authorization-flow_happy-flow_test-module to use a BRCAC issued from CA: AC SERPRO SSLv1, making sure that organisations are accepting this new type of certificate

### \[Add new Test Scenario and Update Serasa Certificate to use new Issuing CA \] - 2023-08-17

- Added dcr_api_fvp-revoked-certificate_test-module that perform the DCR flow, but presenting a revoked certificate. The server must reject the registration attempt.
- Update tests dcm-subject-dn-test-fvp and dcr-brcac2022-support-fvp to use a BRCAC issued from CA: AC SERASA SSL EV V4, making sure that organisations are accepting this new type of certificate

### \[Add new Test Scenario and implemented a new ticket to be opened for failures on this test\] - 2023-07-13

- Added directory_api_server-registration_test-module test module that ensures institutions have correctly registered theirs servers according to the Directory Operation Guide, beginning with 3 validations:
  - Certify that the Security Certification has been correctly added into the Authorisation Server
  - Certify that the Functional Certification has been correctly registered into the Functional APIs
  - Certify that the Server has been registered with valid metadata
- Added a new ticket to be opened in case institutions fail on the specific directory_api_server-registration_test-module test module. By that, there are 2 tickets that can be opened for each server being tested: one for the current 25 DCR tests; another for the directory registration test.

### \[Add new Test Scenario\] - 2023-07-06

- Added fvp-payments-consents-server-certificate-v2 test module that aims to confirm if the Certificate Used on the Server Endpoints is aligned with the Brazil Certificate Standards

### \[Update Soluti Certificate to use new Issuing CA\] - 2023-06-29

- Update FAPI-DCR Tests to use a BRCAC issued from CA: AC SOLUTI SSL EV G4, making sure that organisations are accepting this new type of certificate

### \[Update consents-bad-logged test\] - 2023-06-15

- Added x-fap-interaction-id to the header request on POST payments-consents

### \[New button on page result to download log as zip file\] - 2023-06-01

- A new button was added to the page sent to institutions when they fail in the tests. The button allows institutions to download their logs as they are able on regular CS.

### \[Send Error Details on Service Desk Ticket \] - 2023-03-10

- Service Desk notification now includes, together with the tests that failed, the hypothesis failure that has been identified on the test.

### \[Update the criterion to choose the Servers being tested \] - 2023-03-09

- Execution routine now includes all Authorization Servers published that contains a correctly formatted well-known. Previously, tests were only executed against Servers with consents or payments consents endpoints published.

### \[Update Soluti Certificate to use new Issuing CA \] - 2023-02-02

- Update tests dcm-subject-dn-test-fvp and dcr-brcac2022-support-fvp to use a BRCAC issued from CA: AC SOLUTI SSL EV G3, making sure that organisations are accepting this new type of certificate

### \[Update Serasa Certificate to use new Issuing CA \] - 2023-01-13

- Update tests dcm-subject-dn-test-fvp and dcr-brcac2022-support-fvp to use a BRCAC issued from CA: AC SERASA SSL EV V3, making sure that organisations are accepting this new type of certificate

### \[Add 3 New Test Scenarios\] - 2023-01-12

- Added dcr-subjectdn-fvp test module, which makes sure that server that support mtls client authentication method can correctly parse the expected tls_subject_dn on [different formats](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID3.md#certificate-distinguished-name-parsing)
- Added dcr-brcac2022-support-fvp test module, which makes sure that the server will accept [both the new and the old format of Brazilian Transport certificates](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-certificate-standards-1_ID1.md)
- Added dcm-subject-dn-test-fvp test module, which makes sure that the server can accept a PUT that changes the tls_subject_dn for one of a new certificate to allow the mtls certificate used on token authentication to be updated.

### \[Update Multiple Clients Test\] - 2022-12-22

#### Test Scope

- Update dcr-multiple-clients test module, which now will return a failure, instead of Warning, if server accept a DCR request when a client_id has already been created for the Software Statement.

### \[Updated DCR Delete Test Behaviour \] - 2022-11-30

#### Test Scope

- Updated fapi1-advanced-final-brazildcr-client-delete-no-authorization-flow test, which now will wait 1 minute time between the client deletion and the time we issue a token

### \[Support for Multiple Servers and mtls.ca correction \] - 2022-11-15

#### Test Scope

- Fixed issue, introduced on the 2022-11-08 release, where the leaf certificate was being sent on the intermediate CA chain, which made the existing SOLUTI BRCAC certificate be sent twice on the tls connection, leading some servers to obtain a handshake failure on the tls connection

#### Platform and Infrastructure

- Implemented capability that allows multiple servers from the same organization registered on the participant directory to be tested. This allows testing and reporting for institutions regardless of the number of servers that are maintained by the organization registered on the participant directory

### \[Update mtls.ca chain sent\] - 2022-11-08

#### Test Scope

- Updated for all tests the intermediate certificate chain so it sends only the intermediate certificate and the root certificate chain, removing all the intermediate certificates that are not related to the currently used certificate, in line with the [RFC5462 definitions](https://www.rfc-editor.org/rfc/rfc5246#section-7.4.2)

### \[Support for Additional CAs\] - 2022-10-25

#### Platform and Infrastructure

- Implemented capability that allows multiple certificates to be used on the same test plan, allowing tests that require more than one certificate to be issued, like the tests that support both the new and old BRCAC certificate standard to be implemented.

### \[New Optional Test and Results Page\] - 2022-08-16

#### Test Scope

- Added dcr-test-multiple-clients in line with [security documentation definitions that clients](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2.md) that servers cannot support more than one client for each tested server. The test returns a WARNING if the server supports more than one client to cater for the adapt period for all institutions

#### Platform and Infrastructure

- Implemented test [Results Page](https://results.conftpp.directory.openbankingbrasil.org.br/). Institutions now receive a unique link that can be used to access their test results after the weekly execution. Results can only be accessed if the user has an active organization within with the [Open Finance Participant Directory](https://web.directory.openbankingbrasil.org.br/organisations)

### \[Support for Phase 3 Tests and Test Removal\] - 2022-08-04

#### Test Scope

- Updated consents-bad-logged test, which now calls both the payments-consents (Phase 3) and the consents (Phase 2) endpoint, ensuring that the endpoint is reachable and that the server is correctly issuing a valid access token
- Removed dcr-subjectdn and dcr-test-attempt-client-takeover in line with the security work group request to no longer support [Brazilian-specific OIDs on the subject_dn](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID3.md#certificate-distinguished-name-parsing) on the human-readable format

#### Platform and Infrastructure

- Routine now obtains payments consents endpoint, in addition to the consents phase 2 endpoint from the tested servers from the participant directory

### \[Platform Release\] - 2022-07-01

#### Test Scope

- Platform Created with 23 Test Plans, including all of the 18 Original [FAPI-DCR Test](https://gitlab.com/obb1/certification/-/wikis/Automated-Production-Tests#test-plan-list), plus 5 Functional Specific tests: consents-bad-logged, dcr-test-sandbox-credentials, dcr_no_subject_type, dcr-subjectdn and dcr-test-attempt-client-takeover. dcr-subject and dcr-test-attempt-client-takeover tests are only executed against institutions that support mtls

#### Platform and Infrastructure

- Platform released with [SOLUTI BRCAC](https://gitlab.com/obb1/certification/-/wikis/Automated-Production-Tests#soluti-credential) and [BRSEAL](https://keystore.directory.openbankingbrasil.org.br/d7384bd0-842f-43c5-be02-9d2b2d5efc2c/application.jwks) used for test execution Communication with tested users done using SysAid Service Desk with results sent within a .zip file

# Testing Infrastructure

Currently, the macroblocks of the testing routine that are executed by the platform can be seen in the diagram below:

![image](uploads/042a68f7b1be5d90c8543ff11cd48c57/image.png)

## Service Desk Tickets

The Defined Service Desk interaction for the FVP is presented below

![image](uploads/7bae98192fc54476cc5dc55ad470c60e/image.png)

More details about how interactions will happen with the institutions are presented down below

### Ticket Opening

After all the tests have been executed, in case of any issues are found during the execution, the Routine will Open a Ticket named "Teste Automático DCR - organisationName". Inside the ticket, the following information should be present:

After all the tests have been executed, in case of any issues are found during the execution, the Routine will Open a Ticket or Update the existing ones. Two types of tickets can be created:

- "Teste Automático DCR - CustomerFriendlyName" - opened if the server failed in at least one ticket related to the dcr or functional tests
- "Teste Automático Cadastro Diretório - CustomerFriendlyName" - opened if the server failed in at least one ticket related to directory validation tests

If the server failed in both types of tests, both tickets will be opened to the institution. Inside the ticket, the following information should be present:

- The List of Tests that have returned a failure
- Hypothesis around the failures in order to help participants to adjust their implementations
- The Well-Known of the tested server
- The Authorisation Server ID found on the directory
- Evidence pointing to where the institution has failed on the test plan - This can come in two potential formats
  - An URI to the Results Page `https://results.sandbox.directory.openbankingbrasil.org.br/<TestID>/index.html`. This URI can only be accessed by users authenticated with Open Finance directory credentials
  - A zip file with the execution logs

### Ticket Maintenance

Upon receipt of the ticket, there is no need to update the ticket by the N2 support team at the Service Desk. The ticket will be closed automatically after the correction is identified in a new test run, which should happen on the defined test execution scheduled date.

An existing ticket will always be updated once a new execution is done on the defined scheduled execution date. If any issues are found on the ticket it will be automatically updated with the new execution logs. If the institution manages to pass on all the existing tests, a note will be left confirming that the latest execution was successful and the ticket will be automatically closed.

As mentioned on the [Test Scope section of this page](https://gitlab.com/obb1/certification/-/wikis/Production-Testing#dcr-automated-test-scope), all the DCR tests executed against the production environment are available on the regular [Conformance Suite](https://web.conformance.directory.openbankingbrasil.org.br/). Institutions can freely execute those tests on Sandbox while correcting any potential issues found on Production.

In case of doubts or issues on the executed tests, it is necessary for the Institution to open a new ticket under the Conformance Service Desk and insert the questions there so that they can be properly analyzed by the Conformance Suite team.

In rare instances, the Conformance Suite team might add notes on the ticket together with the execution logs in case a specific behaviour or action is expected of the institution.

## Infrastructure

In order for this to work two main infrastructure blocks have been commissioned by the initial structure

- OCITPP - A Conformance Suite Copy that is protected by VPN and holds productions keys inside a secure KMS to guarantee that production credentials cannot be accessed
- Results - A file repository to store each test plan obtained after the execution above has been completed. This repository is protected using the Directory OIDC and it can only be accessed by users linked to active organisations

The FVP will also interact with two of the core platforms of the ecosystem

- The Participant Directory, using its [Public Participants API to extract all of the active A.S.](https://data.directory.openbankingbrasil.org.br/participants)
- The [Open Finance Service Desk](https://servicedesk.openfinancebrasil.org.br/), to open tickets against institutions that had any failure

### Results Page

Automated tests are stored inside the test results page. This platform has the sole purpose of storing all of the Conformance Tests executing logs.

The Base URL of the platform is https://results.sandbox.directory.openbankingbrasil.org.br/TestID/index.html where the TestID is a random string of characters that will be provided to the institution once a Service Desk ticket has been opened.

To access the results page the user will need to authenticate with his Open Finance Directory credentials and will also need to be linked to an Active Organisation inside the Directory. Additionally, there is no way to index the existing test results so the institution must save the test URI if it ever wants to check its results again.

## Directory Interaction

In order for the FVP to start executing the automated tests, it will interrogate the [Directory Public API](https://data.directory.openbankingbrasil.org.br/participants), parse the JSON response and extracts information about every single organisation registered in the directory.

This information includes:

- Organisation ID
- Organisation Name
- List of all Authorisation Server registered under this organisation
- Well-Known URL
  - Customer Friendly Name
  - Authorisation Server ID
  - Consents URI

After extracting all the directory information, the FVP the Well-Known endpoints of every Authorisation Server are interrogated and processed at this part of the subroutine. After that, the fetched information is updated.

The information includes the following:

- Supported authorisation methods (either private key or MTLS)
- Whether Pushed Authorisation Request is supported
- If PAR is supported, whether it is mandatory.

With all this information at hand, a series of test plans will be created for each valid potential test scenario. Here the number of valid plans per AS depends on the number of credentials X supported_authorisation_variants. For example, if one AS supports both authorisation variants and the tests are being executed with two different types of Software Statements, then 4 valid test plans are generated.

# Test Clients

The FVP will use 4 different Clients/Software Statements registered on the participant directory, each one of them set with credentials issued from different Certificate Authorities.

Tests might be executed using one or more Clients, depending on the test objective and the testing scope. The information of the organisation and the clients that are used are as follows:

- Organisation: Open Banking Brasil - Chicago - d7384bd0-842f-43c5-be02-9d2b2d5efc2c
  - SS1: Ferramenta Validacao Producao - Serasa - bc97b8f0-cae0-4f2f-9978-d93f0e56a833 [Keystore](https://keystore.directory.openbankingbrasil.org.br/d7384bd0-842f-43c5-be02-9d2b2d5efc2c/bc97b8f0-cae0-4f2f-9978-d93f0e56a833/transport.jwks)
  - SS2: Ferramenta Validacao Producao - Soluti - 70ee2970-038b-44d6-9300-d3af3a890154 [Keystore](https://keystore.directory.openbankingbrasil.org.br/d7384bd0-842f-43c5-be02-9d2b2d5efc2c/70ee2970-038b-44d6-9300-d3af3a890154/transport.jwks)

## Serpro Credential - Serpro S.S. - V10 Chain - Expires 01/08/2024

TLS Certificate issued by Sepro used by the Serpro Software Statement - 21ef921f-7d9f-4fa5-afae-d24545d6c880

issuer: AC SERPRO SSLv1 V10 alias: obb-brcac-serpro

<details>
<summary>obb-brcac-serpro</summary>

```
-----BEGIN CERTIFICATE-----
MIIHWjCCBUKgAwIBAgINAI0zPZUl9sfbEb0REzANBgkqhkiG9w0BAQsFADCBjDEL
MAkGA1UEBhMCQlIxEzARBgNVBAoMCklDUC1CcmFzaWwxNTAzBgNVBAsMLEF1dG9y
aWRhZGUgQ2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMTEwLwYDVQQD
DChBdXRvcmlkYWRlIENlcnRpZmljYWRvcmEgZG8gU0VSUFJPIFNTTHYxMB4XDTIz
MDgwMjIyMjY1NFoXDTI0MDgwMTIyMjY1NFowggFDMTcwNQYDVQQDDC53ZWIuY29u
ZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMTQwMgYKCZIm
iZPyLGQBAQwkMjFlZjkyMWYtN2Q5Zi00ZmE1LWFmYWUtZDI0NTQ1ZDZjODgwMTMw
MQYDVQRhDCpPRkJCUi1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZj
MmMxFzAVBgNVBAcMDlJJTyBERSBKQU5FSVJPMQswCQYDVQQIDAJSSjEiMCAGA1UE
CgwZQ0hJQ0FHTyBBRFZJU09SWSBQQVJUTkVSUzELMAkGA1UEBhMCQlIxFzAVBgNV
BAUTDjQzMTQyNjY2MDAwMTk3MRMwEQYLKwYBBAGCNzwCAQMTAkJSMRgwFgYDVQQP
DA9CdXNpbmVzcyBFbnRpdHkwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIB
AQCrjG8dM4FlS1QksaZZvYMPF8doXDTASg9KfxBgrOLeHru8uC9EuFpfzW76euIw
jcqxtUbLWLTlEUSlUm+OCWgVBaeUIzWpeKIFCFN0bVTTea8QS52iGb2QTR74sups
b/wLyZ5pllUz0fOKEiL1C524FzrSbqArrdQca5Vdxm+hoFY4laQ6885F3DBHT84X
hjr0KM9qHJVt1ocTqe7lxviZlN6JYG3lzmJSkV1OTQ9gblA4JCJ2asbqvVV1B81R
x+8PpnN0QXobJ4kcBvxtuCf8Qf+kYYk6PxenYVmV675FDrYuDTBiBe9e4a6joA2d
lnJMx389Vz2el9wxq1oTF+hFAgMBAAGjggH/MIIB+zAfBgNVHSMEGDAWgBStFk9L
8Qy+woqihRjXDUYlkyLjzTCBiAYDVR0fBIGAMH4wPKA6oDiGNmh0dHA6Ly9yZXBv
c2l0b3Jpby5zZXJwcm8uZ292LmJyL2xjci9hY3NlcnByb3NzbHYxLmNybDA+oDyg
OoY4aHR0cDovL2NlcnRpZmljYWRvczIuc2VycHJvLmdvdi5ici9sY3IvYWNzZXJw
cm9zc2x2MS5jcmwwgYcGCCsGAQUFBwEBBHsweTBCBggrBgEFBQcwAoY2aHR0cDov
L3JlcG9zaXRvcmlvLnNlcnByby5nb3YuYnIvY2FkZWlhcy9zZXJwcm9zc2wucDdi
MDMGCCsGAQUFBzABhidodHRwOi8vb2NzcC5zZXJwcm8uZ292LmJyL2Fjc2VycHJv
c3NsdjEwOQYDVR0RBDIwMIIud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5r
aW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYIKwYB
BQUHAwIwYwYDVR0gBFwwWjAIBgZngQwBAgIwTgYGYEwBAgFpMEQwQgYIKwYBBQUH
AgEWNmh0dHA6Ly9yZXBvc2l0b3Jpby5zZXJwcm8uZ292LmJyL2RvY3MvZHBjc2Vy
cHJvc3NsLnBkZjANBgkqhkiG9w0BAQsFAAOCAgEAHk5wZEIZRXPGqp0+JA6AormP
qhwbUU93pzZ44teZTZY9jtmFw5YjWkMsT3gjZAtZWRXcrCJdKoLFh21uiStNeuFs
hdkelJ0vUn5w54MGpr8wMPlbI3CsLam/y5RA0wv+UDQVpDQierxO8Jt1e6MYD2vY
YuxmDqUbpGUuPN3rZslIChQEfxy6sWnjzHWVh32A2VUEbmTreS3472FFoWFDo9z3
jZ4c7t95z3K0ltOOjlQWQkTwXainTfcTwrk9EG3l+T68HQXaRiat8Mt6iKjHQLT0
e7CQPOhGMmU1VBQhenAvRyEp74bmN3uh/OXbINpJGELcpTZSBQLnBmHxihuyjNej
JrDow3ZXcREMvPBaa3h3ZMZ6dx0ho1tQPjb1c9EhRjMdBDGAFLPadXhAVrGJBE92
lUn/3fbvEyLFdWnFOa7pP7bYi8vG0v/Q+eP6FWq6J/qlpt7ChNntjzS1to+hUw3z
9MyEYxmisc0azfbmke5+7D+G71/tBXaONx3b5AO+c3gdKxLpR0dkkHyZGNlfhXfR
euXtDrGnHHkbeWVWbaJG7V9dH/U94+xlACVHM0fnPbrafRDU5dcm+9K6/8pSXksV
EepIqHWsAj19FqeB6rDpWFctIsQQbDz72DRXHRPj4Ky5FPusA7KQsseBW0Splu+A
lTBVLDIK2zFj5QndOqsu003d
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Soluti S.S. - G4 Chain - Expires 27/06/2024

TLS Certificate issued by Soluti used by the Soluti Software Statement - 70ee2970-038b-44d6-9300-d3af3a890154

issuer: AC SOLUTI SSL EV G4 alias: obb-brcac-soluti-v3

<details>
<summary>obb-brcac-soluti-v3</summary>

```
-----BEGIN CERTIFICATE-----
MIIHlzCCBX+gAwIBAgIIEd4jBihkDEwwDQYJKoZIhvcNAQENBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDExNBQyBT
T0xVVEkgU1NMIEVWIEc0MB4XDTIzMDYyODE5NDQwMFoXDTI0MDYyNzE5NDQwMFow
ggFvMTcwNQYDVQQDDC53ZWIuY29uZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdi
cmFzaWwub3JnLmJyMTQwMgYKCZImiZPyLGQBAQwkNzBlZTI5NzAtMDM4Yi00NGQ2
LTkzMDAtZDNhZjNhODkwMTU0MTMwMQYDVQRhDCpPRkJCUi1kNzM4NGJkMC04NDJm
LTQzYzUtYmUwMi05ZDJiMmQ1ZWZjMmMxFzAVBgNVBAcMDlJpbyBkZSBKYW5laXJv
MQswCQYDVQQIDAJSSjFJMEcGA1UECgxAQ0hJQ0FHTyBBRFZJU09SWSBQQVJUTkVS
UyBDT05TVUxUT1JJQSBFTSBHRVNUQU8gRU1QUkVTQVJJQUwgTFREQTELMAkGA1UE
BhMCQlIxFzAVBgNVBAUTDjQzMTQyNjY2MDAwMTk3MRMwEQYLKwYBBAGCNzwCAQMT
AkJSMR0wGwYDVQQPDBRQcml2YXRlIE9yZ2FuaXphdGlvbjCCASIwDQYJKoZIhvcN
AQEBBQADggEPADCCAQoCggEBAMj9+3LcvxAv+r53CAJtkCvEhV70j6zgev1xyUql
CgVilxj8+AkAj1wR6+ZuSU8o/j6EME9v+1wJHDvL1pfop6++/ohNc1//bI6p4aMA
9orRNLfkYF3mxc2dlX0RFGvFY2wn/0ah34QlDMTq+d7ioI6ZMyBrBW6xnCsJ0DXw
glgwl18z35iIMDJ4aEJOam4kK9SIe8irW4iE2wyeTOYrnKT9DdACpkTd4+1chAUZ
2rtgjePwyINJI7DSqcpQeGDOcYN6ll/66uHeA8gFMtQyM9g0v0qcy4PdQUx5krJD
r8YPgn6TFxqyiTF9A4zvXQ5RgJ1Bi6VrWnwvocM19pPerWkCAwEAAaOCAiswggIn
MAkGA1UdEwQCMAAwHwYDVR0jBBgwFoAU/ga5LJV+L+bQuKjxL7fyLoXV18AwgYAG
CCsGAQUFBwEBBHQwcjBGBggrBgEFBQcwAoY6aHR0cDovL2NjZC5hY3NvbHV0aS5j
b20uYnIvbGNyL2FjLXNvbHV0aS1zc2wtZXYtdjEwLWc0LmNydDAoBggrBgEFBQcw
AYYcaHR0cDovL29jc3AzLmFjc29sdXRpLmNvbS5icjA5BgNVHREEMjAwgi53ZWIu
Y29uZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMGQGA1Ud
IARdMFswBwYFZ4EMAQEwUAYGYEwBAgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6Ly9j
Y2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYucGRm
MBMGA1UdJQQMMAoGCCsGAQUFBwMCMIGQBgNVHR8EgYgwgYUwQKA+oDyGOmh0dHA6
Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC1n
NC5jcmwwQaA/oD2GO2h0dHA6Ly9jY2QyLmFjc29sdXRpLmNvbS5ici9sY3IvYWMt
c29sdXRpLXNzbC1ldi12MTAtZzQuY3JsMB0GA1UdDgQWBBSGMh5fTIfm9x5ca1bP
1WpKWcfD7zAOBgNVHQ8BAf8EBAMCBaAwDQYJKoZIhvcNAQENBQADggIBAByPVs29
esGtuNo5c3zBZS5wG1WIggewirOmj04fiw6+NdGWxlOHQTXE5QdDotLZZfF20aXf
xNbu6CUhtiNtxOycwegzDR9aAEmjHDLb4k6rMauchnv0BCSsNKMhcA6BHpPlOcE4
Nf4Sor71UWhIjj4dbk7Ujk45h3Q+G42SwYAfcBUP9qXhYSXPz+oV9WhfLfO1Pxiy
1O0hcIOUT6VF+9ETgEw8uVw3nt+394QOv0F8lW3QtWN87tW5eOSgBpoiFis74w97
npleOLVFyFyM3Cxl+cIXTfTcNx+jVvh6RNXtG8QsX0tE+lYq3glUqMwaOQ7cemxh
+++I1HilRElyGN8NQSFVgcwh9YmekgbwbdZp69orGe5BxPb3ijEPNydm+nuUCm1d
Hjto0l4urXU+g13MYRewk9eBHsZXdp6o44/0xRMQSk1FmxGMe7IOIo59rB8OdbaP
qFVSEifapYc+MF60UsFV4rxKZSnMhHy1k3D4Z1gW7wSGSshT0Ys0HIFr8Mni4/Qt
K8HVNCx1C7CnWG8T8IEhQkV9iAQO0SkNlFlPWQaoaBYDL2Ll+UwDxtiwfA7xmVuJ
EUffsoWfHCeHxHjlAqCVnhV0tLryRFiGo0vRvD0mcfUzwKoYrdntvocY+eDfggxe
waB5SA5rdviooPpoN1P0eb5mz5O8UMwaraWo
-----END CERTIFICATE-----
```

</details>

## Serasa Credential - Serasa S.S. - V4 Chain - Expires 30/07/2024

TLS Certificate issued by Serasa used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SERASA SSL EV V4 alias: obb-brcac-serasa-v2

<details>
<summary>obb-brcac-serasa-v2</summary>

```
-----BEGIN CERTIFICATE-----
MIIHxzCCBa+gAwIBAgIIB4Faz1mRPo0wDQYJKoZIhvcNAQELBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoMCklDUC1CcmFzaWwxNTAzBgNVBAsMLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDDBNBQyBT
RVJBU0EgU1NMIEVWIFY0MB4XDTIzMDczMTExNDgwMFoXDTI0MDczMDExNDc1OVow
ggFDMR0wGwYDVQQPDBRQcml2YXRlIE9yZ2FuaXphdGlvbjETMBEGCysGAQQBgjc8
AgEDEwJCUjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxCzAJBgNVBAYTAkJSMSIw
IAYDVQQKDBlDaGljYWdvIEFkdmlzb3J5IFBhcnRuZXJzMQswCQYDVQQIDAJTUDES
MBAGA1UEBwwJU0FPIFBBVUxPMTMwMQYDVQRhDCpPRkJCUi1kNzM4NGJkMC04NDJm
LTQzYzUtYmUwMi05ZDJiMmQ1ZWZjMmMxNDAyBgoJkiaJk/IsZAEBDCRiYzk3Yjhm
MC1jYWUwLTRmMmYtOTk3OC1kOTNmMGU1NmE4MzMxNzA1BgNVBAMMLndlYi5jb25m
dHBwLmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIwggEiMA0GCSqG
SIb3DQEBAQUAA4IBDwAwggEKAoIBAQDM7Q2MgkLsqSusK6CoFpe7idPfW4QN5mMR
jK1qiCXJFTlHyot6gDlq48dHq5VDg78zy33Bio/r93KGwQEOKGsr8HOuAou6IOQA
9OPyUNMg9f64scq8lUkNqNoqAKr/I2U6ELE0LtOAwe8SW4uMhkcYBOE+eP5D76M2
n5idrjsKdN/WloUKU9H2ZjraJLOhPQ0MHD8epL7SrU0/wKEShxO5e9i0MByP00ht
B74bn3yWc7pFe9TQ8oeyhMmsIky50ixIHKm5Vv/RWCjB/6CmBLyEENoNhNDMEy4k
GNGsDcuPGWrRnhNbylAX7luWpSvoOCd7z/ZLZ354zDiMHbn57VAdAgMBAAGjggKH
MIICgzAJBgNVHRMEAjAAMB8GA1UdIwQYMBaAFLFWplh4DM49EiNVGKlDGLbQWMUQ
MIGjBggrBgEFBQcBAQSBljCBkzBNBggrBgEFBQcwAoZBaHR0cDovL3d3dy5jZXJ0
aWZpY2Fkb2RpZ2l0YWwuY29tLmJyL2NhZGVpYXMvc2VyYXNhc3NsZXZ2MTAtNC5w
N2IwQgYIKwYBBQUHMAGGNmh0dHA6Ly9vY3NwLmNlcnRpZmljYWRvZGlnaXRhbC5j
b20uYnIvc2VyYXNhc3NsZXZ2MTAtNDA5BgNVHREEMjAwgi53ZWIuY29uZnRwcC5k
aXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMIGFBgNVHSAEfjB8MAkG
B2BMAQIBgQAwbwYFZ4EMAQEwZjBkBggrBgEFBQcCARZYaHR0cDovL3B1YmxpY2Fj
YW8uY2VydGlmaWNhZG9kaWdpdGFsLmNvbS5ici9yZXBvc2l0b3Jpby9kcGMvZGVj
bGFyYWNhby1zZXJhc2Etc3NsLWV2LnBkZjATBgNVHSUEDDAKBggrBgEFBQcDAjCB
pwYDVR0fBIGfMIGcME+gTaBLhklodHRwOi8vd3d3LmNlcnRpZmljYWRvZGlnaXRh
bC5jb20uYnIvcmVwb3NpdG9yaW8vbGNyL3NlcmFzYXNzbGV2djEwLTQuY3JsMEmg
R6BFhkNodHRwOi8vbGNyLmNlcnRpZmljYWRvcy5jb20uYnIvcmVwb3NpdG9yaW8v
bGNyL3NlcmFzYXNzbGV2djEwLTQuY3JsMB0GA1UdDgQWBBQ4XEp8dD3mZfBTKm2J
n4UgdrMItzAOBgNVHQ8BAf8EBAMCBaAwDQYJKoZIhvcNAQELBQADggIBAJmNLrQL
+OeV3DHURcHa2nHzkF+V6WugJRDnlovEed1kuK+knd/us0kmpMZfqw5GJT1ZVYFX
wiW2WWfEnswEM+U1pOQCckqhWRfn+jaShj7irR+Boe9aCOw/Z2wLDl5Fk2pqb2Sj
hp2JGfBjrDqy5Sw9piVZxHf0oObNsh/S3I402xFyBg7r0D6rOGtMg2JNTc+5w1dZ
mZoqOYxY+pLU6c5JgvsvaipJmBav256QywYM1nOZheva6b2OnJ5ddrDqyTe2MX6+
DD4qG9kPouqegrLAxQUcJZsdmmQ59RuiwiHiwR3javX5R71fSDAd4VTdX6KHRtgr
/O94a9JSW+7/Sh9jjW+ORN09wSRVM04AB5t86D7YdMlbi/kFtXOjq0IGpPl1UyD/
LUrBtQji4O3uiCwzhVSRX5Hjte5e80GLossLA3HKc0vqpNoDzKKkOj7upzOHOT5O
gfVnd7LID1xn/FmyF4O8jlxoI0IZDTRcdfYnUHTUCFIF0NaPImQ2hIHxHTFHwOtO
B5pNOHS7PfGpIWpt7OHEdsGh+Q3LG4zXwoCVdiTNSFZWkxN1LZECb1Fhmj+Nwout
4H75JUMdk2CHPVKKOxcNeWXeAyDLmPHl+Pah5zurX6sdaOq0SVnaN8mG1iZdd+KO
0G+Zk0R+t4wxbnGVJ+HR5f4diOF9fxegCldJ
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Serasa S.S. - G4 Chain - Expires 20/11/2024

TLS Certificate issued by Soluti used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SOLUTI SSL EV G4 alias: obb-brcac-soluti-dcm-tls-cert-update-v3

<details>
<summary>obb-brcac-soluti-dcm-tls-cert-update-v3</summary>

```
-----BEGIN CERTIFICATE-----
MIIHlzCCBX+gAwIBAgIIEd4jERdackgwDQYJKoZIhvcNAQENBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDExNBQyBT
T0xVVEkgU1NMIEVWIEc0MB4XDTIzMTEyMTE3MzgwMFoXDTI0MTEyMDE3MzgwMFow
ggFvMR0wGwYDVQQPDBRQcml2YXRlIE9yZ2FuaXphdGlvbjETMBEGCysGAQQBgjc8
AgEDEwJCUjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxCzAJBgNVBAYTAkJSMUkw
RwYDVQQKDEBDSElDQUdPIEFEVklTT1JZIFBBUlRORVJTIENPTlNVTFRPUklBIEVN
IEdFU1RBTyBFTVBSRVNBUklBTCBMVERBMQswCQYDVQQIDAJSSjEXMBUGA1UEBwwO
UmlvIGRlIEphbmVpcm8xMzAxBgNVBGEMKk9GQkJSLWQ3Mzg0YmQwLTg0MmYtNDNj
NS1iZTAyLTlkMmIyZDVlZmMyYzE0MDIGCgmSJomT8ixkAQEMJGJjOTdiOGYwLWNh
ZTAtNGYyZi05OTc4LWQ5M2YwZTU2YTgzMzE3MDUGA1UEAwwud2ViLmNvbmZ0cHAu
ZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9yZy5icjCCASIwDQYJKoZIhvcN
AQEBBQADggEPADCCAQoCggEBAK/TbHTlFk94cic91xBGoGAAkRiy1H0WSBIiI6B+
HWDUPN0XW8dnOVGEp/Hk/p8SB2kuIs5mEiECfeEd8/peZqlkFkmNRwYu8e10O7F1
bEx8uwGTkPX/m1s+bbw+b/oA+hDvm+77Bwun04VCtTylpyEyNfcwe7FYK8NWZnz0
A+kOC74KNwXDlpx5fCKYaknLxN40caY8scpSrbPPgk1+6TbjyyUBODDXsgj8qPwh
uzSGrQ7gmrfKVd12BqrDDYiPD2g4q832lvm6zoMu5txujujQ+Svxhc3w2wIAPDf6
eFgeRceNhSzzvODYNH52DcM6th6kNKsQNiRmexARvmhNNh0CAwEAAaOCAiswggIn
MAkGA1UdEwQCMAAwHwYDVR0jBBgwFoAU/ga5LJV+L+bQuKjxL7fyLoXV18AwgYAG
CCsGAQUFBwEBBHQwcjBGBggrBgEFBQcwAoY6aHR0cDovL2NjZC5hY3NvbHV0aS5j
b20uYnIvbGNyL2FjLXNvbHV0aS1zc2wtZXYtdjEwLWc0LmNydDAoBggrBgEFBQcw
AYYcaHR0cDovL29jc3AzLmFjc29sdXRpLmNvbS5icjA5BgNVHREEMjAwgi53ZWIu
Y29uZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMGQGA1Ud
IARdMFswBwYFZ4EMAQEwUAYGYEwBAgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6Ly9j
Y2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYucGRm
MBMGA1UdJQQMMAoGCCsGAQUFBwMCMIGQBgNVHR8EgYgwgYUwQKA+oDyGOmh0dHA6
Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC1n
NC5jcmwwQaA/oD2GO2h0dHA6Ly9jY2QyLmFjc29sdXRpLmNvbS5ici9sY3IvYWMt
c29sdXRpLXNzbC1ldi12MTAtZzQuY3JsMB0GA1UdDgQWBBQ3ZGduKdZRoh8RHnMu
lRcGqwTTpDAOBgNVHQ8BAf8EBAMCBaAwDQYJKoZIhvcNAQENBQADggIBAAq9CdAd
9wR+IS5g+eD2x/8wNZjPkFyimCQXuTnkJeDzdLjUv1TJvoPXRg6mByeWy5tX1JRe
vU9e29z+q2yCuuoFmqKLCseWabHvhjA7L68whJIuSqPBohbjb4dPcb+cWlIZ69mq
hq5G+wT1fC/PRzK+4eDvwstC+gMpP7547MCoVP6g8n5GPe6gbsdG4gufjOJ4c3YQ
VWncCeH2psmOlYaXDFgR4zppNZ+Kp6tLott3iz8Q73Bu2t8lQRAekUOUrbsw70z4
3KVDfQt5GircSEiph9rzD3u/JGJjnB+m7URVC8Tg9FIIWhoWsJxqRXwr9B9JECc1
f6EAdLdr82IYhzVmAkfWb1l+YBWSPfYaPoVbjdJw7mZQlk7LUrN+przNyl961VkC
INfKap+EYzjfdQ1j9kbARzFJmJ50ruOqbk6lQ21kv15oF7HC09DSuNqfs/mGOpzQ
fp1OtIz4vxBO9jkYjRkKzEYW9rpNwrZ9Lsttb7n84PkXO8CAq+7ep5D75CjHDQWx
U3EYoQVL5pi84LUw4x11cPrrnSw3Qx0eDyE554A5pBUzFVUIkE8tGM5CQKQ77tDD
FfWy75gY8C4ee5MJ7Uhh3JA5RAnMJ4Y3OH9gn6jrlZsiLGnPJh2uZaAV9S5UoixO
vd0g7wv04oksqGSykYL5RAp1gu9yJNwkF2Se
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Soluti S.S. - G4 Chain - Expires 30/10/2024

TLS Certificate issued by Soluti used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SOLUTI SSL EV G4 alias: obb-brcac-soluti-dcm-tls-cert-update-v2

<details>
<summary>obb-brcac-soluti-dcm-tls-cert-update-v2</summary>

```
-----BEGIN CERTIFICATE-----
MIIHlzCCBX+gAwIBAgIIEd4jECU6ZF4wDQYJKoZIhvcNAQENBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDExNBQyBT
T0xVVEkgU1NMIEVWIEc0MB4XDTIzMTAzMTE3MzIwMFoXDTI0MTAzMDE3MzIwMFow
ggFvMR0wGwYDVQQPDBRQcml2YXRlIE9yZ2FuaXphdGlvbjETMBEGCysGAQQBgjc8
AgEDEwJCUjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxCzAJBgNVBAYTAkJSMUkw
RwYDVQQKDEBDSElDQUdPIEFEVklTT1JZIFBBUlRORVJTIENPTlNVTFRPUklBIEVN
IEdFU1RBTyBFTVBSRVNBUklBTCBMVERBMQswCQYDVQQIDAJSSjEXMBUGA1UEBwwO
UmlvIGRlIEphbmVpcm8xMzAxBgNVBGEMKk9GQkJSLWQ3Mzg0YmQwLTg0MmYtNDNj
NS1iZTAyLTlkMmIyZDVlZmMyYzE0MDIGCgmSJomT8ixkAQEMJDcwZWUyOTcwLTAz
OGItNDRkNi05MzAwLWQzYWYzYTg5MDE1NDE3MDUGA1UEAwwud2ViLmNvbmZ0cHAu
ZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9yZy5icjCCASIwDQYJKoZIhvcN
AQEBBQADggEPADCCAQoCggEBALYRnC+2Efr2L4pN12v7srROAYbKoKH/KMxwCqqZ
JqXUntaF/BPid2Rg+e+FMqPreeO94DX+UsfsULau7YD2T5GJKvacrX/xDNbBpIth
SbWgub47HHk5zJOTsYGFvCnBwt3yS/RYSvA8sUFwQgoiOJdjjog9rwecqGmJjyXB
2sS7IhnYK0LrOMcz3WnJj5064sWgzMb8LnV1iR5i/1ITEDzS43ph3GTMQiiJv3k7
MOAJq8rEKj9zKWe8tdNEJ+EO0Qbbx0wrC7n6/ab+FZ29g2OSTxhAkJZe2xV04guN
5MA7T+wngn7D81fm2pG+WkeLT3FB8na5I2wemlazhrsrraUCAwEAAaOCAiswggIn
MAkGA1UdEwQCMAAwHwYDVR0jBBgwFoAU/ga5LJV+L+bQuKjxL7fyLoXV18AwgYAG
CCsGAQUFBwEBBHQwcjBGBggrBgEFBQcwAoY6aHR0cDovL2NjZC5hY3NvbHV0aS5j
b20uYnIvbGNyL2FjLXNvbHV0aS1zc2wtZXYtdjEwLWc0LmNydDAoBggrBgEFBQcw
AYYcaHR0cDovL29jc3AzLmFjc29sdXRpLmNvbS5icjA5BgNVHREEMjAwgi53ZWIu
Y29uZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMGQGA1Ud
IARdMFswBwYFZ4EMAQEwUAYGYEwBAgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6Ly9j
Y2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYucGRm
MBMGA1UdJQQMMAoGCCsGAQUFBwMCMIGQBgNVHR8EgYgwgYUwQKA+oDyGOmh0dHA6
Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC1n
NC5jcmwwQaA/oD2GO2h0dHA6Ly9jY2QyLmFjc29sdXRpLmNvbS5ici9sY3IvYWMt
c29sdXRpLXNzbC1ldi12MTAtZzQuY3JsMB0GA1UdDgQWBBTvzON+0GLLbpP3rjuA
ur25PrA7qDAOBgNVHQ8BAf8EBAMCBaAwDQYJKoZIhvcNAQENBQADggIBADQqGgO7
0UvhmmEmN681V0P3jAq0K1JeToL+W+tf1sg/UDXnfN8wvmSJQBx41uIhKTHmbddi
83nvZqXythlB7t89d09FEzeJ+rJPuqZv8D3dh+vvGhNwAh58wHQH88ATQRsXH9nG
Kp9jJMrQCh7nV65qb2VhiYER05cB1x2tGz5zBHBs/iroWyHCwWCewvkM0rIwvy9f
YZzZ3cy9uggwa+5syhJfKiBQZCLB6dnSaKugkSShfaVeMaygW4cV+QQqKj4ryg5u
JJQEZK4TRYps/8Z0NZkux1akBbysQ4v5B+UlnD6lXx8Ob7TS5S9CFlx2Ed+HcISM
xkBkjXjEdTKeMZueN80EDDUjuM+VvGQAvLXJ+4aLaaoIvRziDNRLH8flpBCa0lZN
/vsVwnbZQ7apn9Gswe7csmT8YEMKdoEPoY1GTi/bKB3MO9T6lLJdHq2zD2BvGhGs
rN5J+5wDJzPYaA/YqC/KgkIhpWY4UmChl/zPystCdVIxCbH8Ft+kqFXYxOR0KJqG
604Z3z0Eni/vnDf8AW0sad8VjhN9ZjxZCH5LO0VmLSzQMmhEJ9hZfQFpR7do5+uV
qBhJSWtGsm9JNjEjDxYiUwSXt4cQwMHfUo/jgLTp1SI5/66G34gvqtjLPQWEglZn
xTmGSAdcAH1/Dd5RCCVO180kzaW44rqQNnSd
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Serasa S.S. - G3 Chain - ~~Expired 23/11/2023~~

TLS Certificate issued by Serasa used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SOLUTI SSL EV G3 alias: obb-brcac-serasa

<details>
<summary>obb-brcac-soluti-dcm-tls-cert-update-v3</summary>

```
-----BEGIN CERTIFICATE-----
MIIHlzCCBX+gAwIBAgIIEd4jARdrb24wDQYJKoZIhvcNAQENBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDExNBQyBT
T0xVVEkgU1NMIEVWIEczMB4XDTIzMDEyMzEzMDEwMFoXDTIzMTEyMzEzMDEwMFow
ggFvMQswCQYDVQQGEwJCUjFJMEcGA1UEChNAQ0hJQ0FHTyBBRFZJU09SWSBQQVJU
TkVSUyBDT05TVUxUT1JJQSBFTSBHRVNUQU8gRU1QUkVTQVJJQUwgTFREQTELMAkG
A1UECBMCUkoxFzAVBgNVBAcTDlJpbyBkZSBKYW5laXJvMTMwMQYDVQRhEypPRkJC
Ui1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZjMmMxFzAVBgNVBAUT
DjQzMTQyNjY2MDAwMTk3MTcwNQYDVQQDEy53ZWIuY29uZnRwcC5kaXJlY3Rvcnku
b3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMTQwMgYKCZImiZPyLGQBARMkYmM5N2I4
ZjAtY2FlMC00ZjJmLTk5NzgtZDkzZjBlNTZhODMzMR0wGwYDVQQPExRQcml2YXRl
IE9yZ2FuaXphdGlvbjETMBEGCysGAQQBgjc8AgEDEwJCUjCCASIwDQYJKoZIhvcN
AQEBBQADggEPADCCAQoCggEBAMNuntCyxZktQiAThZNsb/XPHyW0bD5C8g4uVifo
Sa29pee9TuFxO5aDFbvlCRYqIw/9f8I5naaZeLGHV0MT67Bixxp/B/Epx7e7K6Fn
Q8aOQZinPasMWodZAzoitMtp+mo+J9AkFGjUqV4yawLaEHyEXbITuQ/Lp/ZGJs7e
OHdLPypYniJbvBrqR1HUt3pbjfonK9Cc5mV05a94gQTb3yyvHhaPlvRk8T87RNgr
IsRHabH2mD5XhgVPFQMDoMgxJmvW78Q2BolGYqM7zCXAAFqSHuVnx7y9etkDh9U4
6HYcy1FJOH2aV/EJjE29FnQrL7lr+ctnU/dhYwqAZhxDjEsCAwEAAaOCAiswggIn
MAkGA1UdEwQCMAAwHwYDVR0jBBgwFoAUhyboEB5t1CA/ZX6c//1B9//JYCMwgYAG
CCsGAQUFBwEBBHQwcjBGBggrBgEFBQcwAoY6aHR0cDovL2NjZC5hY3NvbHV0aS5j
b20uYnIvbGNyL2FjLXNvbHV0aS1zc2wtZXYtdjEwLWczLmNydDAoBggrBgEFBQcw
AYYcaHR0cDovL29jc3AyLmFjc29sdXRpLmNvbS5icjA5BgNVHREEMjAwgi53ZWIu
Y29uZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMGQGA1Ud
IARdMFswBwYFZ4EMAQEwUAYGYEwBAgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6Ly9j
Y2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYucGRm
MBMGA1UdJQQMMAoGCCsGAQUFBwMCMIGQBgNVHR8EgYgwgYUwQKA+oDyGOmh0dHA6
Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC1n
My5jcmwwQaA/oD2GO2h0dHA6Ly9jY2QyLmFjc29sdXRpLmNvbS5ici9sY3IvYWMt
c29sdXRpLXNzbC1ldi12MTAtZzMuY3JsMB0GA1UdDgQWBBSK5akEHEPzlVRmF+A+
N7PmSWoqQzAOBgNVHQ8BAf8EBAMCBaAwDQYJKoZIhvcNAQENBQADggIBADUZodyh
5tI++yxSSJ8F6HLlqn0p8i/kJCrxyLJTcMGCW3Cm+cOSdsLqJu0NbfL0c/KBkUH/
HHoRDphLPtPQPMUiiLNWjXpibZ6WuXy77IMjeC2nS2BB0t5zivh5OqsljWcUCsms
Jkuv2Unt0sKkrfNP3TAThbW+Zu5KU030geO2vbODlb1TAvgDM7FGm/4a9YERsDK1
6PyrKB49ObU+jwdhZgQ72X2lLpvAjQ+Rn7YbWmZ1bjagF4EqbHwghPFVkRAomoHb
T49aOf+dVa8Ub8qQKvBXDXMBHUBCF/SeE+50ksDEt3lLd8a8x+k/hOUZj6qASyLb
7TrFyOGLMhgoURcgBQYw5y6VUkX746I2ooSWr9TLADAlUh/pqt0yg2SlKPN8mKJw
pJBjr5t28NKpKWqZ0Oz/xG4V6HyrBP2buPMMY9iVHtiXMGewU85cOF6fRIWhWiaf
Sc8wfPkQqwl+KO0hlYMy0UzhbYqUhV6bTS2o2wp9qUGUQjYiD1goGJpfJlY1OLiL
H0TWNW+Q+59wqDouclmXIXMIpAn/803l3LNuLHKnza8HhtAsN0+jhmFhjrQswtq5
jr0hSXvP5Hnc4q48JwFzduNgf28+AqjrLemzNm70eLr2hDwqNP3yxSgg/KX9Beq6
b7MekeIfmi2KfRF84ZRTtQeD50xMoOltxmVx
-----END CERTIFICATE-----
```

</details>

## Serasa Credential - Serasa S.S. - (V3 Chain) - ~~Expired 19/12/2023~~

TLS Certificate issued by Serasa used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SERASA SSL EV V3 alias: obb-brcac-serasa-v3

<details>
<summary>obb-brcac-serasa-v3</summary>

```
-----BEGIN CERTIFICATE-----
MIIHxDCCBaygAwIBAgIIW2DbwXOM3rgwDQYJKoZIhvcNAQELBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoMCklDUC1CcmFzaWwxNTAzBgNVBAsMLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDDBNBQyBT
RVJBU0EgU1NMIEVWIFYzMB4XDTIyMTIxOTE1MDAwMFoXDTIzMTIxOTE0NTk1OVow
ggFDMR0wGwYDVQQPDBRQcml2YXRlIE9yZ2FuaXphdGlvbjETMBEGCysGAQQBgjc8
AgEDEwJCUjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxCzAJBgNVBAYTAkJSMSIw
IAYDVQQKDBlDaGljYWdvIEFkdmlzb3J5IFBhcnRuZXJzMQswCQYDVQQIDAJTUDES
MBAGA1UEBwwJU2FvIFBhdWxvMTMwMQYDVQRhDCpPRkJCUi1kNzM4NGJkMC04NDJm
LTQzYzUtYmUwMi05ZDJiMmQ1ZWZjMmMxNDAyBgoJkiaJk/IsZAEBDCRiYzk3Yjhm
MC1jYWUwLTRmMmYtOTk3OC1kOTNmMGU1NmE4MzMxNzA1BgNVBAMMLndlYi5jb25m
dHBwLmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIwggEiMA0GCSqG
SIb3DQEBAQUAA4IBDwAwggEKAoIBAQCufTATS7fS8eP6wUekm0op5/q4/FoJn60D
CirmnuJzQtz3UuZfUPmGPwoyBiDNgLIrmZ9nY6yqWfT1+MUx9Km+x/a1ItmtXehg
O20mqTrUBOj3OzIW5kh76eEmI+O1n1kYXQ5QtqIjRcV3orzdfWnupigzos3sAFgn
Qu6I049HL5Ua1tBmc7cnUo4BXAPrl2PRVfqdmeEFsgElFu6hBce4mJshvYDVvK5L
VI+iAx6PlYBrOrQeEms16kAi93uSfiidMLsyP6Kje4Yj5qvt4fpsMqR2iqlC/fAM
K3cjRS8mfoctdtxfG0VeR0HV4NVZvUcCVE+CDGWdZVbONDvtrq3JAgMBAAGjggKE
MIICgDAJBgNVHRMEAjAAMB8GA1UdIwQYMBaAFDBpPcnubSo1CySCrFk9Y1pVK+fF
MIGjBggrBgEFBQcBAQSBljCBkzBNBggrBgEFBQcwAoZBaHR0cDovL3d3dy5jZXJ0
aWZpY2Fkb2RpZ2l0YWwuY29tLmJyL2NhZGVpYXMvc2VyYXNhc3NsZXZ2MTAtMy5w
N2IwQgYIKwYBBQUHMAGGNmh0dHA6Ly9vY3NwLmNlcnRpZmljYWRvZGlnaXRhbC5j
b20uYnIvc2VyYXNhc3NsZXZ2MTAtMzA5BgNVHREEMjAwgi53ZWIuY29uZnRwcC5k
aXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMIGFBgNVHSAEfjB8MAkG
B2BMAQIBgQAwbwYFZ4EMAQEwZjBkBggrBgEFBQcCARZYaHR0cDovL3B1YmxpY2Fj
YW8uY2VydGlmaWNhZG9kaWdpdGFsLmNvbS5ici9yZXBvc2l0b3Jpby9kcGMvZGVj
bGFyYWNhby1zZXJhc2Etc3NsLWV2LnBkZjATBgNVHSUEDDAKBggrBgEFBQcDAjCB
pwYDVR0fBIGfMIGcME+gTaBLhklodHRwOi8vd3d3LmNlcnRpZmljYWRvZGlnaXRh
bC5jb20uYnIvcmVwb3NpdG9yaW8vbGNyL3NlcmFzYXNzbGV2djEwLTMuY3JsMEmg
R6BFhkNodHRwOi8vbGNyLmNlcnRpZmljYWRvcy5jb20uYnIvcmVwb3NpdG9yaW8v
bGNyL3NlcmFzYXNzbGV2djEwLTMuY3JsMB0GA1UdDgQWBBTtgD0BDVtTNJyQm1po
D1kRHzxc9jALBgNVHQ8EBAMCBaAwDQYJKoZIhvcNAQELBQADggIBAGcLWbskRaTD
CbxN6TI8dwz9ZdXATH+oHgdYQuAFyg4U1/aE3i+InbQAGIPLSWBHYMwRymNgXPQd
JyUbh4Q5HVGCCvOqAT6x/iBJ2gA7mNpBWTyUotUm2tuZJyd6yfMcXj2sz9uI3n21
T7+U25n5nFx+h3Zs1VQ8D6Aroz1BCD5b8KF5cWKtzI0OV1QnTICbwV5qBwq5IuBZ
kv9a3yHVB6qDS2lDvBzmdLfyla+/5iZtK0J9APyTBjNm2Rdf4zzzx2JMw0aFdvvX
IC2+ejQKauGRnIXdrJCuC7Vg78K0A/qCxCKk2DKF1Gt5lpY+ZJsdqf1NVBjNyWVb
5GAZIU8pbi0FsWParTpRL98VxHRnnBVLhQoQ36988NS9XD2RB8ywI0+p8Ce3E0Lw
MQHagnBLszslpnKeQgkeuqYfR2QAv3Y1QzyiLflWQCmZqkSF0jlZKuVzlPVDTm9X
BnG5Itaan28+XtToXzNMSgc78fu+6bVJT4eeWuPgWQDFyg1e6/MUU+jlWnvYclvX
k1dPwPNyC/Iy7HUPFk2G3HQGl2HN+Ys6egNEbk4MIwWb2QP9O7JkZHXtkmBfqnaV
XQ3bZpG2gnQ5iD8CrqdshWioTtYtQqFQwPZzgj52ib6YEjJEMTVTe11KJGWFXdbf
DF/HFEAZ0Q/IAVD14+0vtnKa7vkJ1Jgq
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Soluti S.S. - V1 Chain - ~~Expired 26/05/2023~~

TLS Certificate issued by Soluti used by the Soluti Software Statement - 70ee2970-038b-44d6-9300-d3af3a890154

issuer: AC SOLUTI SSL EV alias: obb-brcac-soluti-v3

<details>
<summary>obb-brcac-soluti-v3</summary>

```
-----BEGIN CERTIFICATE-----
MIIHhTCCBW2gAwIBAgIIEd4iBRlYyqgwDQYJKoZIhvcNAQENBQAwdDELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRkwFwYDVQQDExBBQyBT
T0xVVEkgU1NMIEVWMB4XDTIyMDUyNjE3NTcwMFoXDTIzMDUyNjE3NTcwMFowggFm
MQswCQYDVQQGEwJCUjFKMEgGA1UEChNBQ0hJQ0FHTyBBRFZJU09SWSBQQVJUTkVS
UyBDT05TVUxUT1JJQSBFTSBHRVNUQU8gRU1QUkVTQVJJQUwgTFREQS4xCzAJBgNV
BAgTAlJKMRcwFQYDVQQHEw5SaW8gZGUgSmFuZWlybzEtMCsGA1UECxMkZDczODRi
ZDAtODQyZi00M2M1LWJlMDItOWQyYjJkNWVmYzJjMRcwFQYDVQQFEw40MzE0MjY2
NjAwMDE5NzEzMDEGA1UEAxMqY29uZnRwcC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdi
cmFzaWwub3JnLmJyMTQwMgYKCZImiZPyLGQBARMkNzBlZTI5NzAtMDM4Yi00NGQ2
LTkzMDAtZDNhZjNhODkwMTU0MR0wGwYDVQQPExRQcml2YXRlIE9yZ2FuaXphdGlv
bjETMBEGCysGAQQBgjc8AgEDEwJCUjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCC
AQoCggEBALx8DIao1NMIxb2zXnDANCtp9FLL2Utep3cfLXPz+09coow7D9qcc1m/
ReJ1rwQA0uxyiX9ZGfEntYTQTW44+PCHkTLlzmdUDTalaD4qIl7wTC3QZBOF5zvq
rRMWJYA/RihzTfPOWXdLgepv39d40vLH+BX6B444IZnfZVi6cRw4a4hEySKVp2mN
obRbYeBJBUtyxJDfrz768O24UNQMU6m+dIy9btwAOsgQXO9tozJSCB2ldCpB3ukz
H6AiqfCkktUa+jLHXMu/4TJC2CLNR+C2Kb+6KTY8h0GORP4T52xRMA3ch3f23qyi
6yl0ezVrx0U75yjYFfVfHiHdOka37bcCAwEAAaOCAiUwggIhMAkGA1UdEwQCMAAw
HwYDVR0jBBgwFoAU/I6aUzaACX8Tz2qEGxPU6CPN6JowfAYIKwYBBQUHAQEEcDBu
MEMGCCsGAQUFBzAChjdodHRwOi8vY2NkLmFjc29sdXRpLmNvbS5ici9sY3IvYWMt
c29sdXRpLXNzbC1ldi12MTAucDdiMCcGCCsGAQUFBzABhhtodHRwOi8vb2NzcC5h
Y3NvbHV0aS5jb20uYnIwNQYDVR0RBC4wLIIqY29uZnRwcC5kaXJlY3Rvcnkub3Bl
bmJhbmtpbmdicmFzaWwub3JnLmJyMGQGA1UdIARdMFswBwYFZ4EMAQEwUAYGYEwB
AgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2Rv
Y3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYucGRmMB0GA1UdJQQWMBQGCCsGAQUFBwMC
BggrBgEFBQcDATCBiQYDVR0fBIGBMH8wPaA7oDmGN2h0dHA6Ly9jY2QuYWNzb2x1
dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC5jcmwwPqA8oDqGOGh0
dHA6Ly9jY2QyLmFjc29sdXRpLmNvbS5ici9sY3IvYWMtc29sdXRpLXNzbC1ldi12
MTAuY3JsMB0GA1UdDgQWBBT/wke0irzCGQEh0phWEOF7WXO7UDAOBgNVHQ8BAf8E
BAMCBaAwDQYJKoZIhvcNAQENBQADggIBAAiY2q+7LMo/nGsncHdBir5NyFYSQwuA
Y479K2Rcw97AepXWkv48yRM/aQbNWvCxbULgyPiBiTb4Y6Gi2fdfHhdT0BsyE7U1
AqpYSp2lrAW4N8vE/yNPIl2xS1Gw09+iNgOp8jjjww4IVwW5pJc9gz9UBabuZIDM
1eGBd7OALcMIbZYPljcHFCLqXU+n43PST4LDxTHcmOOMeh1c5dTVIJ903xND3nc4
GfMpUrtHOnQmQKDIaAdbggx9+nWXKLOBbMuI0buObq3sbwRx6QEr0OoSsx9z/KsB
HvmAG1Pear5NCI4URRnLXDQkcNPziQKkltmFynRwyvAOp2HrtA7bNiN9sxXNPRpk
N+bV9cbrDoosjS51awrq4dZNQcFdUKLNUO8VwWsPI8qIRrlijopQxig63IBocUED
XKXMxF6zznBoyrmnn7OPw9mnY74O8mFviOwytkw79QeXDtD0xDHqWbgPTZiwd3h/
UBAOHISdHE26IcnQJc9XtMsuML2+/wGBOf0yuo/4ECJP5pWMeOvHmjlpjQy+Z3xN
GTaFgWG0WkOb/637NuieBUA517xjrxsLxXmjX9tuHPDl7qMj7VC8OosR6uXX5fEz
Hj20ZDovemS4xO6fLuPhuP8tDbSDjcI+jCXVEWLYRqaG7MYP7fEZ83E9tSEMZNfn
A4X+lYntnHF/
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Soluti S.S. - V3 Chain - ~~Expired 23/06/2023~~

TLS Certificate issued by Soluti used by the Soluti Software Statement - 70ee2970-038b-44d6-9300-d3af3a890154

issuer: AC SOLUTI SSL EV V3 alias: obb-brcac-soluti

<details>
<summary>obb-brcac-soluti</summary>

```
-----BEGIN CERTIFICATE-----
MIIHjzCCBXegAwIBAgIIEd4jARdmv6QwDQYJKoZIhvcNAQENBQAwdzELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRwwGgYDVQQDExNBQyBT
T0xVVEkgU1NMIEVWIEczMB4XDTIzMDEyMzEyNTAwMFoXDTIzMDYyMzEyNTAwMFow
ggFrMQswCQYDVQQGEwJCUjFJMEcGA1UEChNAQ0hJQ0FHTyBBRFZJU09SWSBQQVJU
TkVSUyBDT05TVUxUT1JJQSBFTSBHRVNUQU8gRU1QUkVTQVJJQUwgTFREQTELMAkG
A1UECBMCUkoxFzAVBgNVBAcTDlJpbyBkZSBKYW5laXJvMTMwMQYDVQRhEypPRkJC
Ui1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZjMmMxFzAVBgNVBAUT
DjQzMTQyNjY2MDAwMTk3MTMwMQYDVQQDEypjb25mdHBwLmRpcmVjdG9yeS5vcGVu
YmFua2luZ2JyYXNpbC5vcmcuYnIxNDAyBgoJkiaJk/IsZAEBEyQ3MGVlMjk3MC0w
MzhiLTQ0ZDYtOTMwMC1kM2FmM2E4OTAxNTQxHTAbBgNVBA8TFFByaXZhdGUgT3Jn
YW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAkJSMIIBIjANBgkqhkiG9w0BAQEF
AAOCAQ8AMIIBCgKCAQEAvHwMhqjU0wjFvbNecMA0K2n0UsvZS16ndx8tc/P7T1yi
jDsP2pxzWb9F4nWvBADS7HKJf1kZ8Se1hNBNbjj48IeRMuXOZ1QNNqVoPioiXvBM
LdBkE4XnO+qtExYlgD9GKHNN885Zd0uB6m/f13jS8sf4FfoHjjghmd9lWLpxHDhr
iETJIpWnaY2htFth4EkFS3LEkN+vPvrw7bhQ1AxTqb50jL1u3AA6yBBc722jMlII
HaV0KkHe6TMfoCKp8KSS1Rr6Msdcy7/hMkLYIs1H4LYpv7opNjyHQY5E/hPnbFEw
DdyHd/berKLrKXR7NWvHRTvnKNgV9V8eId06RrfttwIDAQABo4ICJzCCAiMwCQYD
VR0TBAIwADAfBgNVHSMEGDAWgBSHJugQHm3UID9lfpz//UH3/8lgIzCBgAYIKwYB
BQUHAQEEdDByMEYGCCsGAQUFBzAChjpodHRwOi8vY2NkLmFjc29sdXRpLmNvbS5i
ci9sY3IvYWMtc29sdXRpLXNzbC1ldi12MTAtZzMuY3J0MCgGCCsGAQUFBzABhhxo
dHRwOi8vb2NzcDIuYWNzb2x1dGkuY29tLmJyMDUGA1UdEQQuMCyCKmNvbmZ0cHAu
ZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9yZy5icjBkBgNVHSAEXTBbMAcG
BWeBDAEBMFAGBmBMAQIBcDBGMEQGCCsGAQUFBwIBFjhodHRwOi8vY2NkLmFjc29s
dXRpLmNvbS5ici9kb2NzL2RwYy1hYy1zb2x1dGktc3NsLWV2LnBkZjATBgNVHSUE
DDAKBggrBgEFBQcDAjCBkAYDVR0fBIGIMIGFMECgPqA8hjpodHRwOi8vY2NkLmFj
c29sdXRpLmNvbS5ici9sY3IvYWMtc29sdXRpLXNzbC1ldi12MTAtZzMuY3JsMEGg
P6A9hjtodHRwOi8vY2NkMi5hY3NvbHV0aS5jb20uYnIvbGNyL2FjLXNvbHV0aS1z
c2wtZXYtdjEwLWczLmNybDAdBgNVHQ4EFgQU/8JHtIq8whkBIdKYVhDhe1lzu1Aw
DgYDVR0PAQH/BAQDAgWgMA0GCSqGSIb3DQEBDQUAA4ICAQBimQkSxogd4sV2/ZL2
1rMpuDUilYOzNa5W+PTUbbNZCwFi9xmjDxOhT/dTJ+/rryLNtCSSblMhPwv7de++
MuTrLJ9CEmRK67C6Yra/AQVqZAO1qrPo71DOWJhs53LTkKkqTzbBZznF+oht6pLD
70yrnmgG4ELRppCQ59GuVWZYvcgh67rzDKoUEtC9cm5Glz8cCgux5JU04TT4nr+w
yEXyhYlX7rXojNPbYCET5uAuneP296j7FudUQRZVxTUbcEC8hSsvMhvoeQZINm81
G3TvfI+Tp6zYbWBQPCtB/B97Ae7w70NCLSRwLua2GvQui5ZVxkVUVSy9l9996pJC
Etjt5mUTrGbow0ZesUKnKPPWKuZDV55BM+WiiJOQwqtnuG4StHIN9g8HgSujqCfa
LRXyLcPlpeUCTWd9Pmgqo31QjsBtvJ+IHHdIHv1WbnPxhiWY2D7WbMuTX6yCnrZg
zsWut9ctToEStC6LssOJs+ioO4PasrTtmpvRRQ9L2xF5t+1ija0IHi4/CHz1cYLW
ZZzKsP5hglcaevLOotTrnUwtPlB+ccfDBdE/0r55vf4wEcdc3IUwsH4O2aMnV+9r
2d1US0T3dTPg9Ck7BQMaFfLQPJcW2QkzmnlPwzpDEAERHJe+hvC697BFPdqLHKaz
A+SrKAWTyo0xW4t2lvZJuw2q+w==
-----END CERTIFICATE-----
```

</details>

## Soluti Credential - Serasa S.S. - V1 Chain - ~~Expires 22/11/2023 - Inactive~~

TLS Certificate issued by Soluti used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SOLUTI SSL EV alias: obb-brcac-soluti-dcm-tls-cert-update

<details>
<summary>obb-brcac-soluti-dcm-tls-cert-update-v1</summary>

```
-----BEGIN CERTIFICATE-----
MIIHiDCCBXCgAwIBAgIIEd4iESFUQ9YwDQYJKoZIhvcNAQENBQAwdDELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxNTAzBgNVBAsTLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRkwFwYDVQQDExBBQyBT
T0xVVEkgU1NMIEVWMB4XDTIyMTEyMjE4NDIwMFoXDTIzMTEyMjE4NDIwMFowggFv
MQswCQYDVQQGEwJCUjFJMEcGA1UEChNAQ0hJQ0FHTyBBRFZJU09SWSBQQVJUTkVS
UyBDT05TVUxUT1JJQSBFTSBHRVNUQU8gRU1QUkVTQVJJQUwgTFREQTELMAkGA1UE
CBMCUkoxFzAVBgNVBAcTDlJpbyBkZSBKYW5laXJvMTMwMQYDVQRhEypPRkJCUi1k
NzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZjMmMxFzAVBgNVBAUTDjQz
MTQyNjY2MDAwMTk3MTcwNQYDVQQDEy53ZWIuY29uZnRwcC5kaXJlY3Rvcnkub3Bl
bmJhbmtpbmdicmFzaWwub3JnLmJyMTQwMgYKCZImiZPyLGQBARMkYmM5N2I4ZjAt
Y2FlMC00ZjJmLTk5NzgtZDkzZjBlNTZhODMzMR0wGwYDVQQPExRQcml2YXRlIE9y
Z2FuaXphdGlvbjETMBEGCysGAQQBgjc8AgEDEwJCUjCCASIwDQYJKoZIhvcNAQEB
BQADggEPADCCAQoCggEBAMNuntCyxZktQiAThZNsb/XPHyW0bD5C8g4uVifoSa29
pee9TuFxO5aDFbvlCRYqIw/9f8I5naaZeLGHV0MT67Bixxp/B/Epx7e7K6FnQ8aO
QZinPasMWodZAzoitMtp+mo+J9AkFGjUqV4yawLaEHyEXbITuQ/Lp/ZGJs7eOHdL
PypYniJbvBrqR1HUt3pbjfonK9Cc5mV05a94gQTb3yyvHhaPlvRk8T87RNgrIsRH
abH2mD5XhgVPFQMDoMgxJmvW78Q2BolGYqM7zCXAAFqSHuVnx7y9etkDh9U46HYc
y1FJOH2aV/EJjE29FnQrL7lr+ctnU/dhYwqAZhxDjEsCAwEAAaOCAh8wggIbMAkG
A1UdEwQCMAAwHwYDVR0jBBgwFoAU/I6aUzaACX8Tz2qEGxPU6CPN6JowfAYIKwYB
BQUHAQEEcDBuMEMGCCsGAQUFBzAChjdodHRwOi8vY2NkLmFjc29sdXRpLmNvbS5i
ci9sY3IvYWMtc29sdXRpLXNzbC1ldi12MTAucDdiMCcGCCsGAQUFBzABhhtodHRw
Oi8vb2NzcC5hY3NvbHV0aS5jb20uYnIwOQYDVR0RBDIwMIIud2ViLmNvbmZ0cHAu
ZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9yZy5icjBkBgNVHSAEXTBbMAcG
BWeBDAEBMFAGBmBMAQIBcDBGMEQGCCsGAQUFBwIBFjhodHRwOi8vY2NkLmFjc29s
dXRpLmNvbS5ici9kb2NzL2RwYy1hYy1zb2x1dGktc3NsLWV2LnBkZjATBgNVHSUE
DDAKBggrBgEFBQcDAjCBiQYDVR0fBIGBMH8wPaA7oDmGN2h0dHA6Ly9jY2QuYWNz
b2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC5jcmwwPqA8oDqG
OGh0dHA6Ly9jY2QyLmFjc29sdXRpLmNvbS5ici9sY3IvYWMtc29sdXRpLXNzbC1l
di12MTAuY3JsMB0GA1UdDgQWBBSK5akEHEPzlVRmF+A+N7PmSWoqQzAOBgNVHQ8B
Af8EBAMCBaAwDQYJKoZIhvcNAQENBQADggIBACgnLmUL/UC+nZYTCvJVWf1Ue7e9
4EaoaoNP0tzRFnuCMNV38EViiCFSOXrKwyRbfWgLKu9hPo2tMGgKKKlJn3QIzlGj
ftQw11B/Ygdc1KvM5KJTyZGS+8TQUbWPqf8atpjg3IqiKmQYUSYi7sWZ+ITJwv/N
gx0VdaTlHSbMKD4uRGhJspeu1LkGtQGk4NYGBGzTzIPDGq6/IVhkJqI2tiCQH8jM
v8tSdvwhQbbfE8lGkmen7Tvf1rJ8lCUWXhNZCeks6obQGSEoto0pniuJhjZ13tiK
lCsblMZDVUjiCqfPvw/wZmbMAu3wFfhrAw8Zd+IJpocXdGJXzY0onrnKY3trbWdt
m5exWuIUCCzsHn45+/a8JdINVy+8MbLV4L5f3o+KtwPP0uSXUFF+sNKA68zqi8xp
p9I4ymQ3kIF1BlzUPbDxZ5rdAfH3BHfYU+cTw17ZcwtjZR+wuxumA4rsY82OLG+l
bZEVejJUD+M2CB04rsmjaff/0E0F2rP29jf/IfcmhYCRF+xgG+zuCLHXUOayCs1T
bueGhieDwW8kLiib/5gSvVG7JAHlnvCd/1Cj1P7Y32JMHV5u2qRihJTcWOJtPbKM
STmyAHiqlNbY4+Z9HbUHstn96rUHqZq6wYyI4ZhfAwRzbD28j0Rd7mt9YQtX9gjH
0lovgFsEBuJviVbd
-----END CERTIFICATE-----
```

</details>

## Serasa Credential - Serasa S.S. - ~~Expires 26/09/2023 - Inactive~~

TLS Certificate issued by Serasa used by the Serasa Software Statement - bc97b8f0-cae0-4f2f-9978-d93f0e56a833

issuer: AC SERASA SSL EV alias: obb-brcac-serasa-v1

<details>
<summary>obb-brcac-serasa-v1</summary>

```
-----BEGIN CERTIFICATE-----
MIIHuTCCBaGgAwIBAgIIfFO/ETcbh9UwDQYJKoZIhvcNAQELBQAwdDELMAkGA1UE
BhMCQlIxEzARBgNVBAoMCklDUC1CcmFzaWwxNTAzBgNVBAsMLEF1dG9yaWRhZGUg
Q2VydGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMRkwFwYDVQQDDBBBQyBT
RVJBU0EgU1NMIEVWMB4XDTIyMDkyNjE1MDAwMFoXDTIzMDkyNjE0NTk1OVowggFD
MR0wGwYDVQQPDBRQcml2YXRlIE9yZ2FuaXphdGlvbjETMBEGCysGAQQBgjc8AgED
EwJCUjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxCzAJBgNVBAYTAkJSMSIwIAYD
VQQKDBlDaGljYWdvIEFkdmlzb3J5IFBhcnRuZXJzMQswCQYDVQQIDAJTUDESMBAG
A1UEBwwJU2FvIFBhdWxvMTMwMQYDVQRhDCpPRkJCUi1kNzM4NGJkMC04NDJmLTQz
YzUtYmUwMi05ZDJiMmQ1ZWZjMmMxNDAyBgoJkiaJk/IsZAEBDCRiYzk3YjhmMC1j
YWUwLTRmMmYtOTk3OC1kOTNmMGU1NmE4MzMxNzA1BgNVBAMMLndlYi5jb25mdHBw
LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIwggEiMA0GCSqGSIb3
DQEBAQUAA4IBDwAwggEKAoIBAQCufTATS7fS8eP6wUekm0op5/q4/FoJn60DCirm
nuJzQtz3UuZfUPmGPwoyBiDNgLIrmZ9nY6yqWfT1+MUx9Km+x/a1ItmtXehgO20m
qTrUBOj3OzIW5kh76eEmI+O1n1kYXQ5QtqIjRcV3orzdfWnupigzos3sAFgnQu6I
049HL5Ua1tBmc7cnUo4BXAPrl2PRVfqdmeEFsgElFu6hBce4mJshvYDVvK5LVI+i
Ax6PlYBrOrQeEms16kAi93uSfiidMLsyP6Kje4Yj5qvt4fpsMqR2iqlC/fAMK3cj
RS8mfoctdtxfG0VeR0HV4NVZvUcCVE+CDGWdZVbONDvtrq3JAgMBAAGjggJ8MIIC
eDAJBgNVHRMEAjAAMB8GA1UdIwQYMBaAFJ5VQbRQLyVNpdDq9vKXC3xMb2OjMIGf
BggrBgEFBQcBAQSBkjCBjzBLBggrBgEFBQcwAoY/aHR0cDovL3d3dy5jZXJ0aWZp
Y2Fkb2RpZ2l0YWwuY29tLmJyL2NhZGVpYXMvc2VyYXNhc3NsZXZ2MTAucDdiMEAG
CCsGAQUFBzABhjRodHRwOi8vb2NzcC5jZXJ0aWZpY2Fkb2RpZ2l0YWwuY29tLmJy
L3NlcmFzYXNzbGV2djEwMDkGA1UdEQQyMDCCLndlYi5jb25mdHBwLmRpcmVjdG9y
eS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIwgYUGA1UdIAR+MHwwCQYHYEwBAgGB
ADBvBgVngQwBATBmMGQGCCsGAQUFBwIBFlhodHRwOi8vcHVibGljYWNhby5jZXJ0
aWZpY2Fkb2RpZ2l0YWwuY29tLmJyL3JlcG9zaXRvcmlvL2RwYy9kZWNsYXJhY2Fv
LXNlcmFzYS1zc2wtZXYucGRmMBMGA1UdJQQMMAoGCCsGAQUFBwMCMIGjBgNVHR8E
gZswgZgwTaBLoEmGR2h0dHA6Ly93d3cuY2VydGlmaWNhZG9kaWdpdGFsLmNvbS5i
ci9yZXBvc2l0b3Jpby9sY3Ivc2VyYXNhc3NsZXZ2MTAuY3JsMEegRaBDhkFodHRw
Oi8vbGNyLmNlcnRpZmljYWRvcy5jb20uYnIvcmVwb3NpdG9yaW8vbGNyL3NlcmFz
YXNzbGV2djEwLmNybDAdBgNVHQ4EFgQU7YA9AQ1bUzSckJtaaA9ZER88XPYwCwYD
VR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQBMGAs8xerQFSGCzgW4eeABiO9M
TaB2fwuvJHLNuN29zVWFKPP6CLXTkNa8oU+gmsqiee4/mRJ72GOwFgS1S6+VqrR2
JLu+YbemxDf8c7PLgNJqL4fDCO1wy23gvkTqrFQ69bNNkzd5PPu+UpdkGRIFM0OR
+wBzQkPvLgIlJyxmfa0u+i2o2mmJWPlggUW/Z13SV9bEoABJDMv18Nn6qpfMJprl
G1YLb1YrhlaxX4yPqzqqkcEqAk1LU11ooSceaVnBwAd9pJzl0POmZUszNiBH8qdW
ENcbV8QzzGo9bAbZ28WbmLpXScaN2Q6GNTTMdxYTt8j2+l4UJYTVl8IogU99UGfa
P3q+cXBXChtI15fs29vJ5RNynTzczTPX5FlJVcBf0djh63NdtAnaQ34KAlOHrvLt
Iw8pHKB1k+iZykgBrjOQgGnTQbgIhZo5l3CH8JbXPtuqlRJPxE1Juc2Jk93yI4wH
AQbfpbpITAglsD2sub7eoCPx8TDGQiSswMXyQtGSzIHqDACZtCE07zqAQT36CU+u
1/NY8vmTcMIiVOl1avVvaG94vkyXIbLscIfkS2dTCgPivzVaPMpxIT8ImsatsrPP
i0MHnnJuu3Pht+rg3X356qIBUJRo4HU2Ns8z6F/0XNjZcOL6R/JTpyxAsqP3MVRq
DqIBNjQhA+NzgrXJzA==
-----END CERTIFICATE-----
```

</details>

## Serasa EV V1 Certificate Chain

AC SERASA SSL EV - CA Chain

<details>
<summary>serasa-v1-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIHdDCCBVygAwIBAgIJAPFtS1twn/HxMA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjAxMTIzMTc0ODU3WhcNMzIwNzAxMTIwMDU5WjB0MQswCQYDVQQGEwJC
UjETMBEGA1UECgwKSUNQLUJyYXNpbDE1MDMGA1UECwwsQXV0b3JpZGFkZSBDZXJ0
aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxGTAXBgNVBAMMEEFDIFNFUkFT
QSBTU0wgRVYwggIiMA0GCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQC35YXt3C8K
9neT+BAlISz4lQpnfg/gT4wBkzd6GPgcgDUXzwsWD1yRsJpsN9BFiPu+BvEHIMm7
lpAxgU4vPvcrjHQ4XM+zJmOktorfcrm2jhcLOmB81HxtiRTN40amw+gjkfeS6RKu
+RApl6Hg2ZRy8R6SPbgr6Db/BFOyhQrDn44CzCtS+EQKjEDD7jU4zkBuCUV28toP
Ppwf8A4f7je0ZfzkqkA3P49rhlTxBAYA5OL22dOGtpu63MtIWSlslwM7Y0BixTG9
k7ZmiAcSWg4YN2YkyzISTuWw8BLLd7aE50i73QXsGkhGo6h9/R+akVp85AGnajy9
DaLKXd0bjG9CjhvIxL816tOZB4KATErj7C1TEv4wIxD+s484h4GQdetRhEBke+6q
/KKlgsv6x6+dXlTK7EJrXXWi2Pty2KfqCbfejmpfG08+QZiR6hkgoAFqQOlkT8Qb
Ag3I+G77IgmGHe8OaZxPfg2+djksjv0c9ERnTA8+/qMqP2gFGONsmDHMfX2uYHm6
elGO/Arjm59tWAiHZfngiVQOezrZ0Gk/sIloS7TB/xpuGgMcekQSyHThb6/j4TJ+
Ie6BoPb7F0caiw1EW1NjakQrlj6OnV5KrbemlJWCs47+SKMAaP4HiklGbCjg6unP
mNF4SQNhwfxSO5dQSFXgwBCxW+oZ1EhpowIDAQABo4IB4jCCAd4wggE3BgNVHSAE
ggEuMIIBKjBDBgVgTAEBADA6MDgGCCsGAQUFBwIBFixodHRwOi8vYWNyYWl6Lmlj
cGJyYXNpbC5nb3YuYnIvRFBDYWNyYWl6LnBkZjBwBgZgTAEBgSIwZjBkBggrBgEF
BQcCARZYaHR0cDovL3B1YmxpY2FjYW8uY2VydGlmaWNhZG9kaWdpdGFsLmNvbS5i
ci9yZXBvc2l0b3Jpby9kcGMvZGVjbGFyYWNhby1zZXJhc2Etc3NsLWV2LnBkZjBx
BgdgTAECAYEAMGYwZAYIKwYBBQUHAgEWWGh0dHA6Ly9wdWJsaWNhY2FvLmNlcnRp
ZmljYWRvZGlnaXRhbC5jb20uYnIvcmVwb3NpdG9yaW8vZHBjL2RlY2xhcmFjYW8t
c2VyYXNhLXNzbC1ldi5wZGYwQAYDVR0fBDkwNzA1oDOgMYYvaHR0cDovL2FjcmFp
ei5pY3BicmFzaWwuZ292LmJyL0xDUmFjcmFpenYxMC5jcmwwHwYDVR0jBBgwFoAU
dPN+//yfU3rxfOurPqSm2hi6RWMwHQYDVR0OBBYEFJ5VQbRQLyVNpdDq9vKXC3xM
b2OjMA8GA1UdEwEB/wQFMAMBAf8wDgYDVR0PAQH/BAQDAgGGMA0GCSqGSIb3DQEB
DQUAA4ICAQB6ipn8UJ5irPIHvYQC+Bg8tiaDyl01FkScURbnVmCwcektDAHjKb4d
+dvBkSQ9tUtF0nzaJRjzOYi5qrQQxrUG+k22TCGP/kfa/cCHAn2C7q7tYK4YafSy
vThPBhOE+CpIeoAfWPwnkD/cwN2vgaQbLB05/27FioheMMl0ZAlKy1aYxWHj98mI
V2ocqK3Ci5gMz/7yuBKgS87Ne7EIpACudw/8GccdxmPuC5iy3+t10+hX3qv/l2DE
4bQ2xjZGJrSdmwXTT/XmWM6SGklav3cUbjnZyKi+OgmAIIJ6bp5n1eDbolgUjP+3
Wu2clsQiIEsLMmlZP1bbrTFTWqAqcAhS+QNiQ0CWwYVxA1G6FW1rOL7BNkPVkCti
rgAuEnk+zVBXRP1oeWcDmuRgtFEj+mpeqd3oaKuHJl/iqeecoHpSy8y3GX87Nc0+
w4+HaBXEz9WaBBUiEXiZv4yOSBDuaJ+zAjAEXnrTypcFmRzuuhPShHLtne1TtJ7k
MGNEsDEuEcLZjMBjOWybE6DpQtIv7nSrxG7aN8eENGD/NohTtNDk/biTURhQVY5U
77BkU5+C7AcAbQ3tHDXEQk1GYZD1TxgygxXfDVrFI/fNfzt+SUv9h0OZgCFjS5aC
wb9FpWqz6AalPeBA62si8VXkFSKl0nPLgCSZ3PeTuGnYeq0dMQudfg==
-----END CERTIFICATE-----
```

</details>

## Serasa EV V3 Certificate Chain

AC SERASA SSL EV V3 - CA Chain

<details>
<summary>serasa-v3-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIH+zCCBeOgAwIBAgIJANG3bBJ4qhSdMA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjIxMjA3MTgxNjE1WhcNMzIwNzAxMTIwMDU5WjB3MQswCQYDVQQGEwJC
UjETMBEGA1UECgwKSUNQLUJyYXNpbDE1MDMGA1UECwwsQXV0b3JpZGFkZSBDZXJ0
aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxHDAaBgNVBAMME0FDIFNFUkFT
QSBTU0wgRVYgVjMwggIiMA0GCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQCoHEim
QIGhtZZm9r1JSVuBu0oa28Syo7Y6RJGVVr45l1xYXgAwEDOWkYgt6veTfdC8H1lP
TcMpUkdjY84LhFyFtDDVeKfXddS3Ojgac/anjBK/vZv9+oKbjx3EUU8LwXVL7WgO
c+Phy332OycPmkXrIMKkaZd+mWVCRgo5/W2AZc+P81PjT2CwYPwG8nto8UQANT7N
aQSk2q3TABusGd37jU3Cuaw5s3eAr+1HJ6bw+uRIlIkF6OEWu61qjitsrRZcv6vo
HJ2L1k90ZeBVwwjQ+RBrz3ZP1AQW/wapHySAe+O7OeKboT6BoDCiEBXPSHaJfmTn
fI+JDPcW7Y9WEPPO3FqVAxDbZZtg4Yp9iUXCBPs1109yQ63i7Q4aFVcKdFd8y/m9
+pbE16qnqtgLwPpdHq4Xw94cdtQMts7aL5rKeiwCf1Besj7XieNz3+IpsNJr/oId
zgenIFQCyEhEy55dOo3dvBeY0p/0sKelTlARv8GYTvU6w+kjmMPxgBcPRaXMVqWV
CSfctfsxpelco4CGUMd0umeyNX7kqBMsmjPUTOri7ISpRm7wmjOoKHpU0a1tBmOx
Z6C7UrN5qJmNgUwBEd36tKuv3/bU0zqT+7yWAVxMFw2PhlmxFAySwoRn7k8bmrdP
xRj9fL3Zy0rc+kCNTTucBjP/QDzH8afiQAdR/wIDAQABo4ICZjCCAmIwggFOBgNV
HSAEggFFMIIBQTBDBgVgTAEBADA6MDgGCCsGAQUFBwIBFixodHRwOi8vYWNyYWl6
LmljcGJyYXNpbC5nb3YuYnIvRFBDYWNyYWl6LnBkZjBwBgZgTAEBgSIwZjBkBggr
BgEFBQcCARZYaHR0cDovL3B1YmxpY2FjYW8uY2VydGlmaWNhZG9kaWdpdGFsLmNv
bS5ici9yZXBvc2l0b3Jpby9kcGMvZGVjbGFyYWNhby1zZXJhc2Etc3NsLWV2LnBk
ZjBxBgdgTAECAYEAMGYwZAYIKwYBBQUHAgEWWGh0dHA6Ly9wdWJsaWNhY2FvLmNl
cnRpZmljYWRvZGlnaXRhbC5jb20uYnIvcmVwb3NpdG9yaW8vZHBjL2RlY2xhcmFj
YW8tc2VyYXNhLXNzbC1ldi5wZGYwCQYFZ4EMAQEwADAKBgZngQwBAgIwADBABgNV
HR8EOTA3MDWgM6Axhi9odHRwOi8vYWNyYWl6LmljcGJyYXNpbC5nb3YuYnIvTENS
YWNyYWl6djEwLmNybDAfBgNVHSMEGDAWgBR0837//J9TevF866s+pKbaGLpFYzAd
BgNVHQ4EFgQUMGk9ye5tKjULJIKsWT1jWlUr58UwDwYDVR0TAQH/BAUwAwEB/zAO
BgNVHQ8BAf8EBAMCAYYwHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMEwG
CCsGAQUFBwEBBEAwPjA8BggrBgEFBQcwAoYwaHR0cDovL2FjcmFpei5pY3BicmFz
aWwuZ292LmJyL0lDUC1CcmFzaWx2MTAuY3J0MA0GCSqGSIb3DQEBDQUAA4ICAQA0
yw7ZCvZ9JlRl/Q5I+c0t0KI5SogFU21JXaj5d+UTC7O5hJeCuixkyF1DRcqhNvBQ
xUGb4hJvna0iD4G8KoxyVy5Lwuw93Dsn1Nocif2wpYyUT9OtBxuIBttfOCAYjk/P
5+Dkxh3hOxA7wDmSGjAk/x8JulMUzZLL+hP6et67uK3FHVCBmKkruWb48VJ7opEA
SqBSCMkixsVT6YQOPdh2hR2kV3WLtlyoNJvY9XVEsXMy9T3R9PlHQB8U674Y2nno
BGo3y1swzXSUXzFlFrS0zy+luIcCetEO3mIOp9CZLNUTsbKU0SyAHmN69YatvGH0
wSBkSdR7iWhls3kvOLdYtxrEd1thaem8P/DFFiSeiYy5dTzM6qfKJEC/7559HDba
0phSYp96J93xYEYnLRvf6UeT4IU8A+XK1M2d+dI+0p6niaNTyUCJ4reryIORFhZ1
XScCTO7D1ErzjHfVnXGM83uh0ue+YpvrUGg3sUO11Ro0y3fXEaFuMRFQY9W/jOIJ
TcyaJ+ik+/bnWMYy6r1lOfV7uQcaFW8EBnfbUEo4vnCm62aQLrWN6EBo4STcpRoC
FAGeqNnVM9qKSp178WQXnjzloglgPzJWCTWFMVC8xxGCYaHmvTHtbyu3RSnTVMtx
KVZPflTXGh1NPG5rzZm0mi2ZDD7sE4pcfKT0/xzSjQ==
-----END CERTIFICATE-----
```

</details>

## Serasa EV V4 Certificate Chain

AC SERASA SSL EV V4 - CA Chain

<details>
<summary>serasa-v4-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIH9zCCBd+gAwIBAgIJAJDYkYXwuQfvMA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjMwNDI1MTgzMTA2WhcNMzIwNzAxMTIwMDU5WjB3MQswCQYDVQQGEwJC
UjETMBEGA1UECgwKSUNQLUJyYXNpbDE1MDMGA1UECwwsQXV0b3JpZGFkZSBDZXJ0
aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxHDAaBgNVBAMME0FDIFNFUkFT
QSBTU0wgRVYgVjQwggIiMA0GCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQDDk+JR
7DlzctC1a9DXYBm9LdAJGBz9cFFqsC5YRgyq8rzCZlY7f1hIfy34OnUdmsi1w0Qy
Zu38NLEZtoShhN4bJWzR4lxIwJVke3ERYne4VEtGUh0U4woScFG2NrxpUkKm2+VV
OBHCBL0en1EoufB2StRapfw9OyXkZtU/Y14gbgAb0WeY76n1n0RKp8Jnp3frGc8H
b+cAIFD6tw/5s0V9r9bA3rXap0SJ7wOX+NbKnknZgsp7lfMIeDJkTnrizPN1JBf6
oN8YdYdCMzhnQGu0G1qdoo9TPf0fJk9xDWL1AU7JElcZ1hqLSwDKZy7LlMXpMHGW
sdWG0tDFh9TvMarSs/YhB8OvuhsEeL5VrR2eIfUId0rwQ8MlIf0qdWtGBxzmg6jR
hXoDL84q57eEcVDh9b9QS4p+Ya1+JmbQy5uoNgaGLu5/sL9IPMImROYCy2TUrieI
iTc2TOrqZq2FirdnYphEvJhijaJu9MpodPeLRq6NmQwoTYX+0Ilv3Tgnn2kuhOH8
Xpkqo/o75Pt3oUxjjBjaw4p9ot3tJQ6svPFEw8LrVRAHqfPuVXEzUfUFlyQiQ4FA
KMl6jq+38c4vUDWFdviEffMntfcwWCCZ8zeY29Gk6Int0SUvNt+kMSuN/3/YC03N
kxkAqIUyu7KndZSL6BPY4O/MvGXLsx7YzGA/uwIDAQABo4ICYjCCAl4wggFKBgNV
HSAEggFBMIIBPTBDBgVgTAEBADA6MDgGCCsGAQUFBwIBFixodHRwOi8vYWNyYWl6
LmljcGJyYXNpbC5nb3YuYnIvRFBDYWNyYWl6LnBkZjBwBgZgTAEBgSIwZjBkBggr
BgEFBQcCARZYaHR0cDovL3B1YmxpY2FjYW8uY2VydGlmaWNhZG9kaWdpdGFsLmNv
bS5ici9yZXBvc2l0b3Jpby9kcGMvZGVjbGFyYWNhby1zZXJhc2Etc3NsLWV2LnBk
ZjBxBgdgTAECAYEAMGYwZAYIKwYBBQUHAgEWWGh0dHA6Ly9wdWJsaWNhY2FvLmNl
cnRpZmljYWRvZGlnaXRhbC5jb20uYnIvcmVwb3NpdG9yaW8vZHBjL2RlY2xhcmFj
YW8tc2VyYXNhLXNzbC1ldi5wZGYwBwYFZ4EMAQEwCAYGZ4EMAQICMEAGA1UdHwQ5
MDcwNaAzoDGGL2h0dHA6Ly9hY3JhaXouaWNwYnJhc2lsLmdvdi5ici9MQ1JhY3Jh
aXp2MTAuY3JsMB8GA1UdIwQYMBaAFHTzfv/8n1N68Xzrqz6kptoYukVjMB0GA1Ud
DgQWBBSxVqZYeAzOPRIjVRipQxi20FjFEDAPBgNVHRMBAf8EBTADAQH/MA4GA1Ud
DwEB/wQEAwIBhjAdBgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwTAYIKwYB
BQUHAQEEQDA+MDwGCCsGAQUFBzAChjBodHRwOi8vYWNyYWl6LmljcGJyYXNpbC5n
b3YuYnIvSUNQLUJyYXNpbHYxMC5jcnQwDQYJKoZIhvcNAQENBQADggIBAGSvLPLK
JCiUxDhfrvr16dCy9YMSe85fkKi4TgtjNCgWOHCwi3KWV5UNn1Q6Qg7h9jJeIzvc
/grMKBP22jBujr6ONMb7T32zMFb4u1dCCqX0JQYcUtriIKMUWqunzJ8TywCwfgWN
cMGDzUk5t6977DSVNtCZ5Ln2uUFNTa7T9apH461L9+NH5AItxCdBH5+8imhmpm2a
BBPAJGvoOkWDSHOUlBtpxrDn1moZpHxJlWqG7rNhCRAfyu2Ln85521kVW00SXmC5
9SpbbKbmrr5fVR34kYPEBGwsRk/DbuRMLK4xioVdTH0vXkXmtCct291B0kSi9JKt
pn15dbaBjwSxMIdspBKJJhWXc9arlhL+APbzwPLFTapdW0s/wZ0fQqmBQvA4FQFT
GOCDTXuX8nO1CSiTbCxXzOPOnpE8lPRPxld7hStgEs15pgLZNLr60L/BFbrXIY8U
O5EM/WACf+T0BJ7bafDx7uevfQyevvHke9QgH6PDKm2SZ8nSrn5FS5a9RUBjyFSA
u7HJJSoNZqRMo0o+OPNV4DqC3Fu4+dn1YlhPSbNXcpp/0BwI9oCgIYCXMJzVOwPz
4ivQGSul+PwalvvnCqjbi1iw4iGZH6cPJSmr4jzhOH3Sww8qbp2uEW3wYx9e1fLu
r404Kw0AhKUAC+B6ia8JO9/RZLJVPfAkKEKz
-----END CERTIFICATE-----
```

</details>

## Soluti EV Certificate Chain

AC SOLUTI SSL EV

<details>
<summary>soluti-g1-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIHMDCCBRigAwIBAgIJAP2UCA7RW3r3MA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjAxMDMwMTMwNzUzWhcNMzIwNzAxMTIwMDU5WjB0MQswCQYDVQQGEwJC
UjETMBEGA1UEChMKSUNQLUJyYXNpbDE1MDMGA1UECxMsQXV0b3JpZGFkZSBDZXJ0
aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxGTAXBgNVBAMTEEFDIFNPTFVU
SSBTU0wgRVYwggIiMA0GCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQC1Ptwas5Dk
KAb5/qOofLJ1DHapM+Ka5SkKZq0FHqduqwO2AMZZLTzsEGJwoiy6K0YNXFtjcFBg
6eNlFaH2D+Pn0ZMiYRYGjUNMO8TtMz0qOsRcMPtbBUK8MEqGzZN7sqi3mbO0djDJ
6NSC27a2aUpt+1LtxXkOmlJ0LuBIaR2PXOkZGzWjvS4XbA6zByrVkXFub8NCQzd3
0aIflg+tGLziMalhn2CRZ76ygVG/6jl20+C9YeTWiYHlFqKzO1gs8v3fGDUiE80F
25SbeRh+K1WNOvFypt+3aAPe4hDJ2fHQtmBlzOljL1aikHNlyLBYPOlVJhg4dt9m
Cy+oS2hSMH2nHCxMLcbRYA3Y3SPqMqD92rEdENG6QYajqZjAwUOOJjwYDHVI37oZ
u9nn963glq9rfIWaFBDp6MoTC89W+cNygQKMp7on7s33dNRJncAf6EeC2klIw0RT
jpHkgD/Z5CUAcJpBB3RSVbgvlVoL2UE+/pIverluEaGat2KimLZ5mYymZhEwyeBH
N/btsfasngRt9FdIjG1fqU9MO/hGxOcONZ6tlfEP9mCAcSbRu7pAfdDtAcUC3nXO
AKJahLxrQPE3pBMgCA5yS7sm8zXnO95+0GYc04ii/yvSFOcW4+4lL0mvG5OggVCM
mUgFXvBvR7FxgpE3xuYsT5IbWhltzFO/6QIDAQABo4IBnjCCAZowgfQGA1UdIASB
7DCB6TBDBgVgTAEBADA6MDgGCCsGAQUFBwIBFixodHRwOi8vYWNyYWl6LmljcGJy
YXNpbC5nb3YuYnIvRFBDYWNyYWl6LnBkZjBQBgZgTAEBgQIwRjBEBggrBgEFBQcC
ARY4aHR0cDovL2NjZC5hY3NvbHV0aS5jb20uYnIvZG9jcy9kcGMtYWMtc29sdXRp
LXNzbC1ldi5wZGYwUAYGYEwBAgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6Ly9jY2Qu
YWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYucGRmMEAG
A1UdHwQ5MDcwNaAzoDGGL2h0dHA6Ly9hY3JhaXouaWNwYnJhc2lsLmdvdi5ici9M
Q1JhY3JhaXp2MTAuY3JsMB8GA1UdIwQYMBaAFHTzfv/8n1N68Xzrqz6kptoYukVj
MB0GA1UdDgQWBBT8jppTNoAJfxPPaoQbE9ToI83omjAPBgNVHRMBAf8EBTADAQH/
MA4GA1UdDwEB/wQEAwIBhjANBgkqhkiG9w0BAQ0FAAOCAgEAgyphkDlsHhWVv6yP
DdFpugHzvtDd/8junfXJXUoE9I8NrKG2cuy8UEVJ8uDSM+sLBSIEJdrZYKHwUlH6
K2AnRMuKdhBM9X/dYdjslm2KOcrfb+nsU/peRIbOvqpeNsKMzjbPYo4CCJ4q2hCx
HrI3FKzotPaS13Um3BzTz2smsgnyTMToj+vgF1D38NTUmoYWtqREas20PEX158JI
xgJtZShSvmU73TO1waHZbxqk6huZ52sHbodT6c7NA7lDllE89YOI2a5VwidJFdaX
lHQuylBZ5kbME1X0mIaKcVNYNhqPai8FywkyNz3/hXLkB/PrImih0QQgqa5x4Fsx
KkOgKp6Iv0nBL2AGlVZvWGX/snIgHGzImzkSKXyzFsyR9PFwhjy0PwRceic89cAE
ji107kztXd5xq+BdJGIPfTzsnPALeDiLdnUCqwzIcCd6SvJwnFeiona4AyA8lVGn
SNTuXtX/0ngZGxMkN2F+dcUNMFptFDnq3U4m9Z5CKeEIygula9YCFa+mj7vvlFPc
gp0caf9NeU6VLt1kqBIXoTxbLSqG0uYjNQIEw8SCYotu5D7tW4aiTS7rGLqryF/i
nwP7rAEk31Omq7FS4zfQzYXwwRgGkPj6jYM3CxWXPe3Zx5yfezjAdaiaji16jInM
d40Egr/61JXqOlX7Nry57kFquH8=
-----END CERTIFICATE-----
```

</details>

## Soluti EV G3 Certificate Chain

AC SOLUTI SSL EV G3

<details>
<summary>soluti-g3-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIHujCCBaKgAwIBAgIJAOJbuMb1P2lRMA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjIxMjA3MTkxMjU0WhcNMzIwNzAxMTIwMDU5WjB3MQswCQYDVQQGEwJC
UjETMBEGA1UEChMKSUNQLUJyYXNpbDE1MDMGA1UECxMsQXV0b3JpZGFkZSBDZXJ0
aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxHDAaBgNVBAMTE0FDIFNPTFVU
SSBTU0wgRVYgRzMwggIiMA0GCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQCew7yd
IZa5Drh8zAWPlZRJt+yHnvUHbunU4Ndkv4GWuaTLpBSn+d2LatVgluP3DGKl2dwa
vZGk902xvjOxnHHGD9RFi4HRkaq9pXVJsClD2G6CjIWXf7qq3JsE66jb/UT4KkRr
KECvJSoxynO85Y45adR3ZZTcYmlJD7oR6tdkucKueAX6sk0QGCxgCeUnXv4Roro/
fbbfGnlVsVjRZwJfGatPem8hmqLXSzzzbbY4u8XREdpUeHgkXtIFPqjaRrVl1seT
lv7CvCnJPglonh8GWs+tCrKOatJ/pUN2CW2aS2SlgST01QWNYD0F+esmGfctr/iw
L3x3YlaC4HyOraUU1FXSL03pvNH42OI1vxYykJ8XbWvFMHyxmJMXouGBY/TF0Gqe
tTaP58kRG2VUVKvDVxNnACqQ5dE3MIM7GvhwmRFYfAI36RGe6KUy3SRzSkBfmo1L
/UznrsAgUG8RAbI9krC2i+6SlMrFEihKnBhNunlC07C2WYv1P3QssIt4SGb8qoyh
TQXu3vsmnq5b7YJQuIC7RDO/TnEFIZHKczmrhVjuKVTAwZUzg4m8frErKbtNz1co
lkbAM/BDwi/oL8p3NmxNalVGKhlml0xZBnNbvzfeILFMcjozJYSL+mFVHQePv3f8
4q8JGsipMcVmQMyfhQq4aHxn1Hf9fv/tIqI16wIDAQABo4ICJTCCAiEwggENBgNV
HSAEggEEMIIBADBDBgVgTAEBADA6MDgGCCsGAQUFBwIBFixodHRwOi8vYWNyYWl6
LmljcGJyYXNpbC5nb3YuYnIvRFBDYWNyYWl6LnBkZjBQBgZgTAEBgQIwRjBEBggr
BgEFBQcCARY4aHR0cDovL2NjZC5hY3NvbHV0aS5jb20uYnIvZG9jcy9kcGMtYWMt
c29sdXRpLXNzbC1ldi5wZGYwUAYGYEwBAgFwMEYwRAYIKwYBBQUHAgEWOGh0dHA6
Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0aS1zc2wtZXYu
cGRmMAkGBWeBDAEBMAAwCgYGZ4EMAQICMAAwQAYDVR0fBDkwNzA1oDOgMYYvaHR0
cDovL2FjcmFpei5pY3BicmFzaWwuZ292LmJyL0xDUmFjcmFpenYxMC5jcmwwHwYD
VR0jBBgwFoAUdPN+//yfU3rxfOurPqSm2hi6RWMwHQYDVR0OBBYEFIcm6BAebdQg
P2V+nP/9Qff/yWAjMA8GA1UdEwEB/wQFMAMBAf8wDgYDVR0PAQH/BAQDAgGGMB0G
A1UdJQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjBMBggrBgEFBQcBAQRAMD4wPAYI
KwYBBQUHMAKGMGh0dHA6Ly9hY3JhaXouaWNwYnJhc2lsLmdvdi5ici9JQ1AtQnJh
c2lsdjEwLmNydDANBgkqhkiG9w0BAQ0FAAOCAgEAV2H81qCfc35o7K80cHjYPk9v
8P4gV7LjxXLNN65UQrUmoKzBeX8/IB0IPJnD5U/i93L2PdHHvWvodbFbBcnb5acP
YpJbZd5sum6GcA59suwgNebGf/2ska+mi0hdLF7Xz+t4gNR7zMOPNVevQzv9cITd
CD5JXwFTJVwO7kwWDd72gAPEM7in/Ir+tnfRJeqeMjNRmXPoDHACp0BCI92iBqT+
2TV6z1u2mo3pMa0Dld2imdhsu37ZJci10fsYipj1JLCslHivM92zu8aHi80vv3Sk
6PCICLvWYtc7bI8+RMiPL5K9dZjSR9Tm8hwthrKo4lrfJAoYebXDcawaL3zv35YO
nwR64pG3Bca8s17z6Melj2PD5xiHLcx7PiK+SFuIOMp0F3nsrtP/ve/Kc/8gSNVE
8TdlodjJe+eAoEXzUHJFw5UkOWlJQPPxtZ9eivTOw+y5OEsy/dwrbZyxdcaJUQZF
1O9Un1n7I3WtXTYe3OFXBRe6Xhq0NXxkho3uk5GQ73h0FdN6uGzR2j/9tUKg1Mjm
Ddm56mC2qbN7UoqzF1BiE1OuX31IbKwN+11ef4QvCRdMrIruOA07hqm/GZvnxQOs
1eBGdsILKxdXJgEHO5aBKjAxcc8w1HpUlDUqSuLxbDorKgAHPW/B+NmIaKXp5n/7
WH6yTZFQc/m4rYvHCdQ=
-----END CERTIFICATE-----
```

</details>

## Soluti EV G4 Certificate Chain

AC SOLUTI SSL EV G4

<details>
<summary>soluti-g4-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIHtDCCBZygAwIBAgIJANjGl6F55VD+MA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjMwMzIyMTgwOTExWhcNMzIwNzAxMTIwMDU5WjB3MQswCQYDVQQGEwJC
UjETMBEGA1UEChMKSUNQLUJyYXNpbDE1MDMGA1UECxMsQXV0b3JpZGFkZSBDZXJ0
aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxHDAaBgNVBAMTE0FDIFNPTFVU
SSBTU0wgRVYgRzQwggIiMA0GCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQDHv3Kv
oEPrNrzImIPn17GI5vdoVxghsm6EVLMUjnM4JdCpDED+0BqZF0kycyZaiWt7jqSR
vcGm66RKzSGcHJlUgahp9qcXAmSwMn00pwvgBKb+4htp48vQc1/5MWpaBzQW4Di/
tWvNkh9URtMyhtltf2u3s9r5vgF12ff7mCu3oj0bDBIaGs/a9EtMKoCfw/ziKUp7
11JYu1fbIWVOgbW9iHE24oiE33LGLm+uToCWpjGL3n9D+q+ryfIYFoes6gPCYYSt
udDUB9lfpe83IOVcVslL3DmYd2oEncGCogO3qzaMSH3OVLMO4Rg5edERpMw5U0tA
MeyO0k5/tmnFfUM476lZl+ce2Ol56p7R2yjKxHJizeCOSmwDE5FXz7ll+Zq9C7QW
UzoPQtyT739UGEeBRTAz4KsO77frCtdifGRvX3lMfI8qeMnfvf08BK9e2dRkCHwD
iv23Aw7QIixDS9PiSsMxObgjHwroEqAAN2Mwz1B1zAuzZVUH7k6MyQQ/II/GDUpT
jT4VKnhjdIfz5aEFHx7By2XjMkx1hyeONLS/2SoDnKitE9yY/PASqWDCPCpSoJ+x
fEdyZvoawEbJfL+CMhU5I7IXgf9f7gibghIc2CG4bf6dfVAdPcGkYkcjw21dtq/G
1V2dHpOX67BbihThAVr8Z7NTgVAv4nC6MPpAywIDAQABo4ICHzCCAhswggEHBgNV
HSAEgf8wgfwwQwYFYEwBAQAwOjA4BggrBgEFBQcCARYsaHR0cDovL2FjcmFpei5p
Y3BicmFzaWwuZ292LmJyL0RQQ2FjcmFpei5wZGYwUAYGYEwBAYECMEYwRAYIKwYB
BQUHAgEWOGh0dHA6Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNv
bHV0aS1zc2wtZXYucGRmMFAGBmBMAQIBcDBGMEQGCCsGAQUFBwIBFjhodHRwOi8v
Y2NkLmFjc29sdXRpLmNvbS5ici9kb2NzL2RwYy1hYy1zb2x1dGktc3NsLWV2LnBk
ZjAHBgVngQwBATAIBgZngQwBAgIwQAYDVR0fBDkwNzA1oDOgMYYvaHR0cDovL2Fj
cmFpei5pY3BicmFzaWwuZ292LmJyL0xDUmFjcmFpenYxMC5jcmwwHwYDVR0jBBgw
FoAUdPN+//yfU3rxfOurPqSm2hi6RWMwHQYDVR0OBBYEFP4GuSyVfi/m0Lio8S+3
8i6F1dfAMA8GA1UdEwEB/wQFMAMBAf8wDgYDVR0PAQH/BAQDAgGGMB0GA1UdJQQW
MBQGCCsGAQUFBwMBBggrBgEFBQcDAjBMBggrBgEFBQcBAQRAMD4wPAYIKwYBBQUH
MAKGMGh0dHA6Ly9hY3JhaXouaWNwYnJhc2lsLmdvdi5ici9JQ1AtQnJhc2lsdjEw
LmNydDANBgkqhkiG9w0BAQ0FAAOCAgEAABxayeHitwL18QeXSQvRZ2eiNb82IlYT
uvER4JRMzZDWoamKOqmD7KXSSj+sdBThYiRkkNiVFiMn2qoYAdylI2I4w1npbxyr
ukfXQ7tadTEiMCFva0uHHw9lpBx+oyy9rcLM7qC5qquksyhC222Yt3WbqC6Fla+L
o3GlTOpogqexeyc9hgvAQxeMmq+xyDcjSLzKmmRmMKQ9y3w7wpufXTO/0K5uOLLZ
sfyXZTw+MYYeIk2+GNv1qQBbWo3gmwlD1W0pJEHe+/KxiCRkDHpJY7Lk2Rm4bSDZ
Rr4Bn8bk/XJWpiu7Fm9b8piPKjTtstDYTzu40ccPRh9UCWDUz4nKF97dXjIgYf+a
TA0vnKdlnpPUDeBVpfyXavhGf/akFh5AO7/v6xkzWOUlawn5g614mWhOQ6ITwmua
y1spnpBO684d0bynFQfMoZGS5fdKoYKKDzp29xhBm3s9WD1f/oP79Ie0eDribpOv
j3Xsjz72MTG4+UVxuv0OIYuXDc8x1foMzVOco6DxuLel6KG5RH+m0tWmX4ouCgBK
TNUQC70AWHBa4PCF5YA7H8qVnH2EUBPo3rxOY0wN6GzyMbg9+D9l5e2Xcg7/ytqY
BIBnZKLPjzS3OqUsM9UgUKGwcEnaHnmRxH8vyVEMGnoK1cZNf9uDM9sMGgQUzKwV
wixwyINOM8U=
-----END CERTIFICATE-----
```

</details>

## Serpro SSLv1 V10 Certificate Chain

AC SERPRO SSLv1 V10

<details>
<summary>soluti-g4-chain</summary>

```
-----BEGIN CERTIFICATE-----
MIIHAjCCBOqgAwIBAgIJAJVIeKgiEmNTMA0GCSqGSIb3DQEBDQUAMIGYMQswCQYD
VQQGEwJCUjETMBEGA1UECgwKSUNQLUJyYXNpbDE9MDsGA1UECww0SW5zdGl0dXRv
IE5hY2lvbmFsIGRlIFRlY25vbG9naWEgZGEgSW5mb3JtYWNhbyAtIElUSTE1MDMG
A1UEAwwsQXV0b3JpZGFkZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2
MTAwHhcNMjAwMzEyMTkzMTQyWhcNMzIwNzAxMTIwMDU5WjCBjDELMAkGA1UEBhMC
QlIxEzARBgNVBAoMCklDUC1CcmFzaWwxNTAzBgNVBAsMLEF1dG9yaWRhZGUgQ2Vy
dGlmaWNhZG9yYSBSYWl6IEJyYXNpbGVpcmEgdjEwMTEwLwYDVQQDDChBdXRvcmlk
YWRlIENlcnRpZmljYWRvcmEgZG8gU0VSUFJPIFNTTHYxMIICIjANBgkqhkiG9w0B
AQEFAAOCAg8AMIICCgKCAgEA61jQVBX27GVzyZkJuyrEezqjBGdLSJDFRyGdwxbm
8Ntr0AA8blhDaN5ASDOjqDESMA7xF38znfkZWBMLxJ3Ob0271W6G9bqgTwp/svhZ
s91UcbZW6sB7gyxzMTGWLxcFMeBrurM0QpMVsp8hDH5Suv5rfP0YB9brz60k104u
HG625rAcbRKHn7XsWJ1ZUQcwRzx1g0L1NlUKpsk0+eOAxTcVSVRTO33k+n6Gve83
4MXMiG6Orved4isnEvQnl4AecCXOuUuM3vXZ+kdJGTpNy1HOy0coFdKCJSSCxU/y
TbTiAiRJTc8rbvor3I7k7wR4ZDR8alDbW/Sbw1JEMtbQqMOXEOV7iEUIub0/uNT2
g0oM4pu8DAxhIwy2YQCpjfCbzYu2bf1nabuOEQ2B4mFt/zgoxa5FLsM+0IjpCi8u
z9RqLvYFo9pIy5BTi7JMkVfbgqcOv7vkQf3xF7sODdInCVRIbB0R6xpHm+bpitx9
t5ip+Sf24QFlKbjy0gwVAnaEyf/iQF+t8qgcFBO65kyfH/2vs6iYg5TNhFKtjpqQ
iTyI7YkRkfTbLFdcgZbiRUUs5TFi0BkS4PAWupO1GgV9sJdk9gm3Z+KNZDgoAnu7
Cvhq1JXt6t7qO96WzBx9q9hi7T6eld1VFrV5Ya5kxM9Lgh+XcBDwfnDLI1Yoozbd
MbkCAwEAAaOCAVcwggFTMIGtBgNVHSAEgaUwgaIwTwYGYEwBAYEJMEUwQwYIKwYB
BQUHAgEWN2h0dHBzOi8vcmVwb3NpdG9yaW8uc2VycHJvLmdvdi5ici9kb2NzL2Rw
Y3NlcnByb3NzbC5wZGYwTwYGYEwBAgFpMEUwQwYIKwYBBQUHAgEWN2h0dHBzOi8v
cmVwb3NpdG9yaW8uc2VycHJvLmdvdi5ici9kb2NzL2RwY3NlcnByb3NzbC5wZGYw
QAYDVR0fBDkwNzA1oDOgMYYvaHR0cDovL2FjcmFpei5pY3BicmFzaWwuZ292LmJy
L0xDUmFjcmFpenYxMC5jcmwwHwYDVR0jBBgwFoAUdPN+//yfU3rxfOurPqSm2hi6
RWMwHQYDVR0OBBYEFK0WT0vxDL7CiqKFGNcNRiWTIuPNMA8GA1UdEwEB/wQFMAMB
Af8wDgYDVR0PAQH/BAQDAgGGMA0GCSqGSIb3DQEBDQUAA4ICAQCDvWkOYakalAHB
3ZcifI9yLyuTtjR8eYXlfDesYr7zMFVlmduVghCgueBMZxmht9BpLq9/ceBWu1q8
sKge5oNNyySPmBJFe+CLjtB7Z1Ljk0Q/7A59lMCDZajojJlSEnH6pdhxA1JD58E0
dGsom3SufuBWxdNfgsvpQNXDoKp48VlkyL4DKFCdJExtzuR5IlcQbB1FrmB5m2zo
GG6j7UdoevmikIv01la+8kyn7CF5aNubRE0cfwxulik5LNM1uLIwfUVwYbbQiB8z
baLUOS2lU/pYr+seLQ7VBPHps/guGB9hKei/Df49KWjDVplu3+AuZhBHqiK533VJ
f9Uwv3Rvx8FCobT54OCrAVfnFs8F6sM3dPh1u7AbW3Ddpeo4oBH5kBA0feLvLk7v
mOnOq64oPMMoj+g6x0B0v7tGqOrNBZK486MaU/uaJi+omx+Le9EfyIz39BbRYGdV
JvO/9P8vn5XnNXsmqziw08ENLjHcrro48tRm3YX0/BUgoitjMUqyzlKTgQ8UOpfi
XeJzqvxvUMO/HgZK9aknN3WQXWXxIFG01OHsEOTd2Nddqbrth5qmZE+1IxwEH+ys
QQzlV0pnPL5K0bRuPCqvH4Jr0CmwV2PqD6dkjI/Sy77XDkTP8adAuYjIEynBoQ0b
tqY/0rJPT3dztepWAwRHhKbvO1yYkA==
-----END CERTIFICATE-----
```

</details>

# DCR Automated Test Scope

The DCR Automated tests plan executed against the institutions is based on a variation of the existing [FAPI DCR Tests built by the Open ID Foundation](https://openid.net/certification/#FAPI_OPs) to allow tests to happen without any specific direct input, other what is already available on the participant directory.

Two main differences exist on the Automated Test Plan when compared to the FAPI-DCR original Tests:

- All of the original DCR tests have been stripped out of the authorization code flow, making sure that all testing can be done on the back channel.
- Addition of DCR functional tests that have been either executed during the functional recertification or have been created specifically for interoperability scenarios raised by the Open Finance Brazil Initial Structure

The tests that are executed against the production environment are also present on the [Conformance Suite](https://web.conformance.directory.openbankingbrasil.org.br/), being an exact copy of the "Brazil DCR Tests without browser interaction test plan"

## Test Plan List

The following test plans are either part of the Automated DCR Test Plan Scope or are expected to be added on future releases:

[200624_AutomaticFVP_TestModules_Summary.xlsx](uploads/113acb4e5ee8f0e97e7feee14a014693/200624_AutomaticFVP_TestModules_Summary.xlsx)

The following certificates are used on the configuration:

| mtls | CN | ClientId | kid | Expiration |
|------|----|----------|-----|------------|
| mtls1 | AC SOLUTI SSL EV G4 | 70ee2970-038b-44d6-9300-d3af3a890154 | 8C_6BXJPhpCHYa5PbxgStjdU6EzIF74HXbeubX0t-XY | 27/06/2024 |
| mtls2 | AC SERASA SSL EV V4 | bc97b8f0-cae0-4f2f-9978-d93f0e56a833 | VsLFCwgZ8nVvmGDfD4d6daPBXphtLrduTmfgaXRK3SE | 30/07/2024 |
| mtls3 | AC SOLUTI SSL EV G4 | bc97b8f0-cae0-4f2f-9978-d93f0e56a833 | BobqahGn3kqH4rytUz2NcAYHPS8ls4EzSyp9CSw9yXQ | 20/11/2024 |
| mtls4 | AC SOLUTI SSL EV G4 | bc97b8f0-cae0-4f2f-9978-d93f0e56a833 | 9LpusG8ucuaZhzQXb9wuCjWegomAvNGuopEz-459T-4 | 30/10/2023 (Revoked on 22/12/2023) |
| mtls5 | AC SERPRO SSLv1 V10 | 21ef921f-7d9f-4fa5-afae-d24545d6c880 | VJwsxBJ-f7g2p66VVjzWjgJlOHdnLVY-V0Ah2CkOwbs | 01/08/2024 |

## Example Test Configuration - Sandbox

The tests executed by the FVP 1.0 can also visualized on the [Sandbox Conformance Suite](https://web.conformance.directory.openbankingbrasil.org.br/).

Those Tests are included in the Test Plan Called: **"Functional Tests for DCR - FVP 1.0 - Live Tests"**

An Example Configuration that includes credentials generated on the [Directory Sandbox](https://web.sandbox.directory.openbankingbrasil.org.br/) and executes tests against the Mock Bank can be found below

Example Configuration With Certificates Generated on May/2024

<details>
<summary>Example Sandbox Configuration</summary>

```
{
    "alias": "obbsb",
    "description": "Example FVP 1.0 Tests Configuration against MB",
    "server": {
        "discoveryUrl": "https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration"
    },
    "client": {
        "jwks": {
            "keys": [
                {
                    "p": "4fgnZu_zXHmZHyEenmw1L3CMx2kF6qK3QmokbEIpa_B4CUh5Bln1E8FihJn09ub_BveI2eOpWdvntPgZBQnRZjDQ_-zhH7iIklgRWtcGdW6HMZVRV9Wvo9_YGFU0buvLdaaDCFp2x9BRnbBkiZyGh-W74MLERTZfwweaEz3u-yU",
                    "kty": "RSA",
                    "q": "2t8ZLs285VLjeqG3ZjKNY3-WKcT5xcUh2ZILz_A9fF6H09XQzAeFajutD3gDJokapaFNuOqYeNfmjP8EEgaYb-g-Mb9gwENAVX8fnzHXTnOTDzeGMbj8a7jqTJqfznZZCCtjOtEZ63nVePt-eXxgpbz1ghYfP7n5ErahWkDy3Gk",
                    "d": "IorvFdJ-5hP_vqvXDLZ7pVewvS2UBiBJIe1jayY8c42ClpzYJWDW-Xsyb43uCh_LXEcwSCmMt8KxYezdLBIKEJ3hn4T6eozU9957U93UwMYHmyT5CkidxZMflNIbTEDjUkuO3J6BgkGUz1K1OxWi5IpNK6ceCuqdimyaYmH9J6dkk9DgVj_Iy1twvVhnx-noGLKW_gLcbfslLGb6VAGnzoPWB15wrW5K3l3BElcyeRggcRMIIAY7yJCIJT0q3avbaeIo7HV2NqEdip5a3UsGkl2pcBMwL-9ejMbl0BWBK5qS-qxxjebucvIWXljWAQ3GjTtXeyK6py5GIXpv12OiGQ",
                    "alg": "PS256",
                    "use": "sig",
                    "e": "AQAB",
                    "kid": "FK57ZxUWIoJIHjWDSBYy9aMozINv0FgD6oww0VvbGrg",
                    "qi": "PmqMKquyijOXsIfA4DunvF3XCASyP0QvFdokZAuIGEkLqcNqTOGitUwGxtNbAgOF0E2tplJk5UF4LLnQiND7_IKo1-6jalgIQ1vOw-tUIhGM1QdOigXw4rP9Mnnun7Gtu5HVBJnEx1HU9lsdpgnvNTFsFyJ6o--AOVRLvVWY9-o",
                    "dp": "t3BN_EB6XO3RofWu94h8PICvqAnX5bwl7OJhowiqu5dAurh8lu1cCKeKpH6e3_hxu2QjUk6AYhQkq0JkfTSVKtIiOEBCGRAivjqEDCxWb-pEEbpXiGhN50iGEmrI3'-rHBkEgSh22I0s3lj1lwFiy1Ytn03QJBO65GogHSeuTH4k",
                    "dq": "iZgXTMUqK0CgoUdo9GZzXEmpLTkXjK0RSqX1pxNwk-8ZlKKmUJ2p0c8STNc1o9QtXFK7ebSBhfa0iY8IEAz1Z-SotL2LJVMh7p2sU3gR0s_1c2uEgV250j69jMroC_N6pRghmag6kz5UZWo1aEo4t_jCnrUpj_ZqDsmhRgvuoYE",
                    "n": "wTI-8ocK1-F_WHd0UjNnQy6YrR_GlEA8hXnVPvCPyywxyt27nLncoB8yLBAXrvypmfPreKcmeWcmMmr0gGD1-Fdk3y6o_RtINv_NXaVhZEHr2Yor0fXgAkqqjIZ42wtHvqcDqzJ8eB4sI-JoveovYSc8mQCRHB2GipdBQHZ9NZ2KYNx-zd0RC1zU2mKO8RWavsbdo7rprhrXCVEBaUPxQNcTc4kTbvaH2yKEwH2QhNdGoS7n8gjGnGoLMHmOILjFqFy4Vg0eIqWvq8zuu2CYGsHne6p9GgUuR2IDCgUVseEVcePoad4foffiNZxKGo2baCxBAskL-tk0d5XSb9LOLQ"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        },
        "org_jwks": {
            "keys": [
                {
                    "p": "9H_KX2EZWAVx6FNtSpB9Gvius_jsZ6BdQtvaipbBLpVFTMuPBqMHncrVSt6YhB0px5uMrw92g1opEH-GtRV8f-mMuhAMVxK2pVse7vSobslPMnfFqIUzvskgX33-knA2GOJjfLc7CwfW8cyDSh_cKMz_dSV_5MmfgmNhKlMYhEM",
                    "kty": "RSA",
                    "use": "sig",
                    "q": "1U3HZbSi8vbq4DOCmJsXEJHRnhzYzUR3n1cNtGU7fueCaTuix_-SqAmgcj4_bUuMmEOjGQgaveMY_DIPI8NE8E0t5nAG_IBnB7Sd_iSMf6lhoteFUInIBI5oHd-omus9-OBJ-UHke-3J6XJKAeyk6jBBuLV1Nm6LSPOpTrMHdRs",
                    "d": "fU5tVoBtlHjAjdGeuEXNKFjQ5pbniij2OJ-t8yhaEG7VTYNqYc3PUeSMwllOy6R6Ug4aCS80fcls7H9_bgtmf5Y9IZb4xNX7dL4JbH99j9wGkZsj1gfZASSYnsYlL2fI9oCWFWC4GwqPtu3lYm5NHE3D4TacMjYFIW7PaevFNuAYYO9q1teuc7XwIw9KnH-tYfMubujtsSKESuTZBwuHLphRriEtK5zDN1IFCaZP7qyfivOziF4Zuv1MHUvgy1mLO2CHcQL-ycwYzOI9Ove4hj9Bm9hN857rBvit8U-pUobBaglwGKVatH80qL13n2eRMG74v8kRI0jEmuKJlxtfrQ",
                    "e": "AQAB",
                    "kid": "i4bP8Jb88xhp6ydmcU7SWK76vpK80s9pOaOyC6mSdiQ",
                    "qi": "ekyikQWhFYIt6DxR5g_UptAh0yKjHD4jmxu0WYsshMOIQHK7Fyu1shNm8zncrw16B4xEwJO9Mk_edUbYr1jQDDrlsl2jF6fy2LvzFjNN3DG2hsOfMz1o7H0oing6AUZcT843ScIJQcI2N_HKVPcl8ezyrXR3kkEUkxGzz3Ru-_M",
                    "dp": "h-jZR7ej7Ofp76kgYYh74phGFMjUMK5V6SppCwzOCeT0BsJImPna6_2qHtopkZbceJag11cTG-TsWr1o1hRBhqD-lxcApQ5D9Rr30QCy-BJzMayedRTGNNF8a1iQQDqb960wfE0mRvVuqC509KlNKmj5v9a-hyEEx-gSRQK36B0",
                    "alg": "PS256",
                    "dq": "nVelaYGo3Z6EPWPhxt5IUkGuJXrT9f62WsRlaJdwHrl5elSyS-NbdDa9suf185JSIJNsAO_4ge--I3Jttoy5EqVr4Vrr3GB_H7D9BlZBiX4RdoSSY4lvEOVXKgosnjI-4ZHZH1OazkvmsBxNOUQtlk6IfE7mKoO6nNKYJmRrcNc",
                    "n": "y7icQbO6wi3E5FtZzbGUMVgcMWgYCZr2yFlOXZwwS41_H2VMUry1pr9cc6Uxfxcl1YRamy3UlKrmWW6iPipJMNwrAV20quzrEQxXHwqS_McRwqawCLYHNTjXykqRmrA07YxvYIP5stta-C4OhQSm77QZN9taaAZLruo0JK0PzFI7tt75FEC2LjLBAGh9cDFY5rJkMpXd1WUAQkuwoMhretVq3W6UBH8_8YP5Bbke6uJ5gA_scYcrsTOXAfizkeqjdns9f1xTW4C2IUqXGyF1Cv1yPZsXT_szs-uQtBN_WFESGiGOs_e8hQs-Oc4HmduK5tnCp70OI6xQh4kBbt2SEQ"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        }
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHMTCCBhmgAwIBAgIUV/TwjE0XFUydwF4OJEEcLiRLlGswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjQwNTIwMTQxMzAwWhcN\nMjUwNjE5MTQxMzAwWjCCAUcxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDESMBAG\nA1UEBxMJU0FPIFBBVUxPMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0g\nQ2hpY2FnbzE3MDUGA1UEAxMud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5r\naW5nYnJhc2lsLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxHTAbBgNV\nBA8TFFByaXZhdGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAkJSMTMw\nMQYDVQRhEypPRkJCUi1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZj\nMmMxNDAyBgoJkiaJk/IsZAEBEyQ5MmY2YjBmMy1kMWVkLTRmNjQtOTk4NS1lY2Vi\nZTIxN2NiNDAwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCXCov0QhgS\nQ4LaG69uh40cFe4sl1YhCPmz81N5j+EW7awShamj6+ubbXhjxhbuncoRF4AYz452\nSEnDwRznifJ2Phpc8wMsvqviL6rHTz4bzhIemsLcV32NfjqerTzqEQMQ8rrJOBwE\n58YqkI/fxkOv6aQrgcojn2hquUD50ixopDpKMXE3+cdB5qGAnWg9gbhL4PUOgWwH\nRQhaHZln7p8yR0m4Zz6L2TKdnG67EqTLhiqhZQYmFCt3CilApqZ7p3Hz2VJ7/MOf\nRbxGP52RHMVKK8DHwEmMffede0imPD/bA1G0I3lw3eK8Kv4W/Ktop8RBu0V7Quiz\nLUjacb6sXSVhAgMBAAGjggLfMIIC2zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBTb\nLgyYT1X5bZIpKER+/3GYRV8ifzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0esdbE\nR0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3NwLnBr\naS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIw\nWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5kaXJl\nY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwOQYDVR0R\nBDIwMIIud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9y\nZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYIKwYBBQUHAwIwggF0BgNV\nHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIwgegM\ngeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3BlbiBG\naW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNlaXB0\nLCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRo\nZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZpY2F0\nZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsGAQUF\nBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEBCwUA\nA4IBAQBoNR0h13vl369lXR3g9mr2caJel76Uy6jgY25Gz5sk+8NHbNs5X8hBEs8v\nb92E9GdlpnFWKD1KSf8YZZKZ/kM7emT5wIcR1vJtYYipK9douOt083HO12T/keNo\nS6lMNLOjVqD61U9qi9cTfkl/6HNu7XRNmnN8xJIYaUKP35mkefw5RydrJzD/6ujq\nLqQXfHD+DzvmqjQFMRhM52Fot/tOOXh+adyB/Ax7Mexod0ItaaXypq5MZrYm1qDM\nX43hhSftvKzYx5kHtoUzBsm0LDL+jzdd1hKfRvtfwOnMoYfayTEjTmh907qqyy4Y\n9egNvG0NxwoT8biFZ4Njik8nYlNz\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQCXCov0QhgSQ4La\nG69uh40cFe4sl1YhCPmz81N5j+EW7awShamj6+ubbXhjxhbuncoRF4AYz452SEnD\nwRznifJ2Phpc8wMsvqviL6rHTz4bzhIemsLcV32NfjqerTzqEQMQ8rrJOBwE58Yq\nkI/fxkOv6aQrgcojn2hquUD50ixopDpKMXE3+cdB5qGAnWg9gbhL4PUOgWwHRQha\nHZln7p8yR0m4Zz6L2TKdnG67EqTLhiqhZQYmFCt3CilApqZ7p3Hz2VJ7/MOfRbxG\nP52RHMVKK8DHwEmMffede0imPD/bA1G0I3lw3eK8Kv4W/Ktop8RBu0V7QuizLUja\ncb6sXSVhAgMBAAECggEAAI2flJN//8j5xAI6J1rbksR42TJiUIetGaYMvPofLWft\nTqXhOzJY/3pl/6+GczfLih9d0aLUI7vUU4hJ94v3FTpWZQlLSxHqBBqlL32xHcRN\nHaDtRFXfddtYBK6QUhF8QGiTfZDgcMOh/XJwpu5srTN2Men7unQKx88nog1xC56t\nIvt3BQ3dbBoqa1hW2WU33k5lrlqYXt5MbSbeNPU6JCxWB42rIrAylT7HR3lfE3LQ\n8EgN9Ma7b4HiBzBx34fQ8fCPZsG6RkthEpbEW0VrUT2OImmY/YZQi1439lTzw+wu\n/VkSiHRC+A4rzsXHaz1KNs19Za3fXkrFihlv4kDgFwKBgQDS+wjdFHsq3WkQKl0Y\nGooLgGSbBUo/Ud7ccpUC3WPIk3ADnwbPyMm1xDgadm7w5/auEvTCCu3FVr+LW0Cd\n1T1ERn9S83wy1r+wP7vUjDI5vemXZ6PmKuxpdQr4897KL6TBpWU8ZOelEirUHTkP\nItbsC92LzeKoQ4QnWO3OFioUgwKBgQC3RUeJXYIi3VSJjB0OZdwFnp9rOZDuyo1q\n0t9K0XAIzaqAfiHxM7hqlmdFIM/UANjyGSH8qesB2Y5QC8r0UBzDnzqmeQE9YrkW\nVdqoUowr1Mdkl3cBrv4K2ZNE8CHE8G22HNiP+b3yl5CNx6e72svmBy8587mLhyFg\nyl65GlbhSwKBgF5X9zy1PeaLH8Ikz4BJzdUa0uInWW47NAcsDco8KbS1iW91G1yr\nEtf/KH9c2ntLnxl0TJLAxFZsVjcA1UI+6qivRZxYWP963Dj6JwoCryr264/Svo3c\nP99ggUmV89hBudEGHuEE1jkQiKpVbwB/uc/P9n/fzy0jE+NsdtqjOqn1AoGAOHAX\nRZAMQVxTakBBumtXxEtC4KxLm524ywrBRLMWgz+CoCs3nKXGxtwmVT1zgt/37yYa\nN0rEWj96+d+H0pDRKtTgJN/ip9q9EMnDmk5BaEYQWUPjnBsdlI3IMlSYsaMwxgJA\nFqZb/lb6Zw7y8oDAhcf0nS4XF4a3mqz3Wp1n390CgYAR6Gwlx2W/iMA0bEaIwFqb\nSdi4jPpOcuLmu5vtF5VuEsSAcqMAQk6BR0Yivcpu3Crtgp6JmDs7KwwEZshPdJcx\nJoQLkezRuXFd/g+iEZ3VRqZGpboKTKq8A7LqaFc29/2bPs2wa4dDZhDROoWTEy4G\nWSZoSaZHqORnYNYcjtUFPQ==\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\n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\n-----END CERTIFICATE-----\n"
    },
    "directory": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "92f6b0f3-d1ed-4f64-9985-ecebe217cb40",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/"
    },
    "directory2": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "3473da82-e233-4da9-a6d5-d898383e2b51",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/"
    },
    "directory3": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "92f6b0f3-d1ed-4f64-9985-ecebe217cb40",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/"
    },
    "directory4": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "3473da82-e233-4da9-a6d5-d898383e2b51",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "apibase": "https://matls-api.sandbox.directory.openbankingbrasil.org.br/"
    },
    "resource": {
        "brazilCpf": "76109277673",
        "consentUrl": "https://matls-api.mockbank.poc.raidiam.io/open-banking/consents/v3/consents",
        "brazilPaymentConsent": {
            "data": {
                "loggedUser": {
                    "document": {
                        "identification": "76109277673",
                        "rel": "CPF"
                    }
                },
                "creditor": {
                    "personType": "PESSOA_NATURAL",
                    "cpfCnpj": "76109277673",
                    "name": "Marco Antonio de Brito"
                },
                "creditors": [
                    {
                        "personType": "PESSOA_NATURAL",
                        "cpfCnpj": "76109277673",
                        "name": "Marco Antonio de Brito"
                    }
                ],
                "payment": {
                    "type": "PIX",
                    "date": "2024-05-19",
                    "currency": "BRL",
                    "amount": "1333.00",
                    "details": {
                        "localInstrument": "DICT",
                        "proxy": "12345678901",
                        "creditorAccount": {
                            "ispb": "12345678",
                            "issuer": "1774",
                            "number": "1234567890",
                            "accountType": "CACC"
                        }
                    }
                },
                "recurringConfiguration": {
                    "sweeping": {
                        "sweeping": {
                            "transactionLimit": "1000000000.00",
                            "totalAllowedAmount": "600.00",
                            "periodicLimits": {
                                "day": {
                                    "transactionLimit": "1000000000.00",
                                    "quantityLimit": 300
                                },
                                "week": {
                                    "transactionLimit": "1000000000.00",
                                    "quantityLimit": 300
                                },
                                "month": {
                                    "transactionLimit": "1000000000.00",
                                    "quantityLimit": 300
                                },
                                "year": {
                                    "transactionLimit": "1000000000.00",
                                    "quantityLimit": 300
                                }
                            }
                        }
                    }
                }
            }
        },
        "brazilOrganizationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
        "consentUrl2": "https://matls-api.mockbank.poc.raidiam.io/open-banking/payments/v4/consents\t"
    },
    "mtls4": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHMTCCBhmgAwIBAgIUeLk+WrYyduKCnZdkgZ1KLbg+m28wDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjQwNTIwMjEyOTAwWhcN\nMjUwNjE5MjEyOTAwWjCCAUcxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDESMBAG\nA1UEBxMJU0FPIFBBVUxPMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0g\nQ2hpY2FnbzE3MDUGA1UEAxMud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5r\naW5nYnJhc2lsLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxHTAbBgNV\nBA8TFFByaXZhdGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAkJSMTMw\nMQYDVQRhEypPRkJCUi1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZj\nMmMxNDAyBgoJkiaJk/IsZAEBEyQzNDczZGE4Mi1lMjMzLTRkYTktYTZkNS1kODk4\nMzgzZTJiNTEwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDa9J1n3LAM\nBAZ2JgNzcVBR2pTi/yGBRG0a7+nPlClP4c04N6hh+O86NcGhSKtgdQ6z7oFmYWkk\nfp5YvvJxKEvzYfOl94mEgc35hDvSnrQMC6tOWJa2quGEFnr19ZY5w85nCfkvgtBG\niqAYjGCjCNJutB217+gSGCjphq32cCuAQODztIevDnEFoO7vHYMpXANpUmvTo2fb\n9u/Hm/tiiZm58azI7pixWVMy4p6znOYvZANFEVHu+YpyC8efg/nvOdUBfJsGXynS\nLorctIUz0FNwWfngfWCpj9FmousSUkEXK6gM2WpLrtYvxD7Hu/69S/tKQS4zAvq5\nTRMYChOrB8QLAgMBAAGjggLfMIIC2zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBRn\nOYBc9xcOdlT2JtYcCJ1gue8NmDAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0esdbE\nR0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3NwLnBr\naS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIw\nWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5kaXJl\nY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwOQYDVR0R\nBDIwMIIud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9y\nZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYIKwYBBQUHAwIwggF0BgNV\nHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIwgegM\ngeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3BlbiBG\naW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNlaXB0\nLCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRo\nZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZpY2F0\nZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsGAQUF\nBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEBCwUA\nA4IBAQALoK3mbAQTW4JoCn6eV7Cq79J78s9NaHMJ4HY3hiAT9CGeK1SLC+XcqU0t\nXK4eiugy1933thUm4Ki7rK3642G24lj3N3DGpqExcSaAdrc40eV6r8hyQyDqHiKg\nbsLKToFYBhtfSQqdV06J3gYC6EEMPAh8LS4MOlCps5lterFQXhqMWZ3RpgFgzAfa\nSV7ppxZpExZBlF5TeoOgxyR3VXlbL9hkVS9nydq4AzI7nsr4gsp3zZz2yAZzLocM\nxS3GCsOCfIFb0G/oKpPwx9bV/zjyeoPpjeviMLq2yHai/iU8N3LCgcY5r1TTMkMq\n+ZkFjMaT0F5agDpX3x98gCOSN5iC\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQDa9J1n3LAMBAZ2\nJgNzcVBR2pTi/yGBRG0a7+nPlClP4c04N6hh+O86NcGhSKtgdQ6z7oFmYWkkfp5Y\nvvJxKEvzYfOl94mEgc35hDvSnrQMC6tOWJa2quGEFnr19ZY5w85nCfkvgtBGiqAY\njGCjCNJutB217+gSGCjphq32cCuAQODztIevDnEFoO7vHYMpXANpUmvTo2fb9u/H\nm/tiiZm58azI7pixWVMy4p6znOYvZANFEVHu+YpyC8efg/nvOdUBfJsGXynSLorc\ntIUz0FNwWfngfWCpj9FmousSUkEXK6gM2WpLrtYvxD7Hu/69S/tKQS4zAvq5TRMY\nChOrB8QLAgMBAAECggEADWrl36pnKJoki5/0hshsxVKLD8ZvsK+KehcCpOOHWcUh\nSAhZ64SpCemnNhfkb9kS767P3WZekZh0Yd7afFm3HpdXKkmbJg4bgUz7qrWdnFfC\nUl8P/7cRpWaiEVy3E7VU+pZ8LGlGE+4raMwaOrnWX2dVPMPfXLoZsIakaXb7pQ4q\n5mLXrD3wp+q1Nh/GYF6IqBP46z5KV2cosbpCr51PfmlBSaAKFxUFrv5d+NgUtKVl\n3qp61k5BdZ7GE3YN7sAJQpcA9mGGexPT9FBBSqUbzknrUZunXazdRFIOMK2o3cQw\nLS9g7AqAmP/E/NstgEOAa3ZmbSO0LBlJqipOeGanmQKBgQD5LVQC3XeiWmDSp/JD\nWtxz2jsAQ/Z4DkgHhYT1wfcfKyT/93ModXBqo0l1xAy3Cg2d+sfU4zZhEm7kNsB+\nzUiSn2KohGxhSCMFcj4W54O21L9iU5aLWXa7XOF51YIq31JAmMByp4YyejWJt0Eh\neAWT2vBPceWvkQJvTh1wPvWKowKBgQDg83DgxQSf5zQUjN3sC4GoApsBhEPOP9Qd\nTmoXcFGReoNjqucmrdmzkevzunsOcZmS6EP//RbNNVlNKEkBN3ORwT9CZfJYkT23\nkqvffl6l3REY0GA4tmkgQ3YNYz84eoV6DjghjSIQqM3yrvrteLc+ZIkeOJ5i0z3C\nc81tZIqfeQKBgQCd5JMvnZaJUiu4UKO6+oBnCQoKCQbM3H/YBEtUTyyAm54+dFaM\ndJ5fdEjATxKficdHK/okdDWpHT0Xb3pa30n1XvntPrxOiJ9ofBPL/7f+yqDbdYwX\nkQEjiJ93zEtHT2uXczO/c1gd9EKomW6z/pHKNxm/vbSFo6WfUihlT//XcQKBgAUA\nRIUqvCSV7kl6rEBgLRzAGhQZjaxbLOsN4DvvKlESqTMhDIyGlu1wFA/SGIREsEZc\n1Y4uYUBkrDyT5bOaOP6HjlF6lL21VOrs3tdUJuSHGqczksAQBhxKg6heiXxG9Qq2\noDbWvWgjaJi5nSiEY4aGk6nRVmwaCCh3jJye/Jn5AoGBAJw5qkBXzlLw6UBtGKbX\nwU+zYj9KxrcrLWuBr0Rc7Thau82J9DZNpSHWIBeX0FY3OMJlzhRrFtPEnS5zwBC8\nTFYf5LDCnIiruE05Hi+Q8RDE51+tInUL793vX9YtmxqTnf4RPPdpZVZ12TpEAkLm\n+8T6VJ7m3oVAyKPkOmbrX0iE\n-----END PRIVATE KEY-----",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\n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\n-----END CERTIFICATE-----\n"
    },
    "mtls3": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHMTCCBhmgAwIBAgIUKgRLib2f0KnbpfVQ/QJEjI1hUAswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjQwNTIwMjExMDAwWhcN\nMjUwNjE5MjExMDAwWjCCAUcxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDESMBAG\nA1UEBxMJU0FPIFBBVUxPMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0g\nQ2hpY2FnbzE3MDUGA1UEAxMud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5r\naW5nYnJhc2lsLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxHTAbBgNV\nBA8TFFByaXZhdGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAkJSMTMw\nMQYDVQRhEypPRkJCUi1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZj\nMmMxNDAyBgoJkiaJk/IsZAEBEyQzNDczZGE4Mi1lMjMzLTRkYTktYTZkNS1kODk4\nMzgzZTJiNTEwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCqlAuwYI7n\noxev69D7gumIQ0I8GAeExsiYUl89pvhmaDEx4ixdzzCrtXjX4VYGD7j9wSZ7mTml\nKAGimJIoYcyXSu8Z/K06pJT+DvuA015MFaIIFLFw6L4knSAjJmrXxb4sR9HDoqtB\ni6Eg28UDfchG8kbjmjzcFg5ItoLl9a7e7bZ76YUd7nYL2TcQ/LpLDJfIh3hzDC+h\nBj4oGsd8P+iII7VTBbOJI5t+WFoE5cNST4NquDkeNpEVIp/rxADVngjh78CZDtK9\nruYPtV+jGZT37A49PzPs3WNyRQQguo+l9K9cD89lhcUK1XoNcSKw8KnD5jmJGxYF\nfNRnDLHDpp5ZAgMBAAGjggLfMIIC2zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBRu\nq5LVNrtXhhR9r67AjV4xwNQCcDAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0esdbE\nR0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3NwLnBr\naS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIw\nWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5kaXJl\nY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwOQYDVR0R\nBDIwMIIud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9y\nZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYIKwYBBQUHAwIwggF0BgNV\nHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIwgegM\ngeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3BlbiBG\naW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNlaXB0\nLCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRo\nZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZpY2F0\nZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsGAQUF\nBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEBCwUA\nA4IBAQBtsK9WqgSg+ZPstULWalpvmxTg3D302999MpFWgdjjLoHNOyFVZeMh80b+\nMzHnCoLqbP844uOUr+NpTNebF95kraDl/UeauZQIBS+hnM24ZrDB0JQ55WsmCU9k\n9Qw7Up1MPt86OU6GYbcpDc4G4bMvk2iM4ZhRqqTvt9eRityQ2KpMY3OC+JFuOBKW\nWhG7GlMPXy4eg8YebqF04cnXTNkqm/nz4R9Kn3g/yZL0Pb85Ir/tJoyi2FlBozXe\nWnXRUa7EfFjKUSO6wqWBhEWgKyVlVz83rzNIIEUucsqYhbr4pe2jQnPdzd+7TZy7\nxjG4mJUl57RUL0WrNzT/Jvmosp/o\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQCqlAuwYI7noxev\n69D7gumIQ0I8GAeExsiYUl89pvhmaDEx4ixdzzCrtXjX4VYGD7j9wSZ7mTmlKAGi\nmJIoYcyXSu8Z/K06pJT+DvuA015MFaIIFLFw6L4knSAjJmrXxb4sR9HDoqtBi6Eg\n28UDfchG8kbjmjzcFg5ItoLl9a7e7bZ76YUd7nYL2TcQ/LpLDJfIh3hzDC+hBj4o\nGsd8P+iII7VTBbOJI5t+WFoE5cNST4NquDkeNpEVIp/rxADVngjh78CZDtK9ruYP\ntV+jGZT37A49PzPs3WNyRQQguo+l9K9cD89lhcUK1XoNcSKw8KnD5jmJGxYFfNRn\nDLHDpp5ZAgMBAAECggEAFykr3yJ1NOFxrWrNAOF5GQ3c1/EBUFd3VCtXEDV0I9+A\n0n+du40O1Dm7M0C+3+rRmO7ZbU3URGcGtc+WhNImp+I+Td5/nOdM7aQWJRtOAfGs\nAwHgR+7qJmmJPAyS1EJevH9x7WjQbQFq+t2sRfmVsIBj/LJsEgwSm2/gnR27RTxz\nW1HJYmq6d3yAyGeJ/P4aEzakB5v8088bHFjTkhINOFjRi5KJslNsC5yFjYwEjg+r\nNKq6pQ790sAygLVT+qT6mvA/X2mbzBmXtnoIYbI1CcQdVdTSF3gBqmNIrj/OU5/d\nExFymrslX7msQTunbYUueuY6vNs9EZr2GqtEeS2DOwKBgQDuqUe4+ymJTZwj23cz\nUJQo5av7fvoAru08Vec0+na2Lj3YdPPNjDseeKFhTSvegsBnVg9h22SIVe0IKbj9\nrePNL2HWQCgZsEuunJ1hGPBHdEEMueqyvkkCyKJ6qwS+xWeucDhYgrD8Yx2+eeaQ\n+7IsIsAqOj1Qpi7GUpvlwahaIwKBgQC2+Ifp9psRwzO7Vk8SIfQCC1uWx9pNN2dj\n6PWe8Cd+JU6oFGXH3u10Z7Mcnol1W5l80iIizMNsR8Kjr3aS5lZEu7izQA9S+Wkl\n/CCV/Kiy9/Y70JHxW6D9J3FXFaMKwx1f46uwBBSw3fIa+gh4u0hNCVf0m6pgpHqV\nTeVSOwrXUwKBgAl33ciQ7kzsL02c31XB1J7qva/0kaaFShQitFF9vkfr/bggq6tz\n7MSAtKZPkXX6afevilyvf4WJIyY3wYcO5wK05oTBdtXOELKUtAmuG5o6GnqOxajh\ns7PQkeGb90w6OKrK+PFJ/guFQyDTZTpLQf5OQqFqPhR9A04K6PRsgmlRAoGAPqhv\nityLkBKj5ZSR8Wi1MfoHvGPmSykc++bsLiiZraZDAGYz0LVz5bgZa0STWCAtOMSR\nMg+jILKWYg2Vcor0ogcTIjdeyBBnRL3JvvNOJjOqHCO5xsiVIfxe4O6k7euRZKQH\nyHgtScBHx5s2SXoBMXhwqXChcQUCgZyyWm2jsccCgYBIdkmPEiyUFcidZxZapsg3\nEXrnZGYG9ZbRQK4vCvZl/aNexjk7yd4Hd+4DqAl/OMLus7ocPJf5Lk61eVSyfqCI\nR4Fw9pBrQtsAnZa2exVejbk7Ofs1wNmyK0HL9Lcl6YpTf/HCCtOBIedRj0sWjxNh\nwcxEMvABWqoXFDbCQ9a31g==\n-----END PRIVATE KEY-----",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\n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\n-----END CERTIFICATE-----"
    },
    "mtls5": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHMTCCBhmgAwIBAgIUV/TwjE0XFUydwF4OJEEcLiRLlGswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjQwNTIwMTQxMzAwWhcN\nMjUwNjE5MTQxMzAwWjCCAUcxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDESMBAG\nA1UEBxMJU0FPIFBBVUxPMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0g\nQ2hpY2FnbzE3MDUGA1UEAxMud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5r\naW5nYnJhc2lsLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxHTAbBgNV\nBA8TFFByaXZhdGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAkJSMTMw\nMQYDVQRhEypPRkJCUi1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZj\nMmMxNDAyBgoJkiaJk/IsZAEBEyQ5MmY2YjBmMy1kMWVkLTRmNjQtOTk4NS1lY2Vi\nZTIxN2NiNDAwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCXCov0QhgS\nQ4LaG69uh40cFe4sl1YhCPmz81N5j+EW7awShamj6+ubbXhjxhbuncoRF4AYz452\nSEnDwRznifJ2Phpc8wMsvqviL6rHTz4bzhIemsLcV32NfjqerTzqEQMQ8rrJOBwE\n58YqkI/fxkOv6aQrgcojn2hquUD50ixopDpKMXE3+cdB5qGAnWg9gbhL4PUOgWwH\nRQhaHZln7p8yR0m4Zz6L2TKdnG67EqTLhiqhZQYmFCt3CilApqZ7p3Hz2VJ7/MOf\nRbxGP52RHMVKK8DHwEmMffede0imPD/bA1G0I3lw3eK8Kv4W/Ktop8RBu0V7Quiz\nLUjacb6sXSVhAgMBAAGjggLfMIIC2zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBTb\nLgyYT1X5bZIpKER+/3GYRV8ifzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0esdbE\nR0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3NwLnBr\naS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIw\nWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5kaXJl\nY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwOQYDVR0R\nBDIwMIIud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9y\nZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYIKwYBBQUHAwIwggF0BgNV\nHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIwgegM\ngeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3BlbiBG\naW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNlaXB0\nLCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRo\nZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZpY2F0\nZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsGAQUF\nBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEBCwUA\nA4IBAQBoNR0h13vl369lXR3g9mr2caJel76Uy6jgY25Gz5sk+8NHbNs5X8hBEs8v\nb92E9GdlpnFWKD1KSf8YZZKZ/kM7emT5wIcR1vJtYYipK9douOt083HO12T/keNo\nS6lMNLOjVqD61U9qi9cTfkl/6HNu7XRNmnN8xJIYaUKP35mkefw5RydrJzD/6ujq\nLqQXfHD+DzvmqjQFMRhM52Fot/tOOXh+adyB/Ax7Mexod0ItaaXypq5MZrYm1qDM\nX43hhSftvKzYx5kHtoUzBsm0LDL+jzdd1hKfRvtfwOnMoYfayTEjTmh907qqyy4Y\n9egNvG0NxwoT8biFZ4Njik8nYlNz\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQCXCov0QhgSQ4La\nG69uh40cFe4sl1YhCPmz81N5j+EW7awShamj6+ubbXhjxhbuncoRF4AYz452SEnD\nwRznifJ2Phpc8wMsvqviL6rHTz4bzhIemsLcV32NfjqerTzqEQMQ8rrJOBwE58Yq\nkI/fxkOv6aQrgcojn2hquUD50ixopDpKMXE3+cdB5qGAnWg9gbhL4PUOgWwHRQha\nHZln7p8yR0m4Zz6L2TKdnG67EqTLhiqhZQYmFCt3CilApqZ7p3Hz2VJ7/MOfRbxG\nP52RHMVKK8DHwEmMffede0imPD/bA1G0I3lw3eK8Kv4W/Ktop8RBu0V7QuizLUja\ncb6sXSVhAgMBAAECggEAAI2flJN//8j5xAI6J1rbksR42TJiUIetGaYMvPofLWft\nTqXhOzJY/3pl/6+GczfLih9d0aLUI7vUU4hJ94v3FTpWZQlLSxHqBBqlL32xHcRN\nHaDtRFXfddtYBK6QUhF8QGiTfZDgcMOh/XJwpu5srTN2Men7unQKx88nog1xC56t\nIvt3BQ3dbBoqa1hW2WU33k5lrlqYXt5MbSbeNPU6JCxWB42rIrAylT7HR3lfE3LQ\n8EgN9Ma7b4HiBzBx34fQ8fCPZsG6RkthEpbEW0VrUT2OImmY/YZQi1439lTzw+wu\n/VkSiHRC+A4rzsXHaz1KNs19Za3fXkrFihlv4kDgFwKBgQDS+wjdFHsq3WkQKl0Y\nGooLgGSbBUo/Ud7ccpUC3WPIk3ADnwbPyMm1xDgadm7w5/auEvTCCu3FVr+LW0Cd\n1T1ERn9S83wy1r+wP7vUjDI5vemXZ6PmKuxpdQr4897KL6TBpWU8ZOelEirUHTkP\nItbsC92LzeKoQ4QnWO3OFioUgwKBgQC3RUeJXYIi3VSJjB0OZdwFnp9rOZDuyo1q\n0t9K0XAIzaqAfiHxM7hqlmdFIM/UANjyGSH8qesB2Y5QC8r0UBzDnzqmeQE9YrkW\nVdqoUowr1Mdkl3cBrv4K2ZNE8CHE8G22HNiP+b3yl5CNx6e72svmBy8587mLhyFg\nyl65GlbhSwKBgF5X9zy1PeaLH8Ikz4BJzdUa0uInWW47NAcsDco8KbS1iW91G1yr\nEtf/KH9c2ntLnxl0TJLAxFZsVjcA1UI+6qivRZxYWP963Dj6JwoCryr264/Svo3c\nP99ggUmV89hBudEGHuEE1jkQiKpVbwB/uc/P9n/fzy0jE+NsdtqjOqn1AoGAOHAX\nRZAMQVxTakBBumtXxEtC4KxLm524ywrBRLMWgz+CoCs3nKXGxtwmVT1zgt/37yYa\nN0rEWj96+d+H0pDRKtTgJN/ip9q9EMnDmk5BaEYQWUPjnBsdlI3IMlSYsaMwxgJA\nFqZb/lb6Zw7y8oDAhcf0nS4XF4a3mqz3Wp1n390CgYAR6Gwlx2W/iMA0bEaIwFqb\nSdi4jPpOcuLmu5vtF5VuEsSAcqMAQk6BR0Yivcpu3Crtgp6JmDs7KwwEZshPdJcx\nJoQLkezRuXFd/g+iEZ3VRqZGpboKTKq8A7LqaFc29/2bPs2wa4dDZhDROoWTEy4G\nWSZoSaZHqORnYNYcjtUFPQ==\n-----END PRIVATE KEY-----",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIFvDCCA6SgAwIBAgIUKhBUxL5Dt4w3xH1V3X1n+x/e3hcwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzgw\nMzA1MTQzNjAwWjB2MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxKjAoBgNVBAMT\nIU9wZW4gRmluYW5jZSBzYW5kYm94IFJvb3QgQ0EgLSBHMjCCAiIwDQYJKoZIhvcN\nAQEBBQADggIPADCCAgoCggIBALJFBgmKj3iDF3C8+8smNNQDxLFA9kCcca1iaxQf\nvMI/FKGW2ullHhH+W3EGEajn39QOlccGyrfCONHLqMW53+HAMtwiIvcrJgj72V7D\nnYflO3aaCFwoC31PL1+pMBo88F6jvezZ8BlRnheT7urCs6+onhz8pm0cVNc77U5X\npi8IOJz1QFKecJnFLjG0NiLCzOzjLSo0A8Rue9K/H5fjq+PqKdXG94AoQyFUwlsU\ny4aXbylDz1kRiOSnOlRNPcY/su95pFKQbGgaZZ1fLf89i5PtHAUu92FbD7H7OyYX\nXpZ97La0d7cUH0A4nb+LpOd/f0c8lAN2Ya1B8aKvWiF23q3c8EoAJyhrdkHKe6yI\nYvLC5G5jkbJefeQcp34IgD8T+Tn3aBF7YgmlYUMbnsuokBG28Hr50EAklCclA0bb\n4pmf8nE6y7VQ0CM/bNZd1F9AjxLukkyvkrOD6A6uv+c5KeC+da245dBzsyhiKe9R\nRX5Gkf7NSkDu9b9YkdDaWV6LXxpUA0SmdT9M16yK3XPDKOWBI4gVSB1KuwrOcal/\ndMwFUlxvqdGugRbxDNNukxa0l3JztGg6XYLjEiiYrQ+7HChbUVNlM0l0VZAz4eON\ngYrq2ExUDWlQXiES389/Qz3R3yDk9ib1YsMHwAux2ulCssFVn4EgtnYFfgf3o01J\n3CedAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNVHRMBAf8EBTADAQH/MB0G\nA1UdDgQWBBQVb9vsej3AhKXXgbWRvfmoWNM++jANBgkqhkiG9w0BAQ0FAAOCAgEA\nVPrUd4UDjOhkxOzSN4bMr0cULZJwQPRV8aj99tzdv8Ef44CwLVkLmm7Z2d1uRA9l\n7xbK6W8L1oL95iV4K4o2u4+ZFG7mrOfU2T2wgTfMlIxHDoAxS49flUYkBpQI1Wj4\nJBZ6fKGFVH6PyIio0I2Mx2u80ZX6lPYQ2q4DR6eBUoNt8T8XSWpD4TjroFbOVIp+\nN84alBca/pvW2aF2HwPndrL/Y++HZp3TpdUeBUT757KOZ7hdwf30pxd8qNn8+peb\nbP2h6b9pjKAmS8ciBExJzchhQWJRP6LIdvexTsBQ1HLxlZNrlg66wYT0kuVVzRTa\n0qRvIjQ0ntmhy2DtmE5VFT9O8ahcQL5Ddk8B4dhiy59vjALS6kIUXJ6GCobzRUsQ\na7b7J7nu+PTY+qVo0LsTMO1rVTUXD63gVk8QmPUwnvduk9nxraNpVP+m17BuEcls\nEsoGAAQYcmzOlnZpqhhbTnbsEayW1bMyxkLjBjXpOfBgrvyv5fU/09lP6VB20FJr\nzVPZWr5PTzaaizDDecSKgZ1ANIwXIIwWirwzDqqQb922JtcH+Ca6JJWgrV7+kDCU\ncVzwKVYievjXMCsmRSzDKEgp4n1AgrxcoaH0smD+qA+wzfsMqvEA1iTNW7zdnF0o\n6UJ9rkWxKr+JRZ5jFO+kpKQ1DxfDJZE554aO8AXzYEI=\n-----END CERTIFICATE-----"
    },
    "mtls2": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHMTCCBhmgAwIBAgIUQbsfNPqgdymAhQUr9B9ho2aiXiQwDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjQwNTIwMjEwODAwWhcN\nMjUwNjE5MjEwODAwWjCCAUcxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDESMBAG\nA1UEBxMJU0FPIFBBVUxPMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0g\nQ2hpY2FnbzE3MDUGA1UEAxMud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5r\naW5nYnJhc2lsLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxHTAbBgNV\nBA8TFFByaXZhdGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAkJSMTMw\nMQYDVQRhEypPRkJCUi1kNzM4NGJkMC04NDJmLTQzYzUtYmUwMi05ZDJiMmQ1ZWZj\nMmMxNDAyBgoJkiaJk/IsZAEBEyQzNDczZGE4Mi1lMjMzLTRkYTktYTZkNS1kODk4\nMzgzZTJiNTEwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCWZGwdFKCJ\npiVIRLPFtv5SDBLkpali74fkk8lb1snY22nL0GlmXfT9nPvjqoNYOZePRkFb6aIf\nIBGwKTwz2mConbBuNrFK3omXBr0qYncKHIsXdiqUycDA307WpBBGQqevdUVqGOIW\n6HMd41dRB/YzuoLaQoygC4nTHr+0g4ol4LsskD8LPd+C/65rwf6hGFa5jYgZ7fsr\nR2WZh8RhQFOus0t2iMc1JMM33WiCoO08UO5DxIBf7+C6I0Vhlmg7EjQqrP2uQlWP\nez7CEOzBTVPvkNL5bSPN68BBUtXhiuYdundtBtVvXUp4k0aozQkspvr4B1BCFwyR\nkt1JHZjegBqbAgMBAAGjggLfMIIC2zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBQn\n1Muny5uXCYQflvU7o4Sfi588cTAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0esdbE\nR0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3NwLnBr\naS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIw\nWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5kaXJl\nY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwOQYDVR0R\nBDIwMIIud2ViLmNvbmZ0cHAuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2lsLm9y\nZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYIKwYBBQUHAwIwggF0BgNV\nHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIwgegM\ngeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3BlbiBG\naW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNlaXB0\nLCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9mIHRo\nZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZpY2F0\nZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsGAQUF\nBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEBCwUA\nA4IBAQAd31lx2qVQ5c9ZX6EuZqJtDKBUGv6M8z7dsyBOYKbyJyV6RA0MuOKY8vyh\nFXMVxxmJZ7iEvbqC4RCaGWwXIA/dh1wk3d/AXr8DDjwtfTvGumuEBDGgMMmnXT3Q\nHkFH3D1QRZzVAEtzVodNjtKYONCXgXXGV6ognCq/UqK3M+RwtnpgseasQdbWFUmB\nGFL7kJUvsVmjV9QI81zpEzPiOh0nQ9rdbZEmCtK1a26MmhGe5vz+vkJEr55zubCb\nYg1jjCJYa61mHMHAuT9RlDZbbpLX2qb3CmiooJZS61xRNV8yV1DvGorJ7DolvT+e\nxgJKH17OFGcs7cLWpO0hgauth4V5\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCWZGwdFKCJpiVI\nRLPFtv5SDBLkpali74fkk8lb1snY22nL0GlmXfT9nPvjqoNYOZePRkFb6aIfIBGw\nKTwz2mConbBuNrFK3omXBr0qYncKHIsXdiqUycDA307WpBBGQqevdUVqGOIW6HMd\n41dRB/YzuoLaQoygC4nTHr+0g4ol4LsskD8LPd+C/65rwf6hGFa5jYgZ7fsrR2WZ\nh8RhQFOus0t2iMc1JMM33WiCoO08UO5DxIBf7+C6I0Vhlmg7EjQqrP2uQlWPez7C\nEOzBTVPvkNL5bSPN68BBUtXhiuYdundtBtVvXUp4k0aozQkspvr4B1BCFwyRkt1J\nHZjegBqbAgMBAAECggEAEo795cYf3ByhSSkWjiAmLiBzTGftCS/J3ePRhgBxaXiv\nYN6tGFwhLr1qkA5V+v3QaCEhUPhPG0wtIpypYzS1l4PYu8u1Vn8zt2wLd+mCtcAO\nogHhAKS3oUAX+IDHyVknBuM6glHjxIlBe2oMjQv7I9MGRsIjnF8QI6S4aiGOsLG5\nr2sp7FrL69DpYS7twm+dnIm0H9LRptkKfXIpqj3Nu3KSxcrLysrROI5wHob7W7HT\nEvXyC2IYsQ2ceD3HTbYcAkcoQc3QesNdI1AdYDGmI1g1B2qGOEqo+wMatShoJFTD\nixZ9uUxQxdVaBSdtjEZwFTvAF1WXFKREaeJ+VORDAQKBgQDMfLMo7sorZkcNzqsO\nzLf3Rv9dsD+cX+8/bYRxSsrP5rGJ/qFzscyFQsOhMZQ+1vnSKT9F9TY69hFaVzNI\nUoE55zs9q8qot9blh3gjnLS8IHU/h9/Y8/eKt1HI3oCh6L3xTTr5R2WcmX/FPD4w\ndgtzYulDBQYpSTZ9q6o8ViIzwQKBgQC8RyqDSsALm1VtPvtTTtXqMc/hY/QXCKBi\nZ8xQ8Yux32vlivkmeKW158ZAtmSvJ77ZREsJX68SlB1Oxx/MrGY185MuaTcs8KzQ\nYDnXwe2rbKbHxQyjoHZ1YsrIa0Dhx9Awyd0uUQ3AKbai1ct5ZpCApmfu9rKblqxn\nm7ZreND1WwKBgAMLmF9zru8Whthdy45c3iCAniz3AvuBMj7vkpldU8fk16AGesEO\nVM1nQSKVam/FI9NNafPQww39vCRsSAc7s1D5cJhqhoocssaYTeG547cphJV9oIfK\nmlUmhcFIDwJaRPni/I3Z0lmSr6RwUTzHhUQipPaqjHzw6i7U76QWZEwBAoGBAKwt\ntL4edOPoaMYgK7xywwOKDB6FxuntlKaJX/rB+ktvE3/2iITbHkftLottgUQA5/JP\nFwP6geNOmkK5rOYC3vIFzxpJVBEABDoHVb5u9cen9BmKpVVZ4BrXfrSsCMixbz2+\nzUuXCikqvH/LXmmmFw3fn/qTlqDcuMuDRd6gvQ8zAoGBAKfpRAN75xwdySNdJr+k\nAaCgR8JItTY1uslfMYaSkwAbHv09nA320cM9ZSnVeI5Sz5W47bQur8ZOp2J/C0sS\nuyh0bLiTYZCa/02r4EQ/4dGSsQdaUnBIQU+H1Zd9u9YZpR1o51LFnWiX7hSO/PMm\nnvWVg0LiH7besUHeZC9rbREs\n-----END PRIVATE KEY-----",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\n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\n-----END CERTIFICATE-----\n"
    }
}
```

</details>

Note that because the FVP 1.0 tests are built to be executed in Production the Certificates and Keys used in the example above differ from what is used in Production, and hence, no guarantee being approved on the Sandbox tests will grant a pass on the Automated Production Execution

## Process to Include Test Within the DCR Test Scope

This session aims to explain the steps required for a new test behaviour/test module to be included in the automated routine. Here, the main objective is to guarantee that the tested behaviour is both being tested correctly and that it's a well-understood behaviour.

### 1. Define the Scope of the Test

The scope and necessity of tests are first discussed in alignment with the Open Finance Initial Structure to have an overview of the behaviour. This discussion is held within both the Squad Sandbox and escalated to either the Specifications or Security WG if needed. Once the scope is well defined and accepted the next steps and agreed upon between the Initial Structure WGs and the Conformance Engineering Team.

### 2. Test Scope on Sandbox

Before moving the test into the production environment the Conformance Engineering team will either confirm that the tested behaviour was already tested on an existing test scenario or release the test on Sandbox for all institutions to execute within a defined time frame, which tends to be at least 3 months. Here the objective is to make sure that no test is done in Production without making sure that institutions have already passed on it on Sandbox.

### 3. Build and Homologate Test Module in Production

Once the specifications of the test are well established, and the behaviour has been tested on Sandbox, the test will then be created and executed on the Production Environment. Here a period of 2 to 4 weeks is expected to create the test and also around 2-4 weeks to homologate the test, verifying that all the steps of the tests are working well and the results are as expected.

In order to do that, 10 to 20 Authorization Servers are chosen in a way that the test can be put to the proof in different types of configurations, such as different authentication methods (private key authentication, tls authentication), and different scopes (payments, consents), for instance. The new test is manually executed against the selected servers, and the results are carefully analyzed. If there are any bugs or errors in the test, the process is repeated until we arrive at the ideal scenario of the test, when it can be released to production, and added to the automatic execution done against all institutions. In this process, no notification is done against the institutions unless a clarification is required.

Finally, prior to moving the test into Production, the Conformance Team will bring once again the final results against the selected institutions for the Work Groups to analyze so they can give the go-ahead for the test, taking into account the failure rate and also the returned responses for the tested institutions.

### 4. Moving the Test Fully into production

Once the test is confirmed to be working it will be moved into the Automated Routine so it is executed against all registered servers. Here, on the first weekly execution of the new test, once again a full review of the result is done for all institutions that fail, checking if the test behaviour and failure rate are within the expected levels. In case of results are not as expected, no institution is notified and the test goes through some adjustments before the next execution.

Once it is confirmed that the test executed well against all the registered institutions the notification on Service Desk will be carried on, and the test will be considered stable, with its execution being done in all the future weeks.

### 5. Review existing tests

Any Institution that does not agree with the tested behaviour is free to open a Service Desk ticket against the FVP, highlighting why they believe the tested behaviour is not in line with specifications. Here, the ticket will be first evaluated by the Conformance Team and, if justified by the specifications, the behaviour will be brought to discussion by the Work Groups who might decide to remove the tested behaviour and re-initiate the process on the "Define the Scope of the Test" of this session

## Common Issues

List of common problems that have been encountered on the automated DCR tests

### 40x on DCR Request - Client already present for this Software Statement on Server

Issue: The server is not accepting a new DCR because there is already a client_id that has been generated for this Software Statement.\
In this case, this client has also been created on a previous DCR test module, and, due to the server refusing to accept the registration DELETE request, likely due to an issue on the Server, the client was not correctly Deleted.

Solution: Evaluate the test plan and check if the issue with the DELETE Request happened on one of the existing test modules.

1. If positive, check what might have caused the issue and implement a correction. Manually delete the created client by using the SoftwareStatementID key provided on this document.
2. If negative, the DELETE issue has happened on a previous test executed against the institution and the issue can not be correctly traced using the provided evidence. Manually delete the created client by using the SoftwareStatementID key provided on this document and wait for the next execution to evaluate what might potentially have caused the issue on the DELETE

### Test was unable to call the Consents API on test

Issue: On the consents-bad-logged test the test was not able to call the POST Consents API because the Consent API URI was not supplied on the test plan. Solution: Review on the directory if the Authorisation Server has been registered with a valid Consents API for Phase 3 and/or Phase 2 - Depending on which phase the institution participates. Refer to the [Directory Operational Guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central) to see how to register the Consents API on the server

### DCR is not being accepted because of missing optional fields on the request

Issue: The server refuses the DCR because an [optional field](https://openid.net/specs/openid-connect-registration-1_0.html) was not sent on the request body Solution: On all the optional fields the server should [apply a server default](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2.md#applying-server-defaults) that it supports, making sure that the request will be processed by the institution

### Routine was unable to confirm within the well-known endpoint the supported token authentication methods

Potential Causes might include:

1. Well-Known used bad SSL certificates, not allowing its information to be accessed
2. Response_body does not include either private_key_jwt or tls_client_auth on the token_endpoint_auth_methods_supported object
3. Server denied access to the FVP when it tried to check the contents of the well-known endpoint

Solution:

1. Make sure the Well-Known endpoint is using either EV of valid CA or ICP-Brasil SSL certificate as mentioned on the [Certificate Standards Documentation](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-certificate-standards-1_ID1.md#endpoints-vs-certificate-type-and-mtls-requirements).
2. Make sure that the return is compliant with the [RFC8414](https://www.rfc-editor.org/rfc/rfc8414.html). Make sure that
3. Make sure that the JSON payload returned contains the expected token authentication methods

### Server claims the authorization token is invalid or expired

Issue: The server is not accepting valid access tokens. For some institutions, it has been identified a synchronization issue in a token cache between different instances of the authorization server. Solution: Implemented a fallback strategy for querying the token in the database when not found in the cache.

### Failure when calling the directory endpoints - Token or Assertion

Issue: The directory returned a 50x when calling one of its endpoints caused by the high usage of the platform during the testing. Solution: No change is required on the institution side, ignore the test results and wait for a new execution to happen.

### Server returned that the client presented invalid certificates

Issue: On all the DCR Requests the Tested server is returning that the issued client credentials are invalid leading to a failure on all tests Solution: The Server is not recognizing the issuing Certificate as valid. Make sure that the API Gateway trust the certificate and the CA that was used to issue this certificate

---

*Conteúdo baixado em 16/09/2026, 15:37:09*
