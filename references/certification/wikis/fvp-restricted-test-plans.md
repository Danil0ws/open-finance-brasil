# FVP Restricted Test Plans

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Restricted-Test-Plans](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Restricted-Test-Plans)
**Slug:** `FVP-Restricted-Test-Plans`

---

# Objective

The FVP Restricted Tests, an extension of the self-executed production tests from FVP Open Test, are specifically designed to handle the security aspects of data sharing and payments initiation for Phase 2 and Phase 3 APIs in the Open Finance Brazil ecosystem. These tests are crucial as they involve the sharing of sensitive customer data and the execution of payment transactions. Due to the sensitive nature of these operations, FVP 3 test plans are restricted to be executed by a specialized group.

To be able to execute the tests, the Restricted group must have an open account in the institution being tested. This setup allows them to perform live transactions and validate the entire flow of operations, including customer data handling and payment processing. If the group does not have an account with a particular institution, that institution will need to conduct its own tests using FVP Open Tests, which provides a platform for self-executed production testing.

# Release Dates

- 07/06/24 - Automatic Payments v1 Test Plan includes: 2 happy scenarios for automatic payments v1
- 09/05/24 - Phase 3 v4 test plan included: 1 happy scenario for payments v4
- 03/05/24 - Phase 2 v3 test plan included: 1 happy scenario for resources
- 15/03/24 - Phase 3 v3 test plan included: 1 happy scenario and 7 unhappy scenarios
- 22/01/24 - Phase 2 v2 test plan included: 10 happy scenarios for each phase 2 API

# Configuring and Executing Tests

The specifications on how to access the platform and configure tests can be seen in the [Manual FVP Main Page](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Manual-Production-Tests), with additional profile requirements to avoid regular PFVPC users executing restricted tests.

## Selecting Test Plans

All test plans designated for the FVP Restricted Tests can be found below the section Open Finance Brasil Functional Production Tests - FVP (Restricted Test Plans). The test plans are split between APIs and Versions, and user can select any of the options in the dropdown list

![image](uploads/db8e9709cec7554b735a734ba9f1ea0f/image.png){width="526" height="135"}

If a user without the right permission tries to create a test plan, an error message will pop up on the screen as shown below

![image](uploads/9b96d249bf6c3f576d1403bb82d4e2a5/image.png){width="371" height="298"}

# Test Plan List

The following test plans are part of the FVP Restricted Tests Testing Scope

[20260602-fvp-restricted-tests.xlsx](uploads/acab1f0384fc99770757a74b74acc9c0/20260602-fvp-restricted-tests.xlsx)

---

*Conteúdo baixado em 16/09/2026, 15:37:32*
