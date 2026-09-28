<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/howto-remove-app -->
<!-- Sitemap-Last-Modified: 2025-12-12 -->

# Remove an application registered with the Microsoft identity platform

Enterprise developers and software-as-a-service \(SaaS\) providers who have registered applications with the Microsoft identity platform may need to remove an application's registration.

Tip

Before permanently removing an application, consider [deactivating it](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/deactivate-application-portal) instead. Deactivation prevents token issuance while preserving the application configuration for investigation or potential reactivation, making it a less destructive alternative to deletion.

In the following sections, you learn how to:

- Remove an application authored by you or your organization
- Remove an application authored by another organization

## Prerequisites

- An [application registered in your Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app)

## Remove an application authored by you or your organization

Applications that you or your organization have registered are represented by both an application object and service principal object in your tenant. For more information, see [Application objects and service principal objects](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals).

Note

Deleting an application will also delete its service principal object in the application's home directory. For multitenant applications, service principal objects in other directories will not be deleted.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/admin-center-settings-icon.png) in the top menu to switch to the tenant containing the app registration from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **App registrations** and then select the application that you want to configure. Once you've selected the app, you see the application's **Overview** page.
4. From the **Overview** page, select **Delete**.
5. Read the deletion consequences. Check the box if one appears at the bottom of the pane.
6. Select **Delete** to confirm that you want to delete the app.

## Remove an application authored by another organization

If you're viewing **App registrations** in the context of a tenant, a subset of the applications that appear under the **All apps** tab are from another tenant and were registered into your tenant during the consent process. More specifically, they're represented by only a service principal object in your tenant, with no corresponding application object. For more information on the differences between application and service principal objects, see [Application and service principal objects in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals).

In order to remove an application’s access to your directory \(after having granted consent\), the company administrator must remove its service principal. The administrator must have at least the [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) access. To learn how to delete a service principal, see [Delete an enterprise application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/delete-application-portal).

## Next steps

Learn more about [application and service principal objects](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals) in the Microsoft identity platform.
