<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Set up and manage pay-as-you-go billing in the Billing node of the Microsoft 365 admin center

This article explains how to set up and manage pay-as-you-go billing in the **Billing** node of the Microsoft 365 admin center for the following services:

- Microsoft 365 Backup
- Microsoft 365 OneDrive Storage
- Microsoft 365 SharePoint Storage
- High Volume Email

Note

Looking for information on Copilot Cowork or Work IQ API billing? These services are managed through the Microsoft admin center. See [Usage-based Billing and Cost Management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

Note

Government Community Cloud \(GCC\) and new Microsoft 365 Backup customers only: Existing backup customers must use the **Setup** node to set up pay-as-you-go billing. For more information, see [Set up or disconnect pay-as-you-go billing in the Setup node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup?view=o365-worldwide).

## Watch: Set up pay-as-you-go billing

Check out this and other videos on our [YouTube channel](https://go.microsoft.com/fwlink/?linkid=2198103).

<iframe src="https://learn-video.azurefd.net/vod/player?id=392bd4b7-524a-4314-ba02-5d8ef705ab89" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Before you begin

- You must have one of the following roles to complete the tasks in this article:

  - [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator)
  - [Billing Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?#billing-administrator)
  - [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?#ai-administrator)
  - [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)


  Caution


  Global Administrators have almost unlimited access to your organization's settings and most of its data. To help keep your organization secure, we recommend that you limit the number of Global Administrators as much as possible.

- To create a new subscription in the Microsoft 365 admin center, you must be a Billing Account Owner or a Billing Account Contributor.
- The tenant must have at least one SharePoint license, or a license that includes SharePoint.
- You must have an Azure subscription in the same tenant as Microsoft 365. If you don't have an Azure subscription, you can create one during the billing policy setup process.
- You must have an Azure resource group in that subscription. If you don't have an Azure resource group, you can create one during the billing policy setup process.
- You must have Owner or Contributor rights to the Azure subscription and resource group.

## Set up pay-as-you-go billing in the Billing node

### Step 1: Create a billing policy and add billing details

Note

You can't edit a subscription or resource group associated with a billing policy.

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), and then go to **Billing** > **Pay-as-you-go**.
2. On the **Billing policies** tab, select **Add a billing policy**.
3. On the **Billing details** page, enter a name for the billing policy.
4. From the **Subscription** drop-down list, select an existing Azure subscription, or select **Create a new subscription**.
5. From the **Resource** group drop-down list, select an existing resource group, or select **Create a new resource group**.
6. From the **Region** drop-down list, select a region. This selection determines where the tenant ID and usage data are stored.
7. Read the pay-as-you-go billing terms of service and privacy statement, and then select the **I accept the pay-as-you-go billing terms of service** checkbox.
8. Select **Next**.

### Step 2: Add users or groups to the billing policy

Note

Choosing users only applies to Microsoft Copilot pay-as-you-go services. For all other services, the **All users** option is automatically applied.

1. On the **Choose users** page, select **All users** or a **Specific group**. If you select **Specific group**, search for and add a single group.

   - When you select a group, only the first 1,000 groups are displayed in alphabetical order.

2. Select **Next**.

### Step 3: Set a budget for the billing policy \(optional\)

Note

If you skip this step, you can [add a budget to an existing billing policy](#add-a-budget-to-an-existing-billing-policy) later.

1. On the **Budget** page, if you want to set a budget, select the **Set a budget for this policy** checkbox.
2. Enter a value for the budget limit.
3. Select when to reset the budget spending:

   - On the first day of the month
   - On the first day of the quarter
   - On the first day of the year

4. To send budget spending alerts, in the **Recipients** box, select the name of one or more groups that you want to receive alert messages.
5. Under the **Send alerts when usage reaches this percentage of budget** section, the default value is 100%. To add other percentages, select **Add more**, and then enter the percentage at which you want an alert sent.

   Note

   It can take up to 24 hours for recipients to receive budget alert notifications.
6. When you finish configuring the budget, select **Next**.
7. Select **Next**.

### Step 4: Review and create the billing policy

1. On the **Review and create policy** page, verify all the details that you entered. Make any needed changes. When everything is correct, select **Create policy**.
2. On the **New billing policy created** page, select **Connect your services** to connect the policy to a pay-as-you-go service, or select **Done** to connect the policy later.
3. If you selected **Connect your services**, you're redirected to the **Pay-as-you-go** page. Select the name of the service to connect.
4. In the side panel, select the **Billing policies** tab.
5. Find the billing policy that you want to connect to, and then select the **Connection status** toggle to set it to **Connected**.
6. Select **Save** and then close the side panel.

## Connect a pay-as-you-go service to a billing policy

If you didn't connect to a service when you created a new billing policy, use the following steps to connect it later.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Pay-as-you-go**.
2. On the **Pay-as-you-go** page, select the **Services** tab.
3. For the service that you want to connect, in the **Billing policy** column, select **Connect a policy**.

   Note

   Manage Copilot services in **Copilot** > **Billing & usage**. For any Copilot services listed, the **Billing policy** column contains a **Manage policies** link. This link opens the side panel but doesn't contain any billing policies. Select **Go to Copilot Billing & usage** to be redirected.
4. In the side panel, find the billing policy that you want to connect to, and then select the **Connection status** toggle to set it to **Connected**.
5. Select **Save** and then close the panel.

## Add a budget to an existing billing policy

If you didn't set up a budget for a billing policy when you first created it, you can create a budget in the Microsoft 365 admin center.

You can only set budgets at the billing policy level, not for individual users, agents, or sites. This policy means any limits or alerts apply to all services and users under the policy.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Pay-as-you-go**.
2. On the **Pay-as-you-go** page, select the policy that you want to manage.
3. In the policy panel, select the **Budget** tab.
4. To view current expenses for services linked to the policy, select **Spending**. Consumption data can take up to four hours to appear in the graph.
5. To configure your budget and alert preferences, select **Settings**.
6. Select the **Set a budget for this policy** checkbox.
7. In the **Budget** text box, enter the dollar amount for your spending limit.
8. Under **Reset the budget**, select when you want to reset the budget.

   - On the first day of each month
   - On the first day of the quarter
   - On the first day of the year

9. \(Optional\) Under **Send email alerts**, search for and select the names of email-enabled groups that you want to receive budget alerts.
10. By default, the budget percentage that triggers alerts is 100%. To set more alerts, select **Add more** and enter a new value. You can add up to four more thresholds \(1-99%\).

    Note

    It can take up to 24 hours for recipients to receive budget alert notifications.
11. Select **Save**.

Important

The only way to stop billing is to disconnect the payment method. Reaching 100% of your budget doesn't stop the service or billing.

## View spending for your organization

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Pay-as-you-go**.
2. On the **Billing policies** tab, select a billing policy.
3. In the billing policy side panel, select the **Budget** tab. The **Spending** option displays data for the current month and includes a chart that displays data for the last six months.

You can also monitor your pay-as-you-go usage and costs in [Microsoft Cost Management for Azure](https://portal.azure.com/#blade/Microsoft_Azure_CostManagement/Menu/costanalysis). Ensure you have at least read access to the billing resource group.

## Disconnect a pay-as-you-go service

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Pay-as-you-go**.
2. On the **Pay-as-you-go** page, select the **Services** tab.
3. Select the service that you want to disconnect.
4. In the side panel, select the **Billing policies** tab.
5. In the **Connection status** column, select the **Connected** toggle to turn it off.
6. Select **Save** and then close the side panel.

If multiple services connect to a single policy, repeat these steps for each service.

Note

After you disconnect the service, review your billing and usage to ensure no further charges are applied.

## Delete a billing policy

After you disconnect a pay-as-you-go service, you can delete the billing policy.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Pay-as-you-go**.
2. On the **Billing policies** tab, select a billing policy.
3. In the billing policy side panel, select **Delete billing policy**.
4. In the confirmation dialog, select **Delete**.
