<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Set up or disconnect pay-as-you-go billing in the Setup node of the Microsoft 365 admin center

This article explains how to set up or disconnect pay-as-you-go billing in the **Setup** node of the Microsoft 365 admin center for the following services:

- Document processing for Microsoft 365
- Microsoft 365 Archive

## Before you begin

- To access the Microsoft 365 admin center, you must have either the [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) role.

  Caution

  Global Administrators have almost unlimited access to your organization's settings and most of its data. To help keep your organization secure, we recommend that you limit the number of Global Administrators as much as possible.
- You must have Owner or Contributor rights to the Azure subscription and resource group.
- The tenant must have at least one SharePoint license, or a license that includes SharePoint.
- You must have an Azure subscription in the same tenant as Microsoft 365.
- You must have an Azure resource group in that subscription.

## Activate pay-as-you-go services in the Setup node

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. Go to **Setup** > **Billing and licenses**.
3. In the **Billing and licenses** section, select **Activate pay-as-you-go services**.
4. On the **Activate pay-as-you-go services** page, select **Get started**.
5. On the **Pay-as-you-go services** page, select the service you want to set up, like **Syntex services**.
6. On the **Set up billing and turn on services** panel, choose your Azure subscription, resource group, and region.
7. Read and accept the pay-as-you-go terms of service.
8. Select **Save** to complete the setup.

## Monitor usage and costs

After setup, monitor your pay-as-you-go usage and costs in [Microsoft Cost Management for Azure](https://portal.azure.com/#blade/Microsoft_Azure_CostManagement/Menu/costanalysis). Ensure that you have at least read access to the billing resource group.

## Disconnect pay-as-you-go billing

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), and then go to **Settings** > **Org settings**.
2. Select **Pay-as-you-go services**.
3. Choose the service to disconnect, like **Syntex services**.
4. In the **Manage billing** panel, select **Edit billing information**.
5. Under **Manage billing**, select **Disconnect Azure subscription**.
6. Select **Disconnect** in the confirmation window.

If multiple services connect to a single policy, repeat the steps for each service.

After you disconnect the service, review your billing and usage to ensure no further charges are applied.
