# Credit Portability MB

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-MB](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Credit-Portability-MB)
**Slug:** `Credit-Portability-MB`

---

---
title: Credit Portability on Mock Bank
---
# Testing Credit Portability Against Mock Bank

The Raidiam Services Ltd. Mock Bank — hereafter referred to as Mock Bank or MB —  is an implementation of several Open Finance Brasil APIs, including the Loans API and the Credit Portability API. Hosted on Raidiam servers, it provides a controlled environment for testing and conformance validation. MB replicates the behavior of the APIs but is not connected to real financial systems — for example, credit portability flows are fully simulated and do not result in actual transfers between institutions.

The Credit Portability API is fully implemented and functional in the Mock Bank, in accordance with the latest version of the [Open Finance Brazil Credit Portability API](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/905740587/PC+API+-+Portabilidade+de+Cr+dito+-+CPC). 

As the Mock Bank is continuously evolving to support the latest versions of the Open Finance Brasil APIs, institutions may encounter issues when executing tests. These issues can be related to both dubious specifications or because a Mock Bank behaviour is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team. Be sure to include:
- A brief description of the issue
- The test environment used (e.g. Conformance Suite)
- The `x-fapi-interaction-id` from the response, if available

# Example of Valid Test Configuration

The following JSON object should be placed in the JSON Configuration field in the Conformance Suite configuration page:

<details>
<summary>JSON Configuration for Credit Portability</summary>

