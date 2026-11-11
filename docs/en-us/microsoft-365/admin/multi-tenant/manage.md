<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/multi-tenant/manage?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-01-06 -->

# Manage multiple tenants in the Microsoft 365 admin center

Multi-tenant management in the Microsoft 365 admin center gives partner and enterprise administrators a unified way to discover connected tenants, move between them, and manage supported capabilities from the **Tenants** scope. Tenant relationships preserve each tenant boundary while delegated access determines which tenants an administrator can open and which actions the administrator can perform.

## Who should use this experience

- Partners and managed service providers that administer customer tenants through Microsoft Partner Center.
- Enterprise central IT teams that administer subsidiaries, regions, business units, or other Microsoft 365 tenants connected through Microsoft Entra Tenant Governance.

## Before you begin

- Establish a supported tenant relationship. Partners use a customer relationship and Granular Delegated Admin Privileges \(GDAP\) in Partner Center. Enterprises use a directional governance relationship in Microsoft Entra Tenant Governance.
- Assign the signed-in administrator an appropriate delegated role in each governed tenant. Available pages and actions can differ when role assignments differ across tenants.
- Use the least-privileged role that completes the task. Some workload-specific actions require additional fine-grained permissions or licenses.

Note

Microsoft Entra Tenant Governance is different from Microsoft 365 multitenant organization collaboration. Tenant Governance establishes a governing-to-governed administrative relationship; it isn't a B2B guest-account model.

## Connect tenants for multi-tenant management

A connected tenant appears in the governing tenant after you establish an administrative relationship and the signed-in administrator has delegated access. The governing tenant is where administration begins. You access a governed tenant in delegated context.

| Scenario | Relationship configured in | Connection model |
| --- | --- | --- |
| Partner / CSP | Microsoft Partner Center | Configure a customer relationship and GDAP with time-bound, role-scoped access. The partner tenant acts as the governing tenant. |
| Enterprise | Microsoft Entra Tenant Governance | Create a directional relationship request from the governing tenant. The target tenant approves it, then delegated access is assigned. |

### For partners: configure relationships in Partner Center

Use Partner Center to establish the customer relationship and configure GDAP. The exact invitation and approval flow depends on the existing customer relationship and requested roles.

1. In Partner Center, open the customer relationship or GDAP administration experience for the customer tenant.
2. Create or update a GDAP relationship, select the Microsoft Entra roles required for the service, and set the relationship duration.
3. Send the request to the customer and have an authorized customer administrator approve it.
4. Assign approved delegated roles to the partner security groups that contain the administrators who manage the customer tenant.
5. After the relationship and role assignment become active, sign in from the partner tenant and verify that the customer tenant appears in **Tenants** and the tenant switcher.

For more information, see the following resources:

- [Introduction to granular delegated admin privileges \(GDAP\)](https://learn.microsoft.com/en-us/partner-center/customers/gdap-introduction)
- [Add and manage multiple tenants in your Partner Center account](https://learn.microsoft.com/en-us/partner-center/account-settings/multi-tenant-account)

### For enterprises: connect tenants with Microsoft Entra Tenant Governance

Microsoft Entra Tenant Governance uses a directional relationship between a governing tenant and a governed tenant. Establish the relationship pairwise for each tenant that central administrators need to manage.

1. From the intended governing tenant, create a Tenant Governance relationship request for the target tenant.
2. In the target tenant, have an authorized administrator review and approve the request.
3. Configure delegated access and assign the appropriate roles to administrators in the governing tenant.
4. Repeat the request-and-approval process for each additional governed tenant.
5. Sign in from the governing tenant and verify that approved tenants appear in **Tenants** and the tenant switcher.

For more information, see the following resources:

- [What is Microsoft Entra Tenant Governance?](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/overview)
- [Configuration management in Microsoft Entra Tenant Governance](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/configuration-management)

Note

**Security boundary**: Connecting tenants doesn't merge directories or remove tenant isolation. Administrators authenticate by using their governing-tenant identity, and delegated roles are honored in the selected governed tenant.

## Open the **Tenants** experience

1. Sign in to the Microsoft 365 admin center with an account in the governing tenant.
2. In the left navigation, select **Tenants**.
3. Use the available pages to review the tenant estate and open supported multitenant experiences, such as **Tenants**, **Agents**, service health, and configuration management.

The **Tenants** page provides a consolidated view of connected tenants and helps administrators search, select, and prioritize tenants. Available cards, columns, filters, and actions depend on roles and enabled capabilities.

## Switch between tenants

Use the tenant switcher when you need to leave the consolidated governing-tenant view and work directly in one governed tenant. Switching changes the active tenant context while preserving the signed-in administrator’s identity and delegated access.

1. In the Microsoft 365 admin center command bar, select the tenant switcher next to the current tenant name.
2. Search for a tenant or select an eligible governed tenant from the list.
3. Confirm the selection. The Microsoft 365 admin center opens in the selected tenant by using delegated access.
4. Use the tenant switcher again to return to the governing tenant or move to another eligible governed tenant.

Tip

To return to consolidated multi-tenant pages, switch back to the governing tenant and select **Tenants**.

### Tenant switcher features

| Feature | What it provides |
| --- | --- |
| Same signed-in identity | Move between eligible tenants without signing out, opening a separate session, or maintaining a local account in every tenant. |
| Delegated tenant context | Open the selected tenant using access granted through Partner Center or Microsoft Entra Tenant Governance. |
| Search and selection | Search the list when many tenants are connected, then select the tenant that requires attention. |
| Clear context cues | Use the active tenant name in the command bar to confirm context before changing settings. |
| Governing and governed grouping | Distinguish the governing tenant from tenants available through delegated relationships. |
| Fast return path | Switch back to the governing tenant for consolidated **Tenants** experiences, or move directly to another governed tenant. |

### Understand tenant context before taking action

- Confirm the tenant name in the command bar before changing configuration, licenses, users, agents, policies, or billing settings.
- Role assignments are evaluated per governed tenant. A page or action available in one tenant might be read-only or unavailable in another tenant.
- Switching tenant context doesn't automatically grant workload permissions. The administrator must have the role required by the target workload and operation.

## Troubleshoot tenant visibility and switching

| Issue | What to check |
| --- | --- |
| A tenant does not appear | Confirm that the Partner Center GDAP or Microsoft Entra Tenant Governance relationship is active, the request was approved, and delegated roles are assigned. |
| A tenant appears but an action is unavailable | Compare delegated role assignments with the role required by the workload. Access can differ across governed tenants. |
| A workload blocks access | Verify that the workload supports delegated administration and that the administrator has workload-specific permissions. |
| The wrong tenant is active | Check the tenant name in the command bar, reopen the tenant switcher, and select the intended tenant. |

## Related content

- [Manage agents across multiple tenants in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/agent-multi-tenant)
- [What is Microsoft Entra Tenant Governance?](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/overview)
- [Introduction to granular delegated admin privileges \(GDAP\)](https://learn.microsoft.com/en-us/partner-center/customers/gdap-introduction)
- [Add and manage multiple tenants in your Partner Center account](https://learn.microsoft.com/en-us/partner-center/account-settings/multi-tenant-account)
- [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference)
