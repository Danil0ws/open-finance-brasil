# Guidelines_FVP_Execution_Team

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Guidelines_FVP_Execution_Team](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Guidelines_FVP_Execution_Team)
**Slug:** `Guidelines_FVP_Execution_Team`

---

---
title: Guidelines for the FVP Execution Team
---
## Introduction - Scheduled and immediate tests

The Scheduled Tests feature of the FVP extends the platform’s capability to validate production implementations of Open Finance Brasil in **multi-day scenarios**.\
Unlike traditional test executions that complete in a single run, scheduled tests allow a flow to begin on one day and automatically continue on subsequent days.

This functionality is especially important for validations that depend on specific dates, times, and system behaviors that can only be observed asynchronously.

This document guides scheduled tests, as well as details for running immediate tests (click to jump):

1. [Automatic PIX Scheduling – Retry Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests#automatic-pix-scheduling--retry-tests-modules-1-to-3)
2. [Payments API — Scheduled PIX Verification](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests#payments-api--scheduled-pix-verification-modules-1-to-2)
3. [Credit Portability — CPC](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests#credit-portability--cpc-modules-1-to-3)
4. [Non-Redirect Journey — NJR (Enrollments)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Scheduled-Tests#gear-non-redirect-journey--njr-enrollments)

## How Scheduled Tests Work

* **Asynchronous Execution**: When a test flow is executed, it may schedule follow-up executions on future dates. These follow-ups run automatically without requiring user intervention.
* **Persistence**: Critical information such as client ID, consent ID, payment ID, and refresh tokens is securely stored between test runs to ensure continuity.
* **Business Timing**: Tests are aligned with real-world payment timelines (e.g., D+2, D+3) and some are restricted to specific execution windows (e.g., between 9:00 PM – 11:59 PM BRT).
* **Automatic Safeguards**: Follow-up tests are only scheduled if the initial flow completes successfully. If an error occurs early in the process, no further executions are triggered.
* **Visibility**: Open Finance Structure can view scheduled executions, their origin, and their status (scheduled, executed, cancelled). Logs and results follow the same evidence and retention rules as other FVP tests.

## Available Scheduled Test Flows

### Automatic Pix Scheduling Flow

This flow validates that a **recurring Pix payment can be scheduled** and later executed as expected.

* The initial execution creates and authorizes a recurring consent, schedules a Automatic Pix payment, and stores the relevant information.
* A follow-up test then confirms that the scheduled payment is executed successfully on the defined future date.

### Automatic Pix Retry Flow

This flow validates the **retry mechanisms for scheduled Pix payments**.

* The initial execution creates a recurring consent with retry enabled, schedules a Automatic Pix payment, and prepares for failure handling.
* On the follow-up execution, the system validates that the original payment failed and that a retry has been correctly initiated with the appropriate references.
* A final verification test then confirms that the retry payment has been moved out from Schedule, accepting both a ACSC or RJCT status.

Together, these flows ensure institutions are compliant with Open Finance Brasil standards for **scheduled and recurring Pix payments**, including both successful scheduling and retry scenarios.

### Credit Portability Accepted Settlement Flow

This flow validates the **scheduled progression** of a Credit Portability request from initial submission through acceptance and settlement, ensuring that all required business transitions occur in compliance with the Open Finance Brasil specification.

The full flow consists of three modules, executed across multiple business days. These steps ensure institutions comply with Open Finance Brasil timing and state transitions for scheduled credit portability.

## Execution Policies

* Scheduled tests can only be executed by authorized personel.
* Scheduled tests execute automatically at the designated times once the initial flow is run.
* Identifiers and credentials are securely persisted across test executions.
* Some tests require execution within strict time windows to reflect real production behavior.
* Logs and results are available through the FVP interface.

## Test Plan List

A full list of available test plans, their corresponding modules, and detailed execution is available below.\
This list provides the technical details (endpoints, expected responses, identifiers) that complement the high-level descriptions above.

[fvp-async_tests.xlsx](uploads/6e9582e0da324affc0edf01e2421798f/fvp-async_tests.xlsx)

---

## Test Execution Documentation

---

## :gear:Automatic PIX Scheduling – Retry Tests (Modules 1 to 3)

**Test Modules:**

* `automatic-payments_api_automatic-pix-scheduling-retry_1-3_test-module_v2`
* `automatic-payments_api_automatic-pix-scheduling-successful-retry_1-3_test-module_v2`

This document explains how to validate recurring PIX payments, including the retry flow when the original payment fails.

### 1) Required Fields for Execution

Different fields are required depending on whether the debtor is an individual (PF) or a legal entity (PJ).

**For Individuals (PF)**

* `loggedUserIdentification`
* `contractDebtorName`
* `contractDebtorIdentification`

**For Legal Entities (PJ)**

* `loggedUserIdentification`
* `businessEntityIdentification`
* `contractDebtorName`
* `contractDebtorIdentification`

**Required for both PF and PJ**

* **Authorisation Server ID**
* **Payment consent – Creditor Account ISPB:** first 5 digits of the institution that holds the creditor (receiver) account
* **Payment consent – Creditor Account Issuer:** branch/agency number of the creditor’s institution
* **Payment consent – Creditor Account Number:** account number of the creditor’s institution
* **Payment consent – Creditor Account Type:** account type at the creditor’s institution
* **Payment consent – Creditor Account Name:** name of the creditor account holder (receiver)
* **Payment consent – Creditor Account CPF/CNPJ:** national ID of the creditor account holder (receiver). For **Automatic PIX**, this **must be a CNPJ**.

### 2) Additional Execution Requirements

**Account balance (debtor):**

* **D+0 (execution day):** R$ 0.00
* **D+1 (day after execution):** R$ 0.00
* **D+2 (two days after execution):** R$ 0.00
* **D+3 (three days after execution):** **at least R$ 1.00**

> **Note:** “D+N” refers to N calendar days after running Module 1.

**Server availability:**

* **Modules 2 and 3** are scheduled automatically by the Conformance Suite (not manual).
* Keep the participant server online and responsive between **21:00 and 23:59 (BRT)** on the scheduled days.

### 3) Test Module Overview

**Module 1 — Schedule the Recurring Payment (manual)**

* Manually create a recurring PIX payment.
* The first payment is scheduled for **D+2**.
* Expected status flow: **Awaiting Authorisation → Authorised → Scheduled**.
* Consent and payment data are persisted for use in Modules 2 and 3.

**Module 2 — Retry after Failed Payment (automatic; runs 2 days after Module 1)**

* The Conformance Suite starts this module at the scheduled time.
* Verifies the first scheduled payment **failed**.
* Confirms the system scheduled a **retry payment for D+1**.
* Runs between **21:00 and 23:59 (BRT)**; participant server must remain online.

**Module 3 — Confirmation of Successful Retry (automatic; runs 1 day after Module 2)**

* The Conformance Suite starts this module at the scheduled time.
* Verifies the **retry payment completed successfully**.
* Final payment status must be **`ACSC`**.
* Runs between **21:00 and 23:59 (BRT)**; participant server must remain online.

---

## :gear:Payments API — Scheduled PIX Verification (Modules 1 to 2)

This document explains how to validate **Payments API** tests for **scheduled PIX verification**.

### 1) Required Fields for Execution

Different fields are required depending on whether the debtor is an individual (PF) or a legal entity (PJ).

**For Individuals (PF)**

* `loggedUserIdentification`

**For Legal Entities (PJ)**

* `loggedUserIdentification`
* `businessEntityIdentification`

**Required for both PF and PJ**

* **Authorisation Server ID**
* **Payment consent – Creditor Account ISPB:** first 5 digits of the institution that holds the creditor (receiver) account
* **Payment consent – Creditor Account Issuer:** branch/agency number of the creditor’s institution
* **Payment consent – Creditor Account Number:** account number of the creditor’s institution
* **Payment consent – Creditor Account Type:** account type at the creditor’s institution
* **Payment consent – Creditor Account Name:** name of the creditor account holder (receiver)
* **Payment consent – Creditor Account CPF/CNPJ:** national ID of the creditor account holder (receiver); can be **CPF or CNPJ**
* **Payment consent – Creditor Account Proxy (Pix key):** PIX proxy for the creditor account holder (receiver)

### 2) Additional Execution Requirements

**Account balance (debtor):**

* **D+0 (execution day):** **R$ 2.00**
* **D+1 (day after execution):** **R$ 2.00**
* **D+2 (two days after execution):** **R$ 1.00**

**Server availability:**

* **Module 2** is scheduled automatically by the Conformance Suite (not manual).
* Keep the participant server online and responsive between **05:00 and 06:59 (BRT)** on the scheduled days.

### 3) Test Module Overview

**Module 1 — Schedule Two Payments (manual)**

* Manually create **two** scheduled PIX payments:
  * First payment scheduled for **D+1**
  * Second payment scheduled for **D+2**
* Expected status flow: **Awaiting Authorisation → Authorised → Scheduled**.
* Consent and payment data are persisted for Module 2.

**Module 2 — Verify Execution of Both Payments (automatic)**

* The Conformance Suite starts this module at the scheduled time.
* Verifies that **both scheduled payments** were completed successfully.
* Final payment status for each must be **`ACSC`**.

---

## :gear:Credit Portability — CPC (Modules 1 to 3)

**Test Plans and Modules related to the instructions below:**

* Production Functional Tests for Credit Portability - API Version 1:
  * `fvp-credit-portability_api_invalid-contract-terms_test-module_v1`
  * `fvp-credit-portability_api_received-portability_test-module_v1`
  * `fvp-credit-portability_api_invalid_grant_type_invalid_x-fapi_invalid_idempodency_test-module_v1`
* Production Functional Tests for Credit Portability Scheduling - API Version 1:
  * `fvp-credit-portability_api_accepted_settlement_1-3_test-module_v1`
  * `fvp-credit-portability_api_accepted_settlement_2-3_test-module_v1` - automatically scheduled
  * `fvp-credit-portability_api_accepted_settlement_3-3_test-module_v1` - automatically scheduled

### 1) Fields for Execution

Field names below mirror the FVP form.

* `alias` — Optional. Automatically bypassed by authorizationServerId information.
* `description` — Optional, user-defined content.
* `publish` — Whether test results should be made visible to other users. “Everything” will reveal configuration information, including secret keys. Use “summary” if these details should remain private while the overall results are public. If in doubt choose “No” – test results can be made public later.
* `discoveryUrl` — Optional. Automatically bypassed by authorizationServerId information.
* `authorizationServerId` — **Required**. Institution’s Authorisation Server ID in the Directory. Must match the **same environment** as the discovery URL.
* **PF / PJ (required, choose 1):**\
  • **PF**: `brazilCpf` (11 digits, numbers only)\
  • **PJ**: `brazilCnpj` (14 digits, numbers only)\
  _(Fill only one. If both are set, the run can be rejected.)_
* `discoveryEndpoint` — Optional. Automatically bypassed by authorizationServerId information.

### 2) Additional Execution Requirements

**Account balance:** not required for Credit Portability tests. Instead, a **personal loan** (“clean”, **CPC**) is required.

**Server availability:**

* **Modules 2 and 3** are scheduled automatically by the Conformance Suite (not manual).
* Keep the participant server online and responsive on the scheduled days. If participant servers are offline during the scheduled window, modules 2 and 3 may fail.

### 3) Module Overview & Windows

* **Module 1 (manual):**
  * Submits a Credit Portability request that reaches status **RECEIVED** and stores the identifiers required for follow-up validation.
  * The test requires the user to have at least one _CREDITO_PESSOAL_CLEAN_ contract with concurrentManagement= _DISPONIVEL_ and isEligible = _TRUE_.
  * The module executes the full pre-check sequence (_consent creation, contract retrieval, eligibility, and POST /portabilities_), then schedules Module 2 for the following business day (D+1), at 10:10 (GMT-3).
* **Module 2 (automatic, next window/day):**
  * Validates that the same portability request progresses to status **ACCEPTED_SETTLEMENT_IN_PROGRESS** within the expected business timeframe.
  * If the status is still _PENDING_, the suite automatically reschedules this module.
  * Once the request is accepted, the test triggers a user-driven cancellation (_PATCH /portabilities/{id}/cancel_) with reasonType = CANCELADO_PELO_CLIENTE, confirming that the process terminates correctly with status = CANCELLED.
  * Upon completion, it schedules the concurrency-management check module for the next day (00:01, GMT-3).
* **Module 3 (automatic, next window/day):**
  * Confirms that the original contract returns to **DISPONIVEL** and remains _eligible_ for future portability.
  * It validates data.portability.status = DISPONIVEL and isEligible = TRUE, then deletes the associated consent to complete the cycle.

### 4) Timing & Maximum Duration

* **Plan‑configured windows:** M1 could run at any time. M2 and M3 execution time is pre-defined by FVP.
* **Maximum duration:** As a product guideline, the end‑to‑end horizon is **≤ 5 business days (excluding weekends and Brazil national holidays)**. If this cap is reached without a terminal state, the run is reported as **Not Completed / Expired**, and a **re‑execution** is required.

---

## :gear: Non Redirect Journey **— NJR (Enrollments)**

Test plans (immediate and scheduled) related to the instructions in this section:

* **Production Functional Tests for No Redirect Payments - API Version 2.2**
* **Production Functional Tests for No Redirect Payments Scheduling - API Version 2.2**
* **Production Functional Tests for No Redirect Automatic Pix Payments - API Version 2.2**
* **Production Functional Tests for No Redirect Automatic Pix Payments Scheduling - API Version 2.2**

---

### **1) Execution fields**

Field names match the FVP form.

**For individual debtor PF:**

* `brazilCpf` -  11 digits, numbers only

**For business debtor PJ:**

* `businessEntityIdentification` - always CNPJ, 14 digits, numbers only
* `brazilCnpj` - 14 digits, numbers only

**Required for both PF and PJ:**

* `alias` — Optional. Automatically filled/overwritten based on data collected via authorizationServerId.
* `description` **—** Optional, at the user’s discretion.
* `publish` **—** Defines result visibility to other users. “Everything” exposes configuration details (including secrets). Use “summary” to keep those details private and publish only the overall result. If unsure, choose “No” (it can be made public later).
* `loggedUserIdentification` - always CPF, 11 digits, numbers only
* `authorizationServerId` **-** Required. The institution’s Authorization Server ID in the Directory.
* `Payment consent – Creditor Account ISPB`: ISPB of the creditor account (first 5 digits of the institution that holds the receiver’s account)
* `Payment consent – Creditor Account Issuer:` creditor account issuer/branch
* `Payment consent – Creditor Account Number:` creditor account number
* `Payment consent – Creditor Account Type:` creditor account type
* `Payment consent – Creditor Account Name:` account holder name (receiver)
* `Payment consent – Creditor Account CPF/CNPJ:` account holder CPF/CNPJ (receiver)
* `Payment consent – Creditor Account Proxy (Pix key):` receiver’s proxy (Pix key)

**Obrigatórios para plano de Enrollments + Automatic Payments:**

* `contractDebtorName` - name of the contract debtor.
* `contractDebtorIdentification` - CPF/CNPJ of the contract debtor

---

### **2) Additional requirements for long-term tests:**

**Account balance (debtor)**

**Production Functional Tests for No Redirect Payments Scheduling - API Version 2.2**

* **D+0 (execution day):** irrelevant
* **D+1 (next day):** minimum **BRL 1.00**
* **D+2 (two days after):** minimum **BRL 1.00**
* **D+3 (three days after):** irrelevant

**Production Functional Tests for No Redirect Automatic Pix Payments Scheduling - API Version 2.2**

* **D+0 (execution day):** irrelevant
* **D+1 (next day):** irrelevant
* **D+2 (two days after):** minimum **BRL 1.00**
* **D+3 (three days after):** irrelevant

> **Note:** “D+N” means **N calendar days** after running Module 1.

**Server availability**

* **Module 2 is automatically scheduled** by the Conformance Suite (it is not manual).
* Running **Module 2 directly** will cause an **undesired ticket** to be opened against the institution, containing an incorrect (“broken”) Test Manager link.
* Ensure the participant server is **online and responsive** on the scheduled days.

  If it is **offline** during the window, **Module 2 will fail**.

---

### **3) Module overview and long-term windows**

* **Production Functional Tests for No Redirect Payments Scheduling - API Version 2.2**
  * Schedules **two payments** of **BRL 1.00** each via JSR:
    * **Payment 1:** D+1
    * **Payment 2:** D+2
    * On **D+3**, the test verifies both payments were successfully executed.
  * **Windows**
    * **Module 1:** can be executed at any time
    * **Module 2:** runs at **5:00 AM BRT on D+3**
* **Production Functional Tests for No Redirect Automatic Pix Payments Scheduling - API Version 2.2**
  * Schedules **one automatic payment** of **BRL 1.00** via JSR:
    * **Payment:** D+2
    * On **D+3**, the test verifies the payment was successfully executed.
  * **Windows**
    * **Module 1:** can be executed at any time
    * **Module 2:** runs at **9:00 PM BRT on D+3**

---

### **4) Schedule and maximum duration**

* **Per plan windows:** Module 1 can be executed at any time. The exact execution times for each plan’s Module 2 are **preconfigured** in the FVP.
* **Maximum duration:** **3 calendar days** (includes non-business days).

---

*Conteúdo baixado em 16/09/2026, 15:38:08*
