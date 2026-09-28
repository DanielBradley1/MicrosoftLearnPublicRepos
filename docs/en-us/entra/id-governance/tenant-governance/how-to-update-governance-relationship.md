<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-update-governance-relationship -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Update a governance relationship

This article describes how to update an existing governance relationship between a governing tenant and a governed tenant. You might need to update a governance relationship to add or modify delegated administration roles or multitenant application configurations.

## Prerequisites

- You must have an active governance relationship between a governing tenant and a governed tenant.
- You must have access to the governance policy template you used to create the existing relationship. If you deleted the policy template, you need to create a new relationship.
- You need the **Tenant Governance Administrator** role.
- Review license requirements for sending governance requests in [Microsoft Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing#microsoft-entra-tenant-governance).

## Update the governance policy template

Before you can update a governance relationship, you must first modify the governance policy template you used to establish the existing relationship. When you update the template, its version number automatically increments by one.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a **Tenant Governance Administrator** in the governing tenant.
2. Browse to **Tenant Governance** > **Templates**, and select the policy template you used to set up the relationship.
3. Modify the template as needed. Update one or more of these configurations:

   - **Delegated administration roles**: Add or change the Microsoft Entra built-in roles assigned to security groups in the governing tenant. These roles determine the access level that users in those groups have when they sign in to the governed tenant.
   - **Multitenant application management**: Add or update custom, multitenant applications. When you update the relationship, Tenant Governance creates or updates a service principal with the corresponding permissions in the governed tenant.

4. Save the updated governance policy template. The version number of the template increments by one.

Note

Updating the governance policy template doesn't automatically update the governance relationship. The tenant admins must complete the governance request and approval process described in the sections that follow for the policy template changes to take effect.

## Send a new governance request with the updated template

After updating the governance policy template, send a new governance request from the governing tenant to the governed tenant using the updated template.

1. In the governing tenant, create a new governance request.
2. Select the governed tenant that has the existing relationship you want to update.
3. Select the updated governance policy template.
4. Submit the governance request. The governed tenant receives an email notification about the new governance request.

## Accept the governance request

An admin in the governed tenant must accept the governance request to complete the update.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a **Tenant Governance Administrator** in the governed tenant.
2. Browse to **Tenant Governance** > **Received requests**.
3. Review the updated governance request, including the changes in the policy template.
4. Accept the governance request. The system updates the existing governance relationship with the new policy template configuration. The governing tenant receives an email confirming the accepted request and the updated governance relationship.

When the governed tenant accepts the governance request, these changes take effect:

- Tenant Governance updates the policy snapshot of the existing governance relationship to reflect the latest version of the policy template.
- If you updated delegated administration roles, Tenant Governance updates the GDAP role assignments in the governed tenant accordingly.
- If you updated multitenant application management, Tenant Governance updates the corresponding service principal and its permissions in the governed tenant.

## Related content

- [Set up a governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-governance-relationship)
- [Terminate a governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-terminate-governance-relationship)
- [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates)
