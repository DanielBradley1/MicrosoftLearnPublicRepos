<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/copilot-capacity-packs -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Use Copilot Studio capacity packs for Microsoft Copilot Chat and SharePoint agents

Tip

For the most complete and up-to-date Copilot Credit licensing and billing information, see the [Copilot Credit Guide](https://go.microsoft.com/fwlink/p/?linkid=2368800).

A Microsoft Copilot Studio capacity pack is a prepaid subscription that provides credits for Copilot Chat and SharePoint agent usage. Each capacity pack provides a fixed number of Copilot Credits that you can use across your tenant. Copilot Credits are the unit of consumption in Microsoft Copilot Chat and SharePoint agents for AI interactions. Credits are available in quantities of 25,000 per month per pack. The number of credits consumed by a Microsoft Copilot Chat agent or a SharePoint agent depends on the design of the agent, how often customers interact with it, and the features they use. For more information about the billing rates for credits, see [Billing rates and management - Microsoft Copilot Studio \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management#message-scenarios).

As an admin, you decide how you use capacity packs to pay for Copilot usage in your organization.

1. You can create a Copilot credit policy to use capacity pack credits by themselves, without requiring a pay-as-you-go billing policy or an Azure subscription.
2. You can pair a Copilot credit policy with a pay-as-you-go billing policy for automatic overage handling.
3. You can use a pay-as-you-go billing policy on its own.

This article explains how global administrators can use Copilot Studio capacity packs in the Microsoft 365 admin center for Microsoft Copilot Chat and SharePoint agents. This article also covers the end-to-end process of buying a capacity pack, setting up pay-as-you-go billing, allocating capacity in the Power Platform Admin Center, and monitoring usage.

Note

Copilot credit policies are currently only available for Microsoft Copilot Chat. For SharePoint agents, continue using pay-as-you-go billing as described in the existing setup process.

## Before you begin

- You must be a Global Administrator or Billing Administrator to buy capacity packs.
- You must be a Global Administrator to enable capacity pack usage.
- Billing administrators or AI administrators can set up pay-as-you-go billing but can't activate a capacity pack.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Understand the difference between capacity packs, pay-as-you-go billing policies, and Copilot credit policies

### Prepaid Capacity packs

A Prepaid Capacity pack lets you pay up front for a set number of Copilot Credits \(25,000 credits per month\). These credits are used first for any Copilot Chat usage in your organization.

### Pay-as-you-go billing policies

A pay-as-you-go billing policy lets you pay per credit for any usage. If you pair a Prepaid Capacity pack with pay-as-you-go billing, any usage beyond the Prepaid Capacity amount is automatically billed at the per-credit pay-as-you-go rate.

### Copilot credit policies

A Copilot credit policy connects your Prepaid Capacity pack credits to a specific set of users in your organization. Copilot credit policies give administrators detailed control over how Prepaid Capacity pack credits are distributed and consumed. If you use a Prepaid Capacity pack by itself \(without pairing it with a pay-as-you-go billing policy\), users covered by the credit policy consume credits only from the prepaid credit pool. When prepaid credits are exhausted, Copilot Chat is unavailable for those users until credits replenish at the next billing cycle.

Copilot credit policies have the following key characteristics:

- **Standalone capability**: Copilot credit policies work independently-they don't require an Azure subscription or pay-as-you-go billing to be set up first.
- **User group scoping**: You can create multiple Copilot credit policies scoped to different user groups, similar to how billing policies work. This scoping lets you allocate capacity to specific teams or departments.
- **Flexible pairing**: You can optionally pair a Copilot credit policy with a pay-as-you-go billing policy for automatic overage billing when prepaid credits run out. For details about overage handling, see [Understand overage handling and business continuity](#understand-overage-handling-and-business-continuity).
- **Tenant limit**: You can create up to 10 Copilot credit policies per tenant.

## Choose your configuration

There are three ways to set up billing for Copilot Chat with Prepaid Capacity packs. Choose the configuration that best fits your organization's needs.

| Configuration | Description | Azure subscription required? |
| --- | --- | --- |
| Copilot credit policy only | Uses Prepaid Capacity pack credits without pay-as-you-go billing. When credits are exhausted, Copilot Chat is unavailable until credits replenish. | No |
| Copilot credit policy + pay-as-you-go billing policy | Uses prepaid credits first. When credits run out, usage automatically switches to pay-as-you-go billing for uninterrupted service. For information about the benefits of using this configuration, see [Understand overage handling and business continuity](#understand-overage-handling-and-business-continuity). | Yes \(for pay-as-you-go overage\) |
| Pay-as-you-go billing policy only | Pay per credit for all usage with no Prepaid Capacity. All charges are billed to the connected Azure subscription. | Yes |

## Understand overage handling and business continuity

A major benefit of the integration between Prepaid Capacity packs and pay-as-you-go billing is seamless continuity when your Prepaid Capacity is exhausted. The service handles continuity in the following ways:

- **Automatic switch to pay-as-you-go billing:** When consumption exceeds the allocated prepaid credits in the Prepaid Capacity pack, Copilot Chat and SharePoint agents automatically switch to pay-as-you-go billing for extra credits. There's no service interruption and users can continue using Copilot Chat and SharePoint agents as usual.
- **Billing for overages:** Any credits used beyond your prepaid allotment incur pay-as-you-go billing charges to the connected Azure subscription. These charges appear on your next Azure invoice. For information about billing rates for Copilot Credits, see [Billing rates and management - Microsoft Copilot Studio \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management).
- **Replenishment:** Copilot Studio Prepaid Capacity packs are subscription products. At the start of every monthly billing period, your 25,000 credits are replenished. You must have pay-as-you-go billing active as a safety net each month to cover any excess usage. Alternatively, you can top up with more Prepaid Capacity pack credits.

## Step 1. Buy a Microsoft Copilot Studio capacity pack in the Microsoft 365 admin center

First, buy a Prepaid Capacity pack for your tenant. Each Prepaid Capacity pack is a tenant license that includes 25,000 Copilot Credits per month. If necessary, you can buy multiple packs.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to [Marketplace](https://go.microsoft.com/fwlink/p/?linkid=868433).
2. In the search box, type "Microsoft Copilot Studio."
3. Find the product, and then select **Details**.
4. On the product details page, in the **Select a plan** drop-down list, select **Microsoft Copilot Studio**.
5. Select a **Subscription length** and **Billing frequency**.
6. In the **Select license quantity** box, enter the number of Prepaid Capacity packs that you want to buy. Each pack represents 25,000 credits.
7. Select **Buy**.
8. In the **Checkout** panel, choose the billing profile that you want to use, or add a new one.
9. Review your order, and then select **Place order**.

After the purchase is complete, the Prepaid Capacity pack license appears in your tenant's subscriptions list. Because it's a tenant-wide resource, users don't need licenses individually assigned to them. However, you must [allocate the Prepaid Capacity pack to a Microsoft Copilot Chat environment](#step-3-allocate-capacity-to-the-copilot-chat-environment-in-the-power-platform-admin-center).

## Step 2. Set up your billing configuration

After you buy a Prepaid Capacity pack, choose one of the following options to configure how credits are used for Copilot Chat.

### Option A: Create a standalone Copilot credit billing policy

Use this option if you want to use Prepaid Capacity pack credits without setting up pay-as-you-go billing. No Azure subscription is required.

You can create multiple Copilot credit policies, each scoped to different user groups, including security groups, distribution groups, or the entire tenant. This scope lets you allocate Prepaid Capacity pack credits to specific teams or departments. You can create up to 10 Copilot credit policies per tenant.

Important

You must be a Global Administrator to complete the following steps.

1. In the Microsoft 365 admin center, go to **Copilot** > [Billing & usage](https://go.microsoft.com/fwlink/p/?linkid=2330674).
2. Select the **Pay-as-you-go services** tab, and then select **Microsoft Copilot Chat**.
3. In the **Copilot credit policies** section, select **Create a Copilot credit policy**.
4. Enter a policy name for the new Copilot credit policy.
5. Under **Scope**, select the user groups that this policy applies to. You can scope the policy to specific security groups, distribution groups, or the entire tenant.
6. Select **Save**.

After you save the policy, the system provisions a Microsoft Copilot Chat environment in the Power Platform admin center if one doesn't already exist. You must then allocate capacity to this environment as described in [Step 3. Allocate capacity to the Copilot Chat environment in the Power Platform admin center](#step-3-allocate-capacity-to-the-copilot-chat-environment-in-the-power-platform-admin-center).

Note

Provisioning happens automatically. If the environment creation process fails, you see an error message. If that happens, wait a few minutes and try saving again.

Important

If you have a standalone Copilot credit policy \(not paired with a pay-as-you-go billing policy\), when your prepaid credits are exhausted, Copilot Chat is unavailable for users covered by the policy until credits replenish at the start of the next monthly billing period. To ensure uninterrupted service, consider one of the following options:

- Buy more capacity packs to increase your prepaid credits.
- Add a pay-as-you-go billing policy for automated overage billing. To learn more, see [Option B: Create a Copilot credit policy paired with pay-as-you-go billing overage](#option-b-create-a-copilot-credit-policy-paired-with-pay-as-you-go-billing-overage).
- Monitor usage closely and set up capacity notifications in the Power Platform admin center. To learn more, see [Step 3. Allocate capacity to the Copilot Chat environment in the Power Platform admin center](#step-3-allocate-capacity-to-the-copilot-chat-environment-in-the-power-platform-admin-center).

### Option B: Create a Copilot credit policy paired with pay-as-you-go billing overage

Use this option if you want to use Prepaid Capacity pack credits first, paired with automatic pay-as-you-go billing when credits run out. This configuration provides business continuity.

#### Step B1: Create a Copilot credit policy

Follow the steps in [Option A: Create a standalone Copilot credit billing policy](#option-a-create-a-standalone-copilot-credit-billing-policy), and then follow the steps in [Step B2: Enable pay-as-you-go billing](#step-b2-enable-pay-as-you-go-billing).

#### Step B2: Enable pay-as-you-go billing

Next, set up a pay-as-you-go billing policy that provides overage billing when prepaid credits are exhausted.

1. If you haven't connected an Azure billing policy, you must do so now. Follow the steps for "Add a billing policy" in [Set up pay-as-you-go for Microsoft Copilot services for IT admins](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).
2. On the **Pay-as-you-go services** tab for Microsoft Copilot Chat, find the billing policy name to bill for any overage, then switch the **Connection status** toggle to **Connected**.
3. If you have multiple Azure subscriptions or billing policies, select the one that you want to use for your service.
4. Select **Save**.

### Option C: Use pay-as-you-go billing only

Use this option if you want to pay per credit for all Copilot Chat usage without Prepaid Capacity.

1. If you haven't connected an Azure billing policy, follow the steps "Add a billing policy" in [Set up pay-as-you-go for Microsoft Copilot services for IT admins](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).
2. In the Microsoft 365 admin center, go to **Copilot** > [Billing & usage](https://go.microsoft.com/fwlink/p/?linkid=2330674).
3. Select the **Pay-as-you-go services** tab, then select **Microsoft Copilot Chat** or **SharePoint agent**.
4. Find the billing policy name, then switch the **Connection status** toggle to **Connected**.
5. Select **Save**.

All Copilot Chat or SharePoint agent usage is billed at the per-credit pay-as-you-go rate to the connected Azure subscription.

## Step 3. Allocate capacity to the Copilot Chat environment in the Power Platform admin center

If you chose [Option A: Create a standalone Copilot credit billing policy](#option-a-create-a-standalone-copilot-credit-billing-policy) or [Option B: Create a Copilot credit policy paired with pay-as-you-go billing overage](#option-b-create-a-copilot-credit-policy-paired-with-pay-as-you-go-billing-overage), allocate your prepaid credits to the Copilot Chat environment in the Power Platform admin center. To learn more about capacity management for Copilot Studio, see [Manage Copilot Studio credits and capacity - Power Platform \| Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/admin/manage-copilot-studio-messages-capacity?tabs=new).

1. Go to the [Power Platform admin center](https://go.microsoft.com/fwlink/p/?linkid=2160305) and sign in with your admin account.
2. In the navigation menu, select **Licensing** > [Copilot Studio](https://go.microsoft.com/fwlink/p/?linkid=2330570).
3. On the **Summary** tab, under **Capacity summary**, find the **Prepaid Capacity** card. In the **License type** column, select **Manage capacity**.
4. The **Manage capacity** panel lists the environments eligible for Copilot Studio capacity. Select the **Microsoft Copilot Chat** environment. This environment is the one that you just created or that you already set up for Copilot Chat.
5. Under **Allocate capacity**, enter the number of credits from the Prepaid Capacity pack that you want to allocate to the selected environment. For example, if you bought one pack of 25,000 credits, you can allocate all 25,000 credits to Copilot Chat, or you can divide them between environments if you have multiple groups of users.
6. Under **Capacity overages**, select the options for what happens when capacity reaches zero. You can choose one or both of the following options:

   - **Draw from the available capacity in my tenant**.
   - **Bill to my pay-as-you-go billing plan**. If you select this option, from the drop-down list, select the billing plan that you want to use.

7. If you want to receive a notification when the capacity usage reaches a certain percentage, you can configure the notification setting. Under **Overage notification**, select the **Send notification when nearing capacity usage** checkbox, and then select a percentage value from the drop-down list.
8. Select **Save**, and then close the **Manage capacity** panel.

   Note

   If you have multiple capacity packs, make sure that the total allocated doesn't exceed the amount that you bought. You can adjust allocations at any time.

After you complete this step, your Copilot Chat environment has the specified number of credits allocated from your Prepaid Capacity. Any Copilot Chat agent credits consumed by users in this environment are drawn from the allocated prepaid pool first.

## Manage Copilot credit policies

After you create Copilot credit policies, you can manage them from the Microsoft 365 admin center.

### Edit a Copilot credit policy

You can change the name or scope of an existing Copilot credit policy.

1. In the Microsoft 365 admin center, go to **Copilot** > [Billing & usage](https://go.microsoft.com/fwlink/p/?linkid=2330674).
2. Select the **Pay-as-you-go services** tab, and then select **Microsoft Copilot Chat**.
3. Find the Copilot credit policy that you want to edit and select it.
4. Make your changes, and then select **Save**.

### Delete a Copilot credit policy

If you no longer need a Copilot credit policy, you can delete it. Deleting a credit policy disconnects the Prepaid Capacity pack from the users covered by that policy.

1. In the Microsoft 365 admin center, go to **Copilot** > [Billing & usage](https://go.microsoft.com/fwlink/p/?linkid=2330674).
2. Select the **Pay-as-you-go services** tab, and then select **Microsoft Copilot Chat**.
3. Find the Copilot credit policy that you want to delete, select the policy, and then select **Delete**.
4. Confirm the deletion.

## Monitor Copilot Chat usage and capacity in the Power Platform admin center

After you start using the Prepaid Capacity pack, monitor consumption to understand how much of your Prepaid Capacity pack credit is used and whether any pay-as-you-go charges are occurring. For more information, see [Manage Copilot Studio credits and capacity - Power Platform \| Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/admin/manage-copilot-studio-messages-capacity?tabs=new).

Note

You can only monitor Prepaid Capacity pack consumption in the Power Platform admin center.

In the Power Platform admin center, go to **Licensing** > [Copilot Studio](https://go.microsoft.com/fwlink/p/?linkid=2330570). On the **Summary** tab, the **Capacity summary** section reflects Prepaid Capacity pack usage, shows how many credits were consumed in total, and shows how many remain available for the current period.

You can also see the credit allocation per environment. If you want to adjust the allocation \(for example, to move some credit units to a different environment or if you buy more capacity packs\), use the **Manage capacity** panel to update the numbers. To open the panel again, go to the **Prepaid capacity** card and select **Manage capacity**.

Use the Power Platform admin center not just to manage credit allocation, but also to check if your Copilot Chat environment's allocated capacity is being used up as users spend credits.

## FAQ

### Do I need to create a Microsoft Copilot Chat environment myself?

No. The Microsoft 365 admin center creates the Microsoft Copilot Chat environment for you when you enable the Prepaid Capacity pack option and save the setup. If you already have an environment from a previous setup in the Power Platform admin center, it's reused. Make sure that you allocate capacity to it as described in [Step 3. Allocate capacity to the Copilot Chat environment in the Power Platform admin center](#step-3-allocate-capacity-to-the-copilot-chat-environment-in-the-power-platform-admin-center).

### What if I already have pay-as-you-go billing set up with a Prepaid Capacity pack?

Your existing configuration continues to work. You can optionally create a Copilot credit policy to take advantage of user group scoping and the policy management features. Your existing Prepaid Capacity pack allocation in the Power Platform admin center remains unchanged.

### How do multiple Copilot credit policies interact with each other?

Each Copilot credit policy is scoped to specific user groups. When a user interacts with Copilot Chat, the system uses credits from the policy that covers that user. If a user is covered by multiple policies, the system uses the most specific policy.

## Related content

[Manage Copilot Studio credits and capacity - Power Platform \| Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/admin/manage-copilot-studio-messages-capacity?tabs=new) \(article\)  
[Billing rates and management - Microsoft Copilot Studio \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management) \(article\)  
[Copilot Studio licensing - Microsoft Copilot Studio \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing?source=recommendations) \(article\)
