# FAQ

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/FAQ](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP/EN/FAQ)
**Slug:** `FVP/EN/FAQ`

---

---
title: FAQ
---

[← FVP](FVP/EN)

# FVP - FAQ

This page gathers the most common questions about FVP, organized by theme. The answers apply to both the manual and the automatic arms, unless stated otherwise.

## About the tool

**What is the Restricted Manual FVP and how does it differ from the Open Manual FVP and the Automatic FVP?**

The Automatic FVP runs daily and automatically, covering DCR, DCM and the checks for every phase up to consent authorization. The Manual FVP, because it includes the full data-sharing and payment-initiation journey, requires the user to authorize the consent and complete the initiations. The Open and Restricted Manual FVP differ in a few modules available only to the Open Finance Brasil structure, such as validating the user's limits.

**I got a "Failed to fetch" message in the tool. What does it mean?**

The "Failed to fetch" message relates to an FVP session timeout, expected on long sessions or after switching browser tabs. It does not stop the module from running: just reload the page to keep following the execution normally.

## Notifications and closing tickets

**I received a Restricted Manual FVP notification ticket but I cannot comment on or close it. What should I do?**

Restricted Manual FVP notification tickets cannot be commented on or closed by the institution. Closing depends on a successful re-execution of the module, performed only by the vendor responsible for the tests. To request a re-execution, open a ticket under Request > Re-execution > Manual FVP - Restricted tests. For questions about FVP, open one under Requests > Information Request > Conformance > Production Validation Tool.

**I requested a re-execution. Since I have nothing to do until the result comes back, will my ticket SLA be affected?**

No. When a re-execution request is opened, the ticket moves to the "Awaiting Requester - Essential" status. Since the institution has nothing to do while it waits, the ticket gains an extra 24h of SLA every 24h. Once the request is closed, the status returns to "Forwarded to N2 Support" and the SLA is counted normally again.

**Instead of logs, I received a JSON with the message "DCR Error – Failure on generating a client". What does it mean?**

On every run, FVP registers a client at the start (DCR, Dynamic Client Registration) and deletes it at the end, since it cannot retain client information and the Open Finance specifications allow only one client per software statement. When the registration fails at the start, the module never runs and returns "DCR Error – Failure on generating a client", along with a log explaining the failure and a button to download it. While DCR fails, the module cannot be created.

## Test behavior

**The test did not finish: the status is "INTERRUPTED" and the logs show "Test was interrupted before it could complete". What does it mean?**

This message has two causes. Blocking failure: FVP found a failure that prevents the next validation steps, for example a failure in the authorization flow, whose code is essential to obtain the access token. Spontaneous interruption: the person running the test pressed "stop", usually after spotting a failure in the holder's environment that does not return an error to FVP. In that case, use the xfapi-interaction-id in the logs to trace the error directly in the holder's environment.

**The engine made "Delete" calls on consents or payments at the wrong point in the test. Why?**

The "Delete" calls are part of the Cleanup step. At the end of the module, whether it succeeds or fails, FVP deletes the resources created during the test so no data is left stored at the holder. On a critical failure, Cleanup may run preventively, before completion. If the test failed before creating the consent or payment, Cleanup may raise an error because there is no resource to delete; in that case, consider the first failure, which interrupted the test. Cleanup typically includes "Unregister dynamically registered client", "Deleting consent" and "Patch consents endpoint".

**After the run, I downloaded the logs and they were empty. Why?**

For security, FVP does not store the information used in the test: five minutes after the run ends, the logs are deleted automatically. Download them within five minutes of the test finishing; after that, the file will come out empty.

## Common error messages

To help identify and fix failures, below are the error messages most often found in the logs, with the likely cause and how to resolve it.

**40x on the DCR request - Client already present for this Software Statement on Server**

Problem: the server rejects a new DCR because a client_id already exists for that software statement. The client was created in an earlier DCR module and the deletion request was refused, leaving the registration active. Solution: check whether the DELETE request failed in any module. If so, fix the cause and delete the client manually using the SoftwareStatementID. If not, the problem happened in an earlier run; delete the client manually and wait for the next run to assess the cause.

**Test was unable to call the Consents API on test**

Problem: in the consents-bad-logged module, the POST Consents API could not be called because the Consent API URI was not provided in the test plan. Solution: confirm in the Directory that the Authorisation Server is registered with a valid Consents API for the phase the institution participates in. See the Directory Operational Guide.

**DCR is not being accepted because of missing optional fields on the request**

Problem: the server rejects the DCR because an optional field is missing from the request body. Solution: the server should apply a supported default for optional fields, ensuring the request is processed.

**Routine was unable to confirm within the well-known endpoint the supported token authentication methods**

