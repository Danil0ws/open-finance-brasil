# Writing New Tests

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Writing-New-Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Writing-New-Tests)
**Slug:** `Writing-New-Tests`

---

# This is a short tutorial to demonstrate the very basics of adding a new test the conformance suite.

The constituent parts of a test in the suite are:

 * A test plan.
 * A collection of one or more test modules.
 * A collection of Conditions.

Let us examine them one by one.

## The Components

### Test Plan

This is, in essence, a Java class which implements the TestPlan marker interface. It will also be annotated with the @PublishTestPlan annotation, which carries with it some metadata about the test plan, as well as specifying the list of test modules involved in the plan. Thus, test modules are re-usable pieces of code which can be used by multiple plans.

If you have the conformance suite running locally, as specified [in this page](/Running-the-conformance-suite-locally), then browsing to the url https://localhost:8443/schedule-test.html will present you with a drop down box full of 'Test Plan' entries. Each of these entries corresponds to a TestPlan class.

### Test modules

These are Java classes which implement the TestModule interface, although in reality they will typically subclass something else which implements this. These classes represent an individual test within a particular plan. These are responsible for configuring all the actions and assertions which will constitute a particular test.

### Conditions

These are again Java classes, implementing the Condition interface, or more commonly extending something else which does. They are the building blocks of the functionality of tests. Although they are called conditions, they encapsulate functionality which performs actions such as interacting with the services under test, transforming data and carrying out verifications of responses. 

The aim is to keep each condition class as fine grained as possible, being responsible for a single activity only. Data is passed between condition objects via the Environment object. We will see more of this in the following demonstration.

## A Simple Example

Imagine a very simple API which exposes a single GET endpoint at /api/v1/hello, which returns a JSON object which looks like this

    { "message": "Hello" }

Let us write a simple test to validate this.

We start with a TestPlan

    @PublishTestPlan(
	testPlanName = "cunning-plan",
	profile = "Some simple examples which will not be committed", // A sub-heading in the test plan dropdown
	displayName = "A cunning plan",// This appears in the test plan dropdown
	summary = "More cunning than a fox who just got made professor of cunning at Oxford", // a short description
	testModules = {
		ApiCallTest.class // these classes implement specific sets of tests
	})
    public class CunningPlan implements TestPlan {
    }

The PublishTestPlan annotation contains some metadata which will be presented in the UI, describing the test. The testModules field is a list of the TestModule classes which do the work. Let's examine ours.

    @PublishTestModule(
	testName = "configurable-endpoint-test",
	displayName = "A simple configurable endpoint test",
	summary = "A test which hits a plain text, unprotected endpoint and carries out asserts on the response",
	profile = "PROFILE",
	configurationFields = {
		"resource.resourceUrl"
	}
)
@VariantParameters({
	ClientAuthType.class
})
public class ApiCallTest extends AbstractTestModule {

	@Override
	public void configure(JsonObject config, String baseUrl, String externalUrlOverride) {
		env.putObject("config", config);
		String url = OIDFJSON.getString(config.getAsJsonObject("resource").get("resourceUrl"));
		env.putString("resource_url", url);
		callAndContinueOnFailure(CallHttpResource.class);
		callAndStopOnFailure(ExtractSimpleMessage.class);
		setStatus(Status.CONFIGURED);
	}

	@Override

	public void start() {
		setStatus(Status.RUNNING);
		callAndStopOnFailure(SimpleMessageAssert.class, Condition.ConditionResult.FAILURE);
		setResult(Result.PASSED);
		setStatus(Status.FINISHED);
	}
}

Looking first at the PublishTestModule annotation. As well as some metadata for configuring how the test is displayed in the UI, there is a configurationFields field. These instruct the UI to offer a way for us to enter configuration details in the UI. In this case, it is a resource URL, which the test will consume. This will be passed into the configure method in the config object, where it can be read or manipulated. In this instance, we take the URL and add it directly to the environment using the key "resource_url". Although this is not strictly necessary - we can just add the entire config object - adding it explicitly gives us some additional behaviours we will see when we examine conditions.

