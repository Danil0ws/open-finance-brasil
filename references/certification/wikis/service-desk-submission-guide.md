# Service Desk Submission Guide

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Service-Desk-Submission-Guide](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Service-Desk-Submission-Guide)
**Slug:** `Service-Desk-Submission-Guide`

---


# Submission of Results for Open Finance Certification

## Process Overview

This page describes how to request of Certificate of Conformance for the Open Finance API. Here, the whole process is represented in the following workflow, with the blocks in Blue (P-X) being the steps expected on the Financial Institution side. 

![Service_Desk_Process](uploads/69a5d9ed2b643020d04605987f8558fd/Service_Desk_Process.jpeg)

Following the workflow above, the certification request process starts with the submission of the passed tests on the Service Desk, being finished only when the [Certification Request document](https://github.com/OpenBanking-Brasil/specs-directory/blob/main/conformance/documents/TnC/Certificado%20de%20Conformidade%20Funcional.docx) is approved on the Docusign. Here note that there is no longer any requirement to submit the word document, with all the signatures being collected directly over Docusign.

Also do note that, that when filling out the certification request form on Service Desk, the same ticket can be used for multiple APIs. Here one ticket can be used to submit multiple requests, with the only requirement being sending the test plan URI for all the APIs that need to be certified.

Here, the required steps are the following:

1. Execute all test modules and achieve a passed state
2. Fill out the certification request form on Service Desk 
3. Wait for request approval by N1 and Conformance Suite Team
4. Sign the document on Docusign
5. Notify on Service Desk that the document has been signed
6. Receive the certification proof URI back on the Service Desk
7. Register the certification link on the directory

## Executing The Test modules 

Before submission, first, all tests must be successfully passed for the desired conformance profiles and testing results gathered, as described in the _instructions_. All tests MUST be in the ‘FINISHED’ status. Note that results with WARNING or SKIPPED are acceptable for certification purposes, depending on the scope of the test plan

Please note that the full supplied log files will be published as part of a successful certification. These may contain client credentials, private keys, and other potentially sensitive data that are part of the test configuration, so it is important to take into account if any sensitive data is being used on the test scope. 

Once all tests have been executed, to publish the results for certification you should click on Publish for certification button found on the right side of your test plan page as seen on the image. The Link will be your evidence of certification, seen in the address bar at the top of the page. Note that once you click on the submission button it won't be possible to re-execute the tests on this plan. In the case of the image, the Test Plan URI is https://web.conformance.directory.openbankingbrasil.org.br/plan-detail.html?plan=DymnHg0CsyFJz&public=true

![Screenshot_2023-01-10_at_20.46.45](uploads/9223a6e8397c0c07e86128c99301180e/Screenshot_2023-01-10_at_20.46.45.png)

Note that when clicking on the "Publish for certification" button no document must be attached and it is not required to save the.zip that is generated, with the URI being the only required evidence of the correct test execution.

## Submitting the Certification Request

You need to submit the logs to the Service Desk, you can do it by accessing [the Service Desk URI](https://servicedesk.openbankingbrasil.org.br/) with your Open Finance Directory account or the regular Service Desk Account.

![image](uploads/e03c41450efea6793d373946190aec52/image.png)

After logging in, you'll then raise on the menu a ticket for the category "Enviar pedido de certificação"

![image](uploads/4d106b23d997703cbb4753f62eb9cc58/image.png)

Then, choose the option "Novo Fluxo Certificação"

![image](uploads/89bd2aefa7a8ca3a0fe868920d3606e5/image.png)

Once inside the ticket creation for the category above, you'll see a form containing the necessary information you need to submit:

![Screenshot_2023-01-10_at_16.07.22](uploads/fee0d06238975a63badc7711adfa748c/Screenshot_2023-01-10_at_16.07.22.png)
![Screenshot_2023-01-10_at_16.08.01](uploads/fdbb224a1e79e66e3aef43a2c58e1bc7/Screenshot_2023-01-10_at_16.08.01.png)

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

> *Note that the Functional Compliance Certificate must be signed by one of the institution's representatives or by a representative whose powers have been duly granted.
> 
> If the institution chooses to be signed by a corporate representative, the signatory's consultation will be carried out using the following Central Bank API: https://olinda.bcb.gov.br/olinda/service/Informes_ComposicaoGruposEstatutarios/version/v1/odata/cargosEstatutariosPorCNPJ
> 
> An example of a call using this API for Banco do Brasil, whose ISPB code is 00000000, would be: https://olinda.bcb.gov.br/Olinda/service/Informes_ComposicaoGruposEstatutarios/version/v1/odata/cargosEstatutariosPorCNPJ(cnpj=@ cnpj)?%40cnpj=%2700000000%27&%24format=text%2Fplain

Down below is an example of how to fill out this form, here for the Mock Bank and the accounts and resources APIs:

![Screenshot_2023-01-10_at_21.15.09](uploads/d070251a05381fd14b3a086754311360/Screenshot_2023-01-10_at_21.15.09.png)

![image](uploads/550310b0dbc66ad1971ed6d1166d72ab/image.png)


After filling it all out and submitting the results, your request will be treated by the initial structure of Open Finance, which will evaluate both the consistency of the presented document, as well as if the certification request executed is valid.

## Signing the Document on Docusign

Once the technical contents of your submission request is approved, you will receive a note on the ticket informing you that the certification request document has been generated for signing on the Docusign, which will be sent for signature to the institution's representative. The primary contact can will also receive the document but only for simple review and tracking. 

The emails received should look like the following ones:

![Screenshot_2023-01-10_at_14.03.09](uploads/03cc654c85ebbf0e9a9f5b3e236ee737/Screenshot_2023-01-10_at_14.03.09.png)

Once pressed the button to sign, the representative will be redirected to Docusign page, where he will be able to review the information on the document and sign it on the last page.

You can see an example of the document attached below, and when you receive it, all the fields will already be filled out. Also, you can find more information about the Terms and Conditions and the Certification Request Document [here](https://github.com/OpenBanking-Brasil/specs-directory/tree/main/conformance/documents/TnC)

[Certificado_de_Conformidade_Funcional_050123.docx](uploads/bd688495e034fb2ea6462fd41b6d33f0/Certificado_de_Conformidade_Funcional_050123.docx)

The legal representative will be requested to sign at the end of the document.

![Screenshot_2023-01-10_at_21.36.38](uploads/55ff2359eb103d608ec9a2d5e1bf3fff/Screenshot_2023-01-10_at_21.36.38.png)

An example of the document filled out is attached below.

[Certificado_de_Conformidade_Funcional_050123.docx.pdf](uploads/27ee4c131149acc50949bda2620766d9/Certificado_de_Conformidade_Funcional_050123.docx.pdf)

Once the process is finished, you should notify the Initial Structure that the document was signed so that the certification link can be generated and sent back to you, so you can register it on the directory.


## Registering the URI on the Directory

After the Document has been approved a certification URI will be sent back to you at the service desk. This URI is the proof that the API has been correctly certified and must be used when registering your API on the Directory,.

Here, to register the certification link on the directory you should follow the [Directory Guide](https://openfinancebrasil.atlassian.net/wiki/spaces/OF/pages/17378602/Guia+de+Opera+o+do+Diret+rio+Central) , session 9 where it is specified how you can add it to you Api Resource once certified.

![Session_9](uploads/17161b3b7d3719991e2ad2e9be056573/Session_9.png)

For any questions around this process we ask you to also raise a Ticket on the Service Desk as an Issue on the Conformance Suite so we can evaluate and clarify the behavior as required. 


---

*Conteúdo baixado em 16/09/2026, 15:38:35*
