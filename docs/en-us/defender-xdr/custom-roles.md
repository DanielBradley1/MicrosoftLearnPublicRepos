<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/custom-roles -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Custom roles in role-based access control for Microsoft Defender portal services

By default, access to services available in the Microsoft Defender portal are managed collectively using [Microsoft Entra global roles](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions). If you need greater flexibility and control over access to specific product data, and aren't yet using the [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) for centralized permissions management, we recommend creating custom roles for each service.

For example, create a custom role for Microsoft Defender for Endpoint to manage access to specific Defender for Endpoint data, or create a custom role for Microsoft Defender for Office to manage access to specific email and collaboration data.

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Locate custom role management settings in the Microsoft Defender portal

Each Microsoft Defender service has its own custom role management settings, with some services being represented in a central location in the Microsoft Defender portal. To locate custom role management settings in the Microsoft Defender portal:

1. Sign in to the Microsoft Defender portal at [security.microsoft.com](https://security.microsoft.com).
2. In the navigation pane, select **Permissions**.
3. Select the **Roles** link for the service where you want to create a custom role. For example, for Defender for Endpoint:

[![Screenshot that shows Roles link for Defender for Endpoint.](https://learn.microsoft.com/en-us/defender-xdr/media/custom-roles/custom-roles-endpoint.png)](https://learn.microsoft.com/en-us/defender-xdr/media/custom-roles/custom-roles-endpoint.png#lightbox)

In each service, custom role names aren't connected to global roles in Microsoft Entra ID, even if similarly named. For example, a custom role named *Security Admin* in Microsoft Defender for Endpoint isn't connected to the global *Security Admin* role in Microsoft Entra ID.

## Reference of Defender portal service content

For information about the permissions and roles for each Microsoft Defender XDR service, see the following articles:

- [Microsoft **Defender for Cloud** user roles and permissions](https://learn.microsoft.com/en-us/azure/defender-for-cloud/permissions)
- [Configure access for **Defender for Cloud Apps**](https://learn.microsoft.com/en-us/defender-cloud-apps/manage-admins)
- [Create and manage roles in **Defender for Endpoint**](https://learn.microsoft.com/en-us/defender-endpoint/user-roles)
- [Roles and permissions in **Defender for Identity**](https://learn.microsoft.com/en-us/defender-for-identity/role-groups)
- [Microsoft **Defender for IoT** user management](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/manage-users-overview)
- [Microsoft **Defender for Office 365** permissions](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions)
- [Manage access to **Microsoft Defender**](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions)
- [**Microsoft Security Exposure Management** permissions](https://learn.microsoft.com/en-us/security-exposure-management/prerequisites#permissions)
- [Roles and permissions in **Microsoft Sentinel**](https://learn.microsoft.com/en-us/azure/sentinel/roles)

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.
