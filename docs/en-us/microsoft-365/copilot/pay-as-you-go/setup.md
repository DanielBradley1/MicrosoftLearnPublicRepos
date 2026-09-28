<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Set up Microsoft Copilot pay-as-you-go services

The Microsoft Copilot pay-as-you-go service offers a usage-based option for organizations to access Copilot services, like Microsoft Copilot Chat. Use this article to configure pay-as-you-go services directly in the Microsoft 365 admin center. To learn more about the pay-as-you-go service, see [Microsoft Copilot pay-as-you-go overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).

This article applies to:

- Microsoft Copilot Chat
- SharePoint agents

Note

Looking for information on Copilot Cowork or Work IQ API billing? These services are managed through the Microsoft admin center. See [Usage-based Billing and Cost Management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

## Watch: Set up pay-as-you-go billing

Check out this and other videos on our [YouTube channel](https://go.microsoft.com/fwlink/?linkid=2198103).

<iframe src="https://learn-video.azurefd.net/vod/player?id=392bd4b7-524a-4314-ba02-5d8ef705ab89" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Before you begin

- You must have one of the following roles to complete the tasks in this article:

  - [Billing Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?#billing-administrator)
  - [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?#ai-administrator)
  - [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)


  Caution


  Global Administrators have almost unlimited access to your organization's settings and most of its data. To help keep your organization secure, we recommend that you limit the number of Global Administrators as much as possible.


  To learn more about these roles, see [Microsoft 365 admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

- You must have an [Azure subscription](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/initial-subscriptions) in the same tenant as Microsoft 365. If you don't have an Azure subscription, you can create one during the billing policy setup process.
- You must have an Azure resource group in that subscription. If you don't have an Azure resource group, you can create one during the billing policy setup process.
- You must have Owner or Contributor rights to the Azure subscription and resource group. If you create the subscription and resource group during the billing policy setup process, you're automatically given the Owner role to both.

  To learn more, see [Use the Azure portal and Azure Resource Manager to Manage Resource Groups](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal).

## Set up a billing policy

To set up pay-as-you-go billing for Microsoft Copilot, first add a billing policy in the Microsoft 365 admin center. You can create up to 50 billing policies for your tenant.

Complete these setup tasks in order:

- [Create a billing policy and add billing details](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot#step-1-create-a-billing-policy-and-add-billing-details)
- [Add users or groups to the billing policy](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot#step-2-add-users-or-groups-to-the-billing-policy)
- [Set a budget for the billing policy \(optional\)](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot#step-3-set-a-budget-for-the-billing-policy-optional)

When you reach the **Review and finish** page, review the details, and then select **Create policy**.

Next, continue to [Connect a billing policy to the Copilot pay-as-you-go service](#connect-a-billing-policy-to-the-copilot-pay-as-you-go-service).

Important

When you set a budget amount, it triggers email notifications based on your organization's spending relative to that limit. However, the system doesn't enforce the budget or prevent your organization from exceeding it. Usage can continue uninterrupted even after the budget is surpassed, ensuring no disruption to the service.

## Connect a billing policy to the Copilot pay-as-you-go service

After you create a billing policy, connect the policy to the Copilot pay-as-you-go service.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Copilot** > **Billing & usage**.
2. On the **Billing & usage** page, select the **Pay-as-you-go services** tab.
3. Select **Microsoft Copilot Chat** or **SharePoint agents** and select the billing policy you created.

To learn how to set up a billing policy for SharePoint agents, see [Use agents with pay-as-you-go billing](https://learn.microsoft.com/en-us/sharepoint/sharepoint-agents-azure-billing).

## Add a budget to an existing billing policy

If you have an existing billing policy that doesn't have a budget assigned to it, you can add one in the Microsoft 365 admin center. To add a budget to an existing billing policy, follow the steps in [Create a budget for pay-as-you-go billing in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-budget).

Important

When you set a budget amount, it triggers email notifications based on your organization's spending relative to that limit. However, the system doesn't enforce the budget or prevent your organization from exceeding it. Usage can continue uninterrupted even after the budget is surpassed, ensuring no disruption to the service.

## View spending for your organization

If you previously set up a budget for your organization, use the steps in [View spending for your organization](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot#view-spending-for-your-organization) to view the spending report in the Microsoft 365 admin center.

## Related management tasks

For tasks after initial setup, use the following articles:

- [Disconnect a pay-as-you-go service](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot#disconnect-a-pay-as-you-go-service)

  Note

  When you turn off pay-as-you-go, it can take up to two hours for users to stop being able to use the agents. If the agent is unused, it stops being available when pay-as-you-go is turned off.
- [Delete a billing policy](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-copilot#delete-a-billing-policy)
- [Create Azure subscriptions and resource groups during billing policy setup](#create-azure-subscriptions-and-resource-groups)

### Create Azure subscriptions and resource groups

As an admin, you can create Azure subscriptions and resource groups from within the billing policy creation process in the Microsoft 365 admin center, without the need to visit the Azure portal.

To create an Azure subscription, you must have one of the following roles:

- The owner, contributor, or Azure subscription creator role for an invoice section.
- The owner or contributor role on a billing profile or a billing account.

Note

The billing account must be connected to a Microsoft Customer Agreement \(MCA\).

To create an Azure subscription and resource group at the same time, use the following steps:

1. In the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to the **Copilot** > **Billing & usage** page.
2. On the **Billing policies** tab, select **Add a billing policy**.
3. Select **Create a new subscription**.
4. In the **Create a new subscription** panel, enter a subscription name and resource group name, and then select a **Region**.
5. If you have access to more than one invoice section, choose one from the **Invoice section** drop-down list. The subscription is created under the selected invoice section.
6. Select **Save**.

To only create a resource group, use the following steps:

1. In the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to the **Copilot** > **Billing & usage** page.
2. On the **Billing policies** tab, select **Add a billing policy**.
3. Select a subscription from the drop-down list, and then select **Create a new resource group**.
4. In the **Create a new resource group** panel, enter a resource group name, and select a **Region**.
5. Select **Save**.

## FAQ

### What if pay-as-you-go is already set up in the Power Platform admin center?

If you set up a pay-as-you-go billing policy in the Power Platform admin center, you can still create a new policy in the Microsoft 365 admin center. Both policies can exist at the same time, and the billing system ensures that your organization is only charged once, regardless of where you configure the policy.

While coexistence is supported, turning off the pay-as-you-go policy in the Power Platform admin center before enabling it in the Microsoft 365 admin center can help streamline management. Managing all pay-as-you-go policies from a single location simplifies administration and reduces potential confusion.

### How can I test that pay-as-you-go is correctly configured and working properly?

Have an eligible user test one of these agents: "Learning Coach," "Writing Coach," or "Career Coach." Ask them to submit a basic prompt such as "What can you do?" This prompt consumes about 12 credits. Then confirm usage in the [Copilot Credits Report](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/view-cost).

## Related articles

- [Microsoft Copilot pay-as-you-go service overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview) \(article\)
- [Meters for Microsoft Copilot pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/meters) \(article\)
- [View costs and billing for Microsoft Copilot pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/view-cost) \(article\)
