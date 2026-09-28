<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tutorial-offboard-custom-workflow-portal -->
<!-- Sitemap-Last-Modified: 2026-03-13 -->

# Execute employee termination tasks by using lifecycle workflows

This tutorial provides a step-by-step guide on how to execute a real-time employee termination by using lifecycle workflows in the Microsoft Entra admin center.

This *leaver* scenario runs a workflow on demand and accomplishes the following tasks:

- Remove the user from all groups.
- Remove the user from all Microsoft Teams memberships.
- Delete the user account.

For more information, see [Run a workflow on demand](https://learn.microsoft.com/en-us/entra/id-governance/on-demand-workflow).

## Prerequisites

Using this feature requires Microsoft Entra ID Governance or Microsoft Entra Suite licenses. To find the right license for your requirements, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

## Before you begin

To complete this tutorial, you must satisfy the prerequisites listed in this section before starting the tutorial as they aren't included in the actual tutorial. As part of the prerequisites for completing this tutorial, you need an account that has group and Teams memberships and that can be deleted during the tutorial. For comprehensive instructions on how to complete these prerequisite steps, see [Prepare user accounts for lifecycle workflows](https://learn.microsoft.com/en-us/entra/id-governance/tutorial-prepare-user-accounts).

The leaver scenario includes the following steps:

1. Prerequisite: Create a user account that represents an employee leaving your organization.
2. Prerequisite: Prepare the user account with group and Teams memberships.
3. Create the lifecycle management workflow.
4. Run the workflow on demand.
5. Verify that the workflow was successfully executed.

## Create a workflow by using the leaver template

Use the following steps to create a leaver on-demand workflow that executes a real-time employee termination by using lifecycle workflows in the Microsoft Entra admin center:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Select **ID Governance**.
3. Select **Lifecycle workflows**.
4. On the **Overview** tab, select **New workflow**.

   [![Screenshot of the Overview tab and the button for creating a new workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/new-workflow.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/new-workflow.png#lightbox)
5. From the collection of templates, choose **Select** under **Real-time employee termination**.

   [![Screenshot of selecting a workflow template for real-time employee termination.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/select-template.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/select-template.png#lightbox)
6. Configure basic information about the workflow like name, description, and [administrative scope](https://learn.microsoft.com/en-us/entra/id-governance/manage-delegate-workflow), then select **Next: Review tasks**.

   [![Screenshot of the tab for basic workflow information.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-leaver.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-leaver.png#lightbox)
7. Inspect the tasks if you want, but no additional configuration is needed. Select **Next: Select users** when you're finished.

   [![Screenshot of the tab for reviewing template tasks.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-tasks.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-tasks.png#lightbox)
8. On the **Select users** page, for **Selection type** choose **Select users to run now**. It allows you to select users for which the workflow will be executed immediately after creation. Regardless of the selection, you can run the workflow on demand later at any time, as needed.

   [![Screenshot of the option for selecting users to run now.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-users.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-users.png#lightbox)
9. Select **Add users** to designate the users for this workflow.

   [![Screenshot of the button for adding users.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-add-users.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-add-users.png#lightbox)
10. A panel with the list of available users appears on the right side of the window. Choose **Select** when you're done with your selection.

    [![Screenshot of a list of available users.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-user-list.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-user-list.png#lightbox)
11. Select **Next: Review and create** when you're satisfied with your selection of users.

    [![Screenshot of added users.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-review-users.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-review-users.png#lightbox)
12. Verify that the information is correct, and then select **Create**.

    [![Screenshot of the tab for reviewing workflow choices, along with the button for creating the workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-create.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/real-time-create.png#lightbox)

## Run the workflow

After the workflow is created, it runs automatically every three hours. Lifecycle workflows check every three hours for users in the associated execution condition, and execute the configured tasks for those users.

To run the workflow immediately, you can use the on-demand feature.

Note

You currently can't run a workflow on demand if it's set to **Disabled**. You need to set the workflow to **Enabled** to use the on-demand feature.

To run a workflow on demand for users by using the Microsoft Entra admin center:

1. On the workflow screen, select the specific workflow that you want to run.
2. Select **Run on demand**.
3. On the **Select users** tab, select **Add users**.
4. Add users.
5. Select **Run workflow**.

## Check tasks and workflow status

At any time, you can monitor the status of workflows and tasks. Three data pivots, users, runs, and tasks are currently available. You can learn more in the how-to guide [Check the status of a workflow](https://learn.microsoft.com/en-us/entra/id-governance/check-status-workflow). In this tutorial, you check the status by using the user-focused reports.

1. On the **Overview** page for the workflow, select **Workflow history**.

   [![Screenshot of the overview page for a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/workflow-history-real-time.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/workflow-history-real-time.png#lightbox)

   The **Workflow history** page appears.

   [![Screenshot of real-time workflow history.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/user-summary-real-time.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/user-summary-real-time.png#lightbox)
2. Select **Total tasks** for a user to view the total number of tasks created and their statuses.

   [![Screenshot of total tasks for a real-time workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/total-tasks-real-time.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/total-tasks-real-time.png#lightbox)
3. To add an extra layer of granularity, select **Failed tasks** for a user to view the total number of failed tasks assigned to that user.

   [![Screenshot of failed tasks for a real-time workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/failed-tasks-real-time.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/failed-tasks-real-time.png#lightbox)
4. Select **Unprocessed tasks** for a user to view the total number of unprocessed or canceled tasks assigned to that user.

   [![Screenshot of unprocessed tasks for a real-time workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/canceled-tasks-real-time.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/canceled-tasks-real-time.png#lightbox)

## Next steps

- [Prepare user accounts for lifecycle workflows](https://learn.microsoft.com/en-us/entra/id-governance/tutorial-prepare-user-accounts)
- [Complete tasks in real time on an employee's last day of work by using lifecycle workflow APIs](https://learn.microsoft.com/en-us/graph/tutorial-lifecycle-workflows-offboard-custom-workflow)
