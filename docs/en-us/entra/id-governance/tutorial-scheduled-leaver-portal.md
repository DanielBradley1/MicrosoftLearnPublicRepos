<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tutorial-scheduled-leaver-portal -->
<!-- Sitemap-Last-Modified: 2024-11-25 -->

# Automate employee offboarding tasks after their last day of work with the Microsoft Entra admin center

This tutorial provides a step-by-step guide on how to configure off-boarding tasks for employees after their last day of work with Lifecycle workflows using the Microsoft Entra admin center.

This post off-boarding scenario runs a scheduled workflow and accomplishes the following tasks:

1. Remove all licenses for user
2. Remove user from all Teams
3. Delete user account

## Prerequisites

Using this feature requires Microsoft Entra ID Governance or Microsoft Entra Suite licenses. To find the right license for your requirements, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

## Before you begin

To complete this tutorial, you must satisfy the prerequisites listed in this section before starting the tutorial as they aren't included in the actual tutorial. As part of the prerequisites for completing this tutorial, you need an account that has licenses and Teams memberships that can be deleted during the tutorial. For more comprehensive instructions on how to complete these prerequisite steps, you can refer to the [Preparing user accounts for Lifecycle workflows tutorial](https://learn.microsoft.com/en-us/entra/id-governance/tutorial-prepare-user-accounts).

The scheduled leaver scenario can be broken down into the following sections:

- **Prerequisite:** Create a user account that represents an employee leaving your organization
- **Prerequisite:** Prepare the user account with licenses and Teams memberships
- Create the lifecycle management workflow
- Run the scheduled workflow after last day of work
- Verify that the workflow was successfully executed

## Create a workflow using scheduled leaver template

Use the following steps to create a scheduled leaver workflow that will automatically perform off-boarding tasks for employees after their last day of work with Lifecycle workflows using the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Select **ID Governance**.
3. Select **Lifecycle workflows**.
4. On the **Overview** page, select **New workflow**.  [![Screenshot of selecting a new workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/new-workflow.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/new-workflow.png#lightbox)
5. From the templates, select **Select** under **Post-offboarding of an employee**.  [![Screenshot of selecting a leaver workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/select-leaver-template.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/select-leaver-template.png#lightbox)
6. Next, you configure the basic information about the workflow. This information includes when the workflow triggers, known as **Days from event**. So in this case, the workflow will trigger seven days after the employee's leave date. On the post-offboarding of an employee screen, add the following settings and then select **Next: Configure Scope**.  [![Screenshot of leaver template basics information for a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/leaver-basics.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/leaver-basics.png#lightbox)
7. Next, you configure the scope. The scope determines which users this workflow runs against. In this case, it is on all users in the Marketing department. On the configure scope screen, under **Rule** add the following, and then select **Next: Review tasks**. For a full list of supported user properties, see [Supported user properties and query parameters](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-rulebasedsubjectset?view=graph-rest-beta&preserve-view=true#supported-user-properties-and-query-parameters)  [![Screenshot of reviewing scope details for a leaver workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/leaver-scope.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/leaver-scope.png#lightbox)
8. On the following page, you can inspect the tasks if desired but no additional configuration is needed. Select **Next: Select users** when you're finished.  [![Screenshot of leaver workflow tasks.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/review-leaver-tasks.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/review-leaver-tasks.png#lightbox)
9. On the review screen, verify the information is correct and select **Create**.  [![Screenshot of a leaver workflow being created.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/create-leaver-workflow.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/create-leaver-workflow.png#lightbox)

Note

Select **Create** with the **Enable schedule** box unchecked to run the workflow on-demand. You may enable this setting later after checking the tasks and workflow status.

## Run the workflow

Now that the workflow is created, it automatically runs every 3 hours. This means lifecycle workflows check every 3 hours for users in the associated execution condition, and executes the configured tasks for those users. However, for the tutorial, we would like to run it immediately. To run a workflow immediately, we can use the on-demand feature.

Note

Be aware that you currently cannot run a workflow on-demand if it is set to disabled. You need to set the workflow to enabled to use the on-demand feature.

To run a workflow on-demand, for users using the Microsoft Entra admin center, do the following steps:

1. On the workflow screen, select the specific workflow you want to run.
2. Select **Run on demand**.
3. On the **select users** tab, select **add users**.
4. Add a user.
5. Select **Run workflow**.

## Check tasks and workflow status

At any time, you can monitor the status of the workflows and the tasks. As a reminder, there are three different data pivots, users runs, and tasks that are currently available. You can learn more in the how-to guide [Check the status of a workflow](https://learn.microsoft.com/en-us/entra/id-governance/check-status-workflow). In the course of this section, we look at the status using the user focused reports.

1. To begin, select the **Workflow history** tab to view the user summary and associated workflow tasks and statuses.  [![Screenshot of the workflow history summary.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/workflow-history-post-offboard.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/workflow-history-post-offboard.png#lightbox)
2. Once the **Workflow history** tab is selected, you land on the workflow history page as shown:  [![Screenshot of the workflow history overview.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/user-summary-post-offboard.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/user-summary-post-offboard.png#lightbox)
3. Next, you can select **Total tasks** for the user Jane Smith to view the total number of tasks created and their statuses. In this example, there are three total tasks assigned to the user Jane Smith.  
   [![Screenshot of workflow's total tasks.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/total-tasks-post-offboard.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/total-tasks-post-offboard.png#lightbox)
4. To add an extra layer of granularity, you can select **Failed tasks** for the user Wade Warren to view the total number of failed tasks assigned to the user Wade Warren.  [![Screenshot of workflow failed tasks.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/failed-tasks-post-offboard.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/failed-tasks-post-offboard.png#lightbox)
5. Similarly, you can select **Unprocessed tasks** for the user Wade Warren to view the total number of unprocessed or canceled tasks assigned to the user Wade Warren.  [![Screenshot of workflow unprocessed tasks.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/canceled-tasks-post-offboard.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/canceled-tasks-post-offboard.png#lightbox)

## Enable the workflow schedule

After running your workflow on-demand and checking that everything is working fine, you might want to enable the workflow schedule. To enable the workflow schedule, you select the **Enable Schedule** checkbox on the Properties page.

[![Screenshot of workflow enabled schedule.](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/enable-schedule.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/tutorial-lifecycle-workflows/enable-schedule.png#lightbox)

## Next steps

- [Preparing user accounts for Lifecycle workflows](https://learn.microsoft.com/en-us/entra/id-governance/tutorial-prepare-user-accounts)
- [Automate employee offboarding tasks after their last day of work using Lifecycle Workflows APIs](https://learn.microsoft.com/en-us/graph/tutorial-lifecycle-workflows-scheduled-leaver)
