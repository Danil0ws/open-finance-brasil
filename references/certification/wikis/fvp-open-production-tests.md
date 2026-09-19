# FVP Open Production Tests

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Open-Production-Tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/FVP-Open-Production-Tests)
**Slug:** `FVP-Open-Production-Tests`

---

# Overview

The FVP Open Tests is an extension of the [FVP automated tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Automated-Production-Tests), designed to allow institutions to conduct production tests on their own servers. Unlike the Conformance Suite tool, the FVP Open Tests restrict access so that only users from the same organization can run tests on their servers, ensuring that no external users can interfere. That's why the need to get a PFVPC Role in the directory in order to execute the tests.

Due to the sensitive nature of the data being shared, the FVP Open Tests include only those test modules that do not involve end-to-end customer data sharing or payment flows. Specifically, these tests stop at the point where the user authorizes consent, but no further actions are taken with this consent. This approach helps ensure the security and privacy of sensitive data while still verifying that the consent process functions correctly.

# Release Dates

- 23/03/23 - Platform Workshop held with Ecosystem - Recording available on [The Open Finance Youtube Channel](https://www.youtube.com/watch?v=maGvy3pC7DM&t=1s&ab_channel=OpenFinanceBrasil)
- 01/04/23 - Platform go-live for the [G1 group](https://gitlab.com/obb1/certification/-/wikis/Automated-Production-Tests), including 4 test plans: Pre-Flight-Payments-Test-V2, Payments-Consents-Core-Test-V2, Pre-Flight-Customer-Data-Test-V2 and Resources-API-Test-V2
- 02/05/23 - Added G2 to execute the tests
- 17/05/23 - Included a new test plan "fvp-homologation_test-plan" containing a test module fvp-payments-consents-server-certificate-v2
- 31/04/24 - Included additional test modules for Customer Data and Services to be executed by the Initial Structure (FVP3.0)
- 10/03/24 - Updated the certificate and Software Statement Used to OrgId: 1dbfe32a-5f1e-4841-a30c-9f1b5f24ad36 and SSId: bcc3ba64-faf5-456c-a162-8fef7ee67170
- 25/03/24 - Update the tool with the new FAPI Profile specifications
- 17/04/2025 - Automatic Pix Tests at the FVP

# Configuring and Executing Tests

The specifications on how to access the platform and configure tests can be seen in the [Manual FVP Main Page](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Manual-Production-Tests)

**→ Open FVP Payments test plans:**

* fvp-automatic-payments_open_test-plan-v1
* fvp-no_redirect_payments_open_test-plan-v1
* fvp-payments-e2e_open_test-plan-v4
* fvp-automatic-pix-payments_open_test-plan-v2

# Complete Guide: Running the Production Test Plan for Payments V4 in FVP

To test Payments Behavior, in addition to the alias, well-known and CPF, it is necessary to provide Creditor Accounts details during the test plan configuration:

![image.png](uploads/892971652174b9b1466b87ea6ae2b2d9/image.png)

* **creditorAccount - ISPB**
  * Must be filled with the ISPB (Identificador do Sistema de Pagamentos Brasileiros) of the credited account from the SPI (Sistema de Pagamentos Instantâneos). Enter only numbers, 8 digits.
* **creditorAccount** - **Issuer**
  * Code of the issuing branch without the check digit. Only numbers, up to 4 digits.
* **creditorAccount - Number**
  * Must be filled with the account number of the receiving user, including the check digit (if applicable). If there is an alphanumeric character, it should be converted to 0. Only numbers, up to 20 digits.
* **creditorAccount - AccountType**
  * Types of accounts used for payment. Must follow the formats defined in the API's Swagger documentation.

# Complete Guide: Running the Production Test Plan for Automatic Pix in FVP

## Test Plan Name

**Production Functional Tests for Automatic Pix Payments - API Version 2**

This test plan validates the functional flows of the Automatic Pix Payments API (version 2) in the production environment.

---

## Important: Field Completion

In addition to the standard fields required to select the Authorization Server, this test plan also requires filling out **additional mandatory fields**. These simulate real-world user and account information needed for proper execution of the Automatic Pix flows.

These fields include:

* Information about the authenticated user (CPF or CNPJ)
* Debtor information in the consent
* Full details of the **creditor account**

> **Note:** Automatic Pix is designed for **payments to legal entities (companies)**. The account to be credited **must be a corporate (CNPJ) account**. Payments to individuals are not supported.

---

## Required Fields

### Authenticated User Data (Individual or Legal Entity)

| Field | Description | Example |
|-------|-------------|---------|
| **Payment consent - Logged User CPF** | CPF of the user authorizing the consent | `76109277673` |
| **Payment consent - Business Entity CNPJ\*** | Legal entity's CNPJ (logged User) | `50685362006773` |
| **brazilCpf** | CPF used during authentication | `76109277673` |
| **brazilCnpj**\* | CNPJ used during authentication, if testing with a corporate user | `50685362006773` |

\* Required only if the authenticated user is a legal entity (CNPJ)

---

### Debtor Information (within consent)

| Field | Description | Example |
|-------|-------------|---------|
| **Recurring Payment consent - Contract Debtor Name** | Name of the account holder responsible for the payment | `Ralph Bragg` |
| **Recurring Payment consent - Contract Debtor Identification** | CPF or CNPJ of the account holder | `76109277673` |

---

### Creditor Account (must belong to a legal entity)

| Field | Description | Example |
|-------|-------------|---------|
| **Payment consent - Creditor Account Name** | Name of the company receiving the funds | `Empresa Exemplo S.A.` |
| **Payment consent - Creditor Account CPF/CNPJ** | CNPJ of the company receiving the funds | `50685362006773` |
| **Payment consent - Creditor Account ISPB** | ISPB code of the recipient's institution | `99999004` |
| **Payment consent - Creditor Account Issuer** | Branch code of the recipient's account | `0001` |
| **Payment consent - Creditor Account Number** | Account number | `11188222` |
| **Payment consent - Creditor Account Type** | Account type (see options below) | `SVGS` |

> **Important:** The recipient account must belong to a legal entity (CNPJ). Individual (CPF) accounts are **not valid** for Automatic Pix flows.

---

## `accountType` Field Explained

### Description

Indicates the type of bank account used by the creditor (recipient). This field is mandatory and must match the other account details (ISPB, branch, number).

### Allowed Values (according to v2.0.0 of the Open Finance BR API)

| Value | Description |
|-------|-------------|
| `CACC` | Checking Account |
| `SVGS` | Savings Account |
| `TRAN` | Prepaid Payment Account |

> `SLRY` (Salary Account) is **not allowed** in this API.

### Example

`"accountType": "SVGS"`

**→ FVP Configuration Template:**

The following template serves to purpose instructing how to build a funcional configuration for FVP test plans, Below are all the fields you will need to fill on Json config in order to run FVP test modules:

```
{
    "alias": "74e929d9-33b6-4d85-8ba7-c146c867a817",
    "description": "mock",
    "server": {
        "discoveryUrl": "https://auth.mockbank.poc.raidiam.io/.well-known/openid-configuration",
        "authorisationServerId": "xxxxx-xxxx-xxxx-xxxx-xxxxx"
    },
    "resource": {
        "brazilOrganizationId": "xxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "name": "John Doe",
        "brazilCpf": "00000000000",
        "loggedUserIdentification": "00000000000",
        "paymentAmount": "0.00",
        "creditorAccountIspb": "00000000",
        "creditorAccountIssuer": "0000",
        "creditorAccountNumber": "0000000000",
        "creditorAccountAccountType": "CACC",
        "creditorName": "John Doe",
        "creditorCpfCnpj": "00000000000",
        "creditorProxy": "00000000000",
        "debtorAccountIspb": "00000000",
        "debtorAccountNumber": "0000000",
        "debtorAccountIssuer": "0000",
        "debtorAccountType": "TRAN"
        "contractDebtorName": "Example",
        "contractDebtorIdentification": "00000000000"
    },
    "directory": {
        "participants": "https://data.example.directory/participants",
        "keystore": "https://keystore.example.directory/",
        "apibase": "https://api.example.directory/",
        "directoryRootsUri": "https://data.example.directory/roots_directory.jwks",
        "discoveryUrl": "https://auth.example.directory/.well-known/openid-configuration"
    }
}
```

# Testing Scope

Similar to the Regular Conformance Suite the FVP has been built with a series of Test Plans aimed to test different behaviours of the Tested Servers. For this, a series of test modules are implemented, each with a well-defined testing path, which will confirm how the server responds to different API calls executed by the FVP. The summary of all the tests presented on the platform can be seen in the sessions below.

All tests are executed on the Production Environment and, as such, the number of scenarios set on FVP should include a sub-set of the existing scenarios on the Sandbox Conformance Suite, mainly due to the limitations of setting different data scenarios on the Production Environment

Note that the first test module for each test group, the pre-flight test, will not access any API, being used to confirm that the registration on the directory required to run the other tests has been set correctly and that the server is correctly accepting the DCR required for the other test to be executed.

# Test Plan List

[20260424-open-manual-fvp.xlsx](uploads/f6db383fb3c53f78f3c8a7ff7454209c/20260424-open-manual-fvp.xlsx)

---

*Conteúdo baixado em 16/09/2026, 15:37:31*
