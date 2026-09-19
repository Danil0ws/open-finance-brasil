# Structure

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Structure](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Structure)
**Slug:** `UpStream-Design/Structure`

---

# Backend

The backend is a java spring application.

It exposes a REST API that is used by the frontend, but can also be driven directly. (See [run-test-plan.py](https://gitlab.com/openid/conformance-suite/blob/master/scripts/run-test-plan.py) and [conformance.py](https://gitlab.com/openid/conformance-suite/blob/master/scripts/conformance.py) in the scripts directory of the git repository).

In order to allow usage of the API (other than by the JS frontend), users are able to create API tokens in the frontend of the suite. The test suite can also accept access tokens from an OAuth server supporting token introspection.

All configurations, test results, etc are stored in MongoDB.

The java backend structured into several components:

A [`Condition`](./Condition) is a single, small piece of functionality that is part of a test. Each condition should be as atomic as possible.

A [`TestModule`](./TestModule) strings together a set of conditions in a series, allowing reaction to calls from the external entities being tested. 

An [`Environment`](./Environment) is the state of a running test module. 

The [`TestRunner`](./TestRunner) creates, manages, and controls the test modules.

The [`TestDispatcher`](./TestDispatcher) intercepts incoming HTTP requests and routes them to the correct test instance. 

The [`EventLog`](./EventLog) collects messages of running tests.

The [`BrowserControl`](./BrowserControl) allows tests to indicate that URLs need to be visited by a browser.

# Frontend

The frontend is a pure javascript application that uses the public API exposed by the java backend.

Server-side generation of HTML should NOT be used. There are two special cases that use Thymeleaf; the spring custom error page and the submission page used to submit (to the conformance backend) any tokens that the authorization endpoint returns to the user's browser as neither could be accomplished without server side processing.



---

*Conteúdo baixado em 16/09/2026, 15:38:43*
