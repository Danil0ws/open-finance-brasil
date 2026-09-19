# Condition

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Condition](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Condition)
**Slug:** `UpStream-Design/Condition`

---

The **Condition** is the basic unit of executable code in the test framework. They implement the `Condition` interface and an `AbstractCondition` abstract class is provided with a set of utility methods to facilitate development of new **Condition**s. This documentation assumes the use of this abstract class.

All of the work within a **Condition** takes place in the `evaluate` function. The **Condition** can use other functions to accomplish its work, but only the `evaluate` function will ever be called by the test framework. 

A **Condition**  takes all of its input by reading the passed-in [`Environment`](./Environment). **Condition**s can read anything in the [`Environment`](./Environment), but most will look for very specific elements in the incoming [`Environment`](./Environment). 

A **Condition**  sends output to the running test by altering the [`Environment`](./Environment), normally by adding new values at well-known locations. Other **Condition**s (or the [`TestModule`](./TestModule) itself) will then in turn look for these values to complete their work.

Upon success, a **Condition**  should call the `logSuccess()` method and `return` the modified [`Environment`](./Environment). 

Upon any error, a **Condition** should throw a `ConditionError` object to be caught and handled by the test framework. This stop execution of the **Condition** immediately and returns control to the containing [`TestModule`](./TestModule). The [`TestModule`](./TestModule) then decide of the **Condition**'s failure constitutes a failure for the entire test or if it should be ignored (but logged) and continue. Syntactically, this accomplished calling one of the helper functions as `return error(...);`. 

**Condition**s are initialized with the ID of the enclosing [`TestModule`](./TestModule) instance as well as a reference to the [`EventLog`](./EventLog). **Condition**s are intended to be created, called, and discarded. **Condition**s should not keep any internal state that lives past the execution of the `evaluate` function. If a particular testing aspect requires multiple steps or options, it should be split into multiple **Condition** objects. 

**Conditions**s should be placed into a package corresponding to the component they are mocking, not the component they are testing. Thus `SignIdToken` is in the `as` package, and `VerifyIdTokenSignature` is in the `client` package. 

---

*Conteúdo baixado em 16/09/2026, 15:38:41*
