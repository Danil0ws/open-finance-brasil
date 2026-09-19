# Test naming convention

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-naming-convention](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-naming-convention)
**Slug:** `Test-naming-convention`

---

We have recently enhanced our Conformance Suite for Open Finance Brasil to ensure a streamlined and standardized testing process for institutions seeking certification. As part of this update, we have **introduced new test module names and displayNames that offer improved control and clarity during the testing phase**. These changes have been implemented to align with industry best practices and provide a more efficient workflow for institutions integrating with our platform.

To facilitate a smooth transition, we have prepared a **comprehensive spreadsheet that maps the old test module names to their corresponding new names**. This spreadsheet serves as a valuable resource for institutions, allowing them to easily identify and locate the updated test modules within our Conformance Suite. By providing this documentation, we aim to empower institutions to swiftly adapt to the changes, ensure compliance with Open Finance Brasil standards, and seamlessly proceed to the next phase of executing the test modules required for certification.

[230629_New_Test_ID_List.xlsx](uploads/4458c3993ca9670dfa58b83fc899436b/230629_New_Test_ID_List.xlsx)

We have also introduced **new regular expressions (regex)** to enhance the identification and naming conventions within our Conformance Suite. These regex patterns ensure consistency and clarity when referring to the different components of the testing process. Here are the updated regex patterns:

_For modules_:

- Regex pattern: ^(._?)api(._?)(\_)(test-module)((\_v\\d)||())$
- Example: accounts_api_core_test-module_v2

_For plans:_

- Regex pattern: ^(.\*?)\_(test-plan)((\_v\\d)||())$
- Example: accounts_test-plan_v2

In addition, we have updated the display name format to provide more context and information about each test plan. The new display name format is as follows:

- Display name format: Functional Tests for {API} - Based on Swagger version: {version}
- Example: Functional Tests for Accounts API - Based on Swagger version: 2.0.1

These changes ensure better standardization and control over the test, making it easier for institutions to locate and execute the appropriate tests during the certification process.

---

*Conteúdo baixado em 16/09/2026, 15:38:39*
