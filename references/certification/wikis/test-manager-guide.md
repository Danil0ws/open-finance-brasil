# Test Manager Guide

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-Manager-Guide](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Test-Manager-Guide)
**Slug:** `Test-Manager-Guide`

---

## Objective

Explain, objectively, how the Test Manager opens, updates, and closes Service Desk tickets when scheduled tests are executed from the long-duration Manual FVP.

---

## Overview

* The Test Manager is the system that enables the execution of scheduled tests from the Restricted Manual FVP and the integration of the respective executions with the Service Desk. When a scheduled test plan is executed, the system can:
  - **Open** a ticket (first failure of the plan).
  - **Update** an existing ticket (subsequent failures of the same plan, via note).
  - **Close** a ticket automatically (when all tests in the plan pass).

> Important: this happens only for tests that belong to long-duration plans. Standalone tests (outside these plans) do not generate automatic tickets.

* Tracking is always based on a combination:
  * Authorisation Server Id (ASId) + Test plan + type (PF or PJ) → there will be at most one open ticket per combination, according to the application logic.
* How to access the Test Manager: https://scheduler.fvp.directory.openbankingbrasil.org.br/

---

## How it works (4-step flow)

### 1) Setup (when the test is created/scheduled)

* **What the system does:** identifies that the test belongs to a long-duration plan and stores the data internally (ASId, test plan, test link).
* **What you see:** nothing changes in the Service Desk (no ticket is created/updated at this stage).

### 2) Ticket creation (failed and there is no open ticket for the combination)

* When the test fails, the system checks whether there is already an open ticket for the same:
  - ASId
  - Test plan
  - Type (PF or PJ)
  - Most recent ticket under these conditions
* If none exists, it opens a new ticket with a standard title/description and the link to the failed test.
* **What you can expect:**
  * Whether a ticket already exists or a new one is created, the Test Manager will start tracking that ticket in subsequent executions.

### 3) Ticket update (failed and there is already an open ticket for the combination)

* If the test fails and there is already an open ticket for that combination, the system does not open another one. It updates the existing ticket, adding a note with standard text and the link to the test that has just failed.
* **What you can expect:**
  * Subsequent failures of the same plan become notes in the same ticket, keeping history and evidence centralised.

### 4) Automatic closure (when all tests in the plan pass)

* When a test passes and the system identifies that it is the last one in the plan (i.e., all tests in the plan have already run and passed), it:
  - Closes the ticket in the Service Desk.
  - Ends tracking for that combination (on the next run of the plan, the cycle restarts).
* **What you can expect:**
  * If the test passed but is not yet the last one in the plan, the ticket remains open.

---

## Possible/common scenarios

* **Multiple consecutive failures in the same test plan**
  * The first failure opens the ticket; the others are added as notes in the same ticket.
* **A test passed, but there are still other tests remaining in the plan**
  * The ticket does not close until the last test in the plan passes.
* **The original ticket was manually closed before the plan was completed**
  * On the next failure, the system will not create a new ticket nor update existing tickets.
    * Reason: it will not find a compatible open ticket and it will still have the original ticket stored as a reference in the database.
  * On the next success, the system will not close any ticket.
    * Reason: it will attempt to close a ticket that is already closed; the Service Desk will block the action, and then the Test Manager will remove the internal record (institution + plan + type). In other words, it “forgets” that ticket and stops tracking that combination.
* **Service Desk/integration unavailable at the time of failure**
  * The system does not reprocess automatically (no retry). On a subsequent failure/success run of the test, the system will try again to update/close the ticket.
* **Exceptions (blacklist)**
  * Some plans may be on an exception list. In these cases, the system does not open or update tickets, even on failure.

---

If you would like to submit suggestions/questions, report inconsistencies, or discuss any point in this document, please use the GitLab Issues page: https://gitlab.com/groups/raidiam-conformance/open-finance/-/issues.

---

*Conteúdo baixado em 16/09/2026, 15:38:38*
