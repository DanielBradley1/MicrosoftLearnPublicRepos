<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Managing AI experiences enabled by usage-based billing

Use spending policies in the Cost Management dashboard to control access and Copilot Credit spending for AI experiences enabled by usage-based billing.

For initial configuration and billing options, see [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup).

To review consumption, see [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending).

Important

For a list of services managed by usage-based billing method, see [Services managed by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits#services-managed-by-usage-based-billing). Microsoft is working to bring more agents and services to be managed by this experience.

To learn more about discovery settings for AI experiences enabled by usage-based billing, see [Discovery setting for AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).

Note

If you are looking for information on other usage-based billing products, use the following articles:

- For Copilot Chat, SharePoint Agents, or Microsoft Copilot Retrieval API \(Preview\), see [Microsoft Copilot pay-as-you-go service overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).
- For Copilot Studio, see [Copilot Studio pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing#copilot-studio-pay-as-you-go).
- For non-Copilot services; Microsoft 365 Backup, Microsoft 365 SharePoint Storage, and High Volume Email, see [Set up and manage pay-as-you-go billing in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node).

## Before you begin

Review the administrator roles and permissions required to create or manage spending policies. For more information, see [Roles and requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#roles-and-requirements).

Before you create additional spending policies, complete the initial usage-based billing setup and activate the default spending policy. For more information, see [Getting started with usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#getting-started-with-usage-based-billing).

## Add Identity-based spending policy

Use this option when you want a policy to apply to the people who use selected agents and services. For example, a group using Cowork.

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select the **Configuration** tab and then select **+ Add spending policy**. You can create any number of spending policies.
3. After you select **+ Add spending policy**, complete the following sections in the add spending policy workflow:

   - Define the policy scope
   - Select agents and services
   - Set limits and alerts
   - Select a billing method
   - Review and add the policy

### Policy scope

The system supports user, group, and tenant policies.

Give the policy a name and select the specific groups that the policy applies to.

1. Create and name the policy and then choose **Identity** as the scope. Use this option when you need to manage usage by users or groups for a supported service.
2. Select the users or groups to which the policy applies. By default, **All users** is selected. To target this rule to a subset of users, switch to **Specific groups** and select the directory group. You can also select multiple groups.
3. At this time, you can only support specific users and resource accounts through security groups. To add specific users or resource accounts to a spending policy, ensure they're in a security group first and then select specific groups from the policy setup. For more details on resource accounts, see [⁠Manage - Resource accounts for voice applications](https://learn.microsoft.com/en-us/microsoftteams/aa-cq-manage-resource-accounts).
4. Select **Next**.

### Select agents and services

When a spending policy has **Auto-apply new services** turned on, newly supported Microsoft Copilot services and agents are automatically added to the policy as they become available.

1. Select the agents and services that users and groups in this policy can access.
2. Use the check box to select the agents and services that can consume credits against the billing method tied to this policy.
3. By default, the **Auto-apply new services** toggle is selected for spending policies.

   - When the setting is on, newly supported Microsoft Copilot services and agents are automatically added to the policy.
   - When the setting is off, future services and agents aren't automatically included. Administrators must review and add the new services and agents to the policy.

4. Select **Next**.

Note

Turn off **Auto-apply new services** for any policy that shouldn't automatically govern future supported services or agents.

### Set limits and alerts

Microsoft continuously evaluates customer usage patterns and industry trends to define healthy spending policies for usage-based billing scenarios. We're continuing to refine these guardrails so customers can successfully use Copilot capabilities. As a result, recommendations and policy requirements may evolve, and administrators may see updated guidance in the product experience.

- **Monthly budget limit for users:** Set at least 2,000 credits per user per month
- **Monthly spending limit for policy:** Set the monthly spending limit for policy at or above the required minimum for eligible users covered by the policy

What if your limit is lower than recommended?

To help ensure a good user experience, your policy must meet the minimum. If your budget meets that minimum but is below the recommended amount, you can still save your policy. We'll suggest a limit that may better support your users.

1. For the users and groups that you selected for this policy, select the credit limits that apply to them, similar to what you did for the default spending policy.
2. Select the monthly spending limit for this policy.

   - **Unlimited monthly budget**: Applies to users and groups in this policy on a monthly basis.
   - **Limited monthly budget**: When you select a limited monthly budget, you limit the number of credits that this policy can spend each month.
   - When users hit the limit, they lose access to agents and services for the rest of the month until credits reset on the first of the month.
   - The policy always uses prepaid credits first, whether through capacity packs or through pre-purchase plans, before moving to pay-as-you-go.

3. Select monthly budget limits for users \(optional\). Use the toggle to select this option and to set a monthly limit for users to prevent a single person from spending all available credits.

   - Specify the maximum credit limit users can spend per month.

4. Configure policy-level alerts:

   - Specify the usage threshold for the policy.
   - Select the administrators or stakeholders who must receive email notifications when policy usage reaches the threshold.
   - Review the prepopulated administrator email address and add other recipients as needed.

5. If the policy has a monthly per-user limit, configure user-level threshold notifications:

   - Turn on user notifications for the policy.
   - Specify the threshold percentage at which users receive an email.


   User-level notifications alert users as they approach their spending limit. The user-level notifications are separate from notifications sent to administrators or stakeholders about overall policy consumption.

6. Select **Next**.

### Select billing method

By default, the field selects the billing method tied to the default spending policy.

If you're a Global administrator or a Billing administrator, you can override this selection and select how this policy should be billed. This feature enables you to do departmental billing and vary billing methods for each group, department, or set of users.

**For Global or Billing administrators**

1. Select **Change** to override.
2. If your tenant has capacity packs, you can choose to use them.
3. Alternatively, you can choose a different Azure subscription to bill against. For more information, see [Configure billing methods](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#configure-billing-method).

### Review and add the policy

1. Before you create the spending policy, verify:

   - Its user and group scope.
   - Its policy-level and per-user limits.
   - Its policy and user notification thresholds.
   - Its selected services and agents.
   - The Auto-apply new services setting.
   - Its billing method.

2. Select **Create spending policy** to complete the setup.
3. You're notified that the spending policy is created. Select **Done**. The spending policy now shows up in the Configuration list and starts applying to scoped users immediately.

## Understand how user or Identity-based spending policies apply to users

The following behaviors can affect which spending policy applies to a user and how previously consumed credits are handled.

### Users in multiple policies

Users can belong in multiple spending policies. If a user is in more than one policy for the same service, the system assigns the user a policy based on the following order:

1. Highest per-user limit
2. If tied, the largest overall policy limit
3. If still tied, the most recently created policy

If a policy doesn't have a per-user limit set, the system uses its overall policy limit as the per-user value for this comparison. The chosen policy applies in full and settings from other policies aren't combined.

When users reach their limit within a policy, they can request more credits but they don't default to other policies. The system keeps the user on the assigned policy and doesn't reevaluate the user against other policies.

To understand more about overlapping policies in Resource-based spending policies, see [Understand Policy hierarchy](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-studio-costs#understand-policy-hierarchy).

### Users who move between Microsoft Entra ID groups

If a user moves from one Microsoft Entra ID group to another during a billing period, the new group's spending policy becomes effective for the user. However, the user's consumption history carries forward across the policy change.

Credits consumed under the previous spending policy remain part of the user's consumption history and are accounted for when enforcing the spending limit under the new policy. Moving a user between groups or spending policies doesn't reset the user's consumption.

Spending limits are preserved when users switch between billing policies.

For example:

- A user belongs to Group 1, which is governed by Spending Policy A.
- The user consumes 500 credits under Spending Policy A.
- During the same billing period, the user moves to Group 2, which is governed by Spending Policy B.
- When Spending Policy B becomes effective, the user's 500 credits of prior consumption remain accounted for.
- The user can continue consuming credits up to the spending limit configured in Spending Policy B.

This behavior provides consistent user-level tracking and reduces the risk that a user could receive a new spending allocation by moving between departments, projects, groups, or spending policies.

## Add Resource-based spending policy

For steps and details on how to create a resource-based spending policy in the Microsoft 365 admin center, see [Create resource-based spending policies](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-studio-costs#add-resource-based-spending-policy)

To understand more about overlapping policies in Resource-based spending policies, see [Understand Policy hierarchy](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-studio-costs#understand-policy-hierarchy).

## Edit spending policy

To edit an identity-based spending policy, follow these steps:

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select the **Configuration** tab.
3. Select the spending policy you want to edit.
4. The spending policy details fly-out opens, where you can modify its settings. This includes:

   1. **Scope**
   2. **Agents and services**
   3. **Billing method**
   4. **Spending limits**
   5. **Alerts, and Email alert settings**

5. After making the necessary changes, select **Save changes** to apply the updates to the spending policy.

Note

You can't convert an existing identity-based policy into a resource-based policy.

## Delete spending policy

To delete a spending policy, follow these steps:

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select the **Configuration** tab.
3. From the list of spending policies, locate the spending policy that you want to delete.
4. Select the More actions menu \(⋮\) next to the spending policy.
5. Select **Delete**.
6. In the confirmation dialog, select **Delete** to remove the spending policy.

When you delete a spending policy, the users and groups assigned to that policy are no longer governed by its spending limits.

Deleting a spending policy doesn't remove, reallocate, or reset Copilot Credits. Spending policies only define access and spending limits, not credit allocation. Any usage that occurred before the policy was deleted remains available in usage and reporting views.

If another spending policy applies to a user through group membership, the user continues to consume Copilot Credits under the applicable policy. Previously consumed credits remain part of the user's consumption history for the current billing period.

Note

Spending policies are limit-based controls and don't reserve or allocate Copilot Credits to users or groups.

## Related articles

- [Understand usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup)
- [Manage Copilot Studio costs in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-studio-costs).
- [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending)
- [Usage-based-billing guidance for CSPs, partner-managed customers, and MACC](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-csp-partner-macc)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