Problem: possible causes include an invalid SSL certificate on the Well-Known, the absence of private_key_jwt or tls_client_auth in token_endpoint_auth_methods_supported, or the server denying FVP access to the Well-Known. Solution: use a valid EV SSL certificate, from a CA or ICP-Brasil; ensure compliance with RFC 8414; and confirm the returned JSON carries the expected token authentication methods.

**Server claims the authorization token is invalid or expired**

Problem: the server does not accept valid access tokens, usually due to a token cache that is out of sync across Authorisation Server instances. Solution: implement a fallback that looks the token up in the database when it is not found in the cache.

**Failure when calling the directory endpoints - Token or Assertion**

Problem: the Directory returned a 50x error when called, due to high platform usage during the test. Solution: no change is required; ignore the result and wait for a new run.

**Server returned that the client presented invalid certificates**

Problem: the server treats the credentials issued to the client as invalid, causing every test to fail. Solution: make sure the API Gateway trusts the certificate and the CA that issued it.

**State was passed in request, but is missing from response**

Problem: the failure happens on the redirect back to FVP. If the test user is not logged in on the mobile device's default browser, the redirect URL parameters are lost when the browser asks for authentication, because the redirect link is single-use. Solution: for QR Code runs, sign in beforehand on the mobile device browser that will be used, so the redirect preserves the parameters.

**Authorization response fragment is empty**

Problem: the authorization server's response returns to FVP in the URL fragment, the part after the #, which exists only in the browser and is never sent to the server. FVP sits behind an infrastructure login, so if the browser that completes the consent journey has no valid FVP session when it returns, the gateway forces a login and the fragment is lost in that detour. Without the parameters, the module has nothing to validate. The message "State was passed in request, but is missing from response" has the same origin. Solution: the message continues with the diagnosis for that specific run, and that is what tells you which side the fix is on. The items below explain each variant, which the tool emits in English only. In most cases it is enough to log in to the FVP in the very browser that completes the journey, right before scanning the QR Code: the login lasts 10 minutes from the moment you log in on that browser.

**Authorization response fragment is empty: the browser that returned from the authorization server had no previous FVP session**

Problem: the browser that returned from the authorization server had never accessed FVP, so it was not logged in. This is the typical case of a tester logged in on the desktop who scans the QR Code with a phone without having logged in to FVP on the phone. The gateway does not recognise the browser, forces a login, and the fragment is lost in that detour. Solution: the fix is on the tester's side and is immediate. Log in to the FVP in the browser that completes the consent journey, on mobile before scanning the QR Code, then run the test again.

**Authorization response fragment is empty even though the browser's FVP login was still valid when it returned**

Problem: the browser returned with the same session it already had, with no new authentication. There was no login detour, so nothing was discarded on the FVP side: the fragment arrived empty because it was sent empty. Solution: this is the only variant that points outside FVP. Check the holder's authorization server redirect, which most likely returned the response without the expected parameters in the URL fragment.

**Authorization response fragment is empty: the browser's FVP login most likely expired during the consent journey**

Problem: the browser already had an FVP session but returned with a fresh login, meaning the login expired in the middle of the consent journey and the gateway asked for authentication again. The fragment is lost in the same login detour. Solution: this is also on the tester's side, but because of timing rather than forgetfulness, and the fix is one of sequence, not configuration. The login lasts 10 minutes from the moment you log in on that browser: log in right before scanning the QR Code and complete the journey within that window.

**Authorization response fragment is empty, although the returning browser was already logged in to the FVP**

Problem: the returning browser is known to have accessed FVP before, but whether its login was renewed on the return cannot be established. This happens when the reference record is unavailable, for example after a service restart, or when that browser has made no request other than the return itself since then. Solution: the message presents two hypotheses and deliberately issues no verdict, so as not to accuse without grounds. Address login expiry first, since it is the more likely one and the one the tester controls: run the test again, logging in to the FVP right before scanning the QR Code and completing the journey within the 10 minutes. If the failure persists with that window respected, investigate the authorization server redirect.

**Authorization response fragment is empty. Ensure the mobile browser is authenticated to FVP before starting the test.**

Problem: this is the generic form of the message, emitted when there is no information at all about the browser's login because the request did not pass through the FVP gateway. It shows up mostly in the Conformance Suite rather than in FVP, and it reads as a warning, not a diagnosis. Solution: ensure the mobile browser is authenticated to FVP before starting the test. If the problem persists, close all FVP tabs, restart the browser, log in again and scan the QR Code once more, or use a private or incognito tab.

---

[↑ FVP](FVP/EN) · [◀ Release Notes](FVP/EN/Release-Notes)


---

*Conteúdo baixado em 16/09/2026, 15:37:37*
