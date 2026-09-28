<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-delete-external-tenant-portal -->
<!-- Sitemap-Last-Modified: 2025-06-06 -->

# Delete an external tenant

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

You can't delete an external tenant until it passes several checks. These checks reduce the risk that deleting an external tenant negatively affects user access. For example, if the tenant associated with a subscription is unintentionally deleted, users can't access the Azure resources for that subscription.

## Prerequisites

- A Microsoft Entra External ID external tenant that you want to delete.
- There are no users in the external tenant, except one [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) who will delete the tenant. You must delete any other users before you can delete the tenant.
- There are no applications in the tenant. Make sure that you remove all applications including the **b2c-extensions-app**. You must delete all apps listed under **App registrations** in the **All applications** section before proceeding with the deletion.

## Delete the external tenant

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to your external tenant from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **Overview** > **Manage tenants**.
4. Select the tenant you want to delete, and then select **Delete**.

   ![Screenshot that shows how to delete the tenant.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-create-external-tenant-portal/delete-tenant.png)
5. You might need to complete required actions before you can delete the tenant. For example, you might need to delete all user flows in the tenant. If you're ready to delete the tenant, select **Delete**.

The tenant and its associated information are deleted.
