<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits -->
<!-- Sitemap-Last-Modified: 2026-10-02 -->

# Managing AI experiences enabled by usage-based billing

Use spending policies in the Cost Management dashboard to control access and Copilot Credit spending for AI experiences enabled by usage-based billing.

Administrators can:

- Create spending policies that control access to supported agents and services.
- Automatically apply existing spending policies to future supported services and agents.
- Configure organizational and user-level spending limits.
- Configure threshold notifications for administrators and users.
- Assign model profiles and billing methods.

For initial configuration and billing options, see [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup). To review consumption, see [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending).

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

## Add spending policy

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select the **Configuration** tab and then select **+ Add spending policy**. You can create any number of spending policies.
3. After you select **+ Add spending policy**, complete the following sections in the add spending policy workflow:

   - Define the policy scope
   - Select agents and services
   - Set limits and alerts
   - Model profiles
   - Select a billing method
   - Review and add the policy

### Define the policy scope

The system supports user, group, and tenant policies.

Give the policy a name and select the specific groups that the policy applies to.

1. Create and name the policy.
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

Microsoft continuously evaluates customer usage patterns and industry trends to help define healthy spending policies for usage-based billing scenarios to support a high-quality user experience. We are actively learning and refining these guardrails to ensure customers can successfully use Copilot capabilities. As a result, recommendations and policy requirements may evolve over time, and administrators may see updated guidance over time in the product experience intended to maintain a quality user experience.

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

### Model profiles

Model profiles are reusable sets of model providers and models that you can apply to spending policies. Use model profiles to control which models are available for supported experiences.

You can also add model profiles directly from **Cost Management > Configuration** tab. For more information, see [Configure model profiles](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#configure-model-profiles).

To understand more about model profile considerations, see [Model profile considerations](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#model-profile-considerations).

Note

Model profiles are currently available only for **Copilot Cowork**. The **Model profiles** step appears only when you select **Cowork** in a spending policy.

To create and assign a model profile while creating a spending policy:

1. By default, supported models and providers that are available in your organization can be used. You can keep the default model selection or customize model access by applying a model profile. In **Model profiles**, select from one of the following options:

   - **Use default model selection** to allow Cowork to use all supported models and providers available in your tenant.
   - **Customize model selection** to apply an existing model profile or create a new one.

2. If you choose **Customize model selection**, select an existing profile or select **Create new model profile**.
3. When creating a model profile:

   1. Enter a name for the profile.
   2. Select the model providers and models to include in the profile. You must select at least two models.
   3. Choose whether Microsoft can select the most comparable model to maintain availability during a model-specific service interruption. If you don't allow Microsoft to select the most comparable model, users might experience a service interruption when a selected model becomes unavailable.
   4. Save the model profile.

4. Select **Next**.

After you create a model profile, you can reuse it across applicable spending policies.

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
   - Its selected model profile.
   - The Auto-apply new services setting.
   - Its billing method.

2. Select **Create spending policy** to complete the setup.
3. You're notified that the spending policy is created. Select **Done**. The spending policy now shows up in the Configuration list and starts applying to scoped users immediately.

## Understand how spending policies apply to users

The following behaviors can affect which spending policy applies to a user and how previously consumed credits are handled.

### Users in multiple policies

Users can belong in multiple spending policies. If a user is in more than one policy for the same service, the system assigns the user a policy based on the following order:

1. Highest per-user limit
2. If tied, the largest overall policy limit
3. If still tied, the most recently created policy

If a policy doesn't have a per-user limit set, the system uses its overall policy limit as the per-user value for this comparison. The chosen policy applies in full and settings from other policies aren't combined.

When users reach their limit within a policy, they can request more credits but they don't default to other policies. The system keeps the user on the assigned policy and doesn't reevaluate the user against other policies.

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

## Edit spending policy

To edit a spending policy, follow these steps:

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select the **Configuration** tab.
3. Select the spending policy you want to edit.
4. The spending policy details fly-out opens, where you can modify its settings. This includes:

   1. Scope
   2. Agents and services
   3. Model profile
   4. Billing method
   5. Spending limits
   6. Alerts, and Email alert settings

5. After making the necessary changes, select **Save changes** to apply the updates to the spending policy.

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
- [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending)
- [Usage-based-billing guidance for CSPs, partner-managed customers, and MACC](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-csp-partner-macc)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
