<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-enable-tenant-discovery -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Enable tenant discovery

Related tenants help administrators discover other Microsoft Entra tenants that have observable relationships with their tenant. Microsoft Entra infers these relationships from activity signals such as B2B collaboration, multitenant application consent, and shared billing accounts. A related tenant doesn't imply ownership or administrative control. It indicates an observed association across Microsoft services.

After you enable related tenant discovery, it remains enabled for your tenant if your tenant meets the licensing requirements.

## Prerequisites

Before you enable related tenants, make sure:

- You have the necessary permissions to enable related tenants. You must hold either the Tenant Governance Administrator or Global Administrator Microsoft Entra role.
- Your tenant is eligible for related tenants with the correct license.
- You understand that this setting isn't a toggle and remains enabled after you turn it on.

## Enable related tenants through the Microsoft Entra admin center

Use this option to enable discovery through the admin center rather than APIs.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a **Tenant Governance Administrator**.
2. Browse to **Tenant Governance** > **Related tenants**.
3. Review the description of enabling related tenants.
4. Select **Discover related tenants**.

After you enable the setting, Microsoft Entra begins aggregating discovery signals and surfaces related tenants in the admin center. The discovery data is synthesized from existing activity and might take time to populate.

## Enable related tenants through Microsoft Graph API

Use this option to enable discovery through scripts or automation.

**Endpoint**

```http
POST /directory/tenantGovernance/settings/enableRelatedTenants
```

This action enables related tenant discovery for the calling tenant.

**Important notes**

- The setting defaults to `false` for new tenants.
- After you enable the setting, `isRelatedTenantsEnabled` changes to `true` and can't be reverted.

## Next steps

After related tenants appear, take any of these actions:

- [Review the list of related tenants](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/related-tenants) surfaced by discovery.
- [Interpret tenant discovery data](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-interpret-discovery-data) to classify and prioritize related tenants.
- Use the data to inform governance decisions:

  - [Set up governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-governance-relationship) with discovered tenants.
  - Plan tenant inventory and cleanup efforts.
  - [Learn more about Tenant Governance](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/overview) and configuration management planning.
