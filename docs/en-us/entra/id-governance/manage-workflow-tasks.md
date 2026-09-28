<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/manage-workflow-tasks -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Manage workflow versions

Workflows created with Lifecycle Workflows are able to grow and change with the needs of your organization. Workflows exist as versions from creation. When you make changes to anything other than basic information, you create a new version of the workflow. For more information, see [Manage a workflow's properties](https://learn.microsoft.com/en-us/entra/id-governance/manage-workflow-properties).

Changing a workflow's tasks or execution conditions requires the creation of a new version of that workflow. Tasks within workflows can be added, reordered, and removed at will. Updating a workflow's tasks or execution conditions within the Microsoft Entra admin center triggers the creation of a new version of the workflow automatically. Making these updates in Microsoft Graph requires the new workflow version to be created manually.

## Edit the tasks of a workflow using the Microsoft Entra admin center

Tasks within workflows can be added, edited, reordered, and removed at will. To edit the tasks of a workflow using the Microsoft Entra admin center, you complete the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **workflows**.
3. Select the workflow that you want to edit the tasks of and on the left side of the screen, select **Tasks**.
4. You can add a task to the workflow by selecting the **Add task** button.

   [![Screenshot of adding a task to a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-tasks.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-tasks.png#lightbox)
5. You can enable and disable tasks as needed by using the **Enable** and **Disable** buttons.
6. You can reorder the order in which tasks are executed in the workflow by selecting the **Reorder** button. You can also remove a task from a workflow by using the **Remove** button.

   ![Screenshot of reordering tasks in a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-tasks-reorder.png)
7. After making changes, select **save** to capture changes to the tasks.

## Edit the execution conditions of a workflow using the Microsoft Entra admin center

To edit the execution conditions of a workflow using the Microsoft Entra admin center, you do the following steps:

1. On the left menu of Lifecycle Workflows, select **Workflows**.
2. On the left side of the screen, select **Execution conditions**.  [![Screenshot of the execution condition details of a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/execution-conditions-details.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/execution-conditions-details.png#lightbox)
3. On this screen, you're presented with **Trigger details**. You see a trigger type and attribute details. In the template you can edit the attribute details to define when a workflow runs.
4. Select the **Scope details** tab.  [![Screenshot of the execution scope page of a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/execution-conditions-scope.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/execution-conditions-scope.png#lightbox)
5. On this screen you can define rules for who the workflow runs. If the trigger **Scope type** is set as Rule-Based, you can define the rule using expressions on user properties. For more information on supported user properties, see [supported queries on user properties](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#user-properties). If the trigger scope type is group-based, you're able to select which group is the scope of the workflow.
6. After making changes, select **save** to capture changes to the execution conditions.

## See versions of a workflow using the Microsoft Entra admin center

1. On the left menu of Lifecycle Workflows, select **Workflows**.
2. On this page, you see a list of all of your current workflows. Select the workflow that you want to see versions of.
3. On the left side of the screen, select **Versions**.

   [![Screenshot of versions of a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-versions.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-versions.png#lightbox)
4. On this page, you see a list of the workflow versions.

   [![Screenshot of managing version list of lifecycle workflows.](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-versions-list.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/manage-workflow-tasks/manage-versions-list.png#lightbox)

## Create a new version of an existing workflow using Microsoft Graph

To create a new version of a workflow via API using Microsoft Graph, see: [workflow: createNewVersion](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-createnewversion)

### List workflow versions using Microsoft Graph

To list workflow versions via API using Microsoft Graph, see: [List versions \(of a lifecycle workflow\)](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-versions)

## Next steps

- [Check status of a workflow](https://learn.microsoft.com/en-us/entra/id-governance/check-status-workflow)
- [Customize workflow schedule](https://learn.microsoft.com/en-us/entra/id-governance/customize-workflow-schedule)
