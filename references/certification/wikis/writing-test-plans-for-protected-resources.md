# Writing Test Plans for Protected Resources

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Writing-Test-Plans-for-Protected-Resources](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Writing-Test-Plans-for-Protected-Resources)
**Slug:** `Writing-Test-Plans-for-Protected-Resources`

---

The functional test suite is required to run against web resources which are protected by a FAPI security profile. Whilst this sounds complicated, most of the heavy lifting is done by helper classes. 

The base class net.openid.conformance.AbstractFunctionalTest will be fully configured from the test UI and will carry out all the steps to obtain an access token for making the resource call. It will then make the call to the configured resource, and pass the response entity, headers and status into the environment object. Any actual validation conditions shall be configured in the validateResponse method of this class. 

It is recommended that these conditions make use of the class net.openid.conformance.condition.client.AbstractJsonAssertingCondition as this provides helper methods for obtaining the response and running JsonPath asserts against it. There is a contrived but working example of this in the codebase. 

If we examine the class net.openid.conformance.raidiam.RaidiamOrgApiTest:
```
    package net.openid.conformance.raidiam;

    import net.openid.conformance.AbstractFunctionalTestModule;
    import net.openid.conformance.testmodule.PublishTestModule;

    @PublishTestModule(
	testName = "organisation-api-test",
	displayName = "Raidiam Directory Org API test",
	summary = "Calls the org api using a FAPI security profile",
	profile = "Raidiam",
	configurationFields = {
		"server.discoveryUrl",
		"client.client_id",
		"client.scope",
		"client.jwks",
		"mtls.key",
		"mtls.cert",
		"mtls.ca",
		"resource.resourceUrl"
	}
    )
    public class RaidiamOrgApiTest extends AbstractFunctionalTestModule {

	@Override
	protected void validateResponse() {
		callAndStopOnFailure(OrgApiValidator.class);
	}

    }
```
We can see that this is very simple. The configuration is described in the PublishTestModule annotation. Here, we and describe the test, and request some fields for the UI to configure. We then extend the base class mentioned above, and implement the validateResponse method. In this test, we are carrying out a single validation, which we will look at next.

```
package net.openid.conformance.raidiam;

import com.google.gson.JsonObject;
import net.openid.conformance.condition.PreEnvironment;
import net.openid.conformance.condition.client.AbstractJsonAssertingCondition;
import net.openid.conformance.testmodule.Environment;

public class OrgApiValidator extends AbstractJsonAssertingCondition {

	@Override
	@PreEnvironment(strings = "resource_endpoint_response")
	public Environment evaluate(Environment environment) {
		JsonObject response = bodyFrom(environment);

		assertJsonField(response, "$.OrgDetails.OrganisationId", "e1ebedfc-7600-46af-a30a-180a1e6f49c1");
		assertJsonField(response, "$.OrgDetails.Status", "Active");
		assertJsonField(response, "$.OrgDetails.OrganisationName", "CECME DO GRUPO PAO ACUCAR/BSB");
		assertJsonField(response, "$.OrgDetails.CreatedOn", "2020-12-30T13:43:08.900Z");
		assertJsonField(response, "$.OrgDetails.LegalEntityName", "COOPERATIVA DE ECONOMIA E CRÃDITO MÃTUO DOS EMPREGADOS DO GRUPO PAO DE ACUCAR - BRASILIA - LTDA.");
		assertJsonField(response, "$.OrgDetails.CountryOfRegistration", "BR");
		assertJsonField(response, "$.OrgDetails.CompanyRegister", "Cadastro Nacional da Pessoa JurÃ­dica");
		assertJsonField(response, "$.OrgDetails.RegistrationNumber", "00543108");
		assertJsonField(response, "$.OrgDetails.RegistrationId", "00543108");
		assertJsonField(response, "$.OrgDetails.RegisteredName", "COOPERATIVA DE ECONOMIA E CRÃDITO MÃTUO DOS EMPREGADOS DO GRUPO PAO DE ACUCAR - BRASILIA - LTDA.");
		assertJsonField(response, "$.OrgDetails.AddressLine1", "ADDRESS TBC");
		assertJsonField(response, "$.OrgDetails.AddressLine2", "ADDRESS TBC");
		assertJsonField(response, "$.OrgDetails.City", "BrasÃ­lia");
		assertJsonField(response, "$.OrgDetails.Postcode", "ADDRESS TBC");
		assertJsonField(response, "$.OrgDetails.Country", "BR");
		assertJsonField(response, "$.OrgDetails.RequiresParticipantTermsAndConditionsSigning", true);

		logSuccess("Org response looks good");
		return environment;
	}

}
```

Again this is very simple. We extend the base class, and can then simply request the HTTP response entity as a JsonObject, and run queries against it using JsonPath.

Finally we tie the whole thing together using a TestPlan instance:

```
package net.openid.conformance.raidiam;

import net.openid.conformance.plan.PublishTestPlan;
import net.openid.conformance.plan.TestPlan;

@PublishTestPlan(
	testPlanName = "Raidiam Services",
	profile = "Raidiam Directory Tests",
	displayName = "Test simple access to a resource",
	summary = "Calls resources on the directory, largely to prove the FAPI security profile",
	testModules = {
		RaidiamOrgApiTest.class
	})
public class RaidiamDirectoryTestPlan implements TestPlan {
}
```

These three classes utilise existing framework code to do all our tedious configuration and work. We are left free to focus on the tests themselves.

---

*Conteúdo baixado em 16/09/2026, 15:38:47*
