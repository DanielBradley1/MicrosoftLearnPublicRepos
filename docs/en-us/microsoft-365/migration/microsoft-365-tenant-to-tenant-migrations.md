<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/microsoft-365-tenant-to-tenant-migrations?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Plan a Microsoft 365 tenant-to-tenant migration

There are several architecture approaches for mergers, acquisitions, divestitures, and other scenarios that might lead you to migrate an existing Microsoft 365 tenant to a new tenant. This article helps you understand the planning considerations and choose the right approach.

## Common scenarios

Tenant-to-tenant migrations typically occur in one of the following business contexts:

- **Merger or acquisition**: Your organization acquired another company, and you need to consolidate users and data into a single tenant.
- **Divestiture or spin-off**: A business unit is being separated, and users need to move to a new or existing tenant owned by another organization.
- **Consolidation**: Your organization has multiple tenants from past acquisitions and wants to consolidate into one.
- **Internal reorganization**: Business restructuring requires moving users between tenants within the same parent organization.

## Choose your migration approach

Your approach depends on the scope of the migration and the workloads involved.

| Approach | Best for | Tool |
| --- | --- | --- |
| Multi-workload orchestrated migration | Migrating mailboxes, OneDrive, SharePoint, and Teams together in coordinated batches | [Migration Orchestrator](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-1-overview?view=o365-worldwide) |
| Individual workload migration | Migrating a single workload, or when you need granular control over each workload's timeline | Cross-tenant tools \([mailbox](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-mailbox-migration?view=o365-worldwide), [OneDrive](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration?view=o365-worldwide), [SharePoint](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration?view=o365-worldwide)\) |
| Partner or third-party tools | Complex migrations requiring specialized capabilities, or when internal resources are limited | Microsoft Consulting Services or certified partner tools |

## Key planning considerations

Before you start a migration, consider the following areas:

### Identity strategy

- Decide how user identities map from the source tenant to the target tenant. For more information, see [Cross-tenant identity mapping](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-identity-mapping?view=o365-worldwide).
- Determine whether users keep their existing UPN or receive a new one.
- Plan for any domain transfers between tenants.

### Workload dependencies

Workloads have dependencies that affect migration sequencing:

- Teams content depends on Exchange mailboxes: Migrate mailboxes before or alongside Teams.
- OneDrive and SharePoint share permissions models: Consider migrating them together.
- The Migration Orchestrator handles sequencing automatically for supported workloads.

### Coexistence during migration

For phased migrations, plan for a period where users exist in both tenants:

- Mail routing between tenants during the transition.
- Calendar free/busy sharing between source and target.
- Teams federation for cross-tenant communication.

### Licensing

- Make sure you have sufficient licenses available in the target tenant before migration.
- Migration Orchestrator requires specific licensing. For details, see [Planning and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-2-planning-prerequisites?view=o365-worldwide).

### Timeline estimation

Migration throughput depends on data volume, workload type, and batch size. Factors that affect your timeline include:

- Number of users and mailbox sizes.
- Volume of OneDrive and SharePoint content.
- Any mailboxes on hold \(which might block migration\).
- Network bandwidth between tenants and Microsoft 365 services.

## Next steps

- [Migration Orchestrator overview](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-1-overview?view=o365-worldwide): For coordinated, multi-workload tenant-to-tenant migrations.
- [Planning and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-2-planning-prerequisites?view=o365-worldwide): Set up your environment for an orchestrated migration.
- [Cross-tenant mailbox migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-mailbox-migration?view=o365-worldwide): Migrate Exchange mailboxes between tenants.
- [Cross-tenant SharePoint migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration?view=o365-worldwide): Migrate SharePoint sites between tenants.
