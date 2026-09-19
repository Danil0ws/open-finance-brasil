# GitLab Issues Guide

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/GitLab-Issues-Guide](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/GitLab-Issues-Guide)
**Slug:** `GitLab-Issues-Guide`

---

## **Version History**

You can view the page history by clicking the Wiki actions button (three dots) in the top-right corner.

## :arrow_right: **What is it?**

GitLab issues are a resource offered by the GitLab platform that serves as a source for the support flow within the Open Finance Brasil ecosystem. Through them, Participants can establish direct contact with Ecosystem Providers whenever they require assistance.

In this context, GitLab issues can address the following Raidiam Assure Products:

* Conformance Suite
* FVP
* Mock Bank

By creating a GitLab Issue, Participants express their needs and describe the situation in detail to support evaluation and investigation by the appropriate parties.

To ensure consistency and proper tracking, all issues must be tagged by **Nature, Platform, Product, Working Group,** and **Status**. This structured classification improves visibility, allows for faster triage, and also feeds into a comprehensive dashboard that consolidates information across all issues.

This guide also includes the SLA rules and defined workflow paths, clarifying expectations for both Participants and Providers regarding response times and resolution processes.

## :arrow_right: **The Anatomy of an Issue**

#### The List of Issues

Before jumping into how to open appropriate Issues, let's take a closer look at the essential elements that make up an Issue.

