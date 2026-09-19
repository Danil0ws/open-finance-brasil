# TestDispatcher

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestDispatcher](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestDispatcher)
**Slug:** `UpStream-Design/TestDispatcher`

---

The **TestDispatcher** handles incoming HTTP requests indented for [`TestModule`](./TestModule) instances. All URLs managed by the **TestDispatcher** are under `/test`. 

A [`TestModule`](./TestModule) is reachable through the pattern `/test/random-test-id`, based on the random test ID assigned to the [`TestModule`](./TestModule) by the [`TestRunner`](./TestRunner).

If a [`TestModule`](./TestModule) has an `alias` associated with it, the test is also available under the pattern `/test/a/alias`. 

Once the **TestDispatcher** determines which [`TestModule`](./TestModule) to forward the request to, it strips off the first part of the path and hands the remaining portion to the [`TestModule`](./TestModule) instance's `handleHttp()` method. For example, if a [`TestModule`](./TestModule) has the ID of `1234abcd`, a request to `/test/1234abcd/foo/bar` would result in the path `/foo/bar` being passed to the [`TestModule`](./TestModule). Likewise, if a [`TestModule`](./TestModule) has the alias of `baz`, then requests `/test/a/baz/qux/batman` would result in the path `/qux/batman` being sent to the [`TestModule`](./TestModule). 

From this point, it is entirely up to the [`TestModule`](./TestModule) how to handle the incoming HTTP request. If the [`TestModule`](./TestModule) throws a `TestFailureException`, the **TestDispatcher** will return an HTML error page.

---

*Conteúdo baixado em 16/09/2026, 15:38:44*
