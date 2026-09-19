# Registering against the Mock Bank (DCR)

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-(DCR)](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-(DCR))
**Slug:** `Registering-against-the-Mock-Bank-(DCR)`

---

## Registering the created application with the Mock Bank

[Portuguese version can be found here](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Registering-against-the-Mock-Bank-%28DCR%29)-(PT))

Supposing all the steps presented on the [previous page](https://gitlab.com/obb1/certification/-/wikis/Discovery-of-the-Mock-Bank) have been correctly done, the client can now be used to execute a DCR against the Mock Bank. The steps done on the previous page are noted down below:

1. Created a Software Statement (S.S.) on the Sandbox Environment
2. Assigned the needed regulatory roles to this S.S.
3. Obtained the keys related to BRCAC and BRSEAL certificates issued by the Sandbox Directory PKI
4. Obtained the Mock Bank details on the participant directory

The Existing Security Specification provides a full guide related to the DCR process that can be found on [Chapter 3 of the TPP Guide - Registering the application with a provider](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/tpp-user-guide.md#30-registering-the-application-with-a-provider). This guide has been built based on the [Open Finance Brasil DCR Specifications](https://github.com/OpenBanking-Brasil/specs-seguranca/blob/main/open-banking-brasil-dynamic-client-registration-1_ID2.md#regulatory-roles-to-openid-and-oauth-20-mappings) and should be followed by the user to allow the client perform a DCR against the Mock Bank

The Mock Bank is configured, [and also has been certified](https://openid.net/certification/#FAPI_OPs), to supports all the 4 FAPI Brazil variations (private_key/mtls) and (by_value/par). This means that any TPP that supports one of the FAPI Brasil variation should have no problem connecting to the Mock Bank.

The execution of a DCR against the Mock Bank can also be seen on the video [Mock Bank - Execute a DCR](https://www.youtube.com/watch?v=9e0CVxsAVwA&t=2s&ab_channel=OpenBankingBrasil)

## Example of a DCR done on the Mock Bank

To make sure that all Authorization Servers on the Scope of the Open Finance are correctly following the security and DCR specifications, the initial structure has commissioned, together with the Open ID Foundation, [test plans for the Brazilian standards](https://openid.net/fapi-op-conformance-testing-certification-submission-overview-for-open-banking-brazil/). These tests not only allow Institutions to test their implementations, making sure that they are compliant with the specifications but also serve as a way for the central authority to guarantee that no Institutions will be able to share data without being compliant.


The execution of these tests create public logs that can be reviewed by anyone interested in the steps that exist on them. 

We can then leverage this tool to correctly execute a DCR against the Mock Bank. On the execution of the test [fapi1-advanced-final-brazildcr-happy-flow against the Mock Bank](https://www.certification.openid.net/log-detail.html?log=l7dSstpmBVFxGbW&public=true), it's possible to check all the steps involved in correctly executing a DCR against the Mock Bank.

On the Open ID Foundation website, it's also possible to consult all of the tests executed against all of the institutions that are currently on Open Finance. This information is displayed on the [FAPI OP Certification Page](https://openid.net/certification/#FAPI_OPs) and also include all the FAPI Tests done against the Mock Bank




---

*Conteúdo baixado em 16/09/2026, 15:38:26*