On the [Main GitLab Issues](https://gitlab.com/raidiam-conformance/open-finance/certification/-/issues) page, Participants can view a list of all open and closed Issues. Each Issue is composed of the following elements:

![image.png](uploads/b80189a3008e223ea2b8a2c8b92315e4/image.png){width="910" height="60"}

1. **Issue Title:**
   * Points out to the main test-module, test-plan, or product related to the issue, along with its subject.
2. **Issue Details:**
   * ![image.png](uploads/5ab3a3e0ec0dec0666869f0cb6901094/image.png)→ Issue Number
   * ![image.png](uploads/c94be7a0e5b4676f3df5d9466e4923be/image.png)→ Issue creation date and Author
3. **Issue Labels:**
   * Labels are fundamental for categorization, triage, and providing clarification to the client. They must be applied at the time of issue creation and updated throughout the analysis and development workflow. Every issue must be evaluated against the following label categories during its lifecycle, even if not all categories are applied at the same time: **Nature**, **Platform,** **Product**, **Working Group**, and **Status.**
     * **Nature Label:** Labels to identify the issue type and follow-up action expected.
       * ~&quot;Questions&quot;: Used for clarifications and doubts.
         * **Criteria**: Applies when a ticket just requires further follow-up.
         * **Follow-up:** The Issue will be closed after clarification.
         * **Example:** Clarification on the conformance suite behavior, or guidance on configuring test plans.
       * ~Bug: Indicates inconsistent or incorrect behavior.
         * **Criteria:** The Conformance Suite is not behaving according to the summary or technical requirements defined in the swagger specification.
         * **Follow-up:** A Merge Request (MR) will be opened with the correction, and the issue will be closed afterward.
         * **Example**: Wrong error message expected by the Conformance Suite, or use of client credentials token where authorization code is required.
       * ~&quot;Change Request&quot;: Indicates the need to change the approved behavior or summary of a test module due to changes or updates to the available specifications.
         * **Criteria:** There is a request to change the summary from a test module and, therefore, its behavior; or if there is a specific "test path" that the Conformance Suite should support following the current specifications, but does not yet.
         * **Follow-up:** A Merge Request (MR) will be opened with the correction, and the issue will be closed afterward.
         * **Example:** Adding a new error message defined by the WG to replace or complement an older one.
       * ~&quot;Test Improvement&quot;: Proposes enhancements to an existing test that already works. Applies when the test already passes successfully, but a possible enhancement has been identified.
         * **Criteria:** The test is functional and passes with current specifications, but improvements could simplify execution.
         * **Follow-up:** A Merge Request (MR) will be opened with the correction, and the issue will be closed afterward. Usually, these issues are deprioritized over bugs or change requests.
         * **Example:** The Conformance Suite starts retrieving endpoints from the directory instead of creating them from the consent URL, or moving webhook tests to a different plan, so the client does not have to be deleted before executing the tests.
       * ~&quot;Breaking Change&quot;: Points to situations where changes will impact ongoing tests. When an introduced change will break the current behavior being enforced by the Conformance Suite. This tag will be added along with other Nature labels.
         * **Criteria:** A test module changes behavior so that participants who previously passed will now fail.
         * **Follow-up:** A Merge Request (MR) will be opened with the correction, and the issue will be closed afterward. The Release Notes will be updated with the correction, and test plans for certification will only be accepted from the correction deploy date.
         * **Example:** A change in the error message from a specific scenario, so participants must adapt their implementations to pass the tests.
     * **Platform Labels:** Labels to identify which technical component or environment of the Raidiam Assure ecosystem the Issue is related to. They are essential to route the ticket correctly and ensure the appropriate team handles it.
       * Examples: ~FVP ~&quot;Mock Bank&quot; ~&quot;Conformance Suite&quot; ~Directory ~&quot;PCM Integration&quot; ~&quot;Test Manager&quot;
     * **Product Labels:** Labels to identify which product the label refers to. This type of label is always included in the issue.
       * Examples: ~&quot;Automatic Payments::v2&quot; ~&quot;CPC Credit Portability::v1&quot; ~&quot;Loans::v2&quot; ~&quot;Payments :: v4&quot;
     * **Working Group Labels:** Labels that identify the Open Finance WG accountable for a given topic/product in the issue. It uses the original Portuguese WG name.
       * Examples: ~&quot;GT Serviços&quot; ~&quot;GT Dados do cliente&quot; ~&quot;GT Portabilidade de crédito&quot;
     * **Status Label:** Labels to identify what is the status of the diagnosis process for the issue. They are generally followed by a Nature Label.
       * ~&quot;Under Evaluation&quot;: When the issue is undergoing evaluation by the provider, a proper response or solution is supplied in this initial triage.
         * **Criteria:** The Issue is under analysis by our internal team to determine the appropriate response or solution.
         * **Follow-up:** Once the evaluation is completed, this label will be replaced by a more specific Status and/or Nature label.
         * **Example:** An issue requiring verification from multiple specifications is being evaluated or is on the queue.
       * ~&quot;Waiting Participant&quot;: When the Provider requires additional information from the participant to proceed.
         * **Criteria:** The ticket cannot progress until the Participant provides missing/further information.
         * **Follow-up:** Once the evaluation is completed, this label will be replaced by a more specific Status and/or Nature label, or may be closed. If the response takes too long, the issue may be closed due to inactivity.
         * **Example:** A participant sent a question without the test ID, making it difficult to investigate; or a merge request has been deployed without being able to fully test it, so the participant was requested to execute the test again.
       * ~&quot;Under WG/DTO Evaluation&quot;: Applied when a doubt or inconsistency requires clarification by a Working Group (WG). In some common cases, the clarification may be provided directly by the Open Finance Brasil technical teams (DTO), without the need to escalate the matter to a formal WG weekly meeting.
         * **Criteria:** Specification-related issues that cannot be resolved internally and require WG or DTO input for clear guidance.
         * **Follow-up:** After the WG/DTO review, it will be replaced by the tag ~&quot;Evaluated by WG/DTO&quot;, along with an appropriate Nature Label.
         * **Example:** The error code for a specific situation is not clear in the specifications.
       * ~&quot;Waiting AOPF prioritization&quot;: The Issue has already been triaged and accepted, but is not yet under active development.
         * **Criteria:** Approved as a Change Request, Test Improvement, or Breaking Change, and waiting to enter the development workflow. Bugs are always considered in the active development flow, while they're not ~&quot;Deprioritized by DTO&quot;.
         * **Follow-up:** Label remains until work starts, then it must be updated to ~&quot;In progress&quot;.
         * **Example:** An adjustment in Automatic Payments tests that, after initial triage, has been accepted as a Test Improvement and is awaiting prioritization to enter the production pipeline.
       * ~&quot;Sent to AOPF board (RAD)&quot;: The Issue has already been triaged and accepted, but was tracked under AOPF board to follow the delivery formal process and sprints.
         * **Criteria:** Approved as any "Nature", and sent to AOPF Jira Board to enter the formal development workflow.
         * **Follow-up:** Label should remain. If OPF participants need post-deployment feedback to be unblocked, the issue should remain open until this is concluded. Otherwise, it can be closed so we avoid duplicating information across boards.
         * **Example:** An adjustment in Automatic Payments tests that, after initial triage, was accepted as a Change Request and allocated by AOPF into their board to track the full development cycle.
       * ~&quot;In progress&quot;: The issue was prioritized and is actively being worked on in the development pipeline.
         * **Criteria:** Linked to an open Merge Request, implementation already ongoing, or testing in progress.
         * **Follow-up:** This label stays throughout the implementation flow. After deployment, it should be removed and the issue closed.
         * **Example:** A Change Request in Conformance Suite is already linked to a Merge Request and under development.
       * ~&quot;Sandbox Testing :: FVP&quot; : When an issue related to the FVP platform is for validation in the sandbox environment.
         * **Criteria:** The merged improvement/correction requires sandbox testing before being considered for deployment.
         * **Follow-up:** Once sandbox testing is completed, this label should be replaced with ~&quot;Waiting Deploy::FVP&quot;.
         * **Example:** An adjustment in Automatic Payments tests that, after merge, must be validated in the sandbox before being consolidated into a deployment.
       * ~&quot;Waiting Deploy::FVP&quot;: When an issue related to the FVP platform has successfully passed sandbox testing and is waiting for deployment.
         * **Criteria:** The issue has gone through Sandbox Testing and is ready to be scheduled for deployment.
         * **Follow-up:** The label remains in place until the deployment is executed. If live production testing was not intended, this label should be removed and the issue closed. If live production testing does occur, this label must be updated by ~&quot;Production Testing::FVP&quot;.
         * **Example:** An adjustment that was validated in the sandbox and is waiting to be released in the upcoming weekly deploy.
       * ~&quot;Production Testing::FVP&quot;: When an issue related to FVP is being validated directly in the production environment.
         * **Criteria:** This is common for scheduled tests or specific scenarios that require validation in production.
         * **Follow-up:** Once production validation is confirmed, this label should be removed and the issue closed.
         * **Example:** A test that requires a scheduled Pix for the next day to be validated in production, so it takes more time than usual to validate the test.
       * ~&quot;Deprioritized by DTO&quot;: When the issue is intentionally parked with lower priority and not expected to progress until a specific condition changes. Use this label to make it explicit in the record that deprioritization was deliberate. Specially useful for bugs, so future readers understand the context and the SLA.
         * **Criteria:** The item is valid, but the responsible team has clearly documented why it will not be prioritized in the current development cycle. The references must be described in the issue comments as a public or private note.
         * **Follow-up:** Once the item becomes prioritized again, this label should be removed and the issue updated with appropriate status labels.
           * An issue should always have at least one of the following statuses: ~&quot;In progress&quot; ~&quot;Waiting Participant&quot; ~&quot;Waiting AOPF prioritization&quot; ~&quot;Under WG/DTO Evaluation&quot; ~&quot;Sandbox Testing :: FVP&quot; ~&quot;Waiting Deploy::FVP&quot; ~&quot;Production Testing::FVP&quot; ~&quot;Deprioritized by DTO&quot; ~&quot;Sent to AOPF board (RAD)&quot;
         * **Example:** A valid enhancement that the Open Finance Structure agrees to postpone until a future release cycle or until higher-priority items are completed.
4. **Issue Status:**
   * ![7.png](uploads/554a2f971e24e59e94aabea475ea71fd/7.png)→  Issue Current state.
   * ![5.png](uploads/f48bb7b70108bb7f70755afc6e70f350/5.png)→ Represents whether the issue has a Merge Request Linked to it.
   * ![6.png](uploads/3ef4de20d0b9e1c1416038a9f3033be9/6.png) → Represents the number of comments contained within the Issue.
5. **Issue Closure Date:**
   * Time since the Issue has been closed.

#### Inside the issue Page

Here is an example of how issues look from [within the Issue page](https://gitlab.com/raidiam-conformance/open-finance/certification/-/issues), where more details about that specific issue can be found. This page can also be accessed by clicking on the Issue Title in the Main GitLab Issues page:

![2.png](uploads/59ca7ca7fa6aa6fe3587159c2473b39f/2.png)

6. **Issue Description:**
   * More information can be provided to ensure a better and faster evaluation of the issue.
7. **Issue Reactions:**
   * Used to represent the number of other participants facing the same issue. This is done by clicking the Thumbs Up Icon.

#### At the bottom of the issue Page

![image.png](uploads/18ad68cbebc1d311e85461b08b83abf2/image.png){width="921" height="458"}

 8. **Issue Linked Merge Request:**
    * When the issue has related merge requests, GitLab displays them in this panel.
 9. **Issue Activity:**
    * Logs every comment, change, or update being carried out on the issue. It also points out the creation of Merge requests or the redirection of other participants who opened new issues regarding the same matter.
10. **Issue Comment Box:**
    * Comments are the main source of communication regarding an issue. It is through the use of comments that:
      * Providers supply answers and updates on the issue.
      * WG/DTO provides assessments and answers specification doubts.
      * Other participants claim to be affected by the same issue.
      * Participants provide help and answers to others.
11. **Issue Close/Reopen Button:**
    * Both of the following buttons can be used by participants:
      * Close Issue: Used when the issue is open and a solution for it has been provided
      * Reopen Issue: Used when the issue is closed, but another unexpected behavior or question arises from the same topic.

## :arrow_right: **SLA rules**

<table>
<tr>
<th>Nature/Status</th>
<th>SLA</th>
</tr>
<tr>
<td>Under Evaluation</td>
<td>3 business days</td>
</tr>
<tr>
<td>Waiting Participant</td>
<td>5 business days</td>
</tr>
<tr>
<td>Bug, Questions</td>
<td>10 business days</td>
</tr>
<tr>
<td>

Change Requests,

Test improvements,

Breaking changes
</td>
<td>

No SLA

These issues are handled either by the regular product pipeline

or by the Quick Response Team (QRT), in case of no open bugs
</td>
</tr>
<tr>
<td>

Under WG/DTO evaluation,

Sandbox Testing (FVP),

Waiting deploy (FVP),

Production testing (FVP),

Deprioritized by DTO,

Waiting AOPF prioritization,

Sent to AOPF board (RAD)
</td>
<td>SLA is paused</td>
</tr>
</table>

## :arrow_right: **How to Create GitLab issues correctly**

#### 0. Before Creating a New Issue

![image.png](uploads/82f02d597e207f1946e22dd791f7d820/image.png)Before following the Issue creation, make sure to use the search bar on the Main Page to search through the Open and Closed Issues. Finding another issue that deals with the same API, product, or subject may lead to a fast answer and solution to the matter being faced.

#### 1. Creating a New Issue

While in the [Main GitLab Issues](https://gitlab.com/raidiam-conformance/open-finance/certification/-/issues) page, in the top right side of the screen, the "New issue" Button can be found (highlighted in yellow in the picture above). Upon pressing it, you will be redirected to the Issue Creation Screen.

#### **2. Writing an Issue Title**

![image.png](uploads/38458134aa291f2ce48d0cc9cb73c364/image.png)Issue Titles are normally composed of two main components:

![image.png](uploads/f633dae5000c4a7b10acdbbbadc634b9/image.png){width="557" height="28"}

\[The Test plan, module, or product the issue refers to\] **-** \[Main subject of issue's description\]

Following this structure is important as it makes it easier for other participants or providers to find other issues that might be related to the one being opened.

#### **3. Writing an Issue Description**

![image.png](uploads/dcdd783040b6523b82df5ad1a1310164/image.png)A well-written description usually contains the following core components:

1. The observed unexpected behavior or question that needs evaluation.
2. The expected behavior, including sections or images from the specification that substantiate it.
3. The Test Name + Test Id + Plan Id.
   * Indispensable for the effectiveness of the solution being provided.

#### **4. Finishing up**

After providing all the information as disclaimed above, make sure to review the issue.

This step ensures that all the parts have a clear and aligned understanding of the problem/doubt the issue refers to, enabling efficiency and effectiveness of the provided solution.

Now that you are done reviewing, feel free to hit the "Create Issue" button at the bottom of the page.

#### **5. Following up**

After an issue is created, it remains part of the workflow until it is resolved. Proper follow-up ensures transparency and efficiency.

* **Keep labels updated**: Adjust labels whenever the context changes or the issue advances in status, according to the label categories.
* **Add progress comments**: Provide updates when they are not automated or reflected by the status — for example, details of an alignment with WG/DTO or a link to a related discussion thread. Use internal notes to record non-public information and maintain organization.
* **Link Jira cards**: When an internal development Jira card is created to address the issue, add its number to the issue title. An automation will link the Jira card to the issue automatically.
* **Close the loop**: Once the solution is delivered or the doubt clarified, apply the final status and close the issue. Always clarify the closure reason for the issue opener.
* **Pending participant response**: If an issue is waiting for a participant’s reply and no response is received within 5 business days, update the status and add a comment noting the absence of feedback. Escalate internally if the delay blocks progress.

#### **6. Data Exposure Warning :warning:**

 If an issue contains information that is not public (e.g., FVP logs, sensitive payloads), you must either:

* Move the sensitive details to internal notes, or
* Access "More actions"inside the issue and turn on confidentiality for the entire issue if the description itself contains non-public data.
  * In this case, the issue will automatically receive this internal label: ![image.png](uploads/94e85753f125ddfa9672e5924eca09bd/image.png){width="78" height="28"}

---

*Conteúdo baixado em 16/09/2026, 15:38:06*
