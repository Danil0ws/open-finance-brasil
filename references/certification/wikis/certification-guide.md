# Certification Guide

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Certification-Guide](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Certification-Guide)
**Slug:** `Certification-Guide`

---


# Submission of Results for Open Finance Certification

## Process Overview

This page describes how to request of Certificate of Conformance for the Open Finance API. Here, the whole process is represented in the following workflow, with the blocks in Blue (P-X) being the steps expected on the Financial Institution side. 

![Service_Desk_Process_-_Page_1](uploads/878d8ca5027258a8d18a107a15f743fb/Service_Desk_Process_-_Page_1.png)

Do note that, that when filling out the certification request form on Service Desk, the same ticket can be used for multiple APIs. Here one ticket can be used to submit multiple requests, with the only requirement being sending the test plan URI for all the APIs that need to be certified.

Here, the required steps are the following:

1. Execute all test modules and achieve a passed state
2. Fill out the certification request form on Service Desk 
3. Wait for request approval by N1 and Conformance Suite Team
4. Receive the certification proof URI back on the Service Desk
5. Register the certification link on the directory

## Executing The Test modules 

Before submission, first, all tests must be successfully passed for the desired conformance profiles and testing results gathered, as described in the _instructions_. All tests MUST be in the ‘FINISHED’ status. Note that results with WARNING or SKIPPED are acceptable for certification purposes, depending on the scope of the test plan

Please note that the full supplied log files will be published as part of a successful certification. These may contain client credentials, private keys, and other potentially sensitive data that are part of the test configuration, so it is important to take into account if any sensitive data is being used on the test scope. 

Once all tests have been executed, to publish the results for certification you should click on **Publish for certification** button found on the right side of your test plan page as seen on the image. The Link will be your evidence of certification, seen in the address bar at the top of the page. Note that once you click on the submission button it won't be possible to re-execute the tests on this plan. In the case of the image, the Test Plan URI is https://web.conformance.directory.openbankingbrasil.org.br/plan-detail.html?plan=DymnHg0CsyFJz&public=true

![Screenshot_2023-01-10_at_20.46.45](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/uploads/9223a6e8397c0c07e86128c99301180e/Screenshot_2023-01-10_at_20.46.45.png)

Note that when clicking on the **Publish for certification** button no document must be attached and it is not required to save the.zip that is generated, with the URI being the only required evidence of the correct test execution.

## Submitting the Certification Request

You need to submit the logs to the Service Desk, you can do it by accessing [the Service Desk URI](https://servicedesk.openbankingbrasil.org.br/) with your Open Finance Directory account or the regular Service Desk Account.

![image](uploads/e03c41450efea6793d373946190aec52/image.png)

After logging in, you'll then raise on the menu a ticket for the category "Requisições"

![image](uploads/e42919a850a62e3ccf927b7da994ae9b/image.png)

Then, choose the option "Enviar pedido de certificação"

![image](uploads/5e5a5acacf22236be07c9a9a3350d8c6/image.png)

Once inside the ticket creation for the category above, you'll see a form containing the necessary information you need to submit:

![Screenshot_2023-01-10_at_16.07.22](uploads/fee0d06238975a63badc7711adfa748c/Screenshot_2023-01-10_at_16.07.22.png)
![image](uploads/33c3fd9eb43420c127dde500921bdcc2/image.png)

You should fill out the form in the following way:

- Title: Customer Friendly Name of the evaluated brand - Test module with execution issues

- Description: Relevant Details over the certification request - Here note that if any conditional scenario is returned as SKIPPED, the institution will need to inform the Description that the Institution does not support the tested functionality so we can confirm this. 

- Institution Name: Organisation Name

- Deployment: Name and Version of implementation

- ISPB: First 8 digits of CNPJ

- Open ID DiscoveryDocument: Well-known endpoints

- Primary Contact Name: Name of the contact that is requesting the certification

- Primary Contact Email: Email of the contact that is requesting the certification

- Representative Name: Name of a company representative who will be responsible for signing the certification document*

- Representative Email: Email of a company representative who will be responsible for signing the certification document*

- Certified APIs: Name, version and Test Plan URI of each API being certified

Down below is an example of how to fill out this form, here for the Mock Bank and the accounts and resources APIs:

![Screenshot_2023-01-10_at_21.15.09](uploads/d070251a05381fd14b3a086754311360/Screenshot_2023-01-10_at_21.15.09.png)
![image](uploads/0ce18d099f4f1733ffddd532461f31ea/image.png)


After filling it all out and submitting the results, your request will be treated by the initial structure of Open Finance, which will evaluate both the consistency of the presented document, as well as if the certification request executed is valid.


## Registering the URI on the Directory

After the Document has been approved a certification URI will be sent back to you at the service desk. This URI is the proof that the API has been correctly certified and must be used when registering your API on the Directory,.

Here, to register the certification link on the directory you should follow the [Directory Guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central) , session 9 where it is specified how you can add it to you Api Resource once certified.

![Session_9](uploads/17161b3b7d3719991e2ad2e9be056573/Session_9.png)

For any questions around this process we ask you to also raise a Ticket on the Service Desk as an Issue on the Conformance Suite so we can evaluate and clarify the behavior as required. 


---

*Conteúdo baixado em 16/09/2026, 15:37:14*
