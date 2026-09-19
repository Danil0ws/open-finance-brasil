# TestRunner

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestRunner](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestRunner)
**Slug:** `UpStream-Design/TestRunner`

---

The **TestRunner** is the component that starts, stops, and manages running [`TestModule`](./TestModule)s. **TestRunner** functionality is accessible through an API:

 * `GET` to `/runner/available`: list of available [`TestModule`](./TestModule) names
 * `GET` to `/runner/running`: list of running test IDs
 * `POST` to `/runner`: create test. Takes the `testName` (which identifies a specific [`TestModule`](./TestModule)) and the `alias` as arguments, and the [`Configuration`](./Configuration) in the HTTP message body as a JSON object; instantiates the [`TestModule`](./TestModule) and calls `config()`
 * `GET` to `/runner/id`: get test status, results, and exposed strings
 * `POST` to `/runner/id`: start test (calls `start()` on the [`TestModule`](./TestModule))
 * `DELETE` to `/runner/id`: cancel test (calls `stop()` on the [`TestModule`](./TestModule))
 * `GET` to `/runner/browser/id`: get front-channel external URLs exposed to the [`BrowserControl`] for a given test
 * `POST` to `/runner/browser/id/visit`: mark front-channel external URL as visited, takes the `url` being visited as a parameter
 
The **TestRunner** creates a unique identifier for each [`TestModule`](./TestModule) instance during the configuration process. If an `alias` is provided, the **TestRunner** will associate the requested `alias` with the test ID. The `baseUrl` supplied to the test varies depending on whether an `alias` as provided: with an alias, the pattern is `/test/a/alias` but without an alias the pattern is `/test/random-test-id`. Calls to these URLs (and any URL underneath them) are handled by the [`TestDispatcher`](./TestDispatcher) module.

The **TestRunner** supplies each newly instantiated [`TestModule`](./TestModule) with a reference to the [`EventLog`](./EventLog) and the [`BrowserControl`](./BrowserControl) object. 

If a [`TestModule`](./TestModule) throws a `TestFailureException` while running the `start()`, `stop()`, or `config()` calls, the **TestRunner** will return an HTTP 500 response from the associated API call.

---

*Conteúdo baixado em 16/09/2026, 15:38:45*
