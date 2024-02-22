# Development Requests

To request a new feature or report a bug, please visit the help section of the developer portal. You'll be directed to GitHub where you'll be able to create an issue directly in our public board. You should track the progress of your issue and communicate with developers directly in GitHub.

{% hint style="info" %}
Please do not communicate though our service desk, customer success managers or any other channels within the business with regard to the status or timeline of an issue.
{% endhint %}

## Our processes

After submitting an issue, your ticket will get triaged and categorised. From here, it will be assigned to the relevant GitHub project, depending on the nature of the work requested.

* Incoming issues that we identify as back-end engineering will be given the `back-end` label, issues that we identity as front-end engineering with be given front-end label and assigned to the [Backlog](https://github.com/reapit/foundations/projects/6) public board to be reviewed.&#x20;
* New issues on the board are reviewed weekly as part of our refinement sessions. To ensure your issue can be progressed quickly, please provide as much relevant information as possible. Whilst your issue is being reviewed it will remain in the ‘[To Review](dev-requests.md#columns-definitions)’ column.
* The team will discuss each issue and should we agree that development is warranted, we will commit to the work. However, if we need to gather more information or investigate, the relevant label will be added and if applicable, we will add a comment.
* Depending on the nature of the request or bug, the issue will then enter a specific column. For more information on columns, please [click here](dev-requests.md#columns-definitions).
* If your issue is assigned to a specific sprint, we aim to complete the work within our 2 week sprint cycle. For more information please [click here](dev-requests.md#my-issue-has-been-carried-over-to-another-sprint).&#x20;
* When an issue is completed by the dev team, it will be moved to [QA](dev-requests.md#columns-definitions) where it will be verified by a member of the dev or product team on our development environment and assuming this is successful, will be released straight to production.
* Any issues failing QA will be moved back to [In Progress](dev-requests.md#columns-definitions) to be fixed before any new issues are worked on.
* Once verified by QA and the work has been completed, the issue will be closed and moved to ‘[Done/Closed](dev-requests.md#columns-definitions)’

## **FAQ’s**&#x20;

### **How do I request a feature?**

You can raise a feature request direct on our GitHub board [here](https://github.com/reapit/foundations/issues/new?assignees=\&labels=external-request%2C+needs-triage\&template=feature\_request.md\&title=).&#x20;

### **How do I report a bug?**

You can report a bug direct on our GitHub board [here](https://github.com/reapit/foundations/issues/new?assignees=\&labels=bug%2C+needs-triage\&template=bug\_report.md\&title=).&#x20;

### **I have a question not covered in the documentation?**&#x20;

We take great pride in ensuring our documentation is as comprehensive and detailed as possible. However, there may be an instance in which you are unable to find the information you need. As we do not provide technical support via email or over the phone, please use the ‘[Question](https://github.com/reapit/foundations/issues/new?assignees=\&labels=needs-triage%2C+question\&template=question.md\&title=)’ template to raise an issue. Please note, it's important that you read the documentation before asking a question as we cannot answer questions which are already covered.

### **How long will it take for my issue to be reviewed?**&#x20;

Your issue will be reviewed in a weekly refinement session and depending on the complexity or requirement, will be assigned to a specific project board. From there it will be prioritised, (if applicable) a specification and relevant label will be added. Once we have scoped out the work it will be moved to the relevant column. Please [click here](dev-requests.md#columns-definitions) for more information on columns and labels.&#x20;

### **How long will it take for my issue to be completed?**

Completion of your issue is dependent on the work required, complexity and alignment with our current development which can be viewed on our [Roadmap](https://github.com/reapit/foundations/milestones). We will prioritise bugs depending on the severity and implications. Feature requests will be prioritised in accordance with the upcoming milestone target dates, customer and developer priority and how achievable the task is given the current state of development.

### **My issue has been carried over to another sprint?**

In the back end team, we work in 2 week sprints and estimate the amount of work we believe we can complete. However, due to other priorities or dependencies, we may not always complete every issue as intended. If your issue has moved to another sprint, we will comment on the ticket to explain why and if more information is needed.

You can see the start and end dates of our sprints [here ](https://github.com/reapit/foundations/projects?type=classic)and access previous sprints [here](https://github.com/reapit/foundations/projects?query=is%3Aclosed\&type=classic).

### **How to do I track the progress of an issue?**&#x20;

If you have created the issue, you will automatically receive updates via email. If you want to track the progress or status of an issue you did not raise, simply subscribe to the issue using the ‘Subscribe’ button from the right-hand navigation.

### **Requesting a new Desktop Integration Type**&#x20;

Desktop Integration types (also known as AgencyCloud Integration Types) are specific to the Desktop API and require initial work from another department before it can be available via the Platform or in the Developer Edition.&#x20;

The request for a new integration type **should not be** submitted via the Foundations GitHub repo but should be requested via the Reapit Service Desk by a Reapit Customer.&#x20;

When the new Desktop Integration type is available, you can then raise a feature request for this to be implemented into the Platform.&#x20;

&#x20;

### **Label Definitions**&#x20;

#### **AgencyCloud**

Your issue relates to AgencyCloud (Desktop CRM) and therefore will require information, action or input outside of the Platform team, please see '[AgencyCloud](dev-requests.md#agencycloud-1)'.

**Investigate**

We need to research or gather more information relating to your request.&#x20;

**Product Decision**

The nature of your request requires product direction.&#x20;

**Too Big**

The feature request is too large to be handled in a single issue and requires the issue to be broken down by our development team.

&#x20;

### **Columns Definitions**&#x20;

**To Review**

All issues raised will be automatically added ‘To Review’. If the nature of your request is related to backend engineering (such as our REST API’s and Webhooks) it will be placed on the ‘Backend’ project. If you issue relates to the Foundations Mono Repo on Github and is associated to our frontend applications, it will be placed on our ‘Frontend Kanban’ project.&#x20;

**Not Ready**

If an issue needs technical investigation, more information is required, a product decision is needed or the issue is deemed too large, it will be moved to ‘Not Ready’. We will update the issue with the relevant label and comment if required.&#x20;

**Near term (0 – 4 months)**

If we identify an issue as short-term goal, we'll assess the effort required and outline a technical specification - please take the time to review this detail. **When we're ready to schedule the issue, it will be assigned to the relevant board where you can continue to track its progress to completion.**&#x20;

**Mid Term (5 – 8 months)**&#x20;

If we identify an issue as mid-term goal, we'll assess the effort required and may outline a technical specification. **When we're ready to schedule the issue, it will be moved to the ‘Near Term’ column.**&#x20;

**Long Term (9+ Months)**&#x20;

Whilst the nature of the request has been accepted, we are unable to commit to a specified sprint and therefore will assign your issue to the ‘Long Term’ column. We will regularly review any issues and where development capacity is available, or work is aligned with our Roadmap, the issue will be updated.

**To do**

The issue has been reviewed, a specification has been added and it is ready for development.

**Blocked**

The issue has been blocked and cannot be progressed, most likely because it’s dependent on another issue. In this instance, a comment will be added with a link to the dependent issue where applicable.&#x20;

**In Progress**

The development work is underway.&#x20;

**To Review**

The development work is currently being reviewed internally.&#x20;

**QA**

When an issue is completed by the dev team, it will be moved to QA where it will be verified by a member of the dev or product team on our development environment and assuming this is successful, will be released straight to production.&#x20;

**Done/Closed**

The work has been completed or the issue is no longer valid/required.

&#x20;

### **AgencyCloud**

Issues raised for features or bugs relating to AgencyCloud, will be handled by a different department, and therefore will not be triaged in the same way or added to a specific board.

Issues relating to AgencyCloud **should not be** submitted via the Foundations GitHub repo but should be requested via the Reapit Service Desk by a Reapit Customer.
