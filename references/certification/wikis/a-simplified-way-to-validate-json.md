# A Simplified Way To Validate Json

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/A-Simplified-Way-To-Validate-Json](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/A-Simplified-Way-To-Validate-Json)
**Slug:** `A-Simplified-Way-To-Validate-Json`

---

In the [previous example](/Writing-New-Tests) we wrote three Condition classes to carry out the work of calling an API and ensuring a particular message was present. This was a verbose example to illustrate the pattern of having single-use, fine grained classes. There is actually a simpler way. The framework contains a number of abstract classes which can be extended, providing useful functionality. In this example we will collapse the ExtractSimpleMessage and SimpleMessageAssert classes into one, which utilises one of these classes. The abstract class in question is called AbstractJsonAssertingCondition, and provides a number of methods for performing Jsonpath queries on an object. Here is our new class:

    public class ValidateHelloMessage extends AbstractJsonAssertingCondition {

	@Override
	@PreEnvironment(required = "resource_endpoint_response")
	public Environment evaluate(Environment environment) {
		JsonObject response = environment.getObject("resource_endpoint_response");
		assertJsonField(response, "$.message", "Hello");
		logSuccess("Message was indeed 'Hello'");
		return environment;
	}

}

This is much simpler. We require that the resource_endpoint_response object is present in the environment before proceeding, and simply use the assertJsonField method to perform the assertion. Should that jsonpath query fail, the test will be failed with an appropriate message.

The assertJsonField method is overloaded with type safety. If you expect the value being examined to be an integer, pass in an integer and that type safety will also be asserted for you. For more on Jsonpath see [here](https://github.com/json-path/JsonPath).

---

*Conteúdo baixado em 16/09/2026, 15:37:07*
