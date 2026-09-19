# EventLog

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/EventLog](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/EventLog)
**Slug:** `UpStream-Design/EventLog`

---

The **EventLog** is used by [`TestModule`](./TestModule)s (and by extension [`Condition`](./Condition)s) to record the progress of the [`TestModule`](./TestModule). 

The **EventLog** is designed to store arbitrary JSON objects, but objects have the following fields automatically added:

 * `testId`: the random ID of the [`TestModule`](./TestModule) that created the event
 * `src`: the source of the event, either the name of the [`TestModule`](./TestModule) or the name of the [`Condition`](./Condition) that logged the event
 * `timestamp`: a timestamp in integer milliseconds since Unix Epoch

The contents of the **EventLog** is available through an API:

 * `GET` to `/log`: return a list of testIds from the database
 * `GET` to `/log/id`: return a list of event objects for the given test id, ordered by increasing timestamp

---

*Conteúdo baixado em 16/09/2026, 15:38:43*
