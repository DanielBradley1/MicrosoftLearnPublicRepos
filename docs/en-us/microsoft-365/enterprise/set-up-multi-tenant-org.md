<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/set-up-multi-tenant-org?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Set up a multitenant org in Microsoft 365

You can set up a multitenant organization or add tenants to an existing one in the Microsoft 365 admin center.

When each external tenant accepts the invitation to join the multitenant organization, the following settings are configured in Microsoft Entra ID:

- A cross-tenant synchronization configuration is added with the name `MTO_Sync_<TenantID>`, but no sync jobs are created yet. \(If you already have a cross-tenant synchronization configuration, it remains unchanged.\)
- An organization relationship is added to the [cross-tenant access settings](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/cross-tenant-access-overview) based on the [multitenant organization templates](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/multi-tenant-organization-templates) for cross-tenant access and identity synchronization. \(If an organizational relationship already exists, the existing one is used.\)
- The multitenant organization template for identity synchronization is set to allow users to sync into this tenant.
- The multitenant org template for cross-tenant access will be set to automatically redeem user invitations, inbound as well as outbound.

## Set up a new multitenant organization

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To set up a new multitenant org in Microsoft 365:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Get started**.
5. Select **Create a new multitenant organization**, and then select **Next**.
6. Type a name and description for the multitenant org.
7. Enter the tenant IDs of any tenants that you want to invite to this org.
8. Select **Next**.
9. Select the **Allow users to sync into this tenant from the other tenants in this multitenant organization** and **Suppress consent prompts for users from the other tenant when they access apps and resources in my tenant** check boxes.
10. Select **Next**.
11. Select **Create multitenant organization**.
12. Copy the instructions for joining the multitenant org and email them to a global administrator in each of the orgs you invited.
13. Select **Done**.

The next step after each external tenant accepts the invitation to join the multitenant organization is to synchronize your users with the other tenants. For details, see [Synchronize users in multitenant orgs in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/sync-users-multi-tenant-orgs?view=o365-worldwide).

## Add a tenant to your multitenant organization

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To add a tenant to your multitenant organization:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Add new tenants**.
5. Enter the tenant IDs of the tenants you want to add, and then select **Add tenant**.
6. Copy the instructions for joining the multitenant org and email them to a global administrator in each of the orgs you invited.
7. Select **Done**.

The next step after each external tenant accepts the invitation to join the multitenant organization is to synchronize your users with the other tenants. For details, see [Synchronize users in multitenant orgs in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/sync-users-multi-tenant-orgs?view=o365-worldwide).

## Related articles

[Set up a multitenant organization using Microsoft Graph API](https://learn.microsoft.com/en-us/azure/active-directory/multi-tenant-organizations/multi-tenant-organization-configure-graph)

[Plan for multitenant organizations in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-multi-tenant-org-overview?view=o365-worldwide)

[Join or leave a multitenant organization in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/join-leave-multi-tenant-org?view=o365-worldwide)

[Synchronize users in multitenant organizations in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/sync-users-multi-tenant-orgs?view=o365-worldwide)
