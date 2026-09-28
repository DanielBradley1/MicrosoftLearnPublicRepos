<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Managing AI experiences enabled by usage-based billing

Microsoft uses a usage-based billing model that uses Copilot Credits to provide flexible payment options alongside fixed licensing. This model enables organizations to manage and optimize AI service expenses effectively through centralized tools like the Cost management dashboard in the Microsoft 365 admin center.

The Cost Management dashboard in the Microsoft 365 admin center helps organizations control, monitor, and optimize Copilot Credit spending for AI experiences enabled by usage-based billing.

Administrators can:

- Create spending policies that control access to supported agents and services.
- Automatically apply existing spending policies to future supported services and agents.
- Configure organizational and user-level spending limits.
- Configure threshold notifications for administrators and users.
- Use Capacity packs, pay-as-you-go billing, Copilot Credit Pre-purchase plans \(P3\), or supported combinations of these billing methods.
- Configure custom approval routing for credit requests.
- Monitor consumption by spending policy, group, user, agent, service, and funding source.

These controls help organizations understand cost drivers, apply spending safeguards, and manage Copilot Credit consumption at scale.

Important

For a list of services managed by usage-based billing method, see [Services managed by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits#services-managed-by-usage-based-billing). Microsoft is working to bring more agents and services to be managed by this experience.

To learn more about discovery settings for AI experiences enabled by usage-based billing, see [Discovery setting for AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).

When a spending policy has **Auto-apply new services** turned on, newly supported Microsoft Copilot services and agents are automatically added to the policy as they become available. See [Select agents and services](#select-agents-and-services).

Note

If you are looking for information on other usage-based billing products, use the following articles:

- For Copilot Chat, SharePoint Agents, or Microsoft Copilot Retrieval API \(Preview\), see [Microsoft Copilot pay-as-you-go service overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).
- For Copilot Studio, see [Copilot Studio pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing#copilot-studio-pay-as-you-go).
- For non-Copilot services; Microsoft 365 Backup, Microsoft 365 SharePoint Storage, and High Volume Email, see [Set up and manage pay-as-you-go billing in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node).

## Role requirements

Global administrator and Billing administrator roles can add, select, and change billing methods, and set billing methods in policies.

AI administrator and License administrator roles can edit spending policies, manage limits and alerts, and billing methods. However, they can't create spending policies.

AI Reader, Global Reader, License Administrator, and other supported reader-based roles can view consumption dashboards and reports. These roles provide read-only access to consumption information and don't allow administrators to create or change spending policies, limits, alerts, request policies, or billing methods.

Note

Review existing role assignments. Assign a supported reader-based role to users who need to review consumption and spending information but don't need configuration permissions.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global administrator is a highly privileged role that you should limit to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

> To learn more about these roles, see [Microsoft 365 admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Get started with usage-based billing

This section covers the initial setup to guide administrators through enabling usage-based billing and creating the first spending policy. This process activates the AI experiences, like Cowork, that are gated by usage-based billing.

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) with one of the following administrator roles:

   - Global administrator
   - Billing administrator

2. In the Microsoft 365 admin center, go to **Copilot** and then the **Cost Management** node.

   [![Screenshot of the Cost management dashboard in Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-cost-management-dashboard.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-cost-management-dashboard.png#lightbox)
3. To unlock AI experiences enabled by usage-based billing, select **Get Started**. This feature is currently available for Cowork and Work IQ API.
4. A side-panel with the title **Activate the default spending policy for your organization** opens.
5. In the **Billing method** section, select how your organization is billed for Copilot credit usage. Select the default subscription for your organization. This subscription is selected by default for other policies that you create. For more detailed information on how the billing method is populated, see [Configure billing method](#configure-billing-method).
6. In the **Set the monthly spending limit** for this policy section, select one of the options.

   - **Don't limit monthly spending** - Allows the policy to use credits against the organization's billing method without restrictions.
   - **Limit monthly spending** - Limits the number of credits the default policy can spend each month.

7. In the **Select the monthly spending limit for users \(optional\)** section, set a monthly limit for users to prevent a single person from spending all available credits. Although this selection is optional, review and set this option for your organization to prevent runaway spending of Copilot Credits by one individual user.
8. In the **Define alerts** section, select the people who receive email notifications when policy usage reaches the threshold that you specify. You can set the threshold as a credit amount or a percentage. Alert emails begin when usage reaches the specified threshold and continue weekly until the monthly usage period resets or you adjust the spending policy. If you set a monthly credit limit per user, you can also configure a user monthly spend alert. This option appears only when a monthly per-user limit is configured.

   Note

   The field prepopulates the logged in administrator email and suggests the administrators that you selected in billing notifications for alerting.
9. If a monthly per-user limit is configured, set the user-level notification thresholds. These notifications alert users as they approach their spending limit and can help them manage consumption before access is affected.
10. Review the **Auto-apply new services** setting. This setting is turned on by default.

    - Leave the setting turned on to automatically add future supported Microsoft Copilot services and agents to the policy.
    - Turn off the setting if you want to review and add future services manually.

11. The default setup targets your entire organization and all users. Optionally, you can customize the default spending policy to specific groups or change the services it governs by selecting **Customize setup configuration** before selecting **Activate**.
12. Select **Activate**. You're notified that the set up is complete.
13. Select **Manage Configuration**. The **Configuration** tab within the Cost management page is displayed. Copilot consumptive services are now available. You can now add more spending policies to scope access to specific groups, users, or services.

Note

When you activate the default spending policy, you set the tenant-level limit for **all users**. Each additional spending policy that you create has its own independent limit and doesn't inherit the tenant-level limit.

## Add spending policies

1. In the Microsoft 365 admin center, go to **Copilot > Cost Management**.
2. Select the **Configuration** tab and then select **+ Add spending policy**. You can create any number of spending policies.
3. After you select **+ Add spending policy**, follow the prompts to add details to the spending policy. The following sections describe the steps that you need to complete as you go through the add spending policy workflow.

### Policy scope

The system supports user, group, and tenant policies.

Give the policy a name and select the specific groups that the policy applies to.

1. Create and name the policy.
2. Select the users or groups to which the policy applies. By default, **All users** is selected. To target this rule to a subset of users, switch to **Specific groups** and select the directory group. You can also select multiple groups.
3. At this time, you can only support specific users through security groups. To add specific users to a spending policy, ensure they're in a security group first and then select specific groups from the policy setup.
4. Select **Next**.

**Users in multiple policies**

Users can belong in multiple spending policies. If a user is in more than one policy for the same service, the system assigns the user a policy based on the following order:

1. Highest per-user limit
2. If tied, the largest overall policy limit
3. If still tied, the most recently created policy

If a policy doesn't have a per-user limit set, the system uses its overall policy limit as the per-user value for this comparison. The chosen policy applies in full and settings from other policies aren't combined.

When users reach their limit within a policy, they can request more credits but they don't default to other policies. The system keeps the user on the assigned policy and doesn't reevaluate the user against other policies.

**Spending policy behavior when a user moves between Entra ID Groups**

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

### Select agents and services

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

### Select billing method

By default, the field selects the billing method tied to the default spending policy.

If you're a Global administrator or a Billing administrator, you can override this selection and select how this policy should be billed. This feature enables you to do departmental billing and vary billing methods for each group, department, or set of users.

**For Global or Billing administrators**

1. Select **Change** to override.
2. If your tenant has capacity packs, you can choose to use them.
3. Alternatively, you can choose a different Azure subscription to bill against. For more information, see [Configure billing methods](#configure-billing-method).

### Review and add policy

1. Before you create the spending policy, verify:

   - Its user and group scope.
   - Its policy-level and per-user limits.
   - Its policy and user notification thresholds.
   - Its selected services and agents.
   - The Auto-apply new services setting.
   - Its billing method.

2. Select **Create spending policy** to complete the setup.
3. You're notified that the spending policy is created. Select **Done**. The spending policy now shows up in the Configuration list and starts applying to scoped users immediately.

## Edit spending policy

To edit a spending policy, follow these steps:

1. In the **Configuration** tab, select the spending policy you want to edit.
2. The spending policy details fly-out opens, where you can modify its settings, such as scoped users and groups, spending limits, alerts, enabled services, and billing method.
3. After making the necessary changes, select **Save** to apply the updates to the spending policy.

## Delete spending policy

When you delete a spending policy, the users and groups assigned to that policy are no longer governed by its spending limits.

Deleting a spending policy doesn't remove, reallocate, or reset Copilot Credits. Spending policies only define access and spending limits, not credit allocation. Any usage that occurred before the policy was deleted remains available in usage and reporting views.

If another spending policy applies to a user through group membership, the user continues to consume Copilot Credits under the applicable policy. Previously consumed credits remain part of the user's consumption history for the current billing period.

Note

Spending policies are limit-based controls and don't reserve or allocate Copilot Credits to users or groups.

## Configure billing method

You have several choices when configuring billing methods in spending policies. Copilot credits are billed to the subscription that you select in the billing method. New policies use it by default. When credits run out for that subscription, usage automatically continues on a pay-as-you-go basis.

Important

- A default billing method is preconfigured, but you can change it at any time.
- Copilot Credit Pre‑Purchase Plan \(P3\) and pay‑as‑you-go aren't separate billing options. P3 is layered on top of pay‑as‑you-go.
- Customers can use Agent P3 and Copilot P3 credits for AI experiences, such as Cowork. Currently, the Microsoft 365 admin center displays only the credits available from Copilot Credit P3. However, if the subscription selected for the **billing method** includes Agent P3, the system uses the Agent P3 credits first and bills any overage charges only after those credits are exhausted.
- You can update the billing method for an existing spending policy. Open the spending policy that you want to modify and update its billing method. Changing the billing method doesn't require you to delete and recreate the policy. Existing spending policy settings, such as scoped users and groups, spending limits, alerts, and enabled services, are retained when you update the billing method.

### Create a new Azure subscription

If you don't have an existing Azure subscription or prefer not to use one, create a new subscription directly from the Microsoft 365 admin center.

If you don't have access to any Azure subscriptions, the system automatically creates a subscription for you by using the billing account linked in the Microsoft 365 admin center.

You must be a Global administrator to create a new subscription this way.

Alternatively, you can manually create a subscription by selecting **Create new** from the subscription dropdown.

### Use an existing Azure subscription

If you already have Azure subscriptions, the system shows the subscriptions linked to the billing account that you can access. These subscriptions appear in the **Subscription** dropdown by name, and you can hover to view the subscription ID.

To learn more about your subscriptions or decide which one to use for usage-based billing, review and manage them in the Azure portal: [View Azure subscriptions](https://portal.azure.com/#view/Microsoft_Azure_Billing/SubscriptionsBlade).

Some subscriptions show an **X prepaid credits available** label. This label indicates that a Copilot Credit Pre-purchase plan \(P3\) is attached. The process uses available prepaid credits first, and once they're exhausted, usage automatically continues on a pay-as-you-go basis.

[![Drop-down list showing a subscription with P3 credits.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/select-subscription-copilot-credits.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/select-subscription-copilot-credits.png#lightbox)

If available, the system selects a subscription with Copilot Credit Pre-purchase plan \(P3\) by default. Learn more about [prepaid discounts](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/copilot-credit-p3).

### Buy Pre-purchase Credits \(Pre-purchase plan: P3\)

You can purchase a **Copilot Credit Pre‑Purchase Plan \(P3\)** from the Microsoft 365 admin center by selecting **Buy Pre-purchase Credits** on the **Cost Management > Configuration** page. You can also complete this step through the Azure portal.

Note

Pre‑purchasing annual credits provides discounted rates compared to pay‑as‑you‑go pricing. Larger commitments unlock greater discounts, and any usage beyond your prepaid credits automatically continues on a pay‑as‑you-go basis. For more information, see [prepaid discounts](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/copilot-credit-p3) in Optimize Copilot Credit costs with a pre‑purchase plan.

#### Steps to purchase prepaid credits

1. Go to **Cost Management > Configuration**.
2. Select **Buy Pre-purchase Credits**.
3. In the side panel, choose the Azure subscription you want to use.
4. Select the credit amount based on your expected usage.
5. Review your current available credits before adding more capacity.
6. View the **Copilot Credit Pre‑Purchase Plan \(P3\)** details and total cost.
7. Select **Go to checkout**.
8. Review the purchase details, including **Important information** and **Additional notes**.
9. Select **Purchase** to complete the transaction.

After you purchase, a notification appears on the **Configuration** tab once processing is complete. The prepaid credits are available to select when you're selecting the subscription in the billing method when configuring spending policies.

### Use existing Prepaid Capacity packs

If you purchased capacity packs, you can use them with the services in this experience.

- During initial setup, if the system detects Prepaid Capacity packs, it sets them as the default billing method. Enable a pay-as-you-go meter to ensure your services continue once Prepaid Capacity pack credits are exhausted.
- In the **Billing Method** page, when setting up a spending policy, the number of credits available from Prepaid Capacity packs reflects the credits that are available for use, instead of the total number of credits purchased. \(where Available credits = Total purchased credits - Credits pre-allocated to environments in Power Platform admin center\)
- You can choose to apply Prepaid Capacity packs at the individual spending policy level in the **Review billing method** step.
- You must be a Global administrator or Billing administrator to override or set the billing method.
- Copilot Credits from Prepaid Capacity packs can be consumed by multiple services managed by both Microsoft 365 admin center and Power Platform admin center. However, capacity that is assigned or used in Power Platform admin center \(for example, allocated to specific environments or consumed by agents\) reduces the Copilot credits available for Cowork and Work IQ API services managed by Microsoft 365 admin center. Therefore, it's important to leverage the **Copilot > Cost management** dashboard in Microsoft 365 admin center to properly identify what is available for Cowork and Work IQ API consumption.

  - Check the Power Platform admin center for additional credit allocation and usage details: [Power Platform admin center](https://admin.powerplatform.microsoft.com/licenses).
  - For more information on how to manage capacity allocation or reallocation, see [Manage Copilot Studio credits and capacity](https://learn.microsoft.com/en-us/power-platform/admin/manage-copilot-studio-messages-capacity#manage-capacity).

Note

If you select both Prepaid Capacity packs and an Azure subscription with Copilot Credit Pre-purchase plan \(P3\), billing is applied in the following order to keep spending predictable:

- Prepaid Capacity packs
- Copilot Credit Pre-purchase plan \(P3\)
- Pay-as-you-go billing

For more information on other purchasing methods such as capacity packs, see [Microsoft Copilot Studio Licensing Guide](https://go.microsoft.com/fwlink/?linkid=2320995).

### Pay-as-you-go

If you choose to override by using the pay-as-you-go option, the connected Azure subscription is billed on a pay-as-you-go basis. If Prepaid Capacity pack credits are available, the system uses those credits first, and then pay-as-you-go.

If you select Pay-as-you-go and you're an Owner or Contributor on the selected Azure subscription, you can configure **Advanced billing settings**.

Select **Advanced billing settings** to specify:

- The **billing region** where the billing policy is deployed.
- The **resource group** where the billing policy is deployed.

If the selected subscription already contains one or more resource groups, select the resource group to use. If the subscription doesn't contain a resource group, the **Resource group** list doesn't appear, and a resource group is automatically created when you create the billing policy.

## Guidance for CSPs, partner-managed, and MACC customers

### For CSPs or partner-managed customers

Important

If you're a Cloud Solution Provider \(CSP\) or a partner-managed customer, see the [Partner-facing FAQs](https://aka.ms/CSPM365CopilotPartnerFAQ) for setup instructions and details.

Setup instructions are available in the FAQ under the question: **What steps are required to configure Cowork usage and billing for my customer?**

**Step 1**: Ensure an Azure subscription is set up and linked to your partner billing account.

If the customer already has an Azure subscription: → Ensure it's associated with your partner billing account.

If the customer doesn't have an Azure subscription: → Create a new subscription by using the Azure portal or Partner Center.

**Step 2**: Configure usage-based billing in Microsoft 365 admin center.

Connect the Azure subscription associated with your partner billing account [more details](https://learn.microsoft.com/en-us/partner-center/customers/purchase-azure-plan).

Configure user access controls \(who can use the services\), spending limits, and alerts [more details](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits#add-spending-policies).

Ensure the setting that allows users to discover and use usage-based services is turned on [more details](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).

### Understanding Azure Consumption Commitment \(MACC\) in Microsoft Copilot

If your organization has an Azure Consumption Commitment \(MACC\), you can apply those committed funds toward eligible Copilot consumption. This approach helps you maximize existing investments while adopting AI-powered capabilities.

To ensure correct application of MACC, administrators must configure billing in the Microsoft 365 admin center by using an Azure subscription associated with the correct billing account. MACC benefits apply only when the selected subscription links to a billing account that includes the commitment. If you use a different billing account or subscription, you still pay for consumption, but it might not count toward your MACC. Therefore, proper setup is critical.

Administrators should:

- Verify access to the billing account that contains the MACC commitment.
- Select an Azure subscription associated with that billing account during setup.
- Ensure the correct billing relationship is established before enabling consumption-based services.

When you configure it correctly, eligible Copilot usage automatically applies against your MACC. You don't need to take any extra action during ongoing usage.

This model allows organizations to seamlessly extend their Azure investment into Microsoft Copilot scenarios while maintaining control over billing, governance, and cost visibility.

## Monitoring spending of Copilot Credits

### Overview tab

This dashboard provides a centralized view of spending patterns, helping administrators identify where credits are used, who consumes them, and how usage trends evolve over time.

The **Overview** tab refreshes every 4 hours.

As an administrator, use the Overview tab to:

- Review total Copilot Credit consumption.
- Compare usage-based billing including Copilot Credit Pre-purchase plans \(P3\) where applicable, with pay-as-you-go consumption. \(Side-by-side visibility\)
- Review consolidated spending insights across supported Copilot experiences.
- Understand Prepaid Capacity pack attribution across the Microsoft 365 admin center and Power Platform admin center.
- Identify changes in consumption patterns.
- Review policies or users that are approaching their spending limits.
- Access common actions for managing credit requests and spending policies.

The pay-as-you-go, and Prepaid Capacity pack breakdowns help organizations reconcile spending, understand funding sources, and evaluate usage across purchasing models.

Note

Use the Power Platform admin center for additional capacity allocation and workload-level details provided by that admin experience.

Note

Users can view their approximate Copilot Credit usage directly in Microsoft Copilot Cowork by entering `/cost`. This command shows the approximate cost in credits for the opened task so far, and additional credit usage details. For more information, see [Check your credit usage for Cowork tasks with `/cost`](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-cost).

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Copilot** > **Cost Management**.
2. Select the **Overview** tab.
3. Review these sections:

   - **Total Copilot Credits used**. Review total consumption for the selected period.
   - **Prepaid Capacity pack credits usage** \(if applicable\). Select the card to view details of Prepaid Capacity pack consumption by service. The flyout shows credits consumed by Microsoft 365 services and Power Platform services, along with the assigned capacity value when available.
   - **Pay-as-you-go credit used** \(includes Copilot Credit Pre-purchase plan \(P3\) credits\). Select the card to view the month-to-date details and spending trend.
   - **Number of Active users of Copilot Credits**. Users who have consumed Copilot Credits during the reporting period.
   - **Prepaid Capacity pack attribution**: Review available breakdowns for usage associated with the Microsoft 365 admin center and Power Platform admin center.


   Note


   Prepaid Capacity pack consumption can include usage managed in both the Microsoft 365 admin center and Power Platform admin center. Use the Power Platform admin center for additional allocation and usage details for Power Platform services.

4. From the **Top Actions** section, you can **View requests** and **Manage spending policies** by being alerted of spending policies credit usage near limit or users credit usage near limit.

#### Viewing and managing credit requests

To view and approve credit requests from end users, select **View requests**. The **Credit requests** page displays all pending and approved requests. End users in your organization can submit credit requests for first-time use or limit increases.

The **Credit requests** page helps administrators review and manage requests from end users who need access to to a supported Copilot service or need a higher spending limit. Each request can include information such as the requested service, license status, current policy, and whether the user is currently covered by a spending policy.

#### Configure custom request policies

Organizations can create custom request policies for credit requests. Custom request policies let administrators define alternate approvers or redirect requests to the appropriate business owner or approval workflow. For example, you can route requests to an internal IT portal or a ServiceNow workflow instead of requiring the request to be approved in the Microsoft 365 admin center.

To configure a custom request policy:

1. On the **Credit requests** page, select **Request policies**.
2. Select **Add request policy**.
3. Choose whether the policy applies to all products and services or to a supported specific product or service. A service-specific request policy takes precedence over a policy for all products and services.

   - **All products and services**: The policy applies to all credit requests.
   - **Specific product or service**: The policy applies only to requests for the selected product or service.

4. Enter the **redirect URL** and the **message** that end users see when they attempt to submit a request.
5. Optionally, add a Learn more link and identify the external service used to handle requests.
6. **Save** the request policy.

Requests submitted when a custom request policy applies still appear in the **All requests** view for audit and history. These requests are labeled **Handled externally**. Requests that don't match a custom request policy continue through the Microsoft credit request service and can be resolved in the Microsoft 365 admin center.

For a request labeled **Handled externally**, an administrator can still approve, reject, or mark the request as already processed. The label indicates that the request was routed to the organization's external workflow; it doesn't provide the approval result from that external system.

Each request shows key details like the requested app, license status, and current policy, making it easy to identify users who are blocked \(for example, 'Not in a policy'\) or need higher limits.

Administrators can act on requests by:

- Adding users to a spending policy to grant access and apply limits.
- Creating new policies or groups to onboard teams at scale.
- Adjusting policy limits to accommodate increased demand.
- Exporting requests for triaging offline.

#### Manage spending policies

1. If users, groups, or policies are nearing their spending limits, they appear in the **Top actions** section. Select **Manage spending policies** to update the limits or create a new policy for the affected users or groups.
2. Review consumption trends to see which groups, agents, services, and users consume the most or least credits over time. Use these trends to decide whether to update spending limits, adjust policies, or redistribute credits.

#### Monitor usage across groups, users, and services

The dashboard surfaces key insights to help you quickly understand consumption.

1. Select the **Consumption** tab.

- **Group-level spending** View which groups use the most and least Copilot credits in the current period. This view helps you identify teams that drive usage and those that might need enablement or controls.
- **User-level spending** See which individual users consume the most credits, so you can detect high usage patterns or outliers. Group and user level spending might differ because users can belong to multiple groups and policies.
- **Agents and services consumption** Track which Copilot experiences, such as Copilot agents or APIs, drive the highest credit usage across your tenant.

Each of these views includes quick actions, such as **Manage group spending** or **Manage user spending**, so you can take action directly from the insights.

#### Understand consumption trends

The **spending trend chart** provides a visual breakdown of Copilot credit usage over time, including:

- **Prepaid credits consumption** \(including consumption from Message/Capacity Packs\)
- **Pay-as-you-go usage** \(including credits from a Pre-Purchase Plan\)
- **Total cumulative consumption**

This chart helps you:

- Track how quickly credits are consumed
- Monitor shifts between prepaid and pay-as-you-go usage
- Identify spikes or steady growth in demand across days or weeks

#### Consumption tab

The **Consumption** tab provides reporting experiences for copilot credit usage by:

- Spending policy
- User
- Group
- Agent
- Service

The **Consumption** tab reports users who consume credits, not all users assigned to a policy. As a result, the number of active users might differ from the number of enabled users.

The **Consumption** tab refreshes every 2 hours.

Note

Exported reports are generated as a point-in-time snapshot, while dashboard views continue to retrieve live data. For this reason, exported counts and dashboard counts might temporarily differ. The export process supports larger result sets through an asynchronous export job.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Copilot** > **Cost Management**.
2. Select the **Consumption** tab.
3. The Policies view is the default view when you open the **Consumption** tab. It aggregates consumption information by spending policy for the selected reporting period.

   Use the view to review the following information:

   - **Policy**: The spending policy name.
   - **Policy status**: Whether the spending policy is active or inactive.
   - **Scope**: The users and groups included in the policy.
   - **Active users**: The number of users in the policy who generated usage during the selected reporting period. This value doesn't include every user who is eligible to use the policy.
   - **Credit usage**: The number of Copilot Credits consumed against the policy during the selected reporting period.
   - **Current spending limit**: The policy's current configured spending limit. This value doesn't change when you select a historical reporting period.
   - **Limit utilization**: Credit usage divided by the current spending limit.
   - **Billing method**: The billing method configured for the policy.


   When you review a historical reporting period, limit utilization compares usage from that period with the policy's current spending limit. Consider this difference when you interpret historical utilization.


   Using the dedicated policy-level view, administrators can:


   - Analyze consumption by individual spending policy.
   - Understand how credits are distributed across governed groups.
   - Identify which policies drive the highest usage.
   - Improve policy optimization and governance decisions.

4. In the **Users** view, select a user. The details panel shows total credits used, daily credit usage, spending policy history, and credits spent by spending policy for the past month. Credits spent by spending policy can include the policy name, associated agents and services, applicable limit, and credits used.

   - Users in a group spending policy that exceed their per-user spending limit: If a running task exceeds the per-user limit, it can complete without interruption. The excess usage doesn't count toward the policy limit, isn't billed \(at Microsoft's sole discretion\), and doesn't appear as consumed credits in the Cost Management dashboards \(**Microsoft 365 admin center > Copilot > Cost Management**\).
   - When a user moves from one Entra ID group to another during a billing period, the new group's spending policy becomes effective for that user. Credits consumed before the move are retained for billing at a policy level but aren't tracked at a user level in the Consumption tab view. Only the current usage against the current spending policy is displayed at a user level in the Consumption tab view.

5. In the **Groups** view, review groups included in spending policies. Select a group to open the details panel and view daily usage, assigned policy, and monthly credit limit.
6. In the **Agents and services** view, review usage for supported services, including Cowork and Work IQ API. This view shows active users, credits used, and session count for each supported service.
7. Compare usage across users, groups, agents, and services to help adjust policies or redistribute credit budgets.

## Related articles

- [Usage-based billing overview for Copilot credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Cowork Usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/cowork-usage-report)
- [View Copilot Credit consumption in the Microsoft 365 admin center and on your Azure bill](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-compare-dashboard-views)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
