<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# Overview of Lifecycle Workflows APIs

Lifecycle Workflows is an Identity Governance service in Microsoft Entra ID that enables organizations to automate basic lifecycle processes for their users at three levels:

1. **Joiner**: When an individual comes into scope of needing access; for example, a new employee joining a company or organization.
2. **Mover**: When an individual moves between boundaries within an organization; for example, a user who was in marketing is now a member of the sales organization. This movement might require more access or authorization, or revocation of other privileges.
3. **Leaver**: When an individual leaves the scope of needing access, access might need to be revoked, and the user deprovisioned. For example, an employee who is retiring or terminated.

For this reason, lifecycle workflows can be referred to as the **Joiner-Mover-Leaver** \(JML\) workflow.

The lifecycle workflow APIs in Microsoft Graph allow you to automate the lifecycle workflows capabilities for your organization. This article introduced the set of APIs that enable the Lifecycle Workflows service in Microsoft Entra ID.

The lifecycle workflows APIs are defined in the OData subnamespace, microsoft.graph.identityGovernance.

Note

This article describes how to export personal data from a device or service. These steps can be used to support your obligations under the General Data Protection Regulation \(GDPR\). Authorized tenant admins can use Microsoft Graph to correct, update, or delete identifiable information about end users, including customer and employee user profiles or personal data, such as a user's name, work title, address, or phone number, in your [Microsoft Entra ID](https://www.microsoft.com/security/business/identity-access/microsoft-entra-id) environment.

## Workflows

Workflows are containers for the processes involved in managing the life cycle of users in the organization. At their core are *tasks* and *execution conditions*.

