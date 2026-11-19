<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/create-lifecycle-workflow -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# Create a lifecycle workflow

Lifecycle workflows allow for tasks associated with the lifecycle process to be run automatically for users as they move through their lifecycle in your organization. Workflows consist of:

- **Tasks**: Actions taken when a workflow is triggered.
- **Execution conditions**: The who and when of a workflow. These conditions define which users this workflow should run against, and when \(trigger\) the workflow should run.

In the Microsoft Entra admin center, you can create and customize workflows for common scenarios by using built-in templates or by cloning an existing workflow. To build a workflow from scratch without using a template or an existing workflow, use Microsoft Graph.

## Prerequisites

Using this feature requires Microsoft Entra ID Governance or Microsoft Entra Suite licenses. To find the right license for your requirements, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).

- An ID verification profile with purpose set to `all` or `onboarding`, if you use either identity-verification template \(Preview\). You can create a profile before you start or select **Create new verification profile** during workflow creation. For profile configuration, see [Create an ID verification profile](https://learn.microsoft.com/en-us/entra/verified-id/how-to-create-id-verification-profile).

## Create a lifecycle workflow by cloning an existing workflow in the Microsoft Entra admin center

You can use an existing workflow as the starting point for a new workflow. The clone option is available only in the Microsoft Entra admin center.

To start cloning from the workflow list:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **Workflows**.
3. Select the workflow that you want to clone, and then select **Clone**.

   [![Screenshot of a selected workflow and the Clone option on the Lifecycle workflows page.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/clone-workflow-list.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/clone-workflow-list.png#lightbox)

You can also start cloning from the workflow creation experience:

1. Browse to **ID Governance** > **Lifecycle workflows** > **Create workflow**.
2. On the **Choose a workflow** page, find the **Clone an existing workflow** card, and then select **Browse workflows**.

   [![Screenshot of the Clone an existing workflow card on the Choose a workflow page.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/clone-workflow-template-card.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/clone-workflow-template-card.png#lightbox)
3. Select the workflow that you want to clone.

After you select a workflow to clone, the **Review + create** tab opens directly. Review the workflow settings, and then select **Create** to create the workflow without making changes.

To customize the workflow before you create it, select the other tabs and update the workflow details or configuration. When you're finished, return to the **Review + create** tab and select **Create**.

## Create a lifecycle workflow by using a template in the Microsoft Entra admin center

Use a built-in template as the starting point for a workflow, and customize it to meet your organization's needs. For available templates and their default settings, see [Lifecycle Workflows templates](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates).

To create a workflow based on a template:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Lifecycle Workflows Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#lifecycle-workflows-administrator).
2. Browse to **ID Governance** > **Lifecycle workflows** > **Create a workflow**.
3. On the **Choose a workflow** page, select the workflow template that you want to use.

   For identity-verification onboarding, select **Pre-hire identity verification initiation \(Preview\)** or **New Hire employee onboarding with identity verification \(Preview\)**. See [Lifecycle Workflows templates](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates).

   [![Screenshot of the workflow template gallery, including the two identity-verification templates in preview.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/templates-list.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/templates-list.png#lightbox)
4. On the **Basics** tab, enter a unique display name, description, and [administrative scope](https://learn.microsoft.com/en-us/entra/id-governance/manage-delegate-workflow) for the workflow.

   If you selected either identity-verification template, also select **Trigger type** on this tab. When you're finished, select **Next**.

   ![Screenshot of basic information about a workflow template.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/template-basics.png)
5. On the **Configure scope** tab, configure the execution conditions for the workflow. For other templates, also select the trigger type on this tab. For more information on what you can configure, see [Execution conditions](https://learn.microsoft.com/en-us/entra/id-governance/understanding-lifecycle-workflows#execution-conditions).
6. Under **Rule**, enter values for **Property**, **Operator**, and **Value**. The following screenshot gives an example of a rule being set up for a sales department. For a full list of user properties that lifecycle workflows support, see [Supported user properties and query parameters](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-rulebasedsubjectset?view=graph-rest-beta&preserve-view=true#supported-user-properties-and-query-parameters).

   ![Screenshot of scope configuration options for a lifecycle workflow template.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/template-scope.png)
7. To view your rule syntax, select the **View rule syntax** button. You can copy and paste multiple user property rules on the panel that appears. For more information on which properties you can include, see [User properties](https://learn.microsoft.com/en-us/graph/aad-advanced-queries?tabs=http#user-properties). When you finish adding rules, select **Next**.

   ![Screenshot of workflow rule syntax.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/template-syntax.png)
8. If you selected either identity-verification template, on the **Select identity verification profile** tab, select a profile from **Verified ID Profile**. If you need a new profile, select **Create new verification profile**. The profile's purpose must be set to `all` or `onboarding`. Select **Next: Review tasks**.

   For other templates, skip this step and continue to **Review tasks**.

   [![Screenshot of the identity verification profile selection tab, with the Verified ID Profile dropdown and Create new verification profile link.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/select-identity-verification-profile.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/select-identity-verification-profile.png#lightbox)
9. On the **Review tasks** tab, you can add a task to the template by selecting **Add task**. To enable an existing task on the list, select **Enable**. To disable a task, select **Disable**. To remove a task from the template, select **Remove**.

   For identity-verification tasks, select or change the profile on the workflow's **Select identity verification profile** tab, not in the task settings. For task settings and email requirements, see [Lifecycle workflow tasks](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks).

   When you're finished with tasks for your workflow, select **Next: Review and create**.

   ![Screenshot of adding tasks to templates.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/template-tasks.png)
10. On the **Review and create** tab, review the workflow's settings. Leave the scheduling checkbox cleared to test the workflow before automatic processing begins. Select it when you're ready to enable scheduled runs. Select **Create** to create the workflow.

    ![Screenshot of reviewing and creating a workflow.](https://learn.microsoft.com/en-us/entra/id-governance/media/create-lifecycle-workflow/template-review.png)

Important

In the Microsoft Entra admin center, a newly created workflow is enabled \(`isEnabled` is `true`\), but scheduling is disabled \(`isSchedulingEnabled` is `false`\) unless you select the scheduling checkbox. This lets you [run the workflow on-demand](https://learn.microsoft.com/en-us/entra/id-governance/on-demand-workflow) for a small audience before enabling scheduled processing. Disabling the workflow itself \(`isEnabled` is `false`\) prevents both scheduled and on-demand runs.

## Create a lifecycle workflow by using Microsoft Graph

To create a lifecycle workflow by using the Microsoft Graph API, see [Create workflow](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-workflows).

For API creation, explicitly set `isEnabled` and `isSchedulingEnabled` for the intended run mode. The values you set control workflow execution and scheduling; don't assume the admin center's checkbox defaults apply to an API request.

The three Preview tasks used by the two identity-verification templates are available only in Microsoft Graph `/beta`, not `/v1.0`. To create a workflow that includes these tasks, see [Create workflow \(beta\)](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-workflows?view=graph-rest-beta&preserve-view=true). For task definitions and arguments, see [Lifecycle workflow tasks](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-tasks).

Note

Microsoft Graph beta APIs are subject to change. Use of these APIs in production applications isn't supported.

## Related content

- [Manage a workflow's properties](https://learn.microsoft.com/en-us/entra/id-governance/manage-workflow-properties)
- [Manage workflow versions](https://learn.microsoft.com/en-us/entra/id-governance/manage-workflow-tasks)
