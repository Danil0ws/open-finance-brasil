# Instructions for running Conformance tests

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Instructions-for-running-Conformance-tests](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/Instructions-for-running-Conformance-tests)
**Slug:** `Instructions-for-running-Conformance-tests`

---

# Open Finance Brasil Functional Conformance Testing 

_**V1.1 07th July 2021**_

This document describes how to run conformance tests and gather testing results for Functional Conformance Suite tests that are deployed in AWS.
Instructions for Running Tests

1. Open  https://web.conformance.directory.openbankingbrasil.org.br/login.html 
2. Log in with OB Brazil Directory
![image](uploads/1c378aece4d6c380ffebc58ab6e4eefe/image.png)

3. After you have logged in, you will see the following screen.
![image](uploads/155ef09f09792a543caca900e9c0cd93/image.png)
- Click on “Create a New Test Plan”
4. Then complete the fields using the dropdown menus (View tooltips for more help)
![image](uploads/05f2ea82dbdb7ab3a105e17f902b4d35/image.png)

5.	Here is an example of ‘tooltips’:
 ![image](uploads/558eba15b9486aa5d7c2b212e981805f/image.png)

6.	Select the relevant test plan from the “Test Plan” dropdown menu.
 ![image](uploads/34400f47301b0ffed8975ff3d8d3e957/image.png)

7.	Fill in the configuration form (as per the guidance given in the form fields when empty). You can switch to the “JSON” tab to view/edit the configuration in the underlying JSON format. Changes to the form are automatically reflected in the JSON and vice versa. The JSON can be copied and saved locally to be pasted back in later. 
8.	Discovery URL – This is the location of your well-known document – Tool tip shown below
![image](uploads/6394d037103dacc1ed8f831d0036ba59/image.png)
9.	Press “Create Test Plan”. 
 ![image](uploads/b5f7b0ba605b00329f2b5570ddf8e1bd/image.png)
10.	You will be taken to a list of all the test modules in the plan.
11.	Press “Run Test” on the first test module.

 ![image](uploads/0d5f6b6a216f783aafa92a270470e436/image.png)

12.	Please read the description of the test in the light blue box near the top of the log page – this may contain specific instructions; for example, one test requires that the user rejects the authentication process.

13.	If applicable, the test will ask you to approve (or deny or ignore) the request on the relevant authentication device.

14.	When the test has completed, press “Continue Plan” to start the next test, or “Return to Plan” to view your progress.

If you require support, please open an issue in this GitLab by visiting this [link](https://gitlab.com/obb1/certification/-/issues)

If it relates to a test failure, please include a link to the relevant log-detail.html, or if using a local install the downloaded log file.
Once you have successfully completed testing, please follow the Certification instructions to complete the certification process.



---

*Conteúdo baixado em 16/09/2026, 15:38:08*
