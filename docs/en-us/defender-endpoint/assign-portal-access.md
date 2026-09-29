<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/assign-portal-access -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Overview of permissions management

This article helps you understand the available permission models for Microsoft Defender for Endpoint portal access and how to switch between them. Defender for Endpoint supports two ways to manage permissions:

- **Basic permissions management**: Set permissions to either full access or read-only. See [Use basic permissions to access the portal](https://learn.microsoft.com/en-us/defender-endpoint/basic-permissions).
- **Role-based access control \(RBAC\)**: Set granular permissions by defining roles, assigning Microsoft Entra user groups to the roles, and granting the user groups access to device groups. For more information on RBAC, see [Manage portal access using role-based access control](https://learn.microsoft.com/en-us/defender-endpoint/rbac).

Important

Starting February 16, 2025, new Microsoft Defender for Endpoint customers will only have access to the Unified Role-Based Access Control \(URBAC\). Existing customers keep their current roles and permissions. For more information, see URBAC [Unified Role-Based Access Control \(URBAC\) for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## Change from basic permissions to RBAC

Important

Switching to RBAC is irreversible. After you switch, you can't return to basic permissions management.

If you have basic permissions, you can switch to Role-based access control \(RBAC\) anytime. Consider the following before making the switch:

- Users who have full access are automatically assigned the default Defender for Endpoint administrator role.
- Other Microsoft Entra user groups can be assigned to the Defender for Endpoint administrator role after switching to RBAC.
- Only users who are assigned the Defender for Endpoint administrator role can manage permissions using RBAC.
- Users who have read-only access \(Security Readers\) lose access to the portal until they're assigned a role. Only Microsoft Entra user groups can be assigned a role under RBAC.

Important

Microsoft recommends that you use roles with the fewest permissions as it helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Related articles

- [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups)
- [Zero Trust with Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/zero-trust-with-microsoft-defender-endpoint)
