# Enable FAPI Unique

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Enable-FAPI-Unique](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Enable-FAPI-Unique)
**Slug:** `Enable-FAPI-Unique`

---

# Overview

[Open Finance Brazil](https://openfinancebrasil.org.br/) and [Open Insurance Brazil](https://opinbrasil.com.br/) have released in the Fourth Quarter of 2023 an Update on the Ecosystem [FAPI Security Profile](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/82083996/EN+Open+Finance+Brasil+Financial-grade+API+Security+Profile+1.0+Implementers+Draft+3), currently based on [FAPI 1.0 Advanced](https://openid.net/specs/openid-financial-api-part-2-1_0.html), aiming to better standardize the registration journey by reducing the number of choices that a Server may chose to respond when communicating with an Application.

In order to enable testing by the Ecosystem for the New Profile, the Mock Bank will be updated, in the first moment, to optionally support the New Profile, and, in the second moment, to only support the new Profile. This document aims to explain how this can be configured so the Mock Bank can be used for testing.

Details on when Open Finance Expects timelines around when this change is expected to take place should be consulted directly on the [Open Finance Brazil Calendar Page](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/calendars)

# Release Dates

- 27/11/23 - Update the Mock Bank to Optionally Support the New Profile
- TBD - Update the Mock Bank to Only Support the New Profile

# Changes Implemented With the New Profile

When executing the Mock Bank on the New Profile, the Following List of Changes will be enforced, on top of the already required definitions of the First Version of the FAPI Profile :

| Attribute                           | Enforced Behaviour                                                                                                |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| response_type                       | code id_token                                                                                                     |
| id_token claims                     | shall include an acr claim on the id_token, either "urn:brasil:openbanking:loa2" or "urn:brasil:openbanking:loa3" |
| id_token encryption                 | shall encrypt the id_token using RSA-OAEP with A256GCM                                                            |
| Client Authentication Type          | private_key_jwt                                                                                                   |
| Pushed Authorization Requests (PAR) | Mandatory                                                                                                         |
| subject_type                        | public                                                                                                            |
| response_mode                       | fragment                                                                                                          |

# Enabling the New Profile on the Mock Bank - Optionality Period

To Enable the Mock Bank to be executed with the New Profile the existing client registered within the Mock Bank must be updated to support the Behaviours highlighted above.

To toggle this configuration the client configuration must be updated while the field software_policy_uri, set within the Software Statement on the Sandbox Directory, is set as "software_policy_uri": "https://www.fapi.new". This means that a DCR or DCM must be executed right after this field is updated on the Directory, as the Mock Bank Server will obtain this information only once the registered SSA is updated.

An Example Collection on PostMan which includes the Call to the Sandbox Directory Assertion Endpoint, the Registration Request, as well as the mTLS certificates can be found below :

- [Mock_Bank_-_DCR.postman_collection.json](uploads/3cc027918bf9a4076dc828c9b91e371c/Mock_Bank_-_DCR.postman_collection.json)
- [key.key](uploads/e82a6f03fd3b4430d392e50bdbc7ed98/key.key)

- [certificate.pem](uploads/0af3582ac1a855ca099df57fdcd5488e/certificate.pem)

# Mock Bank and the OIDF FAPI-OP Tests

The Mock Bank can also be used against the [OIDF Conformance Suite](https://www.certification.openid.net/login.html) to evaluate the updated tests for the FAPI Unique Profile. For this, the following configuration file can be used, which relies on Sofware Statement 10120340-3318-4baf-99e2-0b56729c4ab2 (Client_1) and 9e357995-a191-4860-9db7-ceda3692a8c9 ( Client_2), both from Organization with ID 74e929d9-33b6-4d85-8ba7-c146c867a817 : 

<details>
<summary>Example of Configuration with the Mock Bank for the Updated FAPI-OP Test</summary>

```
{
    "consent": {
        "productType": "personal"
    },
    "alias": "obbsb",
    "description": "Mock Bank Phase 2 Testing",
    "publish": "everything",
    "server": {
        "discoveryUrl": "https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration"
    },
    "client": {
        "jwks": {
            "keys": [
                {
                    "p": "78JUKZQYXOJrtxspJB-CynvSl66pz4A_ZTHARx3XkwBIiauDubWrEL2-NqTQFzmwl-7blrVpV2YLLnhFu4LxYLxhteCZajOiODh--ZKHmPMuYeSvpWj8-_UbCwfAVr8KMpeMApS8vrN00A1JrenGZEohEeMhfOfQc7t4AkNxByM",
                    "kty": "RSA",
                    "q": "4ShWLujmausedyNz8gzMZMZCftcp4Fq4VHguJB7s8yrGgWQarrzbFWlFIpus5Wn7j-QUzoNMMR8TOn5izzurfWWAevm9bMRExAi_QOK2ljAVzxQqUfhI14SJLHBPDYaLEbJ1TKvK7EfPLrdPneC8Sf3poelY2jCbR4pu720DsQk",
                    "d": "KGWyWxfKrwv-qWFh0v98jMiN8Z28Qdm3Za3XQ08PhKYq_j0REnLSyZUbRBMelrBZG1PReVHKHjP6C21lLRuevelfFQ2NtSQP03iBnqRtlWJFQ0IpX9dV9zw63loF_YKyd-QoSFb3KzE2mll2Ye_SkOPKj11oOZgUg6TOfc9Yr5sIlGoW97FWRYBh9MMzy0RVhBoKQjhe0MZq0LunD2hKcJmu38e-1R2KWhYtJaPNJ7F7zsHanw26X5DJ4F0uEECf42pzdySOHRAsjtVn3xipqBG8IZd7ArJKNxIhv-NfF40GGIoc2eI-7ippPG8hM9DehJ-ztjZi7eW_ocM5H5kZsQ",
                    "e": "AQAB",
                    "kid": "4d918f4529378c8dfba0c6f5547bcf32473bbbe4728b0378251aac8e57338964",
                    "alg": "PS256",
                    "qi": "cSaM3v0bA-lbX95xbKu70iLqAdNEtPF8dy0CD9OvOuMoMC2VllAORPEIhWqAP_c2FTV6xM1bfIH321fVcDUnJUBBhFcW4QH34ly_u6SO80PJ_tRwSv0SJM7g2jehZBmx2OkeVT_sA9xz3f6uFwcdArXMvZrFqEV1pH7krxhLceU",
                    "dp": "e8jtAvp_CZWs30CaoRfTww7iz4VSDtu731csWotBvZer28g9nif5Rg9woW2-Mf-K-SZNISZQWNtKcpeOCR212afpGqn3CynVWwlwJRJOB92l2MzlEpV95-fIKo259A92CGDN3JdGS38DlFcH705_K1BKep21sHNO4DGt6B1Bwdk",
                    "dq": "NCmTJdUBJL4J1dIZ13bNl38zAo24fuilkbQyBF5ByOgdCvb1E4xfOSulP6pPOOr_w8s0Ys-aRDsNylxjad1KEogEZvkawGsL_1qDbHXZlRvYwZvLXigmP__Ng8UVG24TI-tzL2sRXQIZ5pnDUTEyjfXMPZ2A3zOplb5liwR3eXk",
                    "n": "0t-TDOj5japF93pOGj-mNOo3tbD29Wq6UGdbbt5aPdEixhKKhY3hYc9dt6nDO6kiGzgxCpu6wSOBKQjCfiaI2Zt_BQyjGHvpPCNBs1Vg87OhlVjadifhJAibWFQYtBnavRJLKzERw135gckVYI1bDqCKt-D_l5ukKBLNdw443hejML11ijwX5IM3bFT1By5kgYxbq-iMAx7yoyahdNPlL0g087zNULRC0ENg_xh1ZpNpdxgkzoYNkpRlrwyA_Igc_xWSaX_zplOd-GiDBE_gu03msmpcuSk3efmL3WHEnUN-mKzR-V6t_L2cbCc5tCoH2Hh9jxB6DNUjw2a_gVFzOw"
                },
                {
                    "p": "_QAQWTyJkEQSp6f1Imm-mgefA76oJybeO_afMfpjD_y8a-ns7jZND74jK5zaTKqzA_vYUVRffDiBOQZfp6JDylvjEqNk6Lk-TR7sRTvSEnbh-GRujCTxTQDk4Pi6dTcRGaiZG3-9e-JEFN0OqrOdcKqbPdEi9Hi5GdFZb6AE2fc",
                    "alg": "PS256",
                    "use": "enc",
                    "kty": "RSA",
                    "q": "8ZJmb-b_H90wN8-FHTKw3qbPHutDyVuRcNH1V9oS_h0ZkgFCgm9Y2norZKL9RYv2UnQVirmLN1S9Nek1E8xRfkufXlAJdblW40w7AE_26phaJ5p9ECYlMpZpWIaOS0zxj8_SFqrK5bxv6AzueBobtm45eUiAx36XnPwM7zbeeuc",
                    "d": "ga2TOSDbb1B0PZxHI7E1MdL4iRRXjkA9WoYnup8SzL7ShaPXJ8drL5WTwmljY8OK8Q5L6ztRct9MAFl66Y_j0Nagv-UeMRiCW3v22PDAemtOpaIIF4lLFbgj1CFXdAXilAHxogLnAh4wetRZq8gWIti4mVdgOeD3jJuA5kXy674ta8Ey8khR23_w1MmjirggiPDGaVE5vMLMQaeSaD4P7etPMyZNHLlODLnjzygOYAkVtV9KFG2SPefAv5FU_NmiXJ3HDQMZD4eKPS0FY0MNPYQbn7ES_PCYpzrCPL7C6FaBNjKNBk-itzZM_Av8EuNOQApAPXjZhRuylWNbcMD-OQ",
                    "e": "AQAB",
                    "kid": "d4bcfab943773cb7fd9bbffcf2bd401d9e44baef1627b31f41d507110839b51e",
                    "qi": "llVUweU_oO9mZ138WaHksBi9GQ8KxPHo-vj_arvivPWzdgIcZVl1pSdqvq3-Dwte821tyH7WGf03iR1FODpHMnYGVwpr5lCRryu2JbmgOHTbPi8Ey7Qxzr_JoHQwG1L2ObVBGIwEZg43Q9Ozs1aHUXpoCj1gFVaYCDfogyaUiFU",
                    "dp": "0qXI9uOmjc1_0sPPIDX3Enwh85Y8n0yHYFm4tn4JGPiPUTJVqQjhJKhk1B0mzQqbPkfkFeMwFVdekEI0RnieBNB4wb31eKczrjZ-9i4WfHUrNAs618iyeDC0YHP3mzycKkbsI6857vm3Qb_ERHCEN5h05QVKG06gn1RlKMGNCIU",
                    "dq": "dGezbODGtzgCcCJTZopyqBeBXsjHVVQGdXL24mp3FHQ5Sh3JSskU69JK7qeLm-OhwoGlj79w0izHMB88MFoYOt994Bh5Nn0k3Upyc-gUd18KsmLDOPDoo8PO55WPI8Hj9QSTm9CZDLMMyajRkJYkHHhowYSqaXca386k_PBXrKk",
                    "n": "7r2-qfK23VJ7eiDbFD04PompIMjnaN0eaSnp08dQJ3poMUrlqYyG9hiA7XgCR-CxkyGBLuWcxjNlaSnc9N-a-vDAUQvaIazdAau0Ya9wBZuWNOepiqzBs2uUj-xK4wc5eRfCAnpKR8ALOdbeY2XjK0xpeEExuv_wOA61yHH6ZyPtSqP--FKYXkHiBIiIcsQYOTDYcvKmQ-dN44v7JqI2K93S_T8eg5tgvBT6fQ3vVCDFVQaqgOQA-ILQY5ft3AbNRA2ix1lMcd4x2P1g53qTseoUQgkhBKb05Wob7Ctdinp7a-7HZOrag4MwPAVkfwtx8MdBQndFCL3c98HD0nJj4Q"
                }
            ]
        },
        "client_id": "En6fJZdp4YlBqFV9R5zqp",
        "scope": "openid accounts resources",
        "org_jwks": {
            "keys": [
                {
                    "p": "78JUKZQYXOJrtxspJB-CynvSl66pz4A_ZTHARx3XkwBIiauDubWrEL2-NqTQFzmwl-7blrVpV2YLLnhFu4LxYLxhteCZajOiODh--ZKHmPMuYeSvpWj8-_UbCwfAVr8KMpeMApS8vrN00A1JrenGZEohEeMhfOfQc7t4AkNxByM",
                    "kty": "RSA",
                    "q": "4ShWLujmausedyNz8gzMZMZCftcp4Fq4VHguJB7s8yrGgWQarrzbFWlFIpus5Wn7j-QUzoNMMR8TOn5izzurfWWAevm9bMRExAi_QOK2ljAVzxQqUfhI14SJLHBPDYaLEbJ1TKvK7EfPLrdPneC8Sf3poelY2jCbR4pu720DsQk",
                    "d": "KGWyWxfKrwv-qWFh0v98jMiN8Z28Qdm3Za3XQ08PhKYq_j0REnLSyZUbRBMelrBZG1PReVHKHjP6C21lLRuevelfFQ2NtSQP03iBnqRtlWJFQ0IpX9dV9zw63loF_YKyd-QoSFb3KzE2mll2Ye_SkOPKj11oOZgUg6TOfc9Yr5sIlGoW97FWRYBh9MMzy0RVhBoKQjhe0MZq0LunD2hKcJmu38e-1R2KWhYtJaPNJ7F7zsHanw26X5DJ4F0uEECf42pzdySOHRAsjtVn3xipqBG8IZd7ArJKNxIhv-NfF40GGIoc2eI-7ippPG8hM9DehJ-ztjZi7eW_ocM5H5kZsQ",
                    "e": "AQAB",
                    "kid": "4d918f4529378c8dfba0c6f5547bcf32473bbbe4728b0378251aac8e57338964",
                    "alg": "PS256",
                    "qi": "cSaM3v0bA-lbX95xbKu70iLqAdNEtPF8dy0CD9OvOuMoMC2VllAORPEIhWqAP_c2FTV6xM1bfIH321fVcDUnJUBBhFcW4QH34ly_u6SO80PJ_tRwSv0SJM7g2jehZBmx2OkeVT_sA9xz3f6uFwcdArXMvZrFqEV1pH7krxhLceU",
                    "dp": "e8jtAvp_CZWs30CaoRfTww7iz4VSDtu731csWotBvZer28g9nif5Rg9woW2-Mf-K-SZNISZQWNtKcpeOCR212afpGqn3CynVWwlwJRJOB92l2MzlEpV95-fIKo259A92CGDN3JdGS38DlFcH705_K1BKep21sHNO4DGt6B1Bwdk",
                    "dq": "NCmTJdUBJL4J1dIZ13bNl38zAo24fuilkbQyBF5ByOgdCvb1E4xfOSulP6pPOOr_w8s0Ys-aRDsNylxjad1KEogEZvkawGsL_1qDbHXZlRvYwZvLXigmP__Ng8UVG24TI-tzL2sRXQIZ5pnDUTEyjfXMPZ2A3zOplb5liwR3eXk",
                    "n": "0t-TDOj5japF93pOGj-mNOo3tbD29Wq6UGdbbt5aPdEixhKKhY3hYc9dt6nDO6kiGzgxCpu6wSOBKQjCfiaI2Zt_BQyjGHvpPCNBs1Vg87OhlVjadifhJAibWFQYtBnavRJLKzERw135gckVYI1bDqCKt-D_l5ukKBLNdw443hejML11ijwX5IM3bFT1By5kgYxbq-iMAx7yoyahdNPlL0g087zNULRC0ENg_xh1ZpNpdxgkzoYNkpRlrwyA_Igc_xWSaX_zplOd-GiDBE_gu03msmpcuSk3efmL3WHEnUN-mKzR-V6t_L2cbCc5tCoH2Hh9jxB6DNUjw2a_gVFzOw"
                },
                {
                    "p": "_QAQWTyJkEQSp6f1Imm-mgefA76oJybeO_afMfpjD_y8a-ns7jZND74jK5zaTKqzA_vYUVRffDiBOQZfp6JDylvjEqNk6Lk-TR7sRTvSEnbh-GRujCTxTQDk4Pi6dTcRGaiZG3-9e-JEFN0OqrOdcKqbPdEi9Hi5GdFZb6AE2fc",
                    "alg": "PS256",
                    "use": "enc",
                    "kty": "RSA",
                    "q": "8ZJmb-b_H90wN8-FHTKw3qbPHutDyVuRcNH1V9oS_h0ZkgFCgm9Y2norZKL9RYv2UnQVirmLN1S9Nek1E8xRfkufXlAJdblW40w7AE_26phaJ5p9ECYlMpZpWIaOS0zxj8_SFqrK5bxv6AzueBobtm45eUiAx36XnPwM7zbeeuc",
                    "d": "ga2TOSDbb1B0PZxHI7E1MdL4iRRXjkA9WoYnup8SzL7ShaPXJ8drL5WTwmljY8OK8Q5L6ztRct9MAFl66Y_j0Nagv-UeMRiCW3v22PDAemtOpaIIF4lLFbgj1CFXdAXilAHxogLnAh4wetRZq8gWIti4mVdgOeD3jJuA5kXy674ta8Ey8khR23_w1MmjirggiPDGaVE5vMLMQaeSaD4P7etPMyZNHLlODLnjzygOYAkVtV9KFG2SPefAv5FU_NmiXJ3HDQMZD4eKPS0FY0MNPYQbn7ES_PCYpzrCPL7C6FaBNjKNBk-itzZM_Av8EuNOQApAPXjZhRuylWNbcMD-OQ",
                    "e": "AQAB",
                    "kid": "d4bcfab943773cb7fd9bbffcf2bd401d9e44baef1627b31f41d507110839b51e",
                    "qi": "llVUweU_oO9mZ138WaHksBi9GQ8KxPHo-vj_arvivPWzdgIcZVl1pSdqvq3-Dwte821tyH7WGf03iR1FODpHMnYGVwpr5lCRryu2JbmgOHTbPi8Ey7Qxzr_JoHQwG1L2ObVBGIwEZg43Q9Ozs1aHUXpoCj1gFVaYCDfogyaUiFU",
                    "dp": "0qXI9uOmjc1_0sPPIDX3Enwh85Y8n0yHYFm4tn4JGPiPUTJVqQjhJKhk1B0mzQqbPkfkFeMwFVdekEI0RnieBNB4wb31eKczrjZ-9i4WfHUrNAs618iyeDC0YHP3mzycKkbsI6857vm3Qb_ERHCEN5h05QVKG06gn1RlKMGNCIU",
                    "dq": "dGezbODGtzgCcCJTZopyqBeBXsjHVVQGdXL24mp3FHQ5Sh3JSskU69JK7qeLm-OhwoGlj79w0izHMB88MFoYOt994Bh5Nn0k3Upyc-gUd18KsmLDOPDoo8PO55WPI8Hj9QSTm9CZDLMMyajRkJYkHHhowYSqaXca386k_PBXrKk",
                    "n": "7r2-qfK23VJ7eiDbFD04PompIMjnaN0eaSnp08dQJ3poMUrlqYyG9hiA7XgCR-CxkyGBLuWcxjNlaSnc9N-a-vDAUQvaIazdAau0Ya9wBZuWNOepiqzBs2uUj-xK4wc5eRfCAnpKR8ALOdbeY2XjK0xpeEExuv_wOA61yHH6ZyPtSqP--FKYXkHiBIiIcsQYOTDYcvKmQ-dN44v7JqI2K93S_T8eg5tgvBT6fQ3vVCDFVQaqgOQA-ILQY5ft3AbNRA2ix1lMcd4x2P1g53qTseoUQgkhBKb05Wob7Ctdinp7a-7HZOrag4MwPAVkfwtx8MdBQndFCL3c98HD0nJj4Q"
                }
            ]
        }
    },
    "mtls": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHLDCCBhSgAwIBAgIUMqeFK92Jnkqi77+SuQAD9+I+038wDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjMwNzI2MTYzNzAwWhcN\nMjQwODI0MTYzNzAwWjCCAT4xCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDEPMA0G\nA1UEBxMGTE9ORE9OMRwwGgYDVQQKExNPcGVuIEJhbmtpbmcgQnJhc2lsMTswOQYD\nVQQDEzJ3ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2ls\nLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxHTAbBgNVBA8TFFByaXZh\ndGUgT3JnYW5pemF0aW9uMRMwEQYLKwYBBAGCNzwCAQMTAlVLMTMwMQYDVQRhEypP\nRkJCUi03NGU5MjlkOS0zM2I2LTRkODUtOGJhNy1jMTQ2Yzg2N2E4MTcxNDAyBgoJ\nkiaJk/IsZAEBEyQxMDEyMDM0MC0zMzE4LTRiYWYtOTllMi0wYjU2NzI5YzRhYjIw\nggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC7s3xHUC748JLIjALl+lcH\nJjds8kM3ydOeIr5kgURu/0f1O/DMSGXCPuaOuSM4rAzUuWfIXj27XT6luXCrL9Ey\nRT9TNBOZfUDPbHi7FvtnnxOXkYuSPU+4NOhkUfEB+V1tyycCUi7cnnGN67J4VLDb\nBJMnu8C7Vk2MzYclbZY6kS0ZPQ5yJtZYz1W27KCLLee956CUuMkxlNVGCK0BH+dG\n/ywEv5wnAqGSH0FWKFjo9v/pc9/ga7dHh8KPLjH9rXCvQ6WxoEwOhoNb5ekfWPjW\n1uRa8ASh8ufB6TJ0fMyMHjF7emZoIHAqATzhN2uvgPyI8/zMiFUi9SHAbY/x82nJ\nAgMBAAGjggLjMIIC3zAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBSa5a+d33Oa10YX\nn9zR2QTCu6NpeTAfBgNVHSMEGDAWgBR67wuI2HqJ4b0vBD0esdbER0IoPTBZBggr\nBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3NwLnBraS1nMi5zYW5k\nYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIwWAYDVR0fBFEw\nTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5kaXJlY3Rvcnkub3Bl\nbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwPQYDVR0RBDYwNIIyd2Vi\nLmNvbmZvcm1hbmNlLmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcuYnIw\nDgYDVR0PAQH/BAQDAgWgMBMGA1UdJQQMMAoGCCsGAQUFBwMCMIIBdAYDVR0gBIIB\nazCCAWcwggFjBgsrBgEEAYO6L3ABAjCCAVIwgfUGCCsGAQUFBwICMIHoDIHlVGhp\ncyBDZXJ0aWZpY2F0ZSBpcyBzb2xlbHkgZm9yIHVzZSB3aXRoIE9wZW4gRmluYW5j\nZSBCcmFzaWwgc2FuZGJveCBBUElzIFNlcnZpY2VzLiBJdHMgcmVjZWlwdCwgcG9z\nc2Vzc2lvbiBvciB1c2UgY29uc3RpdHV0ZXMgYWNjZXB0YW5jZSBvZiB0aGUgT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IG9mIEFQSXMgQ2VydGlmaWNhdGUgUG9s\naWN5IGFuZCByZWxhdGVkIGRvY3VtZW50cyB0aGVyZWluLjBYBggrBgEFBQcCARZM\naHR0cDovL3JlcG9zaXRvcnkucGtpLWcyLnNhbmRib3guZGlyZWN0b3J5Lm9wZW5i\nYW5raW5nYnJhc2lsLm9yZy5ici9wb2xpY2llczANBgkqhkiG9w0BAQsFAAOCAQEA\nUmXiP0tHm0ZWl2M8SDh0QUgEWWkE3wtuNkXQ5lJuy7xnwIx4n7vChF0EWHVbmqVN\nuC4+SzMcyzRpxf7Eoyp+BOY0rSjk3J1BhUX6znexYZVOdk+sgVxn8OLEV03pC9NJ\ngkzMC/ykb6ADBg2/6GrA0TAGPZG8xtCVw/GmCZO9gSRAlFnvcHJTRq+wCkvLHyEh\nbcBgFJJc96as6p4eFAxybWK+NdmQCOZDak9p+nfpO83d0hac9wTNrmRkqnKbKfs+\nwRbyZbM7H8xmktnYcz/UvjEb8MMR+c5gky3byT2ueNKoR6FQi33Ibe+VVzyprR1g\nSIkiTMT0K0BPovZyiLEUkA==\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC7s3xHUC748JLI\njALl+lcHJjds8kM3ydOeIr5kgURu/0f1O/DMSGXCPuaOuSM4rAzUuWfIXj27XT6l\nuXCrL9EyRT9TNBOZfUDPbHi7FvtnnxOXkYuSPU+4NOhkUfEB+V1tyycCUi7cnnGN\n67J4VLDbBJMnu8C7Vk2MzYclbZY6kS0ZPQ5yJtZYz1W27KCLLee956CUuMkxlNVG\nCK0BH+dG/ywEv5wnAqGSH0FWKFjo9v/pc9/ga7dHh8KPLjH9rXCvQ6WxoEwOhoNb\n5ekfWPjW1uRa8ASh8ufB6TJ0fMyMHjF7emZoIHAqATzhN2uvgPyI8/zMiFUi9SHA\nbY/x82nJAgMBAAECggEBAI/gHaQgL1E8Ppcg01vrT2g4gAWvkZyixOYTJbOuboFS\nhprQzlwYJoAFbP77pKbdIpywXX/11QXYjJvFkDp31bfd4pNpeJiPrO0R7V0jWaPt\nCLyGoOCAxKmjTHsRYFauCVKOhSE/U5JilRI/F7cq28GWOSIcxbgTiDAknrIu1Reg\nPh87xhXug6gZf2D/UcYAkrKb/kiS1Ny5XrJW03AXOyjbEzXsb+sduvIEMCXR5NMD\nqNxMjjeah0nZ1zmO8W4kkI6TCRLhbgAju+B2zk5yAyAupLwgyPMIQHFvTd7Dei2A\nKiLiRiASomZ+KViauf/YXPaoBS3mEog3Lry5o44MgrECgYEA4pfwrBS6GFTBqgF7\nPBFCisMndVPIw7WOIlZEX9VNMqLdUGmWICGMCDKhYPn37Jz+MoWTeAma5DCQHtGg\n52xL29E+AuEi5ZZZms6OgAAt6rvZ4X9+GhXG6eLAMBOv2cy2Xdy5pgvocsQGRAUX\nc/0T0IeMPDGY5HFlEJgfpk+Xgv0CgYEA1A9uy9WSPbbvIf2ZdCUb81EtFlywqPfN\ni22sFg7Oz5vmpDOtqqRrx6bKMveOqTXWV+0qx6JC75MfKLmSMErPpcKNIau4I0+Q\n/VfN0YiNhzoxTqbjBHt1++ArpcHRP+WZRTX3RNXY6mEXI4e/zVNVFCk16fHcyAiH\nPawBNJqRGb0CgYAxVqAi+AhlT98zY0swExoIGOI4m9u1MY0XUO1maI18nxXNcpAr\nwuI4zr1w3jzrmmuHGKq5km3VjfVzoHWGrn/+BxuXiOoOT6SHHr7MhD17RRf2D8qn\nZ2J+fs8WKNM7e2WiHnOWAjXE94XdvbYTnWF5IGqamLoP09kLufP6RI5bCQKBgFnS\nG5zs3l+Tj6B3GTtvyHH8TTuukQlQxNgs4PoK1aBsKXodhY7Ey/4p8HU8FEopyps9\nkqQyX2W4jDckuv4HggJ08HB1mq4iMoiMW1pIG6JOjLoCyB+K58ODBRnViXsmFhCR\ntiWK6rED5Ngg1KX0iRHcDsEDt/9mVVpS88PDQHiFAoGBAIh6E5AaTUQbjzJO2jnN\nhCMoTjS+lnMbcKMv9/ZLOQ4y4ozLXz+6eNW6Q33H7iisAYJH4vkwMeHJXONPR4fW\n/k6zvHqzpeqRXfYh7pVDm7jazz5dhD74VszaGhSTD2yHCEgQggiE4UYNa0YSuHnz\ngc4BQHjn6r7giI3yhRjjhZWY\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIHFDCCBPygAwIBAgIUZJOYHaqMZR7leKm8iaKrR380T8QwDQYJKoZIhvcNAQEN\nBQAwdjELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MSowKAYDVQQDEyFPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBSb290IENBIC0gRzIwHhcNMjMwMzA5MTQzNjAwWhcNMzMw\nMzA2MTQzNjAwWjB5MQswCQYDVQQGEwJCUjEcMBoGA1UEChMTT3BlbiBGaW5hbmNl\nIEJyYXNpbDEdMBsGA1UECxMUT3BlbiBGaW5hbmNlIHNhbmRib3gxLTArBgNVBAMT\nJE9wZW4gRmluYW5jZSBzYW5kYm94IElzc3VpbmcgQ0EgLSBHMjCCASIwDQYJKoZI\nhvcNAQEBBQADggEPADCCAQoCggEBAJJZYsafIn0x1j8WLDfJ3HSXt65NqnKwGdcW\nn4z4VqdrvcIl6kJM7cjF3ImaN5SLideuK63/QP4tgGilZxooxLE8V8M/uPgGU74K\noTMBuDho6sND/UtHsr/wgkX9+/Kn50vdLbhXZBmvcL+5gtXKDQGR+d1LyaU8EigX\nkhvegMCSyW72PlQ9FetapanOpH0e5+osGRVI9ysm7PFrWE6UOs8EA/d6+v8SwHTW\nbD6iVVgtGnQtm0C4w4H6VVNnFE0F8pSnXQQPzQXMONIFi/UZPSB00H0qnxRvWkw3\nJa7QErS8hdMPGUHQ9N/RujhMhf7tlUArcgod6mc+SYfcI3j1pUcCAwEAAaOCApUw\nggKRMA4GA1UdDwEB/wQEAwIBBjASBgNVHRMBAf8ECDAGAQH/AgEAMB0GA1UdDgQW\nBBR67wuI2HqJ4b0vBD0esdbER0IoPTAfBgNVHSMEGDAWgBQVb9vsej3AhKXXgbWR\nvfmoWNM++jBZBggrBgEFBQcBAQRNMEswSQYIKwYBBQUHMAGGPWh0dHA6Ly9vY3Nw\nLnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2luZ2JyYXNpbC5vcmcu\nYnIwWAYDVR0fBFEwTzBNoEugSYZHaHR0cDovL2NybC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL2lzc3Vlci5jcmwwggF0\nBgNVHSAEggFrMIIBZzCCAWMGCysGAQQBg7ovcAECMIIBUjCB9QYIKwYBBQUHAgIw\ngegMgeVUaGlzIENlcnRpZmljYXRlIGlzIHNvbGVseSBmb3IgdXNlIHdpdGggT3Bl\nbiBGaW5hbmNlIEJyYXNpbCBzYW5kYm94IEFQSXMgU2VydmljZXMuIEl0cyByZWNl\naXB0LCBwb3NzZXNzaW9uIG9yIHVzZSBjb25zdGl0dXRlcyBhY2NlcHRhbmNlIG9m\nIHRoZSBPcGVuIEZpbmFuY2UgQnJhc2lsIHNhbmRib3ggb2YgQVBJcyBDZXJ0aWZp\nY2F0ZSBQb2xpY3kgYW5kIHJlbGF0ZWQgZG9jdW1lbnRzIHRoZXJlaW4uMFgGCCsG\nAQUFBwIBFkxodHRwOi8vcmVwb3NpdG9yeS5wa2ktZzIuc2FuZGJveC5kaXJlY3Rv\ncnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyL3BvbGljaWVzMA0GCSqGSIb3DQEB\nDQUAA4ICAQCANeSAlmJy3e9rrgTGShVCyMQhy68j3cAJyFzqCutyNMGHUgFOjAgD\nzIUQZmAepTDJdhJF+BoruBfAIJUr6tD9EBw2MZXiTLHZG9mqtGwsMbeI3o3R9Y3G\nEpGp72jIHw7mtUZdoaWcmgqxCWn6UT9bBKAkdt6KyRepPUy1YI59MZxpVOs5J0s2\nQFd3FRCNxdzgsuGqdxTb1Gre4I5E1vJWcp1Fe/kPdaOgPVC89M6uk3WYTnMNZ20N\n8K0ecXy8+E3K+to35berWn16g1ZrufylX6s2yyxcsUnh5KP1smFd8MePekKIW0SD\n8hqD1MtGQEmzdWrPCT9fZUzONj4VuDcl/vgfKUBsBszTmqwGF34G+663v10KUhga\nkCiIOZtkT9B+aESGAfczQiFO1h4cI52TKwEptfbplrFS2gILrzleqv0JoDDFYVhY\nV5AVDjqeHaniClCi10JdSN11LqNdagpyojN2a2WhVSAigIT3yDeqozlzjgPui/1E\nDt0zBkXd5uFDwNeLUwOribuS3hxVG5Bg73ZJl+UV3ZuAzFFCfkVBz6BeqUusf8+P\n3pqAQ4gzhSWNsTBIsjaVV8ZU8IqxKhBkRUSNjihG2kM8kX9knQvRbCBuuse/dDUe\n4cUJ+wT1omVgq+TWhShOAjsHEa233omXbH7v5igLBEkzzqmM5cAv8Q==\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\n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\n-----END CERTIFICATE-----\n"
    },
    "client2": {
        "jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "kid": "e3e17dcfa71ce60081cf9af83e61aa1f0da58253ff67c12869483ea33949475f",
                    "p": "1wSUAUhcTnM7vl2tV66R7bv4FlAwmlXfCKfuvsKJ248GSvuw28tQoIUAE4M5bfCESoXoav9PEchQ_lDxx65N_GKbYpq3DAT5x2GPLJY28FhSYkV6WqC8GZriAdnJLVkEJdpaQn1eSWtRLe69vtGXwd59V08t7oXXHK1sZ9EfZFk",
                    "kty": "RSA",
                    "q": "ztF1OO4zvFG0SQdHOObJZ3oTgTuHgasWEzTflObgb1RhScDWVL72456YU3KD53WJJmRwOGGsnDktOtBXcEl7Vc0PNxt14_lti0QA5zJWvF-4ZzRKJqYFFJFuk9SpBm8WaX1HLeX9AqwOnZQQQNmZFekdJWGhpLedRzVxD7YXR2s",
                    "d": "E6wjnRw7AYgPmXPdDz23wRcocgIosqmk6ui6aRmkz2Gl1CtwnVH01yKR6ULQJP1MWvD1HN0zJ-pBMdmfL0BamHp_Ora_WYYi9Supvuv_NpKSlJPkwNnYjVY3QBOT7xxXs-SyrfeZHo-vlAiZS5n_qcsNtq9RpXlS39l24x_8fyfOBglC34uBC7QXWhdhkcgnoQTLsN-UcAnPCOUwEeSynNJKT7nP7n99lg_SnVHvhMzldHZ0mznCH-hYFAAVpWFWg4qBZ0bZwEhm7ktO7LPKayr6rq982axYVjJn7GGn0mm-bwLiS0lbPHVWLCHG52Ulh8wDwhiSZhb4qOymxBfHIQ",
                    "e": "AQAB",
                    "qi": "jGlrN8OzKYJourLLiU4cSLEn3Mh0lD1Z_bBenMra5Wf0e8niX_LxQv02onEcmqeMnCsUnD2OJM_R8qWI-mlizuANQ0YlTxwnWvU3BVpn5laYsxINh6HTxBnscRe5xCQbDYsdu9Ws1jiiz2i9OiOXx-AFMdmWA9zcfYufWM25bhM",
                    "dp": "DcG0OnTHuxkyTFav_XkkywIIuFy_D1DJKUOdScUmjs6Sx39c7GMQsIRx4c22gesue5ofqaDWDTw0umCxZ2YmhSxF5sQhS_qRhIkgYOjncO8lrjXlwyCfiD_Zj-bAMU-NrWJP_gsJWkcsdXTd3PSJ8hRrDof5V1Zm0eXilq3RhVk",
                    "dq": "l18o--0kQp5OZPEFyPjpymnIIttON7Lf6ljVl-dPt0w8FL4mYUqP61NlzBXRwzP8mPQESs_6hTE4EIbyqIWv1sHKdBwOMjiaW8b_Hjhy0VcB4c-cwiLbLw2usFaDC-l8ruL5mPdvMmh6Hg2Dw-M_r5C6O2T06VlWrQrJYKV27lc",
                    "n": "rbWcSsX9BoV0SlipiDOQwat6fKzUXIT8o4yQ7f888sVWFfsPaOAih5o3LnOHIg8VvP4jqJug-nYAR5COsHIGg2IngCvx78VhUAsABSo5EcpewT2mEgaIbB_kEk8xsTrNcVrNhs30fDL765Y5ZtS4u3Rb8mBzgbk7_Naii_-2BPvTJzSmVsqPmvcrr7C94Io4wttCM3aepX43nlBlJux7pLqtS5r56lqyV8u_63rcogOVzL-8wQWFo3vgkPoU59Dn19DZpwH-7vTZ4SxeSV8UgQqBg4AOhuHPaFtICFFfc3H98yqOMfOzffkrGsZgkBTvrkVGv7kIz9EzHF_EZvKgMw"
                },
                {
                    "p": "zCG3BNKwsnisn_pwvRBwp0q9VG8SHxb1Ft5ytEnbzt5eBQrd_A9ySKAPQnfGVlpECq5whKB7f7WxiiOwIS33fmYblhvmLbQU7vRhxOs-Y-O5ZANHof5z6wQAChxrL0pSCabsmx7-RNx7OeLTL02yb2M_MPpld7u7wMOHXwwopGk",
                    "kty": "RSA",
                    "use": "enc",
                    "alg": "PS256",
                    "kid": "ed9b5d5880f720ea3c3d102163cec04cd89b89fc4babc06bac7b4037f92d6af6",
                    "q": "xtAS0Jt3K8PHCaOWmVhnYjVziXc-zdkd5PK5pS-BbiA-ZWtNrum_XXzjM0wHJctHaDyLiSQh9ar6qM-QVnV1pBYXF0XUopiqPGaAgCtHWjNhpLQ6poEJBnMYejm0-uDgwWQ7x7BA3esiB2XMUhiEoIBlgjVQ2Y4-_8PD3ScoaGs",
                    "d": "FCg8fQcRswXtPpKxdVBMyZqZKnckQb78_CB39lci8Pat3QNTQ6hBOXz_PHqo7nWO0t_5yL4LBqAAmtiqOZIXLPjWv16l0nbnuM1SYKhCE1o1gYuC5lFIdAJJjGneiJJsqg7EzNR02rWBoX_socQ9BiV7CctDdxsv9Np5_OMHEbQrH2qMSMNC8l0ehdLjBaJzdAZph7qKC1RPuAGn_K8G1VOoR9e3vqCZnPSUP1BJa3-UuQTPnj1LGk3BJMQ6LxUDbDZRDOInjuVidn0GgDQp4kbZJb7kv1xEsvnj9Uwnt52fViFfypDth-RK143GUHFhYfTWOuQwZE9JRKQm_AS_0Q",
                    "e": "AQAB",
                    "qi": "luBO0Apk6wasMBaJApi4HHnhEcL176I5fPOXH3v2Wtb81V79w6cfhC9HwHnJ1TLZ29W47l_vYuGhM7Ap5Key_IyCqU9x2UA71d2c2XYvKVhXNFHdtvrvqXqR4gc3LXYeM_1kNOmG-uPnGZ6rnEXDaDb7AU4PQ1W3Uaxs14V08fQ",
                    "dp": "mkbk5q1BxDD17pa9u_Z_3b_b5cNoQ7z7EQSgVmf3y5o-Hrt-2DDoY8Esp0SUztC72gLKoUIU9IlinA-q3vi5s3sCYGnHhkUzCQIEHmrYpXAHvnHIIsOH4lgMm5es3nniFM9mxTogW_Ty4OXwTDEBqbOtn5uvMlXdaaudVRWAZfk",
                    "dq": "gA0WgTwQ9qRDd2bhIeV5uRyaTOj8D5OPGJ5pigZeA_NKnQIO5-Dv-6PrpmeKlwIl_PI6IVufb97vUXlXCwjee5Aq0TeN7CgORZbznxnA_Ezp0C6xM_saOAg7tMWkVo4u1QDdLBHOxeCja0Za4mmeSs5IEySJ7YYb95o8dh25ff8",
                    "n": "nof98yUaVLe4noUGHR3FoHAn-GP9M29TUcs5Qi0zF6yl4psHIHUi7BGYRN-xokD77WhRnh3qVNJ6a2EFE4SGCeSGz6gshLzw9-QUda6MwLE59qFsSX2kjUdpy3LlURpN_DwOPgi3EqirhE17pLkmgWnPQPwTXaCsiBu8hEFfmKLygWZpHeXet1a4PSWARJOfpmdp_ihtkEP8SaSH36K2_9rcLR2N3DwCYtAmj-5RWGtKYmI4r-f_rBbBBWtiJJ15hntHk-dffjTH_6glHT11S2KJDsIq87T7BuuCIVmdJrk6Tut-fNAcwLovrPpAffQF4mvXNsp6t23puTK1Ry9f4w"
                }
            ]
        },
        "client_id": "R0MeRnrJCTIClaKaOq5-M",
        "scope": "openid accounts resources",
        "org_jwks": {
            "keys": [
                {
                    "alg": "PS256",
                    "kid": "e3e17dcfa71ce60081cf9af83e61aa1f0da58253ff67c12869483ea33949475f",
                    "p": "1wSUAUhcTnM7vl2tV66R7bv4FlAwmlXfCKfuvsKJ248GSvuw28tQoIUAE4M5bfCESoXoav9PEchQ_lDxx65N_GKbYpq3DAT5x2GPLJY28FhSYkV6WqC8GZriAdnJLVkEJdpaQn1eSWtRLe69vtGXwd59V08t7oXXHK1sZ9EfZFk",
                    "kty": "RSA",
                    "q": "ztF1OO4zvFG0SQdHOObJZ3oTgTuHgasWEzTflObgb1RhScDWVL72456YU3KD53WJJmRwOGGsnDktOtBXcEl7Vc0PNxt14_lti0QA5zJWvF-4ZzRKJqYFFJFuk9SpBm8WaX1HLeX9AqwOnZQQQNmZFekdJWGhpLedRzVxD7YXR2s",
                    "d": "E6wjnRw7AYgPmXPdDz23wRcocgIosqmk6ui6aRmkz2Gl1CtwnVH01yKR6ULQJP1MWvD1HN0zJ-pBMdmfL0BamHp_Ora_WYYi9Supvuv_NpKSlJPkwNnYjVY3QBOT7xxXs-SyrfeZHo-vlAiZS5n_qcsNtq9RpXlS39l24x_8fyfOBglC34uBC7QXWhdhkcgnoQTLsN-UcAnPCOUwEeSynNJKT7nP7n99lg_SnVHvhMzldHZ0mznCH-hYFAAVpWFWg4qBZ0bZwEhm7ktO7LPKayr6rq982axYVjJn7GGn0mm-bwLiS0lbPHVWLCHG52Ulh8wDwhiSZhb4qOymxBfHIQ",
                    "e": "AQAB",
                    "qi": "jGlrN8OzKYJourLLiU4cSLEn3Mh0lD1Z_bBenMra5Wf0e8niX_LxQv02onEcmqeMnCsUnD2OJM_R8qWI-mlizuANQ0YlTxwnWvU3BVpn5laYsxINh6HTxBnscRe5xCQbDYsdu9Ws1jiiz2i9OiOXx-AFMdmWA9zcfYufWM25bhM",
                    "dp": "DcG0OnTHuxkyTFav_XkkywIIuFy_D1DJKUOdScUmjs6Sx39c7GMQsIRx4c22gesue5ofqaDWDTw0umCxZ2YmhSxF5sQhS_qRhIkgYOjncO8lrjXlwyCfiD_Zj-bAMU-NrWJP_gsJWkcsdXTd3PSJ8hRrDof5V1Zm0eXilq3RhVk",
                    "dq": "l18o--0kQp5OZPEFyPjpymnIIttON7Lf6ljVl-dPt0w8FL4mYUqP61NlzBXRwzP8mPQESs_6hTE4EIbyqIWv1sHKdBwOMjiaW8b_Hjhy0VcB4c-cwiLbLw2usFaDC-l8ruL5mPdvMmh6Hg2Dw-M_r5C6O2T06VlWrQrJYKV27lc",
                    "n": "rbWcSsX9BoV0SlipiDOQwat6fKzUXIT8o4yQ7f888sVWFfsPaOAih5o3LnOHIg8VvP4jqJug-nYAR5COsHIGg2IngCvx78VhUAsABSo5EcpewT2mEgaIbB_kEk8xsTrNcVrNhs30fDL765Y5ZtS4u3Rb8mBzgbk7_Naii_-2BPvTJzSmVsqPmvcrr7C94Io4wttCM3aepX43nlBlJux7pLqtS5r56lqyV8u_63rcogOVzL-8wQWFo3vgkPoU59Dn19DZpwH-7vTZ4SxeSV8UgQqBg4AOhuHPaFtICFFfc3H98yqOMfOzffkrGsZgkBTvrkVGv7kIz9EzHF_EZvKgMw"
                },
                {
                    "p": "zCG3BNKwsnisn_pwvRBwp0q9VG8SHxb1Ft5ytEnbzt5eBQrd_A9ySKAPQnfGVlpECq5whKB7f7WxiiOwIS33fmYblhvmLbQU7vRhxOs-Y-O5ZANHof5z6wQAChxrL0pSCabsmx7-RNx7OeLTL02yb2M_MPpld7u7wMOHXwwopGk",
                    "kty": "RSA",
                    "use": "enc",
                    "alg": "PS256",
                    "kid": "ed9b5d5880f720ea3c3d102163cec04cd89b89fc4babc06bac7b4037f92d6af6",
                    "q": "xtAS0Jt3K8PHCaOWmVhnYjVziXc-zdkd5PK5pS-BbiA-ZWtNrum_XXzjM0wHJctHaDyLiSQh9ar6qM-QVnV1pBYXF0XUopiqPGaAgCtHWjNhpLQ6poEJBnMYejm0-uDgwWQ7x7BA3esiB2XMUhiEoIBlgjVQ2Y4-_8PD3ScoaGs",
                    "d": "FCg8fQcRswXtPpKxdVBMyZqZKnckQb78_CB39lci8Pat3QNTQ6hBOXz_PHqo7nWO0t_5yL4LBqAAmtiqOZIXLPjWv16l0nbnuM1SYKhCE1o1gYuC5lFIdAJJjGneiJJsqg7EzNR02rWBoX_socQ9BiV7CctDdxsv9Np5_OMHEbQrH2qMSMNC8l0ehdLjBaJzdAZph7qKC1RPuAGn_K8G1VOoR9e3vqCZnPSUP1BJa3-UuQTPnj1LGk3BJMQ6LxUDbDZRDOInjuVidn0GgDQp4kbZJb7kv1xEsvnj9Uwnt52fViFfypDth-RK143GUHFhYfTWOuQwZE9JRKQm_AS_0Q",
                    "e": "AQAB",
                    "qi": "luBO0Apk6wasMBaJApi4HHnhEcL176I5fPOXH3v2Wtb81V79w6cfhC9HwHnJ1TLZ29W47l_vYuGhM7Ap5Key_IyCqU9x2UA71d2c2XYvKVhXNFHdtvrvqXqR4gc3LXYeM_1kNOmG-uPnGZ6rnEXDaDb7AU4PQ1W3Uaxs14V08fQ",
                    "dp": "mkbk5q1BxDD17pa9u_Z_3b_b5cNoQ7z7EQSgVmf3y5o-Hrt-2DDoY8Esp0SUztC72gLKoUIU9IlinA-q3vi5s3sCYGnHhkUzCQIEHmrYpXAHvnHIIsOH4lgMm5es3nniFM9mxTogW_Ty4OXwTDEBqbOtn5uvMlXdaaudVRWAZfk",
                    "dq": "gA0WgTwQ9qRDd2bhIeV5uRyaTOj8D5OPGJ5pigZeA_NKnQIO5-Dv-6PrpmeKlwIl_PI6IVufb97vUXlXCwjee5Aq0TeN7CgORZbznxnA_Ezp0C6xM_saOAg7tMWkVo4u1QDdLBHOxeCja0Za4mmeSs5IEySJ7YYb95o8dh25ff8",
                    "n": "nof98yUaVLe4noUGHR3FoHAn-GP9M29TUcs5Qi0zF6yl4psHIHUi7BGYRN-xokD77WhRnh3qVNJ6a2EFE4SGCeSGz6gshLzw9-QUda6MwLE59qFsSX2kjUdpy3LlURpN_DwOPgi3EqirhE17pLkmgWnPQPwTXaCsiBu8hEFfmKLygWZpHeXet1a4PSWARJOfpmdp_ihtkEP8SaSH36K2_9rcLR2N3DwCYtAmj-5RWGtKYmI4r-f_rBbBBWtiJJ15hntHk-dffjTH_6glHT11S2KJDsIq87T7BuuCIVmdJrk6Tut-fNAcwLovrPpAffQF4mvXNsp6t23puTK1Ry9f4w"
                }
            ]
        }
    },
    "mtls2": {
        "cert": "-----BEGIN CERTIFICATE-----\nMIIHJzCCBg+gAwIBAgIUc5n89HnfUzOq8r4Yn8waz0UMDTcwDQYJKoZIhvcNAQEL\nBQAweTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gRmluYW5jZSBCcmFzaWwx\nHTAbBgNVBAsTFE9wZW4gRmluYW5jZSBzYW5kYm94MS0wKwYDVQQDEyRPcGVuIEZp\nbmFuY2Ugc2FuZGJveCBJc3N1aW5nIENBIC0gRzIwHhcNMjMwNzI2MTY0MDAwWhcN\nMjQwODI0MTY0MDAwWjCCATkxCzAJBgNVBAYTAkJSMQswCQYDVQQIEwJTUDEPMA0G\nA1UEBxMGTE9ORE9OMRwwGgYDVQQKExNPcGVuIEJhbmtpbmcgQnJhc2lsMTswOQYD\nVQQDEzJ3ZWIuY29uZm9ybWFuY2UuZGlyZWN0b3J5Lm9wZW5iYW5raW5nYnJhc2ls\nLm9yZy5icjEXMBUGA1UEBRMONDMxNDI2NjYwMDAxOTcxGDAWBgNVBA8TD0J1c2lu\nZXNzIEVudGl0eTETMBEGCysGAQQBgjc8AgEDEwJVSzEzMDEGA1UEYRMqT0ZCQlIt\nNzRlOTI5ZDktMzNiNi00ZDg1LThiYTctYzE0NmM4NjdhODE3MTQwMgYKCZImiZPy\nLGQBARMkOWUzNTc5OTUtYTE5MS00ODYwLTlkYjctY2VkYTM2OTJhOGM5MIIBIjAN\nBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA3t6hs0KeudIwIE95IWO0XkE5W+xn\n+8pspAmjMELFOWjl55PUzsohBhJ2hdajqxext/zXjlPnPBCk6xOLYRr571MwRJn9\n2s1nTMvFMO6JWQHnFjLgRc4nA4KiE2ZN5b1JanvCwrFhvMjBZBgWBlLlVcEvDNQa\nZk9WVUPeyOkPesHgJ16y3tTFXhbIMtCRTVzooPY9vI1edGyoJwa7/tovECgdBXHb\nOhC9SuBxdH49EvEMxkdW5mV4rTtKJvwV7MxhF7N176HpFxMr+W0lwkfXKDFu/TTX\nym05r4OIDFoNZvrGsaTja3Pi1prxagt+xDBbYjBWzQZZ+mm+kunrs9D+EQIDAQAB\no4IC4zCCAt8wDAYDVR0TAQH/BAIwADAdBgNVHQ4EFgQUlwLB3ZQ46zfwqiPufKto\niVMfIRYwHwYDVR0jBBgwFoAUeu8LiNh6ieG9LwQ9HrHWxEdCKD0wWQYIKwYBBQUH\nAQEETTBLMEkGCCsGAQUFBzABhj1odHRwOi8vb2NzcC5wa2ktZzIuc2FuZGJveC5k\naXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMFgGA1UdHwRRME8wTaBL\noEmGR2h0dHA6Ly9jcmwucGtpLWcyLnNhbmRib3guZGlyZWN0b3J5Lm9wZW5iYW5r\naW5nYnJhc2lsLm9yZy5ici9pc3N1ZXIuY3JsMD0GA1UdEQQ2MDSCMndlYi5jb25m\nb3JtYW5jZS5kaXJlY3Rvcnkub3BlbmJhbmtpbmdicmFzaWwub3JnLmJyMA4GA1Ud\nDwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEFBQcDAjCCAXQGA1UdIASCAWswggFn\nMIIBYwYLKwYBBAGDui9wAQIwggFSMIH1BggrBgEFBQcCAjCB6AyB5VRoaXMgQ2Vy\ndGlmaWNhdGUgaXMgc29sZWx5IGZvciB1c2Ugd2l0aCBPcGVuIEZpbmFuY2UgQnJh\nc2lsIHNhbmRib3ggQVBJcyBTZXJ2aWNlcy4gSXRzIHJlY2VpcHQsIHBvc3Nlc3Np\nb24gb3IgdXNlIGNvbnN0aXR1dGVzIGFjY2VwdGFuY2Ugb2YgdGhlIE9wZW4gRmlu\nYW5jZSBCcmFzaWwgc2FuZGJveCBvZiBBUElzIENlcnRpZmljYXRlIFBvbGljeSBh\nbmQgcmVsYXRlZCBkb2N1bWVudHMgdGhlcmVpbi4wWAYIKwYBBQUHAgEWTGh0dHA6\nLy9yZXBvc2l0b3J5LnBraS1nMi5zYW5kYm94LmRpcmVjdG9yeS5vcGVuYmFua2lu\nZ2JyYXNpbC5vcmcuYnIvcG9saWNpZXMwDQYJKoZIhvcNAQELBQADggEBAIJALd/v\n5DC4ZUxCzlNvEgy757uMxxTJlMlqLvl+q5yqxX2ewxP8coLQI0JbRq7o6VTmMQBT\nFHqPnAafi6iHVtqqUh5ZZZ/UWCV7pDENPm1CXLV6adQzIbbgMtd6IhTIbIblJXJ4\nWkc730e6uqbpAXRmoBMRurBWCd8KL3BylpuYWlvf9EZXbz/Ab4JvK2aBdsb+K3qJ\n+3q3VSVsAbx9FQtDkmGzr8hxTWgYJiTJX7zDwbUkys3JxO8w/wdFEuGuUw98/UAP\n6IaCRDr6/Dk1Yc8CUR34w3M8CxxYpOlQN0K+pyhdClHBxy0yMhNL5xVQGbLui+sF\nZHv4lnaWk1l1lVk=\n-----END CERTIFICATE-----",
        "key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDe3qGzQp650jAg\nT3khY7ReQTlb7Gf7ymykCaMwQsU5aOXnk9TOyiEGEnaF1qOrF7G3/NeOU+c8EKTr\nE4thGvnvUzBEmf3azWdMy8Uw7olZAecWMuBFzicDgqITZk3lvUlqe8LCsWG8yMFk\nGBYGUuVVwS8M1BpmT1ZVQ97I6Q96weAnXrLe1MVeFsgy0JFNXOig9j28jV50bKgn\nBrv+2i8QKB0Fcds6EL1K4HF0fj0S8QzGR1bmZXitO0om/BXszGEXs3XvoekXEyv5\nbSXCR9coMW79NNfKbTmvg4gMWg1m+saxpONrc+LWmvFqC37EMFtiMFbNBln6ab6S\n6euz0P4RAgMBAAECggEAXtu3S0sRr9mMblQlJFcBkBSGy19Fqt+veeo4MPRaaWMC\nZ5x+OT3C7IizNafzpYDCPaM6Q/PmOaSD7SI2crA+rORlaO16JMTEMOWSGo+Mmfu7\nVbF1z4A9DrttLICgqyXzt4TRknhZNzbjSS0PQsXJosREuFsWmXEvN79ZdX3s/rv2\nnZq3yjNYPVsoamPqxPwePve76wks3Na3yvV6upDV+4XGoEQ6xjfbYkv0ROGGmrcY\nhBTrjB8Thr2ZeW9rJUoNvSsPamynlsvvpH04qdmVKPpY1Op0CyeETO2xel8PTZnA\nAsu/ZJQ+2VeP2wiuybZ+W9HqsZ93OW9IIZbL3Hf3GQKBgQD5RaFAxxzVstetZ2Ma\npdPWOHRaY3Cu9Cx0ggz9/3bNluALqigFU8tsoOrsldJE2gBleyZmJfSg3pPGCbon\npi6YCqXruGGkz0sAqm2Ql8k0yxyvbarpgnLaRMADAM1z2shY25pW2/UEAGugVh6h\nHHKljOzD7fvEWL9Jhlnct+MCJwKBgQDk4pJ2njJXz1aeqZ0/8pmd8+8FHVZlLj5c\nRHh4J9jZWSmBSUYsXeLFCNMnI/brK27xv+2RUD+B6BWXGjiCW+8gTOc+31jq6fkL\niCYGuESaqulgbrU4zo/4/a3IjhFweyKlquigfcSNUzLGXLLdcx+Pq3LCngtK5jMU\nN6b4itz5BwKBgFEm8hB8wk5wIvc5KXKLeiPLzVV/+jd7Ft33WPN4L91OuTIS+2SA\nm0GKQfEz9Xik4GwpY57tzG5zB/j5QbmWyKSHEu1i4aceNXTKB1GDmOWvGm+ibHoJ\nFgspRrmzkS+ekosbM2wDwAjFekSAxQf+kvSCpLJE0CpkGiJ9stPAqg8RAoGAB4a3\nwDTFfQOxWnhDVnX4vSvnQSjMzXjuzgPmXjUZOVRoO/sX1p+jtEzs/I1/Mg50kHh6\nLFwSKohiJVzUXNz/CPXeaL/ZYagd61YnwfLPNrLGB8i8JskMDOjyjPS2+BbkdcQf\n8B8Sln8U3Vbw/r0pXYUKugGOZ4EYTuLhl6yhRYMCgYEA4+rOxZyGbKSVf3aJe9GJ\nS8reu9k22swir4c6svjKMaKrhNPFPsvOMHQxtk6UsVrdHuuFVZCHZWjQhHOkz9MF\nWNNbFNbqQzoBoEsqpDf18iCRNtdtjK2F1epnO/ZzD6lX/Hm+VddAWL4Tla8bnmsM\nRfpB7kz+J7FO+NwmMkxwZTc=\n-----END PRIVATE KEY-----\n",
        "ca": "-----BEGIN CERTIFICATE-----\nMIIEajCCA1KgAwIBAgIUdIYzEFdw7QJcrySyq6IiEwZfTfAwDQYJKoZIhvcNAQEL\nBQAwazELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gQmFua2luZyBCcmFzaWwx\nFTATBgNVBAsTDE9wZW4gQmFua2luZzEnMCUGA1UEAxMeT3BlbiBCYW5raW5nIFJv\nb3QgU0FOREJPWCAtIEcxMB4XDTIwMTIxMTEwMDAwMFoXDTIzMTIxMTEwMDAwMFow\ncTELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gQmFua2luZyBCcmFzaWwxFTAT\nBgNVBAsTDE9wZW4gQmFua2luZzEtMCsGA1UEAxMkT3BlbiBCYW5raW5nIFNBTkRC\nT1ggSXNzdWluZyBDQSAtIEcxMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKC\nAQEA6fX+272mHX5QAcDaWkVHFWjnDIcORNUJU3OuNyeuOYhlvXJWydrXe3O+cV+P\nS39faMj/nfem3GfJBE7Xn0bWA/8ksxSfrg1BUBJDge4YBBw+VflI3A0g1fk9wJ3H\nGInsvV4serRJ/ISJTfs0uRNugX+RrbkT/T0tup4vGd3Kl2sbwUdDjokuJNJHANeO\nDRkQ+ra+9Wht71FBlc07yPf7qtpaWHm6aS3s47OJD35ixkG4xiZuHsScxcVtlo1V\nW98P2cQfH9H2lll4wWlPTVHpPThB2EYrPhwcxDh8kHkkOHNkyHO/fYM47u7H4VeQ\nV75LXWKa7iWmZg+WhFb8TXSr/wIDAQABo4H/MIH8MA4GA1UdDwEB/wQEAwIBBjAP\nBgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBSGf1itF/WCtk60BbP7sM4RQ99MvjAf\nBgNVHSMEGDAWgBSHE+yWPmLsIRwMSlY68iUM45TpyzBMBggrBgEFBQcBAQRAMD4w\nPAYIKwYBBQUHMAGGMGh0dHA6Ly9vY3NwLnNhbmRib3gucGtpLm9wZW5iYW5raW5n\nYnJhc2lsLm9yZy5icjBLBgNVHR8ERDBCMECgPqA8hjpodHRwOi8vY3JsLnNhbmRi\nb3gucGtpLm9wZW5iYW5raW5nYnJhc2lsLm9yZy5ici9pc3N1ZXIuY3JsMA0GCSqG\nSIb3DQEBCwUAA4IBAQBy4928pVPeiHItbneeOAsDoc4Obv5Q4tn0QpqTlSeCSBbH\nIURfEr/WaS8sv0JTbIPQEfiO/UtaN8Qxh7j5iVqTwTwgVaE/vDkHxGOen5YxAuyV\n1Fpm4W4oQyybiA6puHEBcteuiYZHppGSMus3bmFYTPE+9B0+W914VZeHDujJ2Y3Y\nMc32Q+PC+Zmv8RfaXp7+QCNYSXR5Ts3q3IesWGmlvAM5tLQi75JmzdWXJ1uKU4u3\nNrw5jY4UaOlvB5Re2BSmcjxdLT/5pApzkS+tO6lICnPAtk/Y6dOJ0YxQBMImtliY\np02yfwRaqP8WJ4CnwUHil3ZRt8U9I+psU8b4WV/3\n-----END CERTIFICATE-----\n-----BEGIN CERTIFICATE-----\nMIIDpjCCAo6gAwIBAgIUS3mWeRx1uG/SMl/ql55VwRtNz7wwDQYJKoZIhvcNAQEL\nBQAwazELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gQmFua2luZyBCcmFzaWwx\nFTATBgNVBAsTDE9wZW4gQmFua2luZzEnMCUGA1UEAxMeT3BlbiBCYW5raW5nIFJv\nb3QgU0FOREJPWCAtIEcxMB4XDTIwMTIxMTEwMDAwMFoXDTI1MTIxMDEwMDAwMFow\nazELMAkGA1UEBhMCQlIxHDAaBgNVBAoTE09wZW4gQmFua2luZyBCcmFzaWwxFTAT\nBgNVBAsTDE9wZW4gQmFua2luZzEnMCUGA1UEAxMeT3BlbiBCYW5raW5nIFJvb3Qg\nU0FOREJPWCAtIEcxMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAp50j\njNh0wu8ioziC1HuWqOfgXwxeiePiRGw5tKDqKIbC7XV1ghEcDiymTHHWWJSQ1LEs\nmYpZVwaos5Mrz2xJwytg8K5eqFqa7QvfOOul29bnzEFk+1gX/0nOYws3Lba9E7S+\nuPaUmfElF4r2lcCNL2f3F87RozqZf+DQBdGUzAt9n+ipY1JpqfI3KF/5qgRkPoIf\nJD+aj2Y1D6eYjs5uMRLU8FMYt0CCfv/Ak6mq4Y9/7CaMKp5qjlrrDux00IDpxoXG\nKx5cK0KgACb2UBZ98oDQxcGrbRIyp8VGmv68BkEQcm7NljP863uBVxtnVTpRwQ1x\nwYEbmSSyoonXy575wQIDAQABo0IwQDAOBgNVHQ8BAf8EBAMCAQYwDwYDVR0TAQH/\nBAUwAwEB/zAdBgNVHQ4EFgQUhxPslj5i7CEcDEpWOvIlDOOU6cswDQYJKoZIhvcN\nAQELBQADggEBAFoYqwoH7zvr4v0SQ/hWx/bWFRIcV/Rf6rEWGyT/moVAEjPbGH6t\nyHhbxh3RdGcPY7Pzn797lXDGRu0pHv+GAHUA1v1PewCp0IHYukmN5D8+Qumem6by\nHyONyUASMlY0lUOzx9mHVBMuj6u6kvn9xjL6xsPS+Cglv/3SUXUR0mMCYf963xnF\nBIRLTRlbykgJomUptVl/F5U/+8cD+lB/fcZPoQVI0kK0VV51jAODSIhS6vqzQzH4\ncpUmcPh4dy+7RzdTTktxOTXTqAy9/Yx+fk18O9qSQw1MKa9dDZ4YLnAQS2fJJqIE\n1DXIta0LpqM4pMoRMXvp9SLU0atVZLEu6Sc=\n-----END CERTIFICATE-----\n"
    },
    "resource": {
        "consentUrl": "https://matls-api.mockbank.poc.raidiam.io/open-banking/consents/v2/consents",
        "brazilCpf": "76109277673",
        "brazilOrganizationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
        "resourceUrl": "https://matls-api.mockbank.poc.raidiam.io/open-banking/resources/v2/resources"
    },
    "directory": {
        "client_id": "QjRzruzFWi_U_tMahlz01",
        "discoveryUrl": "https://auth.sandbox.directory.openbankingbrasil.org.br/.well-known/openid-configuration",
        "participants": "https://data.sandbox.directory.openbankingbrasil.org.br/participants",
        "keystore": "https://keystore.sandbox.directory.openbankingbrasil.org.br"
    }
}
```

</details>

The Certificates on the Configuration File Above are set to expire on - 2024-08-24 16:37:00 

Past successful executions can be seen on:

| Test Name                      | Test Results |
| ------------------------------ | ------------ |
| fapi1-advanced-final-test-plan | [30/11/23](https://demo.certification.openid.net/plan-detail.html?plan=bTiKj2eO4ot3d&public=true)     |

---

*Conteúdo baixado em 16/09/2026, 15:37:27*
