# Executing tests against an AS

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Executing-tests-against-an-AS](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Executing-tests-against-an-AS)
**Slug:** `Executing-tests-against-an-AS`

---

## Running test plans on the CS

The local version of the conformance suite is exactly the same as the one found on the [Open Finance Brasil server ](https://web.conformance.directory.openbankingbrasil.org.br/login.html) and as such can run all the tests that exist there.

When you run locally, the CS will also be already logged with the account DEVMODE@developer.com, which has full access to the U.I. menus.


## Display OIDF-FAPI test plans

The Conformance Suite comes pre-loaded with the OIDF-FAPI test plans that can also be executed locally. Although those tests do not appear on the test plan list, they can be easily surfaced for the local execution. 

To display the "OIDF-FAPI" test plans when running the conformance suite locally, the "Test an OpenID Provider / Authorization Server" should be added to the "fintechlabs.profiles.visible" in the "application.properties" file before the application is executed.

Profile: Test an OpenID Provider / Authorization Server

Property: fintechlabs.profiles.visible

File: src/main/resources/application.properties

An example of the adjustment:

 "fintechlabs.profiles.visible=Open Banking Brasil Functional Tests, Open Banking Brasil Functional Tests for Phase 1 - Open Data, Open Banking Brasil Functional Tests for Phase 2 - Customer Data, Open Banking Brasil Functional Tests for Phase 3 - Payment Initiation, Open Insurance Functional Tests, Open Banking Brasil Functional Tests for Phase 4, Development only functional tests, Test an OpenID Provider / Authorization Server"

The test plans below should now be visible in the list on U.I. allowing you to run them locally.

- FAPI1-Advanced-Final: Brazil Dynamic Client Registration Authorization server test
- FAPI1-Advanced-Final: Authorization server test

## Insert production credentials 

The conformance suite will use the pre-defined user configuration data to run the conformance tests, which includes the credentials for one or more clients registered on the participant directory. To authenticate and register against a production A.S. a valid set of credentials issued by ICP Brasil and registered into an S.S. in the directory will then be needed. Those credentials should be placed exactly the same way as the Sandbox-issued credentials were inserted on the hosted version of the conformance suite.

For Phase 3 the CS will also require the user to provide the Payments Consents and Payments Payload objects, so the user should make sure that he is inserting values that are for the correct environment being tested. 

## Update the redirect_uri

The Conformance Suite local execution will use a redirect_uri that can be defined prior to running the Conformance Suite. The standard URI if you just execute the test is of the format https://localhost.emobix.co.uk:8443/test/a/alias/callback, where the <alias> is the alias provided on the test configuration and the https://localhost.emobix.co.uk:8443 is the host that can be modified prior to the image execution.

The source of this URI is a global environment variable that is provided when executing running the Image on Docker and can be updated on **docker-compose-dev-mac.yml** or **docker-compose-dev.yml**, depending on what command is executed when running the CS. This will update the application.properties, that define the redirect_uri that is used by the application.

Down below is the example of where this is present on both the docker-compose-dev-mac.yml and the application properties, and the fintechlabs.base_url variable that can be updated

**docker-compose-dev-mac.yml:**

```
    command: >
      java
      -Xdebug -Xrunjdwp:transport=dt_socket,address=*:9999,server=y,suspend=n
      -jar /server/fapi-test-suite.jar
      --fintechlabs.base_url=https://localhost.emobix.co.uk:8443
      --fintechlabs.devmode=true
      --fintechlabs.startredir=true
```

**application.properties:**

```
# Make sure static clients match the redirect uri below
oidc.redirecturi=${fintechlabs.base_url}/openid_connect_login
```


## Register against the A.S. (DCR) and update the redirect_uri

Phase 2 and 3 tests require that the client_id used has already been registered with the redirect_uri, so it's important that prior to executing the tests the user performs either a DCR or a DCM against the tested A.S., with the redirect_uri before the functional tests are executed

In order for the DCR/DCM to be performed, it is also important that the redirect_uri used by the C.S. is also be registered on the S.S. directory as this element must be present inside the Software Statement Assertion when doing the registration.

For more details about executing the DCR check the [Registering against the Mock Bank wiki page](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-%28DCR%29)

---

*Conteúdo baixado em 16/09/2026, 15:37:28*
