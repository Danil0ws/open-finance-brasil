# TestModule

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestModule](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestModule)
**Slug:** `UpStream-Design/TestModule`

---

A **TestModule** is a component that strings together multiple [`Condition`](./Condition) executions in a single flow. **TestModule**s implement the `TestModule` interface, and an `AbstractTestModule` class is provided with a set of utility methods that facilitate **TestModule** development. This documentation assumes the use of this abstract class.

Active **TestModule**s have a unique identifer assigned to them by the [`TestRunner`](./TestRunner). Since multiple instances of the **TestModule** could be running in the system simultaneously, this ID is a random string that identifies this instance of the **TestModule**. This ID needs to be passed to all calls to the [`EventLog`](./EventLog) as well as any instantiations of [`Condition`](./Condition)s.

A **TestModule** instance is created by the [`TestRunner`](./TestRunner) in response to user action. The [`TestRunner`](./TestRunner) calls `configure()` on the **TestModule** and hands the module a [`Configuration`](./Configuration), an [`EventLog`](./EventLog), a unique test ID string, a hook for [`BrowserControl`](./BrowserControl), and the base URL of the test instance. The `configure()` function should handle all initialization of the **TestModule**, including any preliminary steps.

The `baseUrl` passed in during `configure()` should be used for all constructed URLs that reference this test from the outside. The **TestModule** can extend this URL with any number of path and query elements. The [`TestDispatcher`](./TestDispatcher) will automatically route any incoming requests to requests that start with this URL.

The [`TestRunner`](./TestRunner) then calls the `start()` function, which kicks off the test itself. The **TestModule** should create and call [`Condition`](./Condition)s in order to execute the desired test. The [`TestRunner`](./TestRunner) can call the `stop()` function at any time, which cancels the test.

A **TestModule** should store all stateful information related to its run inside its [`Environment`](./Environment). **TestModule**s should avoid using additional instance variables, as these are not available to any [`Condition`](./Condition)s during the test lifecycle.

A **TestModule** instance should make any calculated values available externally through the `expose()` function. This is useful for letting the test framework (including the user running the tests) see and use values which may include a random component, such as a redirect URI or state parameter.

A **TestModule** has a `state`, which indicates what part of the lifecycle it is in. The **TestModule** is responsible for setting its own `state` in response to events. The available values for `state` are:

* `CREATED`: the test has been created by the [`TestRunner`](./TestRunner), but no configuration has been added yet.
* `CONFIGURED`: the test has been given a [`Configuration`](./Configuration) by the [`TestRunner`](./TestRunner) and has been assigned a unique ID, and will automatically move into `RUNNING`.
* `RUNNING`: the test is currently executing
* `WAITING`: the test is paused and waiting for input from the external asset being tested, through the [`TestDispatcher`](testDispatcher)
* `FINISHED`: the test has run all test conditions, either successfully or not
* `UNKNOWN`: the test is in an undefined state, probably because of an error
* `INTERRUPTED`: the test has stopped running because of a fatal error. Not all Conditions were run.
* `no status`: the test module was abandoned during before or during redirection, meaning it could not reach a final status

The **TestModule** should set its state to `RUNNING` while executing conditions but set it to `WAITING` or `FINISHED` at the completion of a module, depending on what the test expects to happen next. (Moving the test to `RUNNING` takes a lock to ensure that the test module is not accessing the `Environment` from multiple threads at the same time, which would lead to unpredictable results. The lock is released when moving back to `WAITING`.)

A **TestModule** has a `result`, which indicates whether the overall test passed or failed once it's completed. The **TestModule** is generally responsible for setting its own `result` at completion, though the `callAndStopOnFailure()` function will by default automatically set the state to `FAILED` if it catches an error.

* `PASSED`: the test has passed all required [`Condition`](./Condition)s
* `WARNING`: the test has passed all required [`Condition`](./Condition)s but has failed some optional tests
* `FAILED`: the test has failed one or more required [`Condition`](./Condition)s
* `SKIPPED`: the test is not applicable or was skipped by the plan. Accepted in certification submissions when specified

The **TestModule** can run a [`Condition`](./Condition) by passing the class of the [`Condition`](./Condition) to either the `callAndStopOnFailure()` or `callAndContinueOnFailure()` functions. (There are also more variants of the 'call' function to cope with more esoteric requirements.)

ConditionResult.FAILURE should be specified as a parameter where the test relates to a MUST/SHALL/REQUIRED/etc, so that the test fails.

ConditionResult.WARNING should be specified as a parameter where the test relates to a SHOULD/RECOMMENDED/etc, so that the test is marked as 'WARNING'.

The 'requirements' parameter to the `call()` functions should always be set to the relevant spec clause(s) the `Condition` is testing, in the form DOCUMENTNAME-SECTION_NUMBER-BULLETNUMBER. eg. RFC1234-3.1-4 is the 4th bullet in section 3.1 of RFC 1234. (The 'specLinks' dictionary in src/main/resources/static/js/fapi.ui.js contains a mapping of DOCUMENTNAME to a url for the standard.)

The `ContinueOnFailure` variant should be used where the test can sensibly carry on running despite the failure, and should be used where possible as users find it useful if a test runs to completion in order that they have a complete list of all failures. For example, if the standard requires an 'expiry' claim in a request object, it will generally be fine to run other tests even if the request object is missing the expiry claim - the test must still FAIL though.

The `StopOnFailure` should be used where the test cannot sensibly run on. If there is any doubt, use 'StopOnFailure', it is the safe option. For example if a test wishes to check that an access token is correctly bound to a TLS client certificate, it must first verify that the access token works when used with the correct TLS client certificate - this test condition must use `stopOnFailure` - if the access token cannot be used with the correct TLS certificate, there is no meaningful way to check if the server allows it to be used with the wrong TLS certificate and the test must instead stop.

If the [`Condition`](./Condition) returns successfully, the test continues to the next step. If the [`Condition`](./Condition) fails (and throws a `ConditionError`), the `stopOnFailure()` functions will stop the **TestModule** by wrapping the error in a `TestFailureException` to be caught by the [`TestRunner`](./TestRunner) or [`TestDispatcher`](./TestDispatcher), while the `continueOnFailure()` functions will quietly log the failed [`Condition`](./Condition) and continue running the **TestModule**.

The **TestModule** can use [`Condition`](./Condition)s to call external services, and it can indicate that it needs a user to visit a URL in a web browser (thereby starting or finishing a front-channel transaction) by calling `goToUrl()` on its [`BrowserControl`](./BrowserControl) element. The **TestModule** should not attempt to emulate a browser call on its own. After exposing URL in this fashion, the **TestModule** should set its state to `WAITING` and return from its current function.

The **TestModule** receives inbound HTTP connections from the outside world through the [`TestDispatcher`](./TestDispatcher) which listens for incoming that map to this test, using its `baseUrl` as the root. The [`TestDispatcher`](./TestDispatcher) calls the **TestModule**'s `handleHttp()` method. The `path` argument will be truncated to remove the **TestModule**'s identifier path (or alias), allowing the **TestModule** to dispatch incoming calls to its own helper functions based on this path. It's recommended that the **TestModule** delegate processing to internal methods for each unique path. Methods should return a `ModelAndView` object for user-facing calls, and a `ResponseEntity` object for API-facing calls. Errors should be handled by throwing a `TestFailureException`, which will be caught by the [`TestDispatcher`](./TestDispatcher). If the dispatch method is annotated with `@UserFacing`, the [`TestDispatcher`](./TestDispatcher) will return an HTML error page, otherwise it will return an API style HTTP message.

---

*Conteúdo baixado em 16/09/2026, 15:38:44*
