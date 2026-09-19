# home

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/home](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/home)
**Slug:** `home`

---

## Welcome to the Open Finance Brazil Functional Conformance Suite

The **Open Finance Brazil Functional Conformance Suite GitLab Wiki** is the central documentation hub for using and maintaining the Conformance Suite within the OFB ecosystem. It brings both operational guidance (how to run tests, submit requests, and raise issues) and technical reference (how the suite works internally and how to develop or adjust tests and test plans).

This Wiki starts with onboarding pages (_Home_, [Introduction](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Introduction)) and an **important Security Advisory**: _because the suite can behave as an open proxy/open relay, anyone running it locally or in the cloud should enforce least privilege and restrict access only to the network segments and resources that need to be tested._

It also contains practical guidance on processes and support, including the [**Service Desk Submission Guide**](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Certification-Guide) (how to submit requests and follow the certification/support flow) and the [**GitLab Issues Guide**](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/GitLab-Issues-Guide) (best practices for reporting problems, attaching evidence, and tracking progress).

The Test Plans section is organized by phase, journey, and environment (including Phase 1–4 tracks, specific journeys like Credit Portability and Optimized Journey, and production execution via Automatic FVP and Manual FVP). The wiki also groups content by execution type (e.g., Open, Restricted, Authorized Organisations, and Scheduled Tests). Use the menu below to jump directly to the page you need:

**Test Plans**

- [Alphanumeric CNPJ](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Alphanumeric-CNPJ)
- [Credit Portability](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability)
- [Optimized Journey](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Optimized-Journey)
- [Phase 1 - Open Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-1-4A-Open-Data)
- [Phase 2 - Customer Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-2-and-4B-Customer-Data/Phase-2)
- [Phase 3 - Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services)
- [Phase 3 - No Redirect Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Enrollments-v2.2.0)
- [Phase 3 - Automatic Payments](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-3-Services/Automatic-Payments-v2.2.0)
- [Phase 4A - Open Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-1-4A-Open-Data)
- [Phase 4B - Customer Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Phase-2-and-4B-Customer-Data/Phase-4B)
- [FVP - Automated Production](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Automatic)
- [FVP - Manual Production](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual)
  - [Open Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Immediate)
  - [Restricted Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Manual/Scheduled)
  - [Authorized Organisations](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Authorized-Orgs)
  - [Scheduled Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Guidelines_FVP_Execution_Team)
  - [Scheduled Tests (PT version)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Orientacoes_Execucao_FVP)

The wiki also includes dedicated pages for **Mock Bank**. Use the menu below to jump directly to the relevant page:

**Mock Bank**

- [Discovery of the Mock Bank](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank) / [(PT version)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Discovery-of-the-Mock-Bank-%28PT%29)
- [Registering against the Mock Bank (DCR)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-%28DCR%29) / [(PT version)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-%28DCR%29-%28PT%29)
- [New Security Profile - FAPI Unique](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Enable-FAPI-Unique)
- [Customer Data](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Data)
- [Payment Initiation](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Payments-APIs)
- [Credit Portability](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-MB)
- [CIBA Flow with the Mock Bank](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA-Flow-with-the-Mock-Bank) / [(PT version)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA-Flow-with-the-Mock-Bank-%28PT%29)

Finally, for those developing or maintaining the suite, the wiki includes documentation on **execution and engineering**, such as the Test Naming Convention, how to run conformance tests locally and against production, how to write new tests and test plans for protected resources, and an overview of the internal architecture/design and main components.

**Running and updating the CS tests**

- [Test Naming Convention](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-naming-convention)
- [Instructions for running Conformance Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Instructions-for-running-Conformance-tests)
- [Writing New Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Writing-New-Tests)
- [Writing Test Plans for Protected Resources](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Writing-Test-Plans-for-Protected-Resources)
- [Running specific tests locally against your own API responses](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Running-specific-tests-locally-against-your-own-API-responses)

**Conformance Suite Design**

- [Running the conformance suite locally](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Running-the-conformance-suite-locally)
- [Executing tests against Production AS](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Executing-tests-against-an-AS)
- [UpStream - Design](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design)
  - [BrowserControl](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/BrowserControl)
  - [Condition](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Condition)
  - [Configuration](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Configuration)
  - [Environment](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Environment)
  - [EventLog](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/EventLog)
  - [Structure](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Structure)
  - [TestDispatcher](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestDispatcher)
  - [TestModule](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestModule)
  - [TestRunner](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/TestRunner)

If you would like to discuss any content or suggest improvements, please feel free to open a [**GitLab Issue**](https://gitlab.com/raidiam-conformance/open-finance/certification/-/issues?sort=created_date&state=opened&first_page_size=20) and our team will follow up.

Team Raidiam

---

*Conteúdo baixado em 16/09/2026, 15:38:49*
