# Running specific tests locally against your own API responses

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Running-specific-tests-locally-against-your-own-API-responses](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Running-specific-tests-locally-against-your-own-API-responses)
**Slug:** `Running-specific-tests-locally-against-your-own-API-responses`

---

If you wish to validate your own API responses locally, without having to aim the conformance suite at a hosted API and the attendant security, it is possible to leverage JUnit tests to do this. All the validators which the conformance suite uses to validate the API responses have corresponding JUnit tests. You can find them in the package net.openid.conformance.apis in src/test/java.

These by default run against example JSON files which are bundled with the conformance suite source code, but it is now possible to override this and run them against JSON files which you provide, having obtained them from your own APIs by whatever means you wish. To run a specific JUnit test from the command line, use something like:

``` mvn test -Dtest=AccountListValidatorTest```

You may run only a specific method in the test class. Typically a unit test has a happy path test, and some failure testing. We are mostly interested in the happy path, which is generally in a method called validateStructure. So to validate the account list structure, you would use

```mvn test -Dtest=AccountListValidatorTest#validateStructure```

Now, to provide your own JSON file, you can pass the resource.override parameter, with a value of the absolute path to your file. For example

```mvn test -Dtest=AccountListValidatorTest#validateStructure -Dresource.override=/Users/george/sampleJson/accountList.json```

Now the test will be run against that file rather than the one in the source code.

---

*Conteúdo baixado em 16/09/2026, 15:38:32*
