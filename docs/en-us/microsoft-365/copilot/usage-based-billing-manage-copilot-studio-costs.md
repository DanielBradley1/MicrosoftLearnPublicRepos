<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-studio-costs -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Manage Copilot Studio costs in the Microsoft 365 admin center

Manage Copilot Studio spending in the Microsoft 365 admin center by creating policies for environments or individual agents. You can set spending limits, choose a billing method, and monitor Copilot Credit usage.

## Move Copilot Studio cost management to the Microsoft 365 admin center

To opt in, create a Microsoft 365 admin center resource-based spending policy. Until then, your existing Power Platform admin center configuration remains in effect. No separate migration step is required.

For resources covered by the spending policy, Copilot Credit management moves to the Microsoft 365 admin center, replacing their Power Platform admin center capacity allocations and linked billing plans.

Important

Start by creating a resource-based spending policy and set Policy scope to **Specific environments** to transition gradually. Selecting **All environments** makes this change for every environment in the tenant.

## Before you begin

Before creating a resource-based spending policy for Copilot Studio agents, ensure that you have the necessary roles in the Microsoft 365 admin center. You should also have a clear understanding of which environments and agents you want to manage under this policy.

Assign roles before creating the first policy. The recommendations are role assignments to consider; an existing Power Platform role does not itself become a Microsoft 365 role. For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

| Who | Recommended Role in Microsoft Admin Center | What they do |
| --- | --- | --- |
| Global Administrator | No change | Tenant-wide administration, including billing. |
| Power Platform Administrator or Dynamics 365 Administrator | AI Administrator | Manage spending policies. |
| Environment Administrator | AI Reader | View consumption when needed. |

## Choose what the policy covers

The policy scope controls which usage a policy applies to. To manage Copilot Studio spending by agent or by environment, under **Policy scope**, select **Resources**. Then choose one of the following options:

| Option | What it covers | Choose it when you want to |
| --- | --- | --- |
| **Specific resource** | Individual agents that you select. | Manage spending for a particular agent. |
| **Resource collection** | All supported usage in the environments that you select, including apps and workflows deployed in those environments. | Use one policy to cover the supported usage across one or more environments. |

