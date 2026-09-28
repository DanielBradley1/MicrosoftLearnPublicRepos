<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/automatic-governance-relationships -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Automatic formation of governance relationships

When a permissioned user in your organization creates a new tenant using the secure add-on tenant creation feature, Microsoft Entra can automatically establish a governance relationship to the newly created tenant on your behalf.

If you defined a default [governance policy template](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates), a new governance relationship forms between the home \(governing\) tenant and the newly created add-on \(governed\) tenant, using the default policy template.

If roles and permissions haven't been defined in the default governance policy template, a governance relationship won't be established when a new add-on tenant is created. Changes to the template don't affect governance relationships that have already been established.

## Microsoft Entra ID Free billing asset

When you create a new Microsoft Entra tenant using the secure add-on tenant creation feature, you're prompted to select an existing subscription and resource group from your billing account. When you create your new tenant, Microsoft generates a new billing asset called **Entra ID Free** under that subscription and resource group, which links to the newly created tenant.

The subscription tracks new tenants created with the same billing account, allowing you to maintain an inventory of all new tenants. The subscription also helps prove tenant ownership and helps regain administrative access if you ever lose it. To learn more, see [Microsoft Entra ID Free](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/microsoft-entra-id-free).

## Related content

- [Governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships)
- [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates)
- [Create a governed workforce tenant](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-tenant)
