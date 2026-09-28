<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/configure-managed-identities-isolation-scope -->
<!-- Sitemap-Last-Modified: 2025-07-17 -->

# Configure isolation scope for user-assigned managed identities

This article shows you how to configure isolation scope for user-assigned managed identities in the Azure portal. You can either enable regional isolation scope or set your isolation scope to none. Regional isolation helps improve security and resilience by restricting where managed identities can be used, ensuring they can only be assigned to source resources in the same region.

## Prerequisites

Before you begin, ensure you have the following:

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Read the [Isolation scope for user-assigned managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/managed-identities-isolation-scope) concept article to understand the benefits and implications.

## Configure isolation scope in Azure portal

Use the following steps to configure isolation scope for a user-assigned managed identity.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Navigate to **Managed Identities**. In the search box, type *Managed Identities*. Under **Services**, select **Managed Identities**.
3. Create a new managed identity. Select **+ Create** to add a new user-assigned managed identity. Configure the basic settings:

   - **Subscription**: Select your subscription
   - **Resource Group**: Choose an existing resource group or create a new one
   - **Region**: Select the specific region for deployment
   - **Isolation Scope**: Select *Regional* to set the isolation scope to regional or *None* to set it to none
   - **Name**: Enter the name of the managed identity

4. Review and create. Select **Review + create** to validate your configuration.
5. Select **Create** to deploy the managed identity.

Once you set the value for isolation scope, you can only update it via Azure Resource Manager deployment template or REST API. The Azure portal doesn't yet support changing the isolation scope after creation.

## Next steps

- [Manage user-assigned managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-manage-user-assigned-managed-identities)
