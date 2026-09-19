# Mockbank Portability   Status Transitions

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Mockbank-Portability---Status-Transitions](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Mockbank-Portability---Status-Transitions)
**Slug:** `Mockbank-Portability---Status-Transitions`

---

---
title: Mockbank Portability - Status Transitions
---
## About this page

This page documents how Mockbank handles credit portability status transitions, with the goal of guiding testers and certification teams when running scenarios against the **Credit Portability (CPC)** and **Payroll Credit Portability** APIs.

The documentation covers:

* How each status is reached in the mock through the spec-compliant API calls exercised by the conformance suite.
* Which transitions happen **on their own** and which are produced by specific request payloads or test data.
* The relationship between what is defined in the spec and what the mock actually implements, avoiding incorrect assumptions — for example, about business-day simulation or background processing.

The conformance suite test modules are the source of truth for the call sequences expected from a participant. This page complements them by clarifying the mock's timing model and the test data needed for specific outcomes.

---

## How the mock handles transitions

Mockbank **does not simulate business days** and **does not perform asynchronous processing** (cron, EventBridge, background jobs) for portability. Status changes happen in three ways:

* **Automatic time-based transitions** evaluated when a `GET` on the resource is called. The timer between each automatic stage is **30 seconds** since the last status update. Creating the portability, waiting 30s, and calling `GET` advances one stage; each subsequent `GET`, with another 30s elapsed, advances to the next.
* **Payload-driven transitions** triggered by spec-compliant calls — for example, `POST /portabilities/{id}/payment` promotes the portability to `ACCEPTED_SETTLEMENT_COMPLETED`, and a divergent `paymentAmount` produces `PAYMENT_ISSUE` on the next `GET`.
* **Cancellation and rejection through spec endpoints**: `PATCH /portabilities/{id}/cancel` and, in Payroll only, `POST /portabilities/{id}/request-discharge`.

> **Spec vs. mock behavior:** the `PENDING` status is part of the spec for both Credit Portability (CPC) and Payroll Credit Portability. The difference lies only in the **mock's automatic flow**: in CPC, the mock **does not transition through `PENDING`** — `RECEIVED` jumps straight to `ACCEPTED_SETTLEMENT_IN_PROGRESS`. In Payroll, `PENDING` is part of the automatic path.

---

## Conformance suite test modules

Each status outcome can be reached by following the call sequence exercised by the corresponding test module.

### Credit Portability (CPC)

