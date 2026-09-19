# Manual Production Tests

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Manual-Production-Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Manual-Production-Tests)
**Slug:** `Manual-Production-Tests`

---

# Objective

The [Manual FVP](https://web.fvp.directory.openbankingbrasil.org.br/) is an implementation of the [Open Finance Sandbox Conformance Suite](https://web.conformance.directory.openbankingbrasil.org.br/) with a set of modifications in order to allow it to safely execute tests against the Open Finance participant's Production Environment, consuming PII data on the process.

The objective of the FVP is to serve as a tool to confirm that the Production Implementation of the Open Finance Participants is aligned with the defined [Open Finance Standards](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17367659/Especifica+es+de+APIs) as well as the [Open Finance Brazil DCR Standards](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID3.md) and [Open Finance Brazil FAPI Standards](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-financial-api-1_ID3.md).

The tests implemented on the platform will require that the user authorize it's consent and will check if the tested API functional flows and the API responses are compatible with the Defined Standards, for example, it will confirm that the national user id is returned as a “text” and not as a number. The PII obtained on the tests won’t be used for any other reasons other than to confirm if the institution is or is not aligned with the specifications.

The Manual FVP contains two sets of test plans:

- [Open Test Plans](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP---Open-Production-Tests) - Executed by any user registered as PFVPC in the directory
- [Restricted Test Plans](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Restricted-Test-Plans) - Restricted to specific users hired by the Initial Structure to be executing the production tests on behalf of the institutions

To know more about how to access and execute tests on each Manual FVP above please go to subsections of this page.

# Release Dates

- 23/03/23 - Launched [Manual FVP Open Production Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Open-Production-Tests)
- 22/01/24 - Launched [Manual FVP Restricted Production Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Restricted-Test-Plans)

# User Guide

This section aims to explain how a user should be able to execute tests against their production servers using the [FVP Hosted Application](https://web.fvp.directory.openbankingbrasil.org.br)

## Creating a Production Directory Account

To Access the Platform, the first requirement is to have an account set on the [Directory Production Environment](https://web.directory.openbankingbrasil.org.br/organisations). On the steps on how to create an account on the Environment, one can refer to the [Participant Directory Operational Guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central) on Chapter 03 - "_Registrando um usúario no Diretório_"

The process for creating an account has multiple steps, which include signing a Document agreeing with the Platforms Terms and Conditions as well as Setting a TOTP for future access, like the [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en-us). If you find any issues in setting an account that could not be clarified with the user guide, please open a support ticket on the [Service Desk](https://servicedesk.openbankingbrasil.org.br/).

## Directory Access Scope

Once the User confirms he has full access to the Participant Directory, in order to access the [FVP Application](https://web.fvp.directory.openbankingbrasil.org.br) he will be required to be assigned the "PFVPC" role on the [Directory Production Environment](https://web.directory.openbankingbrasil.org.br/organisations) for the organisation that he is going to be testing.

The User that will access the FVP will be the same user that will need to authorize the Consent for the Open Finance APIs to be called, so it's required that the CPF registered for this user on the directory be also a controller of the Products that are going to be tested on the FVP.

Here, if the institution is going to test the "Authorisation Server A" it will be required to assign the "PFVPC" role to the user that is testing exactly on the organisation that controls the "Authorisation Server A"

To assign the "PFVPC" role to a user the organisation Admin will have to follow the following steps:

1. Enter the Organisation that has the server that will be tested
2. Select on the left side menu the item "AUTHORITY DOMAIN ROLE CLAIMS"
3. Click on any of the ROLES that have been assigned for this organisation (DADOS, PAGTO or CONTA)
4. Select on the sub-menu, also on the left side, the item "AUTHORISATION DOMAIN USERS"
5. Click on the button "NEW AUTHORISATION DOMAIN USER" on the right side of the screen
6. Once a box appears, select on the session "Authorisation Domain Users Information" the System as "Production Validation Tool" and the Contact as "PFVPC". On the e-mail set the e-mail of the user that will access the Platform for testing

If a user without the "PFVPC" Role tries to log in to the platform they will receive a 403 - FORBIDDEN message on his screen

## Accessing the Platform

To access the [FVP platform](https://web.fvp.directory.openbankingbrasil.org.br) the PFVPC will be required to perform an SSO flow with the Directory where it will share its Directory Information with the platform so it knows which servers it can execute tests and for which CPF it can test.

Once authenticated, the user will also have to accept the FVP terms and conditions, which explain the purpose and the objectives of the Platform. The user will be required to accept the terms and conditions every time that he wishes to log in to the platform.

## Selecting The Server and CPF/CNPJ that will be tested

After accepting the terms and conditions, the user will now be access the interface similar to the Regular Conformance Suite, where he will now be able to click on the button "Create a new Test Plan".

From there a page will appear, where he will select which test plan he will execute, defined on the session "Test Scope" of this document, as well as what types of authentication will be used to authenticate the testing user on his server - The types of authentication that the server accepts should be reflected within the Sever Metadata/Well-Known endpoint.

**PF TESTING**

After selecting the information above, only three pieces of information need to be included by the user to execute the tests, the alias, his CPF, and the Authorisation Server Well-Known, which must be equal to one of the well-known registered within the directory for the organisation that he is a PFVPC for. The alias must correspond to the orgId where the Authorisation Server is registered, and in case it is left in blank, it will correspond to the first org that has this well-known published.

![image](uploads/7c11981567aba1dc247535fac2430426/image.png)

In case the CPF or the Provided Well-Known is not a match with what the PFVPC has an error message similar to the one below will be provided, informing that he won't be able to run the existing test

![image](uploads/7360d507a5adc781a94356ea19abbf1e/image.png)

**PJ TESTING**

In case the institution is testing PJ, the CNPJ will also be required in the test plan configuration, in addition to the alias, the well-known and the CPF. Note that **the CPF must correspond to someone with authorization access to the CNPJ included**.

![image](uploads/e66336495843eca0db33d0486a242b5d/image.png)

## Running the test modules

After confirming the CPF and the provided Well-Known the platform will also define a redirect_uri that will be used on all the tests that will be executed. This redirect_uri will contain the unique organisation id for which the user is a PFVPC. If your organisation hasn't still been accepted as an organisation on the FVP then the created redirect_uri won't be accepted by the test client and a failure on the DCR, explained in the session below "Pre-Test Setup - DCR", will occur.

[The full list of organizations that have been authorised to run a test on the FVP can be seen here](https://gitlab.com/obb1/certification/-/wikis/FVP-Authorized-Orgs)

From the test execution screen the user will now be able to click on "Run Test" where a Pre-Test Setup will be executed. Details of this pre-test setup are defined below. Additionally, each of the existing test module summaries can be seen both within the FVP as well as in the session "Test Scope" of this document and their behaviour is similar to the behaviour of a regular [Conformance Suite Test](https://web.conformance.directory.openbankingbrasil.org.br/) that is executed for the Sandbox certification.

![image](uploads/13efbefa8f801872ff995c0c273d8419/image.png)

## Pre-Test Setup - DCR

After clicking on starting, all the tests will execute a DCR, as defined on the [Open Finance Brazil DCR Standards](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID3.md), against the target server to obtain a client_id that will be used only on the scope of the test module that is going to be executed. All test modules use the same client to execute the tests and if there's any issue with accepting the DCR the test will not continue and an error message will appear.

The test client that is used and the Software Statement are the same as the one defined on the [Automated FVP Tests](https://gitlab.com/obb1/certification/-/wikis/Automated-Production-Tests) and any issues on accepting a DCR from the Automated tests will very likely mean a failure on accepting a DCR for the tests defined on this page.

Once a test plan is finished the client_id generated for the scope of the test will also be excluded, implying that no clients will be persisted once a test module is completed.

Down below are the details of the Software Statement used on the scope of the test

- Organisation: Open Finance Brasil - FVP - Iniciador - 1dbfe32a-5f1e-4841-a30c-9f1b5f24ad36
- Software Statement: Ferramenta de Validação em Produção - bcc3ba64-faf5-456c-a162-8fef7ee67170

<!--THIS HAS BEEN REMOVED DUE TO INITIAL STRUCTURE REQUEST

<details><summary>Used Transport Certificate</summary>

issuer: AC SOLUTI SSL EV G4

alias: obb-brcac-soluti-v4

```
-----BEGIN CERTIFICATE-----
MIIHczCCBVugAwIBAgIKEd4kAhZtAYZLtjANBgkqhkiG9w0BAQ0FADB3MQswCQYD
VQQGEwJCUjETMBEGA1UEChMKSUNQLUJyYXNpbDE1MDMGA1UECxMsQXV0b3JpZGFk
ZSBDZXJ0aWZpY2Fkb3JhIFJhaXogQnJhc2lsZWlyYSB2MTAxHDAaBgNVBAMTE0FD
IFNPTFVUSSBTU0wgRVYgRzQwHhcNMjQwMjIyMTYxMjAwWhcNMjUwMjIxMTYxMjAw
WjCCAU0xHTAbBgNVBA8MFFByaXZhdGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGC
NzwCAQMTAkJSMRcwFQYDVQQFEw40NDQ3MTE3MjAwMDExOTELMAkGA1UEBhMCQlIx
MDAuBgNVBAoMJ0lOSUNJQURPUiBJTlNUSVRVSUNBTyBERSBQQUdBTUVOVE8gTFRE
QTELMAkGA1UECAwCU1AxEjAQBgNVBAcMCVNhbyBQYXVsbzEzMDEGA1UEYQwqT0ZC
QlItMWRiZmUzMmEtNWYxZS00ODQxLWEzMGMtOWYxYjVmMjRhZDM2MTQwMgYKCZIm
iZPyLGQBAQwkYmNjM2JhNjQtZmFmNS00NTZjLWExNjItOGZlZjdlZTY3MTcwMTMw
MQYDVQQDDCp3ZWIuZnZwLmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu
YnIwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCqqJLjJ4bTajoRtO5J
5fr+ZJe08DgVfRnTo0561dCgLr/Oi3fKv41ycjWx4wKLXs7LFUXmoE06f6D2r4M3
giJJI95UO5DDbSizIX2TdSrBCxGHdjdvQGJsXh/qPs7CThdEQX9JfsBZh3kL+xT2
5Bv3kXUhxIAz5DewSZHSOqn8fZ4pp8c+m/FqeST4fRnKPYtgO3V1Pyh61AkCw1Kd
0gxjz2WIK+gpCTeKQGFj21leX1TrQCS51UZhwOVHY9eUjQ8Cpig0XcZhB48YrXWZ
avylAl8FSFjOU/pxLQcnzVqMF54GeH6Q9xK3C4QhawCKmnkcf40x4Xs1QEui6NVV
jq4LAgMBAAGjggInMIICIzAJBgNVHRMEAjAAMB8GA1UdIwQYMBaAFP4GuSyVfi/m
0Lio8S+38i6F1dfAMIGABggrBgEFBQcBAQR0MHIwRgYIKwYBBQUHMAKGOmh0dHA6
Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktc3NsLWV2LXYxMC1n
NC5jcnQwKAYIKwYBBQUHMAGGHGh0dHA6Ly9vY3NwMy5hY3NvbHV0aS5jb20uYnIw
NQYDVR0RBC4wLIIqd2ViLmZ2cC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwu
b3JnLmJyMGQGA1UdIARdMFswBwYFZ4EMAQEwUAYGYEwBAgFwMEYwRAYIKwYBBQUH
AgEWOGh0dHA6Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2RvY3MvZHBjLWFjLXNvbHV0
aS1zc2wtZXYucGRmMBMGA1UdJQQMMAoGCCsGAQUFBwMCMIGQBgNVHR8EgYgwgYUw
QKA+oDyGOmh0dHA6Ly9jY2QuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGkt
c3NsLWV2LXYxMC1nNC5jcmwwQaA/oD2GO2h0dHA6Ly9jY2QyLmFjc29sdXRpLmNv
bS5ici9sY3IvYWMtc29sdXRpLXNzbC1ldi12MTAtZzQuY3JsMB0GA1UdDgQWBBQU
xVtSg6V4D3ppsKvqXOODzJu5YTAOBgNVHQ8BAf8EBAMCBaAwDQYJKoZIhvcNAQEN
BQADggIBAB+SxnR1sHSOSw6FpVjtllI5Dil7CmdI7ywXl2qmePcXBZ/atckgGEEq
+2d+MMa7U+fYkWgdPVRSC19P8l/rrFZVLBMKVBJFbltkFY0oONIDH9CNsSkTTEFL
OLhrLKPVXJUoy6VRNE6UV+ZEAFf7jNy5oo4dTfKXUW4nuAV1+SfL/rdHmxUr1ZOs
Y9hb2c5jTnJ22o3pXE6s8v0lfTp0l72qbA7+VS4un54PvoN6u373tqbKceIShMp+
2CwtxibwCU0Af2xnO1OhizswhLCINlruSj/ovM2uBhIi7n4QoyFLg3XtVjcWnZPC
5uP2VouKOsLJHN8W0w+f2JqzIUIyPjXbQeDVCq6SwIk7Wh7kgvq/HdgIYnbUdPmS
+k2sxBn301aJR2Z9OkZKoxxChWn63zjr6YtJ2NAONsKx4VBkQoBsJL4/gkRIgdKj
BThVrKTThCoFRYIYlFpyPqPfTRYotaB5+sF9EEld2xYvMUpVJFPBMOGVm0ieT+Z+
KUqcoDegVEiYvfABni3Bgwi+qoBLMS70fdP/n+/XWEMqOkdvQgupzEpA7Qq80zxh
kWO2lcAGS2M9Topw9D4P+RScVw0M8Sw8arnlwgtDRJhe07dNiiBGtXQiNq25IZA/
og1BKkCLfuvG6dLkkRlYJFSP05md9UX9H+RXy71KdFerP0t3rCmQ
-----END CERTIFICATE-----
```
</details>

<details><summary>Used Signing Certificate</summary>

issuer: AC SOLUTI Multipla v5

alias: obb-brseal-soluti-v3

```
-----BEGIN CERTIFICATE-----
MIIHiDCCBXCgAwIBAgIIEd4kAiZlw9gwDQYJKoZIhvcNAQELBQAwWTELMAkGA1UE
BhMCQlIxEzARBgNVBAoTCklDUC1CcmFzaWwxFTATBgNVBAsTDEFDIFNPTFVUSSB2
NTEeMBwGA1UEAxMVQUMgU09MVVRJIE11bHRpcGxhIHY1MB4XDTI0MDIyNjIwMTUw
MFoXDTI1MDIyNTIwMTUwMFowggEbMQswCQYDVQQGEwJCUjETMBEGA1UEChMKSUNQ
LUJyYXNpbDELMAkGA1UECBMCU1AxEjAQBgNVBAcTCVNhbyBQYXVsbzEaMBgGA1UE
CxMRQ2VydGlmaWNhZG8gUEogQTExGTAXBgNVBAsTEFZpZGVvY29uZmVyZW5jaWEx
FzAVBgNVBAsTDjA5NDYxNjQ3MDAwMTk1MR4wHAYDVQQLExVBQyBTT0xVVEkgTXVs
dGlwbGEgdjUxMDAuBgNVBAMTJ0lOSUNJQURPUiBJTlNUSVRVSUNBTyBERSBQQUdB
TUVOVE8gTFREQTE0MDIGCgmSJomT8ixkAQETJDFkYmZlMzJhLTVmMWUtNDg0MS1h
MzBjLTlmMWI1ZjI0YWQzNjCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEB
ALfHwMiKJeHfFmzb7nS4t5Yh+icvz47FuEhYb4gOJCK6X30/+r/BVn2/bWIWoYVf
5ubTcZGWch3K/3QRXxBx4HOmxk9d+VNd2u5/08wQg6IbMqu+uX6bcZfKuVxhIJw/
kY3NbpHi0gDRoLRVaS8QvQJ6Z8t1AshgyvK/REbjdPIAG1Rua+9BWWaUJfcDnHSA
pO7Xa/TwdbVQDcrr6ptYkhHKTxfoqqMLWL4kI2rWaKamxWlYGkUPGdS0570NWzu4
dVkb3GmLIPYoHA6N33y3NrCgVoG4ekQN3+xw7h+3KvyBKSEF1rV2kRafhJcd4sxE
rfbIXEB6QnAIJC+Y8yS4xZUCAwEAAaOCAo4wggKKMAkGA1UdEwQCMAAwHwYDVR0j
BBgwFoAUxVLtJYAJ35yCyJ9Hxt20XzHdubEwVAYIKwYBBQUHAQEESDBGMEQGCCsG
AQUFBzAChjhodHRwOi8vY2NkLmFjc29sdXRpLmNvbS5ici9sY3IvYWMtc29sdXRp
LW11bHRpcGxhLXY1LnA3YjCByQYDVR0RBIHBMIG+gRhtYXJjZWxvQGluaWNpYWRv
ci5jb20uYnKgNAYFYEwBAwKgKxMpTUFSQ0VMTyBDT1NUQSBWQVNDT05DRUxMT1Mg
TUFSVElOUyBKVU5JT1KgGQYFYEwBAwOgEBMONDQ0NzExNzIwMDAxMTmgOAYFYEwB
AwSgLxMtMjEwODE5OTE0MTg1NzU1NTg5OTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAw
MDAwoBcGBWBMAQMHoA4TDDAwMDAwMDAwMDAwMDBdBgNVHSAEVjBUMFIGBmBMAQIB
JjBIMEYGCCsGAQUFBwIBFjpodHRwOi8vY2NkLmFjc29sdXRpLmNvbS5ici9kb2Nz
L2RwYy1hYy1zb2x1dGktbXVsdGlwbGEucGRmMB0GA1UdJQQWMBQGCCsGAQUFBwMC
BggrBgEFBQcDBDCBjAYDVR0fBIGEMIGBMD6gPKA6hjhodHRwOi8vY2NkLmFjc29s
dXRpLmNvbS5ici9sY3IvYWMtc29sdXRpLW11bHRpcGxhLXY1LmNybDA/oD2gO4Y5
aHR0cDovL2NjZDIuYWNzb2x1dGkuY29tLmJyL2xjci9hYy1zb2x1dGktbXVsdGlw
bGEtdjUuY3JsMB0GA1UdDgQWBBS5jeSwIzHSkOXPOWNZZg6tUuzqxjAOBgNVHQ8B
Af8EBAMCBeAwDQYJKoZIhvcNAQELBQADggIBADnZob5NWuDkaZz5jw9Gp03bqoNn
0RqtaJEPtmdDFq/JArD49Z003NFk36VNnXzwQX5nR6OnQUbaDfJ6owLYl1eEdXjp
5ut7WFGQgFR0klAeBulK2TkuuTnicT9Uy8bKkfPJcIY6oPEzeB4oqbCS1uVMOcXh
6g2L0yH5z9GBUpziI+uHSkOBXExzglV8FZP1K5c3o/TsAe9lslsyJw7OzFp367ZG
OzQGeEb6Um6yL5GKO34Y9D2uzxiyomZnCpeMfC7aTLHiQS1+6lCluHHeKG9bIQDK
LM5BZFlTls34vUe4tyOcyX93Ci82QMZdNMuMjV1xbdqRR9Vy69ZM8vxLsLziWGgm
0gV0MXVf6RJZWpPcwZYk8IkPdPs4Aw0MhcpgGtiWgBVp/HEt8T0K45rHSTl4kPea
90aZurkYdXH0BYbVELrlS6jWy9yiaqxGhh4dLI5+aA5FMo7aXVlon2BFTpVswwUn
iWvVfPHwfdE4zmvr/1TBtvbebyoEzvJDUPnlkPcdwiTwKlkG5qVL2c8W1Dy9/k+U
6Bg8MR5MvdzmRSAiREqZVZBl9WvRw5r+YS4qe9v6SVc7aTZuqP8bOqz8FwfQTlml
uhxdjEHOhUVokRcL67XfTKzkVDTTu5gH0lP3cnMROJjrFx/VoVlbOjUqmPf6YSjz
CtC0SgNgGFNMDlRE
-----END CERTIFICATE-----
```
</details>-->

## Checking the Results and Data Persistence

Once the test is finished the logs will be kept available for the institution to download, if they wish to do so, for a 5-minute period of time after the test modules have reached a final state, be it a FAILED or a PASSED. The Initial Structure will be capable of seeing the final test result of the test and there is no requirement for any information to be sent once a test is executed.

All Data generated from the interaction between the Tested Server and the FVP will be persisted for only five minutes once a test plan arrives on an end state, being erased permanently after this time. Additionally, while stored on our servers, all the data will be encrypted meaning that only the user that has initially shared the data will be able to access this data while it remains on our servers.

The only data that will be persisted after a test execution has been done will be the test metadata, meaning, which institution executed the tests and what is the final state of each executed test module.

# Test Plan List

The following test plans are part of the FVP

[fvp_Manual-tests_available.xlsx](uploads/289cfa8d3b5edcd22dd34fbe4d121677/fvp_Manual-tests_available.xlsx)

---

*Conteúdo baixado em 16/09/2026, 15:38:10*