```
{
    "alias": "obbsb",
    "description": "Credit Portability",
    "server": {
        "discoveryUrl": "https://auth.mockbank.openbankingbrasil.org.br/.well-known/openid-configuration"
    },
    "directory": {
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br/",
        "client_id": "984e85a9-9001-40eb-97b3-194f5afbd956"
    },
    "resource": {
        "consentUrl": "https://matls-api.mockbank.openbankingbrasil.org.br/open-banking/consents/v3/consents",
        "brazilCpf": "76109277673",
        "brazilOrganizationId": "b961c4eb-509d-4edf-afeb-35642b38185d"
    },
    "consent": {},
    "browser": [
        {
            "match": "https://auth.mockbank.openbankingbrasil.org.br/auth*",
            "tasks": [
                {
                    "task": "Login",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "text",
                            "name",
                            "login",
                            "ralph.bragg@gmail.com",
                            "optional"
                        ],
                        [
                            "text",
                            "name",
                            "password",
                            "P@ssword01",
                            "optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//button[contains(text(),\"Sign in\")]",
                            "optional"
                        ]
                    ]
                },
                {
                    "task": "Consent",
                    "optional": true,
                    "match": "https://auth.mockbank.openbankingbrasil.org.br/interaction*",
                    "commands": [
                        [
                            "wait",
                            "xpath",
                            "//*",
                            60,
                            ".*Before proceeding, we need to confirm some information:*",
                            "update-image-placeholder-optional"
                        ],
                        [
                            "click",
                            "xpath",
                            "//input[@id='consent-toggle']/following-sibling::div[1]"
                        ],
                        [
                            "click",
                            "id",
                            "continue-button"
                        ]
                    ]
                },
                {
                    "task": "Verify Complete",
                    "match": "*/test/*/callback*",
                    "commands": [
                        [
                            "wait",
                            "id",
                            "submission_complete",
                            10
                        ]
                    ]
                }
            ]
        }
    ],
    "client": {
        "jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "d": "Q9gSOfnkGJnAsV3a94j9ae9ihjqgMwXgVm73VTyEs1u9Jq73pCWX0e9JdeNMKdgKpiJYjyxa3ttxCY58eiGKEi7c50zYRx8YLTL2rIVWqS6JVGpXuzIQutkQDM4AfD72bG3-xT-caSCansGbdEIFJjX32Ujbs1UUoQlE96m3hNOjB5vNyHBWrBUgUGG9_uJiWFG6Lbj8ZGtiihA_PQkzuArLzDvO2OMVHCzIyQ4CwFE1tI9xHFHpioJQXBnymURQvkm3MmEwHRG_KUdABQ55gG32jothy7jOOYAMkvOCejteTZv1nT4dsEj-CBxDBtTI6SerXb11VX8b0suzSBxx0Q",
                    "dp": "S15AOPpOtYgYjfOi2rNojY3NpU-Qobnfnnt_MZEJ2_DS0bGwXSgGJjHOOOAowy1HK0n7-AhXbwhr026sBuicR_Kpj6RkzGVrJug8y9R02FXZwlQpgjSBZdO6C2B1OOvtyKmnKg5q1KdQ7Kx6vYPV7UutOJn6NlH0RbFgG4NGelk",
                    "dq": "oBgBMB54mtrriQCg4YyDY_zf7LW4f6oqiUl3l7odf_ArjVamjHM-boZnhGoVzZ5uXNs03wEdBIc2HLmsoGLVuodcYHjyptmvyPebiH2mavFlUlI8ILG6lkyIhMp3Ri8iXGX2MYlPjP2EawNDMHB6BO0bZ5NugyzxuF_OKhfEFLc",
                    "e": "AQAB",
                    "kid": "-duNE0ZX5NmDkUlgNoqDY5Ve7UdFTA7S25WJSAv8tNQ",
                    "kty": "RSA",
                    "n": "-6Ep5kV0qcQnrxQzbEgMGKQRHnhXlp3ZpAVqQbbzkVG_a1tHLi0V7YAmjf3isXMvdvWjApeShL32gqxgcKDvC5Mnd5ufR1ujzb5lsnYXy-tKMQWnAlCqy7mSuxi8JIBXyZb7CMGU29L32Tvd5MjDh_hSgwnHcTggE-ehqzK5eyvK7DjvlbfCKXgDx94kMcwyI2K0EurahHj9_I3lEQzAt73OocF_z84FQxO87A8Q1cM3nEGyykZPaFyulQ4bf4U2tT_Jfd0ppYX1j194ouPeqMZBsGnxKf4L4QvuberbRpdeOO92HhWHHiwiTuhYxF876-LKgPzqxK-Y1a2_4gsVAw",
                    "p": "_oebNFofSe_8fdotMxUEk7n3pq5eT96rO_VPdHyTZERDrkU0djQf9BLy7DejYoRReuI0AJWkBL9EGBhECaowmx8gTCs43ffQrBDULYB4elmS07ov1pq1STqzqRKbu_INaSGVgxFzhYC_EeFVpB0RPlAUvb1_aQkH79J8VMnp2_U",
                    "q": "_RVEyO9NB6XiJjMz9t6XrNxG01Vguo2VVBLaDJhoi1g7gydUDkNc9twhF1Ifps8Gf3m9aMjjOmYqE5kuWCPBHxkk8cZOm4C2AhVbQxMkZLOyPeJDfKfCi7yJRIfmwqQM5AKosALfN-jW_p746lRhCAps8eH9XF6bjugi_MH1yhc",
                    "qi": "yXG_vCx0xL9DlU7f0Ixub9NSD1QJtAJYxwKyHukw_8f4rHLiZ8eeCerfZfPd7zsPGSqOmY2605MNT1Z2ohYgoRyu05uwstEDKqtgl_uxupfO6AJKCja4paIB-ICvQQXpOY1n9BW6VcDwSylTnv1pKvVnTvxzy5z008wvrafQtFw",
                    "use": "sig"
                },
                {
                    "kty": "RSA",
                    "alg": "PS256",
                    "use": "enc",
                    "kid": "e96744c58188c084310920b152ffb02a392b119a009fb1fa1a656006715e1604",
                    "n": "4eIXvOR1XXo3MT9syMwRZj2ChbV2Qlp_623VCIhYvPtJ5k5rlCr1hP4n0PC49U47pa3UKNs6DYHefHKm9I4h4crgk7zsln2_JP3kK1equqIO1U12Rv4Xbm_2_eqR3hPKcE3il2ky2Neby8OThFnyDwBNKdxI4MvOKm910qQhYns2L4w_i9fjF2z1Wpi6sMPW8IERhkqaBWgoaH9g2obGbNuoYCzEjOWvRb_nVjYKRPqTI2A11kWZ4mVTRkTO4yM1gdI7z8Hsl4fqlEXeVdmMkVJhRvQa-vFfegecgO8nUY2XoOUx_UR51F8PO9bepy-jH16cRDwjLE-2ex7mE_wfMw",
                    "e": "AQAB",
                    "d": "BqovoVF4vww8nA9IuLhnHDlDZFbHov4qZeCecQgcEJNpIxdiqDZuR4EvECsSIgOWOFvwW-lzOI1oHaVNlMvezXU5eoWpnpuEnzHlYHwCzxftNrde5PBZWHC-sAMStvBzJpLw7riNZgWFx_wNmoTQfHqgGQfLyxcB9Pf6v387qiN1wHfSXQshtFiDg_6tBaH6dS1jRAg7_56dQp1wWJeRaqMCg9QeESmo3c-76hnRSMU6fgrONU6qGMSLopv-nirh3H1gZePcXzVgf9cerRMQgV1pWUZEd_iJqTaX8U7wB0txmVF6QzRxR71Ah6nZuV_Rv7X88zB8u0rXOvjeGtuZKQ",
                    "p": "8fN0GXyZnvxba4yoOgdL9ta9pkjjWVu5eTOIyvSgKf09hUSWKL6sKm1N0l68detwzBFpnxObOeUCMnU_BFhJM-s0w5GognaAX6GB5-TzdYHwmsgqAch3-_hi_kZU6A-SLZu7bQFGXTEotQ1zMxVuCMZ7AjTs0CGZrS-vItFYtik",
                    "q": "7v_Ldwh3L9On2CNAefLgs7dyDBAgWrkXOJ9Z1EnrKgMHbqgq5dOixv2ezKNdOUte9G4ve555XTf2sC-p0TF9PNYC0_4KthI8NLik8RtDsQmYJUYw7qfV_YitzGflM2DRr6KaV5SmO_aPWRfzuVWh_6kIQ_GmXf47ASasKVeD_fs",
                    "dp": "Jyi-_q0C9A9mAHcodxPdQJsq4LHlUf4de7dSiX6kOYeKIHqkTv3lQYylTsoUeIVdoTmkPaHfurQM8fu18k8Tsfp8dLarbkodptyt-Mk-eiNIvNRusBExEi_2Xa8maNS0VPtij1boe4bMTtlZbsgmIfd1yzqjpV_6zmPsVZdKY1k",
                    "dq": "qjW-YA3FZGhmtwWUG8Wfxh41uOWbRUFgilDils_2DTuPBX363yc0XGevuqn18KH_BDGc23tnj74VkDDBzlxihvsblILuefDOs_V0csoqEWF128X7f1xEiIXY0SSFFWw0qdMx_IG_SiE0wgzO5QVZlEx7uHfXNkWjHBTAs8jCFhU",
                    "qi": "8W2vDdiA8qDxL2fiJPP2m3NqbjGW7Tf5PsfGo0Gqfv6nWVweuVwsyUNT1AYduZUCvFRG5LRNHqiwZNpNB6XQln1W41GaIqGkHWJkveHhg9xIQmSK2hrX4OnSdyvMiGiB2yvce0FTgQ0OzXuNkIKJKJLP2nAJusNgNcVT7qgKCRA"
                }
            ]
        },
        "org_jwks": {
            "keys": [
                {
                    "d": "BpgLagicLjysglxtDX7bJnOv4-IP-5yyGdL4oOkDCl_-lO8twPDhWLfXNCf2QTs7l1T1GLNUyALKjYDNEvjbpu03_K1dtRwO2ZS4_VHTPhe99Etn1GXntdfcFvQiD9Lz6uzs2-0DOIG_5xWUiVhTUN5HPRfMMXF3ktG2ucTOQqsJU0O2SOohVIvqYH4EDJNIw8qUsu1C2JEDMj79H_8KaXEUVx8tFFLMxmt67a_a7sImXvEaIYhUCu-DMMDrzBc660s_eTcihJ_DkJgYPPWctnmpUClKa4zgABDqGXhPQFfLS4ywGAHnLZF1MyNeKFXpmeJShjNJ5MqjBKJTnFHDQKs",
                    "dp": "CFfrENWCU61YHATfdTy73lt2reMz0dBDicy92s4FqHpcup6O6f5MWGvhpBlLVC-tNA97qzyKExFwxl6c6rf45l8T6GLjy4C2DJEH0pGKeh7-PP7XW1KBvsclbJdSoSj-bOFRomFVGKYhIF3nRnr9-Dvj1k8aEcClPT1E9i9rGI7P",
                    "dq": "BzCeCJQ9pKQVCpyFi50PR8_E7d9uW9nYqJpf0GBT5XdnZ44qnliLAffZmVwcxXh6e_JzIjC0ByJrYKd_dekXLCrsOex1XxqvI7WH6EZ3Nvoe_1835ZgtQ2PsPSvGKifHHPXocKyqqRdT7KlGTXfnpKtezsXPxe63VS-3coE62-_F",
                    "e": "AQAB",
                    "kid": "EKSYJfNcI8Bm22_dP0ziWpTjw9UceAdVjykgwO5BkfE",
                    "kty": "RSA",
                    "n": "oBp-b0EhezRYfisJBL_WA2Yh0Y2zPYHsy8N4G9mddkop-kFJT12XSSBx8GXmyjDL14Wg5vRNA6R_TwXbJbnHnE59uMYiWNi_G7OL6jMsncmYdyBuwl-lDWExaXC5Qg9vYgGnt7d1SthQoiJkduPIiNpniq5p7px-jJYQO4SECUqpeLl9rU_Xvxn5zpFu4dw65wBi4oSDiJ0zujQtxofOmbJCKYTWrPmd8yPlPgwIttP2ZcprMs5Ya57-99NhAealcVptRTOQTEWEOflmurq58Byu7pT64ns-9Su8JPcHMMzxOOVM7KNPuZA7Xa5-1aBd1XrhxkBHIDzUqOpanSlr2uk",
                    "p": "DgL5bOQ5-JXM6Ed_3BRKW2a3EcHB_UjlWPlGGkc0RBeEwlNi6D3PQGZmgTxyGXWA4W3HMi2S2pXx8oxWd9rrw9Uc_BNrIdvkMcU9LnkCvxK-dcHalVrXhv0l1EbQx0mG9LjLsiqmJiJYnUYTuLjO8lJaebSTp-EH2fgTs81_SBKv",
                    "q": "C20t29WtF9yAXt2r5Yu7chtrJUMIsu_TUY2N6p75BWWBB76oNib4Dp5fVePnbTqdSP913dS1K1vHwEAqS_Z_C6vfmaYha6Hguipo5jotTTJoYDxV_xTp1dGWcr8MltBE9ikhLa8xvGVxXjSi4vkqc_TyXlBSHbbBSZtjB32rCLHn",
                    "qi": "BRx-2fqZYWrIzcayN1v10HfzcQaZue-NNZP7Eid81oBBxBrDQmiGdzQLi0BKctjLBr21_GWUgHgEYRym3He5biuDVM0WnyhXYeLLc_pv3bIG6FoPrP4XDZo4GTM4JdVj2im_OQWdXuokFzsZzeVV6H8p46TxpyNDix5oFjmyuB11",
                    "alg": "PS256",
                    "use": "sig"
                },
                {
                    "p": "2a8fRJ7ybF-qtF1zrYzSm7z3C4wNTUMbVYqe44tR9FbKsobqW2tS0iAZf-GJ_SZPcWxkE76gunW7YqMJecGUtXsJ8TTHwjcPQOMYzxnyJu8Q4JOj01YJVrxUY9D0ZzpWM9oTAj1-qoE0w7Dy-XNUc14-HeRlmOkg2tTfrXTVR8c",
                    "kty": "RSA",
                    "q": "0xlPJFRUcBU5j2SKSajVnd4H5p88RSsd4cArMby1ZRuSeHEsX76c6QKAPq7uTfKrTeZic34yzAEUyHloP1fZQYQ2UQn-f6PsTAWdT1Lp5oi2VZCT0yc9-1EGnLAiUCbM9SQQyf2GIVhCiAk_0VuY6le61Pw0U4GssvFJzIrx4as",
                    "d": "GxnizpWcqL1wajD8-Y-8H9-II4UZMKfkgbfwRiLK9uAd8-kEJdO9jdNeMxyytg2saDhxNTeRTkYz_VbBf3p9dGhuYx84d-ZagUbIiU3ho3FCsBRrzQQZw9OQrzPDUzp0-SBn1_GLCf9fo4ysxWHbn9euJVi2fpN_bHlBi1n8fKhdBHYE7X3XJnRYrUXItxZw5sJsqM_boONLxdLAvgmZx5CHft94JZsR6JPwlj9Ba_CuNWX_3OuUGyV0f5_1ICAEYijw9PA8KAW6t5UUYn39_KYL8nF5L1Bh6W1j8eN84I2lcKZNO6Pou064ag_wqGhk4uXuQO1IV8jRFn3-pqhSEQ",
                    "e": "AQAB",
                    "use": "enc",
                    "kid": "c1d7b80ce4b88c4f2cfb68e7a8c45bfff355ae94259bc1a73a95ddbaeaf7c96b",
                    "qi": "pU1IXwiQoFERdzJsx7kSC79Gwhak7uw7OAJCbcfkKE3GSwTWHrKfg5uDZlNvSnNU1Hbpxd0bgc40dFI2aNBML1gyDwTjQplWVJikkFix8E6z_ErSa_D5w5yV4k6CNtt7OzlMXawiZ-ndcuiOs5MkfSRyeB3k5rQmuZjLVzFFlnw",
                    "dp": "Gn4dqBRQHLBn7huRgIWq_Bk7V8RrugN4yChevgKurrYBZUjWLNoa8kfF0rJ4QL7w3DT82QpSNV8utwpwlMjieFPJGfn6dcCNsq_wzQOzXNmrjClrvsSxzkSNYLiFhiqrYxQfTB5_0_B1o3tdls5acM__b1PkqX916CwQLOQTMPE",
                    "alg": "PS256",
                    "dq": "NS0x94fawWVHW6zK_SUvspXkzZ6dMxtaaqza9KuB0ldwvTBdKj09D6FWpvOwCiiwKG55rHhE2YkIMDwNG6_Iha2FdUKcPpEPjFL5vqq3SyBzNfi2lEFVZsKRdNUVv7UWekY8iHV53Vp7YANcdSOq0JWK9e4WTFblJyqLGaCCsAM",
                    "n": "s4DcK4uxKroJPE1R7Te4ppNexbuK3C-Z3MpXFr5hmY43gYIoVMo89jE6OcDiO0Z4rxe8dsH4oYA2vAJQ0IhAaUxYMk2kN01ei761zMQWHLUPLcEKWgipYHy4AgwAUaF7-Glyb0DT1RRcY4f1tEddftxhwXZjeFduj6luVg6fVvXRIRjttybUkIKvf5ShMofVFCF_IyjYlOal4g3DVnCg62dR71WX3fRXSufxrRBG-L61rv2VSMg8pIb1DFiYKDlEXEnTdLk-7goBpTIz3wBsrZgJESSZOn_BG_-fCE0V75rheLMuJd4IGE4H0taVfEQOJKRKBVzc2jAz0sOaVuPY7Q"
                }
            ]
        },
        "client_id": "Jj-hosRwYqvtnQZNph2Ah"
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHQDCCBiigAwIBAgIUOyyDtirdgYQIT/eSBtvaP5JRcoswDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjUxMTA1MjAzMjAwWhcN\nMjYxMjA1MjAzMjAwWjCCAUoxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJVSzEPMA0G\nA1UEBxMGTE9ORE9OMSYwJAYDVQQKEx1PcGVuIEJhbmtpbmcgQnJhc2lsIC0gUmFp\nZGlhbTEtMCsGA1UECxMkYjk2MWM0ZWItNTA5ZC00ZWRmLWFmZWItMzU2NDJiMzgx\nODVkMUMwQQYDVQQDEzpodHRwczovL3dlYi5jb25mb3JtYW5jZS5kaXJlY3Rvcnku\nb3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMRcwFQYDVQQFEw4wMDAwMDAxMDc0Mjg1\nMTEdMBsGA1UEDxMUUHJpdmF0ZSBPcmdhbml6YXRpb24xEzARBgsrBgEEAYI3PAIB\nAxMCVUsxNDAyBgoJkiaJk/IsZAEBEyQ5ODRlODVhOS05MDAxLTQwZWItOTdiMy0x\nOTRmNWFmYmQ5NTYwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC8bzfe\nH4l2IegWdHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao\n49DYEbaR5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaq\nMIRL9RCqDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VN\ntbT3v+STfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBh\nJmGD96kmJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyC\nwnl0XQQnwjQKKConAgMBAAGjggLrMIIC5zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQW\nBBTLmBupVqnHkdd6f2hhj5mRrTUZnzAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0e\nsdbER0IoPTBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwRQYD\nVR0RBD4wPII6aHR0cHM6Ly93ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5icjAOBgNVHQ8BAf8EBAMCBaAwEwYDVR0lBAwwCgYI\nKwYBBQUHAwIwggF0BgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB\n9QYIKwYBBQUHAgIwgegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3Ig\ndXNlIHdpdGggT3BlbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2Vydmlj\nZXMuIEl0cyByZWNlaXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBh\nY2NlcHRhbmNlIG9mIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2Yg\nQVBJcyBDZXJ0aWZpY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRo\nZXJlaW4uMFgGCCsGAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2Fu\nZGJveC5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVz\nMA0GCSqGSIb3DQEBCwUAA4IBAQAjJQE5R9iYGgnrEpEOUGNFVqHYs8L8Y1quoglO\nYsz1GhC2bzm7WSo7iRXfil5D8om6BDM+2TsMkvH21yeNnIclIrK/ReDHqkubbWoa\n9awJDNVa6VoNRdCB6dqEiLwZl4p+bacoShQCd113v5B76gVyCPBmId41rDJv/beB\nv7F894KM4LMMkkZGSnrGft9fc8Y2CPN452EgnTh41PhJHK8DVw8mtx704gblJ64B\nwqhogdzyAjY1uz+a3M1gTTCkEEkuhYXYrHDXgz327JRCW2oXKj7oMMszMI5E4uYL\n/QQijgFOoCPdX+/SvXZo7uMl0dtegLOR/oHxOwLuryqBk9mG\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQC8bzfeH4l2IegW\ndHsOIooz+nUxpfI5v23ubPsB0P9rLEoPlIn0A7E2zg/b7UCQFvzmzgao49DYEbaR\n5B5rutlRn52rkHufNF2fNEGXgtqrko/Uwf2tGDpve+e6MRuXhyYUEwaqMIRL9RCq\nDSTHFUS+QoNaPdccw9yAQkffEckKoXJA5GYkLvkZ06Vh8R7L6Agjh1VNtbT3v+ST\nfrIbSYcEXJoHwWn7vnSewcJm3B1yxpKAVySFbL336yu0cYU8RkZ42SBhJmGD96km\nJ+vuTXQBs5ZTndbZo6/UO+r3+qaQ8rK1r4qeEYaOwSYh9wsFxpLJIgyCwnl0XQQn\nwjQKKConAgMBAAECggEAJwYvf0hvuu/dtVzNKUm87nPVtoEED7KV7TVTrHYgl4z2\nD5D3GvpyxoNZZHYXk1+3Y4NSfMKle0H72e3w4OWy4QUZ7bB/8aIyK2jylpKqf7Lc\nJ7c/NoxYecMi4/wMl06Nc8XW8QMYOvTXTShor/Q3JuH2ewdol9P2Q/e2E7wGszUN\n9Of74KkoQ1bGf8Z3eutjqdP35/n6cETQDoFiqsV8DfHQGCiiNPKWGD2asQDhhRx4\nvh0TGIxvWF5lnSSxvbGsNFUoGWxr8eUH/EGcH1UnHfYL4xhUYqWTEOhM2v/csmzY\nt8o4BntudmXxlfgYU3NyPKkyx7/bVcnW1PJVtoDKkQKBgQDv7j0jjaWt6dJwsKa0\n5XQ4Xga1PbpDb3LWfzZr3IScUxbVytTnOWVXpok4esn4S00iQpAp7FV3YZ/qox7p\ngcOgV7lW6CIShnLgmr4CEt1hV/sRvqddmmgfrY4ZJLy24MSxwBeZiUPNRHKl9RZA\nJr2WsM04JPE4mmf9QOpGjjy71wKBgQDJDguPpQflCGT8s2KNQjBGnWGVfdNHd1vF\nOFP79wkROAEBb2mJsuBBl8Iu3YvImaKAyAln3uqOhQ8rr+y12DqBRgoAyHY3dr46\nlhQFDonNGVdOxrwRnxajKft32W8Tn6pdjuIs4N5q23Luqym5l9PA6h8aa3E+7yeE\ncvRIfqK6MQKBgG4OjED4wpzp+rvybCXictNAXjdY3037m2PE6sPDXZkPjBP5fHus\nGk6Ad8VOncKlV/Z1Lgfs/q9KOr64oH9gJMoyMzQoOyjgP2XD1ZDB8oaqguJ63+7R\n2x1c0Se7cE07AT6/7JNjIZTQ5v41VEWM/75Vz20HlRbvzO+gjVZb/IP1AoGANJwd\nQFhByZe5vTo/dpE0SrYR++kx6Qh9lgzYRR1uXPgXo0WBC0woTGGmqVbFphc1o5c0\nht6Y5/Q/dQIS4b6UCJHIOk46SOckffYZhP0559ZSt0VfnwjPBqEMsV7PJwZnsRWb\nb3zkFngYCgX15B+rhFZ/Dw3AU2SHJaxi6blhYXECgYEAnBAJuYoIfZolppeUZXwp\nAYoTLGMtXnjvX/YFumlEWzjnXLo4Lk9L+lO9sV5BwhQ6klNBARy5TjAedr+Kw0ee\noGh8F964pkF4jy7qBLMkf4/jaEvft/2tg16ELOj74llsd5GPA8Pgzeh1AXtlowwi\nC1Ere9RQ/zspggyX1uEakrI=\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\n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\n-----END CERTIFICATE-----\n"
    }
}
```

</details>

---

*Conteúdo baixado em 16/09/2026, 15:37:17*
