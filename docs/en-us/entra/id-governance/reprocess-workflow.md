<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/reprocess-workflow -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Reprocess workflow runs using Lifecycle Workflows

Reprocessing workflows is a feature that allows workflows created using lifecycle workflows to be run again to ensure workflows operate as intended. This is useful when dealing with runs that failed for some reason. This article provides step-by-step instructions for reprocessing workflows using the Microsoft Entra admin center, enabling you to quickly and efficiently manage workflow runs for users or specific runs.

## Reprocess a workflow using the Microsoft Entra admin center

To reprocess a workflow using the Microsoft Entra admin center, complete the following steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **workflows**.
3. On the workflow list screen, select the workflow you want to reprocess.
4. On the workflow overview page, select **Workflow history**.
5. On the workflow history screen, the **Users** tab is automatically open, allowing you to see a list of users processed by the workflow.
6. To reprocess a workflow for a user, select the user you want to reprocess a workflow for, and select **Reprocess**.  ![Screenshot of reprocessing a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/reprocess-workflow/reprocess-workflow.png)

   Note

   You're able to reprocess up to 10 users at a time.
7. If you want to reprocess a workflow based on a run, select the **Runs** tab.
8. On the **Runs** tab, you can see a full list of workflow runs. Select the run you want to reprocess and select **Reprocess**.

   Note

   Only a single run can be reprocessed at a time.

## Next steps

- [Lifecycle Workflows history](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-history)
- [Auditing Lifecycle Workflows](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-audits)