Next we see some method calls in which we pass classes which are our actual conditions. Note that the framework uses reflection to create these, we do not do this ourselves. Thus, the use of the Environment object is necessary. This is essentially a context object for the test run, and contains the config options, and is also where we can put data for further processing. In this example we have used three condition classes: CallHttpResource, ExtractSimpleMessage and SimpleMessageAssert. Each of these is very finely grained, doing exactly one thing each. This architecture allows us to configure tests out of small collections of objects rather than having to write long-winded individual tests over and over again. 

The entrypoint into a condition is the evaluate method. Here is a trimmed version of that method for the CallHttpRequest class.

    @PreEnvironment(strings = "resource_url")
    @PostEnvironment(required = "resource_endpoint_response")
    public Environment evaluate(Environment env) {
		String uri = getUri(env);

		RestTemplate restTemplate = createRestTemplate(env);

		HttpMethod method = getMethod(env);
		HttpHeaders headers = getHeaders(env);

		HttpEntity<?> request = new HttpEntity<>(getBody(env), headers);

		ResponseEntity<String> response = restTemplate.exchange(uri, method, request, String.class);
		JsonObject responseCode = new JsonObject();
		responseCode.addProperty("code", response.getStatusCodeValue());
		String responseBody = response.getBody();
		JsonObject responseHeaders = mapToJsonObject(response.getHeaders(), true);
            JsonObject jsonBody = jsonParser.parse(responseBody));
		env.putObject("resource_endpoint_response_code", responseCode);
	        env.putObject("resource_endpoint_response", jsonBody);
            env.putObject("resource_endpoint_response_headers", responseHeaders);
		return environment;
		
	}

The first thing to note is the pair of annotations on the method. PreEnvironment and PostEnvironment. These allow us to configure pre- and post conditions for our tests. In this instance, we are telling the framework that this class requires a string with the key 'resource_url' to be present in the environment object. If it is not, then the test fails prior to invoking this class. Similarly, the PostEnvironment annotation expects that upon completion there should be an object with the key 'resource_endpoint_response' in the environment. If not, the test will fail at this point. 

So this test is very simple. It uses a RestTemplate - essentially an HTTP client - to call a URI.   Then it adds the response code, headers and entity to the environment before returning. We do not do any validation of the response, other than to parse it to JSON, which will of course fail if it is not valid JSON. It is the responsibility of other conditions to process and validate the actual response.

The next class is the ExtractSimpleMessage class, which is even simpler

    public class ExtractSimpleMessage extends AbstractCondition {

	    @Override
	    @PreEnvironment(required = "resource_endpoint_response")
	    @PostEnvironment(strings = "message")
	    public Environment evaluate(Environment env) {
		JsonObject response = env.getObject("resource_endpoint_response");
		String message = OIDFJSON.getString(response.get("message"));
		env.putString("message", message);
		logSuccess("Message extracted");
		return env;
            }
 
        }

Again, we see that PreEnvironment and PostEnvironment are specifying what this class expects to be given, and what it should be passing on upon completion. In this instance, it is pulling a field called 'message' out of the response body from the last condition. In this contrived example we simply assume it is present. In a more complete test, the existence of it would be validated too.

Finally the actual asserting part of this test is the SimpleMessageAssert class.

    public class SimpleMessageAssert extends AbstractCondition {

	@Override
	@PreEnvironment(strings = "message")
	public Environment evaluate(Environment env) {
		String message = env.getString("message");
		if(!message.equals("Hello")) {
			logFailure("Message not correct");
			throw error("Message was not 'Hello'");
		}
		logSuccess("Message was correct!");
		return env;
	}

}

This is self explanatory. It requires that "message" exists when it starts, and then checks whether or not it says "Hello". If not, it throws an error, which fails the test.

These basic building blocks are what we will use to build our conformance test suite.

Please note that these test classes currently exist in the codebase, as well as an implementation of the "hello" endpoint, at /api/v1/hello.

---

*Conteúdo baixado em 16/09/2026, 15:38:46*