| Outcome | Test module |
|---------|-------------|
| Happy path: `RECEIVED` → `ACCEPTED_SETTLEMENT_IN_PROGRESS` → `ACCEPTED_SETTLEMENT_COMPLETED` → `PORTABILITY_COMPLETED` | `credit-portability_api_portability-payment_core_test-module_v1` |
| `PAYMENT_ISSUE` (divergent payment amount) | `credit-portability_api_portability-invalid-payment_test-module_v1` |
| `CANCELLED` (cancellation via `PATCH /cancel`) | `credit-portability_api_cancelled-portability_test-module_v1` |
| `REJECTED` (requires CPF `87517400444` — [Gabriel Nunes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Data) | `credit-portability_api_rejected-portability_test-module_v1` |

### Payroll Credit Portability

| Outcome | Test module |
|---------|-------------|
| Happy path: `RECEIVED` → `PENDING` → `ACCEPTED_SETTLEMENT_IN_PROGRESS` → `ACCEPTED_SETTLEMENT_COMPLETED` → `AWAITING_CONTRACT_DISCHARGE` → `PORTABILITY_COMPLETED` | `payroll-credit-portability_api_portability_completed_test-module_v1` |
| `PAYMENT_ISSUE` (divergent payment amount) | `payroll-credit-portability_api_payment-issue-completed_test-module_v1` |
| `CANCELLED` by the user (`PATCH /cancel`) | `payroll-credit-portability_api_user-cancelled-portability_test-module_v1` |
| `REJECTED` by the creditor (requires CPF `87517400444` — [Gabriel Nunes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Data) | `payroll-credit-portability_api_creditor-rejected-portability_test-module_v1` |
| `REJECTED` by the proposer via discharge request (`POST /request-discharge`) | `payroll-credit-portability_api_proposer-rejected-discharged_test-module_v1` |

---

## Credit Portability (CPC)

| Status | How it is reached in the mock |
|--------|-------------------------------|
| `RECEIVED` | Set on the `POST` that creates the portability. |
| `PENDING` | **Not produced by the mock's automatic flow** for CPC. The status is part of the spec, but the mock's CPC flow goes directly from `RECEIVED` to `ACCEPTED_SETTLEMENT_IN_PROGRESS`. |
| `ACCEPTED_SETTLEMENT_IN_PROGRESS` | Automatic: `GET` 30s after `RECEIVED`. |
| `ACCEPTED_SETTLEMENT_COMPLETED` | Triggered by `POST /portabilities/{id}/payment`. The `paymentDateTime` sent in the payment promotes the transition on the next `GET`. |
| `PAYMENT_ISSUE` | Automatic on `GET` when the `paymentAmount` sent in the payment is **lower** than the contract's `contractOutstandingBalance`. |
| `PORTABILITY_COMPLETED` | Automatic on `GET` after `ACCEPTED_SETTLEMENT_COMPLETED`, provided there is no payment amount divergence. |
| `CANCELLED` | `PATCH /portabilities/{id}/cancel` — the spec cancellation endpoint. |
| `REJECTED` | Use CPF `87517400444` ([Gabriel Nunes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Data) when creating the portability — the mock automatically forces `REJECTED` on any `GET`. |

---

## Payroll Credit Portability

| Status | How it is reached in the mock |
|--------|-------------------------------|
| `RECEIVED` | Set on the `POST` that creates the portability. |
| `PENDING` | Automatic: `GET` 30s after `RECEIVED`. Does not correspond to "1st business day" — it is 30 seconds. |
| `ACCEPTED_SETTLEMENT_IN_PROGRESS` | Automatic: `GET` 30s after `PENDING`. Does not correspond to "3rd business day". |
| `ACCEPTED_SETTLEMENT_COMPLETED` | Triggered by `POST /portabilities/{id}/payment` with the amount **equal** to the outstanding balance. |
| `PAYMENT_ISSUE` | Automatic on `GET` when the `paymentAmount` is **different** from `contractOutstandingBalance`. In payroll the rule is exact equality (any divergence, higher or lower, triggers it). |
| `AWAITING_CONTRACT_DISCHARGE` | Automatic: `GET` 30s after `ACCEPTED_SETTLEMENT_COMPLETED`. |
| `PORTABILITY_COMPLETED` | Automatic: `GET` 30s after `AWAITING_CONTRACT_DISCHARGE`. |
| `CANCELLED` | `PATCH /portabilities/{id}/cancel` — the spec cancellation endpoint. |
| `REJECTED` | Three spec-compliant ways: (1) use CPF `87517400444` ([Gabriel Nunes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Customer-Data) when creating the portability — the mock automatically forces `REJECTED` on any `GET`; (2) `PATCH /cancel` providing reason `SALDO_DEVEDOR_ATUALIZADO_SUBSTANCIALMENTE_DIVERGENTE` — the mock converts it to `REJECTED` instead of `CANCELLED`; (3) `POST /portabilities/{id}/request-discharge`, which sets `REJECTED` with reason `RESERVA_DA_MARGEM` (proposer-side rejection). |

---

## Operational note

Since each automatic transition depends on **a `GET` issued after 30s** since the last status update, walking through the full payroll flow up to `PORTABILITY_COMPLETED` requires roughly four `GET` calls interleaved with 30s waits, plus one `POST /payment` at the right moment. The timers are counted from the portability's `statusUpdateDateTime`, not from the creation time.

---

*Conteúdo baixado em 16/09/2026, 15:38:12*
