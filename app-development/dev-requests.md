# Development requests

To request a new feature or report a bug, please visit the help section of the developer portal. You'll be directed to GitHub where you'll be able to create an issue directly in our public board. You should track the progress of your issue and communicate with developer directly in GitHub.

{% hint style="info" %}
Please do not raise requests though our service desk, customer success managers or other channels within the business with regard to the status of an issue.
{% endhint %}

## Our processes

After submitting an issue, your ticket will get triaged and categorised. From here, it will be assigned to the relevant GitHub project, depending on the nature of the work requested.

### Back end

Issues that align to back end engineering \(such as our REST APIs and webhooks\) will be managed using [Scrum Agile Framework](https://www.scrum.org/resources/what-is-scrum) using a 1 week sprint cycle. 

* Incoming issues that we identify as back end engineering will be given the `back end` label and assigned to the [Back end backlog](https://github.com/reapit/foundations/projects/6) public board
* New issues in the board are reviewed weekly as part of our backlog refinement sessions. To ensure your issue can be progressed quickly, please provide as much relevant information as possible.
* The team will discuss each issue and should we agree that development is warranted, we will commit to the work
* The issue will then enter our backlog and be prioritised against the needs of other customers and developers
* If we identity an issue as short term goal, we'll assess the effort required and outline a technical specification - please take the time to review this detail
* **When we're ready to schedule the issue, it will be assigned to a** [**dated GitHub project board**](https://github.com/reapit/foundations/projects) **for that particular sprint where you can continue to track its progress to completion**

### Front end

Issues relating to services within the [Foundations Mono Repo on Github ](https://github.com/reapit/foundations)\(mostly Front End but some back end services\), are managed using the [Kanban Agile methodology](https://kanbanize.com/kanban-resources/getting-started/what-is-kanban). For those not familiar with Kanban, it differs from Scrum in that it encourages a more fluid, continuous delivery cycle that is orientated around flow of issues rather than operating in sprint cycles.

* All incoming issues will be added to the board in the "icebox" column and assigned a "needs triage" label. 
* The team meet weekly on Fridays to look at new issues in the icebox where they will be validated for clarity and completeness of requirements, and that they fit into our long term product roadmap. If the issue is accepted by the team, it will be added to the backlog column for development.
* The backlog column will be groomed in priority order, with the top priority items at the top and the lowest at the bottom. Priority is measured against upcoming milestone target dates, customer and developer priority, and crucially from a Kanban process perspective, how achievable the task is given the current state of development.
* The top priority issues will be moved based on our best estimation of achievable work for the week into the 'ready for dev' column to be worked at in order. 
* Kanban methodology states that we should prioritise flow of work and minimise work in progress so if any unforeseen blockers are found by the development team when working on an issue, that issue will be de-scoped, returned to the backlog pending clarification, and the next item at the top of the backlog will be moved into ready for dev.
* When an issue is completed by the dev team, it will be moved to QA where it will be verified by a member of the dev or product team on our development environment and assuming this is successful, will be released straight to production.
* Any issues failing QA will be re-opened and moved to "in progress" to be fixed before any new issues is worked on. Where possible the number of "in progress" issues should never exceed the number of developers in the team.

### Agency cloud

Tickets logged for features or bugs relating to Agency Cloud, will be handled by a different department, and therefore will not be triaged in the same way or added to a specific board.

We will add comments where applicable or may request, depending the requirement, that you raise a ticket/log an issue externally \(outside of Github\).