- [Tasks](#workflow-tasks) are specific actions that run automatically when a workflow is triggered.
- [Execution conditions](#execution-conditions) define the *scope* of "who" and the *trigger* of "when" a workflow runs.

To create workflows, we recommend using one of the [predefined workflow templates](#workflow-templates).

### Workflow templates

Microsoft Entra ID provides the following predefined **workflow templates** that define the templates for combinations of [*tasks*](#workflow-tasks) and *execution conditions* that can be part of a workflow. You can use the workflow templates to create your workflows programmatically.

| Workflow template type | Lifecycle category |
| --- | --- |
| Onboard pre-hire employee | Joiner |
| Onboard new hire employee | Joiner |
| Post-Onboarding new hire employee | Joiner |
| Real-time employee change | Mover |
| Employee group membership changes | Mover |
| Employee job profile change | Mover |
| Real-time employee termination | Leaver |
| Pre-Offboarding of an employee | Leaver |
| Offboard an employee | Leaver |
| Post-Offboarding of an employee | Leaver |

Use the [workflowTemplate resource type](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) and its associated methods to identify the preconfigured templates, and the tasks and execution conditions that they support, and copy and use the templates to [create your workflows](#create-and-manage-workflows) programmatically.

### General workflow information

Each workflow contains general descriptive information such as its identifier, name, description, and whether it's enabled to run as scheduled or on-demand.

### Workflow tasks

Workflow tasks are specific actions that run automatically when a workflow is triggered. Lifecycle workflows define the following preconfigured and read-only tasks allowed for the specified workflow categories. These task definitions show the settings for the task type, guiding you as you create tasks for your workflow.

Lifecycle Workflows currently support the following tasks:

| Task | taskdefinitionID | Category |
| --- | --- | --- |
| Send welcome email to new hire | 70b29d51-b59a-4773-9280-8841dfd3f2ea | Joiner |
| Send onboarding reminder email | 3C860712-2D37-42A4-928F-5C93935D26A1 | Joiner |
| Generate Temporary Access Pass and send via email to user's manager | 1b555e50-7f65-41d5-b514-5894a026d10d | Joiner |
| Request user access package assignment | c1ec1e76-f374-4375-aaa6-0bb6bd4c60be | Joiner, Mover |
| Assign licenses to users | 683c87a4-2ad4-420b-97d4-220d90afcd24 | Joiner, Mover |
| Send email to notify manager of user move | aab41899-9972-422a-9d97-f626014578b7 | Mover |
| Add user to groups | 22085229-5809-45e8-97fd-270d28d66910 | Joiner, Leaver, Mover |
| Add user to teams | e440ed8d-25a1-4618-84ce-091ed5be5594 | Joiner, Leaver, Mover |
| Enable user account | 6fc52c9d-398b-4305-9763-15f42c1676fc | Joiner, Leaver |
| Run a custom task extension | 4262b724-8dba-4fad-afc3-43fcbb497a0e | Joiner, Leaver, Mover |
| Disable user account | 1dfdfcc7-52fa-4c2e-bf3a-e3919cc12950 | Leaver |
| Remove user from selected group | 1953a66c-751c-45e5-8bfe-01462c70da3c | Joiner, Leaver, Mover |
| Remove users from all groups | b3a31406-2a15-4c9a-b25b-a658fa5f07fc | Leaver |
| Remove user from teams | 06aa7acb-01af-4824-8899-b14e5ed788d6 | Joiner, Leaver, Mover |
| Remove user from all teams | 81f7b200-2816-4b3b-8c5d-dc556f07b024 | Leaver |
| Remove all license assignments from user | 8fa97d28-3e52-4985-b3a9-a1126f9b8b4e | Leaver |
| Remove access package assignment for user | 4a0b64f2-c7ec-46ba-b117-18f262946c50 | Leaver, Mover |
| Remove selected license assignments from user | 5fc402a8-daaf-4b7b-9203-da868b05fc5f | Leaver, Mover |
| Remove all access package assignments for user | 42ae2956-193d-4f39-be06-691b8ac4fa1d | Leaver |
| Cancel all pending access package assignment requests for user | 498770d9-bab7-4e4c-b73d-5ded82a1d0b3 | Leaver |
| Delete user | 8d18588d-9ad3-4c0f-99d0-ec215f0e3dff | Leaver |
| Send email to manager before user last day | 52853a3e-f4e5-4eb8-bb24-1ac09a1da935 | Leaver |
| Send email on users last day | 9c0a1eaf-5bda-4392-9d9e-6e155bb57411 | Leaver |
| Send offboarding email to users manager after their last day | 6f22ddd4-b3a5-47a4-a846-0d7c201a49ce | Leaver |

Use the [taskDefinition resource type](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) and its associated methods to discover all the predefined tasks that can be configured for your workflow and the settings for the properties. The [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) resource type and its associated GET methods allow you to view the tasks configured for your workflow.

### Execution conditions

For every workflow task, there's an execution condition that defines the *scope* of "who" and the *trigger* of "when" a workflow and its associated tasks runs. For example, an execution condition can specify that a workflow runs for exiting employees, seven days before their employment end date, if they are in the R&D department. The associated task in the workflow can specify that the user is removed from the R&D teams and groups.

```json
⁄⁄Sample snippet for the executionConditions object

"executionConditions": {
    "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
    "scope": {
        "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
        "rule": "department eq 'R&D'"
    },
    "trigger": {
        "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
        "timeBasedAttribute": "employeeLeaveDateTime",
        "offsetInDays": -7
    }
}
```

When creating or updating a workflow, use the [workflowExecutionConditions resource type](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) to configure the execution conditions. Use this object to also configure a workflow that runs on-demand only.

### Create and manage workflows

After identifying the tasks and execution conditions that you want to define for your workflow, use the [workflow resource type](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0), and its associated methods to create and manage the workflow. You can create up to 100 workflows in a tenant. The category of the task must match the category of the workflow. Each workflow can have up to 25 tasks. Therefore:

- A task supported for only the "leaver" workflow category can't be specified in a "joiner" or "mover" workflow scenario, and vice versa.
- A task supported for "joiner", "mover", and "leaver" workflow categories can be specified in either a "joiner", "mover" or "leaver" workflow scenario.

You can schedule a workflow to run based on the [tenant-wide schedule](#settings) or run it on-demand. The tenant schedule can take care of scheduled new hires and terminations, while you can run a workflow on-demand immediately to terminate an employee's access if there is a sensitive event.

### Workflow versions

While a workflow is in use, you might need to update execution conditions and tasks for a workflow. However, Lifecycle Workflows doesn't allow you to update these properties for an existing workflow.

Instead of creating new workflows, use the [workflowVersion resource type](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) and its associated methods to create and manage a new workflow version, based on an existing workflow object. The workflow version can have a similar or different set of tasks and execution conditions.

## Reports

Lifecycle workflows support extensive reporting capabilities to track the status of workflow processing at the workflow run-level, task-level, and user-level.

For more information about the reporting capabilities for Lifecycle Workflows, see the [overview of Lifecycle Workflows reporting APIs](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-reporting-overview?view=graph-rest-1.0).

## Extensions

Sometimes, the built-in tasks might not be adequate to fulfill all your business scenarios. To extend your lifecycle management scenarios, Lifecycle Workflows supports defining custom tasks to integrate with external systems via Azure Logic Apps. For example, for a "leaver" scenario, you might also want to grant the user's manager access to the user's email account.

Use the [customTaskExtension resource type](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) and its associated methods to define the settings for your Azure Logic App.

## Settings

Each tenant defines a tenant-wide [schedule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) when all scheduled workflows are run. The tenant can adopt the Microsoft Entra ID-defined default schedule where workflows are run every three hours, or modify the schedule to run between 1 hour and 24 hours.

## License checks

Using this feature requires Microsoft Entra ID Governance licenses. To find the right license for your requirements, see [Compare generally available features of Microsoft Microsoft Entra ID](https://www.microsoft.com/security/business/identity-access-management/azure-ad-pricing).

## Related content

- [What are Lifecycle Workflows?](https://learn.microsoft.com/en-us/azure/active-directory/governance/what-are-lifecycle-workflows)
- [Concepts in Lifecycle Workflows](https://learn.microsoft.com/en-us/azure/active-directory/governance/understanding-lifecycle-workflows)
- [Tutorial: Automate employee offboarding tasks after their last day of work with Microsoft Graph](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-scheduled-leaver-graph)
- [Tutorial: Execute employee offboarding tasks in real-time on their last day of work with Microsoft Graph](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-offboard-custom-workflow-graph)
- [Tutorial: Automate employee onboarding tasks before their first day of work with Microsoft Graph](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-onboard-custom-workflow-graph)
