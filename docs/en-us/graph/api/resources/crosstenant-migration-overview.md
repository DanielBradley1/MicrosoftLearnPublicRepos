<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenant-migration-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-27 -->

# Cross-tenant migration API overview

The cross-tenant migration API in Microsoft Graph enables tenant administrators to migrate user data from one Microsoft 365 tenant to another. This API provides a unified solution for moving Exchange, Teams, and SharePoint data across tenants, supporting scenarios such as mergers, acquisitions, and organizational restructuring.

## Why use the cross-tenant migration API?

Organizations often need to consolidate or reorganize Microsoft 365 environments. The cross-tenant migration API simplifies this process by allowing admins to:

- Create and manage migration jobs for user or group data.
- Validate configurations before migration.
- Monitor migration progress and troubleshoot issues.
- Cancel or delete migration jobs for compliance purposes.

## Key features

- **Create migration jobs**: Define workloads \(Teams, Exchange, OneDrive and SharePoint\) and resources to migrate.
- **Retrieve migration jobs**: Get details for all jobs or a specific job.
- **Update migration jobs**: Modify the `completeAfterDateTime` property.
- **Cancel migration jobs or specific users**: Stop migrations in progress.
- **Validate migration jobs**: Check configuration without performing migration.
- **Delete migration jobs**: Remove jobs and associated data for compliance.

## API status

- **Preview**: Currently available in the `/beta` endpoint.
- **Scope**: User data migration only.
- **Limitations**:

  - Job names must be unique per tenant.
  - Jobs in progress can't be deleted.
  - `completeAfterDateTime` can't be set in the past.

## Permissions

Permissions vary by operation. For the least-privileged permissions and supported permission types \(delegated vs. application\) for each operation, see the **Permissions** section of the corresponding API operation.

Note

For delegated access, the signed-in user must also be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) or a custom role that grants the permissions required for the operation. For the exact permissions and supported roles, see the **Permissions** section of each API operation.

## Related content

- [Microsoft Graph overview](https://learn.microsoft.com/en-us/graph/overview)
- [Cross-tenant migration job resource type](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta)
- [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference)
