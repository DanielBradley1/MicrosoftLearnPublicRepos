<!-- Source: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/prerequisites -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Prerequisites to use PowerShell or Graph Explorer for Microsoft Entra roles

If you want to manage Microsoft Entra roles using PowerShell or Graph Explorer, you must have the required prerequisites. This article lists the PowerShell and Graph Explorer prerequisites for different Microsoft Entra role features.

## Microsoft Graph PowerShell

To use PowerShell commands to do the following:

- Add users, groups, or devices to an administrative unit
- Create a new group in an administrative unit

You must have the Microsoft Graph PowerShell SDK installed:

- [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation)

## Graph Explorer

To manage Microsoft Entra roles using the [Microsoft Graph API](https://learn.microsoft.com/en-us/graph/overview) and [Graph Explorer](https://learn.microsoft.com/en-us/graph/graph-explorer/graph-explorer-overview), you must do the following:

1. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.
2. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
3. Browse to **Entra ID** > **Enterprise apps**.
4. In the applications list, find and select **Graph explorer**.
5. Select **Permissions**.
6. Select **Grant admin consent for Graph explorer**.

   ![Screenshot showing the "Grant admin consent for Graph explorer" link.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/media/prerequisites/select-graph-explorer.png)

7. Use [Graph Explorer tool](https://aka.ms/ge).

## Next steps

- [Microsoft Graph PowerShell documentation](https://learn.microsoft.com/en-us/powershell/microsoftgraph/)
- [Graph Explorer](https://learn.microsoft.com/en-us/graph/graph-explorer/graph-explorer-overview)
