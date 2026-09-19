# CIBA Flow with the Mock Bank

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA-Flow-with-the-Mock-Bank](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA-Flow-with-the-Mock-Bank)
**Slug:** `CIBA-Flow-with-the-Mock-Bank`

---

---
title: CIBA Flow with the Mock Bank
---
CIBA (Client Initiated Backchannel Authentication) is a decoupled authorization flow: instead of sending the user through a browser redirect, the authentication request is delivered out of band and approved on a separate channel. In this guide the **Raidiam conformance suite** plays the client (the receiver) and the **Mock Bank** plays the OpenID Provider and data holder. Token delivery is **ping**.

This page gives guidance for the CIBA **happy path**: the clean asynchronous flow with no fallback. The suite registers a CIBA client for you on each run (dynamic DCR) from your software statement, then deletes it at the end, so you never register a client by hand. Because the suite does not drive a browser, the consent is approved **by hand on the Mock Bank screen**: the plan pauses and waits for a human to approve the request.

## 1. What to add to your software statement

This guide assumes you already have a sandbox directory organisation and a software statement that you use for other plans. You only add what CIBA needs. You do not create a new statement, and you do not do DCR yourself.

- **Roles**: the statement must carry `CONTA` and `DADOS`.
- **Redirect URI**: add the suite callback `https://web.conformance.directory.openbankingbrasil.org.br/test/a/<alias>/callback`. Registration requires a non-empty `redirect_uris` even for a CIBA client. The `<alias>` is the value you put in the `alias` field of the test config.
- **Webhook** (`software_api_webhook_uris`): add `https://web.conformance.directory.openbankingbrasil.org.br/test-mtls/a/<alias>`, with no trailing slash. The suite matches this value exactly against its own mTLS base before it runs. This field holds a single value, so a statement can point at one environment at a time.
- **Transport certificate**: use a **BRCAC** certificate. An organisation with the `DADOS` role is not allowed to use a plain `TRANSPORT` (rtstransport) certificate. Generate the BRCAC in the directory and keep the private key: it becomes your `mtls.key`, and the issued certificate becomes your `mtls.cert`.
- **Backchannel Client Notification Endpoint** (the directory field): leave it **empty**. The suite builds the notification endpoint itself as `<mTLS base>/cb`, and the Mock Bank accepts that value inside the DCR body.

## 2. Select the plan

Sign in to the conformance suite at `https://web.conformance.directory.openbankingbrasil.org.br/`, select the CIBA Customer Data happy path plan (profile "Phase 2 - Customer Data - API Version 3"), and fill the config it asks for in the UI.

- **Do not pick any variant.** The plan already fixes all four: `openbanking_brazil`, `plain_response`, `private_key_jwt` and `pushed` (PAR). Setting any of them yourself returns HTTP 400 ("already sets this variant").
- **DCR is dynamic.** The suite registers a fresh CIBA client from your software statement on every run, adding the CIBA grant type, ping delivery mode and the notification endpoint, and it deletes that client at the end, even when the test fails. You do not pre-register a client.

## 3. Run it

Start the test in the suite, then approve on the Mock Bank screen when the plan pauses (section 4).

## 4. Approve on the Mock Bank screen

The plan reaches `WAITING` and asks you to complete the CIBA authentication. To approve:

1. Wait for the test status to become `WAITING`.
2. Open the block **Call the backchannel authentication endpoint** in the log and copy the `auth_req_id` from the `/bc-authorize` response.

   ![image.png](uploads/b3ead387044ef82ef31f61dc653e22c4/image.png){width=526 height=172}
3. In a new browser tab, open:

   ```
   https://auth.mockbank.openbankingbrasil.org.br/ciba/authorize/<auth_req_id>
   ```
4. Log in as `ralph.bragg@gmail.com` / `P@ssword01`, toggle **I consent**, and click **Confirm Consent**.

> **Timing**
>
> Approve when the pending log line appears, not on a timer. Approving too early consumes the grant during the pending polls and shows up as `invalid_grant`. The approval window is fixed at 600s (`requested_expiry` is ignored).

Once you approve, the Mock Bank sends the ping to the suite on `POST /cb`, the suite exchanges the `auth_req_id` for tokens, confirms the consent is `AUTHORISED`, and polls the Resources API until a resource comes back. The registered client is then deleted.


---

*Conteúdo baixado em 16/09/2026, 15:37:11*
