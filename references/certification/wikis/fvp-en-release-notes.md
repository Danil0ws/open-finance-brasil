# Release Notes

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Release-Notes](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/Release-Notes)
**Slug:** `FVP/EN/Release-Notes`

---

---
title: Release Notes
---

[← FVP](FVP/EN)

# FVP - Tool Release Notes

This page gathers the FVP release notes, recording the relevant changes to the tool and to the test plans. Entries are grouped by year, most recent first; each year is collapsed and opens when clicked.

<details>
<summary>2026 - 16 changes</summary>

**21 Aug · Plans** - Open payments end-to-end plan v4 retired

The end-to-end payments plan in Open mode is no longer offered in version 4. With Restricted retired earlier in August, version 4 is no longer offered in either mode; version 5 remains available in both.

**21 Aug · Plans** - No-redirect scheduling now validates Payments v5

In the no-redirect payments scheduling plan (Enrollments v2.2.0, Restricted), both modules now check the consent and the payment against version 5 of the Payments API, and their names end in v5.

**13 Aug · Behavior** - A failure to fetch the Directory roots is reported as a Directory problem

In the certificate chain validation, when the Directory roots cannot be fetched the test fails pointing at the Directory. The roots are read once and reused throughout the run.

**04 Aug · Plans** - Restricted payments end-to-end plan v4 retired

The end-to-end payments plan in Restricted mode is no longer offered in version 4. Version 5 remains available in both modes, and version 4 remains available in Open mode.

**29 Jul · Logs** - Service Desk block in the test log

Each run now carries its own Service Desk block in the test log. It shows the ticket lookup, how many candidates it returned, which belong to the same Authorisation Server and which survived the executed-module, segment and status filters; every call made to the Service Desk, with method, address, body, status code and response time; and the outcome, with the number of the request opened, updated or closed. The last line summarises the run as Authorisation Server, brand, module, segment, time and action taken. When a run moves no ticket, that line says why, and the block only appears when there was contact with the Service Desk.

**15 Jul · Messages** - More tolerant reading of the Directory roots

The certificate chain validation now accepts the Directory roots response in list form and ends the module with a clear message when the response cannot be parsed.

**13 Jul · Documentation** - FVP documentation restructured

The FVP documentation was reorganized into per-plan pages, in Portuguese and English, with one spreadsheet per plan.

**09 Jul · Form** - Simplified configuration form

The plans' configuration form stopped showing the fields that FVP does not use or fills on its own (logged-user and business-entity identification, Directory discovery and base, keystore, publish and alias), leaving only the fields the participant actually fills in. The CPF and CNPJ help texts were also revised.

**03 Jul · Plans** - Payments E2E plans v5

The end-to-end payments plans gained a version 5, in the Open (Immediate) and Restricted (Scheduled) modes, with the corresponding modules.

**26 Jun · Form** - New run fields in the configuration form

The manual plans' configuration form gained the run fields Type, Cycle and Service Desk Ticket, used to identify test and retest runs.

**25 Jun · Interface** - Manually ending a test as failed

The tool now offers a control to manually end a test as failed, useful when the holder's environment has a problem that does not return an error to FVP.

**18 Jun · Behavior** - Scheduled modules restricted to their schedule

The asynchronous modules of the Restricted Manual FVP now run only on their schedule; manual execution was blocked, preventing triggers outside the multi-day flow.

**18 Jun · Plans** - Standardized plan display names

The Manual FVP plan display names were standardized into the Open (Immediate) and Restricted (Scheduled) modes, making the list clearer.

**20 Apr · Plans** - Optimised Journey

The Optimised Journey was added to FVP, with the corresponding payments and enrollments plans.

**03 Mar · Plans** - Client deletion plan

Manual FVP now offers the client deletion plan, in Scheduled mode, covering the termination of the client registration with the holder.

**29 Jan · Plans** - No-redirect journey plans

Four Enrollments API v2.2.0 plans covering the no-redirect journey were added: payments and automatic payments, each in Open (Immediate) and Restricted (Scheduled) mode.

</details>

---

[↑ FVP](FVP/EN) · [◀ Client Management](FVP/EN/Manual/Scheduled/Client-Management) · [FAQ ▶](FVP/EN/FAQ)


---

*Conteúdo baixado em 16/09/2026, 15:37:49*
