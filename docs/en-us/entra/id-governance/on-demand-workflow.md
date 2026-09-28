<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/on-demand-workflow -->
<!-- Sitemap-Last-Modified: 2026-03-13 -->

# Run a workflow on-demand

Scheduled workflows by default run every 3 hours, but can also run on-demand so that they can be applied to specific users whenever you see fit. A workflow can be run on demand for any user, and doesn't take into account whether or not a user meets the workflow's execution conditions. Running a workflow on-demand allows you to test workflows before their scheduled run. This testing, on a set of users up to 10 at a time, allows you to see how a workflow will run before it processes a larger set of users. Testing your workflows before their scheduled runs helps you proactively solve potential lifecycle issues more quickly.

## Run a workflow on-demand in the Microsoft Entra admin center

Use the following steps to run a workflow on-demand:

Note

To be run on demand, the workflow must be enabled.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **workflows**.
3. On the workflow screen, select the specific workflow you want to run.

   ![Screenshot of a list of Lifecycle Workflows workflows to run on-demand.](https://learn.microsoft.com/en-us/entra/id-governance/media/on-demand-workflow/on-demand-list.png)
4. Select **Run on demand**.
5. On the **select users** tab, select **add users**.
6. On the add users screen, select the users you want to run the on-demand workflow for.

   ![Screenshot of add users for on-demand workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/on-demand-workflow/on-demand-add-users.png)
7. Select **Add**.
8. Confirm your choices and select **Run workflow**.

   ![Screenshot of a workflow being run on-demand.](https://learn.microsoft.com/en-us/entra/id-governance/media/on-demand-workflow/on-demand-run.png)

## Run a workflow on-demand using Microsoft Graph

To run a workflow on-demand using API via Microsoft Graph, see: [workflow: activate \(run a workflow on-demand\)](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activate).

## Next steps

- [Customize the schedule of workflows](https://learn.microsoft.com/en-us/entra/id-governance/customize-workflow-schedule)
- [Delete a Lifecycle workflow](https://learn.microsoft.com/en-us/entra/id-governance/delete-lifecycle-workflow)
