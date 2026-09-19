# BrowserControl

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/BrowserControl](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/BrowserControl)
**Slug:** `UpStream-Design/BrowserControl`

---

The **BrowserControl** object allows a [`TestModule`](./TestModule) to indicate that it needs someone to visit a URL with a browser and interact with an external service. For instance, this is used to start a front-channel message process and deal with interactive portions of protocols, such as the authorization endpoint of OAuth and OIDC. 

**BrowserControl** can use a Selenium instance (with an internal, headless browser implementation) to mimic human interaction. This can be configured using an additional block in the configuration JSON object named `browser`. This member a list of objects, each object with a URL pattern `match` used for matching the URLs sent to the `goToUrl` function. When a URL is sent to the **BrowserControl** class, if one of these `match` URLs matches the incoming URL, the URL is fetched by Selenium and then the matching configuration object's list of `tasks` is executed in order. Each task also contains a URL to `match` against (defaults to `*` or any URL), a required `task` name, and a list of `commands` to execute on the given page. If the current URL matches the `match` URL, the `command` list is executed in order. Commands are formatted as lists of options. The first option is the type of command, `text` or `click`. The second option is the means of searching for the page element to interact with, using Selenium's selector types of `id`, `name`, `xpath`, `css`, or `class`. The third option is the argument to the selector type used in the second option. For a `click` action, these arguments simulate a click. For the `text` action, the fourth option is the text value that is typed into the element selected.

If the framework is able to complete all `tasks` and their associated `commands`, it results in a `success` being logged, much like a `Condition` would do. If there are any errors (such as failure to match an expected non-optional URL or failure to find and interact with the elements in the script), the framework will record them in the log and stop the test as a failure.

Any URLs sent to the `goToUrl` function that do NOT match any browser control objects will be placed into a queue and exposed in the UI for user interaction. These are available by calling `/runner/browser/{id}` and can be marked as visited by calling `/runner/browser/{id}/visit`.

An example configuration follows:

```json
    "browser": [{
        "match": "https://mitreid.org/authorize*",
        "tasks": [{
                "task": "Initial Login",
                "match": "https://mitreid.org/login*",
                "commands": [
                    ["text", "id", "j_username", "user"],
                    ["text", "id", "j_password", "password"],
                    ["click", "name", "submit"]
                ]
            },
            {
                "task": "Authorize Client",
                "match": "https://mitreid.org/authorize*",
                "optional": true,
                "commands": [
                    ["click", "id", "remember-not"],
                    ["click", "name", "authorize"]
                ]
            },
            {
                "task": "Verify Complete",
                "match": "https://*/test/a/*/callback*",
            }
        ]
    }]
```
Each `task` should be things that happen on a single page. In the above example, the first task logs in by typing a username and password into the appropriate fields and ends with clicking the submit button on the login page, resulting in a new page to get loaded. (The result of logging in).

The second task clicks the "Do not remember this choice" radio button, and then clicks the authorize button which then should trigger the redirect from the server. This task is optional as it's possible the client has been whitelisted or previously remembered.

The third and final task verifies that the results of the interaction redirect back to the test framework server running on `localhost`. It's required that task lists always include a verification `task` with no `command` objects to ensure all redirects and other items return as expected - if this is missing tests may randomly fail.

A more detailed example can be found here: https://gitlab.com/openid/conformance-suite/-/wikis/Authlete-Automated-Example-Configuration. There is also a step-by-step tutorial available at https://gitlab.com/openid/conformance-suite-automated-testing-tutorial.

The configuration can be a little tricky to perfect; a few hints:

1. The log page within the conformance suite frontend contains a reasonable level of detail as to what Selenium does, this is the first place to check if the automation is not working as expected. Extra logging can be enabled by including `"browser_verbose": true` at the root level of the test config json.

2. Some debug output is only available if you run the suite locally: you can add `logging.level.net.openid.conformance.frontChannel=DEBUG` to `application.properties` resulting in more detail being logged to the java console (if running in docker, this would then appear in the docker output or can be retrieved via `docker logs`. If running in an IDE the output will usually appear within the IDE). If running the suite locally, you will need to set `fintechlabs.startredir` to `true` in `application.properties` as otherwise selenium (running within the jam) will not be able to reach the httpd frontend, which runs in a different docker container.

3. There are a few commands that are available but not really documented; check the source code of [BrowserControl.java](https://gitlab.com/openid/conformance-suite/-/blob/master/src/main/java/net/openid/conformance/frontchannel/BrowserControl.java#L370) (in particular the `doCommand` method) for some of the more advanced cases.

---

*Conteúdo baixado em 16/09/2026, 15:38:40*
