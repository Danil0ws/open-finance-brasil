# Existing Functionalities

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Existing-Functionalities](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Existing-Functionalities)
**Slug:** `Existing-Functionalities`

---

[[_TOC_]]

[This page is also available in Portuguese here.](https://gitlab.com/obb1/certification/-/wikis/Funcionalidades-existentes)

# Executing a DCR or using existing client

The Mock TPP can execute a new Dynamic Client Registration (DCR) or use an existing client by providing the necessary information.

![image](uploads/d41abd3da05c9872f40eadafa4077e70/image.png)

If you want to use an existing client, you need to fill out the

- Client ID
- Registration Access Token

After successfully doing a DCR, the information is stored in the local MongoDB session. It later can be accessed by going to "Use Existing Client Information" and seeing the Client IDs.

![image](uploads/eccdc47d51eb3c0de2a601c2e1d1b1c4/image.png)

After doing the DCR, you'll be able to see more details about which scopes were granted:

![image](uploads/3d3abc324c7045050399d5a6e2e38a33/image.png)

# Payments - PIX

The Mock TPP currently supports both the regular PIX and PIX Scheduled Payments. It also allows multiple payments to be created against a given server and its status to be checked

[We've recorded a video explaining how the Mock TPP handles Phase 3 Payments - PIX.](https://www.youtube.com/watch?v=RwtOiYdsNaQ)

**The existing macro steps in order for a Regular Payment flow are:**

## Regular Payment flow

When running the Mock TPP, you'll be able to create PIX Payments that test the whole process. You can set your own payment information or use the default one that the Mock Bank has been preset with. In every step, the Mock TPP logs what it's doing so it's easier to follow. You will also get the responses printed out in the U.I so you can verify the end status.

### Application Start > Bank Selection > DCR

- Select Payments from the Home Menu
- Retrieve participants list that have payments-consents registered in their API Family type from the directory (Back-End)
- Display participants - Allow search and selection of a participant (U.I.)
- Perform a DCR with the selected participant (Back-End)
- Prompt a new screen that shows the Client ID for the selected participant (U.I)

### Regular PIX Payment

- Select Create Payment in the Payments Menu (U.I)
- Input the payment information necessary and press create payment (U.I)
- Call the Consents API (Back-End)
- Display the screen waiting for the consent to be granted (U.I.)
- Redirect to the selected A.S. and wait for Consent to be granted (Back-End)
- Poll the Consents API - Check if the status has changed to consumed (Back-End)
- Call the Payments API (Back-End)
- Poll the Payments API until Payment status changes to an accepted state (Back-End)
- Display on the Mock TPP Screen The Payments/Consents Response or the Error Response (U.I.)
- Go back to the Payments Menu and you can see the Consent ID, Payment ID and Refresh Token that were generated from the executed payment

## Scheduled PIX Payment flow:

The Mock TPP supports scheduled PIX payments and this option can be selected in the Payment Detail view after creating Create Payment in the Mock TPP menu. There is also the option of checking the payment status after creating a payment

### Application Start > Bank Selection > DCR

- Select Payments from the Home Menu
- Retrieve participants list that have payments-consents registered in their API Family type from the directory (Back-End)
- Display participants - Allow search and selection of a participant (U.I.)
- Perform a DCR with the selected participant (Back-End)
- Prompt a new screen that shows the Client ID for the selected participant

### Scheduled Payments

- Select Create Payment in the Payments Menu (U.I)
- Input the payment information necessary and press "Yes" in Payment Schedule option (U.I)
- Select the payment date (Needs to be D+1) and press create payment (U.I)
- Call the Consents API (Back-End)
- Display the screen waiting for the consent to be granted (U.I.)
- Redirect to the selected A.S. and wait for Consent to be granted (Back-End)
- Poll the Consents API - Check if the status has changed to consumed (Back-End)
- Call the Payments API (Back-End)
- Poll the Payments API until Payment status changes to an SASC (scheduled) (Back-End)
- Display on the Mock TPP Screen The Payments/Consents Response or the Error Response (U.I.)
- Go back to the Payments Menu and you can see the Consent ID, Payment ID and Refresh Token that were generated from the executed payment (U.I)
- Press Check Status to see the current payment status and the payment date (U.I)

#### Patch

There is also the option of revoking a scheduled payment after creating. The Mock TPP then calls the /patch/ endpoint and turns the payment status to RJCT.

- Select Revoke Payment in the Mock TPP Menu (U.I)
- Fill out the patch info and press revoke payment (U.I)
- Call the Payments API Patch endpoint (Back-End)
- Go back to Mock TPP Menu and press Check Status to see the scheduled payment become rejected (U.I)

# Customer Data

The Mock TPP is being developed to fully support Phase 2 Customer Data. In its current version after doing the DCR or using an existing client, the user is prompted about the consent information and then can use the Phase 2 APIs

[We've recorded a video explaining how the Mock TPP handles Phase 2 Customer Data](https://www.youtube.com/watch?v=gqtyTx98LzU)

### Application Start > Bank Selection > DCR

- Select Customer Data from the Home Menu
- Retrieve participants list that have customers-personal registered in their API Family type from the directory (Back-End)
- Display participants - Allow search and selection of a participant (U.I.)
- Perform a DCR with the selected participant (Back-End)
- Prompt a new screen that shows the Client ID for the selected participant (U.I)

## Calling the Consents

- Select Personal or Business (PF/PJ), Identification Number, Rel (CPF/CNPJ) (U.I)
- Choose which consents to allow from available list (U.I)
- Send consent request to the client (Back-End)
- Authenticate user information (U.I)
- Accept or decline chosen consents and consent to data sharing (U.I)
- If approved, go to the Consent Response Menu

![image](uploads/d4202ce2aff97775163fde5261edbacb/image.png)

## Calling Phase 2 API Resources

In the Consent Response Menu, the user can select which Phase 2 API they want to call.

![image](uploads/80514584b8acc1e91408bcea525540f9/image.png)

### Resources

Calls the endpoint

```
open-banking/resources/v1/resources/
```

![image](uploads/ecf34b3f78eb7f3438314529491fdbaf/image.png)

### Personal/Business Info

Available endpoints

```
open-banking/customers/v1/personal/identifications/
open-banking/customers/v1/personal/financial-relations/
open-banking/customers/v1/personal/qualifications/
```

![image](uploads/35a57f519d949e15504120a46d583084/image.png)

### Accounts

Available endpoints

```
open-banking/accounts/v1/accounts/
open-banking/accounts/v1/accounts/{accountID}
open-banking/accounts/v1/accounts/{accountID}/overdraft-limits
open-banking/accounts/v1/accounts/{accountID}/balances
open-banking/accounts/v1/accounts/{accountID}/transactions
```

![image](uploads/355c131542d451555c5826c2644951f2/image.png)

### Credit Card

Available endpoints

```
open-banking/credit-cards-accounts/v1/accounts/
open-banking/credit-cards-accounts/v1/accounts/{accountID}
open-banking/credit-cards-accounts/v1/accounts/{accountID}/limit
open-banking/credit-cards-accounts/v1/accounts/{accountID}/transactions
open-banking/credit-cards-accounts/v1/accounts/{accountID}/bills
```

![image](uploads/c2be349d791ef6afa92ecf1d4e4bf324/image.png)

### Credit Operations

![image](uploads/7388d9faa78a98a8778305c64fc31bca/image.png)

#### Loans

Available endpoints

```
open-banking/loans/v1/contracts/
open-banking/loans/v1/contracts/{contractId}
open-banking/loans/v1/contracts/{contractId}/warranties
open-banking/loans/v1/contracts/{contractId}/scheduled-instalments
open-banking/loans/v1/contracts/{contractId}/payments
```

![image](uploads/ca3d4466795d12c8ec8e1ff727f50665/image.png)

#### Financings

Available endpoints

```
open-banking/financings/v1/contracts/
open-banking/financings/v1/contracts/{contractId}
open-banking/financings/v1/contracts/{contractId}/warranties
open-banking/financings/v1/contracts/{contractId}/scheduled-instalments
open-banking/financings/v1/contracts/{contractId}/payments
```

![image](uploads/8c7416829dbc4950dfdc01c2a2a03271/image.png)

#### Unarranged Accounts Overdraft

Available endpoints

```
open-banking/unarranged-accounts-overdraft/v1/contracts/
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}/warranties
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}/scheduled-instalments
open-banking/unarranged-accounts-overdraft/v1/contracts/{contractId}/payments
```

![image](uploads/130ec644893cc5d99892e91c59e00d8e/image.png)

#### Invoice Financings

Available endpoints

```
open-banking/invoice-financings/v1/contracts/
open-banking/invoice-financings/v1/contracts/{contractId}
open-banking/invoice-financings/v1/contracts/{contractId}/warranties
open-banking/invoice-financings/v1/contracts/{contractId}/scheduled-instalments
open-banking/invoice-financings/v1/contracts/{contractId}/payments
```

![image](uploads/f7e219fa8d1acd6566fc02aa467e93a3/image.png)

### Phase 2 Version 2 APIs

The Mock TPP also supports the new Phase 2 V2 APIs. You can use them by selecting the "v2" option in the Customer Data menu.

![image](uploads/e32c4d626c790dab6a1dda2d4b05b0c7/image.png)

The Mock TPP supports the new v2 APIs such as "transactions-current". Below is a video showcasing the Mock TPP running the Phase 2 v2 against the Mock Bank:

<div align="left">
      <a href="https://www.youtube.com/watch?v=kAYFy-kx51g">
         <img src="https://img.youtube.com/vi/kAYFy-kx51g/0.jpg" style="width:100%;">
      </a>
</div>

---

*Conteúdo baixado em 16/09/2026, 15:37:29*
