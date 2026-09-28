<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/workflow-sensitivity-labels -->
<!-- Sitemap-Last-Modified: 2026-03-13 -->

# Sensitivity labels in Lifecycle Workflows

Maintaining and classifying data within your environment is an important part in maintaining a secure environment. Sensitivity labels from Microsoft Purview Information Protection let you classify and protect your organization's data, while making sure that user productivity and their ability to collaborate isn't hindered. With sensitivity labels in Lifecycle Workflows, administrators are able to quickly view the sensitivity labels of groups and teams during workflow creation, and editing.

The following tasks support viewing sensitivity labels:

- [Add user to groups](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks#add-user-to-groups)
- [Add user to teams](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks#add-user-to-teams)
- [Remove user from selected groups](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks#remove-user-from-selected-groups)
- [Remove user from selected teams](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks#remove-user-from-selected-teams)

## License requirements

Using this feature requires Microsoft Entra ID Governance or Microsoft Entra Suite licenses. To find the right license for your requirements, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

## Prerequisites

Along with Microsoft Entra licenses required for Lifecycle workflows, you must also have:

- [A created sensitivity label](https://learn.microsoft.com/en-us/purview/create-sensitivity-labels?tabs=classic-label-scheme#create-and-configure-sensitivity-labels)
- [A sensitivity label applied to the group or team you want to use with a Lifecycle workflow](https://learn.microsoft.com/en-us/purview/sensitivity-labels-teams-groups-sites#using-sensitivity-labels-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites)

## View assigned sensitivity labels during workflow creation

To view the sensitivity labels of groups and teams using Lifecycle workflows during workflow creation, do the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **Create a workflow**.
3. On the **Choose a workflow** page, select the workflow template that you want to use.
4. Add Basic information, Trigger type, and scope details for the workflow.
5. On the tasks page, add the task you want to use to view sensitivity labels with. Task availability is based on which template you selected to create your workflow. For more information on workflow templates, see: [Lifecycle Workflows templates and categories](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates).
6. After adding the group-related tasks to the workflow, select the task, and then select **select groups**.  ![Screenshot of selecting group in workflows.](https://learn.microsoft.com/en-us/entra/id-governance/media/workflow-sensitivity-labels/select-groups-workflow.png)
7. On the list pane, you're able to see a list of groups or teams that can be selected, and their sensitivity labels.  ![Screenshot of adding groups to workflow along with their sensitivity labels.](https://learn.microsoft.com/en-us/entra/id-governance/media/workflow-sensitivity-labels/add-group-sensitivity-label.png)
8. After adding the group or team to the task, select **Next** to move to the review screen, and **Create** to create the workflow.

## View assigned sensitivity labels on existing workflow tasks

Sensitivity labels of groups and teams used within existing tasks of a workflow can be viewed by doing the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **workflows**.
3. Select the workflow that has the task that you want to view.
4. On the workflow overview screen, select **Tasks**.
5. On the tasks screen, select the specific task related to sensitivity you want to view.
6. On the task overview screen, select the group or teams selection option.
7. On the list screen, you're able to see the group currently assigned to the task, a list of groups or teams that can be added to the task, and also their sensitivity labels.  ![Screenshot of teams and sensitivity labels within a task for an existing workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/workflow-sensitivity-labels/sensitivity-label-existing-workflow.png)

## Related content

- [Lifecycle Workflow built-in tasks](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks)