To know what happens when more than one policy applies, see [Understand Policy hierarchy](#understand-policy-hierarchy).

### Select agents or environments

- **For specific agents:** Select **Resources > Specific resource**, search for each agent by name, and then select it.

  Apps and workflows don't currently appear in the agent selector, so you can't select an individual app or workflow. To cover them, create a policy for the environment where they're deployed.
- **For environments:** Select **Resources > Resource collection**, and then select the **Specific environments**. You can create a spending policy for one environment or multiple environments.

Note

Start with **Specific environments** to gradually transition spending management to the Microsoft 365 admin center. Selecting **All environments** applies the resource-based spending policy to every environment and replaces their existing Power Platform admin center spending controls.

Note

Resource-based policies created in the Microsoft 365 admin center don't apply to AI Builder features or the credits they consume. AI Builder powers prompts used as tools, in topics, and as nodes in agent flows. Don't move resources, agents, workflows or environments that use AI Builder to these policies. For more information, see [Add a prompt node to an agent flow](https://learn.microsoft.com/en-us/microsoft-copilot-studio/prompt-node-workflow) and [Use prompts to make your agent or agent flow perform specific tasks](https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-prompt-node).

## Add Resource-based spending policy

In the Microsoft 365 admin center, create a resource-based spending policy for the agent, resource, or environment you want to manage. As part of the standard policy setup, define the scope, set the spending limit, and choose the billing method.

You don't need to remove the existing Power Platform policy or complete a separate opt-in step. Once the new policy is linked to the environment, it takes precedence for that scope.

When you create a policy: After you link an environment to a Microsoft 365 spending policy, allow up to 12 minutes for the new policy to apply.

Use this option when you want usage to follow an agent or environment rather than the identity of the person using it. The resource list only shows resources that consume Copilot Credits.

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select **Configuration**, and then select **Add spending policy**.
3. Enter a name for the policy, then select **Resources** as its scope.
4. Choose what the policy covers:

   - **Specific resources**: Choose Specific resources when particular agents need their own policy or billing method. Select the agents you want to manage, including agents in different environments.
   - **Specific environments**: Choose Specific environments when you want to move and manage a limited set of environments first. Select one or more environments to cover the supported resources in them.
   - **All environments**: All existing environments and automatically includes new environments. Before you select **All environments**, note that creating this policy brings Copilot Credit management for those environments into the Microsoft 365 admin center; the corresponding Power Platform admin center capacity allocations and linked billing plans no longer apply. If you're trying the transition, start with a specific environment rather than all environments.

5. Review the resources shown for your selection. Only resources that consume Copilot Credits appear in the list.
6. Choose No limit or set a monthly spending limit for the policy. You can also set a per-agent limit so that no single agent covered by the policy uses more than the amount you specify. For example, a policy could have a 10,000-credit limit and a 1,000-credit per-agent limit.
7. Configure alert thresholds and recipients as needed.
8. Use the default billing method or choose an available billing-method override. Review the settings, then create the policy.

## Edit or remove a spending policy

You can edit an existing resource-based policy to add or remove environments. You can't convert an existing identity-based policy into a resource-based policy. To manage a resource or environment when you have only an identity-based policy, create a new resource-based policy.

If you remove an environment from a spending policy or delete the resource-based spending policy, the applicable Power Platform admin center policy resumes for that environment automatically. The same fallback applies when you delete the Microsoft 365 admin center resource-based spending policy that covered it; no additional Power Platform setup is required.

## Understand policy hierarchy

When more than one cost control could apply to Copilot Studio usage, check them in this order:

**Microsoft 365 admin center before Power Platform admin center**. If a spending policy in the Microsoft 365 admin center covers the environment or agent, its controls take precedence over the Power Platform admin center controls for that usage.

**Resource-based policy before identity-based policy**. Within the Microsoft 365 admin center, a policy for the agent or its environment takes precedence over a policy for the person using the agent. If multiple policies of the same type apply, the policy with the highest applicable per-agent or per-user limit applies. Spending limits from overlapping policies aren't combined.

**Example**: Suppose your organization has a spending policy for an HR agent and an identity-based policy for a user who runs it. The HR agent's resource policy applies, regardless of who runs the agent.

**Overlapping policies**. If you have a resource-based **All-environments** policy and a **Specific resource** HR agent policy, the policy with the higher per-agent limit applies. If the agent reaches that limit, usage does not fall back to the user's identity-based policy.

Suppose an agent is covered by both an environment-specific spending policy and an agent-specific spending policy. If the agent-specific policy provides a higher per-agent spending limit, that policy applies to the agent. The limits from the two policies aren't added together.

## Understand what happens to Power Platform controls

When you create a resource-based spending policy in the Microsoft 365 admin center that covers a Copilot Studio environment, the Microsoft 365 admin center spending policy takes precedence over the spending policy configured in the Power Platform admin center.

The Power Platform spending policy no longer applies to the environment while it's covered by the Microsoft 365 admin center spending policy.

Existing Power Platform capacity allocations and linked billing plans don't apply while spending for that environment is managed by a resource-based spending policy in the Microsoft 365 admin center. Creating a new resource-based spending policy in Microsoft 365 admin center doesn't require you to delete the Power Platform configuration.

Environments that aren't linked to a Microsoft 365 admin center resource-based spending policy continue under their applicable Power Platform configuration during the opt-in period.

### Check where an environment's spending is managed

In the Power Platform admin center, the **Manage capacity** experience indicates when Copilot Credits for an environment are managed by a Microsoft 365 admin center resource-based spending policy and explains that Power Platform capacity allocations and linked billing plans don't apply. The **Manage agent** experience also displays a message when an agent is covered by a policy. Use these indicators to identify which experience manages spending during the transition.

For Power Platform capacity-management details, see [Manage Copilot Credits and capacity for Copilot Studio](https://learn.microsoft.com/en-us/power-platform/admin/manage-copilot-studio-copilot-credits-capacity).

## Monitor usage and troubleshoot

You can view consumption by environment and agent. For more information, see [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending).
